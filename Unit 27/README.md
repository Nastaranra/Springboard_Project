## Fake News Detection

## Overview


The topic of fake news detection on social media has recently attracted tremendous attention. The basic countermeasure of comparing websites against a list of labeled fake news sources is inflexible, and so a machine learning approach is desirable. Our project aims to use Natural Language Processing to detect fake news directly, based on the text content of news articles.

## Problem Definition

Develop a machine learning program to identify when a news source may be producing fake news. We aim to use a corpus of labeled real and fake new articles to build a classifier that can make decisions about information based on the content from the corpus. The model will focus on identifying fake news sources, based on multiple articles originating from a source. Once a source is labeled as a producer of fake news, we can predict with high confidence that any future articles from that source will also be fake news. Focusing on sources widens our article misclassification tolerance, because we will have multiple data points coming from each source.
The intended application of the project is for use in applying visibility weights in social media. Using weights produced by this model, social networks can make stories which are highly likely to be fake news less visible.

## Dependencies

• python 3.x

• nltk

• numpy

• sklearn

• scipy

• pandas

• spacy

## Dataset

We get the ground truth data from https://www.kaggle.com/arminehn/rumor-citation/data#. We only use Snopes URLs since the labels of each news were clearly presented. Only "true" or "false" labels were kept. We randomly select 281 true news and 281 false news and crawl the Snope website for additional content.


## Phases of the project

Building machine learning models to detect fake news
Using multiple data sources to detect fake news.

## Exploratory Data Analysis:


•	The purpose of EDA is to enhance our understanding of trends in the dataset without involving complicated machine learning models. 

•	The last stage of my exploratory data analysis of the text is Word cloud analysis. Word cloud is a great way to represent text data. The size and color of each word that appears in the Word cloud indicate its frequency or importance.

•	In the results, we can see how often some words used in the news text in fake or real news.


## Prediction Algorithms 

We implemented five different algorithms from scratch for the prediction model which were: Logistic Regression model and the Naïve Bayes classifier model, PassiveAgressiveClassifier model, Support Vector Machine model, Random Forest. 


## Evaluation Metrics 

We used the following three metrics for the evaluation of our results. The use of more than one matrix helped us evaluate the performance of the models from different perspectives.



## Conclusion

We successfully implemented a machine learning and
Natural Language Processing model to detect whether 
An article was fake or real.
We got 7592 articles correctly identified as Fake and 7131
Correctly identified as real. When doing such a classification, 
it is important to check that we limit the number of false positives 
as they can cause real to be marked as fake.
I would like to choose PassiveAggressiveClassifier method, because this 
method has less false positive and false negative.
So overall PassiveAggressiveClassifier Method performed much better in 
determining in fake news cases which is around 99%.


## Future Work:



• Our research focuses on daily news articles which have on average around
 1000 words. It is difficult to detect linguistic cues in single (or few) statement
news. Some other method can be researched upon for these cases.


• For designing a fake news detector for social media like Facebook or twitter,
we can take into account the user information, user authenticity and origin of
the news.


## Link to Jupyter Notebook in Repository

https://github.com/Nastaranra/Springboard_Project/blob/master/Unit%2027/Capstone%20Three-Fake_news_detection%20-%20Step%206%20Documentation.ipynb
https://drive.google.com/file/d/1iMuQc_HQIDCRRkkX4CJU8o4id7JfGJy3/view?usp=sharing
