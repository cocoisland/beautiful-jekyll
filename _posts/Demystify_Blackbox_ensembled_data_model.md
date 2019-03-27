# Would you trust your life with a black box Artificial Intelligent data model.

[workbook codes here](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/thinking_blackbox.ipynb)

Everytime a plane flies, do you wish the pilot would know the inside-out working of black box AI model that controlled the plane. When a new data model is released to production, does anyone know whether data model would perform as good in production as in trained model.

Rather than trusting a blackbox data model by faith, let look into how blackbox data models think. Using data from LendingTree.com, examined how two data models (Logistic Regression, RandomForest) use the data to estabblish their models. After data cleaning-fitting-transforming- training, predictions by respective data models are shown below. At first glance, Logisic regression shows a higher accuracy score than RandomForest. This is due to Logistic simpler data model implementation by bruta-force mapping dimensional features to label outcome, which results in higher bias and overfitting in training data model as compared to production deployment. RandomForest data model works by assembling most significant dimensional features on label outcome, as measurement to its prediction accuracy.

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
