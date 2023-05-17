# Module 12 Challenge: Credit Risk Classification

## Overview of the Analysis

The following analysis will explore the results of random oversampling on an imbalanced dataset. Imbalanced data is inherently biased toward the result with most occurences.

### Purpose of the analysis
The purpose of the analysis is to predict the creditworthiness of borrowers based on a given set of historical data. However, the data is imbalanced with more healthy loans than risky. In order to fix the imbalance, we will employ random oversampling to see if the results improve.

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

The following is a breakdown of the metrics of each machine learning model.

* Machine Learning Model 1:
  * This model uses the `LogisticRegression` model to fit and predict classes based on the *original* data
  * Description of Model 1 Balanced Accuracy, Precision, and Recall scores:

    ||Precision|Recall|
    |:---|:---:|:---:|
    |Healthy|1.00|0.99|
    |Risky|0.85|0.91|
    
    Balanced Accuracy: 0.95
  
* Machine Learning Model 2:
  * This model uses the `LogisticRegression` model to fit and predict classes based on the *resampled* data
  * Description of Model 2 Balanced Accuracy, Precision, and Recall scores:

    ||Precision|Recall|
    |:---|:---:|:---:|
    |Healthy|1.00|0.99|
    |Risky|0.84|0.99|
    
    Balanced Accuracy: 0.99
    
## Summary

The most important aspect of this analysis is the risky loans. This is what we need to predict as accurately as possible. We must also ensure that the recall for all loans are high because recall is dependent on false negatives. False negatives when predicting risky loans would mean that a risky loan is being predicted as healthy - the worst outcome!

Based on the results above, the best model is Machine Learning Model 2, which includes random oversampling. The balanced accuracy, which is the mean of the recalls for both classes, is high at 99%. Precision for this model preforms almost identically for both classes as Model 1. Precision varies with the number of false positives, so in the case of risky loans, there are a fair number of healthy loans being flagged as risky. This is acceptable for the lending service because it's better to not give a loan than to give a loan that ends up defaulting. However false negatives, as mentioned, means that risky loans are being predicted as healthy and can be detrimental to the success of the business. Model 2 reduces the false negatives and brings the recall up to 0.99 from 0.91 in Model 1.

I would not recommend the lending service use any of the models. The goal of any business is to maximize its profits. While Model 2, improves recall, there is still the issue of precision for risky loans. There is a fair proportion 16% of loans being classified as risky, which are actually healthy. This could lead to the loss of business for those cases. A new model which improves upon the precision must be found to provide better returns for the business.