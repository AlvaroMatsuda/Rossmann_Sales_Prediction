# Rossmann Sales Prediction

![image](https://user-images.githubusercontent.com/72954917/119910864-7bb82a80-bf2e-11eb-885c-01168af8cbae.png)

# Context

**Obs:** The following context is not real. I made up this context to make the project closer to a real life problem.

**Company name:** Rossmann

**Product/Service:** Rossmann is a drugstore chain that operates in 7 European Countries with over 3.000 stores.

**Business Model:** Rossmann is a traditional drugstore that operates with physical stores. So the metrics that are most important for this type of business model is average ticket and number of customers.

**Problem:** Rossmann came up with a new visual identity and the stores will need to be reformed to match that.

The CFO asked store managers to predicting their daily sales for up to six weeks in advance, such that he can plan the allocation of the budget necessary to each store to be reformed.

**Proposed Solution:** Use machine learning to predic the daily sales up to six weeks in advance for each store, so that the CFO can use the sales prediction as portion of the budget necessary to do the reform of the store.**

**Deliverables:** Build an API on Telegram Bot that allow the CFO to request the prediction on his cellphone of each store given an ID store.

- The data can be found here: https://www.kaggle.com/c/rossmann-store-sales

# Solution Strategy

- 1. **Check Data (Data Description):** Use basic statistics to have a first look at the data and check and fill NA values.
- 2. **Feature Engineering:** Combine and derive new variables based on the existing ones on the data to better understand the behavior of the sales.
- 3. **Exploratory Data Analysis (EDA):** Explore the data to better understand it and the business, and what variables is/isn't correlated to sales.
- 4. **Data Preparation:** Prepare data to be used by Machine Learning algorithms 
- 5. **Feature Selection:** Select the most significant variables to train models
- 6. **Machine Learning Moddeling:** Train machine learning models
- 7. **Hyperparameter Fine Tunning:** Tunning moldel with better result
- 8. **Translate the result into business:** Convert machine learning performance into business results
- 9. **Deploy:** Deploy model to production.

# Top Insights
- **Hypothesis:** Stores with near competitors should sell less.
  -  **FALSE** Stores with near competitors sell more.

![image](https://user-images.githubusercontent.com/72954917/120121760-a77c2000-c17b-11eb-990e-fa636f4b85f2.png)


-  **Hypothesis:** Stores with longer active promo should sell more.
  -  **FALSE** Stores with longer active promo sell less, after certain period of time

![image](https://user-images.githubusercontent.com/72954917/120121828-0b9ee400-c17c-11eb-8204-6019022c7f1a.png)


- **Hypothesis:** Stores should sell less on school holidays.
  - **FALSE** Stores sell more on school holidays

![image](https://user-images.githubusercontent.com/72954917/120122694-adc0cb00-c180-11eb-8a48-4ce25c3ad96b.png)


# Machine Learning Performance
- To have a benchmark for comparisson I used a mean model
- I used 4 Machine Learning models:
  - Linear Regression
  - Lasso Linear Regression
  - Random Forest Regression
  - XGBoost Regression

- To evaluate the performance of the models I calculated 3 metrics: RMSE, MAE and MAPE
![image](https://user-images.githubusercontent.com/72954917/119747241-ac359100-be68-11eb-8eee-b99c24586d4c.png)

- With cross validation the metrics are: 

![image](https://user-images.githubusercontent.com/72954917/119752441-6c27db80-be73-11eb-89ed-8c25c7e8c729.png)

- Despite XGBoost Regression having the worst performance, after Fine Tunning it was the model with the best performance. So we are going to select XGBoost as the final model

![image](https://user-images.githubusercontent.com/72954917/119761746-c3817800-be82-11eb-8baf-d4f45754b33d.png)

![image](https://user-images.githubusercontent.com/72954917/119765541-de0b1f80-be89-11eb-8316-984cf87dccbe.png)


# Business Results
![image](https://user-images.githubusercontent.com/72954917/119905379-8a004980-bf22-11eb-9509-fb82c9e4dde0.png)

- As we can see on the graph above, there are some stores that have bigger errors than the average of 11%.
- To have a better look at the result of the model into the business, I calculated the best and worst scenario accordingly to MAE (Mean Absolute Error).
  -  To calculate the worst scenario I took the predicted sales for each store and subtract it by the MAE for that store.
    -  predicted sales of n store - MAE of n store
  -  To calculate the worst scenario I took the predicted sales for each store and sum it by the MAE for that store.
    -       -  predicted sales of n store + MAE of n store
  - After that I summed all the worst scenarios for all stores and the best scenarios, generating this table:
![image](https://user-images.githubusercontent.com/72954917/119906223-2e36c000-bf24-11eb-8186-1f9cc9a01471.png)

  - As we can see all stores will sell:
    - On the worst scenario: R$ 283,102,898.04
    - On the best scenario:  R$ 284,563,051.71

![image](https://user-images.githubusercontent.com/72954917/119906941-9cc84d80-bf25-11eb-9f90-3f98a36b3bb7.png)

- In the graph above we can see that the predictions are close to the real values, thus indicating that we can have some level of trust of the predictions.

- With the graph below we can see if predictions are higher or lower than the real values overall.
![image](https://user-images.githubusercontent.com/72954917/119907223-31cb4680-bf26-11eb-89b1-f36f045f44fb.png)

# Conclusions
The goal of this project was to predict sales of all Roassmann's stores up to 6 weeks in advance because the CFO want to know how to allocate the budget for each store to reform their stores to match their new visual identity. To make the prediction I got a dataset of the company and analysed it to have a better understanding of the data and the business (explore the data to see what impacts sales) and used machine learning model to make the predictions of the sales. The performance of the model has as error of 11% in average. With that I calculated the best and worst scenario for each store so the CFO can have a better plan to allocate budget for each store.

Finally, I deployed the model to production where the CFO can access the prediction on his phone through a Telegram Bot where you need to send a message with the store ID and the bot will respond with the predicted sales up to 6 weeks for the given store.


# Lessons Learned
- The steps of a Data Science project and the why's of each step
- How to better handle date type variables;
- The importance of EDA and the benefits of it (have a better understand of the data and the business);
- The importance of preparing the data to be used by ML models. (most algorithms are based on normal distribution)
- The importance of cross validation
- How to interpret regression models through MAE, MAPE, RMSE and how they are calculated.
- The importance of translating the performance of the model to business performance and how to do it.
- How to deploy model to production.

# Next Steps to Improve
- Improve the code
- Understand better how to deploy a model
- Understand better the algorithms of de models
- Improve the Telegram Bot to send not only the predicted sales but also the best and worst scenario
