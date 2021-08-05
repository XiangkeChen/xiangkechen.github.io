---
layout:     post
title:      A Crash in Causal Inference
subtitle:   Causal Inference, DID, RDD, Panel Data
date:       2020-04-19
author:     Xiangke
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - Statistics
    - Causal Inference
    - Data Analysis
---




# A Crash In Causal Inference

I leaned **Causal Inference** in my master program and found it's interesting and used frequently in business world. I am pretty interested in it and decided to take another causal course. 

This is my notes for the course **A Crash In Causal Inference** at Coursera.



- **Course Name**: A Crash Course in Causality: Inferring Causal Effects from Observational Data
- **Platform**: Coursera
- **University**: by University of Pennsylvania
- **Professor**: Jason A. Roy, Ph.D.





# Hypothetical Interventions

There are something you could manipulate while others not.


For example,

Intervention like `Region`, `whether to have a drug` a things that you can change.

If you care about whether the race has a causal impact of people getting a job, you cannot assign race to one person. Instead, you can do like what are listed in the table:

| No Direct Intervention | Manipulate Intervention |
| ---------------------- | ----------------------- |
| Race                   | Name on Resume          |
| Obesity                | Bariatric Surgery       |
| Socioeconomics Status  | Gift of Money           |



This course/notes primarily focus on treatments/exposures that could be thought of as interventions

- Treatment that we can imagine being randomized (manipulated) in a hypothetical trial. 

Because their meaning is well defined and potentially actionable.



The **Fundamental Problem of Causal Inference** is that we can only observe one potential outcome for each person.

However, with certain assumptions, we can estimate population level (average) causal effects.



# Average Causal Inference Effects

**How to estimate causal inference effects?** 



**Example**: Regional (A=1) versus genreal (A=0_ anesthesia for hip fracture surgery on risk of major pulmonary complications

- Suppose E(Y_1 - Y_0) = 1
  - Probability of major pulmonary complications is lower by 0.1 if given regional anesthesia compared with general anesthesia.
  - If 1000 people were going to have hip  fracture surgery, we would expect 100 fewer people to have pulmonary complications under regional anesthesia compared with general anesthesia. 



**In General**

```
E(Y_1 - Y_0) ≠ E(Y|A=1) - E(Y|A=0)
```

It's changing the original population which is not true. 



E(Y|A=1) - E(Y|A=0) is genially **NOT** a causal effect. Because it is comparing two different populations of people

E(Y_1 - Y_0) is a causal effect because it is comparing what would happen if the same people treated with A=1 versus if the **SAME PEOPLE** were treated with A = 0.























