## New York Crime Statistics, 1990-2007

#### *Contains precinct-level crime totals for assaults, violent crimes, burglaries, felonies, forcible rapes, larcenies, motor vehicle theft, murders, property crime, and robberies.*
#### **Note: crime rates per 1,000 residents are also available from the website.**

### Source:[New York City Police Department, United States Census Bureau, Furman Center](http://datasearch.furmancenter.org/)
*New York City Neighborhood Information provided by the Furman Center, retrieved from http://www.furmancenter.org/data/search on 6/19/2012. Terms can be found at http://www.furmancenter.org/data/disclaimer/.*

## Filename: furman-nyc-crime-stats-1990-2007.csv

## Data Processing Notes

 1. Download one of each of the crime indicator csvs Furman data portal has. 
 
 2. Combine them into a single file
 
 	cat * > combined.csv

 3. Standardize 
 
Original Column Name | 1990 Value | 2007 Value 
--- | --- | --- |
Assaults| assaults90 | assaults07 
Violent Crimes | vcrimes90 | vcrimes07 
Burglaries | burg90 | burg2007 
Total Felonies | felonies90 | felonies07 
Forcible Rape | rape90 | rape2007 
Larcenies | larceny90 | larceny2007 
Motor Vehicle Theft | movtheft90 | movtheft07 
Murder | murder90 | murder07 
Property Crime | propcrime90 | propcrime07 
Robbery | robbery90 | robbery07 


4. Replace 

### assaults07

Original | Standardized
--- | --- |
27294.56455 | 27294
138.10245 | 138
167.19305 | 167
174.58255 | 174
196.97205 | 196
249.30905 | 249
208.8679 | 208

### vcrimes07

Original | Standardized
--- | --- |
50452.56455 | 50452
268.10245 | 268
319.19305 | 319
394.58255 | 394
422.97205 | 422
470.30905 | 470
362.8679 | 362
533.39965 | 533
547.24385 | 547
193.5055 | 193
379.7121 | 379
448.43945 | 448

### felonies

felonies06 |felonies06 |  felonies07 | felonies07
Original | Standardized | Original | Standardized
--- | --- | --- | --- |
205522.4768 | 205522 | 199940.5646 | 199940
3655.65952 | 3655 | 3589.10245 | 3589
1774.81328 | 1774 | 1850.19305 | 1850
3190.84272 | 3190 | 3169.58255 | 3169
1444.75884 | 1444 | 1500.97205 | 1500
2987.56996 | 2987 | 3020.30905 | 3020
2272.8584 | 2272 | 2002.8679 | 2002
4207.29732 | 4207 | 4226.39965 | 4226
7881.12152 | 7881 | 7932.24385 | 7932
1743.50404 | 1743 | 1610.5055 | 1610
4311.72828 | 4311 | 4177.7121 | 4177


### larceny06

Original | Standardized
--- | --- |
115363.4768 | 115363
3049.65952 | 3049
1315.81328 | 1315
2445.84272 | 2445
873.75884 | 873
2105.56996 | 2105
1604.8584 | 1604
3115.29732 | 3115
6747.12152 | 6747
1276.50404 | 1276
3538.72828 | 3538

### propcrime2006

Original | Standardized
--- | --- |
153436.4768 | 153436
3373.65952 | 3373
1498.81328 | 1498
2781.84272 | 2781
1078.75884 | 1078
2478.56996 | 2478
1865.8584 | 1865
3655.29732 | 3655
7322.12152 | 7322
1517.50404 | 1517
3845.72828 | 3845
3982.40972 | 3982
1835.96148 | 1835
1009.41596 | 1009

## Issues with the data

 Precinct 22 is missing

 There are a few precincts with no values for certain years. Ideally there would be zeroes where warranted. Precinct 33 is the main one. No data for years 1990-1993. I made the assumption that the four year span of "no crime" for every crime category for Precinct 33 was unlikely. I inserted -9999 in the empty cells. Likewise, for the missing data points for precinct 22, I made the cells have a value of -9999, meant to signify no value, rather than "zero crime."
 
 For the rest of the empty cells, which were not surrounded by series of blanks, I inserted zeroes. **There were no cells with the value of zero in the original dataset.**  
