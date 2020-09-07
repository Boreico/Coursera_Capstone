# Coursera_Capstone

## Introduction

In this project I will try to create machine learning model that could predict, does some weather conditions will lead to road accident with the injured. Model of similar type could be used by emergency services for provisional allocation of ambulance teams in specific regions.

In context of this problem False Negative outputs are more unwanted than False Positive, because the cost of FN output may be human life. Therefore I will try to crate **recall-oriented** ML model.


## Data

I will use Seattle city road accidents data. It contain information of severity, location, weather conditions, date, and other details for each case. 

Most of the columns in table such as: 
CROSSWALKKEY(*A key for the crosswalk at which the collision
occurred*), JUNCTIONTYPE(*Category of junction at which collision took place*), SPEEDING, do not have valuable information for my task, so they will be removed from dataset.

Columns such as: **WEATHER, ROADCOND, LIGHTCOND** contains data that will be used as atributes for classification problem my model wil be solving.

**SEVERITYCODE** column can be used as a target values for ML. 

Also the data should be balanced to prevent creation of biased ML model.

