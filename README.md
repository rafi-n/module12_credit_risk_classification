# Module 12 Challenge: Credit Risk Classification

## Overview of the Analysis

The following describes the analysis completed for the machine learning models used in this Challenge.

### Purpose of the analysis
The purpose of the analysis is to predict the creditworthiness of borrowers based on a given set of historical data.

* Explanation of the financial information the dataset included, and what was predicted:
  1. Loan Size (`loan_size`): the amount of the loan requested
  2. Interest Rate (`interest_rate`): interest rate applied to loan
  3. Borrower Income (`borrower_income`): borrower's annual income
  4. Debt to Income Ratio (`debt_to_income`): ratio of all debt to income
  5. Number of Accounts (`num_of_accounts`): number of accounts held by borrower
  6. Derogatory Marks (`derogatory_marks`): tabulation of negative credit information (i.e. late payment, foreclosure, etc.) that may be deemed a credit risk
  7. Total Debt (`total_debt`): sum of all debts held by borrower
  8. Loan status (`loan_status`): what we're trying to predict; whether the loan is healthy (0) or risky (1)

* Information about of predicted classes (`loan_status`):

  The information to be predicted is the loan status (`loan_status`) which represents the creditworthiness of a borrower. If the `loan_status` is 0, then the loan is in good standing. However, if the `loan_status` is 1, then it is at risk of defaulting.
  
  The original data has an imbalanced number of healthy loans vs risky:
  `y.value_counts()`
  `> loan_status`
  `> 0  75036`
  `> 1  2500`
  `> Name: count, dtype: int64`
  This imbalance will bias our results in favor of healthy loans because there are more healthy (0) loans in the dataset.

### Process
A synopsis of the machine learning methodology is as follows:
1. Separate the data into features and targets
2. Create training and test sets for both features and targets
3. Fit a logistic regression model (`LogisticRegression`) with the training data
4. Make predictions
5. Run random oversampling (`RandomOverSampler`) on the training targets
6. Repeat steps 3-4 (inclusive), using the oversampled training data

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * This model uses the `LogisticRegression` model to fit and predict classes based on the *original* data
  * Description of Model 1 Balanced Accuracy, Precision, and Recall scores.

    |   | Precision  | Recall  |
    |:---|:---:|:---:|
    | Healthy  | 1.00  | 0.99  |
    | Risky  | 0.85  | 0.91  | 
* Machine Learning Model 2:
  * This model uses the `LogisticRegression` model to fit and predict classes based on the *resampled* data
  * Description of Model 2 Balanced Accuracy, Precision, and Recall scores.

    |   | Precision  | Recall  |
    |:---|:---:|:---:|
    | Healthy  | 1.00  | 0.99  |
    | Risky  | 0.84  | 0.99  | 
## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.
