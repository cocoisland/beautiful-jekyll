## Can you predict which water pumps are faulty?

Using data from Taarifa and the Tanzanian Ministry of Water, the goal of the Kaggle competition was to predict which water pumps were functional, which needed repairs, and those which didn’t work at all.
Predict one of these three classes based on a number of variables about what kind of pump is operating, when it was installed, and how it is managed.
A smart understanding of which waterpoints will fail can improve maintenance operations and ensure that clean, potable water is available to communities across Tanzania.

Kaggle competition or not, all data modeling project should start with a baseline model, so that subsequent model can compare with.

### Begin project by establishing Baseline metrics.
#### Method 1: Majority baseline by value_counts. Random chance predictions have
54% functional well pump.
38% non-functional pump.
7% repairable.

```python
df_label.status_group.value_counts(normalize=True)
functional                 0.543081
non functional             0.384242
functional needs repair    0.072677
Name: status_group, dtype: float64
```
#### Method 2: Feed LogisticRegression with numeric only.
Numeric data value can range so wide that no regression iteration can ever be enough to converge.
Do not increase max_iteration of LogisticRegression, instead call a Scaler.

```python
X=df_num = df_train.select_dtypes(np.number)
pipe = make_pipeline(
    RobustScaler(),
    LogisticRegression(solver='lbfgs',multi_class='auto',max_iter=500)
    )
pipe.fit(X,y)
y_pred = pipe.predict(X)

Accuracy score= 0.5577946127946128
```
#### Method 2: LogisticRegression with non-numeric categorical value object only.
Encoders are friend of LogisticRegression, transforming non-numeric data into numeric.
But nasty data character are hidden landmine bomb to Encoder.
Nasty datatype - NaN, '?', space in front/after, keyword:False, True, None .

Data cleanup
```python
def cleanup(data):
  data.fillna('unknown', axis=1, inplace=True)
  
  # Nasty keyword(False, True) object breaks OneHotEncoder
  data['permit'] = data['permit'].astype(dtype='str')
  data['public_meeting'] = data['public_meeting'].astype(dtype='str')
  
  # One unique value adds no value, hence removed
  data.drop('recorded_by', axis=1, inplace=True)
  
  return data
df_train = cleanup(df_train).copy()

```
#### High cardinality features add no value but noise to regression.
Filter out features with high number of unique categorical values by eyeballing method.
nunique() function lists out number of unique categorical values.
```python
# Exclude non-number columns with high number of categorical values. 
# High cardinality columns when split by encoding turns into many useless noisy data.
filter_cols  = df_train.select_dtypes(object).nunique().sort_values().index.tolist()[:-6]
X = df_train[filter_cols].copy()
pipe = make_pipeline(
    OneHotEncoder(categories='auto'),
    LogisticRegression(solver='lbfgs', multi_class='ovr',
                      max_iter=500))
pipe.fit(X,y)
y_pred = pipe.predict(X)
accuracy=accuracy_score(y, y_pred)

Accuracy score= 0.757020202020202
```
OneHotEncoding non-numeric categorical value into 0 and 1.
Automatically increase both training accuracy score and testing bias into the model.

#### Method 3: LogisticRegression with categorical value without Encoder.
Transforming unique categorical value into nominal value is more accurate and efficient than OneHotEncoding.

```python
X = df_cat = df_obj.apply(lambda x: x.astype('category').cat.codes)
pipe = make_pipeline(
    RobustScaler(),
    LogisticRegression(solver='lbfgs',multi_class='auto',max_iter=500)
    )
pipe.fit(X,y)
y_pred = pipe.predict(X)

Accuracy score= 0.6286531986531987
```

#### Method 4: Include all non-numeric categorical value (all cardinality) using cat code.
Converting non-numeric to category code, solve the high cardinality columns problem.
```python
X = df_cat_all = df_train.apply(lambda x: x.astype('category').cat.codes)
pipe = make_pipeline(
    RobustScaler(),
    LogisticRegression(solver='lbfgs',multi_class='auto',max_iter=500)
    )
pipe.fit(X,y)
y_pred = pipe.predict(X)

Accuracy score= 0.6557912457912458
```
#### Method 5: Everything both numeric and non-numeric using Encoder
OneHotEncoder going crazy transforming both numeric and non-numeric, turning LogisticRegression into a neural network overfitting model?
Accuracy of 96% on training data? OneHotEncoder not to be trusted.
Using this model to predict on df_test data, yields nonsense category unknown error.
```python
pipe = make_pipeline(
    OneHotEncoder(categories='auto'),
    LogisticRegression(solver='lbfgs', multi_class='ovr',
                      max_iter=2000))

pipe.fit(X,y)
y_pred = pipe.predict(X)

Accuracy score= 0.9674579124579125
````

#### DecisionTreeClassifier
Fast and raise accuracy to reasonable 74%.
```python
clf = DecisionTreeClassifier()
cv_score = cross_val_score(clf, 
                            X, y,
                            scoring = 'accuracy',
                            cv = 3,
                            n_jobs = 1,
                            verbose = 1)

score.loc[score.shape[0]] = ['DecisionTreeClassifier_all', cv_score.max(), X.shape]
cv_score

array([0.74191919, 0.74358586, 0.73823232])
```

#### RandomForestClassifier
```python
param_grid = {
    'n_estimators': [10, 20, 30],
    'max_depth': [6, 10, 20, 30]
}
gridsearch = GridSearchCV(RandomForestClassifier(n_jobs = 1), 
                       0.8078619528619528   param_grid=param_grid, 
                          scoring='accuracy', cv=3, 
                          return_train_score=True, verbose=1)
gridsearch.fit(X, y)
score.loc[score.shape[0]] = ['RandomForestClassifier_all', gridsearch.best_score_, X.shape]
gridsearch.best_score_
0.8078619528619528

```

#### Prepare validation testing for RandomForestClassifier and XgBoost.
```python
y_num = y_train.apply(lambda x: x.astype('category').cat.codes)
y_test_num = y_test.apply(lambda x: x.astype('category').cat.codes)

xg_train = xgb.DMatrix(X_train, label=y_num.status_group)
xg_test = xgb.DMatrix(X_test, label=y_test_num.status_group)
xg_train.save_binary('train.buffer')
xg_test.save_binary('train.buffer')
# setup parameters for xgboost
param = {}
# use softmax multi-class classification
param['objective'] = 'multi:softmax'
param['silent'] = 1 # cleans up the output
param['num_class'] = 3 # number of classes in target label

watchlist = [(xg_train, 'train'), (xg_test, 'test')]
num_round = 30
bst = xgb.train(param, xg_train, num_round, watchlist)

# get prediction
y_pred1 = bst.predict(xg_train)
y_pred2 = bst.predict(xg_test)
print('Train accuracy score:',accuracy_score(y_num.status_group,y_pred1))
print('Test accuracy score:',accuracy_score(y_test_num.status_group,y_pred2))

score.loc[score.shape[0]] = ['XgBoost_all', accuracy_score(y_num.status_group,y_pred1), X_train.shape]

Train accuracy score: 0.8024410774410774
Test accuracy score: 0.7781144781144781
```

### All score
```python
	method	accuracy	shape
0	majority_baseline	0.543081	(1, 1)
1	logReg_num	0.557795	(59400, 9)
2	logReg_OneHotEncoder	0.757020	(59400, 23)
3	logReg_cat_codes	0.628653	(59400, 23)
4	logReg_cat_allcodes	0.655791	(59400, 38)
5	logReg_allnumcat_Encoding	0.967458	(59400, 38)
6	DecisionTreeClassifier_all	0.743586	(59400, 38)
7	RandomForestClassifier_all	0.807862	(59400, 38)
8	XgBoost_all	0.802441	(47520, 38)
```
