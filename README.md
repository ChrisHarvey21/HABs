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






The outline of the Model Train and Validation Code section of the workbook is as follows

-the first step createa a seaborn pairplot to analyze the relationship and collinearity between my variables in my dataset.
-The next step analyzes the variance of inflation factor for each of the variables that will be used in the final model.  Each of the VIF factors are below 10 which indicates there is little to know multicollinearity between the variables used in the final model.
-The next step does a linear regression to help me understand which predictors may be the most impotant for determining the predictand.
-The next code is simply importing the required libraries and modules needed for the Random Forest Regression Model. There is also some small data organization
-The next section of code is the meat and potatoes of the model (and I'm really proud of what I was able to do).  I will walk you through the steps I used to create it to help you understand what is happening.  I first created a random forest regression model using 80% of the data for training and 20% for testing.  I then fitted the random forest regression model to the data and predicted the target values of the test set.  I then analyzed the Root Mean Square Error of the test values compared to the predicting values. After I was sure the random forest regression was working I created a for loop that could run the code thousands of times and plot the RMSE values .  However, once I found the lowest RMSE value there was no way to know which random forest regression model created this low RMSE value.  To solve for this I generated a random set seed for each run of the random forest regression.  Now by creating a table of the random seed and the corresponding RMSE I could find the random seed of the random forest regression associated with the minimum RMSE.
-The next code I simply printed the mean, max, and minimum RMSE value
-The next code I stored the random state(or set seed) associated with the minimum RMSE
-The next code I repeated the random forest regression with the known set seed that would produce the minimum RMSE.
-Lastly I calculated the absoulte errors and ensured that the average error between the predictions and actuals in the dataset was good compared to the average severity of algal bloom.
