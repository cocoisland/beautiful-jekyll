---
title: What is Good, Bad, Ugly feature data and What to do.
subtitle: Few Data Scientists write data models, but most Data Scientists clean data.
image: /img/algorithm/codeIcon.jpg
---

This article is inspired by one of our smartest cohort Data Science fellow, Daniel Martin, who was asked what is good data versus bad data with respect to a black box regression data model. Good question. Other than tweaking a few parameter settings to force a machine learning data model to bias one way or the others, most data scientists can only do data cleaning or data engineering to affect the result of the algorithmic data model.

### What is good, bad, ugly data
Since the good, bad and ugly data are classified in the context of resulting high or low accuracy score from a black box data model, the only relevant quality of the data will be how well it correlates to the actual result that compared to its prediction. Fitting good feature data will positively correlate well to the actual result used in the training. Bad feature data will negatively correlate to the actual training result. Ugly feature data are those data correlate both positively and negatively to actual training result.

### Sort out the good, the bad and ugly data
Before data cleaning or engineering, good-bad-ugly data must be identified in order to help our black bod data model to output accurate and meaningful score. 

#### Method 1: Quick and dirty looping through feature X data to see how well it score.
Adding and deleting feature X data to data model for quick score, is fast convenient ways to identify one or two good or bad feature X. But this method does not work for identifying many feature X nor ugly data.
```python
  for feature in [X1, X2, X3 ...]
    x = df[feature]
    bbm = blackBoxModel.fit(x)
    bbm.predict(y)
```

#### Method 2: Seaborn correlation visualization.
Seaborn correlation visualization map gives full picture of all feature X data, the good, bad and ugly.
```python
  import seaborn as sns
  sns.(df, x=[X1,X2,X3], y=Y, method=corr)

```

Method 3: Statsmodel
Statsmodel show complete picture of each feature X parameter cofficient, standard error and pvalue.
Feature X parameter coefficient shows how each degree increase or decrease impact directly on the output prediction.
Standard error show how often the range of feature X are predicted by the model.
Pvalue greater than 5% establishes null hypothesis as valid and all statsmodel reading will be rejected. 
Conversely pvalue less than 5% establishes null hypothesis as invalid and all statsmodel reading will be accepted

Method 4: variance factor
Unlike seaborn correlation which find correlation between feature X and prediction Y, variance factor only find correlation amont feature X in order to remove high collinearity between the features.

Method 5: basic data engineering by sorting out all wrong prediction.
When all correlation between features X and Y output or features X correlation among themselves have been cleaned out, all data model will still make wrong prediction. These are the true bad quality data that caused the data model to fail.

#### Find bad quality data
Combined prediction from data model with training actual result in a dataframe. Then filter out wrong prediction which are opposite to training actual result. Depending on the type of data model and what supporting library are available, it will be useful to pierce into how and why the data model makes the wrong prediction.

With Gradient boosting ....

For regression, these are usually the ugly data that gives regression data model a hard time classifying them. To help data model better sorting out data that resides in the border probabilities classification, increase rexxxx factor or use support vector gradient.

### Data cleaning or engineering.
After identifying problematic features X or bad quality data, data cleaning or engineering can begin.

Bad feature X data can be removed. Good feature X can be enhanced by squaring. Non numeric data can be transformed into numeric. Datetime can be grouped into year, month or day in ways that make sense.




