# Credit Classification Report

## Overview of the Analysis

The purpose of this analysis is to accurately predict the outcome of a borrower's loan. 
These predictions are based on the following known factors: loan size, interest rate, borrower income, debt-to-income ratio, number of accounts, derogatory marks, and total debt. 
This information hopefully can tell us if a loan will be healthy or high-risk.
The process of this analysis included several steps:
* Importing the data into Pandas.
* Separating data into independent and dependent variables.
* Examining the dataset for a balance of outcomes.
* Splitting the dataset into training and testing data for a logistic regression model.
* Running and fitting the training data to the logistic regression model.
* Comparing and analyzing predictions from the test data using the model to the actual test sample of the dataset.
* Increasing the size of the original dataset by resampling the underrepresented data points.
  * There are far less high-risk loans than healthy ones, so the high-risk loans were resampled to improve representation.
* Running the logistic regression again, on the new, larger dataset.
* Analyzing the outcome of the new regression to determine the accuracy and precision of the predictions, and comparing it to the previous model.

## Results

* Machine Learning Model 1 (original data):
  * Accuracy: 95.20%
  * Precision:
    * Healthy Loans: 99.70%
    * High-Risk Loans: 84.66%
  * Recall:
    * Healthy Loans: 99.46%
    * High-Risk Loans: 90.95%
* Machine Learning Model 2 (resampling):
  * Accuracy: 99.37%
  * Precision:
    * Healthy Loans: 99.98%
    * High-Risk Loans: 84.13%
  * Recall:
    * Healthy Loans: 99.38%
    * High-Risk Loans: 99.35%

## Summary

Based on these results, I would recommend using the second model. It is almost completely perfect at predicting healthy loans and includes almost no high-risk loans in its healthy loan predictions. 
Practically speaking, the goal of the bank should be to minimize risk, which would necessarily entail having as high a precision for healthy loans as possible and as high a recall for high-risk loans as possible. 
Maximizing these values will minimize the number of incorrectly classified real high-risk loans, which is the primary outcome the bank would wish to avoid.
Out of 18,653 loans predicted to be healthy, only 4 were actually high-risk. Now, the second model is slightly worse when it comes to predicting healthy loans as being high-risk, seen it its precision for high-risk loans of 84.13% (compared to the first model's of 84.66%).
This difference is very slight, but it will, on average, classify more borrowers who would have healthy loans as those who would be high risk. While the difference in precision for healthy loans between the two models is very slight, the crucial difference is the recall. 
As previously stated, only 4 of the actual high-risk loans were classified as healthy, meaning that the model caught almost all of the 619 high-risk loans in the test dataset. 
This recall value of 99.35% vs the first model's 90.95% is the main driver of the second model's higher accuracy score, and it is substantial.
The first model allowed 56 of the 619 high-risk loans to slip through the cracks, greater than an order of maginitude more than the second model.

Now, both models have a precision of ~84% for high-risk loans. Is this level of error a problem? In my estimation, it is not. The vast majority of people who have healthy loans are correctly predicted. 
Sure, there are going to be an amount of people whose loans would be classified as high-risk when in reality, they wouldn't be. 
But this fraction is exceedingly small when taken as a part of the entire group of healthy loans (1 minus the recall of healthy loans: 0.54% in the first model and 0.62% in the second).
The most concerning source of error in the original model, the recall of high-risk loans, was redressed through resampling, bringing the overall accuracy up to 99.37%.

In conclusion, the second model provides an exceedingly accurate prediction of healthy loans, and allows almost zero high-risk loans into its predictions of healthy loans. I would definitely recommend this second model be utilized fo predicting future borrowers' loan outcomes.
