# Data Science at Scale Final Project

In this project, our team of 4 were tasked with creating an end-to-end data intensive application that tracks the inventory of bikes and available docks at a given station with the Citibike Bike Sharing system in NYC. Our team was assigned station 4. To complete this project, you must apply the skills you have learned in DSCC 202-402 Data Science at Scale. This sort of forecasting application could be the basis of how an application like Bike Angels runs (https://citibikenyc.com/bike-angels) and helps keep the system running smoothly with the
help of Data-Intensive Applications and Human participation.

The application has 4 components:
1. Extract Transform Load (ETL)
   All the data available was maintained in a raw data directory in DBFS. In addition, a set of delta tables is updated every 30 minutes by an automated job that runs on the platform. We developed an ETL pipeline that extracted and stored the information about the station and weather in Bronze tables with defined schemas. We utilized spark streaming jobs to continually load real-time data into the tables as well as Partitioning and Z-ordering to optimize delta tables for our application. 
3. Exploratory Data Analysis (EDA)
   After the necessary data were collected, we conducted exploratory data analysis to answer some key questions to understand the usage of bikes at our station, such as
- The monthly trip trends for our assigned station
- The daily trip trends for our given station
- How a holiday affected the daily (non-holiday) system use trend
- How weather affected the daily/hourly trend of system use?
4. Modeling and MLOps
  Considering historical data, we built a forecasting model that infers net bike change at our station by the hour. We registered our model at the staging and production level within the Databricks model registry. we also stored artifacts in each MLflow experiment run to be used by the application to retrieve the staging and production models. And we tuned the model hyperparameters using the MLflow experiments and hyperparameter scaling (spark trials, hyper-opts).
5. Application
  Finally, we created a notebook that displayed the following
- Current timestamp when the notebook is run 
- Production Model version
- Staging Model version
- Station name and a map location (marker)
- Current weather (temp and precip)
- Total docks at this station
- Total bikes available at this station
- Forecast the available bikes for the next 4 hours
- Highlight any stock out or full station conditions over the predicted period
- Monitor the performance of your staging and production models using an appropriate residual plot that illustrates the error in the forecasts


