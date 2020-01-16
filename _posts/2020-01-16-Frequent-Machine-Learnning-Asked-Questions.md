---
layout:     post
title:      Frequent Asked Machine Learning Questions
subtitle:   Machine Learning, Tips
date:       2020-01-16
author:     Xiangke
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Machine Learning
---





# Classification and Regression

**1.connection and differenced between classification and regression**

connection:

* classification produce continuous output, eg. probability estimate of belonging to certain class, classify by applying certain threshold/cutoff (such as NB, Tree, NN)
  + Different cutoff value apply for the purpose of maximize accuracy or minimize FP/FN(ROC curve, but what is FN) or minimize costs(profit cost matrix)
* regression can predict discrete value, in the form of integer quantity

difference:

* classification use accuracy to evaluate
* zregression use sum of square error, error based.

**2.The difference of binary classification and multi-class classification.**

**multiclass** or **multinomial classification** is the problem of [classifying](https://en.wikipedia.org/wiki/Statistical_classification) instances into one of three or more classes. (Classifying instances into one of two classes is called [binary classification](https://en.wikipedia.org/wiki/Binary_classification).)

# Overfitting

**1.What is the signal of your model is over-fitting and why almost all predictive models are prone to over-fitting?**

Model doesn’t generalize well from our training data to unseen data. 

Signal: 

accuracy/any kind of error plot plot of training and testing data, those two line diverges as model become more and more complex

Why:

The tendency of DM procedure to tailor models to the training data, at the expense of generalization to previously unseen data points



**2.How to avoid over-fitting in decision tree, KNN and logistic?**

-cross validation. train model on subtraining sets, then estimate the geralization performance for each from the validation sets, and then pick the best performed one and the hyper parameters. Then train the model on whole training set using tunned hyper parameters.

-sequential forward selection for features.

DT:

- stop growing tree before it gets too complex (hyperparameter tunning)
- purnning. (can prune tree branches that represent anomalies which might just be noise)

KNN:

- chose K based on validation

Logistics:

- Use regularization term, C = 1/lambda

**3.Why Naive Bayesian is less likely to suffered from over-fitting?**

Briefly, with the Naive Bayes (NB) algorithm the 'naive' conditional independence assumption means that interactions between variables can be ignored. What follows is:

- it has a simpler hypothesis function (compared with other algorithms e.g. logistic regression)

- since the interactions are not modeled, some of the information in the data is ignored. This makes it an inherently high bias model; it has a high approximation error but as a result it also does not overfit. (A model with high variance attempts to model all of the data including the noise in the data).

- Since the interactions are not modeled, less training data is needed. This is why the NB classifier is known to perform well both with small data sets and with missing data.

**not sure about this..**



# Logistics

**1.We can use linear regression as classifier, why need logistic?** 

linear regression assign values to response variable, whereas logistics assign possibility, which is more interpretable. 

The target variable in our training data is binary, however, regression requires continuous target variable

Moreover, a classifier predict the probability over categorical class, we need the output to be between[0,1]. But linear regression did not confine in this interval Let's why we bring in sigmoid function in logit.

p = 1/(1 + exp^(-f(x))), f(x) = ax+bx+cx+....

**not sure about this question**

**2.The difference of ordered logit and multi-class classification.**

ordinal logistics classify ordinal multi-calss where as in multi-class classification problem the different classes did not rank in order. 

Also ordinal logistics is very like regular logistics except for different threshold to assign ordered class.

**not sure about this question**

**3.interpret coefficient**

exp(betap) is the effect of unit increase in the independent variable xp on the odds ratio/

比如x长1单位，positive 比 negative的odds 翻一倍。exp(betap) = 2



# Naive Bayes

**1.Why need the Naive assumption in the Naive Bayesian classifier?**

Assumption: attributes are conditionally independent of each other, given class label 

so that we can simplify P(X|Ci) = P(x1|Ci) * P(x2|Ci)* ....P(Xk|Ci). And can be very efficient on large dataset.

If we bring in covariance/correlation between attrbutes into consideration, then the computation process would be very costly for dataset with many features.

Probability ranking might not be accurate but the ranking are still valid, thus the prediction are often accurate

**2.How to calculate P(X_k|C_i) when X_k is categorical/numerical?**

- Categorical: P(Xk|Ci) = |Di,xk| / |Di| . the ratio of the number of data points in clusters i that have the same value as the predicted data point on Ak attribute over the total number of points of cluster i

- Numeric: usually we will assume certain distribution, often Gaussian. Then just use normal distribution pdf to calculate P(Xk|Ci) = pdf(Xk)

  mu*Ci* *,*sigma*Ci* – mean and standard deviation for Ak within Ci 

  

# KNN

**1.How to select K in KNN? Why need a separate validation set?**

You can segregate the training and validation from the initial dataset. Plot the validation error curve to get the optimal value of K. This value of K should be used for all predictions. usually we draw elbow plot, and chose K where it gave the greatest amount of error reduction and also consider the accptable level of error rate

Why: Because we want to test the generalization ability of the model on new dataset. so that the model did not see the validation data before, so that it won't gave us a misleading result

**2.Why we need to do feature normalization in KNN? Should normalization be done before or after the split of training and testing data?**

Because KNN is a model based on distance, which is really susceptible to scale difference. It inherently assign greater importantce to bigger value. 

normalization should be done after the train test split. run normalization on testing dataset, and apply the trained nomalized transfomation on testing dataset. in this way the model won't see the testing data during training

**3.The difference of decision boundary between KNN and logistic regression.**

- KNN boundary is irregular and non-linear. 

- logistics is a line or a hyperplane.



# Cross Validation

**1.Why we need to do cross validation? The advantage of cross validation comparing with training/testing split.**

To test if model performance would be consistent. Different modeling procedures may have different performance on the same data. Different training sets may result in different generalization performance. Different test sets may result in different estimates of the generation performance

Cross Validation is used to assess the predictive performance of the models and and to judge how they perform outside the sample to a new data set also known as test data. Not only simple estimate of generalization performance, but also some statistics(mean variance) on the estimated performance

The motivation to use cross validation techniques is that when we fit a model, we are fitting it to a training dataset. Without cross validation we only have information on how does our model perform to our in-sample data. Ideally we would like to see how does the model perform when we have a new data in terms of accuracy of its predictions. In science, theories are judged by its predictive performance.  

Advantages of train/test split:

1. This runs K times faster than Leave One Out cross-validation because K-fold cross-validation repeats the train/test split K-times.
2. Simpler to examine the detailed results of the testing process.

Advantages of cross-validation:

1. More accurate estimate of out-of-sample accuracy. It gives you multiple estimates of out-of-sample error, rather than a single estimate.
2. More “efficient” use of data as every observation is used for both training and testing. Use all data, avoid wasting much training data in validation set

**2.How to implement cross validation by yourself based on the stratified sampling?**

CV process:

The general procedure is as follows:

1. Shuffle the dataset randomly.
2. Split the dataset into k groups
3. For each unique group:
   1. Take the group as a hold out or test data set
   2. Take the remaining groups as a training data set
   3. Fit a model on the training set and evaluate it on the test set
   4. Retain the evaluation score and discard the model
4. Summarize the skill of the model using the sample of model evaluation scores

Stratified CV:

The splitting of data into folds(step 2) may be governed by criteria such as ensuring that each fold has the same proportion of observations with a given categorical value, such as the class outcome value. This is called stratified cross-validation.

**3.Stratified CV vs training testing split. Which strategy is better, based on variance of the evalation method?**

– 10-fold stratified cross validation
– 10 times 90/10 random training/test split 

10-fold stratified CV is better. Because in random train/test split, the splited dataset might not be representable of the class distribution of the whole dataset. If one class is not much represented in dataset, the random split train/test split might result in an training test set that did not have any the minortity class, which could leads to very high variance model performance. Moreover, in 10 times random training/test split, some data might not be chosen by 1 times as subtraining set, which make the model loss information.

Stratified CV on the other hand, is designed to split data so that each split are similar with respect to something, in this case we will not missing minority class in sub-training. And we will be using every part of dataset to train and test model. This could generate less variance and more concsistent model performance 

> [Stratified sampling](https://en.wikipedia.org/wiki/Stratified_sampling) aims at splitting one data set so that each split are similar with respect to something. In a classification setting, it is often chosen to ensure that the train and test sets have approximately the same percentage of samples of each target class as the complete set.
>
> As a result, if the data set has a large amount of each class, stratified sampling is pretty much the same as random sampling. But if one class isn't much represented in the data set, which may be the case in your dataset since you plan to oversample the minority class, then stratified sampling may yield a different target class distribution in the train and test sets than what random sampling may yield.
>
> Note that the stratified sampling may also be designed to equally distribute some features the next train and test set. For example, if each sample represent one individual, and one feature is age, it is sometimes useful to have the same age distribution in both the train and test set.

**not sure about this**



**4.What are the two flaws of using training/validation/testing split to set the hyper parameter and evaluate the performance? How grid search via cross validation and nested cross validation fix these two flaws?**

Training/validation/testing split flaw:

- waste too much training data on validation sets
- **what's the others? ** did not show generalized model performance?

GridSearch CV:

The model is trained on the training subset and the parameters that minimize error on the validation set are chosen. Finally, the model is trained on the full training set using the chosen parameters, and the error on the test set is recorded.





# TBD...