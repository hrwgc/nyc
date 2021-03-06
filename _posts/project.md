
# Stop and Frisk

 > In the first three months of 2012, 203,500 New Yorkers were stopped by the police.
 > - 181,457 were totally innocent (89 percent).
 > - 108,097 were black (54 percent).
 > - 69,043 were Latino (33 percent).
 > - 18,387 were white (9 percent).
      - [NYCLU](http://www.nyclu.org/issues/racial-justice/stop-and-frisk-practices)
 
# Project Ideas

## What do we have? 
- NYPD stop question and frisk databases for 2003-2011
- over ** 4.2 million ** records 
- each record has 112 columns of information on the stop: justification, demographic, outcome, if force was used/why, location (street address)

- ~2.6 million records contain precise geographical coordinates 

## Tasks

### Database cleanup 
1. Currently running local MySQL and PostgresSQL databases. Some cells contain extra spaces around cell content. (this is due to the format we received the databases in initially). There are also some encoding issues. PostGIS import with UTF-8 encoding fails but works with LATIN1. 
2. Migrate refined database to PostGIS database (locally (?) or set up a server environment for remote PostGIS)
3. Geocode the remaining ~ 2 million records
4. Add additional geographical reference boundaries to entries. They currently contain some precinct information, but community districts, boroughs, etc. might have more 
Meaning to people. NYC has a great listing of [community boundary shapefiles]() on their Byte of the Big Apple site. 
5. Viral storming of the data - cross upload it to as many open data repositories as possible: thedatahub geocommons, buzzdata, junar, providing the same amount of metadata as on main site.

### Data Analysis

1. Aggregate overlapping points where appropriate to create elevation columns for particular geographical areas (whether blocks, points, etc). Elevation can then be used to visualize density. 
2. Review free text columns, some of which have several hundred thousand unique responses, and consider if/ how we might recode them. 
3. Basic statistics of stops/frisks for each precinct/community district/other boundary, with attention paid to demographic information as well as the reasoning given for the action taken by the NYPD. 
4. Make the results of #3 as transparent and accessible to ordinary non-statistical and non-developer people as possible. (ie, plain language documentation and CSV summaries of precinct aggregate statistics. 

### Mapping 

1. Heat maps - by year or aggregate, looking at demographics as well as other categories
2. Choropleths - same for #1 but use data analysis #3 boundary statistics to help people understand the phenomenon using boundaries they may more closely identify with 
3. Context / background maps: precinct level crime statistics; census demographic information (community district and census block); points of interest (subway/bus stops, night clubs, dunkin donuts :) )


### Web Development 

1. Documentation website - primarily to let developers know how they can use the data.
2. Map site - part of number 1 that would feature maps created using data analysis work 
3. User friendly web accessible instance of the complete database. Allow anyone to find/report stops near them. Allow for rich crowd sourced metadata creation on things like NYPD officer demographics. 

     
### Background Reading

 - [NYCLU Report on 2011 Database](http://www.nyclu.org/files/publications/NYCLU_2011_Stop-and-Frisk_Report.pdf) (pdf)
 - [Center for Constitutional Rights](http://ccrjustice.org/ourcases/current-cases/floyd%2C-et-al.-v.-city-new-york%2C-et-al.) Background on how the data became open

### Resources

 - [Original NYPD Database Files](http://www.nyc.gov/html/nypd/html/analysis_and_planning/stop_question_and_frisk_report.shtml) - Note: they are offered only as portable SPSS database files (.por extensions).
 - [NYPD Data Dictionary]() - .zip file with an XLS spreadsheet for each year
 - [NYPD sample UF 250 form and Metadata](data/metadata/Stop-and-Frisk_metadata.pdf)
 - [NYCLU-provided Data Dictionary](http://www.nyclu.org/content/stop-and-frisk-database)

### Mapping

 - [311 Service Requests from 2010 to Present](http://nycopendata.socrata.com/)
 - [NYPD Public Indicators](https://nycopendata.socrata.com/Public-Safety/NYPD-Public-Indicators/yts9-kmw9) - Cleaned up version of their dataset is available [here](/context/nypd-public-indicators.csv)
 - [NYC Geographic Boundary Shapefiles](http://www.nyc.gov/html/dcp/html/bytes/applbyte.shtml), New York City Bytes of the Big Apple
 - [OSM Metro Extracts - New York City](http://metro.teczno.com/#new-york) - Open Street Map Metro Extract for New York City
 - [NYPD Parking Tickets](https://nycopendata.socrata.com/api/file_data/euL63Q3X_Z0TWP4sSuxKWnoLLKs6f7we9a7rej4GD28?filename=Parking%2520Tickets.zip) (.zip file) - MS Access Database offered on NYC Open Data Portal; I have it converted to a SQLite database. 

 
### To do
 - Research NYPD "Clean Halls" program, in effect since 2001, which allows NYPD officers to enter "clean halls" participating buildings to conduct frisks/stops.
