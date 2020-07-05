---
title: "First Machine Learning Project: Drugs and Personality Data"
date: 2020-06-30
tags: [data engineering, data science, messy data, machine_learning]
header:
  teaser: "/images/drugs_personality/benzos.png"
  image: "/images/drugs_personality/benzos.png"
  teaser: "https://github.com/drenize/drenize.github.io/blob/master/images/drugs_personality/benzos.png"
excerpt: "Data Engineering, Data Science Life Cyclw, Machine Learning"
mathjax: "true"
---

# Drug Abuse and Personality Traits
Authors: Drenizë Rama & [Eike Rogall](https://rogall-e.github.io/)

[Jupyter Notebook](https://github.com/drenize/drug_abuse_and_personality/blob/master/Drug_Risk_Project.ipynb) <br>


**Objective**

This project aims at examining the relationship between personality traits and drug consumption.
First, the normalized data is coded into more apprehensible, numeric categories. 
Then further features are engineered to highlight deeper data structures. The engineered variables are: soft drug consumption, hard drug consumption, legal drug consumption, illegal drug consumption, synthetic and nonsynthetic drug consumption, recent consumtion, hard score and hardliners.

The hard score (hard_score) is build of the mean of neuroticism, extraversion, impulsiveness and sensation seeking. The hardliner variable, however, comprises only the 10% highest hard scores. 

**Business Case**

A drug prevention organization is interested in the use frequency of illegal drugs of hardliner personalities versus other people. Furthermore, they want to predict the use of illegal drugs.


## Data Science Life Cycle
- Business Understanding
- Data Mining
- Data Cleaning
- Data Exploration
- Feature Engineering
- Predictive Modeling
- Data Visualisation

## Data Cleaning
- normalized values were converted into comprehensible numeric categories

## Data Engineering
New features were build: 
+ soft = soft drugs
+ hard = hard drugs
+ legal = legal drugs
+ illegal = illegal drugs
+ hard_score = includes personality traits neuroticism(Nscore), extraversion (Escore), open to new experiences (Oscore), sensation seeking (SS), impulsiveness (impulsive)
+ hardliners = 10% highest scoring participants on hard_score

## Predictive Modeling
Models were applied and compared for recall and accuracy scores
+ XGBClassifier
+ AdaBoost
+ RandomForestClassifier
+ Support Vector Machine
+ DecisionTreeClassifier

## Recommendations
+ reliable prediction of hardliners is not possible with current data
+ reliable prediction of illegal drug users on the other hand is possible based on: 
sensation seeking, ethnicity, openness to new experiences, country, conscientiousness,  age
+ illegal drug use is a widespread issue throughout society


## Future Work
Data related implications:
+ collect data on socioeconomic status
+ collect data on amount of drug doses
+ collect data on clinical diagnoses
+ collect data on abuse and addiction
+ collect timeline data to identify co-morbidity of diverse substance abuse or/and addiction

Model related implications: 
+ try unsupervised machine learning models 
+ apply regression models on continuous data
+ new model for hardliner prediction

