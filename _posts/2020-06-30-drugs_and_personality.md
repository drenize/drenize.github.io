---
title: "Drugs and Personality"
date: 2020-06-30
tags: [data engineering, data science, messy data, machine_learning]
header:
  image: "/images/drugs_personality/benzos.png"
  teaser: "/images/drugs_personality/benzos.png"
excerpt: "First Machine Learning Project"
mathjax: "true"
---

# Drug Abuse and Personality Traits
Authors: Drenizë Rama & [Eike Rogall](https://rogall-e.github.io/)

So for our second portfolio project in the data science bootcamp we tackled the task of examining the relationship between drug abuse and personality traits. 
In order to do so, we used the [UCI dataset](https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29) on drug consumption. Personality traits have been assessed with the [NEO-FFI-Revised Scale](https://arxiv.org/abs/1506.06297). 
For the whole code on this project please click [here](https://github.com/drenize/drug_abuse_and_personality/blob/master/Drug_Risk_Project.ipynb) <br>


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


Packages I imported for this project: 

```python
    import pandas as pd
    import numpy as np
    import seaborn as sns
    import matplotlib.pyplot as plt
    import statsmodels.api as sm


    #split data into test and training data sets
    from sklearn.model_selection import train_test_split

    #packages for building a pipeline
    from sklearn.pipeline import Pipeline
    from sklearn.preprocessing import OneHotEncoder, StandardScaler
    from sklearn.impute import SimpleImputer
    from sklearn.model_selection import cross_val_predict, cross_val_score, cross_validate
    from sklearn.metrics import roc_curve, confusion_matrix, accuracy_score, recall_score, precision_score
    from sklearn.metrics import f1_score
    from sklearn.compose import ColumnTransformer
    from sklearn.metrics import classification_report 

    #feature importance
    from sklearn.inspection import permutation_importance
    from sklearn.datasets import make_classification
    from sklearn.feature_selection import SelectFromModel

    #import classification models
    from xgboost import XGBClassifier
    from sklearn.ensemble import AdaBoostClassifier
    from sklearn.ensemble import RandomForestClassifier
    from sklearn.svm import SVC
    from sklearn.tree import DecisionTreeClassifier


    #GridSearch model improvement
    from sklearn.model_selection import GridSearchCV, RandomizedSearchCV
    from sklearn.metrics import make_scorer
    from sklearn.model_selection import StratifiedKFold
```

First we created a label of people who have recently consumed drugs, namely last week or yesterday:
```python
    drug_rec = drug_risk[illegal] > 5
    drug_rec[illegal] = drug_rec[illegal].astype(int)
    drug_rec_dum = drug_rec[illegal].sum(axis=1)
    drug_rec_dum.values[drug_rec_dum > 0] = 1
    drug_risk = pd.concat([drug_risk, drug_rec_dum], axis=1)
    drug_risk.rename(columns={0: "ill_rec"}, inplace=True)


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

