# Machine Learning Pipeline: Implementation Plan


## Data Preprocessing

1. The Dataset used in this project is from Kaggle in csv format. The Dataset loaded into dataframe using pandas package.

2. Using the info function checked the datatypes of different columns. 

3. Using the describe function checked Dataset statistical information such as standard deviation, mean of different numerical columns.

4. The Dataset contains na records. As number of records are very less so removed the na records from the dataset because their effect on the model will be less.

5. The Time related columns such as Date_of_Journey, Arrival Time and Duration are converted into datetime object to extract hours, minutes etc.. which will be helpful for model training. Because models work with numbers very well and improves learning and model performance.

6. The Arrival Time, Dep_time and Date of Journey are converted into datetime object for extracting components. But the Duration is converted into timedelta object because the data is not in correct time format.

## Feature Engineering

1. Generally algorithms doesnot accept the string values while Airline, Source and Destination columns are present in the strings datatype. According to these columns prices vary highly So we need to convert them into numerical values.

2. We use pandas get dummies function for converting the categorical strings into binary indicator columns which is One Hot Encoding. Then it will be easy for model to understand the data.

3. The Get dummies converts the 3 categorical columns into numerical data so that the model could understand the non numerical easily.

4. We will drop the Route and Additional Info because the route doesnot offer much value to the model as we have Total number of the stops in our dataset.

5. The Total number of stops column we will convert the string values to the numerical value. According the string values we provide the number or by meaning of the string.  

6. We will concat all the dataframes available. The other dataframes include Airline, Source and Destination Columns which are converted into different dataframes during One-Hot-Encoding.

7. We seperate the independent variables and dependent variable which is Price column. The column which we will predict in model. 


## Model Selection and Training

1. We need to split the dataset into Training and Testing data where we will use the Train data for Training the Model and Testing data for testing as the Testing data is not seen by the Model it will be hard for the model to predict this data So, that we could validate our model using metrics.

2. We will be using the Grid Search CV for Model Tuning to find the best model and parameters among Extra Trees, Random Forest and Linear Regression for out dataset.

3. After Model Tuning the Random Forest performed well among the three algorithm's. The best paramaters for Random Forest are bootstrap should be True because it introduces randomness in dataset for different trees while training model which shows how well the model performs on unseen data

4. max_depth should be 20 for a tree as this model doesnot Underfit or Overfit for the dataset, For selecting max_features the sqrt parameter is best.

5. The minimum number samples in each leaf node (min_samples_leaf) should be 1 As, this doesnot allow Overfitting Problem along with other paramters, while for split (min_samples_split) should be 5 this parameter improves generalization. 

6. The Total number of Trees (n_estimators) should be 100. So The Overfitting, Underfitting Problems wont be present in the model.

7. The algorithm Random Forest along with these parameters are used for building the model.

## Model Evaluation

1. The Final Best Random Forest Model RMSE score is 79.16.


