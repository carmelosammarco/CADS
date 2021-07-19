# CADS   
 
[![Build Status](https://travis-ci.com/carmelosammarco/CADS.png)](https://travis-ci.com/carmelosammarco/CADS) [![Build status](https://ci.appveyor.com/api/projects/status/qqy9y9iu1a473qk4?svg=true)](https://ci.appveyor.com/project/carmelosammarco/CADS) [![PyPi](https://img.shields.io/badge/PyPi-Project-yellow.svg)](https://pypi.org/project/CADS/) 

<p align="center">
  <img width="600" height="200" src='CADS/DATA/LOGO.gif'>
</p>

## Dependencies:

The dependencies required are listed below:

- [x] motuclient>=1.8.1
- [x] ftputil>=3.4
- [x] netCDF4>=1.4.2
- [x] pandas>=0.23.4
- [x] xarray>=0.11.0
- [x] json5>=0.9.1
- [x] h5py>=2.10.0
- [x] h5netcdf>=0.8.0

## Installation

```
pip install CADS
```

When the installation is concluded, just type in the terminal "CADS",press the enter key and the application will pop up.

## Functionalities:

The program is divided into two tabs. The first tab is exslusively used by the **motuclient download mechanisms** while the second tab for the **FTP download data request**. For more information please to read [this article](). Here below a description of the two TABS:

### TAB-1 : Motuclient data request

I can summarise the workflow of this tab as follow:

**1) Filling the form with all the parameters required**
- **Usename**
- **Password**
- **Product :** name of the product 
- **Dataset :** name of the dataset 
- **Long min/max :** Longitude min and max
- **Lat  min/max :** Latidude min and max
- **Depth min/max :** Depth min and max (if it is avaiable)
- **Date start/end :** Defined by dates and time  (**From** [date_start] at [hh:mm:ss] **To** [date end] **at** [hh:mm:ss])
- **Variable-1,2,3 :** Max three variables are allowed. If you want use less just leave the cell empty.
- **File name :** It needs to be typed also if just used by the single file download method)
- **Out-Dir :** output directory where we want to save the data

**2) Generation of the motuclient script**

**3) Download the data**
  
To do that just a click to the more appropriate methods (based on your needs) is required (by Depths, Days, Months, Months&Depths, Yearly (very usefull when requested just a grid point) or just as single file.


<p align="center">
  <img width="" height="900" src='https://i.imgur.com/fxIABmu.png'>
</p>
<p align="center">
  <img width="" height="200" src='https://i.imgur.com/OcKysIVl.png'>
</p>

also is possible to run an interactive terminal session which reproduce what is already described and seen in the GUI interface. To activate this functionality do as descibed here below:

```
from CADS import download
```
Once the module is imported we can call the interactive download process typing;

```
download()
```

At this point the system is going to ask:

- **Username and password**

- **Type of the download** which can be set typing one of the following:

     - **MONTH**: The entire period selected will be downloaded by months
     - **DEPTH**: The entire period selected will be downloaded by depth levels
     - **DAY**: The entire period selected will download as daily files
     - **MONTH&DEPTH**: The entire period selected will be downloaded by months and depth levels
     - **YEAR**: The entire period selected will be downloaded by years. Very usefull just when you want extract a grid point (The --longitude-min = --longitude-min and --latitude-min = --latitude-max).

- **Starting/Ending Time**: If not values as HH:MM:SS are typed then "12:00:00" is going to be used as default value.

- **Motu client script** which is generated by the CMEMS web portal.
Please to copy and paste just from the "--motu" until the end. You can leave untouched   "--out-dir <OUTPUT_DIR> --out-name <OUTPUT_FILENAME> --user <USERNAME.> --pwd <PASSWORD.>" because they were already set previously.

Following an example of the full script generted by the Web-portal:

```
python -m motuclient  --motu http://..... --service-id GLOBAL_ANALYSIS_FORECAST_PHY_001_024-TDS --product-id global-analysis-forecast-phy-001-024 --longitude-min -180 --longitude-max 179.9166717529297 --latitude-min -80 --latitude-max 90 --date-min "2019-04-19 12:00:00" --date-max "2019-04-19 12:00:00" --depth-min 0.493 --depth-max 0.4942 --variable thetao --variable bottomT  --out-dir <OUTPUT_DIR> --out-name <OUTPUT_FILENAME> --user <USERNAME> --pwd <PASSWORD>
```

What you need to use as module's input:

```
--motu http://nrt.cmems-du.eu/motu-web/Motu --service-id GLOBAL_ANALYSIS_FORECAST_PHY_001_024-TDS --product-id global-analysis-forecast-phy-001-024 --longitude-min -180 --longitude-max 179.9166717529297 --latitude-min -80 --latitude-max 90 --date-min "2019-04-19 12:00:00" --date-max "2019-04-19 12:00:00" --depth-min 0.493 --depth-max 0.4942 --variable thetao --variable bottomT  --out-dir <OUTPUT_DIR> --out-name <OUTPUT_FILENAME> --user <USERNAME> --pwd <PASSWORD>
```

The results are going to be downloaded in the file path in which the terminal/command-prompt was at the moment of the data request. Below an example:

<p align="center">
  <img width="" height="400" src='https://i.imgur.com/R982Iaj.gif'>
</p>


### TAB-2: FTP data request

This Tab, as for the previous one, allows to subset the Copernicus marine data products by bounding box, variables, depths /range of depths and time coverage. In addition it is requested the FTP link of the dataset (example: /Core/GLOBAL_REANALYSIS_PHY_001_025/global-reanalysis-phy-001-025-monthly/) which is the key value from which the tool is able to extract from an ad-hoc json database a series of information that allow to identify and correctly select the data prior the download. **At the moment I implemented the database just for the Multi-Year datasets)**. Here below a more detailed description of all the inputs requested:

1. **CMEMS personal login credential**

- Username
- Password

2. **FTP Link of the dataset** (Our key value to extract from the data-base all the parameters needed to make the Tool works) as example below:

```
/Core/GLOBAL_REANALYSIS_PHY_001_025/global-reanalysis-phy-001-025-monthly/
```

For more detailed information about the MULTI YEAR datasets please to look the [MY_datasets](CADS/Database/datasets_MY.pdf) file. The Database that I implemented can be view from [HERE](CADS/Database/CMEMS_Database.json)

3. **Time range**

- Date start
- Date end

Date format as YYYY-MM-DD also in the case of the MONTHLY dataset where the term "DD" can be set to any real value.


4. **Geographic bounding box** (if interested to subset by geographic area)

5. **Variables name** (if interested in extract a selection rather than all)

6. **Depths** information parameter values (if interested in a SINGLE/RANGE  or all the depths)


<p align="center">
  <img width="" height="900" src='https://i.imgur.com/qRzr8GTl.png'>
</p>

Once all the empty and mandatory fields are populated then it is possible to click on the download button. The main python modules used are “ftplib” that make possible to connect into the Copernicus marine data server and then be able to download the data locally (The files are going to be downloaded in the same directory where the tool is run). All the analyses and data processing are performed mainly with xarray and  in real time (while the file or files are downloaded) which helps to preserve the file storage capabilities of the host pc. 

### TAB 3: FTP data request AVS (Automatic variables selection)

This Tab is a prototype of a development that had the aim to make the user able in selecting the variables without type them manually but just selecting them on a screen.

The input needed in this case are the following:

1. **CMEMS personal login credential**

- Username
- Password

2. **FTP Link of the dataset** Our key value to extract from the data-base all the parameters needed to make the Tool works. At the moment the only database avaiable to show that this prototype is working is the following:

```
/Core/BLKSEA_REANALYSIS_PHYS_007_004/sv04-bs-cmcc-cur-rean-m/
```

For more detailed information about the structure of this new Database please to refer to [CMEMS_Databaseselvar.json](CADS/Database/CMEMS_Databaseselvar.json) file. In summary can be pointed out that:

Record example from [DATABASE of TAB-2](CADS/Database/CMEMS_Database.json):

```
"/Core/BLKSEA_REANALYSIS_PHYS_007_004/sv04-bs-cmcc-cur-rean-m/" : ["MY","M","FRONT","01_m-CMCC--RFVL-BSe2r2-BS-b"],
```

Record example from [DATABASE of TAB-3](CADS/Database/CMEMS_Databaseselvar.json):

```
"/Core/BLKSEA_REANALYSIS_PHYS_007_004/sv04-bs-cmcc-cur-rean-m/" : ["MY","M","FRONT","01_m-CMCC--RFVL-BSe2r2-BS-b",”1992-01-01”,”2018-11-01”, ”27.32”, “41.96”, “40.86”, “46.8”, “LDY”, “Variable1”, “Variable2”… ]
 ```

These modification will adress easily the check for:

-Bounding box limits (W-E-S-N)

-Variables selection

-Level Depths (LDY/LDN)

-Date range validation

3. **Time range**

- Date start
- Date end

Date format as YYYY-MM-DD also in the case of the MONTHLY dataset where the term "DD" can be set to any real value.

4. **Geographic bounding box** (if interested to subset by geographic area)

5. **Variables name** (It is possible to select the variables from a list using the "Get-Variables" button, to register the selection just click on "Set-Variables)

6. **Depths** information parameter values (if interested in a SINGLE/RANGE  or all the depths)

## Use the program as a script

 It is possible use the FTP download functionalities in a pure scripting way which allow to be free in look/modify/customise the code. To do so please to:

1. Open the Terminal/command_prompt in the location where you desire download the files or anyway have the script

2. Activate your python environment and import the module:

```
from FTPsubsetMO import script
```

3. Run the function "script" as follow: 

```
script()
```

The above function will allow you to add, in the path folder where you run the command, the files needed  to run the subsetting process in a pure scripting way. "FTPsubsetMO.py" is the only file to modify based on your data request needs. The script's inputs are highlighted with **""**. More information can be found as form of comments in FTPsubsetMO.py script.

## Citing CADS

If you use CADS, even a small part of it, for your research and publications, please consider citing it.

Thanks to all who already did so!


## Dislaimer & Aknoledgement:

The Python tool that is presented here, first in its type inside the Copernicus framework, is a result of personal intellectual work and development, so as such I will not be held responsible for any use you make of it, nor for the results and conclusions you may find using them. Also although I have cross-checked the whole code, I cannot warranty it is exempt of bugs. I would strongly acknowledge the important contribution of the Copernicus scientific community, responsible to gave me the motivation in developing such python applicative. Also I thank Copernicus as the European Union's Earth observation programme and partners (European Space Agency-ESA, the European Organisation for the Exploitation of Meteorological Satellites - EUMETSAT, the European Centre for Medium-Range Weather Forecasts - ECMWF, EU Agencies and Mercator Océan) for the free and open data policy in support of tackling global challenges and providing opportunities for the European Earth observation community for creating jobs and growth.
