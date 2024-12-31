---
layout: post
title: Decision Tree
date: 2024-12-25 18:00:00
description: Understand the concept of the Decision Tree
tags: WIL
categories: AI/ML
toc:
  sidebar: left
---

A decision tree is a flowchart-like structure used to make decision or prediction. It is a decision support recursive partitioning structure that uses a tree-like model of decisions and their possible consequences, including chance event outcomes, resources costs, and utility.

The decision tree is a non-parametric supervised learning method used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features.

## Structure

**Nodes**: represent decisions or tests on attributes.

- **Root node**: represents the entire dataset and the initial decision to be made. - **Internal node**: represents decisions or tests on attributes. Each internal node has one or more branches.
- **Leaf node**: represents the final decision or prediction. No further splits occur at these nodes.

**Branche**: represents the outcome of a decision or test, leading to another node.

## Metrics

1. **Gini impurity**  
   Measure the likelihood that a randomly classified new instance will be misclassified based on the class distribution of the dataset.

   $$
    Gini = 1 - \sum_{i = 1}^{n} {p_i^{2}}
   $$

   where $$ p_i $$ is the probability of an instance being classified into a particular class.

2. **Entropy**  
   Measures the amount of uncertainty or impurity in the dataset.

   $$
   entropy = -\sum_{i = 1}^{n} {p_i \log_2{p_i}}
   $$

   where $$ p_i $$ is the probability of an instance being classified into a particular class.

3. **Information gain**  
   Measures the reduction in entropy or Gini impurity after a dataset is split on an attribute.

## Advantages

1. **Simplicity and Interpretability**

   - Easy to understand and interpret
   - Visual representation mirrors human decision-making processes
   - White-box model: Conditions and results can be explained using boolean logic

2. **Minimal Data Preparation**

   - No need for normalization or scaling
   - No need for dummy variables
   - Can handle missing values (depending on the algorithm)

3. **Versatile**

   - Suitable for both <U>classification and regression</U> tasks
   - Can handle numerical and catagorical data
   - supports multi-output problems

4. **Efficiency**

   - Prediction cost is logarithmic in the number of training data points

5. **Robustness**

   - Performs well even if assumptions are somewhat violated

6. **Validation-Friendly**

   - Models can be validated using statistical tests, ensuring reliability

7. **Non-linear Relationships**
   - Capable of capturing complex, non-linear relationships between features and target variables

## Disadvantages

1. **Overfitting**

   - Trees can become overly complex and fail to generalize well
   - Mitigation: <U>Pruning,</U> setting minimum samples per leaf node, or maximum tree depth

2. **Instability**

   - Small changes in data can lead to completely different tree structures
   - Mitigation: Use ensembel methods, such as Random Forest, Gradient Boosting

3. **Limited Extrapolation**

   - Predictions are piecewise constant and not smooth
   - Poor performance in extrapolating beyond the training data range

4. **Suboptimal Solutions**

   - Finding the optimal decision tree is NP-complete
   - Algorithms rely on <U>heuristic methods</U>, such as greedy algorithms
   - Mitigation: Train multiple trees using ensemble methods

5. **difficulty with Certain Patterns**

   - Struggles with learning patterns like XOR, parity, or multiplexer problems

6. **Bias Toward Dominant Classes**

   - Decision trees may become biased if certain classes dominate the dataset
   - Mitigation: Ensure a balanced dataset before training

7. **Feature Bias**
   - Features with more levels/categories may dominate the tree structure

## Reference

- “1.10. Decision Trees.” Scikit, scikit-learn.org/1.5/modules/tree.html. Accessed 30 Dec. 2024.
- “Decision Tree.” Wikipedia, Wikimedia Foundation, 20 Oct. 2024, en.wikipedia.org/wiki/Decision_tree.
- “Decision Tree.” GeeksforGeeks, 17 May 2024, www.geeksforgeeks.org/decision-tree/.
