## Credit Card Fraud Detection

A project on techniques with imbalanced classification

## Project Introduction

It is often that the data we retrieve have imbalanced label and we are asked to make classification. These scenarios are troublesome since not only the models we usally use bring poor result, but also the evaluation metric we often used, accuracy, is not adequate for imbalanced data sets due to the impact of the minority class. This project aims to demonstrate some techniques used to combat these situations, such as resampling or cluster before predicting, as well as using PR (Precision-Recall) curve to evaluate model. The approaches for the project are :


1. Do basic EDA and feature engineering.
2. Randomly split the dataset into train, validation, and test set.
3. Resample the dataset.
4. Train on resampled train set then predict and evaluate with validation set.
5. Predict and evaluate with validation set.
6. Try other different models.
7. Compare the difference between the predictions and choose the best model.
8. Find the optimised threshold of the chosen model.
9. Predict on test set to report final result.

## Data Description


The project take use of The Credit Card Fraud Data on Kaggle, the data description on the webpage is as followed :

The datasets contains transactions made by credit cards in September 2013 by european cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.
It contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, we cannot provide the original features and more background information about the data. Features V1, V2, ... V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-senstive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.
Given the class imbalance ratio, we recommend measuring the accuracy using the Area Under the Precision-Recall Curve (AUPRC). Confusion matrix accuracy is not meaningful for unbalanced classification.

The dataset has been collected and analysed during a research collaboration of Worldline and the Machine Learning Group of ULB (Université Libre de Bruxelles) on big data mining and fraud detection. 


## Exploratory Data Analysis

The purpose of EDA is to enhance our understanding of trends in the dataset without involving complicated machine learning models. From these column values, we can see that there are some very useful correlations present within our new dataset. For example, V2 and V5 are highly negatively correlated with the feature called Amount. We also see some correlation with V20 and Amount. This gives us a deeper understanding of the Data available to us.
The mean value of all transactions is $88.35 while the largest transaction $25,691.
The distribution of the monetary value of all transactions is heavily right-skewed.
Fraud transaction seem to have higher mean than non-fraud ,meaning that this feature 
Would likely is useful to use in predictive model.
The median for valid transaction is higher than fraud, this mean the distribution of value for class 0 
Is left skewed.
Feature distribution helps in understanding what kind of feature we are dealing with.

- We split the dataset into %70 training set and %30 test set.
We have identified input feature and target variable, we will separate them 
Into two object X, y .

- We start to preprocess the features Time, Amount with StandardScaler.
The StandardScaler will transform the data ,so its distribution will have a 
Mean 0 and standard deviation of 1.
Machine learning can’t estimate correct output without standardization.
Before going to resampling approach, we need to normalize the Amount features.

- In this project I used SMOTE(synthetic minority over-sampling).
Smote uses characteristic of nearest neighbors of fraud cases
To create new synthetic fraud cases.

We know crating a training dataset that will allow our algorithm
To pick up the specific characteristic that make a transactions more or less
Likely to be fraudulent.

Using the original data set that is a not goo idea, because %99 our transaction
Is non-fraudulent and algorithms that always predict that transaction is non fraudulent 
With high accuracy.
We do not want a %99 accuracy with non-fraudulent .we want to detec t fraudulent transaction.
With oversampling we will balance class distribution and force the algorithm to detect fraudulent transactions.

To create our balanced training data set, I took all of the fraudulent transaction in our data set and counted them.
Then I randomly selected the same number of non-fraudulent transactions and concatenated the two.
We will see the output the class distribution after shuffling .
We now we reduced the number of transaction and having outlier skew.


## Modeling

we are using XGBoost, Isolation Forest, RandomForest, Local Outlier Factor to perform my predictions. In this project I would like to compare 2 machine learning method:
- Random Forest
- XGBoost

The Random Forest classification report is :
With the Random Forest Classifier with SMOTE Model, we have:
- The model is able to predict only 92% of fraudulent transactions .(precision score)
- 84978 transactions classified as valid and were actually valid(True Positive)(here 84980 are the number of CORRECTLY PREDICTED safe cases).
- 11 transactions classified as fraud but that were really valid(type 1 error)( here 9 are the number of MISCLASSIFIED safe cases. Hence 9 safe cases were misclassified as a fraud. This is potentially less dangerous as it’s better to stop some safe transactions with the slightest chance of fraud.;
- 30 transactions classified as valid, but which were fraud (type 2 error)(here 30 are the number of MISCLASSIFIED fraud cases. hence 30 fraud cases were misclassified as safe. This is very dangerous because we are letting the fraud cases pass through. This can cause a huge loss to the organization.;
- 99 transactions classified as fraud and were actually fraud.
 we have 129 transactions as fraud.
- Look at the precision, recall, f1_score .The accuracy looks good.


## Evaluation metrics:


We use evaluation metrics for evaluating the performance of the model.
I evaluated the performance of the model using Recall, precision, f1-score.
We have not used accuracy ,because accuracy usually gives us a misleading conclusion.
When there is unbalanced class distribution.

In confusion matrix we have:
- Accuracy: The measure of correct predictions made by the model.

- Sensitivity(Recall)or(True positive rate): the ratio of correct positive predictions
To the total positive examples.

- Specificity(True Negative):the ratio of correctly identified non-fraud cases 
To total non-fraud cases.

- Precision: the ratio of correct positive prediction to the total predicted positive.

- Hyperparameter are important, they have a significant impact on the performance 
Of the model.




## COCLUSION AND FUTURE ENHANCEMENTS:


## COCLUSION

4 kind of models of machine learning has been used to examine their performance on a dataset which contains real world transaction data. Comparison between these algorithms(LOF, IF, RF, XGB) helped us to decide Random Forest and XGB which turned out to be both accurate and cost effective at the same time. While we couldn't reach out goal of 100% accuracy in fraud detection, we did end up creating a system that can, with enough time and data, get very close to that goal. As with any such project, there is some room for improvement here.



## FUTURE ENHANCEMENTS

This model can further be improved with the addition of more algorithms into it. However, the output of these algorithms needs to be in the same format as the others. 
More room for improvement can be found in the dataset. As demonstrated before, the precision of the algorithms increases when the size of dataset is increased. Hence, more data will surely make the model more accurate in detecting frauds and reduce the number of false positives. 




## Link to Jupyter Notebook in Repository

https://drive.google.com/file/d/1OWgSR99AwIBez99juSgQMZUog4yeIJVT/view?usp=sharing
https://github.com/Nastaranra/Springboard_Project/blob/master/Unit%2020/Capstone_Two_Documentation.ipynb
