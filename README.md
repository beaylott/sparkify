# Udacity Data Scientist Nanodegree Capstone Project: Sparkify 

This repository contains the notebooks and other files used to completed the Sparkify project. Spark 3.0.x was used on both the desktop and AWS EMR cluster environments.

## Problem Statement

The purpose of this project is to try to identiy users who may 'churn' (i.e. cancel their subscription/close their account) in a data set of a simulated music streaming service. Churn analysis is important for businesses which rely heavily on subscriptions as even small increases in churn rates can have dramatic effects on bottom line financial viability for these business models. 

## Metrics

The metric used in both cross-validation and evaluation is the f1 score. The f1 score is chosed due the unbalanced nature of the Sparkify dataset i.e. there is a much larger number of un-churned users than churned users. False positives in this context are less problematic than false negatives. The usual accuracy metric is also calculated and presented in the evaluation.

## Technical solution 

In this project PySpark is used to do churn analysis on two Sparkify datasets - a 'mini' dataset which is a straified subset of the full dataset and the full data set itself. PySpark is used in anticipation of not being able to analyse the full dataset on a single machine. Pandas is also used in the exploratory data analysis of the mini data set. 

User churn is identified by determining if the user visited the 'Cancellation' page. This is taken to indicate user churn on its own.

For features the notebook calculates a number of aggregates which are all used in the final model including average length of session, average number of songs per session, average error rates per user. The other features used were the platform (derived from the user agent strings), the stated gender of the user, and the downgrade status (calculated in a similar way to churn status). 

Both notebooks train a range of classifiers from the pyspark.ml library on the data set (logistic regression,decision tree,random forest,gradient boosted tree,scalar vector classifier) as well as cross-validating these and using a parameter grid to tune a subset of available hyper-parameters (chosen based on recommendations in the documentation).

The full data set is analysed on an AWS EMR cluster using the Sparkify_aws.ipynb file. This is largely similar to the local notebook but does not include the exploratory data analysis (this is generally a difficult thing to do on a cluster as the data typically needs to be loaded into memory on a single machine first to graph it).

## Modelling output

It was found that the RandomForestClassifier was consistently marginally better on both the mini and full data set achieving f1 scores of 0.80 and 0.68 respectively. For the best model the hyper-parameters found were numTrees=4 and maxDepth=3. The notebook also uses the feature importance score functionality associated with the Random Forest Classifier to ascertain the relative importance of different features

## References

Blog post: https://medium.com/@beaylott/churn-prediction-for-the-sparkify-data-set-38f058e1271a

PySpark documentation: https://spark.apache.org/docs/latest/

## Files
* Sparkify_local.ipynb: Notebook used to analyse mini sparkify data set on a desktop.
* Sparkify_aws.ipynb: Notebook used to analyse full sparkify data set on an AWS EMR cluster.
* start.sh: convenience script used to start Jupyter Spark environment used for environment on desktop.
