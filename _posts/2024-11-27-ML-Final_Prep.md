---
layout: post
title: Machine Learning Final Preparation
date: 2024-11-27 18:00:00
description: Answering the questions to prepare the final
tags: WIL
categories: AI/ML
toc:
  sidebar: left
---

## What is the condition number of a matrix and why is it important in Machine Learning?

- The state of regulation of a matrix can be shown from its conditional number. In this case, a measure of how sensitive the solution to a linear equation is to the data changes or changes to the matrix itself.

Condition numbers are, thus, important to understand in machine learning because they make our models unstable and, even worse, very sensitive and bad, in cases of using a regression training algorithm for our linear models.

This means that a small perturbation or error may cause significant changes in the output for the same inputs. This is especially alarming in machine learning, which develops models using noisy or incomplete data. Model predictions can be negatively impacted by high sensitivity and may yield unreliable results.

The condition number is not only significant for solution precision, but it is also paramount for the generalization of machine learning algorithms. Dress a matrix in a condition number that means that it is well conditioned, and you can have a much smoother landscape with a better optimization convergence during training and have models that generalize effectively to unseen data. On the other hand, under-conditioned models are likely to overfit the training data, which is a characteristic of lower generalization ability.

### Citation

- Guggenheimer, H., Edelman, A., \& Johnson, C. R. (1995). A Simple Estimate of the Condition Number of a Linear System. College Mathematics Journal. https://www.tandfonline.com/doi/epdf/10.1080/07468342.1995.11973657?needAccess=true

## What are LASSO and Ridge regularization? When do you need to use regularization? Would you use LASSO or Ridge in a high-dimensional problem? Which is generally more accurate? Why?

LASSO: A regression analysis method that enhances the prediction accuracy and interpretability of the resulting statistical model by performing both variable selection and regularization. Lasso penalizes based on the absolute value of the coefficients. It not only shrinks the coefficient but also some can be set to exactly zero, making it a variable selection technique.

Ridge regularization: Adds a penalty equivalent to the square of the magnitude of coefficients. In this case, use an L2 norm of the coefficients, which shrinks all coefficients towards zero, but does not eliminate them. Additionally, Rdge performs better when the multicollinearity among the predictors is present.

Using regularization is useful for high-dimensional datasets since it curbs excessive fitting of those datasets.

I would use Lasso. It is also common practice to use Lasso in some cases due to its variable selection ability. It can shrink the model incrementally and eventually force some coefficients to be exactly zero. This could make the model simpler and more interpretable, possibly enhancing its performance in the presence of new data. However, Ridge, most of the time, incorporates all predictors, which might not be suitable in a situation when one is trying to build a prediction from the most crucial features.

In essence, Ridge estimates tend to be better when there is high multicollinearity while all the features of the data are of interest because it yields more stable estimates in this case. To handle this concern, Ridge reduces the size of the coefficients and retains all the features thereby increasing the robustness of the analysis and the results.

### Citation

-Ranstam, J., Cook, J.A. (2018). LASSO regression. British Journal of Surgery, 105.

## Under what conditions are k-fold cross validation and bootstrapping a poor choice for model selection? What are some alternatives in these cases?

- ### k-fold cross-validation:

1. High-dimensional settings where predictors are independent of class labels but the model is allowed to select predictors, cross-validation may give misleadingly optimistic results if feature selection is not properly handled within the cross-validation process.

   - Alternatives: Lasso / Ridge Regularization, PCA

2. When there is considerable variability in the error estimates. Error estimates obtained from CV can show significant variability depending on how the data is split. Relying solely on the mean performance may lead to overestimating the model's reliability.

   - Alternatives: Repeated cross-validation, Bootstrap

3. If the model is not completely retrained for each fold, including any feature selection or preprocessing steps. This is a common blunder even in top-ranked journal papers.

   - Alternatives: Nested cross-validation

4. When working with large numbers of predictors, such as in genomics, improper cross-validation implementation can have dramatic consequences in terms of incorrect error estimation.
   - Alternatives: Regularization, Feature Filtering, Nested CV, PCA

- ### Bootstrapping

1. Unsupervised learning, such as clustering, because cluster centers will tend to fill feature space densely and be close to all data points regardless of K.

   - Alternatives: cross-validation, AIC/BIC, Silhouette score, or elbow

2. Leave-One-Out (K = N) Bootstrap. When K = N, where every data point is included except one. It is low bias and high variance. The training sets are almost identical across iterations, leading to a highly variable estimate despite low bias. Also, it has a high computational cost. Running N iterations can become computationally expensive.

   - Alternatives: k-fold cross-validation

3. The bootstrap error estimate does not provide a good estimate in general.

   - Alternatives: cross-validation, AIC/BIC, Ensemble evaluaion

4. Problems with standard errors that may be invalid due to the influence of the model selection process and optimization criteria after model selection that may differ from the desired criteria on the training set.

   - Alternatives: Cross-validation, AIC/BIC

5. Problems with traditional methods, such as F-statistics, that adding or removing terms based on significance fails to account for multiple testing issues adequately.
   - Alternatives: AIC/BIC, cross-validation, Regularization (Lasso and Ridge)

## Citation

- Trevor Hastie, Robert Tibshirani, and Jerome Friedman, 2009, The Elements of Statistical Learning: Data Mining, Inference, and Prediction (Second Edition), Ch 7 : Model Assessment and Selection

## Give a brief descrption of dropout. Why is it used so widely in Deep Learning?

- To address overfitting, Dropout randomly sets a subset of neurons to zero at the start of each training cycle. This procedure increases robustness by preventing complex co-adaptations and forcing the network to learn redundant representations.
  Dropout, by its nature, makes the network less sensitive to individual neurons. As a result, this model can generalize and perform better on new, untested data. A more generalized representation that can manage different inputs is achieved using dropout, allowing each model update to be viewed as a mini-semble of multiple neural network topologies. It is also shown to improve performance on a wide range of tasks and datasets. Finally, it helps the model perform better and train faster. During training, it allows models to learn more efficiently and reach their best performance quicker by temporarily turning off some neurons during training.

### Citation

- Byrd, J., \& Lipton, Z. C. (2018). What is the Effect of Importance Weighting in Deep Learning? International Conference on Machine Learning. https://www.semanticscholar.org/paper/b661520bf0061b7d96ccf12016e351dd3a6ee780

## Why are convolutional layers used widely in image classification and segmentation?

- There are several reasons. First, it is utilized for an explicit feature extraction, which is localized in a region of interest. Such features are derived from local areas of the image, which enables the identification of edges, textures, and other low-level patterns. Second, these local features help in enhancing the correlation as well as the intensity of pixels from areas that are closer as opposed to those that are farther away. It is important to mention that during the image classification process, cure areas are concentrated, which makes local features even more significant.

Second, it is utilized for the purpose of architecture that is economical. For instance, architecture that has been designed with weight sharing in mind for a structure such as a neural network can apply the same filters or kernels all over the entire image, thus minimizing the number of parameters, as well as the number of computations required to be performed. Such relevant units in the feature maps process little portions at a time while interrelating and distinguishing a pattern.

Third, it is utilized for the hierarchical feature processing. Convolutional networks build hierarchical representations, starting with simple features and progressing to more complex patterns. In the same way, the local features detect some parts, which in the next stage get combined for general feature detection. Moreover, deep representations are less affected than shallow representations by transformations like translations, scaling, and small rotation of the images.

Fourth, it is used in the context of invariance. Convolutional layers give consistent regions as patterns that can be recognized. Such patterns can also be enhanced through data augmentation or more sophisticated architectures to be invariant to scaling or rotations.

Fifth, it is used for efficient learning of features and structures of patterns as well as deeper networks. Convolutional networks make use of local receptive fields, weight sharing, and subsampling to hit efficiently, and with so many processes, the image across features. Earlier networks with no invariances had average higher misclassification rates of around 4.5\%, but these architecture limitations have largely been alleviated by complementary ones other architectures have strengthened.

Lastly, emphasizes other methods as wavelet transforms. In some of the tasks, wavelet transforms are used in conjunction with CNNs in order to increase edge detection and capture discrete jumps in images, although CNNs are now robust enough to perform such tasks independently.

## Citation

- Bishop, C. M. (2006). Chapter 5: Neural networks. In Pattern recognition and machine learning. Springer.
- Trevor Hastie, Robert Tibshirani, and Jerome Friedman (2009), Ch 11: Neural Networks, The Elements of Statistical Learning: Data Mining, Inference, and Prediction (Second Edition)

## If Model A gives a RMSE of 0.32 and Model B gives a RMSE of 0.34 (same training and out-of-sample validation sets), what are some factors you would consider in determining which is the better model? Why are these factors relevant?

- There are several factors to consider in determining which model is the better. First, model Complexity and interpretability. If the model is too complicated, then the risk of overfitting increases. The complex model has good performance in the train data, but it might not perform well in the new data. Also, too complex a model is hard to interpret, and there are possible debugging difficulties. The simple model makes it easy to understand the result or the processing of the prediction.

Second, robustness to overfitting. If the model is overfitting to the training data, it does not generalize well to the new data. In particular, if the training data is low or noisy, the model is likely to overfit. Especially with less training data or too much noise, there is the possibility to be overfitting.

Lastly, training time and resource efficiency. A more complicated model takes more time to train, and the time required to train models can increase exponentially, especially when trained on a large dataset. Also, a complex model such as a deep learning model can require significant computational resources.

### Citation

- Bishop, C. M. (2006). Chapter 3: Linear Models for Regression. In Pattern recognition and machine learning. Springer.
- Trevor Hastie, Robert Tibshirani, and Jerome Friedman (2009), Ch 7: Model Assessment and Selection, The Elements of Statistical Learning: Data Mining, Inference, and Prediction (Second Edition)
- Goodfellow, I., Bengio, Y., \& Courville, A. (2016). Chapter 5: Machine learning basics. In Deep learning. MIT Press. Retrieved from http://www.deeplearningbook.org

## You are given some binary classification training data with two features $X_1$, $X_2$. Both $X_1$ and $X_2$ are {0, 1}-valued. You can easily calculate $P(X1|Y= y)$ and $P(X2|Y= y)$ and $P(Y= y)$ for $y= 0, 1$, but what else do you need to check in order to satisfy the conditions for using a Naive Bayes classifier?

- We need to check the conditional independence of features given the class, $P(X_1, X_2 | Y = y) = P(X_1 | Y = y) \cdot P(X_2 | Y = y)$ and sufficient data, enough data to accurately estimate the conditional probabilities.

### Citation

- Bishop, C. M. (2006). Chapter 4: Linear Models for Classification. In Pattern recognition and machine learning. Springer.

## Are association rules as found by the a priori algorithm transitive? (e.g. if $A \Rightarrow B$ and $B \Rightarrow C$, does $A \Rightarrow C$?)

- No. It does not guarantee that $ A \Rightarrow C$ will also be valid if $A \Rightarrow B$ and $B \Rightarrow C$ are valid association rules. Because the strength of the association rule is determined by its support and confidence, but because $A \Rightarrow B$ and $B \Rightarrow C$ hold with high support and confidence does not imply that $ A \Rightarrow C$ will also hold with high support and confidence. The Apriori algorithm generates rules based on empirical patterns found in the data. The relationship between A and C is not guaranteed by the relationship found in $A \Rightarrow B$ or $B \Rightarrow C$. The association rules, however, rely on data rather than logical reasoning which may lead to no establishment of transferability.

### Citation

- Tan, P.-N., Steinbach, M., & Kumar, V. (2021). Chapter 5: Association analysis: Basic concepts and algorithms. In Introduction to data mining (2nd ed.). Pearson.
- Trevor Hastie, Robert Tibshirani, and Jerome Friedman (2009), Ch 14: Unsupervised Learning, The Elements of Statistical Learning: Data Mining, Inference, and Prediction (Second Edition)

## Is the following statement true or false? "Performing PCA before utilizing another classification or regression model can reduce the number of input features and improve performance and therefore is a good idea." If true, provide some supporting details. If false, give a counterexample.

- False. PCA captures linear correlations, so it may fail to preserve important nonlinear relationships in the data. Applying PCA can remove informative features, reducing the performance of the classifier or regressor. Also, PCA does not consider the label. PCA is the unsupervised method that does not make use of any labels in the computation. Therefore, if the classification or regression model is the supervised model, such as logistic regression and decision trees, then performing PCA before utilizing another model may not improve performance.

### Citation

- Trevor Hastie, Robert Tibshirani, and Jerome Friedman (2009), Ch 3: Linear Methods for Regression, The Elements of Statistical Learning: Data Mining, Inference, and Prediction (Second Edition)

## Is the following statement true or false? "Performing k-means and then adding labels of the resulting clusters to your set of features can enhance your feature set and improve your classification/regression model and is therefore a good idea." If true, provide some supporting details. If false, give a counterexample.

- False. The label generated by k-means clustering and the actual label may not match. Then the clustered label may act as noise because it is not useful information. In addition, the feature space may be unnecessarily expanded. Small data and large number of clusters can lead to overfitting.

### Citation

- Trevor Hastie, Robert Tibshirani, and Jerome Friedman (2009), Ch 14: Unsupervised Learning, The Elements of Statistical Learning: Data Mining, Inference, and Prediction (Second Edition)
