# Marketing Campaign Success Predictor

## Table of Contents

### Executive Summary

The purpose of this project is to create a Binary Classification model which will assess the effectiveness of a marketing campaign. The dataset we used for this project is the Portugese Bank Marketing Dataset found on Kaggle.

The dataset provides data for direct phone call marketing campaigns for a Portugese Retail Banking institution, which aims to promote term deposits to bank's existing customers. The dataset includes data between May 2008 and November 2010.

https://www.kaggle.com/yufengsui/portuguese-bank-marketing-data-set

The same kaggle dataset can be found on the following website with a few more additional columns which we thought would be useful for our model.

http://archive.ics.uci.edu/ml/datasets/Bank+Marketing#.


### Technologies and Libraries Used

- Python
- Pandas
- Numpy
- Matplotlib
- Seaborn
- Scikit-learn
- Stats Models


### Data Cleaning Data Gathering and Feature Engineering

In order to bring more scope into the project, and make it more widely usable, We decided to supplant the existing data set with additional economic data from Portugal and the Eurozone.

The original dataset had a column for 3m EURIBOR. We used this column to work out the corresponding date for when 3m EURIBOR fixed at that level. We then applied this to the entire dataset, and were thus able to create a date column. This opened up the opportunity for us to add any more economic data that we saw relevant to our model.

For the purposes of this project, we decided to bring in the following economic variables, so as to create a more robust model.

- Portugal Month-on-Month Inflation
- Portugal Wage Growth                        
- Portugal Annual Income Tax Rate 
- Portugal Bank Lending Rate        
- Portugal Personal Savings Rate          
- Portugal Average Wage                  
- Portugal Unemployment Rate         
- Portugal Sales Tax 
- EURUSD Foreign Exchange Rate                             
- Eurozone GDP Growth Rate  

Additionally, we Feature Engineered the Age column in the existing dataset based on Age Groups that banks and financial institutions typically to bucket their clients into.

We then created dummy variable columns for the the categorical data in the dataset.

And finally used Feature Engineering to address any multicolinearity issues in our dataset.

### Modelling

In order to carry out the modelling, we split our final dataset into 3 subsets. Train (26,360 rows), Validation(6,590 rows) and Test (8,238 rows).

We initially ran the model on the original kaggle dataset, and obtained a ROC-AUC score of 87%

Following the additional economic data for Portugal and Eurozone, our model performance increased to 90.5%. Using hyperparameter tuning with Sci-Kit learn's GridSearchCV function, we were able to increase the performance to 92.8%. As it stands, our best performing model is the Logisitic Regression model using GridSearchCV.


