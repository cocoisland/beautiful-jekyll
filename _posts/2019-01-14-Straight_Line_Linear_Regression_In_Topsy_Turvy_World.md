## Humans like to think and see in straight lines, but the world is curve.

Linear Regression is usually the first data model that everyone learned when they studied data science. The data model is easy to conceptualize, explain and understand by everyone because it is an extension of linear geometry mathematical functions that we all have learnt from school. Input x-values output the y-value and magically predict the next y-value in a straight extrapolating line.

Scikit library contains ready to use powerful data model algorithms. The data models are functions performing gradient descent computations reducing the cost functions. A few lines of code, a magical data model to predict future value is born.

![](https://cocoisland.github.io/img/linearReg.png)

At the core of Regression data model, are the many names of cost function reductions, such as minimum square error, ordinary least square, sum of square error, loss functions, error functions. They are all a flavor of cost optimizer of gradient descent. Gradient descent is the algorithm for finding the minimum cost or error of the functions.

![](https://cocoisland.github.io/img/gradient_descent.png)

Even though we have the formula to extrapolate y-output label projections into future predictions based on incoming x-values observation data points, the y-output predictions seldom accurately predict future true occurrings most of the time. 

In nature of the universe, natural occurrings always fall on shape of a normal bell curve distributions. A single line or sheet of prediction plane slicing through a cloud space of bell curve distribution of possible true y-output predictions, will only be able to predict those true future occurings that exist in the straight path of predictions. This means most of the possible true occurrings that exist above and below the plane of predictions, will not be discovered.

### Missed bullmark prediction, what went wrong
Plotting seaborn regression graph, the thickest bell curve known y-label training output distribution shows the narrowest regression errors as the line of prediction slicing through the denser cloud.
 
![](https://cocoisland.github.io/img/regplot.png)

Conversely in region where fewer true known y-label values in existence, the line prediction encounters wider uncertainty as otherwise known as wider regression error. In nature, true occurences that occur above, below or around the y-prediction band projection, will not be accurately predicted or captured.



### Looking under the hood of Linear Regression prediction making
Statsmodel library is a powerful library examining many angle of feature column or dimensional relationships affecting the prediction output. Intuitively, the more dimension or factors affecting the output, the greater the uncertainty and the higher the regression errors will be.

For the purpose of choosing the most direct influential x-dimensional features impacting y-output prediction, we are mostly concerned with the standard error of x-dimensional feature coefficients and multi-collinearity. 

![](https://cocoisland.github.io/img/statsmodel.png) ![](https://cocoisland.github.io/img/statsmodel_code.png)

High coefficient standard errors of x-dimensional value features mean the predicted y-output prediction by Linear Regression model has higher uncertainty as it passes through the cloud of true y-output prediction as shown in the regression graph above. 

Removing outliers in training dataset, reduce data distraction which help Linear Regression model reduce its coefficient standard errors of x-dimensional features and eventually produce more accurate predictions.
![](https://cocoisland.github.io/img/outlier.png)

### Many ways to reduce regression errors, but most effective way, is to logarithmically transform y-label training output.
Logarithmic transformation has the effect of smoothing out uneven y-label training value into a relatively smooth normal distribution. Thing in nature exists harmoniously in the shape of normal distribution. Hence logarithmically transforming unevenly y-value into denser cloud of smooth normal distribution shape, greatly reduce the uncertainty encountered by the Linear Regression model as it projects its prediction in a straight line through the cloud of true y-values.
![](https://cocoisland.github.io/img/logy_statsmodel.png) ![](https://cocoisland.github.io/img/logy_code.png)

High multi-collinearity means the data model is overfitting the y-test with y-train value. It also makes the data model insensitive to other relevant x-value changes. Statsmodel library detects high multi-collinearity in x-value features if exist. 

To remove multi-collinearity, use Variance-Inflation-Factor functions to identify offending x-value features. X-value features identified by Variance-Inflation-Factor to have value over 10, should be dropped in order to reduce high inter-features correlation. Dropping all x-value features with high Variance-Inflation-Factor, will systematically tune the Linear Regression data model to best fitting its straight line or plane of predictions through the best possible true y-value distributions.

![](https://cocoisland.github.io/img/vifout.png)

### Conclusion
Linear Regression should be used in cases where we expect the true y-values distribution exist in narrow straight band of possibility. If this requirement is met, then the above techniques can be used to optimize the Linear Regression model to best fit that narrow band of straight line true possibility.



