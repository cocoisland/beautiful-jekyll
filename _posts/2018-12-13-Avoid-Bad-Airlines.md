
## Can you avoid a bad Airline ?

[Major Airline Incidents data](https://github.com/fivethirtyeight/data/tree/master/airline-safety)

[Workbook on Github](https://github.com/cocoisland/DS-Unit-1-Sprint-4-Statistical-Tests-and-Experiments/blob/master/Airline_accident.ipynb)

Fear of flying is understandable because  air travelling put you in an uncontrollable situation. 
When air plane accident crashes,  it goes into headline news. Headline news solidified people suspicions into belief system. 
Eventually people think it makes good sense to avoid airline with bad fatal accidents. 

### Strategy 1: Avoid airline with high fatalities accidents.

![Headline Airline crashed](https://cocoisland.github.io/img/headline_crashed.png)

Comparing all bad news headline fatalities airlines during 1985-1999 with 2000-2014, the prior unfortunate airlines no longer had bad accidents. Instead a new set of prior no accident airlines, showed up as bad news headline fatalities airlines in 2000-2014 period. 
* Airline fatalities crashes are rare and non-recurring. 
* Rare accidents are unpredictable and random.

## Avoid accident prone Airlines?
If non-recurring accidents are random, then avoiding airlines with bad record of high accident incidents, make better sense.

### Strategy 2: Avoid bad airline with highest bad past accident records

![Airline accidents](https://cocoisland.github.io/img/airline_accidents.png)

From period 1985-1999 to 2000-2014, most of the prior top 56 major accident prone airlines 
showed up in the latter period. However upon closer examination, these major airlines shared a commonality which was servicing high traffic airports
* Top accident airlines commonality are major airline flown in and out of major busy airport.
* Higher rate of passengers travelled and flight flown, resulted in higher accident incidents rate.

These high accident incidents records did not indicate these busy airlines as accident prone, but a natural outcome of high traffic servicing airlines.

### Hence the need to normalize data in order to compare objectively
Combine the three measures of crash rates — incidents, fatal accidents and fatalities — into a single measure and call it as airline’s safety score. Calculate it as follows:
* subtract an airline’s crash rate from the average for all airlines. This gives safer airlines positive scores and less safe airlines negative scores.
* Multiply the result by the square root of the number of seat kilometers flown. This gives more credit to an airline that has achieved a strong safety record over a larger sample of flights.
* Standardize the score in each category to calculate how many standard deviations an airline is above or below the mean. Then average the scores from the three categories together. 
* This is the safety score.

### Strategy 3: Normalized accidents by airline traffic into Safety Index and compare.

![Negative Safety Index](https://cocoisland.github.io/img/negative_safety_index.png)

The above Safety Index chart showed airlines with most negative score measured over 30 years from 1998 - 2014.
Positive Safety Index indicates airlines with good safety performance. Negative Safety Index indicates airlines with more accient prone performance.

Normalizing all airline incidents, fatal accidents and fatalities from acccident against each airline seat and flight enabled a more objective comparison between airlines accidents and safety record. The Safety Index chart above filtered down airlines with the top most negative Safety Index score. It turned out most of the airlines with most negative Safety Index score, were airlines that we flown regularly without any concern of safety for the past 30 years. The airline with bad accidents that we heard in the news and avoided, did not have negative score near the bottom. So our fear and avoidance, was unfounded.

### Conclusion
It is easy to be misled by fear of airline accident especially when the fear is enforced by headline news. Next time when you look at headline news airline crashes, may be you would resist your temptation to rule out flying too quickly. Using Safety Index of airline incidents over a long period of time, would be a better guide to your decision making.
