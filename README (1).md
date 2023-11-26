
# Investigating links between crime and grocery prices
It has been widely reported that shoplifting incidents have increased at an alarming pace amid the rising cost of living 
This project uses grocery price data from https://www.kaggle.com/datasets/ziedzen/uk-grocery-retailer-sales-and-pricing-analysis and crime data from https://data.police.uk/data/archive/ to explore possible relationships between fluctuiations in grocery prices and incidents of crime, in particular shoplifting.
## Date Compatibility Issues and Fix
Crime data is reported on a month-by-month basis, however the grocery price data is dated using a year and a week number. This creates a number of issues, primarily that the data needs to be processed to line up the corresponding staistics, and additionally that an entry in the grocery data may correspond to multiple entries in the crime data; for example, if a week starts in may but goes into june, that record does not natrually correspond to any monthly crime staistic.
We fix this issue by creating two functions; **MonthFromWeek()**, which takes as input a year and a number and outputs the month that numbered week falls in. The issue of overlapping weeks is addressed by employing the following convention: a week is said to be in the same month and year as its Monday. The second function, **toDate()**, simply serves to transform the output of MonthFromWeek() into a datetime object.

test
![Some text here !!!](https://github.com/KacperRawicki/delete-this/blob/main/Initial%20Comparison.png)
