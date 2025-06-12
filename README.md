# Excel Terror Attacks Project

## Introduction
This project interactively visualizes information about terror attacks around the world from 1970 to 2017. It was created to make this information accessible and visual, allowing users to explore, investigate, and identify trends related to terror attacks and terrorist groups worldwide.
There are three dashboards, each delving into a different level of depth on global terrorism.

### Dashboard 1
![](screenshots\dashboard1.jpg)
### Dashboard 2
![](screenshots\dashboard2.jpg)
### Dashboard 3
![](screenshots\dashboard3.jpg)

### Dashboard File
My final dashboard is in [project.xlsx](project.xlsx)

### Excel Skills Used
The following Excel skills were utilized for analysis:
* Charts
* Data Validation
* Formulas and Functions
* PivotTable

### Global Terrorism Database
The Global Terrorism Database (GTD) is an open-source database including information on terrorist attacks around the world from 1970 through 2017. The GTD includes systematic data on domestic as well as international terrorist incidents that have occurred during this time period and now includes more than 180,000 attacks. The database is maintained by researchers at the National Consortium for the Study of Terrorism and Responses to Terrorism (START), headquartered at the University of Maryland.

To view the database: [Click Here](https://www.kaggle.com/datasets/START-UMD/gtd/data)

## Cleaning the database
The original database contains 135 columns. I used Power Query to remove irrelevant columns, rename columns for better clarity, and reformat some of the values to better organize the information.

![](screenshots\powerquery.jpg)

## Dashboard 1 Build
![](screenshots\dashboard1.jpg)

1. I used a PivotTable created from the database.
The rows represent countries, and the values show the count of events.
Two slicers were added to allow the user to filter the information by region and by year or range of years.

![](screenshots\dashboard1_1.jpg)

2. The world map visualization doesn't support PivotTables, so I had to create a separate table to display the map.
The left column lists countries in alphabetical order, and the events count column pulls data from the PivotTable.
Since the PivotTable is filtered, I used a formula to return "NA" for countries that are currently filtered out.

``=LET(val, GETPIVOTDATA("Events Count", $B$4, "Country", D4), IF(ISNUMBER(val), val, NA()))``

![](screenshots\dashboard1_2.jpg)

3. The user can select a specific country to see the number of terror attacks, with region and year filters applied.
I created a data validation drop-down list for selecting the country, and the terror attacks count is pulled from the PivotTable based on the selected country.

`` =GETPIVOTDATA("Events Count", $A$4, "Country", $G$4)``

4. The "Top 10" chart pulls the data from the PivotTable, sorts by descending order and shows the top 10 countries with highest values.

``=TAKE(SORT(FILTER(Terror_Around_the_World_Table!$A$4:$B$208, Terror_Around_the_World_Table!$B$4:$B$208<>0), 2, -1), 10)``

## Dashboard 2 Build
![](screenshots\dashboard2.jpg)

1. I used a PivotTable created from the database.
The rows represent terror groups, the columns represent attack types, and the values show the count of events. Top 5 filter is applied to the PivotTable.
Two slicers were added to allow the user to filter the information by country and by year or a range of years.

![](screenshots\dashboard2_1.jpg)

2. I created a stacked bar chart that pulls data from the PivotTable and displays the number of terror attacks along with the distribution of attack types, based on the applied filters.

![](screenshots\dashboard2_2.jpg)

3. I created a line chart that pulls data from the PivotTable and displays the number of terror attacks over the years, based on the applied filters.
A trendline was added to show whether the number of attacks is increasing or decreasing over time.

![](screenshots\dashboard2_3.jpg)

## Dashboard 3 Build
![](screenshots\dashboard3.jpg)

1. I used a PivotTable created from the database.
The rows represent the attack type, and the values show the count of events.
Three slicers were added to allow the user to filter the information by country, by terror group name and by year or a range of years.

![](screenshots\dashboard3_1.jpg)

## Conclusion
In conclusion, this project provides an interactive and visual exploration of global terror attacks from 1970 to 2017. Through the use of PivotTables, slicers, and various chart types, users can filter and analyze the data by region, country, year, terror group, and attack type. The dashboard makes it easy to identify trends, compare distributions, and gain insights into the scale and nature of terrorism across different dimensions. By transforming complex data into accessible visuals, this tool supports deeper investigation and understanding of global terrorism patterns.