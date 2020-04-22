# MLB - Data Challenge

-----

**Notes:** The details of my implementation without many codes. This document is written for technical audience. So more code and logic details, please refer to `mlb-data_challenge`

[TOC]

<div style="page-break-after: always;"></div>
# Business Background

## Background

There are lots of baseball fans around the world. And players who are talented in this area will be honored as **Hall of Fame**. 

This is one of most honorable award in baseball area.

So if we identify which player is more likely to be selected by Hall of Fame, we might have better investment.

- For executives, they can know which players have higher potential
- For advertisement companies, they can know which players might bring higher revenue

## Problem & Task

For this exercise, I am going to analyze Major League Baseball statistics and come up with an implementation of a classifier that indicates if a player is in the baseball Hall of Fame or not, based on the players history performance.





# Data Source

## Environment

* Platform : Google Colaboratory
* Language : Python
* Version: 3.7.4
* Packages :
  * pandas
  * numpy
  * matplotlib
  * Scikit-learn
  * seaborn

* Inital Models : 
  * Decision Tree
  * K Nearest Neighbors
  * Random Forest
  * XGBoost



## Source Table

The data come from Sean Lahman. He summarized the data on his website ([link](http://www.seanlahman.com/)). 

The file contains:

1. **MASTER** - Player names, DOB, and biographical info
2. **Batting** - batting statistics
3. **Pitching** - pitching statistics
4. **Fielding** - fielding statistics  
5. **AllStarFull** - All-Star appearances
6. **Hall of Fame** - Hall of Fame voting data
7. **Managers** - managerial statistics
8. **Teams** - yearly stats and standings 
9. **BattingPost** - post-season batting statistics
10. **PitchingPost** - post-season pitching statistics
11. **TeamFranchises** - franchise information
12. **FieldingOF** - outfield position data  
13. **FieldingPost**- post-season fieldinf data
14. **ManagersHalf** - split season data for managers
15. **TeamsHalf** - split season data for teams
16. **Salaries** - player salary data
17. **SeriesPost** - post-season series information
18. **AwardsManagers** - awards won by managers 
19. **AwardsPlayers** - awards won by players
20. **AwardsShareManagers** - award voting for manager awards
21. **AwardsSharePlayers** - award voting for player awards
22. **Appearances** - details on the positions a player appeared at
23. **Schools** - list of colleges that players attended
24. **CollegePlaying** - list of players and the colleges they attended



For this project, I mainly use `HallofFame`, `Master`, `Batting` table for analysis. 

**More data will come into analysis in the future.**

<div style="page-break-after: always;"></div>
### Master Table

Master table contains the following information:

![8SCxBt.png](https://s2.ax1x.com/2020/03/09/8SCxBt.png)

<div style="page-break-after: always;"></div>
### Hall of Fame Table

Hall of Fame table contains the following information:

![8SPC4S.png](https://s2.ax1x.com/2020/03/09/8SPC4S.png)

<div style="page-break-after: always;"></div>
### Batting Table

Batting table contains the following information:

![8SP9N8.png](https://s2.ax1x.com/2020/03/09/8SP9N8.png)

<div style="page-break-after: always;"></div>
# Analysis Flow

I followed the below approach to do the analysis. Due to limit time, I was unable to analyze very deep nor could I go through every detail. But the logic is the same as what I showed below.

![](https://hackernoon.com/hn-images/1*oU3LAye3LxFcHg0UePmbSA.png)

Picture Source: [hackernoon](https://hackernoon.com/)







# Feature Engineer

**Objective**: Predict if a player is in the baseball Hall of Fame

**Approach**: Based on the objective, I aggregated all the data to individual label. The unit observation of the final table is per person level with his/her demographic features and baseball performance.

Due to the space of this document and the limit time, I only address the feature engineer process for one table. For other table, the approaches and logic behind are exactly the same. For more details, please refer to the codes.



<div style="page-break-after: always;"></div>
## Master Table

There are 18846 rows in total in this table with 18846 unique players. So there are no duplicate records. Each row represent an player's information.

```python
# check how many players are in this table
Master.playerID.nunique()
```



**Keep necessary columns**

Not all columns are useful for prediction. For example, I only need to know when was the player born so that I could know his age. I don't need the birth month, or where is his birth city etc. 

To avoid information redundant, I decided to drop some columns based on my understanding. Given more knowledge of the data and the domain knowledge, I could make better decisions. For now, I decided to drop them.

```python
# drop columns
droplist = ['birthMonth','birthDay', 'birthCountry','birthState', 'birthCity','deathDay','deathCountry',
            'deathState', 'deathCity', 'nameFirst', 'nameLast','nameGiven','retroID', 'bbrefID']
master_x = Master.drop(droplist,axis = 1).copy()
```



### Missing Values

I check the data for columns with missing values and decide how to handle them. The data is pretty clean.

**Death column**

There are lots of missing values in *death* related fields which make sense. Because many players are still alive. For those who are dead, their information are also useful. So the missing values here makes sense. Given more knowledge of the data, I could make better decisions like creating dummy variables.

For now, I think these missing values make sense and I would choose to keep them first.

**Other columns**

For columns like throws, bats, they indicate players' characteristics and I do think they are important. Since there only less than 1% missing, I decided to remove these missing values first. Given more knowledge of the data, I could make better imputation like using predictive modelings or find some third part data to complete the information.

For columns like height, weight, same operations: remove just for now.



```python
# Change setting to display all columns and rows
pd.set_option("display.max_columns", None)
pd.set_option("display.max_rows", None)

# check the the missing percentage
1 - master_x.count()/len(master_x.index)

# output
playerID      0.000000
birthYear     0.007588
deathYear     0.504616
deathMonth    0.504669
weight        0.046217
height        0.042715
bats          0.063196
throws        0.051894
debut         0.010241
finalGame     0.010241
dtype: float64
```



```python
# drop empty rows
master_x = master_x[(master_x.debut.notnull() & master_x.finalGame.notnull()) & master_x.birthYear.notnull() & 
                   master_x.throws.notnull() & master_x.bats.notnull()]

# impute missing values using median number (height, weight)
master_x.weight.fillna((master_x.weight.median()), inplace=True)
master_x.height.fillna((master_x.height.median()), inplace=True)

# the current missing values percentage after processing
1 - master_x.count()/len(master_x.index)
```



Now there are only 17446 records remaining.

```python
# ther are 17446 records remaining
master_x.shape
```



### Transformation

I care more about the players' age instead of when he was born. So I am gonna to replace the birth-year column with the age.

If a player dies within the five year span, he is eligible six months after his death provided he meets the above criteria. If an active player dies, he is eligible six months after his death.

The age calculation follows the following rules
* If the player is still alive (deathYear is null), then I use current year (2015) - birth year
* If the player is not alive (deathYear is not null), then I use death year  - birth year



```python
# calculate the age
master_x['age'] = np.where(master_x.deathYear.isnull(),master_x.birthYear.apply(lambda x: 2015 - x),master_x.deathYear - master_x.birthYear)
```



**Restriction for Hall of Fame - retire at least 5 years**

If the player wants to enter Hall of Fame, one condition is that the player has been retired for at least five seasons. 

If a player comes back and plays in the major leagues, the clock restarts. The easiest way to figure out the rule is to add six to the last season the player was active. Therefore, players eligible in 2007 played their last game in 2001.

So I want to find these inactive players. Only players retired for more than 5 years are qualified to enter Hall of Fame.

```python
# create a new column indicating the final game year for each player
master_x['finalgame_year'] = master_x.finalGame.apply(lambda x: float(str(x)[:4]))

# create label indicating the retire years so far
master_x['retire'] = master_x.finalgame_year.apply(lambda x: 2015 - int(x))
```



Now I have done with this dataset. I am going to select only necessary columns for prediction.

```python
master_final = master_x[['playerID','age','weight', 'height', 'bats', 'throws', 'debut','finalgame_year','retire']]
master_final.head()
```





Preview the data**

| playerID  | age  | weight | height | bats | throws | debut      | finalgame_year | retire |
| --------- | ---- | ------ | ------ | ---- | ------ | ---------- | -------------- | ------ |
| aardsda01 | 34.0 | 220.0  | 75.0   | R    | R      | 2004-04-06 | 2015.0         | 0      |
| aaronha01 | 81.0 | 180.0  | 72.0   | R    | R      | 1954-04-13 | 1976.0         | 39     |
| aaronto01 | 45.0 | 190.0  | 75.0   | R    | R      | 1962-04-10 | 1971.0         | 44     |
| aasedo01  | 61.0 | 190.0  | 75.0   | R    | R      | 1977-07-26 | 1990.0         | 25     |
| abadan01  | 43.0 | 184.0  | 73.0   | L    | L      | 2001-09-10 | 2006.0         | 9      |

### 

### Exploratory Data Analysis

### Outlier Detection 

Here I mainly use basic exploratory data analysis to gain insight of the data.



**Weight and Height**

Same situation happens for players' weight and height. It's possible for baseball players that are heavier than others or extreme high. I lack this domain knowledge. Given more time, I could make better decisions.

For now, I just use 1.5 quantile to replace those "outliers" values.

```python
# weight distribution
plt.figure(figsize = (20,5))
plt.subplot(1,4,1)
plt.title('weight Distribution')
sns.distplot(full_data.weight)
plt.subplot(1,4,2)
plt.title('weight BoxPLot')
sns.boxplot(full_data.weight)
plt.subplot(1,4,3)
plt.title('height Distribution')
sns.distplot(full_data.height)
plt.subplot(1,4,4)
plt.title('height BoxPLot')
sns.boxplot(full_data.height)
plt.show()
```

![8SiNss.png](https://s2.ax1x.com/2020/03/09/8SiNss.png)



```python
# create a function to remove outlier based on quantile
def remove_outlier(column_name,low,high):
  q1, q3= np.percentile(full_data[column_name],[low,high])
  iqr = q3 - q1
  lower_bound = q1 -(1.5 * iqr) 
  upper_bound = q3 +(1.5 * iqr)
  full_data.loc[full_data[column_name] > upper_bound ,column_name] = upper_bound
  full_data.loc[full_data[column_name] < lower_bound ,column_name] = lower_bound
```



```python
# remove outliers in weight column
remove_outlier('weight',25,75)

# remove outliers in height column
remove_outlier('height',25,75)
```



**Bats and throws**

The distribution of `bats` and `throws` are also not very balanced. This make sense since most people are right handed. I am not sure if this will impact our analysis at this point, but I'll do **feature selection** later do see if this feature is important.

```python
# check the distribution
plt.figure(figsize = (12,5))
plt.subplot(1,2,1)
sns.countplot(full_data.bats)
plt.subplot(1,2,2)
sns.countplot(full_data.throws)
plt.show()
```

![8SPL5T.png](https://s2.ax1x.com/2020/03/09/8SPL5T.png)

**Age**

It seems that most players' ages are in reasonable range. 

However, by looking at the box plot, there are some outliers which might not be reasonable.

```python
# age distribution
plt.figure(figsize = (12,5))
plt.subplot(1,2,1)
plt.title('Age Distribution')
sns.distplot(full_data.age)
plt.subplot(1,2,2)
plt.title('Age BoxPLot')
sns.boxplot(full_data.age)
plt.show()
```

![8SiuqI.png](https://s2.ax1x.com/2020/03/09/8SiuqI.png)



So there are some people aged more than 120 years old which doesn't make sense. I decided to remove them in terms of the data quality.

The lowest age here is -19 years old which should be removed

```python
print('Max Age')
print('---------')
print(full_data.age.sort_values(ascending = False)[:10])
print('Min Age')
print('---------')
print(full_data.age.sort_values(ascending = True)[:10])

# output
Max Age
---------
3736     168.0
13102    164.0
12768    161.0
7981     159.0
8358     156.0
16803    155.0
3954     151.0
7367     150.0
11875    150.0
8556     147.0
Name: age, dtype: float64
Min Age
---------
7882    -19.0
14651    20.0
11901    20.0
3729     20.0
2740     21.0
14225    21.0
14307    21.0
11703    21.0
7046     21.0
16717    21.0
Name: age, dtype: float64
```



```python
# only keep resonable age
full_data = full_data[(full_data.age <= 120) & (full_data.age > 15)]
```

<div style="page-break-after: always;"></div>
# Predictive Modeling

## Normalization

Normalizing the features allows for faster gradient descent convergence and reduce bias of features which have large ranges.

```python
min_max_scaler = preprocessing.MinMaxScaler()
x_scaled = min_max_scaler.fit_transform(x)
x_scaled_df = pd.DataFrame(x_scaled, columns = x.columns)
```



## Feature Selection

Taking a univariate selection approach, I choose to use the chi2 metric since the target is categorical.
I also tested using f_classif which also worked, and mutual_info_classif (long runtime).

Actually, there are multiple ways to do feature selection. 

* Univariate Selection
* Feature Important
* Correlation Matrics with Heatmap
* And so on

I chose the first approach for no reason. If I could have more time, I'll also try other approaches. In addition, the thrid approach returns me the result that there are tons of correlated features and leave nothing to me. I guess this might due to the small sample size. I need more inforamtion to make the decision. For now, Univariate could be a good approach. 



```python
selector = SelectPercentile(chi2, percentile=20)
fit = selector.fit(x_scaled_df,y)

# Show results from greatest to least
x_scores = pd.DataFrame(fit.scores_)
x_col = pd.DataFrame(x_scaled_df.columns)
featureScores = pd.concat([x_col,x_scores],axis=1)
featureScores.columns = ['Feature', 'Score']
fs_sorted = featureScores.sort_values('Score', ascending=False)
fs_sorted
```

| Features  | Score     |
| --------- | --------- |
| R         | 50.027255 |
| RBI       | 49.348040 |
| H         | 44.371156 |
| And so on | And so on |



```python
# Filter dataframe on features with highest scores
x_chi2 = x_scaled_df[fs_sorted.Feature[0:14].tolist()]
x_chi2.head()
```





## Model Construction

Here I want to skip the basic training and split process and briefly talk about the models.

I used models including

- K Nearest Neighbor
- Decision Tree
- Random Forest
- XGBoost



### Other Models

In this document, I only introduce how I do with XGBoost, for other models, please refer to the detail codes



### **XGBoost**

Documentation: https://xgboost.readthedocs.io/en/latest/



```python
# Fit XGRegressor to the Training set
xg_reg = xgb.XGBRegressor(objective ='binary:hinge', 
                          learning_rate = 0.1,
                          max_depth = 5)
xg_reg.fit(X_train,y_train)

# Test the model
pred_xgb = xg_reg.predict(X_test)

# Get the model performance
print(classification_report(y_test, pred_xgb))

# Get all Measurements
xgb_summary = get_all_measurements(y_test, pred_xgb, "XGBoost")
xgb_summary
```

![8SkJDs.png](https://s2.ax1x.com/2020/03/09/8SkJDs.png)

The XGBoost model give us 92% accuracy and around 0.58% precision and 36% recall. This is not very good. I will summarize the low performance later. 



```python
# plot roc curve
plt.figure(figsize = (6,4))
fpr_xgb, tpr_xgb, thresholds = roc_curve(y_test, pred_xgb)
plt.plot(fpr_xgb, tpr_xgb, linewidth=1, label='XGBoost') 
plt.title("XGBoost ROC Curve")
plt.show()
```

![8SkNEq.png](https://s2.ax1x.com/2020/03/09/8SkNEq.png)



**Visualize Results: Feature Importance and sample tree**

Visualizing the model for a better idea of what's going on in the blackbox.



![8Ska5V.png](https://s2.ax1x.com/2020/03/09/8Ska5V.png)

```python
# Visualizing: Shows the sixth boosted tree
plt.rcParams['figure.figsize'] = [70, 35]
xgb.plot_tree(xg_reg, num_trees=5)
```

![8SkgV1.png](https://s2.ax1x.com/2020/03/09/8SkgV1.png)

This is the visualization of the tree. Clear picture could be found here: [Link](https://s2.ax1x.com/2020/03/09/8SkgV1.png)



#### Hyper-parameter Tuning

I can improve the performance (AUC, accuracy, etc) by tuning the parameters, but this requires more time. I have included code below that can be used for this purpose.

The most popular method for tuning hyperparameters is using GridSearch.

Documentation: 

https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html



```python
# Code for using GridSearch to tune hyperparameters
# list some feasible features for tuning, Will add more in the feature
parameters = {'objective' : ['binary:hinge','binary:logistic']}
              # 'learning_rate' : [0.05, 0.1],
              # 'max_depth' : [5, 4, 3],
              # 'gamma' : [0.5, 1]}

clf = GridSearchCV(xgb.XGBRegressor(), parameters, n_jobs=5 ,
                   cv=StratifiedKFold(n_splits=5, shuffle=True), 
                   scoring='roc_auc',
                   verbose=2, refit=True)

clf.fit(X_train, y_train)

print(clf.best_score_)
print(clf.best_params_)

# output
0.9061710653839832
{'objective': 'binary:logistic'}
```



### Model Comparison and Conclusion

Here, I want to plot all the ROC curve together.

```python
plt.figure(figsize = (12,8))
plt.plot(fpr_xgb, tpr_xgb, linewidth=1, label='XGBoost') 
plt.plot(fpr_knn, tpr_knn, linewidth=1, label='KNN') 
plt.plot(fpr_dt, tpr_dt, linewidth=1, label='Decision Tree') 
plt.plot(fpr_rf, tpr_rf, linewidth=1, label='Random Forest') 
plt.title("Model ROC Curves")
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.legend(loc = 'lower right')
plt.show()
```

![8SkwCT.png](https://s2.ax1x.com/2020/03/09/8SkwCT.png)

And these is the result comparison among each model.

![8SkjG8.png](https://s2.ax1x.com/2020/03/09/8SkjG8.png)



With limited information, I am not sure the penalty/cost of wrong prediction ( False positive and False negative). So personally I prefer a model with high precision and recall in imbalanced data.

Since Random Forest has the highest F1-score. It's my best my model this time.

<div style="page-break-after: always;"></div>
# Reflection & What's Next

## Imbalanced Issue

I think this is the most severe issues in this analysis this time. 

This is a very **imbalanced data** in terms of target variable and will cause some problem in our feature prediction. With this in mind, let me finish the prediction and discuss more about the consequence of using imbalanced data.

```python
# check the distribution
plt.figure(figsize = (6,5))
sns.countplot(full_data.inducted)
```

![8SPqaV.png](https://s2.ax1x.com/2020/03/09/8SPqaV.png)

And most time we are referring to **accuracy**. However, for imbalanced data, accuracy might not make perfect sense. 

The conventional model evaluation methods do not accurately measure model performance when faced with imbalanced datasets.

"*Standard classifier algorithms like Decision Tree and Logistic Regression have a bias towards classes which have number of instances. They tend to only predict the majority class data. The features of the minority class are treated as noise and are often ignored. Thus, there is a high probability of misclassification of the minority class as compared to the majority class"*   (from [Link](https://www.analyticsvidhya.com/blog/2017/03/imbalanced-data-classification/) )

So we need to address this issue.



- Collect more data
- Resampling Techniques
  - Random Undersample
  - Random oversample
- Cluster-Based Over Sampling
- Try more ensemble models

## Model Aspect

### **Constructing Model**

I tried some baseline models to have a feeling of the prediction. However, I was unable to do hyper-parameter tuning which is very important for modeling.

Also, try to use more ensemble models techniques

So, next

1. Try hyper-parameter turning.
   1. Grid Search
   2. Random Search
2. Try ensemble model
   1. Bagging
   2. Boosting
   3. Stacking etc

### Evaluating Models

Apart from constructing models, we should also come up with more evaluation metrics.

Lift chart could be a good example.

In addition, we should also collect information about the cost of wrong prediction (false positive and false negative) so that we can better decide which metrics works better in our context.

By having the penalty/cost information, we could also build a **cost matrix**, combined with confusion matrix, we can know the expected value (cost) of making a wrong prediction. This is helpful for us when choosing models.

### Time Series Model

Our current objective is to predict if a player is in the Hall of Fame or not. In the future, we can extend our analysis/model to predict if a player will be in the Hall of Fame next year.

This is a time-series prediction problem.

We could take advantage of history data to predict future. From business application prospective, this model might be more widely used.

## Data Source Aspect

This time, I only used some tables. In the future analysis, we should include more players' information.

For example:

- Number of Big Awards Received
- Win times
- Lose Time
- Team
- League
- Salary Information
- And so on

With more sound and reliable data, we can have a better prediction.

## Data Engineer Aspect

We cannot ensure the quality of the data. Missing values, outliers always exists.

This time, I dropped some outliers directly because of they are very small proportion of the whole data. But with more time, research and information, I think we can try some imputation like

- Aggregation (min/max/median)
- Prediction Models

Or we might find some third part data to supplement our source table.

In addition,

More Exploratory Data Analysis should be performed.

## Application Aspect

Think more about how this prediction can impact the real-world business so that we could better tailor our product to the market.

Maybe design an **interactive dashboard** for baseball executives to use. Or maybe we can try to program a phone application etc.

---------

Done! 

Thanks for Reading

2020/03/08

​																																				**Warm Regards**

​																																				**Xiangke Chen**