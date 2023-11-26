
# Investigating links between crime and grocery prices
It has been widely reported that shoplifting incidents have increased at an alarming pace amid the rising cost of living<sup>[1](https://news.sky.com/story/shoplifting-up-25-in-the-past-year-12987599)</sup> <sup>[2](https://www.theguardian.com/uk-news/2023/sep/15/its-organised-looting-uk-in-grip-of-a-shoplifting-epidemic-say-store-owners)</sup> 
resulting in a government response earlier this year.<sup>[3](https://www.gov.uk/government/news/action-plan-to-tackle-shoplifting-launched)</sup>
This project uses grocery price data from https://www.kaggle.com/datasets/ziedzen/uk-grocery-retailer-sales-and-pricing-analysis and crime data from https://data.police.uk/data/archive/ to explore possible relationships between fluctuiations in grocery prices and incidents of crime, in particular shoplifting.
## Date Compatibility Issues and Fix
Crime data is reported on a month-by-month basis, however the grocery price data is dated using a year and a week number. This creates a number of issues, primarily that the data needs to be processed to line up the corresponding staistics, and additionally that an entry in the grocery data may correspond to multiple entries in the crime data; for example, if a week starts in may but goes into june, that record does not natrually correspond to any monthly crime statistic.
We fix this issue by creating two functions; **MonthFromWeek()**, which takes as input a year and a number and outputs the month that numbered week falls in. The issue of overlapping weeks is addressed by employing the following convention: a week is said to be in the same month and year as its Monday. The second function, **toDate()**, simply serves to transform the output of MonthFromWeek() into a datetime object.\
![Figure 1](https://github.com/KacperRawicki/delete-this/blob/main/Direct%20comparison.png)
![Figure 2](https://github.com/KacperRawicki/delete-this/blob/main/Adjusted%20Comparison.png)
## Initial Comparison
An initial standardised comparison reveals an unusual spike in the count of shoplifting for the month of may. An extended plot of the data shows this spike reocurring in previous years. There are a number of posible causes for this anomaly, including human error or administrative delays, and the May data will therefore be omitted in this analysis. Additionally, a time lag of one month will be applied to the mean price, which has been found to result ina  stronger correlation.
figure
figure
## Secondary Comparison
The standardized figures show signs of correlation. Removing the date variable, we can see an apprent weak correlation. After a permutation spearman rank test, we see a correlation of **0.721** with a  pvalue of **0.0135** < 0.05, indicating evidence for a medium-strong correlation.
## Further Comparisons
Comparing the mean price with overall crime, we note a weaker correlation indicating insufficient evidence for an increase in criminal activity as a result of increased mean grocery prices. The correlation for this comparison following a permutation spearman rank test was **0.200**, with a p value of **0.296** > 0.05
## Conclusions
This work concludes with presenting statistically significant evidence for a strong link between UK-wide reports of shoplifting and rises in mean grocery prices (p = 0.0135). There is insufficient evidence to conclude, however, that rises in grocery prices result in an overall increase in crime (p =0.296). Additionally, it should be stressed that this conclusion is based on data from years 2018/19, and it cannot account for changes in behaviour following the cutoff point, in particular the impact of the COVID-19 pandemic.
