
# Project 2: Ames Housing Data Sale Price Prediction
---
## Overview
One of the big milestones in life is to buy a house. It has become one of the American dreams. Some people purchase houses for investments, others purchase for residence purpose. As a property consultant in Ames Iowa, I am building a house price prediction model using historical property transactions from Ames Iowa and subsequently advise clients on their houses value and whether they should sell their houses based on their comfortable sale prices.

The data consists of two csv files as elaborated below:
- train.csv -> Contains 2051 house transactions with 81 house features consisting of 24 nominal (categorical features with no particular order), 23 ordinal (categorical features with ordering), 15 discrete (countable numerical features) and 20 continuous variables (uncountably infinite numerical features)
- test.csv -> Contains 878 clients' houses with 81 house features ready to be predicted for their houses value

Refer to full data dictionary [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)



## Problem Statement
House price insights are important information that people refer either when they are looking to sell their houses or just to get their property value and hence, their net worth. It plays a very prominent role in determining the owners' next move.

As a property consultant in Ames Iowa, this project aims to provide better visibility and advice for clients regarding to their property value by building a machine learning model for house price prediction. Clients will just need to input their house features to generate proce Apart from that, additional information regarding house features that matter to determine the house price can also be provided.


---
 ## Executive Summary
 For this project, I attempted to create machine learning models using 3 different methods on 3 different regression models:
 #### Method 1
 Using cleaned dataset with all features included in the training set
 #### Method 2
 Using cleaned dataset with features determined from high coefficient value from lasso regression
 #### Method 3
 Using cleaned dataset with Criteria for Model 3 Features to drop:
- Variables with more than 70% threshold of counts in each of the category
- High Colinearity variables (>0.75) and drop variables with lower correlation to Sale Price
- Low correlation variables to Sale Price (<0.4)

Afterwards, modelling was done with 3 different regression, mainly Linear Regression, Lasso Regression and Ridge Regression. Below was the RMSE values obtained from each of the methods and models

|Models| RMSE Model 1 Training Set|RMSE Model 1 Test Set|RMSE Model 2 Training Set|RMSE Model 2 Test Set| RMSE Model 3 Training Set|RMSE Model 3 Test Set|
|---|---|---|---|---|---|---|
|Linear Regression|24302.914044|25570.676220|24401.460914|25561.571177|28071.103928|28521.573545|
|Lasso Regression|24477.559941|25496.935323|24408.411782|25530.561228|28073.188038|28515.111914|
|Ridge Regression|24317.722749|25528.915560|24498.579915|25714.302236|28073.046195|28513.820921|

Based on all 3 models, it can be inferred that:
- All 3 models test data have higher RMSE than those in training data. This means that models are slightly overfitting and cause them to perform slighty worse on the test data
- Referring to test set for all models, lasso regression has been the best performer comparing to other regression models, suggesting that data is not completely linear. Also, lasso regression is able to cover more ranges compared to ridge as the size of coefficients can go close to zero. This will reduce the effect of the noisy columns on the model
- On test set, regularization models are better performers to avoid overfitting as from linear regression. It can be seen that the value of (Test set RMSE - Training set RMSE) for regularization models are tighter than the value of (Test set RMSE - Training set RMSE) in linear regression model

Model 1 is a model with all features included. As features are dropped as shown in model 2 and model 3, the RMSE is slightly higher. Dropping features can reduce the information of the SalePrice prediction as the predictor columns are dropped.
For prediction purposes, i will use Model 2 of Lasso Regression as this model has the lower RMSE compared to model 3. 

While model 1 has slightly lower RMSE compared to the rest of the model, it might need longer time to run the model especially if datasets have too many features.
Also, if test_csv does not have a lot of features, it is necessary to create many new columns and fill in with some values which can induce imputing mistakes or cause the prediction to be more distorted

Top 10 Features based on method 2 model:
- Gr Liv Area
- Overall Qual
- BsmtFin SF 1
- Total Bsmt SF
- Building Age
- Exter Qual
- Kitchen Qual
- Mas Vnr Area
- Mas Vnr Type
- Overall Cond
---
### Conclusions and Recommendations
Below are the key takeaways based om the analysis above:
- Based on some observations, house style with Overall Qual, Gr Liv Area, Building Age, Total Bsmt SF, 1st Flr SF,higher counts of storeys, basement quality, exposure, heating quality have relatively moderate to high correlation to Sale price
- 3 methods (All features, features with relatively strong lasso coefficient, and features after feature engineering) were fitted to 3 regression machine models (Linear, Lasso and Ridge regression) and were tested to compare their performances . Generally, regularization models (Lasso and Ridge) reduce the overfitting as compared to Linear Regression as they have lower RMSE
- Method 2 with lasso modelling has the best model RMSE performance of 25530.56 on test set in training data. Therefore, method 2 lasso modelling were chosen as the model to predict the house sale price
- Achieved a relatively well low bias public score of 29240.47768 and private score of 23019.72643 once fitted to the kaggle DSI-US-11 Project 2 Regression Challenge
- There are a total of 57 features for the final model and top 5 features will be Overall Qual, Gr Live area, exter qual, kitchen qual and total bsmt SF


More importantly, based on model 2, clients may want to invest a certain amount of money to improve the overall quality or improve the ground living area as well as primary features such as exterior conditions,kitchens,etc. Through the model, clients may also focus on other features that are important from model 2 which could return higher ROI with lower cost such as improving garage areas to fit in more cars,etc.

Recommendations will be based on clients' expectations by the minimum price that they would sell e.g. buy price. If predicted price is higher than the minimum price, I will suggest the client to sell the house.

---
