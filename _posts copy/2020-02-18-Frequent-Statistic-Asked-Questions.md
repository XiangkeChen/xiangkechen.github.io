---
layout:     post
title:      Frequent Statistics Asked Questions
subtitle:   Data Analysis, Tips, Statistics, FAQ
date:       2020-02-18
author:     Xiangke
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - Data Analysis
    - Statistics
    - FAQ
---



```
Update time: 
- 02/03/2020 orginal post
- 02/18/2020 update linear regression knowledge
```



# Conceptual Questions

**Prediction VS Forecasting**

Forecasting would be a subset of prediction. Any time you predict into the future it is a forecast. 

All forecasts are predictions, but not all predictions are forecasts, as when you would use regression to explain the relationship between two variables.

**Correlation vs Casuation**

Correlation does not imply causation. Causation explicitly applies to cases where action A causes outcome B.

![png](https://images.ctfassets.net/vrkkgjbn4fsk/6zStaOhyU0II1ktEbqsFUN/1504e23f790afdda052f3516b8bc1089/correlation-vs-causation.png?q=90&w=1168)



Further read: [causation-correlation](https://amplitude.com/blog/2017/01/19/causation-correlation)





# Linear Regression

**What's the assumption of linear regression**

[Link](http://r-statistics.co/Assumptions-of-Linear-Regression.html)

- Regression model is linear in parameters

- The mean of residuals is zero

-  No auto-correlation ( previous data points)
- No perfect multicollinearity

- Normality of residuals

  QQ-plot



**What is Covariance**

Covariance is a measure of the relationship between two random variables. The metric evaluates the variance between two variables. 

- Positive covariance
- Negative covariance



![3APRpQ.png](https://s2.ax1x.com/2020/02/18/3APRpQ.png)



**Covariance vs Correlation**

> [Link](https://corporatefinanceinstitute.com/resources/knowledge/finance/covariance/)

**Covariance** measures the total variation of two random variables from their expected values. Using covariance, we can only gauge the direction of the relationship (whether the variables tend to move in tandem or show an inverse relationship). However, it does not indicate the strength of the relationship, nor the dependency between the variables.

On the other hand, **correlation** measures the strength of the relationship between variables. Correlation is the scaled measure of covariance. It is dimensionless. In other words, the correlation coefficient is always a pure value and not measured in any units.

The relationship between the two concepts can be expressed using the formula below:



![cor](https://cdn.corporatefinanceinstitute.com/assets/covariance3.png)



# To Be Continued ...

I'll keep updating this post along the time



