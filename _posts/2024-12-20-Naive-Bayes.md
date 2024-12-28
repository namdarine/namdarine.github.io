---
layout: post
title: Naive Bayes Classifier
date: 2024-12-20 18:00:00
description: Understand the concept of the Naive Bayes Classifier
tags: WIL
categories: AI/ML
toc:
  sidebar: left
---

> Naive Bayes classifier is a family of linear **Probabilistic classifier**.

-> Assumes the features are conditionally independent given the target.

This classifier is one of the types of the simplest Bayesian network models.  
Also, it is widely utilized for its simplicity and efficiency in machine learning.  
As it is the family of "linear" probabilistic classifier, it is highly scalable, requiring a number of parameters linear in the number of varibales in a learning problem.  
Naive Bayes classifier is mostly used in the language model. It is fast and making prediction is easy with high dimension of data.
The naive Bayes classifier is based on Bayes' Theorem, $$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$, where A and B are events and $$P(B) \neq 0$$.  
For more information on Bayes' Theorem, check [Wikipedia](https://en.wikipedia.org/wiki/Bayes%27_theorem).

## Assumption

- **Feature independence**: The features of the data are conditionally independent of each other.
- **Continuous features are normally distributed**: If a feature is continuous, then it is assumed to be normally distributed within each class.
- **Discrete features have multinomial distributions**: If a feature is discrete, then it is assumed to have a multinomial distribution within each class.
- **Features are equally important**: All features are assumed to contribute equally to the prediction of the class label.
- **No missing data**: The data should not contain any missing data.

## Advantages

- Easy to implement and computationally efficient.
- Effective in cases with a large number of features.
- Performs well even with limited training data.
- Performs well in the presence of categorical features.
- For numerical features data is assumed to come from normal distributions.

## Disadvantages

- Assumes that features are independent, which may not always hold in real-world data.
- Can be influenced by irrelevant attributes.
- May assign zero probability to unseen events, leading to poor generalization.

## Applications

- **Spam email filtering**
- **Text classification**: used in sentiment analysis, document categorization, and topic classification.
- **Medical diagnosis**: helps in predicting the likelihood of a disease based on symptoms.
- **Credit scoring**: Evaluates the creditworthiness of individuals for loan approval.
- **Weather prediction**

# Referrence

- CS 481, Artificial Intelligence Language Understanding, prof. Jacek Dzikowski, Spring 2024, Illinois Tech
- Comment, et al. “Naive Bayes Classifiers.” GeeksforGeeks, 10 July 2024, www.geeksforgeeks.org/naive-bayes-classifiers/.
- “Naive Bayes Classifier.” Wikipedia, Wikimedia Foundation, 28 Nov. 2024, en.wikipedia.org/wiki/Naive_Bayes_classifier.
