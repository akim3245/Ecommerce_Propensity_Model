# Ecommerce Propensity Model

#### -- Project Status: [Active]

## Project Intro
Building a model to predict customer propensity to purchase on a store website. 

## Project Description
Information from the dataset is fictional and contains a day's worth of visits. 

Some of the features included:
* Basket icon click
* Checked delivery detail
* Sign in
* Saw checkout
* Basket add detail
* Basket add list
* Saw homepage
* and more

Target variable: 'Ordered'

I plotted the value counts of people who ordered and it appears that majority of people who visited this website did not make an order. 

[![Screen-Shot-2020-06-13-at-11-12-03-PM.png](https://i.postimg.cc/7bv5gkWF/Screen-Shot-2020-06-13-at-11-12-03-PM.png)](https://postimg.cc/8fHkSqD4)


## Modelling
I used cross validation to get the auc roc scores for the following algorithms:
* Logistic Regression
* Random Forest
* Decision Tree
* Stochastic Gradient Descent

Logistic Regression performed with the highest roc auc score of 0.9975.

I proceeded with Logistic Regression to train, make predictions and plotted a graph to show the roc curve. 
[![Screen-Shot-2020-06-13-at-11-19-01-PM.png](https://i.postimg.cc/L8txg4WM/Screen-Shot-2020-06-13-at-11-19-01-PM.png)](https://postimg.cc/87CRqGDy)
