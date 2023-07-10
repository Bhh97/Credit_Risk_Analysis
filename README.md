# Credit_Risk_Analysis
This repository contains a Spark-based credit risk analysis project. The dataset used in this project is obtained from Kaggle.

## Project Description
The objective of this project is to build a machine learning model using Apache Spark to predict whether a client will default or not, which is a common problem in credit risk analysis.

The dataset consists of various features such as 'balance', 'income', 'age', 'education', etc. for each client. The target variable is 'default_ind' which indicates whether the client has defaulted on their loan or not. The dataset is split into training and testing sets for model building and evaluation.

## Approach
Data Loading and Preprocessing:
The data is loaded into a Spark DataFrame and inspected. This includes checking for missing values, data types, and basic summary statistics.

### Feature Engineering:
The categorical and numerical features are identified. For categorical features, we use a combination of StringIndexer and OneHotEncoder to convert the categorical variables into a form that can be provided to the machine learning model. For numerical variables, they are used as they are.
A VectorAssembler is then used to combine all the feature columns (categorical and numerical) into a single vector column. This is necessary as Spark MLlib expects input data to be in this form.
All these steps are combined into a Spark ML Pipeline for convenience and reproducibility.

### Model Building:
A Logistic Regression model is trained on the processed training data. The features column produced by the VectorAssembler is used as the input features for the model. The target column is 'default_ind'.

### Model Evaluation:
The trained model is then used to make predictions on the test data. Several metrics including accuracy, precision, recall, and F1 score are computed to evaluate the performance of the model.
This allows us to get an understanding of how well our model will generalize to unseen data and where its weaknesses may lie.

### Saving and Loading the Model:
The pipeline model can be saved for future use. This allows us to reuse the model on new data without having to go through the training process again. The model is saved and loaded using the .write().overwrite().save() and PipelineModel.load() methods respectively.

# Conclusion:
This project showcases how to perform credit risk analysis using Spark MLlib. The goal is to predict whether a client will default or not based on various features. The project demonstrates how to prepare data, build and evaluate a logistic regression model, and save the model for future use in Spark.
