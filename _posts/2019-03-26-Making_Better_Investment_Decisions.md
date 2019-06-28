---
title: How to avoid investing in bad loans from Lending Tree
subtitle: Feature Importance helps making investment decisions.
image: /img/featureImportance/investment.jpg
---
High yield personal loan paper investments attract investors attention who are hungry for yield return. But to earn these attractive yield return, investors would have to make risky investment decisions. Read on to find out how to mitigate making risky investment decisions using algorithmic data model.

### Checking credit score and history, can not predict future loan payment default
Investors lose money when the loan paper that they invested in, are defaulted by borrowers. Focusing on borrower credit score and credit history, will not be enough to avoid bad loan paper. But what if we could reliably predict the likelihood of a bad loan paper default based on some factors of a loan paper?

Using loan paper datasets from Lending Tree, I set out to identify which dataset features should investors focus on, if they want to avoid losing money in bad loan paper. I first used feature importance from Random Forest to identify the features that have the most correlation to loan paper default. Then I use partial dependent plot and Shapley values to further examine how each unit increase of the dataset features influence the overall prediction.

Lending Tree has collected a long list of [dataset features](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/data/LCDataDictionary.txt) for loan paper that they sell. With proper method and correct algorithmic data model, these confusing dataset features can be turned into useful guide to investing. To learn how I derived the result of these data model, please checkout my full working code in this link below.
[Full working codes here](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/thinking_blackbox.ipynb)


### Credibility on prediction made by Random Forest
Using LendingTree datasets, after loading, data cleaning and fitting, Random forest produced an accuracy rate of prediction of 74%.
```
RandomForest ROC AUC: 0.7390850313774844
```

### High interest rate and sub grade loan contributed most to borrowers defaulting on loan paper payment.
Feature Importance of Random Forest found interest rate followed by sub grade loan to have most influence on triggering loan default.

![](https://cocoisland.github.io/img/invest/randomforestFeatureNeg.png)


### Partial dependence plot showed how each unit increase of interest rate impacted on the probability of loan paper default.
How much interest rate increased would have material impacts on borrower ability to make future payment? Partial dependence plot showed interest rate below 15% has lower probability of default. A rise of interest rate beyond 20%, raises loan default probabilities.

![](https://cocoisland.github.io/img/invest/rf_pdp_plot.png)

### Shapley showed how fairly distribute the “payout” among the features
Since Random forest data model predictions range from 70-80% accuracy, this means 20-30% predictions made, are wrong. Let examine what Random forest is thinking when it is making right prediction versus wrong prediction. To examine the edge cases, Shapley plot is used to sort which dataset features skewed the probability reading to cause Random forest to make a right or wrong prediction.

### Example case where RandomForest correctly predicted loan default (rf_pred=1) and the true value (y_val) of the case confirmed the loan was indeed defaulted. 
First, let look at prediction that RandomForest correctly predicted. For example case 19833, RandomForest has correctly predicted loan to default. Shapley plot show what are the dimensional features that RandomForest used to make the prediction.

```python
# True positives, with high confidence
preds[(y_val==1) & (rf_pred==1)].sort_values(by='confidence', ascending=False).head(1)

	y_val	rf_pred	rf_pred_proba	confidence
24627	1	1	0.781189	0.281189
```
#### Next Shapley plot showed interest rate of 15% as having high impact on probability of loan default.
Beside high interest rate, Shapley plot also showed "total revolving high limit" and high "sub grade" loan paper, to be high risk for default. Conversely "total high credit limit" to have lowering probability of loan default.

![](https://cocoisland.github.io/img/invest/shapley_correctPrediction.png)

#### Now for the prediction, let look at what RandomForest was thinking
Example case where RandomForest predicted loan default, but the loan did not default.
```python
# False positives, with high (mistaken) confidence
preds[(y_val==0) & (rf_pred==1)].sort_values(by='confidence', ascending=False).head(1)

	y_val	rf_pred	rf_pred_proba	confidence
33542	0	1	0.791149	0.291149
```
#### Shapley showed what was RandomForest thinking when it make wrong prediction.

![](https://cocoisland.github.io/img/invest/shapley_wrongPrediction.png)

For wrong prediction made on case 31995, RandomForest incorectly thought high "int_rate" of 17.47, would cause the loan to default. But opposing high credit limit of $12900 had high influence on preventing loan default.
![](https://cocoisland.github.io/img/rf_false_shap.png)

## Conclusion
As mentioned above, high accuracy score obtained from trained data model may not mean much, if the production deployed model does not gain confidence from users working with the model. However the ability to pierce into the inner working of mysterious black box data model, is invaluable skills and powerful techniques that any Data Scientists could have. Being able to understand how black box data models work and demonstrate to project stakeholders, will win much needed confidence and support of the data model deployment. Lastly gaining insight on how data model predicts, will enable a Data Scientist to develop investment strategy as in the case working with LendingTree investment loan profolio.
