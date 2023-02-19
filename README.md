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

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I chose Logistic Regression to estimate the probability of absenteeism occuring by classifying people into 2 classes.
* Take the median value of the 'Absenteeism Time in Hours' and use it as a 'cut-off' line.
* Moderately Absent: absent less than or equal to the median value of the 'Absenteeism Time in Hours'
* Excessively Absent: absent more than the median value of the 'Absenteeism Time in Hours'

## Insights from model (based on the Odds_ratio)
* Reason_3: The most crucial reason for excessive absence is poisoning. If someone is poisoned, they won't go to work and they're being excessively absent after being poisoned are 22 times higher than when no reason was reported.
* Reason_1: various diseases. A person who has reported this is 16 times more likely to be excessively absent than a person who didn't specify a reason.
* Reason_2: pregnancy and giving birth. When woman is pregnant, she goes to the gynecologist, gets a regular pregnancy check and comes back to work. 2.5 times more likely to be excessively absent than the base model.
* Transportation Expense: for 1 standard deviation increase in Transportation Expense, it is close to twice as likely to be excessively absent.
* Pet: for each additional standardized unit of Pet, the odd = 1 - Odds_ratio, or 24% lower than the base model. This is maybe because if someone have several pets, they're probably not taking care of them on their own(somebody else can take them to the doctor if something is wrong)


## Use Tableau to analyze absenteeism model
Below are a few highlights from the Tableau. 

![alt text](https://github.com/nengnengfei/Data_Science_Absenteeism_Analysis/blob/main/Age%20vs%20Probability.png "Age vs Probability")
![alt text](https://github.com/nengnengfei/Data_Science_Absenteeism_Analysis/blob/main/Reasons%20vs%20Probability.png "Age vs Probability")
![alt text](https://github.com/nengnengfei/Data_Science_Absenteeism_Analysis/blob/main/Transportation%20Expense%20vs%20Children.png "Transportation Expense and Children")

## Summary
* Dropped Reason 2 and Reason3 (doesn't tell much about what to expect from individuals being absent)
* Reason 1 represents very serious diseases; the numbers tell us that the expected probability of an individual to be excessively absent because of Reason 1 is higher than 50%.
* Reason 4 represents light reasons for absence, a dental appointment, physiotherapy a medical consultation, and others. It is quite probable that none of these could be serious enough to require that a person is absent from their workplace for an entire day. (People who must be absent for such a reason are not expected to be excessively absent.)
* There is a positive correlation, the higher the transportation expense of person, the higher the chance they will be away from work excessively.
* People with no children don't exhibit a high probability for excessive absence.
* People with 1 or 2 children don't generally spend more than $240 on transportation.
