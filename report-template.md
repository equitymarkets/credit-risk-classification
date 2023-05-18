# Module 12: Loans 

## Overview of the Analysis

This analysis set out to test a new loan decision system used by a bank to grant credit to consumers. Loans fit into one of two categories: (0) the loan is healthy, or (1) the loan is not healthy. To maximize value, we must minimize the chances of false positives and false negatives in both the healthy loan and unhealthy loan categories. Out of our predictions for 75036 healthy loans and 2500 unhealthy loans, we would like to see the highest accuracy possible. 

Our stages in the machine learning model are as follows: 1. Read the data from a csv into a pandas dataframe named 'lending_df'. 2. Create a features set (x values - all columns but our target) and a labels set (y - our target). 3. Check the balance of our labels by using the value_counts function. 4. Split the data into training and testing datasets. 4. Perform our logical regression by fitting the model, saving the predictions, and eveluating the performance by printing a balanced accuracy score, the confusion matrix, and a classification report. We repeat step 4 with the RandomOverSampler module at the end, to further curate the data. 



## Results

To analyze the models, we use a classification report. 

The classification report uses the column 'precision', found with the formula (True Positive/(True Positive/False Positive)). The Original model scores a 1.00 score for good loans (100% accuracy) and a .87 score for bad loans (87% accuracy). We achaive the same results with the Resampled model. Precision is used when the cost of false positives is high. The bank would rather not loan to someone who will not repay (false 0) or deny someone who would repay (false 1). 

The column 'recall' is defined by the formula (True Positive/(True Positive/False Negative)). In other words, we weight this datapoint if the cost of a false negative is high. We can see here that the Resampled data shined, coming in at 1.00 and .99 for the 0 and 1 values vs. 1.00 and .89 for the original data model. 

The F1 score combines the two numbers, so we can see why the Resampled data still did better in this category. Given the formula ((Precision * Recall)/(Precision + Recall)), the resampled data received scores of 1.00 and .93, whereas the original scored 1.00 and .88. 

Accuracy scores paint a similar picture: While the Original model scored well at .9443, the Resample did much better, with an accuracy score of .9936. 


## Summary

I recommend the model with the Resampled Data:
* It performs better when predicting the occurance of bad loans. Bad loans should be avoided at all costs. 
* It is probably more important to predict the "1"s, since no business wanted to have bad loans on its balance sheet. However, we must also predict the "0"s, because without making loans we are not in business, and denying a loan to someone who would pay it back is an opportunity cost-the interest income will simply flow to a competing firm. 