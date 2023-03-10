# Customer Churn Rate for E-commerce Company

<img src="images/CustomerSerivce.gif" width="750" align="center">

## Business Problem

When we lose customers, we lose money. I have been tasked by the company heads to predict which customers are at risk of leaving (churning) and taking their business elsewhere. 

Taking into account a range of features, like membership status and website usage, I use machine learning models to successfully predict which customers the company should re-target to retain business.

## Overview

The data comes from the ["Customer Churn"](https://www.kaggle.com/datasets/undersc0re/predict-the-churn-risk-rate) dataset, posted by Pawan Trivedi on Kaggle. I tried Decision Trees, Logistic Regression, K Nearest Neighbors, Random Forest, and finally XGBoost Classifier to find the best model for prediction. XGBoost Classifier was the best of the lot, succesfully predicting a little over 94% of targets in the test data. From there, I used the model to indicate the most important features, which were membership_category, village region, and customer care feedback.

Based on all of this, I recommend the company uses XGBoost Classifier moving forward to predict customer churn risk. I also suggest using membership category, wallet points, and customer care feedback to re-target customers.

There is overfit present in this model and some of the others, which can be solved by improving the data and increasing the amount of data. I had to cut about a quarter of the data out of the analysis, so possibly determining why the values were negative would be a good start.

## Data Understanding

The dataset contains columns focusing on customer site usage, customer transactions, customer demographics like age, gender, location, preferred device and internet type, and more.

I began with some exploratory data analysis. We have an even split in our data between class 0 (not at risk of churn) and class 1(at risk of churn).

<img src="images/datasplit.png" width="750" align="center">

EDA further revealed that there are six types of membership. The majority of customers either hold "basic" membership or no membership at all. These categories are also most at risk of churn. "Platinum" members, by contrast, have no risk of churn.

<img src="images/membershipcategories.png" width="750" align="center">

Points also seemed to be a solid indicator of the target, showing key areas that are dominated by class 0 or class 1 when graphed.

<img src="images/points_age.png" width="750" align="center">


## Modeling Results

After trying Decision Trees, Logistic Regression, K Nearest Neighbors, Random Forest, and XGBoost Classifier. I determined that XGBoost Classifier was the best model for predicting churn. We want to minimize the amount of false negatives since these are customers at risk of churn that would fall through the cracks otherwise. We would assume they don't need to be re-targeted but actually do. False positives, by contrast, will not lose us business if we re-target them. 

Here is the confusion matrix for the XGBoost Classifier model:

<img src="images/confusionmatrix.png" width="750" align="center">

I used this model to determine which of the features have the greatest influence on the target, and found membership category to be far and away the most important feature. Following this category are points in wallet and whether the customer has given feedback about customer care quality.

<img src="images/featureimp.png" width="750" align="center">

And looking more closely at points in wallet, our second most important feature, we can see that most of the at risk customers seem to have between 500-750 points.

<img src="images/points_atrisk.png" width="750" align="center">

## Answering the Business Question

The XGBoost Classifier had a recall score of over 94% when validated against the test data and a recall score of 96% on the test. This means it successfully predicted customers who were at risk of churn 94% of the time and was pretty good at minimizing false negatives. It also helped us figure out where the company needs to focus its re-targeting efforts.

Based on all of this, I recommend the company uses XGBoost Classifier moving forward to predict customer churn risk. I also suggest use membership category, wallet points, and customer care feedback to re-target customers.


## Conclusions
Ultimately, I recommend that the company uses XGBoost Classifier moving forward to predict customer churn risk. I also suggest retargeting customers that have no or basic membership, hold between 500-750 wallet points, and/or have given feedback on customer care.

In the future, the model can be improved with:
- Using more up-to-the-date, high-quality data.
- Including data on re-targeting to determine whether re-targeting hurts or helps.

## Links to Materials
[Presentation](https://github.com/npagrawal/Churn-Rate-ML/blob/main/Which%20customers%20are%20unhappy.pdf)  
[Jupyter Notebook](https://github.com/npagrawal/Churn-Rate-ML/blob/main/Churn%20Rate%20Analysis.ipynb)

## Repository Structure
```
├── data
├── images
├── Churn Rate Analysis.ipynb
├── README.md
└── Which customers are unhappy.pdf
```
