# Would you trust your life with a black box Artificial Intelligent data model.

[workbook codes here](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/thinking_blackbox.ipynb)

Everytime a plane flies, do you wish the pilot would know the inside-out working of black box AI model that controlled the plane. When a new data model is released to production, does anyone know whether data model would perform as good in production as in trained model.

Rather than trusting a blackbox data model by faith, let look into how blackbox data models think. Using data from LendingTree.com, examined how two examples of data models(Logistic Regression, RandomForest) use the data to estabblish their models. After data cleaning-fitting-transforming- training, predictions by respective data models are shown below. At first glance, Logisic regression shows a higher accuracy score than RandomForest. This is due to Logistic simpler data model implementation by bruta-force mapping dimensional features to label outcome, which results in higher bias and overfitting in training data model as compared to production deployment. RandomForest data model works by assembling most significant dimensional features on label outcome, as measurement to its prediction accuracy.

```python
LogisticRegression Accuracy: 0.8517464424320828
RandomForest ROC AUC: 0.7172292772194447
```
RandomForest comes from the ensemble data model family. It sees the world as group of factors contributes to a certain outcome. Logistic regression belongs to the Linear data model family, which sees the world with simplistic one-to-one straight line cause-effect relationship.

## What dimensional features does Logistic regression sees as having most impact on its prediction outcome.

The plot shows Logistic regression thinks higher "revolving balances" has most impact on model predictions on positive loan defaults from LendingTree.com datasets. 

![](https://github.com/cocoisland/cocoisland.github.io/blob/master/img/log_fe_pos.png) 

Conversely Logistic regression deems having highest "earliest credit line" as preventing loan defaults.
![](https://github.com/cocoisland/cocoisland.github.io/blob/master/img/log_fe_neg.png)

However RandomForest thinks interest rate follows by sub grade loan, has most influence on model predicion of positive loans default.
![](https://github.com/cocoisland/cocoisland.github.io/blob/master/img/rf_fe_neg.png)

## Taking a deeper view into how data models see each individual dimensional feature.
Using "loan interest rate" as an exmple feature, Logistic Regression data model can only see in straight line, projecting higher loan interest rate has decreasing loan default impact.

![](https://github.com/cocoisland/cocoisland.github.io/blob/master/img/log_pdp.png)

RandomForest model sees lower "loan interest rate" has lower loan default. A rise of interest rate to 15 and beyond 20, raises loan default probabilities.

![](https://github.com/cocoisland/cocoisland.github.io/blob/master/img/rf_pdp.png)


## Since data model predictions range from 70-80% accuracy, this means 20-30% predictions made, are wrong.
we Human learn by mistakes and the same applies to learning insight by examing mistake prediction made by data models. As Logistic regression operates by simple dimensional features one-to-one mapping to label output, there is not much insight to be gained from looking some occasionally coincidental dimensional features occurred in the wrong observation rows with respect to label output. Since RandomForest assembles a forest of trees data model to make prediction, it is beneficial to learn what forest of trees that RandomForest has assembled for a particular wrong prediction.

Sample True positive case predictions made by RandomForest model.
```python
# True positives, with high confidence
preds[(y_val==1) & (rf_pred==1)].sort_values(by='confidence', ascending=False).head(1)

	          confidence	rf_pred	rf_pred_proba	y_val
  19833	     0.283510	   1	      0.783510	   1
```
For case 19833, RandomForest correctly predicted loan default and these were the dimensional features that RandomForest used to make the prediction.

![](https://github.com/cocoisland/cocoisland.github.io/blob/master/img/rf_true_shap3.png)

Sample False positive case predictions made by RandomForest model.
```python
# False positives, with high (mistaken) confidence
preds[(y_val==0) & (rf_pred==1)].sort_values(by='confidence', ascending=False).head(1)

	           confidence	rf_pred	rf_pred_proba	y_val
  31995	      0.267696	 1	       0.767696	   0
```

