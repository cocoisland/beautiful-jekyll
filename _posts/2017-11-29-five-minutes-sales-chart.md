### How to process a sales report data into a readable chart in 5 minutes.

Most sales data reports often contain many unknown feature columns which distract a person from the important relevant data. When a columned feature is recorded as unknown, it is usually recorded as such(i.e. unknown) because it is deemed irrelevant by the person who first recorded the data.

A bare minimum, but meaningful sales report chart, has to show sales over times or sales over territory location or category. Sales number can be combined, accumulated, sum or whatever ways deemed appropriate, but they are grouped and categorized over time series period or discreet categories.

Hence the first rule in preparing a sales graph or chart, is to look for the sales number feature versus date times or sales number feature versus location or meaningful and related category.

Common mistake made when preparing sales data report are, people often by instinct started out using pandas library plot or seaborn library plot, to plot all columned features, in an futile attempt to make sense out of any relationship between unknown column features. 

For example

  ***df = pandas.read_csv( sales_url)***

 ***df.plot()***

or

  ***seaborn.plot(data=df)***

This exercise will only guarantee to fail in futile attempt to gain any new insight into unknown relationship between unknown columned features.

Instead of plotting all columned features including unknown features and known features, it will be more efficient to extract only relevant known features from all the columned features.

First, read any instructions that come with the data report. Any known columned features that the data preparer knowingly recorded, is relevant to any person who subsequently read and process the data preparer data report. In other words, the data preparer instructions can be deemed as the first data cleaning filtering by instructing the reader to ignore unknown columned features and only start working on known columned features.

To start identifying known features from the dataset with known and unknown features, run the describe command with an include all option. 

 ***df.describe( include='all')***

This option outputs all numerical feature values and object feature values together in one output, which enable the person to quickly identify which relevant features are of type numerical and type object. This identification is needed to decide which relevant features to be chosen to plot line graph or bar chart later on.

To plot line, all feature data has to be of type numerical. Any feature object type, will cause the line plot library to fail. A line graph needs a common meaningful time series or chronological index axis. If the sales report data has no common meaningful time series or chronological column or row to be made into index axis, then a line graph will be meaningless to be plotted because any natural order of meaningful data needs to be evolved comparing to a time series or chronological order. Without any natural order, the plotted data will appear as random data point in a graph.

When relevant sales report data contains discreet categorical value, it makes sense to plot bar chart. However to plot bar chart without any data structured filtering, it will easily overwhelm the bar chart plot. Basic data structured filtering usually starts with grouping, summing and sorting the data before attempting any bar chart plotting.

To sort out sales numbers that are derived from Yes offered from No offered.

  ***df_yes = df[ df['offered']=='Yes']***
  
To get sales earned from California only.

 ***CA_sales = dfyes.loc[ df_yes['state'] == 'CA', 'sales' ].sum()***
  
To group sales earned by individual states.

  ***state_sales = df_yes.groupby('state')['sales'].sum()***
  
To sort the states with the highest sales value.

 ***top_state_sales = state_sales.sort_values(ascending=False)***
  
To limit the top 5 state with highest sales value.

 ***top_5state = top_state.head(5)***
  
To bar chart 5 states with highest sales value.

  ***top_5state.plot(kind='bar')***

Following these few simple rules and steps, an initial meaningful sale line graph or categorical bar chart can be setup quick. Often  this initial sales line graphor categorical bar chart, will be able to convey all the essential relevant sales data information the person needed.


