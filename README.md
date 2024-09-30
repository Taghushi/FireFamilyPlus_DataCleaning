### Overview
To run this code, run the cells in the library section then skip everything and go straight to the Main section. 

You are required to input everything that I list within the file.

Below is how you extract data from FireFamilyPlus



### Finding RAWS Station ID
First we get the Google Earth application. Download the following kml file and load it into Google Earth. You can find the file on this page: https://www.wfas.net/index.php?option=com_content&view=article&id=80&Itemid=483
This is a maps with all RAWS shown on the map.
If we have a region of interest, we can search that area ands see which RAWS we would like to include.
Say we have a fire in Redway California, and there is a powerful wind blowing west to east. Then we can use this to see any RAWS to the east that we can use to see if fire risk is increasing towards this area, or if maybe the fire may be moving in a different direction.
Anyways, the main point of this is to get a station ID,  see the general geography of your region of interest, and find any nearby RAWS that can contribute to the analysis

### Downloading Weather Data (fw13 files)
To collect this RAWS weather data, go to https://famprod.nwcg.gov/cognos11/bi/?perspective=home&folder=.public_folders%2FFAMWEB%2BData%2BWarehouse%2FPublic%2BAccess%2BReports
Go to General Information -> Public Access Reports ->Weather Data Extract -> Historical
From here, you input station id, time frame, and hourly or daily granularity for the weather data.
This will create a csv called FW13.csv. Rename the file to include station_id(location)_time frame_W.fw13. As you can see, we replace the .csv tag with .fw13. The W signifies this is weather data
040421(Redway)_2022-2024_W.fw13
Now, you need to add information about the RAWS location and the fuel-type/biome this RAWS resides in.
Go to Public Access Reports ->Weather Data Extract -> Station Catalog Data extract -> Station Information -Station catalog
Type in the station id and you get the following file Station Information - Station Catalog by Station.csv
Rename the file to be the station_id(location)_time frame_S.txt. As you can see, the .csv tag is replaced with a .txt tag
040421(Redway)_2022-2024_S.txt

### Using this Data in Fire Family Plus
Go to FireFamily Plus and make a new .mbd project
Go to data import, and import fw13 in weather data section and .txt in station information import. 
Next scan you .txt file and look for fuel type. You must manually put this in. On the fuel type portion on the Fire Family Interface:
Note that there have been new fuel models added since 2016. As a result, on rare occasions you may get a fuel type that isn’t in the Fire Family Plus list. In this case, use ChatGPT to find which of the available fuel models are closest to this.

TO GET INPUT DATA:
Go to the R tab and a table is shown. Export this as a csv

TO GET OUTPUT DATA (ERC, BI, IC, and SC):
Go to your Fire Family Plus object and make sure that you change the year parameter to only include one year. If you have data from 2022-2024, then you need to perform this whole process once per year.
Go to Weather/Climatology tab, then input ERC, BI, IC, and SC. Export the following files as txt files and put them into a folder. 
Do this for each year.

IF YOU WANT TO USE MULTIPLE STATIONS
Be sure to do this before you have created the data object. First, upload a second RAWS station fw13 
files and its station metadata in a txt file. The time time period for this station must be the same as your original RAWS station.
Go to Data/SIG on upper bar. Hit new SIG and both stations will pop up. Upload them into the object. Then go to set variable, and you can set the weights of each station!

