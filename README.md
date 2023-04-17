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
**Our Dataset**: 

**Our Motivation**: Affordable housing in Singapore has been a hot topic in recent times, especially with the boom in property prices during the COVID-19 pandemic. During the pandemic, construction of built-to-order flats in Singapore were put on a halt, and the rise in raw material cost following that only exacerbated the situation. This pushed many young couples to seek resale flats, and with high demand and low supply of public housing, prices of HDB resale flats have skyrocketed. This caused us to question: What are the possible factors that affect the prices of resale flats? How can we predict the prices of HDB resale flats for future buyers, including ourselves, so that we can make more informed decisions?

**Our Question**: How can we predict the prices of HDB resale flats given property and geographical features?

# 2. Data Preparation and Cleaning


# 3. Exploratory Data Analysis


# 4. Machine Learning
After finding some possible factors that might affect the HDB resale price, we can attempt to predict the resale price of a given flat for future buyers using machine learning models. The models that we have chosen are Support Vector Regression (SVR), Random Forest Regression, and XGBoost.

## 4A. Support Vector Regression


## 4B. Random Forest Regression
Random Forest Regression uses ensemble learning method for regression and combines predictions from multiple machine learning algorithms to make a more accurate prediction than a single model. We can use this model to predict resale price.

After running the random forest regression model, we found that the model accuracy is 0.956.

We found that the most important variables that affect resale price are floor area in sqm, travel time to Raffles Place MRT and remaining lease.

To achieve better predictions, we tuned the hyperparameters of our model using Random Search and Grid Search and found that Random Search produces a slightly higher model accuracy of 0.957.

## 4C. XGBoost



# 5. Results

| Model         | Model Accuracy   | Tuned Model Accuracy |
| ------------- | ---------------- | -------------------- |
| SVM           | 0.523            | 0.922                |
| Random Forest | 0.956            | 0.957                |
| XGBoost       | Test2            | Test3                |



# 6. Conclusion
Other factors might also affect resale price: Economic conditions, government intervention, crime rate


Useful Links:
- [EDA visualisations](https://www.data-to-viz.com/)
- [EDA chart names](https://ft-interactive.github.io/visual-vocabulary/)
- [Data science map](https://coggle.it/diagram/XIpNSBc5AmfW0P_J/t/data-science-map)
