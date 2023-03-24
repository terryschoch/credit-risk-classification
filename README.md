# credit-risk-classification

## Overview 
### The Objective
The goal of this analysis was to build and train a supervised machine learning model using historical lending data and then to evaluate whether it could accurately identify credit risk in the sense of whether a client would be creditworthy or not in regard to seeking a loan approval. 

* There are two keys risks inherent in creating this type of model:
  1. Wrongly identifying a person as a credit risk when they are actually likely to repay the loan and should be classified as a "healthy loan" instead. This represents a profit opportunity loss.
  2. Approving a loan to a person who is actually a credit risk and unlikely to repay the loan, classifying them as a healthy loan when they should in fact be regarded as "high risk".


### The Data
The model was trained by using the aforementioned past lending data which included information such as loan size and its interest rate as well as the clients' income, total debt, debt to income ratio, their number of accounts held and whether they had any prior flags on their accounts. Together, these pieces of information represent the ***features***.

Also included was the *loan status*, or ultimate outcome of whether the client's loan status was deemed *healthy* (0) or *high-risk* (1). This too was the status that our model sought to predict and this category would then be designated as our ***labels set*** in the machine learning model.

### The Preprocessing
After loading and conducting an initial review of the *lending_data.csv*, the above identifying *features* and *labels* became the first step completed. Once identified, the data was seperated into ***X*** and ***y*** respectively and then reviewed again.  A basic check on the balance of the labels data (y) via the *value_counts* function for healthy loans vs high risk of defalt was applied.

The data was next split into training (***X_train, y_train***) and testing (***X_test, y_test***) datasets using the *train_test_split* function.

From here, a *logistic regression model* was instantiated and then fit to the original training data to hone the machine learning model. Next, predictions for the test data labels using the testing feature data (***X_test***) were made and we were then able to evaluate the efficacy of the model vs our quarantined test labels (***y_test***).

The performance evaluation was conducted by calculating the balaned accuracy score, generating a confusion matrix, and printing a classification report. This allowed us to answer the question: *"How well does the logistic regression model predict both the 0 (healthy loan) and 1 (high-risk loan) labels?"*

We next trained and evaluated a second *logistic regression model* with resampled data which we acquired by using *RandomOverSampler* from the *imbalanced-learn library*. The model was fit to the resampled data and predictions again made followed by a performance evaluation via calculating the accuracy score, generating a confusion matrix and printing the classification report. The same question for the first model was posed and answered for the resampled model.


## Results
### Machine Learning Model Scores:
**Machine Learning Model 1 (Original Data):**
  - Balanced Accuracy Score: **99.24%**
  - Precision Score: 
    - Healthy Loans: **100%**
    - High Risk Loans: **87%**
  - Recall Score: 
    - Healthy Loans: **100%**
    - High Risk Loans: **89%**
  

**Machine Learning Model 2 (Resampled Data):**
  - Balanced Accuracy Score: **99.52%
  - Precision Score: 
    - Healthy Loans: **100%** 
    - High Risk Loans: **87%**  
  - Recall Score: 
    - Healthy Loans: **100%**
    - High Risk Loans: **100%**
    

## Summary
Based on the original test data, the logistic regression model did a great job by achieving a 99.2% balanced accuracy score. In regard to predicting healthy loans, it reached 100% across the board in precision (TP/(TP+FP)), recall (TP/(TP+FN)) and F1 (2(PrecisionRecall)/(Precision+Recall)). However, the precision accuracy dropped to 87% on High Risk Loans which was a significant decline relatively speaking. The recall rate also dropped to 89% and the F1 score for high risk loans predictions was just 88% as a result.

This represented a fairly signficant miss rate in the prediction model in regard to accurately predicting high risk loans, particularily the 89% recall rate was concerning. But given the cost opportunity of profit gained by offering succesful loans vs the cost of covering a loss for a failed loan, the model still did a reasonable job overall and could be considered viable given the macro average for the f1-score was 94% and the weighted average an even better 99%.

Conversely, the resampled data model achieved a slighty better 99.5% balanced accuracy rate and an identical 100% across the board in precision, recall and F1 for Healthy Loans. However, while the precision score again dropped to 87%, the recall score was a perfect 100% on this model and the F1 score was 93% as a result. While the miss rate was still significant and a fair number of false positives were registered for High Risk loans as shown by the precission score, that there were no unidentified high risk loans was a significant improvement. The opportunity cost in this scenario was such that it would likely greatly mitigate the signficance of the precision inaccuracy. 

Moreover, the far superior recall rate with the resampled data model indicated that overall clearly this should be the model recommendeded for use.
