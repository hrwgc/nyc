*This is a modified version of [Vanessa Hurst's scripts](https://github.com/DBNess/nyclu) for working with the NYPD data in PostgreSQL/PostGIS.*

## create DB based on postgis template

	createdb -T template_postgis nyclu
	psql -d nyclu
	CREATE EXTENSION PostGIS;

## create postgis compatible sql from csv using OGR

	ogr2ogr -f "PGDump" sqf_2010.sql all_new.csv 

## import data

	psql -d nyclu --set ON_ERROR_ROLLBACK=on -f ~/desktop/sqf_2010.sql


The following did not work for me: 

## create a geometry column for our new lat/long data

	SELECT AddGeometryColumn ('public','new_all','lat_lon',4326,'POINT',2);
    
## populate geometry column

	UPDATE 'new_all' SET lat_lon = ST_Transform(ST_GeomFromText('POINT('|| xcoord ||' ' || ycoord || ')', 2263), 4326) WHERE coalesce(trim(xcoord),'')  <> '' AND coalesce(trim(ycoord),'')  <> '';


## create index to speed up geo calculations

	CREATE INDEX ix_sqf_2010_lat_lon ON sqf_2010 USING GIST (lat_lon);

## create new table with only geo mapping to help other data users

	CREATE state_plane_to_latlng 
	AS
	SELECT DISTINCT xcoord, ycoord
	, ST_x(the_geom) as longitude
	, ST_y(the_geom) as latitude
	FROM sqf_2010
	ORDER BY xcoord, ycoord;

## export table to csv

	COPY state_plane_to_latlng TO '/state_plane_to_latlng.csv' CSV HEADER;



