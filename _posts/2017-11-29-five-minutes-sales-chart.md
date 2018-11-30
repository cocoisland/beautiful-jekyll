### Bare essential Sales data reporting

When reading a sales report, the first thing a reader expects to find, is either a sales line graph or bar chart. Hence a bare essential sales data report should consist of line graph or bar chart only. Getting a line graph or bar chart up in the shortest time, often sufficiently serve the needs of the sales data.

Line graph shows action-by-action performance over time. Bar chart shows summarized results over specific categories. Category could be discreet region, sale items, campaign etc. 

To finish up a sales report satisfactorily,  Pie chart shows the total summary result.

First, avoid plotting all data blindly in hope of seeing correlation in data features. It will lead to distraction. Instead use Dataframe describe function to decide to plot line graph or bar chart. With option include=All, look for numerical data to plot line graph.  Categorical data are only for bar chart. 

```python
For example
Avoid
df = pandas.read_csv( sales_url)
df.plot()
or
seaborn.plot(data=df)

To choose plot line graph or bar chart
df.describe( include=’all’)
```

Any feature object type, will cause the line plot library to fail.  A line graph needs a common meaningful time series or chronological index axis.  Without any natural order, the plotted data will appear as random data point in a graph. 

Categorical data charts against sales data, gives meaning summarized sales result insight. To plot all categorical data on bar chart, could easily overwhelm a bar chart plot. Filter down the categorical data to top five or bottom five, to plot on bar chart convey a clearer insight.

```python
For example, raw data contains numerical sales and category state, but no time series data. The right sale report, is to plot bar chart.

Filter out data with no offered by extracting the Yes offered
df_yes = df[ df[‘offered’]==’Yes’]

Analyzing sales earned from California only.
CA_sales = dfyes.loc[ df_yes[‘state’] == ‘CA’, ‘sales’ ].sum()

Summarizing sales earned by individual states.
state_sales = df_yes.groupby(‘state’)[‘sales’].sum()

Sorting the states with the highest sales value at the top
top_state_sales = state_sales.sort_values(ascending=False)

Limiting the top 5 state with highest sales value.
top_5state = top_state.head(5)

Finally plot the bar chart 5 states with highest sales value.
top_5state.plot(kind=’bar’)
```

Following these few simple rules and steps, an initial meaningful sale line graph or categorical bar chart can be setup quick. Often this initial sales line graphor categorical bar chart, will be able to convey all the essential relevant sales data information the person needed.
