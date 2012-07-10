## Reference Documents

[PostgreSQL Cheatsheet][3]
[Using Regular Expressions in PostgreSQL][4]

-----

# xcoord column maintenance

## Remove wrongly values xcoord column values:

     update new_all SET xcoord = '' where xcoord ~* '\\N' OR xcoord ~* '[A-Z]{1,}';

### Response:

     nyclu=# update new_all SET xcoord = '' where xcoord ~* '\\N' OR xcoord ~* '[A-Z]{1,}';
     UPDATE 946155

-----

## Verify removal was successful

     nyclu=# select xcoord from new_all where xcoord ~* '[A-Z]{1,}';

     xcoord
     --------
     (0 rows)

## Remove leading and trailing white space

     update new_all set xcoord =     replace(xcoord, ' ', '') where xcoord ~* '^[ ]{1,}' OR xcoord ~* '[ ]{1,}$';

### Response

     nyclu=# update new_all set xcoord =     replace(xcoord, ' ', '') where xcoord ~* '^[ ]{1,}' OR xcoord ~* '[ ]{1,}$';
     UPDATE 4259631

### Verify it was successful     

     nyclu=# select xcoord, ycoord from new_all where xcoord != '';
     xcoord     | ycoord
     ---------+---------
     1012304 | 0222651
     0987555 | 0214890
     0990313 | 0215177
     0986626 | 0205180
     1002692 | 0218421
     0930949 | 0133127
     1019287 | 0208218
     0984103 | 0201020
     1021547 | 0247314
     1010719 | 0186857


-----

## Make xcoord null if ycoord is null, ycoord null if xcoord null

 - *based off of discussion on stackoverflow discussion on [PostgreSQL - Using a Subquery to Update Multiple Column Values][2]

     UPDATE new_all SET xcoord = '', ycoord = ''
     WHERE
     ycoord = ''
     OR ycoord = '0'
     OR ycoord ~* '^0$'
     OR ycoord ~* '^[ ]{1,}$'
     OR xcoord = ''
     OR xcoord = '0'
     OR xcoord ~* '^0$'
     OR xcoord ~* '^[ ]{1,}$'

### Response

     nyclu=# update new_all SET xcoord = '', ycoord = ''
     where
     ycoord ~* '^[ ]{0,}[0]{0,}[ ]{0,}$'
     OR xcoord ~* '^[ ]{0,}[0]{0,}[ ]{0,}$';

     UPDATE 946320

### Verify it was successful

     nyclu=# select xcoord, ycoord from new_all
     where ycoord ~* '^[ ]{1,}'
     OR ycoord ~* '[ ]{1,}$'
     OR ycoord ~* '^[ ]{0,}[0]{1,}[ ]{0,}$'
     limit 10;

     xcoord | ycoord
     --------+--------
     (0 rows)
     

#### Note: Why was this necessary?

Some records only contain an xcoord and a '0' value for the ycoord.
![](https://img.skitch.com/20120707-dauj1s35uei5bks8puaji8k1n7.png)


********


# ycoord column maintenance

## Remove wrongly valued ycoord column values:

     update new_all SET ycoord = '' where ycoord ~* '\\N' OR ycoord ~* '[A-Z]{1,}';

### Response

     nyclu=# update new_all SET ycoord = '' where ycoord ~* '\\N' OR ycoord ~* '[A-Z]{1,}';
     UPDATE 946266

-----

## Remove leading and trailing white space

     update new_all set ycoord =     replace(ycoord, ' ', '') where ycoord ~* '^[ ]{1,}' OR ycoord ~* '[ ]{1,}$';

### Response

     nyclu=# update new_all set ycoord =     replace(ycoord, ' ', '') where ycoord ~* '^[ ]{1,}' OR ycoord ~* '[ ]{1,}$';
UPDATE 675555

### Verify it was successful

     nyclu=# select ycoord from new_all where ycoord ~* '^[ ]{1,}' OR ycoord ~* '[ ]{1,}$';
     ycoord
     --------
     (0 rows)

-----

<!-- update new_all set xcoord =     replace(xcoord, ' ', ''); where xcoord ~* '^[ ]{1,}' OR xcoord ~* '[ ]{1,}$';
update new_all set ycoord =     replace(ycoord, ' ', '') where ycoord ~* '^[ ]{1,}' OR ycoord ~* '[ ]{1,}$';
update new_all SET ycoord = '' where xcoord = '' or xcoord = '0' or xcoord = 0;
update new_all SET xcoord = '' where ycoord = '' or ycoord = '0' or ycoord = 0; -->


# Add better latitude / longitude pairs

## Create new geometry column (lat\_lon) in table new\_all for reprojected lat/lons

     SELECT AddGeometryColumn ('public','new_all','lat_lon',4326,'POINT',2);


## Create geom column with geometry from original xcoord/ycoord in NY State Plane projection (EPSG:2263)

     nyclu=# SELECT AddGeometryColumn ('public','new_all','geom',2263,'POINT',2);
     addgeometrycolumn                 
     --------------------------------------------------
      public.new_all.geom SRID:2263 TYPE:POINT DIMS:2 
      (1 row)

## Populate geom with geometry from original xcoord/ycoords

     UPDATE new_all SET geom = ST_GeomFromText('POINT('|| xcoord ||' ' || ycoord || ')', 2263) WHERE coalesce(trim(xcoord),'') <> '' AND coalesce(trim(ycoord),'') <> '';



## Populate lat_lon with geometry from unprojected WGS84 lat/lon

     <!-- UPDATE new_all SET lat_lon = ST_Transform(ST_GeomFromText('POINT('|| cast(xcoord as int) ||' ' || cast(ycoord as int) || ')', 2263), 4326) WHERE coalesce(trim(xcoord),'')     <> '' AND coalesce(trim(ycoord),'')     <> ''; -->
     
     UPDATE new_all SET lat_lon = ST_Transform(ST_GeomFromText('POINT('|| xcoord ||' ' || ycoord || ')', 2263), 4326)
     WHERE coalesce(trim(xcoord),'')     <> ''
     AND coalesce(trim(ycoord),'')     <> '';

### Response

     nyclu=# UPDATE new_all SET lat_lon = ST_Transform(ST_GeomFromText('POINT('|| xcoord ||' ' || ycoord || ')', 2263), 4326)
     WHERE coalesce(trim(xcoord),'')     <> ''
     AND coalesce(trim(ycoord),'')     <> '';

     UPDATE 3313111
     

## Create Spatial Index for quick geo queries

     CREATE INDEX ix_lat_lon ON new_all USING GIST (lat_lon);

### Response

     nyclu=# CREATE INDEX ix_lat_lon ON new_all USING GIST (lat_lon);
     CREATE INDEX


## Retroactively assign primary key to existing postgres database

 - *Thank you to Enrico Stahn for the [excellent tutorial][1]*

     ALTER TABLE "public"."new_all" ADD COLUMN "id" integer;
     CREATE sequence "public"."new_all_id_seq";
     UPDATE new_all SET id = nextval('"public"."new_all_id_seq"');

     nyclu=# update new_all set id = nextval('"public"."new_all_id_seq"');
     UPDATE 4259631
     
### Unique key (verify)

     nyclu=# select id, pct from new_all where pct = '5' limit 10;

     id     | pct
     ---------+-----
     5135229 | 5
     5135463 | 5
     5136117 | 5
     5136577 | 5
     5137605 | 5
     5137607 | 5
     5137631 | 5
     5138339 | 5
     5139589 | 5
     5139987 | 5
     (10 rows)



     ALTER TABLE "public"."new_all"
     ALTER COLUMN "id" SET DEFAULT nextval('"public"."new_all_id_seq"');

     ALTER TABLE "public"."new_all" ALTER COLUMN "id" SET NOT NULL;
     ALTER TABLE "public"."new_all" ADD UNIQUE ("id");
     ALTER TABLE "public"."new_all" DROP CONSTRAINT "new_all_id_key" RESTRICT;
     ALTER TABLE "public"."new_all" ADD PRIMARY KEY ("id");

Note, this may have been able to be accomplished using "ALTER TABLE your_table ADD COLUMN id serial NOT NULL PRIMARY KEY;"


[1]:http://blog.enricostahn.com/2010/06/11/postgresql-add-primary-key-to-an-existing-table.html
[2]:http://stackoverflow.com/questions/7460102/postgresql-using-a-subquery-to-update-multiple-column-values

[3]:http://www.petefreitag.com/cheatsheets/postgresql/
[4]:http://www.oreillynet.com/pub/a/databases/2006/02/02/postgresq_regexes.html?page=2