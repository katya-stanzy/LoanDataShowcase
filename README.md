# LoanDataShowcase
Analysis of a bank loan datasetThis folder contains my work to analyse a loan dataset, inherited through an examination in one of my study courses.
The dataset contains 256 984 cases and 19 variables, all with a different level of missing and potentially erroneous data.

# The task
#### 1. Ingest, Explore and Clean.
The data has three main issues: (a) a large number of varied records that signify missing data and a (b) skewed    distribution of some variables with significant number of outliers; and (c) a higher number of 'Fully Paid' labels (19 014) compared with 'Charged Off' (11 448). 

(a) has been addressed in the cleaning stage; the final number of records is 152 330 for 16 variables.

(b) majority of outliers are found in Annual Income, Current Credit Balance and Maximum Open credit.

(c) may need to be addressed at the modellin stage.
#### 2. Create and Test (1.) a preliminary classification model with Logistic Regression using numerical variables only.
The resultant logistic model, after cross-validation, works best at classication of 'Fully Paid' cases. The 'Charged Off' had only a small proportion of cases assigned correctly: 1 317 (correct): 10 168 (wrong). NB: the confusion matrix here is such that 'Charged Off' is the positive case and 'Fully Paid' is the negative. 

The following can be done to resolve the issue:

(a) although data normalisation is not required for a Logistic Regression, a Robust standartization of numerical variables may improve the outcome.

(b) change model threshold to favour correct classification of 'Charged Off' cases.

(c) adjust model parameters to account for unequal number of positive and negative cases;

(d) split datasest into 'High Income' and 'Average Income' parts.
#### 3. Estimate input of numeric variables into the model with the help of the Average Marginal Effects in SHAP package.
Annual Income, Current Loan Amount, Monthly Debt, Maximum Open Credit -- are the most important vairables. The rest could be removed
#### 4. Create dummy variables from categorical features.
Done

#### 5. Create and Test (2.) a new Logistic Regression model using dummy variables as well as the most important numerical variables.
2 (a) is implemented. The model still favors 'Fully Paid' cases with a slightly improved rate of the correct classification for 'Charged Off': 3672 (correct) : 7813 (wrong)
