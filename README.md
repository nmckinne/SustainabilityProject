# Sustainability Project: Using Sustainability Indicators from the UN's Global Sustainability Goals to Predict Political Stability and Absence of Violence in countries. 

# Background

In 2015, all UN Member States developed a set of 17 Global Sustainability Goals to allow for peace and prosperity globally. The set of goals include those to reduce poverity and inequality, improve health and education, increase economic growth, increase access to clean water and food, and do so in a manner that protects the land and oceans.

Climate change induced floods and droughts, poverity, lack of education, and lack of access to clean water and food all contribute to political tension and violence as people struggle to meet their basic needs. The goal of this project is to see how well each country's status of several sustainable development goals can be used to predict the political stability and absence of violence for each country. Being able to accurately predict political instability can be a matter of national security, but also can allow for measures to be taken to aid and assist those countries that are in danger for instability and provide insight into what conditions promote higher levels of instability. 

The Sustainability Indicators data were obtained from World Bank:https://api.worldbank.org/v2/sources/46/indicators Documentation on the Sustainability Goals can be found here: https://datatopics.worldbank.org/sdgatlas/ The Worldwide Governance Indicators data were also obtained from World Bank: https://datacatalog.worldbank.org/dataset/worldwide-governance-indicators.  Yearly Political Stability and Sustainability Indicator Data were obtained for each available country for a ten-year period from 2010-2020. 

This model is important because it may help predict which countries are headed for periods of political instability and what could be done to help prevent that by understanding which features are the most predictive. 

# Preprocessing

Four primary techniques were used to fill in missing data.  First, missing sustainability indicator data was filled per country by the next closest year if available.  Next, all features with more than 30% of missing data were removed from the dataset.  Additionally, any features that were closely correlated to another feature (>0.8) were removed. Finally, KMeans clustering was used to fill in missing values by cluster using the cluster mean of each feature.

# Results

Several supervised learning models were used to try and predict political instability including Keras and Pytorch Deep Neural Networks, a Random Forest Regressor and an XGBoost Regressor.  The neural networks outperformed other models, with Keras having the lowest mean squared error and highest r-squared score.  The results are shown in the table below.

|Model| RMSE | MAE | R2 Score | Mean Squared Error|
|---|---|---|---|---|
|**Keras DNN**|**0.26**|**-**|**0.92**|**0.07**|
|Pytorch DNN | 0.29 | - | 0.90 | 0.08 |
|Random Forest Regressor | 0.35 | 0.27 | 0.84 | 0.12|
|XGBoost Regressor | 0.38 | 0.28 | 0.81 | 0.14|
|Decision Tree | 0.56 | 0.38 | 0.61 | 0.31|
|Multiple Linear Regression | 0.61 | 0.46 | 0.53 | 0.37|

Analysis of the data shows that the percent of the population over the age of 15 that has an account at a financial instution or with a mobile money service provider is a key feature in this estimation.  Other features that were also important included GDP per capita, threatened mammal species, adolescents out of school and % of land that is forest area. This are important findings in determining what things can play a role in political instability.  




