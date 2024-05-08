# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.

The goal was to understand how our predictive model can predict high risk/healthy loans from a number of numerical qualities and features. 

* Explain what financial information the data was on, and what you needed to predict.

We had loan size, interest rate, borrower income, a debt to income ratio, number of accounts, "derogatory marks", total debt, and loan status. We were trying to predict whether or not the loan was healthy or high risk - which was the final column, loan status. Originally, it was assigned a value of 1 for high risk loan and 0 for healthy loans. Most of the loans were healthy loans, by about a 30:1 rate. 

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).

The main variable we were trying to predict was the loan status. We wanted to essentially be able to predict whether or not a loan would be a risky or healthy invesstment, based upon the data we could train off of. 

* Describe the stages of the machine learning process you went through as part of this analysis.

To be honest, I followed the template notebook fairly exactly, just working through the data cleaning process to set up our features X and out target y, and then after splitting those into training/test data, we applied a Logisitic Regression model with the y_test to create the predictions.

* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any other algorithms).

Logistic Regression is a method that works well with binary dependent variables - in this case, it would be out target - loan status. 

## Results


* Machine Learning Model 1: Logisitic Regression
    * Description of Model 1 Accuracy, Precision, and Recall scores.


This is more impactful - the minority value is often the one we are interested in being the "true/positive case".


For High-Risk loans = 0 and healthy loans to 1, we had:

True Positives: (Actual 0, Predicted 0): 563

True Negatives: (Actual 1, Predicted 1): 18663

False Positives: (Actual 1, Predicted 0): 102

False Negatives: (Actual 0, Predicted 1): 56

Precision: $ \frac{\text{\# True Positive}}{\text{\# True Positive + \# False Positive}} $. Here, our precision was 0.85 for high risk loans : $\frac{563}{563+102}$. Essentially, out of all the loans that we labeled as high risk, ~85% of these loans were actually high-risk. 15% of the time if our model was to label a set of features for a loan as high-risk, it would actually be a healthy loan. From a financial perspective, it definitely makes sense to have precision be more stringent here. Higher precision for healthy loans means a lower liklihood to lose money with a bad investment, while less precision on high-risk loans just means the volume of healthy loans you are giving out is reduced slightly. In the first case high precision means you minimize losses, and the second case, high precision means you are missing out on fewer healthy loan/profitable opportunities. 

In other words: Out of 100 loans that we predicted to be high risk, we would find 85 loans to be actually high risk. 

Recall the definition of recall: $ \frac{\text{\# True Positive}}{\text{\# True Positive + \# False Negative}} $. For the high-risk loans, our recall was $\frac{563}{563+56}$ which is ~0.91. Essentially, we captured 91% of the actually high-risk loans with our predictions. Recall is useful if getting a false negative has a high cost. In this case, a false negative means a high risk loan that we predicted was actually healthy. That absolutely has a high cost, and thus the recall measurement is important when we consider high-risk loans. Personally, 91% seems like good odds, but I'm not sure what the standards are for the banking industry. 

In other words: Out of 100 loans that are actually high risk, we would predict that 91 of those are high risk. 


The F1 Score gives you a balance between Precision and Recall: $\text{F1} = 2 \times \frac{\text{Precision} * \text{Recall}}{\text{Precision} + \text{Recall} } $. Here that gives us 0.88.

The support tells you the number of actual occurences of the class in the specified dataset. We can see the support for high risk loans is $563 + 56 = 619$ because the actual occurences of healthy loans in the data set is the sum of the True Positives and the False Negatives. 

The accuracy metric does not change if we swap high-risk/healthy loans for 0/1. So the accuracy remains around 99.2%.


## Summary

I recommend this model, but I would want to do more analysis. We are able to capture 91% of the actually high risk loans with our predictions. Further, we were able to capture an extrmely high percentage of the healthy loans. The analysis I would want to consider would be to sum combinations of the prospective profits/losses of loans the company/bank can accept over various periods (assuming all of these are 5/10/30 year loans) and produce projected results of profit/loss. 

But it is worth noting, that these features alone are not sufficient in accepting healthy loans in general. What could have been a healthy loan in the past might not be a healthy loan in the future, due to features not encapsulated by our training data. 
