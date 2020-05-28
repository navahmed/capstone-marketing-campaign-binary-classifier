# Marketing Campaign Success Predictor

Naweed Ahmed
Email: naweed.ahmed83@gmail.com

Linekdin: https://www.linkedin.com/in/naweedahmed

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

We dropped the duration column for our modelling entirely. This column shows the last contact duration in seconds. The UCI website notes that this attribute has a strong impact on the target variable. We investigated this in the EDA and Validation note book, and decided to drop it in order to have more realistic predictive results.

### Addressing Multicolinearity Between Features

In order to address the issue of multicolinearity between features, we plotted a correlation heatmap, using a threshold of 0.7 as our cutoff point. We came across a number of features which had correlation scores above 0.7, and used the following measures to address the problem.

- emp_var_rate: Strong correlation with cons_price_idx, euribor3m, nr_employed, portugal_bank_lending. We will drop emp_var_rate entirely. We have another feature for Portugal_Unemployment_Rate. This variable will be able to capture any impact of Unemployment on our target variable. So we can do with dropping emp_var_rate entirely.

- euribor3m: Strong correlation with nr_employemt and Portugal_Bank_Lending_Rate. We will drop the nr_emplopyed and Portugal_Bank_Lending_Rate features. Again, our Portugal_Unemployment_Rate feature will capture any impact of Unemployment, and the Portugal_Bank_Lending_Rate will be directly influenced by the euribor3m feautre. As such, it makes sense to drop these 2 features entirely.

- nr_employed: Strong correlation with Portugal_Bank_Lending_Rate. We have already decided to drop these 2 features.

- Income_tax: Strong correlation with Sales_Tax. Again it makes sense as to why these two variables would move in tandem. Rather than dropping 1 of them, we will look to add these 2 features together and make a combined tax variable. This would allow us to capture any nuances in the difference in movement of any 1 of these features, and would represent the total income and sales tax paid on average in the country. The new column will be called Combined_Tax.

- Portugal_Personal_Savings: Strong correlation with Portugal_Wages and Portugal_Unemployment_Rate. All 3 of these features would be important to our model, and so instead of dropping any of these, we will create a new feature called Feature_2 which will multiply all 3 of these features together.

- Portugal_Personal_Savings: Strong correlation with Portugal_Unemployment. We have already treated this correlation above.

### Modelling

In order to carry out the modelling, we split our final dataset into 3 subsets. Train (26,360 rows), Validation(6,590 rows) and Test (8,238 rows).

We initially ran a baseline Logistic Regression model on the original kaggle dataset, and obtained a ROC-AUC score of 73%. After adding the economic data for Portugal and the eurozone, our ROC-AUC score on the baseline model improved by 2% to 75%.

We then moved onto running additional models and ensemble methods to see how the dataset fared with those, keeping in mind that a large portion of the features are categorical.

 - Decision Trees
 - Gaussian Naive Bayes
 - Random Forest
 - Bagged Tree
 - XGBoost
 - Voting Classifiers

After hyperparameter tuning with GridSearch CV, we improved the performance using a Random Forest model, giving us a ROC-AUC score of 81%.

The following table shows a summary of all the models we ran.

### Evaluation

The figure below represents the importance of each feature on the hyperparameter tuned Random Forest model.

![](/Images/Feature_importance.png)

As expected, the most important feature influencing an individuals decision to place a term deposit is the interest rate the customer received in the euribor3m column. Furthermore, Feature_2, which is the additional feature we created out of Personal Savings, Wages and Unemployment Rate. Again, this is as expected, as these economic variables would represent an individuals ability to place a term deposit.

### Future Work

We have created a robust model which can accurately predict the effectiveness of a bank's marketing campaign. This model can easily be updated to swap out any economic data that would be considered relevant to an individual's uptake of a term deposit going forward. Moreover, the model can also be updated to asses marketing of a bank or financial institution's other products and can help the marketing manager design the campaign based on these results.


