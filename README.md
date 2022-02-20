# LoanDataDataset
Analysis of a bank loan dataset. The dataset contains 256 984 cases and 19 variables, all with a different level of missing and potentially erroneous data.

Dataset description and a report are to follow.

# The task
The objective of the analysis is to create a model that would identify loans that are most likely to default.

#### 1. Ingest, Explore and Clean.
Problems with the dataset:

(a) a large number of varied records that signify missing data;

(b) skewed distribution of some variables with a significant number of outliers; and 

(c) an unbalanced sample: there are 'Fully Paid' labels (19 014) compared with 'Charged Off' (11 448). 

After cleaning, there is 152 330 cases and 16 variables.

An exploratory data analysis (EDA) has demonstrated that Loan Term, Purpose, Current Loan Amount, Monthly Debt and Annual Income have a high association with Charged Off loans.

#### 2. Create and test a preliminary classification model with Logistic Regression using numerical variables only.
The resultant logistic model, after cross-validation, works best at the classification of 'Fully Paid' cases. The 'Charged Off' had only a small proportion of cases assigned correctly: 1 317 (correct): 10 168 (wrong).

The following can be done to resolve the issue:

(a) A Robust standardization of numerical variables may improve the outcome;

(b) Change model parameters to account for an unequal number of positive and negative cases;

(c) split dataset into 'High Income' and 'Low to Average Income' parts or take log of skewed variables.
#### 3. Estimate input of numeric variables into the model with the help of the Average Marginal Effects in the SHAP package.
Annual Income, Current Loan Amount, Monthly Debt, Maximum Open Credit are the most important among unscaled numerical variables. 
#### 4. Create dummy variables from categorical features.
Done

#### 5. Create and test a new Logistic Regression model using dummy variables and the most important numerical variables.
2 has been implemented together with balancing the sample size (LogisticRegression(class_weight='balanced', max_iter=10000)). 
After training, the best model returned accuracy 0.66.

On testing, the model performs a lot better for the 'Charged Off' cases: 6589 (correct) : 4896 (wrong). 
The model performance in respect of the  charged off (negative) loans is moderate: negative recall is 0.57 (compared with initial 0.11), positive precision of 0.73, negative F1 = 0.56. (compared with initial 0.19).

An explicit oversampling of the minority cases did not change the model outcome. 

#### 6. Classification with Boosted Random Forest
BRF was trained using normalised data and a balanced sample, with undersampled majority cases. The best model had learning rate of 1 and returned accuracy 0.70.
On testing, BRF has performed a lot better, with true negative : false positive = 7559 : 3943; positive precision = 0.75, negative recall = 0.66; negative F1 = 0.58.

Feature importance in the descending order:
Credit Score, Annual Income, Maximum Open Credit, Monthly Debt, Current Loan Amount, Current Credit Balance,Number of Open Accounts, Years of Credit History, Bankruptcies, Tax Liens, Term: Long term, Home Ownership:Rent, Purpose: Business Loan, Purpose: Other.

# Loan Data Database
A database was created by importing a clean .csv file into SQLight Studio. 
The database contains:
Fact Table (17 columns)
Home Ownership (2 columns)
Loan Status (2 columns)
Loan Term (2 columns)
Purpoose (2 columns)
Years in Current Job (2 columns)

As the DBS is over 5 MB, it is not in the git folder.
The SQL work is shown in two script files: SQLight_script_1 and SQLight_script_2
