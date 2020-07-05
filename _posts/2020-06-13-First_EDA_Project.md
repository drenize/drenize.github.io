---
title: "First Data Science Project - House Prices"
date: 2020-06-13
tags: [data wrangling, data science, messy data, machine learning]
header:
  teaser: "/images/KChouse.png"
  image: "/images/KChouse.png"
excerpt: "Data Wrangling, Data Science, Messy Data, Machine Learning"
mathjax: "true"
---

# EDA-Project-1-House-Prices

## Analysing King County House Market


This project is about predicting house prices in King County, Washington in the context of a data science bootcamp. The project journey goes through all stages of the data science cycle from business understanding, over data cleaning, to delivering predictions. Furthermore, a train-validation-test is implemented as well a multicollinearity check.

The project aims at finding the best choice in real estate of mansion sized properties (defined as over 10,000sqft in size) in a price category of 3,5M upwards.

You can find the code to the project [here](https://github.com/drenize/EDA-Project-1-House-Prices/blob/master/FirstProject_EDA_Drenize.ipynb)

## Data Science Life Cycle
1. Business Understanding
2. Data Mining
3. Data Cleaning
4. Data Exploration
5. Feature Engineering
6. Predictive Modeling
7. Data Visualisation

## Data Cleaning
Missing values occured in three categorical variables for which an imputation by mode has been applied. 
- **waterfront**: 11% missing values
- **view**: 0.3% missing values
- **yr_renovated**: 17.8% missing values

## Data Engineering
Two variables, previously stored as object data types, were converted to an adequate data type
- **sqft_basement**: numerical, int
- **date**: from string to datetime

Date was split into a month and a year variable to explore price variations over time. 
A variable 'sqft_total_property' was created as the sum of 'sqft_living' and 'sqft_lot'.

## Model Choice
Linear regression modeling is explored for prices. Features were chosen through an algorithm by significance.

## Results and Recommendations
- In the course of 1 year there is a 10.4% price decrease in luxury house prices. Therefore, it is recommended to by a luxurious mansion sized house in 2015.
- When buying a property of more than 10,000 sqft space
a. buy at the waterfront
b. with 1.5 of floors
c. graded with a 10 or 11

## Future Work
- improve  and apply the linear model by reducing features and evaluate train-test split
- compare price segments
- search for underrated objects
- explore multicollinearity

## Presentation
You can find the final presentation of the business case [here](https://github.com/drenize/EDA-Project-1-House-Prices/blob/master/House_Prices_Prediction_Drenize.pdf)
