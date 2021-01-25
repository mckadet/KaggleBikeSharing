# KaggleBikeSharing

## Introduction
There are now over 500 bike-sharing programs around the world that allow users to rent a bike from one location and return it to another. The purpose of this project was to analyze both historical usage patterns and weather data to predict bike rental demand in the Capital Bikeshare program in Washington, D.C. 

## Descriptions
BikeSharing Script.R is a file containing the R code used for cleaning, analyzing, and modeling the data and ultimately producing prediction metrics for rental demand in D.C. 

## Preparing the Data
The data comes from bike rental data recorded over a two-year period in the Capital Bikeshare program. The response variable for this dataset was count, or the number of bicycles rented at that particular time. Because a datetime was included with each count, feature engineering was done to obtain an hour, month, and year explanatory variable for analysis. In addition, other explanatory variables such as whether or not it was a holiday and what the weather was like were converted to factors where appropriate. Target-encoding was used to transform the season variable, making for easier interpretability of the results.

## Methods
As aforementioned, the goal of this project was to predict the number of bikes that would be in demand in D.C. To do so, several modeling techniques were considered with various tuning parameters, sets of explanatory variables, and types of regression.

### Model 1
This model was a random forest regression model with explanatory variables count, season, humidity, atemp, and holiday. I used mostly default tuning parameters with repeated cross validation as a primary method for model validation. The specific random forest model was the ranger model specification from the caret library. Target encoding with season as the explanatory variable in a linear model was used for encoding the season variable.

### Model 2
For this model, an extreme gradient boosting tree regression model with default hyper-parameters and the same explanatory variables as before were used. This model already performed better than the random forest, so it was used as a primary candidate for prediction.

### Model 3
This model was also an extreme gradient boosting tree model but incorporated a log transformation of the response variable count. Feature engineering was also done to add a year, month, and hour explanatory variable to the model. Also, enhanced target encoding was done by adding several more explanatory variables to the linear model used for encoding the season variable.

# Results
The third model, an extreme gradient boosting tree model, performed by far the best out of three for being able to correctly predict what the demand would be for renting bicycles in Washington, D.C.
