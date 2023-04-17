# we-love-SC1015-please-give-A

## Tutorial Group: A134
### *Members: Shingamu Sai Ajay, Siah Yee Long, Sally Ngui Yu Ying*

- [x] Data preparation
    - Added features into HDB resale dataset:
        1. Get coordinates and address of flat sold
        2. Get all MRT stations info and created "nearest MRT" and "distance to nearest MRT" feature
        3. Get all primary and secondary schools info and created "schools within 1km" feature
        4. Get all shopping malls info and created "nearest mall", "mall nearest distance", "mall within 500m" and "mall within 1km" feature
        5. Get all hawker centres info and created "hawkers within 1km" feature
        6. Connected to Google Map's API to get "travel time to RP (Raffles Place MRT Station) in minutes" feature
- [ ] EDA
- [ ] Analytics visualisation (perhaps we can do this on PowerBI
- [ ] Machine learning
- [ ] Video

# 1. Problem Formulation
**Our Dataset**: [Resale Flat Prices from Data.gov.sg](https://data.gov.sg/dataset/resale-flat-prices)

**Our Motivation**: Affordable housing in Singapore has been a hot topic in recent times, especially with the boom in property prices during the COVID-19 pandemic. During the pandemic, construction of built-to-order flats in Singapore were put on a halt, and the rise in raw material cost following that only exacerbated the situation. This pushed many young couples to seek resale flats, and with high demand and low supply of public housing, prices of HDB resale flats have skyrocketed. This caused us to question: What are the possible factors that affect the prices of resale flats? How can we predict the prices of HDB resale flats for future buyers, including ourselves, so that we can make more informed decisions?

**Our Question**: How can we predict the prices of HDB resale flats given property and geographical features?

# 2. Data Preparation and Cleaning
With our current dataset, we wanted to dig deeper into its geographical location, and how they may affect the resale price of the flats. We start by extracting the longitude and latitude coordinates by using the one map API. With the geographical coordinates, we consulted experienced homebuyers and researched on what people think are important factors when buying a house. We consolidated these factors: distance to nearest MRT and mall, number of schools and hawkers within 1km, as well as travel time to Raffles Place MRT, where most offices are located, assuming this is their workplace.

We added these features into the HDB resale dataset: 
1. Get coordinates and address of flat sold
2. Get all MRT stations info and created "nearest MRT" and "distance to nearest MRT" feature
3. Get all primary and secondary schools info and created "schools within 1km" feature
4. Get all shopping malls info and created "nearest mall", "mall nearest distance", "mall within 500m" and "mall within 1km" feature
5. Get all hawker centres info and created "hawkers within 1km" feature
6. Connected to Google Map's API to get "travel time to RP (Raffles Place MRT Station) in minutes" feature

# 3. Exploratory Data Analysis
We conducted EDA on numerical and categorical variables. We found that the two factors that have the highest correlation with resale price are floor area and travel time to RP in minutes. 

We found that resale price and floor area are positively correlated, which is expected as larger floor area suggests a larger flat they are paying for. 

The resale price and travel time to Raffles Place MRT in minutes are negatively correlated, which is possibly because people want a shorter travel time to the central business district for greater convenience, where most of the offices are located at.

# 4. Machine Learning
After finding some possible factors that might affect the HDB resale price, we can attempt to predict the resale price of a given flat for future buyers using machine learning models. The models that we have chosen are Support Vector Regression (SVR), Random Forest Regression, and XGBoost.

## 4A. Support Vector Regression
Support Vector Regression (SVR) works by finding a hyperplane that maximizes the margin between the data points and the hyperplane while still fitting the data within a certain tolerance level.

We first one-hot encode categorical data. Then, we train-test-split the data and scaled numerical features before training our model with a basic linear model. We achieved an accuracy score of 0.523 and RMSE of 114510.

After tuning the hyperparameters of our model by using Random Search and Grid Search. We found that Grid Search gave a higher accuracy of 0.922.

## 4B. Random Forest Regression
Random Forest Regression uses ensemble learning method for regression and combines predictions from multiple machine learning algorithms to make a more accurate prediction than a single model. We can use this model to predict resale price.

We dropped columns that are not needed and conducted label-encoding for categorical variables. After doing a train-test-split and running the random forest regression model, we found that the model accuracy is 0.956 and RMSE is 35164.

We found that the most important variables that affect resale price are floor area in sqm, travel time to Raffles Place MRT and remaining lease.

After tuning the hyperparameters of our model, we found that Random Search produces a slightly higher model accuracy of 0.957.

## 4C. XGBoost
Gradient Boosted Regression Trees (GBRTs) combine the power of decision trees and gradient boosting to improve the accuracy of predictions. They are widely used in regression problems, where the goal is to predict a continuous target variable. 

We cleaned up the data by dropping a few variables that are unnecessary. Then we label-encoded the categorical variables. 

After that, we did a train-test-split and ran the model. We obtained the RMSE of (value), R-squared score of (value) and Explained Variance Score of (value).

After tuning the hyperparameters of our model, we found that Grid Search produced a higher accuracy of (value).

# 5. Results

| ML Model      | Model Accuracy   | Tuned Model Accuracy | 
| ------------- | ---------------- | -------------------- |
| SVR           | 0.523            | 0.922                |
| Random Forest | 0.956            | 0.957                |
| XGBoost       | Test2            | Test3                |

**Model Recommendation**: XGBoost

# 6. Conclusion
Other factors might also affect resale price: Economic conditions, government intervention, crime rate


Useful Links:
- [EDA visualisations](https://www.data-to-viz.com/)
- [EDA chart names](https://ft-interactive.github.io/visual-vocabulary/)
- [Data science map](https://coggle.it/diagram/XIpNSBc5AmfW0P_J/t/data-science-map)
