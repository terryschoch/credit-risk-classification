# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Description of Model 1 Accuracy, Precision, and Recall scores.



* Machine Learning Model 2:
  * Description of Model 2 Accuracy, Precision, and Recall scores.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.



## Overview of the Analysis
### The Objective
Our goal in this challenge was to build a supervised machine learning model which can accurately identify credit risk in the sense of whether a client is creditworthy or not in regard to seeking a loan approval. 

There are two main risks inherent in this type of model:
1. Wrongly identifying a person as a credit risk when they are actually likely to repay the loan. This represents a profit opportunity loss.
2. Approving a loan to a person who is actually a credit risk and unlikely to repay the loan

### The Data
The model was trained by using past lending data which includes inforation such as loan size and interest rate as well as the clients' income, total debt, debt to income ratio, their number of accounts held and whether they had any prior flags on their accounts. Together, these pieces of information for each client represents the "features".

Also included within the data was the loan status, or ultimate outcome of whether is was repaid or defaulted. This too is the status that our model sought to predict and this category would then be designated as our "labels set" in the machine learning model.

### The Process
After an initial review of the csv which contained the data, the above identifying features and labels became the first step. Once identified, the data was seperated respectively and then reviewed again. (ie. A basic check on the labels data via "value_counts" for healthy loans vs high risk of defalt was applied).

The data was next split into training and testing datasets using "train_test_split"/
From here, a logistic regression model was instantiated and then fit to the training data to hone the machine learning model. Test predictions were then produced and from there we were able to evaluate the efficacy of the model vs our quarantined test data.

* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

## Results
#### Machine Learning Model Scores:
* Machine Learning Model 1 (Original Data):
  * Description of Model 1 Accuracy, Precision, and Recall scores.
- Accuracy Score: 100%
- Precision Score: 
  - Healthy Loans: 100% 
  - High Risk Loans: 87%
  - Macro Avg: 94%
  - Weighted Avg: 99%
- Recall Score: 
  - Healthy Loans: 100%
  - High Risk Loans: 89%
  - Macro Avg: 94%
  - Weighted Avg: 99%
-F1 Score:
  - Healthy Loans: 100%
  - High Risk Loans: 88%
  - Macro Avg: 94%
  - Weighted Avg: 99%
  


* Machine Learning Model 2 (Resampled Data):
  * Description of Model 2 Accuracy, Precision, and Recall scores.
- Accuracy Score: 100%
- Precision Score: 
  - Healthy Loans: 100% 
  - High Risk Loans: 87%
  - Macro Avg: 94%
  - Weighted Avg: 100%
- Recall Score: 
  - Healthy Loans: 100%
  - High Risk Loans: 100%
  - Macro Avg: 100%
  - Weighted Avg: 100%
-F1 Score:
  - Healthy Loans: 100%
  - High Risk Loans: 93%
  - Macro Avg: 96%
  - Weighted Avg: 100%



## Summary
- **Question: How well do the logistic regression models predict both the 0 (healthy loan) and 1 (high-risk loan) labels?**

- **Answer:** Based on the original test data, the logistic regression model does a great job of predicting healthy loans, achieving 100% across the board in precision, recall and F1. However, the precision accuracy drops to 87% on High Risk Loans which is a significant drop relatively speaking. The recall rate also drops to 89% and the F1 score for high risk loans predictions is 88%.
This represents a fairly signficant miss rate in the prediction model in regard to accurately predicting high risk loans, particularily the 89% recall rate. But given the cost opportunity of profit gained by offering succesful loans vs the cost of covering a loss for a failed loan, the model still does a good job overall and should be considered viable given the macro average for the f1-score is 94% and the weighted average an even better 99%.

- **Answer:** Again, in using the oversampled data, the logistic regression model does a great job of predicting healthy loans. Achieving 100% across the board in precision (TP/(TP+FP)), recall (TP/(TP+FN)) and F1 (2(PrecisionRecall)/(Precision+Recall)) in this regard.
However, the precision score drops to 87% on High Risk Loans this time, suggesting there are a fair number of False Positives being predicted, or clients being misidentified as high risk loans. The recall remains perfect at 100%. As a result, the overall F1 score for high risk loans registers at 93%.
This still represents a signficant miss rate in the prediction model, but still keeping the focus on the cost opportunity of profit gained by offering succesful loans vs the cost of covering a loss for a failed loan, the model does a good job and should be considered quite viable as a means of determining loan approvals.
