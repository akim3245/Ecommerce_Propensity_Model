# Ecommerce Propensity Model

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

Target variable: 'Ordered' -- *did the customer make an order or not?*


## Building the Model
I used cross validation to get the roc auc scores for the following algorithms:
* Logistic Regression
* Random Forest
* Decision Tree
* Stochastic Gradient Descent

Logistic Regression performed with the highest roc_auc score of 0.9975.

As a base model, I proceeded with Logistic Regression to train and make predictions. Here is a cross tab of the predicted vs actual values.
[![Screen-Shot-2020-06-24-at-10-24-58-PM.png](https://i.postimg.cc/s2MQpW1w/Screen-Shot-2020-06-24-at-10-24-58-PM.png)](https://postimg.cc/bGjwPsxt)

There is a high number of 0's being predicted and very few 1's being predicted (only 26) which shows that the dataset is highly imbalanced.
Another visual of imbalanced data is shown by the value counts of the target variable.

[![Screen-Shot-2020-06-13-at-11-12-03-PM.png](https://i.postimg.cc/7bv5gkWF/Screen-Shot-2020-06-13-at-11-12-03-PM.png)](https://postimg.cc/8fHkSqD4)

To handle the imbalanced dataset, I upsampled the minority class (where df.ordered == 1) to match the same count as the majority class and then trained the model and made predictions on the upsampled data. As a result, precision increased from 0.868 to 0.992 and recall increased from 0.985 to 0.992. 
The crosstab of predicted vs actual also showed an increase in 1s being predicted compared to the base model.
[![Screen-Shot-2020-06-24-at-10-36-12-PM.png](https://i.postimg.cc/cC34H798/Screen-Shot-2020-06-24-at-10-36-12-PM.png)](https://postimg.cc/N2gwCXwg)

## Propensity Modelling
After training the model, it was time to use the test data to build a propensity model.

The test data was split 50/50 into the control group and treatment group. 

The trained model was applied to the treatment group to make probability predictions and the data was split into deciles.

A new dataframe was created to put together the number of actual 1's (people who converted in each decile), the conversion rates, and lift.

Lift over control = (treatment conversion rate - control conversion rate) / control conversion rate

[![Screen-Shot-2020-06-24-at-9-41-52-PM.png](https://i.postimg.cc/tgpPGwMV/Screen-Shot-2020-06-24-at-9-41-52-PM.png)](https://postimg.cc/dhND8Hvq)

The chart demonstrates a decrease in conversion rate as decile number increase. 
