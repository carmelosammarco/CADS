# CADS   
 
[![Build Status](https://travis-ci.com/carmelosammarco/CADS.png)](https://travis-ci.com/carmelosammarco/CADS) [![Build status](https://ci.appveyor.com/api/projects/status/qqy9y9iu1a473qk4?svg=true)](https://ci.appveyor.com/project/carmelosammarco/CADS) [![PyPi](https://img.shields.io/badge/PyPi-Project-yellow.svg)](https://pypi.org/project/CADS/) 

<p align="center">
  <img width="" height="200" src='CADS/DATA/LOGO.gif'>
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

**- TAB-1 : Motuclient data request**

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

![Imgur](https://i.imgur.com/7NsVoa8.png)
![Imgur](https://i.imgur.com/OcKysIV.png)


- TAB-2: FTP data request



