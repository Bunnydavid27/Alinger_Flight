# Machine Learning Pipeline: Implementation Plan


## Data Preprocessing

1. The Dataset used in this project is from Kaggle in CSV format. The Dataset was loaded into a dataframe using the pandas package.

2. Using the info function, checked the datatypes of different columns. 

3. Using the describe function for checking the Dataset for statistical information, such as the standard deviation, mean of different numerical columns.

4. The Dataset contains na records. As the number of records is very less so removed the na records from the dataset because their effect on the model will be less.

5. The time-related columns, such as Date_of_Journey, Arrival Time, and Duration, are converted into a  datetime object to extract hours, minutes, etc, which will be helpful for model training. Because models work with numbers very well and improves learning and model performance.

6. The Arrival Time, Dep_time, and Date of Journey are converted into a datetime object for extracting components. But the Duration is converted into a timedelta object because the data is not inthe  correct time format.

## Feature Engineering

1. Generally, algorithms do not accept string values while the Airline, Source, and Destination columns are present in the string datatype. According to these columns, prices vary highly, so we need to convert them into numerical values.

2. We use pandas get dummies function for converting the categorical strings into binary indicator columns, which is One Hot Encoding Technique. Then it will be easy for the model to understand the data.

3. The Get dummies converts the 3 categorical columns into numerical data so that the model can understand the non-numerical easily.

4. We will drop the Route and Additional Info because the route does not offer much value to the model as we have the Total number of stops in our dataset.

5. The Total number of stops column, we will convert the string values to numerical values. Accordingto  the string values, we provide the number or by meaning of the string.  

6. We will concat all the dataframes available. The other dataframes include Airline, Source and Destination Columns which are converted into different dataframes during One-Hot-Encoding.

7. We separate the independent variables and the dependent variable, which isthe  Price column. The column that we will predict in the model. 


## Model Selection and Training

1. We need to split the dataset into Training and Testing data, where we will use the Training data for training the Model and Testing data for testing. Since the Testing data is not seen by the Model, it will be hard for the model to predict this data So, we could validate our model using metrics.

2. We will be using the Grid Search CV for Model Tuning to find the best model and parameters among Extra Trees, Random Forest, and Linear Regression for our dataset.

3. After Model Tuning, the Random Forest performed well among the three algorithms. The best parameters for Random Forest are that bootstrap should be True, because it introduces randomness in the  dataset for different trees while training the model, which shows how well the model performs on unseen data

4. max_depth should be 20 for a tree, as this model does not Underfit or Overfit for the dataset. For selecting max_features, the sqrt parameter is best.

5. The minimum number of samples in each leaf node (min_samples_leaf) should be 1, which does not allow the Overfitting Problem, along with other parameters, while for split (min_samples_split) should be 5 this parameter improves generalization. 

6. The Total number of Trees (n_estimators) should be 100. So the Overfitting, Underfitting Problems won't be present in the model.

7. The algorithm Random Forest, along with these parameters, is used for building the model.

## Model Evaluation

1. The Final Best Random Forest Model RMSE score is 79.16.




