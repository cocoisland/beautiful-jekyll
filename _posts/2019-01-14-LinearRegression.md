Humans like to think and see in straight lines, but the world is curve.

Linear Regression is usually the first data model that everyone learned when they studied data science. The data model is easy to conceptualize, explain and understand by everyone because it is an extension of linear geometry mathematical functions that we all have learnt from school. Input x-values output the y-value and magically predict the next y-value in a straight extrapolating line.

Scikit library contains ready to use powerful data model algorithms. The data models are essentially functions performing gradient descent computations reducing the cost functions. A few lines of code, a magical algorithm able to predict future value is born.

![](https://cocoisland.github.io/img/regplot.png) ![](https://cocoisland.github.io/img/linearReg.png)

Even though we now have the formula to extrapolate y-value into future possible predictions based on incoming x-values data points, the y-value output never accurately predict future true output most of the time. 

In nature of the universe, natural occurrings always fall on shape of a normal bell curve distributions. A single line or sheet of prediction plane slicing through a cloud space of bell curve distribution of possible true y-value existence, will only be able to predict those true y-values that exist in the path of predictions.

Plotting seaborn residual graph, the thickest bell curve distribution shows the narrowest regression errors as the line of prediction slicing through the cloud. Conversely in region where fewer true y-values in existence, the line prediction encounters wider uncertainty as otherwise known as wider regression error.

Therefore Linear Regression should only be used in situation where the cloud of true y-values exist in a narrow relatively straight band of line projection. If this requirement is met, then further techniques can be used to optimize the Linear Regression model to best fit that narrow band of straight line true y-values.

From given datasets, after identifying a feature as y-value target, the remaining features would be chosen based on assumed  relationships that have high impact on y-value target. To proven the accuracy of that initial assumption, statsmodel library is used to examine the impact relationship of chosen x-value features on the output y-value target.

Statsmodel library is a powerful library examining many angle of relationships. But for the purpose of justifying selection of x-features for optimum y-target output, we are mostly concern with the standard error of x-feature coefficients and multi-collinearity. 

![](https://cocoisland.github.io/img/statsmodel.png) ![](https://cocoisland.github.io/img/statsmodel_code.png)

High coefficient standard errors mean the predicted y-value output by Linear Regression model has higher uncertainty as it passes through the cloud of true y-value as demonstrated in the regression graph above. 

Removing outliers in training dataset, help Linear Regression model to direct x-value coefficent to better predict y-value output through denser cloud of true y-value.
![](https://cocoisland.github.io/img/outlier.png)

However the most effective ways to reduce high standard errors, are to logarithmically transform the y-value. Logarithmic transformation has the effect of smoothing out  uneven y-value into a relatively smooth normal distribution. Thing in nature exists harmoniously in the shape of normal distribution. Hence logarithmically transforming unevenly y-value into denser cloud of smooth normal distribution shape, greatly reduce the uncertainty encountered by the Linear Regression model as it projects its prediction in a straight line through the cloud of true y-values.
![](https://cocoisland.github.io/img/logy_statsmodel.png) ![](https://cocoisland.github.io/img/logy_code.png)

High multi-collinearity means the data model is overfitting the y-test with y-train value. It also makes the data model insensitive to other relevant x-value changes. Statsmodel library effectively detects any high multi-collinearity in selection of x-value features if exist. 

To remove multi-collinearity, use Variance-Inflation-Factor functions to identify offending x-value features.

![](https://cocoisland.github.io/img/vifout.png)





Linear Regression limitation.
Linear Regression gives us magical power to extrapolate prediction projections in a straight line which empower our human mind to see the linear causality and effect. Just like any local TV weathermen would love to use Linear Regression model to easily explain and predict rain or no rain the next day and week due to incoming clouds, wind direction, pressure centers etc. But we all know predictions made in a straight line extrapolation, are seldom accurary. In short term prediction such as extrapolating into next day predictions, it may at best have about 50-60% accuracy. Long-term, the accuracy will further reduce by 50% and so on. There are always some unexpected independent variables in actual future occurring that differ from the Linear Regression equation predictions. Those unexpected independent variables could have been collected in the training and testing dataset, but they occur too infrequently to be significant to train-fit the Linear Regression model. Hence when they happen, they throw the prediction off. Considering a line or a plane of predictions sliding through a cloud of unexpected independent variables surrounding the line or plane, there will be a lot of errors or misses by any predictions.

People still love Linear Regression.
Human likes to think in clear-cut black and white mental pictures and Linear Regression straight lines and plane fit the need. Linear Regression is easy to understand, visualize and grasp by its audience. It operates comfortably in our mental construct of scientific linear causality and effect model. Outside of that comfort and familiar convenience, Linear Regression data scientist have to be mindful of the many curve and bends lurking hidden around all linear predictions.


