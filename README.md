# Reor20 - Radar Precipitation Prediction



<img src="https://static.wixstatic.com/media/09ad8a_9dd7a5b132e545a89304fbee1d78c522~mv2.png/v1/fill/w_1895,h_983,fp_0.50_0.50,q_90,usm_0.66_1.00_0.01,enc_auto/09ad8a_9dd7a5b132e545a89304fbee1d78c522~mv2.png" height="300" width="600" >


## Aim of the project

[Reor20](https://www.reor20.com/) is a company aiming to make flood risk analysis faster and cheaper by using machine learning (ML) instead of the more computationally intensive computational fluid dynamics (CFD).

The objective of this project was to create a ML model that can accurately predict the average rainfall occurring in any watershed of the conterminous United states from rain gauges data.

## Introduction

**What is a watershed?**

<img src="https://streamline.imgix.net/d0137d76-8f43-408c-9b43-aa3e54f62403/dd342d5f-7adf-4256-9935-7d4b22d7db23/Watershed%20diagram.jpg?ixlib=rb-1.1.0&w=2000&h=2000&fit=max&or=0&s=c559560279d62ca63db72008d5950fdc" height="200" width="300" >

A watershed or catchment is an area of land that drains or “sheds” water into a specific waterbody. Each watershed has rain gauges within its borders.

**What are rain gauges?**

<img src="https://thumbs.dreamstime.com/b/meteorology-rain-gauge-garden-rain-against-background-vineyard-meteorology-rain-gauge-garden-193026261.jpg" height="200" width="300" >

Rain gauges are an instrument used by meteorologists and hydrologists to gather and measure the amount of liquid precipitation over a predefined area, over a period of time.

**How do I aim to predict the rainfall from rain gauges data?**

Rain gauges measure precipitation in a specific point of the watershed (point measurement), therefore the company is not sure that its information can be used to find the *average* precipitation over the whole watershed. That is why ML may be a good solution to the problem.

**What is the target variable for this ML problem?**

<img src="https://site.extension.uga.edu/climate/files/2015/08/new-radar-precip-map.jpg" height="200" width="300" >

Radar date is considered to be a reliable source for measuring precipitation. It is used by Reor20 for their flood detection model, but it's a relatively new inventiona and its data doesn't go back in time that much, while rain gauges have been aroung for a much longer time.


## Available data

The company provided the following data:
- watersheds/catchments features: position and geographical/topografical information (size, mean altitude, altitude standard deviation, minimum altitude, maximum altitude, altitude range, altitude variace, number or rain gauges inside its border, centroid latitude, centroid longitude, mean slope, slope standard deviation, minimum slope, miximum slope, slope range)
- rain gauge features: name, elevation and position (latitude and longitude), watershed it belongs to.
- rain gauge measurements: name of rain gauge, date and measurement (in mm of rain)
- radar measurements: name of watershed, date and average measurement over the watershed (in mm of rain)

NOTE: the radar measurements span timewisefrom 2010 to 2021.

## Method

### Exploratory Data Analysis 

At first we performed an exploratory data analysis. To get a feeling of the spacial correlation between the rain gauges and the radat data measurements, I plotted the map of the US with both for two particular days. Below a snipped of the 1st of April 2015 is provided.

<img src="https://raw.githubusercontent.com/mferrari0/Reor20---Radar-Precipitation-Prediction/main/Images/screenshot%202%20second%20of%20april%202015%20-%201.PNG">

We then proceeded to spacially visualize which the watersheds had a higher correlation between rain gauges and radar measurement by calculating the mean average difference between rain gauge and radar measurement over the whole time span (2010-2021). 

![My Image](Images/average_difference.PNG)

There was a clear difference between the plains and the more elevated regions of the US. However, if we divide each average difference by the amount of precipitation, we don't notice any clear separation between regions of the US: the more it rains, the lower the correlation between rain and radar measurement.

![My Image](Images/average_difference.PNG)



