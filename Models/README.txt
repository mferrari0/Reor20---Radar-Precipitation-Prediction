I tested the performance of two models, which I called : 

- Aggregated statistis model
- All rain gauges model

The "all rain gauges" model considers one 2x2 area and, to predict the radar data inside a certain catchment, uses the following features:

*   all of the rain gauge measurements of the area
*   the distance of every rain gauge to the center of the catchment the model is predicting on
*   aggregated statistics regarding the catchment the model is predicting on

Why would I consider the rain gauges outside a catchment to predict the precipitation inside the catchment?
It happens sometimes that the rain gauges data and the radar data are not correlated. This can be caused by the fact the number rain gauges is not enough to
capture the precipitation on the entire catchment. By considering the rain gauges of the entire area, I was hoping for the model to learn the general pattern
of a precipitation.
The model was trained on varoius areas of the US south-east and performs with an average score of around 0.5 R2. To obtain a decent score, a sufficient 
number of colums and rows needs to be used. Every area has a different number of rows and colums because the number of rain gauges changes and the number of 
measurement days also changes.
What I would have tried, if I had the time, was to combine the dataframes of different areas, instead of training with the data belonging to one
single area. This way, the algorithm would have more rows to train on.
The not so obvious decision is on how to make this concatenation, since every area has a different amount of rain gauges.


The "aggregated statistics" model considers one 2x2 (latitude and longitude units) area and, for each day, computes some aggregated statistics 
about the catchment it is predicting on and the whole 2x2 area. As aggregated statistics I used: 
*   Minimum
*   Maximum
*   Mean
*   Median
*   Quantiles (every 10%)
The model has been trained on multiple 2x2 areas and concatenating every area's dataframe into a unique one, obtaining a dataframe with 2M rows. 
The final score was not impressive: around 0.30 R2.
More details can be found inside the notebook.


What I also would have tried, is to use a similar approach to what was tried in "Deep Learning for Precipitation Estimation from
Satellite and Rain Gauges Measurements". Using a CNN and giving as input the rain gauge measurements and catchment features (altitude, slope etc.), 
it may be possible to estimate the radar measurement for each catchment.

