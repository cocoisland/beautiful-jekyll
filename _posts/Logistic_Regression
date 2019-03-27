# Predicting root cause factors with Logistic Regression.

The world does not exist in black and white, but we see and think in dualism. Logistic Regression is a data model that helps us examined the probability factors that make up our thinking process of making binary decisions.

Data cleanings for Logistic Regression are less restrictive because Logistic Regression has Regularization built-in which mitigates multi-collinearity overfitted problems. Including as many data features or dimensions into the regression, will help the model improves its prediction accuracy without increasing the residual errors risk of high collinearity overfitting problems.

![](https://cocoisland.github.io/img/logistic_data_prep.png)

Logistic Regression works with two or more y-label training value. The model automatically splits the prediction probability into the number of y-label in the training data. Higher number of y-label prediction probabilities decrease model score. Model score correlates predicted y-value accuracy with respect to actual true y-value.

The feature X-values can vary unevenly from extreme large to very small value. These data value extremes not only affect the model accuracy, it causes difficulties interpretting probability readings. MinMax_scale from sklearn helps scale the data into the range of [0,1], which improve the model accuracy and human probability readings.

![](https://cocoisland.github.io/img/logistic_score.png)

For each row observation, Logistic Regression calculates a coefficient for each x-feature in the row observation. The set of coefficients dot.product with x-feature values plus the model Intercept, produce the predicted y-label value. The larger a positive coefficient is, the bigger influence the coefficient has on the underlying probability ratio of the model to produce prediction with higher probability towards a One.

For example, if an income y-label has two outputs, ('<=50K','>50K'), then each positively increment of x-value multiplying with a large coefficient capital-gain, will positively affect the underlying probability ratio of the model towards 1, to produce a positively probability resulting an '>50K' y-label output. Conversely a negatively decrement of x-value coupling with large coefficient, will negatively decrease the probability ratio of the model to zero, to produce a '<=50K' y-label output.

Predictions of a likely outcome can be made based on the value of the coefficient. Visually a positively large coefficients can be seen to have positive influence on outcome that sit on the positive scale of the model prediction probability range, eg (large positive capital gain results in >50K income). Negatively large coefficients are seen to have negative influenced outcome, eg (large negative capital gain results in <=50K income)>

![](https://cocoisland.github.io/img/logistic_coef.png)

To test the validity of large coefficient influence on the model to produce a likely outcome, setup testcase which enables the target coefficient and disable the rest.

![](https://cocoisland.github.io/img/logistic_test.png)

Logistic Regression is robust, as it can take in datasets with various imperfections and perform reasonably well. It is flexible, as it can be used in many different settings from root cause predictions, survival analysis to neural network computations and more. At its core, it is a straight forward mathematical algorithm which work elegantly.
