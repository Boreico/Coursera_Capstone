## Data

I will use Seattle city road accidents data. It contain information of severity, location, weather conditions, date, and other details for each case. 

Most of the columns in table such as: 
CROSSWALKKEY(*A key for the crosswalk at which the collision
occurred*), JUNCTIONTYPE(*Category of junction at which collision took place*), SPEEDING, do not have valuable information for my task, so they will be removed from dataset.

Columns such as: **WEATHER, ROADCOND, LIGHTCOND** contains data that will be used as atributes for classification problem my model wil be solving.

**SEVERITYCODE** column can be used as a target values for ML. 

Also the data should be balanced to prevent creation of biased ML model.
