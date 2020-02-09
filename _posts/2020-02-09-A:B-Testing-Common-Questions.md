---

layout:     post
title:      A/B Testing Summary
subtitle:   A/B Testing
date:       2020-02-06
author:     Xiangke
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - Data Analysis
    - A/B Testing
---



# A/B Testing Common Questions



```
Lasest Update time: 2020/02/09
```





General Questions You Should Be Aware Of:



# Conceptual Questions

- **What is A/B Testing?**

  the idea is to challenge an existing version (A) with a new one (B), by randomly splitting traffic and comparing metrics on each of the splits.

- **When is A/B Testing a good idea? When is it a bad idea?**

  A/B Testing cannot test haven't existed yet. It also has issue with testing new products. It cannot to measure long-term effect. If a feature takes a long time to be effective, AB Testing might not be a good solution. It has novelty effect.

- **What is a Null Hypothesis/Statistical Significance?**



# Experiment Questions

- **What are the main steps in A/B Testing?**
  - Pick one variable to test
  - Identify your goal
  - Primary goal
    - Secondary goal
  - Create a 'control' and a 'testing' group
  - Split samples groups equally
  - Determine sample size
  - If this experiment has finite audience, then we might need to do the test longer to make sure there is enough interactions to gain a statistical result.
  - Decide how significant you results need to be 
  - Make sure you're only running one test at a time on any campaign



- **What metrics do you want to improve?**
- **Can you think of some variations can be made?**
- **What change do you want to test? Why?**
- **How many visiits/sample size do I need?**
- **Can you calculate the practical significance (given costs)?**
- **Will you launch the variation? (Given the test result)**
- **How big is the sample size**
- **How long to run the experiment?**
- **How much traffic% for testing?**
- **How to divide the % of the traffic for testing?**
- **What's the target audience of the testing?**



- **How to make your result more confidence?**

  You can increase in confidence by A increase the confidence level which means you can change your significant level and increase the power.

  You can increase the power. A) increase the sample size , so you can either open your experiment to attach more traffic or longer time



# Statistical Questions





# Novelty Effect

- **How to avoid Novelty effect?** 

  **We ran an A/B test. Test won, so we make the change on the site for all users. But after waiting for some time, we realize that the new version of the site is not performing better than the old one. What could be the reason?**

  **Assume there was no technical or statistical problem with the test, and the reason has to do with user behavior**

  (From collection data challenge)

  This question is also really common and can be rephrased in tons of ways. Sometimes they directly ask you about novelty effect, but more often they give you some test results and you have to explain them.

  The main reason a situation like the one described in the question happens is because of novelty effect. That is, when a site puts up a small new feature, at first users tend to engage with it a lot out of curiosity and to try it out. As novelty wears off and users get used to it, they go back to their normal behavior.

  Obviously, this can have a very bad impact on test result reliability, since tests measure the impact of a change over a small period of time and use that data to estimate what would happen in the long run.

  A good proxy to check for novelty effect is:

  **IMPORTANT**

  1. From your test results, only consider users for which it was the first experience on the site. First time users are obviously not affected by novelty effect.

  2. Look at test results between new users in the control group vs new users in test group

  3. If test group is winning overall, but not winning for the new user subset, it is a big warning that your results might be affected by novelty effect. Especially in cases like the one of the question where you already know that some time after making the change, you saw no improvement.

  







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

