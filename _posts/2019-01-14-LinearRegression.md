Humans like to think and see in straight lines, but the world is curve.

Linear Regression is usually the first data model that everyone learned when they studied data science. The data model is easy to conceptualize, explain and understand by everyone because it is an extension of linear geometry mathematical functions that we all have learnt from school. Input x-values output the y-value magically predict the next y-value in a straight extrapolating line.

Scikit library contains ready to use powerful data model algorithms. A few lines of code, a magical algorithm able to predict future value is born.

from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X, y)
m_hat = model.coef_[0]
b_hat = model.intercept_
y_hat = [m_hat*x + b_hat for x in X]
seaborn.regplot(x, y, data=df, scatter_kws={'alpha=0.3'})
or
beta_0 = model_intercept_
beta_i = model.coef_
y = beta_0 + beta_i[0]*x_1 + beta_i[1]*x_2

![](https://cocoisland.github.io/img/regplot.png) ![](https://cocoisland.github.io/img/linearReg.png)


A | B
- | -
![Seaborn regplot](https://cocoisland.github.io/img/regplot.png) | ![Linear Regression](https://cocoisland.github.io/img/linearReg.png)



Even though we now have the formula to extrapolate y-value into future possible predictions based on incoming x-values data points, we will find that the y-value output will never accurately predict future true output most of the time. Unless the nature of future true value y-value output consistently exists along the projected straight line path as extrapolated by the formula, the true y-value will not be seen by the straight line prediction. 

Given the nature of the universe where natural occurrings always fall on shape of a normal bell curve distributions, a single line or a sheet of plane prediction slicing through a cloud of bell curve distribution of possible true y-value existence will only be able to predict a thin slice of accurate predictions.

Doing the best we can under circumstance where if linear algrebra regression formula is all we have, we optimize the data model to capture as much true y-value as possible through the thickest section of the bell curve true y-value distributions.
The slice through the thickest bell curve distribution has the smallest residual errors encountered by the data model formula. The high density of true y-value data points exist in the thickest bell curve distribution guaranteed higher hit by the formula as it projects its prediction through the thick cloud of true y-value possibilities.

Using residualplot seaborn library, residual error can be seen thinnest on the graph where data points concentration is higher. Conversely residual error widen where data point concentration lowest.




A few lines of libraries and codes, would magically give us the ability to extrapolate target predictions into the future. After importing sklearn libraries, the dataset can be splitted into training data to train-fit and then test the model. The r2_score() gives us insight into relationship between independent-dependent and data input-output.
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression

X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=.5)
model.fit(X_train, Y_train)
Y_test_predicted = model.predict(X_test)
R2 = r2_score(Y_test, y_test_predict)

Linear Regression is loved by people because it is easy to visualize mathematically a best-fitting straight slanting line rising y-axis over x-axis in 2-dimensionally bivariate regression dataset clouds, or flat slanting plane rising z-axis over (x,y) plane in 3-dimensionally 2-variables regression dataset clouds.

graph and code in ax1 and ax2
fig = plt.figure(figsize=(10,8))
ax = fig.add_subplot(111, projection='3d')
ax.scatter(df.sqft_living, df.grade, df.price, c='red', alpha=0.3)

x1 = np.array(ax.get_xlim())
y1 = np.array(ax.get_ylim())
xx, yy = np.meshgrid(x1, y1)
zz = beta_i[0]*xx + beta_i[1]*yy + beta_0

#plot the plane
plt3d = plt.gca(projection='3d')

# add Opacity to plane
plt3d.plot_surface(xx, yy, zz, alpha=0.5)

Linear Regression limitation.
Linear Regression gives us magical power to extrapolate prediction projections in a straight line which empower our human mind to see the linear causality and effect. Just like any local TV weathermen would love to use Linear Regression model to easily explain and predict rain or no rain the next day and week due to incoming clouds, wind direction, pressure centers etc. But we all know predictions made in a straight line extrapolation, are seldom accurary. In short term prediction such as extrapolating into next day predictions, it may at best have about 50-60% accuracy. Long-term, the accuracy will further reduce by 50% and so on. There are always some unexpected independent variables in actual future occurring that differ from the Linear Regression equation predictions. Those unexpected independent variables could have been collected in the training and testing dataset, but they occur too infrequently to be significant to train-fit the Linear Regression model. Hence when they happen, they throw the prediction off. Considering a line or a plane of predictions sliding through a cloud of unexpected independent variables surrounding the line or plane, there will be a lot of errors or misses by any predictions.

People still love Linear Regression.
Human likes to think in clear-cut black and white mental pictures and Linear Regression straight lines and plane fit the need. Linear Regression is easy to understand, visualize and grasp by its audience. It operates comfortably in our mental construct of scientific linear causality and effect model. Outside of that comfort and familiar convenience, Linear Regression data scientist have to be mindful of the many curve and bends lurking hidden around all linear predictions.


