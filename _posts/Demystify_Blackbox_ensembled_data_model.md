# Would you trust your life with a black box Artificial Intelligent data model.

Everytime a plane flies, do you wish the pilot would know inside-out working of black box AI model that controlled the plane. When a new data model is released to production, does anyone know whether data model would perform as good in production as in trained model.

Rather than trusting a blackbox data model by faith, let look into how blackbox data models think. Using data from LendingTree.com, examined how three data models (Logistic Regression, RandomForest, GradientBoosting) use the data to estabblish their models. After data cleaning-fitting-transforming- training, predictions by respective data models are shown below:
[View training data model and prediction codes](https://colab.research.google.com/github/cocoisland/DS-Unit-4-Sprint-1-Tree-Ensembles/blob/master/thinking_blackbox.ipynb#scrollTo=drrf_vENTTeQ)

```python
#How do Linear or Regression model think
encoder = ce.OrdinalEncoder()
X_train = encoder.fit_transform(X_train)

X_train, X_val, y_train, y_val = train_test_split(
    X_train, y_train, test_size=0.2, stratify=y_train, random_state=42)

lr = LogisticRegression(solver='lbfgs')
lr.fit(X_train,y_train)
lr_pred = lr.predict(X_val)

rf = RandomForestClassifier(n_estimators=100, 
        class_weight='balanced', 
        min_samples_leaf=0.005, )
rf.fit(X_train, y_train)
rf_pred_proba = rf.predict_proba(X_val)[:,1]

gb = GradientBoostingClassifier()
gb.fit(X_train, y_train)
gb_pred_proba = gb.predict_proba(X_val)[:,1]

print('LogisticRegression Accuracy:', accuracy_score(y_val, lr_pred))
print('RandomForest ROC AUC:', roc_auc_score(y_val, rf_pred_proba))
print('GradientBoosting ROC AUC:', roc_auc_score(y_val, gb_pred_proba))

LogisticRegression Accuracy: 0.8517464424320828
RandomForest ROC AUC: 0.7172292772194447
GradientBoosting ROC AUC: 0.712577529134745

```



```python
LogisticRegression: Features coefficients show their relative impact on model predictions.
lr = LogisticRegression(solver='lbfgs')
lr.fit(X, y)
pd.Series(lr.coef_[0], X.columns)
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
