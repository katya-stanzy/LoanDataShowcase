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

An EDA has demonstrated that Loan Term, Purpose, Current Loan Amount, Monthly Debt and Annual Income have a high association with Charged Off loans.

#### 2. Create and test a preliminary classification model with Logistic Regression using numerical variables only.
The resultant logistic model, after cross-validation, works best at the classification of 'Fully Paid' cases. The 'Charged Off' had only a small proportion of cases assigned correctly: 1 317 (correct): 10 168 (wrong). NB: the confusion matrix here is such that 'Charged Off' is the positive case and 'Fully Paid' is negative. 

The following can be done to resolve the issue:

(a) although data normalisation is not required for a Logistic Regression, a Robust standardization of numerical variables may improve the outcome.

(b) change model parameters to favour the correct classification of 'Charged Off' cases.

(c) adjust model parameters to account for an unequal number of positive and negative cases;

(d) split dataset into 'High Income' and 'Low to Average Income' parts.
#### 3. Estimate input of numeric variables into the model with the help of the Average Marginal Effects in the SHAP package.
Annual Income, Current Loan Amount, Monthly Debt, Maximum Open Credit are the most important among unscaled numerical variables. 
#### 4. Create dummy variables from categorical features.
Done

#### 5. Create and Test (2.) a new Logistic Regression model using dummy variables and the most important numerical variables.
2a and 2c have been implemented together with balancing the sample size. The model performs a lot better for 'Charged Off': 6589 (correct) : 4896 (wrong). Selection of features to reflect results the exploratory data analysis (EDA)did not improve the model.
