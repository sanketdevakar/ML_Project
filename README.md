# Student Performance Indicator

###  Problem statement
- This project understands how the student's performance (test scores) is affected by other variables such as Gender, Ethnicity, Parental level of education, Lunch and Test preparation course.


###  Data Collection
- Dataset Source - https://www.kaggle.com/datasets/spscientist/students-performance-in-exams?datasetId=74977
- The data consists of 8 column and 1000 rows.

    * gender : sex of students  -> (Male/female)
    * race/ethnicity : ethnicity of students -> (Group A, B,C, D,E)
    * parental level of education : parents' final education ->(bachelor's degree,some college,master's degree,associate's degree,high school)
    * lunch : having lunch before test (standard or free/reduced) 
    * test preparation course : complete or not complete before test
    * math score
    * reading score
    * writing score


# Approach for the project 

1. Data Ingestion : 
    * The raw data is read from a CSV file.
    * The dataset is then split into training and testing sets.
    * These sets are saved as separate CSV files for further processing. 

2. Data Transformation : 
    * A ColumnTransformer pipeline is created to preprocess the data.
    * For numeric features:
        - Missing values are imputed using SimpleImputer with the median strategy.
        - The features are scaled using StandardScaler.
    * For categorical features:
        - Missing values are imputed using SimpleImputer with the most frequent strategy.
        - Features are encoded using OrdinalEncoder.
    * Encoded values are also scaled with StandardScaler.
    * The complete preprocessor pipeline is saved as a pickle (.pkl) file for reuse.

3. Model Training :   
    * Initial testing is done with various base models, with CatBoost Regressor showing the best performance.
    * Hyperparameter tuning is performed on CatBoost and KNN models to optimize performance.
    * A final Voting Regressor is built by combining predictions from CatBoost, XGBoost, and KNN models.
    * This ensemble model is saved as a pickle file for deployment.

4. Prediction Pipeline : 
    * This pipeline converts given data into dataframe and has various functions to load pickle files and predict the final results in python.

5. Flask App creation : 
    * Flask app is created with User Interface to predict the gemstone prices inside a Web Application.

# Exploratory Data Analysis Notebook

Link : [EDA Notebook](https://github.com/sanketdevakar/Student_Performance/blob/Main/notebook/1%20.%20EDA%20STUDENT%20PERFORMANCE.ipynb)

# Model Training Approach Notebook

Link : [Model Training Notebook](https://github.com/sanketdevakar/Student_Performance/blob/Main/notebook/2.%20MODEL%20TRAINING.ipynb)

