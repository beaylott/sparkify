# Udacity Data Scientist Nanodegree Capstone Project: Sparkify 

This repository contains the notebooks and other files used to completed the Sparkify project. Spark 3.0.x was used on both the desktop and AWS EMR cluster environments.

## Project Definition, 
### Project Overview

The purpose of this project is to try to identiy users who may 'churn' (i.e. cancel their subscription/close their account) in a data set of a simulated music streaming service. Churn analysis is important for businesses which rely heavily on subscriptions as even small increases in churn rates can have dramatic effects on bottom line financial viability for these business models.

### Problem Statement

In this project PySpark is used to do churn analysis on two Sparkify datasets - a 'mini' dataset which is a straified subset of the full dataset and the full data set itself. PySpark is used in anticipation of not being able to analyse the full dataset on a single machine. Pandas is also used in the exploratory data analysis of the mini data set. The full data set is analysed on an AWS EMR cluster.

### Metrics

The metric used in both cross-validation and evaluation is the f1 score. The f1 score is chosed due the unbalanced nature of the Sparkify dataset i.e. there is a much larger number of un-churned users than churned users. False positives in this context are less problematic than false negatives. The usual accuracy metric is also calculated and presented in the evaluation.

## Files
* Sparkify_local.ipynb: Notebook used to analyse mini sparkify data set on a desktop.
* Sparkify_aws.ipynb: Notebook used to analyse full sparkify data set on an AWS EMR cluster.
* start.sh: convenience script used to start Jupyter Spark environment used for environment on desktop.
