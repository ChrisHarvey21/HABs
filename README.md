# HABs data Project 
determine the likelihood and severity of an algal bloom occuring based on precipitation and temperature information

For the first data set:
-Data from NYSDEC website at url "https://nysdec.maps.arcgis.com/apps/webappviewer/index.html?id=692b72ae03f14508a0de97488e142ae1"
-To downlaod the data first select HABs status
-Next filter by your lake of interest.  Skaneateles Lake ID code is 0707SKA0193
-Finally click options and export to CSV

For the second data set:
-The site used for data gathering is "http://climod2.nrcc.cornell.edu/"
-Next proceed to the heading "product selection" and choose "single station" and "Daily Data Listing"
-Next click on the tab Options Selections and choose HTML, the range of dates, and the parameters you want.
-For this script I chose HTML, 2016-11-01 to 2022-11-03, max temp, min temp, average temp, and precipitation
-Lastly choose your location. I selected Syracuse Hancock Airport
-Click Go

The next section organizes, merges, and filters the data.  
  The end result is a pandas dataframe containing all the instances of algal blooms
  and the correspodning precipaiton and temperature data.
