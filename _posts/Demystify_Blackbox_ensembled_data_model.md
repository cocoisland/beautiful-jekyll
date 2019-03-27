# Would you trust your life with a black box Artificial Intelligent data model.

[workbook codes](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/thinking_blackbox.ipynb)

Everytime a plane flies, do you wish the pilot would know inside-out working of black box AI model that controlled the plane. When a new data model is released to production, does anyone know whether data model would perform as good in production as in trained model.

Rather than trusting a blackbox data model by faith, let look into how blackbox data models think. Using data from LendingTree.com, examined how three data models (Logistic Regression, RandomForest, GradientBoosting) use the data to estabblish their models. After data cleaning-fitting-transforming- training, predictions by respective data models are shown below:
[workbook codes](https://github.com/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/thinking_blackbox.ipynb)

```python
LogisticRegression Accuracy: 0.8517464424320828
RandomForest ROC AUC: 0.7172292772194447
GradientBoosting ROC AUC: 0.712577529134745

```
Firstly, feature important selection based on impurity reduction is biased towards preferring variables with more categories.

Secondly, when the dataset has two (or more) correlated features, then from the point of view of the model, any of these correlated features can be used as the predictor, with no concrete preference of one over the others.

gb = GradientBoostingClassifier()
gb.fit(X_train, y_train)
mportances = pd.Series(gb.feature_importances_, X_train.columns)
top_20 = importances.sort_values(ascending=False)[:20]
plt.figure(figsize=(8, 8))
top_20.sort_values().plot.barh(color='grey')

Importance can be measured by looking at how much the score (accuracy, F1, R^2, etc. - any score we’re interested in) decreases when a feature is not available.
