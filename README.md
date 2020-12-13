# Covid-19-Trends-and-Resource-Distribution-in-Maryland

## Background 
In 2020, the COVID-19 pandemic has spread across the United States. According to the Johns Hopkins University [Coronavirus Resource Center](https://coronavirus.jhu.edu/region/us/maryland), Maryland had 228,471 cases and 5,064 deaths as of December 12, 2020. The [Maryland Department of Health](https://coronavirus.maryland.gov) has taken action to address the COVID-19 pandemic, including expanding testing, increasing contract tracing, and sharing guidelines to mitigate the risk of contracting the virus. With the winter months looming ahead, however, the situation could worsen before improving. A critical factor in Maryland's recovery is the distribution of recently approved vaccines, but the question of how to distribute resources remains.

The [following graphic](https://coronavirus.jhu.edu/data/state-timeline/new-deaths/maryland/26) shows that Maryland's situation is getting worse in terms of cumulative deaths. It's interesting to note that despite newly implemented lockdown policies (orange lines), deaths continue to increase at an increasing rate. Thus, it is critical that Maryland's Department of Health understand what is causing these changes and who is most affected. 

![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Maryland%20COVID%20Deaths%20Timeline%20Graph.png) 

## Business Question
* How should Maryland distribute resources to support the most vulnerable groups to COVID-19?

## Data Question
* What are the predictors for total COVID-19 deaths and how do they influence outcomes?
* What do confirmed COVID-19 deaths in Maryland look like for different age groups, races, and genders? 
* Cluster Q

## Data
This analysis used datasets from [Maryland Open Data](https://opendata.maryland.gov). The program provides transparency about state trends to facilitate decision and policy-making.
* [Maryland's Confirmed COVID-19 Deaths By Age Distribution](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MD_COVID-19_-_Confirmed_Deaths_by_Age_Distribution.csv)
* [Maryland's Confirmed COVID-19 Deaths by Race](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MD_COVID-19_-_Confirmed_Deaths_by_Race_and_Ethnicity_Distribution.csv)
* [Maryland's Confirmed COVID-19 Deaths by Gender](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MD_COVID-19_-_Confirmed_Deaths_by_Gender_Distribution.csv)
* [Maryland's Confirmed COVID-19 Deaths by Date](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MDC19_DeathsbyDate.csv)
* [Maryland's Confirmed COVID-19 Hospitalizations by Date](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MDC19_HospitalizationsByDate.csv)
* [Maryland's Confirmed COVID-19 Testing by Date](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MDC19_TestingbyDate.csv)
* [Maryland's Confirmed COVID-19 Total Cases Statewide by Date](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MDCOVID19_TotalCasesStatewide.csv)
* [Maryland's Confirmed COVID-19 Total Hospitalizations Statewide by Date](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Data/MD_COVID-19_-_Total_Hospitalizations.csv)

## Data Answer
### Multiple Linear Regression - Understanding Predictors and Problem Scope
![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Regression%20Statistics.png)

The multiple linear regression shows statistically significant predictors for cumulative COVID-19 deaths in Maryland:
  * Predictors (excl. Intercept): Daily Total Tests, Total Cases, Total Hospitalizations, Rolling Average % Positive, Total Cases > Age 60
  * Equation: Total Deaths = 155.6687532 + 0.001196659(Daily Total Tests) - 0.023330713(Total Cases) + 0.353647773(Total Hospitalizations) - 20.64741629(Rolling Average % Positive) + 0.042615389(Total Cases Age > 60)

An interesting observation is that Total Cumulative Deaths isinversely related to Rolling Average % Positive and Total Cases. Meaning that the increases in deaths are not explained by an increase in absolute or percentage positive cases. The biggest drivers for deaths are Hospitalizations and Cases Age > 60. Meaning that the impact of 1) preventing hospitalizations (severe symptom development) 2) quality of care in hospitals (capacity, treatment efficacy) should be studied further.
								
![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Total%20Deaths%20vs.%20Days%20Since%20Start%20Prediction%20Fit.png) 

The fitting model suggests that cumulative COVID-19 deaths in Maryland follows a 'poly3' pattern:
  * Fitting Equation: Cumulative Deaths = 0.0007(x)^3 - 0.3446(x)^2 + 63.727(x) - 489.89, where x = # of days since 3/29/2020
  * R-Square Value: 0.9938
  * Prediction for 12/30/2020: 5,566 total cumulative deaths 
  
Note that although we can use this poly3 fit equation to predict the total cumulative deaths on a certain day, it is likely that the data will have to be refitted once new data and events arise (vaccine, policy changes, maks-wearing). 
  
### Rolling Averages - Understanding Trends [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/10ZE6mmDmrSa-LYPKPn0hQOVz1uDfzyC-?usp=sharing)
![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Maryland%20COVID%20Rolling%20Averages.png)

The rolling averages graphs show that 


### Pivot Tables and Pivot Charts - Understanding Who is Affected

![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Maryland%20COVID-19%20Cumulative%20Confirmed%20Deaths%20By%20Age%20Group.png)

The graph demonstrates that confirmed deaths are higher for older individuals, and the gap has widened throughout the course of the pandemic. In November, the confirmed deaths for the 80+, 70-79, and 60-69 age groups were approximately 2,100, 1,100, and 700 respectively. In contrast, the younger age groups had confirmed deaths below 500. The data shows that older individuals are several times as likely to die from COVID-19. 

![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Percentage%20of%20Maryland%20COVID-19%20Confirmed%20Deaths%20By%20Age%20in%20November%202020.png)

The [U.S. Census Bureau](https://www.census.gov/quickfacts/MD) estimates that individuals over 65 account for only 15.9% of the population, but the pie chart shows that people above 60 represent 87% of Maryland's cumulative confirmed COVID-19 deaths. This demonstrates that older individuals are much more at risk from COVID-19. 

![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Maryland%20COVID-19%20Cumulative%20Confirmed%20Deaths%20By%20Gender.png)

The graph demonstrates that there are not major gender discrepancies in COVID-19 confirmed deaths. Males have slightly higher confirmed deaths than females, but the values are relatively similar. 

![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Maryland%20COVID-19%20Cumulative%20Confirmed%20Deaths%20By%20Race.png)

The graph illustrates the presence of racial discrepancies. In November, Whites and African Americans had around 2,000 confirmed deaths. Hispanics, Asians, and Other Races had below 500. 

![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/Percentage%20of%20Maryland%20COVID-19%20Confirmed%20Deaths%20By%20Race%20in%20November%202020.png)

The [U.S. Census Bureau](https://www.census.gov/quickfacts/MD) estimates that whites account for 58.5% of the population, African Americans for 31.10%, Hispanics for 10.6%, and Asians for 6.70% (hispanics may be double-counted in the data if they have reported being part of multiple races). When we analyze the pie chart, we see that African Americans and Hispanics account for larger percentages of COVID-19 confirmed deaths than their percentages of the total population would indicate, which means that they could be more at risk.

## Business Answer
With the COVID-19 pandemic escalating in severity, the distribution of resources, especially vaccines, to combat the virus is becoming increasingly important. State governments should consider protecting the most vulnerable populations first in order to prevent more deaths and spread. The data analysis about Maryland's COVID-19 confirmed deaths demonstrates that the elderly and certain racial minorities are more at risk.
[University of Washington Model](https://covid19.healthdata.org/united-states-of-america/maryland?view=total-deaths&tab=trend)
![alt text](https://github.com/matthewprk/covid-19-trends-in-maryland-/blob/main/Screenshots%20of%20Data%20Answer/UW%20Model%20COVID%20Deaths%20Scenarios.png)


