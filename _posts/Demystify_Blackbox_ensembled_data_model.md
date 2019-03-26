# Would you trust your life with a black box Artificial Intelligent data model.

Everytime a plane flies, do you wish the pilot would know inside-out working of black box AI model that controlled the plane. When a new data model is released to production, does anyone know whether data model would perform as good in production as in trained model.

Fortunately, there are ways to look into the thinking of black box data model.

lr = LogisticRegression(solver='lbfgs')
lr.fit(X, y)
pd.Series(lr.coef_[0], X.columns)

Firstly, feature important selection based on impurity reduction is biased towards preferring variables with more categories.

Secondly, when the dataset has two (or more) correlated features, then from the point of view of the model, any of these correlated features can be used as the predictor, with no concrete preference of one over the others.

gb = GradientBoostingClassifier()
gb.fit(X_train, y_train)
mportances = pd.Series(gb.feature_importances_, X_train.columns)
top_20 = importances.sort_values(ascending=False)[:20]
plt.figure(figsize=(8, 8))
top_20.sort_values().plot.barh(color='grey')

Importance can be measured by looking at how much the score (accuracy, F1, R^2, etc. - any score we’re interested in) decreases when a feature is not available.
