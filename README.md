# Marketing Campaign Success Predictor

## Table of Contents

1) Navigating the Git Hub Repository
2) Executive Summary
3) Technologies and Libraries Used
4) Data Cleaning Data Gathering and Feature Engineering
5) Modelling
6) Evaluation

### Navigating the Git Hub Repository

- Jupyter Notebooks: The main Jupyter Notebooks can be found in the Notebooks folder.
  - 01 Data Cleaning.ipynb
  - 02 Data Visualisations.ipynb
  - 03 Feat_Engineer.ipynb
  - 04 Modelling.ipynb
 
 - Data: The relevant CSV files can be found in the Data Folder.
  - bank-additional-full.csv
  - LIBOR EUR.csv
  - Portugal_Eurozone_data.csv
  - data_feat.csv
  - data_final.csv
  
 - Original Kaggle Dataset Notebook: We ran the model using the original dataset on Kaggle. Notebooks of that analysis can be found here.
  - Data Cleaning and EDA.ipynb
  - Feature Engineering and Baseline.ipynb
  
  - Original Kaggle Datasert Data: CSV files for the model using the original dataset on Kaggle.
   - bank-cleaned.csv
   - bank-full.csv
   - bank2.csv
   - data2.csv
   
  - Presentations: Folder for presentation of the project.
    - presentation.pdf
    
  - README.md

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

The dataset that we used for our analysis can be found here.

The features available in this data set is as follows

- age: Age of the customer
- job: Job of the customer
- marital: Marital status of the customer
- education: Highest educationa attained by the customer
- default: Has the customer defaulted previously?
- housing: Does the customer have a housing loan?
- loan: Does the customer have any existing loans?
- contact: Was the customer contacted by mobile or telephone?
- month: What month of the year was the customer previously?
- day_of_week: What day of the week was the customer contacter previously?
- duration: Duration of last call in seconds.
- campaign: Number of times the customer was contacted on this campaign
- pdays: Number of days that passed by after the customer was last contacted from a previous campaign
- previous: Number of contacts performed before this campaign and for this customer
- poutcome: Outcome of previous campaign
- emp.var.rate: Employment varition rate.
- cons.price.idx: Consumer Price Index
- cons.conf.idx: Consumer Confidence Index
- euribor3m: 3m EURIBOR fixing
- nr.employed: Number of employees
- y: Has the customer subsribed on this campaign (This is our target variable)

       
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

### Evaluation

Following the additional economic data for Portugal and Eurozone, our model performance increased to 90.5%. Using hyperparameter tuning with Sci-Kit learn's GridSearchCV function, we were able to increase the performance to 92.8%. As it stands, our best performing model is the Logisitic Regression model using GridSearchCV.


