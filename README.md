# Faulty_Wafer_detection
This is project for detection of faulty wafer detection to detect faulty wafer

## Problem Statment
To build a classification methodology to predict the quality of wafer sensors based on the given training data.

The inputs of various sensors for different wafers have been provided. In electronics, a wafer (also called a slice or substrate) is a thin slice of semiconductor used for the fabrication of integrated circuits. The goal is to build a machine learning model which predicts whether a wafer needs to be replaced or not(i.e., whether it is working or not) based on the inputs from various sensors. There are two classes: +1 and -1. 
-	+1 means that the wafer is in a working condition and it doesn’t need to be replaced.
-	-1 means that the wafer is faulty and it needs to be replaced. 

## Architecture

Below diagram explains the flow of architecture for project flow

![image](https://user-images.githubusercontent.com/46865218/159209166-a04f9f64-72e5-48f1-aa50-8024a0c26133.png)

Client will send the data in the form of multiple csv file from which we define a schema file. 
If the file support the schema file it go to tempory Good Data folder and else it will be gone to Bad Data folder.

To reach good data folder we need to validate the file using different parameters 
  - flie name regex
  - time of file 
  - no of columns

once these are matched data in .csv files gone to local DB.

From localDB to Data process like EDA
  - impute missing values
  - data transformation to standard format

Once EDA has complted data will examined for patterns and divided them to n number of clusters

Each cluser data is fed to diffenrent training model based good AUC score we select the appropiate traning algorithm
In this we use two  classification algorithms
  - Randforest Classifier
  - XGBoosting 
 
Based on best socre we will select best alogorithm and traning will be done.

Predict file will be send by Clinet and all the files will be gone through abouve mentioned steps like Data Preprocessing and EDA and then they will be given to model algorihm for predicting output for classification

