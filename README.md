# LoanDataShowcase
Analysis of a bank loan dataset

This folder contains my work to analyse a loan dataset, inherited through an examination in one of my study courses.
The dataset contains 256,984 cases and 19 variables, all with a different level of missing and potentially erroneous data.

# The task
#### 1. Ingest, Explore and Clean.
The data has three main issues: (a) a large number of varied records that signify missing data and a (b) skewed    distribution of some variables with significant number of outliers; and (c) a much higher number of 'Fully Paid' labels compared with 'Charged Off'. 

(a) has been addressed in the cleaning stage; the final number of records is 152307 for 16 variables.

(b) majority of outliers are found in Annual Income, Current Credit Balance and Maximum Open credit. As these represent genuine cases, they are left in the data to be dealt with at a later stage.
#### 2. Create and Test (1.) a preliminary classification model with Logistic Regression using numerical variables only.
The resultant logistic model, after cross-validation, works best at classication of 'Fully Paid' cases. The 'Charged Off' had only a small proportion of cases assigned correctly: 3592 (correct): 7856 (wrong). NB: the confusion matrix here is such that 'Charged Off' is the positive case and 'Fully Paid' is the negative.

The following can be done to resolve the issue:

(a) adjust model parameters to account for unequal number of positive and negative cases;

(b) split datasest into 'High Income' and 'Average Income' parts.

(c) although data normalisation is not required for a Logistic Regression, a Robust standartization of numerical variables may improve the outcome.
#### 3. Estimate input of numeric variables into the model with the help of the Average Marginal Effects in SHAP package.
Mean values of Maximum Credit, Annual Income, Years of Credit History, Current Loan Amount, Monthly Debt were found important for the model.  Max values of Maximum Credit and Annual Income, i.e. different set of variables, were also found important. Tax Liens, Bnkruptcies, Nimber of Credit Problems, Number of Open Accounts, Current Credit Balance do not add to the model.
#### 4. Create dummy variables from categorical features.
#### 5. Create and Test (2.) a new Logistic Regression model using dummy variables as well as the most important numerical variables.
 
