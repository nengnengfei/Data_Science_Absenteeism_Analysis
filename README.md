# Absenteeism Analysis: Project Overview 
* Focued on the business problems
* Looked into the dataset and applied Logistic Regression
* Created a dataviz
* Predicted absenteeism from work to know whether or not an employee can be expected to be missing for a specific number of hours in a given workday
* Improve business decision-making by reorganizing the work process in a way that will allow business to avoid a lack of productivity and increase the quality of work 
* Explored whether a person presenting certain characteristics is expected to be away from work at some point in time or not

## What is Absenteeism?
* Absence from work during normal working hours, resulting in temporary incapacity to execute regular working activity.

## This analysis will address ABSENTEEISM at a company during work time
    Business problems: 
    * the business environment of today is more competitive than is used to be, and that leads to increased pressure in the workplace
    * unachievable business goals
    * elevated risk of becoming unemployed
    * becomes detrimental to a person's health

## Code and Resources Used 
**Python Version:** 3.9  
**Packages:** pandas, numpy, sklearn, pickle.   
**Tableau Public**

## Analyze the columns in the dataset 
With each employee, we got the following:
* ID
*	Reason for Absence
*	Date
*	Transportation Expense
*	Distance to Work
*	Age
*	Daily Work Load Average
*	Body Mass Index
*	Education
*	Children
*	Pets
*	Absenteeism Time in Hours
       

## Data Cleaning
After collecting the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Removed columns that will not improve the analysis
* Converted the nominal values in 'Reason for Absence' column to dummy variables
* Grouped 'Reason for Absence' based on the [Absenteeism Feature Descriptions](https://github.com/nengnengfei/Data_Science_Absenteeism_Analysis/blob/main/Absenteeism_Feature_Description.png) Table
*	Made new columns for each group of reason


## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/salary_by_job_title.PNG "Salary by Position")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/positions_by_state.png "Job Opportunities by State")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/correlation_visual.png "Correlations")

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I chose Logistic Regression to estimate the probability of absenteeism occuring by classifying people into 2 classes.
* Take the median value of the 'Absenteeism Time in Hours' and use it as a 'cut-off' line.
* Moderately Absent: absent less than the median value of the 'Absenteeism Time in Hours'
* Excessively Absent: absent more than the median value of the 'Absenteeism Time in Hours'

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = 11.22
*	**Linear Regression**: MAE = 18.86
*	**Ridge Regression**: MAE = 19.67

## Productionization 
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary. 


