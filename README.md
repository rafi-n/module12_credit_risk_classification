# Module 12 Challenge: Credit Risk Classification

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
The purpose of the analysis is to predict the creditworthiness of borrowers based on a given set of historical data.

* Explain what financial information the data was on, and what you needed to predict.
The data included the following:
1. Loan Size (`loan_size`): the amount of the loan requested
2. Interest Rate (`interest_rate`): interest rate applied to loan
3. Borrower Income (`borrower_income`): borrower's annual income
4. Debt to Income Ratio (`debt_to_income`): ratio of all debt to income
5. Number of Accounts (`num_of_accounts`): number of accounts held by borrower
6. Derogatory Marks (`derogatory_marks`): tabulation of negative credit information (i.e. late payment, foreclosure, etc.) that may be deemed a credit risk
7. Total Debt (`total_debt`): sum of all debts held by borrower
8. Loan status (`loan_status`): whether loan is healthy (0) or risky (1)

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
The information to be predicted is the loan status (`loan_status`) which represents the creditworthiness of a borrower. If the `loan_status` is 0, then the
loan is in good standing. However, if the `loan_status` is 1, then it is at risk of defaulting.

* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).
The analysis uses Logistic Regression twice: once on the original data set and again with random oversampling. A synopsis of the methodology is as follows:
1. Separate the data into features and targets
2. Create training and test sets for both features and targets
3. Fit a logistic regression model (`LogisticRegression`) with the training data
4. Make predictions
5. Run random oversampling (`RandomOverSampler`) on the training targets
6. Repeat steps 3-4 (inclusive), using the oversampled training data

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Description of Model 1 Balanced Accuracy, Precision, and Recall scores.



* Machine Learning Model 2:
  * Description of Model 2 Balanced Accuracy, Precision, and Recall scores.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.
