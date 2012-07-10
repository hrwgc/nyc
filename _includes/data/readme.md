# Resources

*Note:This project is a continuation of previous work, see [here](http://wiki.datawithoutborders.cc/index.php?title=Project:Current_events:NYC_DD:NYCLU) for work done at Data Dive NYC*

*It was also inspired by Naomi Robbin's work with [crime and stop and frisk data](http://www.forbes.com/sites/naomirobbins/2012/03/23/visualizing-stop-and-frisk-and-murder-rates-in-new-york-city/).*

## NYPD Budget Data

[Mayor’s Fiscal 2013 Preliminary Budget](http://council.nyc.gov/html/budget/PDFs/2013/056%20Police%20Department.pdf), see breakdown sections, especially p. 27

# Crime Data

## [Crime Database](http://www.ucrdatatool.gov/index.cfm) Table Builder

### Grab NYC Precinct-level Crime Statistics

#### Problem 1
 - NYPD offers [crime data as pdf reports](http://www.nyc.gov/html/nypd/html/crime_prevention/crime_statistics.shtml) for each precinct as well as monthly one-page [citywide crime reports](http://www.nyc.gov/html/nypd/downloads/pdf/crime_statistics/cscity.pdf).
 - PDF reports have structure, but need to be processed to allow for cross precinct and across-time comparisons. 
 
#### [Solution](https://github.com/hrwgc/nyc/blob/gh-pages/data/data-processing.md)

#### [Finished dataset of NYPD precinct-level crime data](https://github.com/hrwgc/nyc/blob/gh-pages/data/nypd-crime-stats-precinct-historical.csv)
#### [Data Dictionary for NYPD precinct-level crime data](https://github.com/hrwgc/nyc/blob/gh-pages/data/crime-pdfs/readme.md)


## FBI Uniform Crime Reports

*For Reference: [Uniform Crime Reports Data Dictionary/Handbook](http://www.fbi.gov/about-us/cjis/ucr/additional-ucr-publications/ucr_handbook.pdf)*

- [Uniform Crime Report for 2011](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2011)
- [Uniform Crime Report for 2010](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2010)
- [Uniform Crime Report for 2009](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2009)
- [Uniform Crime Report for 2008](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2008)
- [Uniform Crime Report for 2007](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2007)
- [Uniform Crime Report for 2006](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2006)
- [Uniform Crime Report for 2005](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2005)
- [Uniform Crime Report for 2004](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2004)
 - Note: This is not the actual UCR Report, but just the table of contents.
- [Actual Report for 2004](http://www2.fbi.gov/ucr/cius_04/documents/CIUS2004.pdf)
- [Uniform Crime Report for 2003](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2003)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 2002](http://www2.fbi.gov/ucr/cius_02/html/web/index.html)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 2001](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2001)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 2000](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/2000)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 1999](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/1999)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 1998](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/1998)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 1997](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/1997)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 1996](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/1996)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 
- [Uniform Crime Report for 1995](http://www.fbi.gov/about-us/cjis/ucr/crime-in-the-u.s/1995)
 - Note: This is not the actual UCR Report, but just the table of contents. The actual report appears to be missing. 

## Other relevant Data Sources

1. [NYPD Public Indicators](https://nycopendata.socrata.com/Public-Safety/NYPD-Public-Indicators/yts9-kmw9)
 - Cleaned up version of their dataset is available [here](https://github.com/hrwgc/nyc/blob/gh-pages/data/nypd-public-indicators.csv)
2. [NYC Geographic Boundary Shapefiles](http://www.nyc.gov/html/dcp/html/bytes/applbyte.shtml), New York City Bytes of the Big Apple
3. [OSM Metro Extracts - New York City](http://metro.teczno.com/#new-york) - Open Street Map Metro Extract for New York City
4. [NYPD Parking Tickets](https://nycopendata.socrata.com/api/file_data/euL63Q3X_Z0TWP4sSuxKWnoLLKs6f7we9a7rej4GD28?filename=Parking%2520Tickets.zip) (.zip file) - MS Access Database offered on NYC Open Data Portal; I have it converted to a SQLite database. 

