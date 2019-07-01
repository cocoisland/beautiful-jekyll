---
title: History of Bees Colony Collapse and Pesticides Usages in US.
subtitle: I built this in hope to bring awareness to bees colony collapse plight.
image: /img/beescolony/bees.jpg
---
Credit to ["Bees colony populations statistic data"](https://data.world/siyeh/us-bee-stats-by-state/activity) collected by a non-profit sporadic bees hive owners throughout United States over the years. I built on this corner-stone datasets into this Dash Plotly application. To expand on this bees colony populations datasets, I scoured the US Department of Agriculture  databases and Kaggle.com for farm pesticide application by States throughout the years. Piecing the three different datasets have been a balancing act since the different datasets were recorded by different timeline, from months, quarter to annual.

["Checkout the live Bees Colony Collapse and Pesticides Usage in US application here"](https://beescolony.herokuapp.com "Live on Heroku")

Worked with Google colab workbook, using python and pandas library, the datasets were downloaded, cleaned, joined into actionable dataframe which to feed into Dash Plotly library. I choosed Dash Plotly library to build this Bees Colony application because Dash Plotly enabled a high responsive and interactive performance. Equally important was Dash Plotly enabled me to integrate three different plots onto one screen and with high interactivities between all the plots. Changing a States, year timeline or pesticides used during the years or states, will automatically update all related Bees colony graph and vice versa. 

["Click here for Full working code on GitHub"](https://github.com/cocoisland/python_apps/bees)
