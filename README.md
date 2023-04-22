# SC1015 Mini Project -- HDB Resale Flat Price Prediction 

## Tutorial Group: A134
### *Members: Shingamu Sai Ajay, Siah Yee Long, Sally Ngui Yu Ying*

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

After that, we did a train-test-split and ran the model. We obtained the RMSE of 34311, R-squared score of 0.957.

After tuning the hyperparameters of our model, we found that Grid Search produced a higher accuracy of 0.962.

# 5. Results

| ML Model      | Model Accuracy   | Tuned Model Accuracy | 
| ------------- | ---------------- | -------------------- |
| SVR           | 0.523            | 0.922                |
| Random Forest | 0.956            | 0.957                |
| XGBoost       | 0.957            | 0.962                |

**Model Recommendation**: XGBoost

Since XGBoost produces the highest accuracy after hyperparameter tuning, we have chosen it to be the best model in predicting resale prices of HDB flats.

# 6. Conclusion
In conclusion, we have looked at certain factors that might affect resale prices. Through this process, we have learnt how to use API to find additional property and geographical features, PowerBI for analytics visualisation, machine learning models such as SVR and XGBoost and how to tune the hyperparameters of the model to improve their accuracy.

As we were doing this project, we realised that Data.gov.sg updated their dataset and added the most recent information for April 2023. Hence, we decided to use it to test the robustness of our model. After using the GBRT to tune our model, we have found the RMSE value of 40165 and accuracy score of 0.947, which shows that our model is highly accurate in predicting future resale prices.

However, it is possible that there are other factors might also affect resale price, such as economic conditions, government intervention, crime rate. This could be an area for future research that we believe will enable better predictions of resale prices and allow future buyers to make more informed decisions before purchasing.

<details>
<summary>Project Video</summary>
https://youtu.be/iR6RlE59T-U
</details>
 
<details>
<summary>References</summary>
https://data.gov.sg/dataset/resale-flat-prices
 
https://slidesgo.com/theme/real-estate-marketing-plan#search-Real+Estate&position-1&results-28​

https://www.channelnewsasia.com/singapore/jurong-point-subway-snatch-theft-illegal-remittance-court-jail-3412236​

https://blog.seedly.sg/whats-driving-up-singapore-property-prices/​

https://upload.wikimedia.org/wikipedia/commons/f/f3/Pinnacle%40Duxton%2C_Singapore_-_20100101.jpg ​

http://souravsengupta.com/​

https://static.mothership.sg/1/2019/04/Screen-Shot-2019-04-28-at-6.39.32-PM.png ​

https://www.asiaone.com/money/4-room-bendemeer-hdb-resale-flat-sold-1m ​

https://www.asiaone.com/money/record-breaking-hdb-resale-maisonettes-toh-yi-drive-flat-sold-13m-jurong-east-flat-sold-1m ​

https://www.straitstimes.com/singapore/housing/more-hdb-resale-flats-sold-for-at-least-1m-in-first-9-months-of-2022-than-in-whole-of-2021

https://towardsdatascience.com/building-a-one-hot-encoding-layer-with-tensorflow-f907d686bf39 

https://towardsdatascience.com/4-categorical-encoding-concepts-to-know-for-data-scientists-e144851c6383​

https://www.researchgate.net/figure/The-architecture-of-Gradient-Boosting-Decision-Tree_fig2_356698772​

https://www.researchgate.net/figure/Comparison-between-a-grid-search-and-b-random-search-for-hyper-parameter-tuning-The_fig2_341691661 ​

https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.gormanalysis.com%2Fblog%2Fgradient-boosting-explained%2F&psig=AOvVaw24T8Kt8qhohPWlI8xN-usc&ust=1681810770505000&source=images&cd=vfe&ved=0CA4QjRxqFwoTCNCz4cDPsP4CFQAAAAAdAAAAABAD ​

https://www.google.com/url?sa=i&url=https%3A%2F%2Fthenounproject.com%2Fbrowse%2Ficons%2Fterm%2Fsvm%2F&psig=AOvVaw3WwKPVtBH7vL0n7-n5pUAQ&ust=1681810719070000&source=images&cd=vfe&ved=0CA4QjRxqFwoTCJiXhKjPsP4CFQAAAAAdAAAAABAD ​

https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn.windowsreport.com%2Fwp-content%2Fuploads%2F2019%2F07%2FFix-power-bi-cant-find-app.jpg&tbnid=nkjYiN1RvGgm-M&vet=12ahUKEwjaiLuUz7D-AhVVFbcAHV7jDLoQMygEegUIARDSAQ..i&imgrefurl=https%3A%2F%2Fwindowsreport.com%2Fpower-bi-cant-find-app%2F&docid=QLf7bmj7RoiUqM&w=1200&h=1200&q=powerbi%20icon&ved=2ahUKEwjaiLuUz7D-AhVVFbcAHV7jDLoQMygEegUIARDSAQ ​

https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn-icons-png.flaticon.com%2F512%2F6681%2F6681415.png&tbnid=k7umq_tdqlVlGM&vet=12ahUKEwjAgfDwz7D-AhUL83MBHdkCB0AQMygMegUIARDcAQ..i&imgrefurl=https%3A%2F%2Fwww.flaticon.com%2Ffree-icon%2Fsetting_6681415&docid=YTQ_sUULeZdjGM&w=512&h=512&q=hyperparameter%20tuning%20icon&ved=2ahUKEwjAgfDwz7D-AhUL83MBHdkCB0AQMygMegUIARDcAQ ​

https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn-icons-png.flaticon.com%2F512%2F3310%2F3310624.png&tbnid=QrTWbWNeEizkqM&vet=12ahUKEwjNi8a507D-AhVT1HMBHQB4DJoQMygAegUIARDJAQ..i&imgrefurl=https%3A%2F%2Fwww.flaticon.com%2Ffree-icon%2Feconomic_3310624&docid=N9YYgIEtLY6C9M&w=512&h=512&q=economic%20conditions%20icon&ved=2ahUKEwjNi8a507D-AhVT1HMBHQB4DJoQMygAegUIARDJAQ ​

https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn-icons-png.flaticon.com%2F512%2F8040%2F8040938.png&tbnid=yGuKbIW36FAu4M&vet=12ahUKEwiKhY7J07D-AhUK-HMBHbEkCckQMygCegUIARDOAQ..i&imgrefurl=https%3A%2F%2Fwww.flaticon.com%2Ffree-icon%2Fpolicy_8040938&docid=zyiocACpzWyrnM&w=512&h=512&q=government%20policies%20icon&ved=2ahUKEwiKhY7J07D-AhUK-HMBHbEkCckQMygCegUIARDOAQ​

https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn-icons-png.flaticon.com%2F128%2F4321%2F4321395.png&tbnid=XCKuEzUa4gYkLM&vet=12ahUKEwj0trfV07D-AhXOBbcAHdDzANgQMygJegUIARDeAQ..i&imgrefurl=https%3A%2F%2Fwww.flaticon.com%2Ffree-icons%2Fcrime&docid=qYj3LFXwIlQoAM&w=128&h=128&q=crime%20rate%20icon&ved=2ahUKEwj0trfV07D-AhXOBbcAHdDzANgQMygJegUIARDeAQ​

https://levelup.gitconnected.com/random-forest-regression-209c0f354c84 
</details>
