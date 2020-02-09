---

layout:     post
title:      A/B Testing Summary
subtitle:   A/B Testing
date:       2020-02-06
author:     Xiangke
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Data Analysis
    - A/B Testing
---



# A/B Testing Summary



```
Lasest Update time: 2020/02/06
```



# Assumption of A/B Testing

- Samples are independent 

# General Questions

General Questions You Should Be Aware Of:

- What is A/B Testing?

  the idea is to challenge an existing version (A) with a new one (B), by randomly splitting traffic and comparing metrics on each of the splits.

- When is A/B Testing a good idea? When is it a bad idea?

  A/B Testing cannot test haven't existed yet. It also has issue with testing new products. It cannot to measure long-term effect. If a feature takes a long time to be effective, AB Testing might not be a good solution. It has novelty effect.

- What is a Null Hypothesis/Statistical Significance?

- How to avoid novelty effect?

  AB Testing. 都找new users. 都找new users. But the downside of this is that you need to operate enough time to collect enough data to generate significant result

  Also you can try to run the experiment a little longer so that users can be more family with your products. 

- What are the main steps in A/B Testing?

- What metrics do you want to improve?

- Can you think of some variations can be made?

- What change do you want to test? Why?

- How many visiits/sample size do I need?

- Can you calculate the practical significance (given costs)?

- Will you launch the variation? (Given the test result)

- How big is the sample size

- How long to run the experiment?

- How much traffic% for testing?

- How to divide the % of the traffic for testing?

- What's the target audience of the testing?



- How to your result more confidence?

  You can increase in confidence by A increase the confidence level which means you can change your significant level and increase the power.

  You can increase the power. A) increase the sample size , so you can either open your experiment to attach more traffic or longer time





# Concepts

**P-Value**

The p-value is the probability of obtaining at least as extreme results given that the null hypothesis is true. In other words, the p-value is the expected fluctuation in a given sample, similar to the variance.

In AB testing, the p-value is the difference we would see across samples if we ran an A/B test.



**Significance Level**

The significance level is the probability of rejecting the null hypothesis is given that it is true. It's a value we set based on the level of accuracy we deem acceptable.

In AB testing, the significance level is the industry standard 5% we use to give us results with 95% confidence.



**Statistical Hypothesis Testing**

An AB test is an example of statistical hypothesis testing, a process whereby a hypothesis is made about the relationship between two data sets and those data sets are then compared against each other to determine if there is a statistically significant relationship or not.

To put this in more practical terms, a prediction is made that Page Variation #B will perform better than Page Variation #A, and then data sets from both pages are observed and compared to determine if Page Variation #B is a statistically significant improvement over Page Variation #A.



**Data Sample**

A data sample is a set of data collected and/or selected from a statistical population by a defined procedure. It's a small portion of the larger population.

In AB testing, the sample is the number of visitors we display our new page variation too in order to collect data.



**Mean**

The mean is the central tendency of a probability distribution.

In AB testing, the mean is our page's conversion rate with the sample visitors.



**Variance**

The variance is a measure of variability across samples. It is officially the expectation of the squared deviation of a random variable from its mean.

In AB testing, the variance affects the sample size we need in order to have a chance of deriving statistically significant results.



**Regression to the Mean**

Regression to the mean is the phenomenon that if a variable is extreme on its first measurement, it will tend to be closer to the average on its second measurement.

In AB testing, this phenomenon ensures that as we continue increasing the sample size and the length of observation, the mean of our cumulative observations will get closer and closer to the true mean of the population.



**Statistical Population**

In statistics, a population is a set of similar items or events which is of interest for some question or experiment. It's the group we want information about.

When AB testing a webpage, the true population is every future individual who will visit that page



**Confidence Level & Interval**

The confidence interval is an observed range in which a given percentage of test outcomes fall. The confidence interval is determined by the confidence level we manually select at the beginning of our test and influences the sample size required.

In AB testing, the confidence level is usually set to 95%, which gives us a range (the confidence interval) in which we know the mean will fall in at least 19 of 20 samples.

**Margin of Error**

The margin of error is a statistic expressing the amount of random sampling error in a sample's results. The margin for error is a function of the standard deviation, which is a function of the variance. Really all you need to know is that all of these terms are measures of variability across samples.

The margin of error is added to and subtracted form the mean to determine the confidence interval.



**Null Hypothesis**

The null hypothesis is a baseline assumption that there is no relationship between two data sets. When a statistical hypothesis test is run, the results either disprove the null hypothesis or they fail to disprove the null hypothesis.

In AB testing, the null hypothesis is the assumption that the original page and the new page variation have no statistical significant relationship.



**Statistical Significance**

Statistical significance is attained when the p-value is less than the significance level. And that is way too many new words in one sentence, so let's break down these terms real quick and then we'll summarize the entire concept in plain English.

In AB testing, statistical significance is how we verify that a new page truly outperforms the original.



**Statistical Power**

Statistical power is the probability that a test correctly rejects the null hypothesis.



**Type I Error**

A type I error occurs when we incorrectly reject the null hypothesis.

In AB testing, a type I error would occur if we concluded that Variation B was "better" than Variation A when it actually was not. These errors are avoided by achieving statistically significant results.



**Type II Error**


A type II error occurs when the null hypothesis is false, but we incorrectly fail to reject it.

To put this in AB testing terms, a type II error would occur if we concluded that Variation B was not "better" than Variation A when it actually was better. These errors are avoided by running tests with a high statistical power.



**Overall Evaluation Metric (OEC)**

One overall metrics



**Heterogeneity (HTE)**

Segment X



**Long Term Effect**

[Long-term experiment](https://en.wikipedia.org/wiki/Long-term_experiment)

A **long-term experiment** is an [experimental](https://en.wikipedia.org/wiki/Experiment) procedure that runs through a long period of time, in order to test a [hypothesis](https://en.wikipedia.org/wiki/Hypothesis) or observe a phenomenon that takes place at an extremely slow rate.

For example,

 You want to test if two referral coupons are effective for customers on a hotel-rental website. Since people don't visit Hotel very often, it may takes some time to be effective

**Network Effect**

网络外部性

A **[network effect](https://en.wikipedia.org/wiki/Network_effect)** (also called **network externality** or **demand-side economies of scale**) is the effect described in [economics](https://en.wikipedia.org/wiki/Economics) and [business](https://en.wikipedia.org/wiki/Business) that an additional user of [goods](https://en.wikipedia.org/wiki/Goods) or [services](https://en.wikipedia.org/wiki/Service_(economics)) has on the [value](https://en.wikipedia.org/wiki/Value_(economics)) of that product to others. When a network effect is present, the value of a product or service increases according to the number of others using it.

The classic example is the telephone, where a greater number of users increases the value to each. A positive externality is created when a telephone is purchased without its owner intending to create value for other users, but does so regardless. Online social networks work similarly, with sites like Twitter and Facebook increasing in value to each member as more users join.



# Metrics

General



**Count**

- Page View
- Visit / Session
- Click
- Visitor / Unique Visitors
- Active Users (DAU, MAU)

**Conversion**

- Click Thru Rate (CTR)
- Click Thru Probability
- User Click Probability
- Bounce Rate (people leave rate)

**Time**

- Active Time
- Page View Duration

**Business**

- Revenue 
- Member
- Order

**Ads Analytics**

- Impression
- Click

**Composite Metric**

- retention
- Acquisitive  
- Percentage user using xxx Out of active user
- sketch competitors
- Adobe competitors
- Brewer base. 你可以很简单用产品 windows也可以。很多时候Mac才能做design 但是很多用户mac普及没有那么广. Make design accessible for all. Collaboration!!!
- 上周四 user conference! 





# Experiments

**Quesions**

- How big is the sample size

- How long to run the experiment?

  不能太长 别让大家知道你已经有了新的version 不让大家知道你在ab

- How much traffic% for testing?

- How to divide the % of the traffic for testing?

- What's the target audience of the testing?



1. Pick one variable to test

2. Identify your goal

   1. Primary goal
   2. Secondary goal

3. Create a 'control' and a 'testing' group

4. Split samples groups equally

5. Determine sample size

   If this experiment has finite audience, then we might need to do the test longer to make sure there is enough interactions to gain a statistical result.

6. Decide how significant you results need to be 

7. Make sure you're only running one test at a time on any campaign



# Common Mistakes

Resources from [link](https://www.widerfunnel.com/3-mistakes-invalidate-ab-test-results/)



**<u>Try not to test multiple variations</u>** 



**Mistake #1: Your test has too many variations**

1. **Longer time**
2. **Larger traffic**

The more variations, the more insights you’ll get, right?

Not exactly. Having too many variations slows down your tests but, more importantly, it can impact the integrity of your data in 2 ways.

**First**, the more variations you test against each other, the more traffic you will need, and the longer you’ll have to run your test to get results that you can trust. This is simple math.

But the issue with running a longer test is that you are more likely to be exposed to cookie deletion. If you run an A/B test for more than 3–4 weeks, the risk of sample pollution increases: in that time, people will have deleted their cookies and may enter a different variation than the one they were originally in.

**Second risk** when testing multiple variations is that the significance level goes down as the number of variations increases.

In other words, the more variations, the higher the chance of a false positive i.e. the higher your chances of finding a winner that is not significant.

**Mistake #2: You change experiment settings in the middle of a test**

When you launch an experiment, you need to commit to it fully. Do not change the experiment settings, the test goals, the design of the variation or of the Control mid-experiment. And don’t change traffic allocations to variations.

Changing the traffic split between variations during an experiment will impact the integrity of your results because of a problem known as [Simpson’s Paradox](https://en.wikipedia.org/wiki/Simpson's_paradox).This statistical paradox appears when we see a trend in different groups of data which disappears when those groups are combined.





# Appendix

Some concepts are from forum 1point3acre. I adjusted them and appended my own content. 





# Resources

[5 Validity Threats That Will Make Your A/B Tests Useless](https://splitbase.com/ab-testing-threats/)

