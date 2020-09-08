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

## Methodology 

First I've read dataset using Pandas library and removed columns that don't related weather conditions or severity of road accidents.
Then I've dataset check for NaN values and figured out that amount of columns with NaN values is insignificant. I've removed all columns with NaN values.

Next, I've categorize the data and convert it to *int64* type. I've replace values 1 and 2 in SEVERITYCODE column to 0 and 1 respectively. This will simplify further evaluation of ML models. I've check counts of values, and figured out that dataset was unbalanced. This could lead to creation bias ML model. So I've removed part of rows with SEVERITY 1.

Then, I've divided the data on target values(y), and atributes(X).
As target values I will use SEVERITYCODE column, other such as COLLISIONTYPE, VEHCOUNT describe severity of collision worse.

After that, I've splited the data on training and test sets in 3 to 1 ratio.
I've ran couple of ML classifiers such as:
* Logistic regression
* MLPClassifier
* GradientBoostingClassifier
* RandomForestClassifier

with default setting

The LogisticRegression had lowest score and was least suitable of the models a tried.

MLPClassifier as a neural network in perspective might had good generalization performance. But model might be hard to tune to have high recall-score. And the model results would be hard to interpret.

RandomForestClassifier and DecisionTreeClassifier has the same accuracy and recall with default setting. I've choosen DecisionTreeClassifier because it could be better choice for further tuning, because it's result would be easy to visualize.

Next I've performed grid search with basic parameters of **DecisionTreeClassifier**:
* max__depth
* max_leaf_nodes
* max_features
* min_samples_split

Grid search has done very slightly improve generalization performance of the model. Which might be due to the fact that weather not directly related to severity of the road accident.

Finally, I've ploted bar chart with feature importances this model, and plot the desidion tree.

## Results and Discussion

In this project I've built the machine learning model, that can predict severety of possible road accidend based weather conditions. The data I used was .csv file with description of road accidents in Seatlle city.

After preprocessing of the data I decided to use as target values SEVERNETYCODE column that contains two types of coded values:
1. Property damage
2. Injury

As an atributes a choose WEATHER, ROADCOND, LIGHTCOND. The last two columns has information directly related to the weather conditions. 

Then I've formated the data suitable for machine learning. I've run couple of ML models can handle binary calsificatin with large dataset. The best output gave DesidionTreeClassifier. Then I've opimized this model using grid seach tool. As performans indicators I've used accuracy and recall. Model reached accuracy of *57.2%* and recall of *98%*. As most important feature for calssification model choosed light conditions.

## Сonclusion

Despite the fact that model did't reached hight generalization performance. It have shown that light condition is highly correlated with severity that weather in general. 
Model of such type can be used by emergency services for provisional allocation of ambulance teams in regions with wether that increace chance of road accidens with injured.

Also this project has shown that data about weather condition does not enough to predict severity of the collision with hight accuracy. In further researches other factors of severity need to be finded

Another conclusion I can make, that emergency services should gather and rely more on data about light and road condition than just weather when predicting severe road accidents.
