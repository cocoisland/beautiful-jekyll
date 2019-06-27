---
title: How to avoid investing in bad loans from Lending Tree
subtitle: Feature Importance helps making investment decisions.
image: /img/featureImportance/investment.jpg
---
High yield personal loan paper investments attract investors attention who are hungry for yield return. But to earn these attractive yield return, investors would have to make risky investment decisions. Read on to find out how to mitigate making risky investment decisions using data science data model.

### Checking credit score and history, can not predict future loan payment default
Investors lose money when the loan paper that they invested in, are defaulted by borrowers. Focusing on borrower credit score and credit history, will not be enough to avoid bad loan paper. But what if we could reliably predict the likelihood of a bad loan paper default based on some factors of a loan paper?

Using loan paper datasets from Lending Tree, I set out to identify which dataset features should investors focus on, if they want to avoid losing money in bad loan paper. I first used feature importance of Random Forest to identify the features that have the most correlation to loan paper default. Then I use partial dependent plot and Shapley values to further examine how each unit increase of the dataset features influence the overall prediction.

Lending Tree has collected a long list of [dataset features](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/data/LCDataDictionary.txt) for loan paper that they sell. With proper method and correct algorithmic data model, these confusing dataset features can be turned into useful guide to investing. To learn how I derived the result of these data model, please checkout my full working code in this link below.
[Full working codes here](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/thinking_blackbox.ipynb)


### High interest rate and sub grade loan contributed most to borrowers defaulting on loan paper payment.
Using LendingTree datasets, interest rate followed by sub grade loan is found by Random Forest to have most influence on triggering loan default.

![](https://cocoisland.github.io/img/featureImportance/randomforestFeatureNeg.png)


### Partial dependence plot showed how each unit increase of interest rate impacted on the probability of loan paper default.
As shown in the Partial dependence plot, interest rate below 10% has lower probability of default. A rise of interest rate beyond 10%, raises loan default probabilities.

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
