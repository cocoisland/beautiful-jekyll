---
title: How to avoid investing in bad loans from Lending Tree
subtitle: Feature Importance helps making investment decisions.
image: /img/featureImportance/investment.jpg
---
High yield personal loan package investments attract investors attention who are hungry for yield return. But to earn these attractive yield return, investors would have to make risky investment decisions. Read on to find out how to mitigate making risky investment decisions using data science data model.

### Checking credit score and history, can not predict future credit default
Investors lose money when the loan that they invested in, are defaulted by borrowers. Focusing on borrower credit score and credit history, are not enough to avoid bad loan package. Investing can be safer than gambling if the investment is made following a systematic process of risk mitigation procedure. To help investors avoiding bad loan packages, Lending Tree provides many pertinent statistical information about the loan package. Unfortunately these long list of statistical investment data are not easily understandable by human. Data science algorithmic data models can be used to help investors navigated through these mountain of statistical data.

### High data model accuracy scores are not indicative of producing better investment result.
After data cleaning, fitting, transformation under model training, data model shows how well they do with accuracy score.
Rather than trusting your investment decision on a blackbox data model by faith, let look into how well two data models work behind the cover. Using data from LendingTree.com, Logistic Regression and RandomForest data models are fitted with data and run to produced with accuracy score. 

[Full working codes here](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/thinking_blackbox.ipynb)

```python
LogisticRegression Accuracy: 0.8517464424320828
RandomForest ROC AUC: 0.7172292772194447
```
At first glance, Logistic regression shows a higher accuracy score than RandomForest. This is due to Logistic regression simpler data model implementation by counting the frequency mapping of dimensional features to label output, which could easily result in higher bias and overfitting in training data model. Logistic regression belongs to the Linear data model family, which sees the world with simplistic one-to-one straight line cause-effect relationship.

RandomForest data model works by assembling a forest of ensembled trees of dimensional features subset with most signficant influence on label output. RandomForest comes from the ensembled data model family. It sees the world as group of factors contributes to a certain outcome. 

### What do data models see as having most impact on its prediction outcome.
Investors rely on their past experience to choose which attributes of loan packages to focus on, while data model uses past statistical data which correlates to the success or failure of loan package payoff to make predictions. Looking under the cover beyond the data model prediction accuracy, we check feature importance of the model to find out what influence the model to arrive at their prediction.

The diagram below shows Logistic regression deemed higher "revolving balances" had most impact on model predictions on preventing loan defaults from LendingTree.com datasets. 

![](https://cocoisland.github.io/img/featureImportance/logisticFeatureImportance.png) 

However Logistic regression deemed having highest "earliest credit line" as preventing loan defaults.

![](https://cocoisland.github.io/img/log_fe_neg.png)

However RandomForest considered interest rate follows by sub grade loan, had most influence on model predicion of positive loans default.

![](https://cocoisland.github.io/img/rf_fe.png)

## Taking a deeper view into how data models see each individual dimensional feature.
Using "loan interest rate" as an example feature, Logistic Regression data model can only see in straight line projection, predicting higher loan interest rate, will decrease loan default probability.

![](https://cocoisland.github.io/img/log_pdp.png)

RandomForest model sees lower "loan interest rate" has low loan default. A rise of interest rate to 15% and beyond 20%, raises loan default probabilities.

![](https://cocoisland.github.io/img/rf_pdp.png)


## Since data model predictions range from 70-80% accuracy, this means 20-30% predictions made, are wrong.
Human learns by mistakes and the same applies to learning how wrong prediction made by data models. As Logistic regression operates by simple dimensional features mapping to label outcome, there is not much insight to be gained from coincidental  features occurred in the wrong observation rows with respect to label outcome. Since RandomForest assembles a forest of trees data model to make prediction, it is beneficial to learn what forest of trees that RandomForest has assembled for a particular wrong prediction.

First, let look at prediction that RandomForest correctly predicted. For example case 19833, RandomForest has correctly predicted loan default and these were the dimensional features that RandomForest used to make the prediction.

```python
# True positives, with high confidence
preds[(y_val==1) & (rf_pred==1)].sort_values(by='confidence', ascending=False).head(1)

	     confidence	rf_pred	rf_pred_proba	y_val
  19833	     0.283510	   1	  0.783510	   1
```
To correctly predict loan default as in case 19833, RandomForest considered "sub_grade" and "int_rate" as having higher impact than opposing feature as "dti (ratio of total monthly debt payment over total debt obligation).
![](https://cocoisland.github.io/img/rf_true_shap3.png)

Conversely sample False positive case 31995, was wrong predictions made by RandomForest model.
```python
# False positives, with high (mistaken) confidence
preds[(y_val==0) & (rf_pred==1)].sort_values(by='confidence', ascending=False).head(1)

	     confidence	rf_pred	rf_pred_proba	y_val
  31995	      0.267696	 1	   0.767696	   0
```

For wrong prediction made on case 31995, RandomForest incorectly thought high "int_rate" of 17.47, would cause the loan to default. But opposing high credit limit of $12900 had high influence on preventing loan default.
![](https://cocoisland.github.io/img/rf_false_shap.png)

## Conclusion
As mentioned above, high accuracy score obtained from trained data model may not mean much, if the production deployed model does not gain confidence from users working with the model. However the ability to pierce into the inner working of mysterious black box data model, is invaluable skills and powerful techniques that any Data Scientists could have. Being able to understand how black box data models work and demonstrate to project stakeholders, will win much needed confidence and support of the data model deployment. Lastly gaining insight on how data model predicts, will enable a Data Scientist to develop investment strategy as in the case working with LendingTree investment loan profolio.
