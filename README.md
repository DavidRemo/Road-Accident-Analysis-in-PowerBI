# Road Accident Analysis in Power BI

I performed a diagnostic and prescriptive analysis on a Road Accident Dataset, to find out why road accidents happened in 2021/22 and what should be done to reduce the occurrence of accidents and it’s casualties, I do believe these insights drawn from my sample analysis can be used to infer on reduction of road accidents and aid the stake holders in decision making in regards to all road users.

## SOFTWARES USED
* Microsoft Excel
* Microsoft Power BI


## Problem Statement:
In this project I created a dashboard in Power BI for Road Accidents Analysis.

## Project Steps
•	Requirement gathering <br/>
•	Stakeholders in project <br/>
•	Raw data overview <br/>
•	Connecting data with Power BI <br/>
•	Data cleaning <br/>
•	Data processing <br/>
•	Data modelling <br/>
•	Data visualization/ Charts design <br/>
•	Report/ Dashboard <br/>
•	Insights <br/>


## Requirements
Client wants to create a Road Accident Dashboard for the year 2021 and 2022 so that they can have insights on the below requirements:
1. Primary KPI – Total casualties and Total Accident values for CY (current year) and YoY (year on year) growth.
2. Primary KPIs – Total casualties by accident severity for current year and YoY growth.
3. Secondary KPIs – Total casualties with respect to vehicle type for current year.
4. Monthly trend showing comparison of casualties for current year and previous year.
5. Casualties by road type for current year.
6. Current year casualties by area/ location & by day/night.
7. Total casualties and total accidents by location.


## Stakeholders
•	Ministry of Transport <br/>
•	Road Transport Department <br/>
•	Police Force <br/>
•	Emergency Services Department <br/>
•	Road Safety corps <br/>
•	Transport Operators <br/>
•	Traffic Management Agencies <br/>
•	Public <br/>
•	Media <br/>

## Datasource:
The dataset used in this project is about road accident casualties in UK in year 2021 and 2022.
* [Road Accidents Dataset](https://docs.google.com/spreadsheets/d/13Oxgq7VZtXqAKtVR4Y9eiQ3_8Jtrb84CfDx7KPhu6S0/edit?usp=sharing) containing 21 columns and 307,973 rows, with a total of 6,467,434 records of observation.

## Power BI Functionalities
•	How to connect to raw data/ flat file <br/>
•	Data cleaning in Power Query <br/>
•	Data processing <br/>
•	Time intelligence function/ calendar date table in Power BI <br/>
•	Data modelling (relationship between multiple tables) <br/>
•	YTD (year to data) and YoY (year on year) Growth calculations using DAX <br/>
•	KPI and advanced KPI generations <br/> 
•	Creating custom columns and measures in the reports <br/>
•	Importing images <br/>
•	Creating different charts and generating insights <br/>
•	Export the report to users <br/>


### Data cleaning
Used the Power Query Editor for data cleaning.  <br/>
For example, under "Accident_Severity" column, replaced “Fetal” with “Fatal”.


### Time intelligence function/ calendar date table in Power BI
#### Created a Calendar table:
<!--- Used the accident date to create a function in calendar such that the table picks the earliest date to the latest accident dates. ---> <br/>
Calendar = CALENDAR(MIN(Data[Accident Date]),MAX(Data[Accident Date]))
#### Extracted year from the calendar table:
Year = YEAR('Calendar'[Date])
#### Extracted month from the calendar table:
Month = FORMAT('Calendar'[Date],"mmm")


### Data modelling
Created a Many to One (*:1) relationship between the Data table and the Calendar table by connecting the “Accident Date” in the Data table to “Date” in the Calendar table. <br/>

That is, the Accident date can have many values whereas, the Calendar’s Date will have a single value. <br/>
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/dda2a5d8-85c1-4b2d-b98c-1bde2640c090) <br/>


### Data Visualization and Dashboard Building
#### Determine the Total Casualties
Current Year (CY) casualties: <br/>
CY Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]),'Calendar'[Date]) <br/>

Previous Year (PY) Casualties<br/>
PY Casualties = CALCULATE(SUM(Data[Number_of_Casualties]),SAMEPERIODLASTYEAR('Calendar'[Date]))<br/>

Year on Year (YoY) Growth <br/>
YoY Casualties = ([CY Casualties]-[PY Casualties])/[PY Casualties]

![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/a0c22045-028b-462b-96f9-1e32a01de6a1) <br/>

##### Insight:
As with respect to last year, the current year casualties/ number of accidents have reduced by almost 12%. <br/>

#### Determine the Total Accidents
Current Year Accidents <br/>
CY Accidents = TOTALYTD(COUNT(Data[Accident_Index]),'Calendar'[Date]) <br/>

Previous Year Accidents <br/>
PY Accidents = CALCULATE(COUNT(Data[Accident_Index]),SAMEPERIODLASTYEAR('Calendar'[Date])) <br/>

Year on Year Accidents <br/>
YoY Accidents = ([CY Accidents]-[PY Accidents])/[PY Accidents] <br/>
 
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/dfcffa1b-f1da-4349-b990-00bdecf7e514) <br/>

##### Insight: 
As with respect to last year, the total accidents have decreased by almost 12%. <br/>

#### Determine Total casualties by accident severity for current year(CY) and year on year (YoY) growth
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/8131b8c1-6a12-4c6a-8df2-50d51314709c) <br/>
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/e8ed2adb-3d54-4dd3-8695-83ef4869cda6) <br/>
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/a1dd8004-e947-44ac-a05c-96b4b646d7e6) <br/>

##### Insight: 
Fatal casualties are around 3,000, Serious casualties are around 27,000, whereas slight casualties are around 165,000. <br/>
As from last year, the fatal accidents have decreased by 33%, serious accidents have decreased by 16%, while slight accidents have decreased by 10%. <br/>
This is as good sign as accidents have reduced.<br/>

#### Total casualties with respect to vehicle type for current year
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/8586fe80-71ee-478e-b47d-30c850d0f240) <br/>

##### Insight: 
Car vehicle type contributes to the highest number of accidents. Therefore, the casualties are very high. <br/>
With this, four wheelers should be driven properly. In addition, there should be norms and regulations for four wheelers in such a way that the number of accidents can reduce. <br/>

#### Monthly trend showing comparison of casualties for current year and previous year
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/a50d44c1-040f-4581-a99c-7208c28829f4) <br/>

#### Current year casualties by area/ location & by day/night
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/7c1d93e2-b4f0-4071-bbd8-f47b57b08e9e) <br/>
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/291faaed-c76d-4191-ac12-0a30b813210d) <br/>
#### Casualties by Road Type
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/3b69ec93-a8cd-4783-abae-aa4803109b7a) <br/>

##### Insight: 
Urban areas experience the highest number of accidents as compared to rural areas. Therefore, the government needs to focus on urban areas when putting measures that will reduce road accidents. <br/>
Similarly, most accidents occur during the day as compared to when its dark. Reason being, many people drive during the day due to a buzz of activities, hence the chances of accidents happening during the day are higher. <br/>
Single carriage-way roads have caused over 70% of accidents. In light of this, the government and other bodies need to take action in expanding the roads with single carriage to double lane. <br/>

#### Total casualties and total accidents by location
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/17eeea2d-3602-4e65-bb93-f213591c6f00) <br/>


### Dashboard Visualization
![image](https://github.com/DavidRemo/Road-Accident-Analysis-in-PowerBI/assets/68180517/a05ab174-5e73-4ad8-b58c-3a5d3e85da76) <br/>


## Summary of Findings:
### Conclusion

Summarily, more road accident casualties were recorded in 2021 than 2022. More fatal, serious and slight casualties happened in 2021 than 2022, fatal casualties occurred more on Saturdays by cars. <br/>

Higher casualties were recorded to have happened on dry surface areas while least on icy/snowy surface areas, though more casualties happened on ice surface in 2022 compare to 2021. <br/>

Greater number of road accident casualties occurred in urban regions during daylight on single carriageway road type. Least road casualties were caused by Agric vehicles, days of the week with less casualties are Monday (2021) and Wednesday (2022). <br/>

### Insights

From my diagnostic analysis the following were observed: <br/>

•	Daylight has more casualties as more vehicles tend to go out during the day than in the dark.<br/>

•	Due to urbanization, urban regions tend to have more road accident casualties.<br/>

•	Cars cause more casualties because it is the most common means of road transportation.<br/>

•	Agricultural vehicles cause less road accident casualties because they are seldom used on roads and mostly used in agricultural environments like farm.<br/>

•	Hypothetically, people go out less during snowy weather, meaning fewer vehicles are used creating lesser road accident casualties compared to when the road is dried.<br/>

#### From my prescriptive analysis the following will recommended to be taken into consideration:<br/>

•	Less or no single carriageway road types are constructed, as they cause very high road accident casualty.<br/>

•	More lights are lit up in the dark to reduce more of the road casualties in the dark.<br/>


