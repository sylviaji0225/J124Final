# Surge in Accidental Drug Related Deaths in Connecticut from 2012 to 2022
## By Sylvia Ji
### Data Analysis
**Download**:[Accidental Drug Related Deaths 2012-2022](https://catalog.data.gov/dataset/accidental-drug-related-deaths-2012-2018),
upload it to Google Drive, and open it with Google Sheets. 

**Question1**
_Which age group has the most death? Which race has the most death percentage? What is the gender distribution of the dead?_

Answer: 30～39, White people 85.44%, Male 74.12%
1. Create a new Age group column to the right of the Age column
2. input =FLOOR(C2, 10) & "-" & FLOOR(C2, 10) + 9
3. Accept the suggestion that this column all use a similar formula to automatically generate age groups
![1.1](https://github.com/sylviaji0225/J124Final/raw/main/question1%20screenshot%201.png)
* New pivot table, pull the age group into the column, value, summarize by COUNTA of age group, and according to the value of the descending sorting

![1.2](https://github.com/sylviaji0225/J124Final/blob/main/question1%20screenshot2.png)

* Create the pivot table in the same way as above, do something similar to age group for Race, filter to remove blank, show as % of grand total
![1.3](https://github.com/sylviaji0225/J124Final/raw/main/question1%20screenshot3.png)

* Do the same thing with sex in the pivot table as I would with race.
![1.4](https://github.com/sylviaji0225/J124Final/raw/main/question1%20screenshot4.png)


**Question2**
_How many people died each year during the decade? What is the rate of change in the number of deaths?_

Answer: as screenshot below
1. Adjusting the format of the date column by Format-Number-Date in the bar
2. Create a new column year to the right of date
3. In C2, enter =LEFT(A2, 4) meaning to keep the first four characters corresponding to column A (year)
4. Accepted recommendation to generate this column "year"
5. Create a new pivot table and put Year in the rows and values(checked by filter-year, no blanks found)
6. in the pivot table new column C Rate of change from the previous year, using the function = (B3-B2)/B2, and accept the proposal to generate the year-on-year rate of change, adjust the number of format, to generate the format of the %
![2](https://github.com/sylviaji0225/J124Final/blob/main/question2.png)
  
**Question3**
_Which three drugs are most common in the analysis of the body of the deceased?_

Answer: Fentanyl、Cocain、Heroin
1. Create a pivot table
2. This form is marked in such a way that if the drug is detected in the body of the deceased, it will be marked Y. Otherwise, it will not be filled out.
3. Pull the column for all medications one by one into the VALUE column and select COUNTA
4. Add Filter to the value column, sort by z-a
![3](https://github.com/sylviaji0225/J124Final/blob/main/question3%20screenshot.png)
  
**Question4**
_What is the regional distribution of the death?_

Answer: as screenshot below
1. create a vew pivot table
2. rows: death county
3. values: death couty, summarize by COUNTA, filter blanks, show as default
![4](https://github.com/sylviaji0225/J124Final/blob/main/question4%20screenshot.png)

**Question5**
_Are drug overdose-related accidental deaths more frequent during certain seasons of the year?_

Answer:Doesn't seem to matter much.
1. Create a new column to the right of year named "season"
2. input =IF(OR(MONTH(A2)=12, MONTH(A2)=1, MONTH(A2)=2), "winter", IF(OR(MONTH(A2)=3, MONTH(A2)=4, MONTH(A2)=5), "spring", IF(OR(MONTH(A2)=6, MONTH(A2)=7, MONTH(A2)=8), "summer",IF(OR(MONTH(A2)=9, MONTH(A2)=10, MONTH(A2)=11),  "fall")))
3. Acceptance of the suggestion to generate a season column
4. create a new pivot table as what I did befor
![5.1](https://github.com/sylviaji0225/J124Final/blob/main/question5%20screenshot1.png)

**Question6**
_What is the youngest and oldest age of the deceased?Is there a significant change in the average or median age of the deceased from year to year?_

Answer: Minimum is 13，the change is not obvious
* Add filter, sort by age from z-a
![6.1](https://github.com/sylviaji0225/J124Final/blob/main/question6%20screenshot1.png)
1. create new pivot table
2. Row:Year, Values: Average of age，Filter：delete blanks
3. input=STDEVP(B2:B12)
![6.2](https://github.com/sylviaji0225/J124Final/blob/main/question6%20screenshot2.png)
4. the same with median of age
![6.3](https://github.com/sylviaji0225/J124Final/blob/main/question6%20screenshot3.png)

**Question7**
_How many minors die each year?What about in total?_

Answer: as screenshot below, 241 in total

1. create a new pivot table
2. Rows:Year Values:CountA of Year, Filters: age 13~20
![7](https://github.com/sylviaji0225/J124Final/blob/main/q6%20screenshot.png)
### Story pitch
A new report published early July by the Centers for Disease Control and Prevention looked at mortality data from the National Vital Statistics System between 2011 and 2021. It suggests that drug overdose deaths involving both cocaine and opioids have spiked over the last decade.

In the state of Connecticut, a parallel situation unfolds. Following the investigation by the Office of the Chief Medical Examiner, the state government has compiled data spanning from 2012 to 2022, encompassing cases of accidental deaths due to drug overdose. Throughout this period, the count of accidental deaths linked to drug overdose experiences an almost annual surge, albeit with a somewhat decelerated pace since 2017. Strikingly, the tally of fatalities in 2022 stands at approximately fourfold of that in 2012.

These tragic events find concentration within counties such as Hartford and New Haven. The majority of these fatality instances gravitate towards individuals aged 30 and above. Over a span of a decade, an alarming count of 141 minors (below 21 years of age) have tragically succumbed due to drug abuse. As nbcnews previously reported, a 13-year-old died days after a suspected fentanyl overdose at a Connecticut middle school in 2022. 

Specific drug detection data underscores that Fentanyl (an opioid), cocaine, and heroin claim the top three slots for highest detected substance concentrations within the deceased bodies. This array of data poignantly underscores the grave impact of drug abuse within the state.

### Data Visualization
![*_Accident Drug Related Death 2012-2022_*](https://github.com/sylviaji0225/J124Final/blob/main/column%20chart.png)
![map](https://github.com/sylviaji0225/J124Final/blob/main/map.png)
### Sourcing
**Aim:**
The information above is primarily derived from an analysis of the dataset, from which it can be observed that there is a rising trend in accidental deaths caused by drug abuse. It also provides a rough depiction of the profile of the deceased individuals. However, there is still a significant amount of information that cannot be presented.In the formal report, I also want to introduce the following perspective: Why drug abuse is becoming more common in the United States? Is there any way to solve the problem? For what reason were these people exposed to these drugs? Additionaly, in the last year, the state has taken a lot of steps to address substance abuse, has it produced real results?

#### Potential Interview Contacts
_Nora D. Volkow, M.D._
* Director of the National Institute on Drug Abuse (NIDA) at the National Institutes of Health. NIDA is the world’s largest funder of scientific research on the health aspects of drug use and addiction.
* Email:Nora.Volkow@nyulangone.org
* I will conduct interviews to understand why people become addicted to these drugs and ask about solutions to the problem of substance abuse.
  
_Peter Canning_
* Peter Canning has been a paramedic in Hartford, Connecticut since January of 1995.His latest nonfiction book about the heroin epidemic, Killing Season: A Paramedic's Dispatches from the Frontlines of the Opioid Epidemic published by Johns Hopkins University Press was selected by Amazon as one of the ten best nonfiction books of April 2021.
* Email: canning@uchc.edu
* I will ask him about substance abuse stories he has seen in Connecticut and learn about the nonfiction he has written.
  
#### Additional Sources
[Opioids and Drug Overdose Prevention](https://portal.ct.gov/DPH/Health-Education-Management--Surveillance/The-Office-of-Injury-Prevention/Opioids-and-Prescription-Drug-Overdose-Prevention-Program)
* from:CT.gov/HomeDepartment of Public Health
* I will learn about the latest data and the latest preventative measures in the state of Connecticut

[NVSS-Drug Overdose Death](https://www.cdc.gov/nchs/nvss/drug-overdose-deaths.htm)
* from: Centers of Diseas Control and Prevention/National Center for Health Statistics
* It helps me to compare the conneticut's accident with all country



