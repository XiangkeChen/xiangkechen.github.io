---
layout:     post
title:      Frequent Asked Machine Learning Questions - General
subtitle:   Machine Learning, Tips, FAQ
date:       2020-02-14
author:     Xiangke
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - Machine Learning
    - FAQ
---



```
update history:
1. Feb 14th orginal post
```





# Data Quality Issue



## Missing Values

Reference Link: [Link](https://towardsdatascience.com/how-to-handle-missing-data-8646b18db0d4)



There are several types of Missing Values:

1. **Missing at Random (MAR):** Missing at random means that the propensity for a data point to be missing is not related to the missing data, but it is related to some of the observed data
2. **Missing Completely at Random (MCAR):** The fact that a certain value is missing has nothing to do with its hypothetical value and with the values of other variables.
3. **Missing not at Random (MNAR):** Two possible reasons are that the missing value depends on the hypothetical value (e.g. People with high salaries generally do not want to reveal their incomes in surveys) or missing value is dependent on some other variable’s value (e.g. Let’s assume that females generally don’t want to reveal their ages! Here the missing value in age variable is impacted by gender variable)

So , if MCAR, we can impute or just drop them. The common practice is that we drop when we have a lot of data. We impute when we have limited data. Be mindful that imputation might result in bias.

Is missing values has pattern, they might contain true information so that we shouldn't drop them otherwise we produce bias. We can replace with **NA**. We can predict.... But still be mindful of introducing bias.



**Exercise**

**You found out that data set contains 25-30% missing values. How will you deal with it?**

- If you have a lot of data (greater than 100 M rows.)
- If you do not have lots of data (less than 10K rows)

Sample dataset can be found here: [link](https://bit.ly/2BW9S7j)

(Answer can refer the previous paragraphs.)





# Overfitting

**1.What is the signal of your model is over-fitting and why almost all predictive models are prone to over-fitting?**

Model doesn’t generalize well from our training data to unseen data. 

Signal: 

accuracy/any kind of error plot plot of training and testing data, those two line diverges as model become more and more complex

Why:

The tendency of DM procedure to tailor models to the training data, at the expense of generalization to previously unseen data points



**2.How to avoid Over-Fitting?**

**General Approaches**

[Reference Link](https://elitedatascience.com/overfitting-in-machine-learning#how-to-prevent)

1. **<u>Cross-Validation</u>**

   Use your initial training data to generate multiple mini train-test splits. Use these splits to tune your model.

2. **<u>Train with more Data</u>**

   Detect more signal

3. **<u>Remove some useless features</u>**

4. **<u>Early Stopping</u>**

   Up until a certain number of iterations, new iterations improve the model. After that point, however, the model’s ability to generalize can weaken as it begins to overfit the training data.

5. <u>**Regularization**</u>

   Regularization refers to a broad range of techniques for artificially forcing your model to be simpler.

   The method will depend on the type of learner you’re using. For example, you could prune a decision tree, use dropout on a neural network, or add a penalty parameter to the cost function in regression.

   Oftentimes, the regularization method is a hyperparameter as well, which means it can be tuned through cross-validation.

6. **<u>Ensembling</u>**

   1. Bagging 
   2. Boosting



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

