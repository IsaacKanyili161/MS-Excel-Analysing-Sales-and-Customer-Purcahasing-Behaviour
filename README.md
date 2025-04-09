# OPTIMIZING SALES AND CUSTOMER ENGAGEMENT - MZALENDO COFFEE MARKETERS
-----------------------------------------------------------------------------------------------------------------------------

![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/eebb5354801e5971468f78c85b7fdacf03aef79d/Cover%20Photo.png)

## Overview
-----------------------------------------------------------------------------------------------------------------------------
This project showcases a Sales Dashboard for a Coffee Marketing Company displaying metrics focusing on profitability across products, customer purchasing behavior and overall sales performance.

Here is a snapshot of the unfiltered dashboard. I have also attached the xlsx file if you want to interact with the analysis further. I have also provided different pivot tables which I found supported the findings of the project.

-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/785da519e6e30703f08e48a2046ffb7e9212d7c5/Sales%20Dashboard.png)

## Business Problem Statement
-----------------------------------------------------------------------------------------------------------------------------
Mzalendo Coffee Marketers seeks to improve its sales and customer engagement strategy by developing an interactive Excel dashboard. This dashboard should provide stakeholders with insights into sales performance, customer purchasing behavior, and product profitability. The goal is to identify trends, optimize pricing strategies, and enhance customer loyalty.

## Data Sources
-----------------------------------------------------------------------------------------------------------------------------
I obtained the data from an Excel Tutorial Project by Mo Chen, a data analyst content creator. Here is the link to the tutorial as well as the dataset used for this analysis:

[Tutorial](https://www.youtube.com/watch?v=m13o5aqeCbM)

[Dataset](https://github.com/mochen862/excel-project-coffee-sales)

#### *Considerations*
I decided to give this project context by **attaching the dataset to a fictional company name and altering the numerical columns** for **unit price and profits** from **USD to KES**. In the [Data Transformation](#data-transformation) section, I provide more insights on how I executed this. This analysis draws inspiration from the tutorial but I used my own unique approach to provide value to whoever would like to use the same dataset to learn.

## Tools
-----------------------------------------------------------------------------------------------------------------------------
This project is purely Microsoft Excel based. I performed my data cleaning, data transformations, analysis and visualization using Microsoft Excel.

## Data Cleaning and Preparation
-----------------------------------------------------------------------------------------------------------------------------
For this analysis, I paid close attention to any duplicate data points as well as any missing data that could potenitally skew the results of my analysis. There were no duplicates. There were several missing data points for the **Phone number(130)** and **Email(204)** columns. These columns will not have an immediate impact on my analysis hence I will ignore the missing values and proceed. Since no grouping is being done with these columns, I will retain other fields for records with missing values.

## Data Modeling
-----------------------------------------------------------------------------------------------------------------------------
I have two types of tables for my analysis: the transaction table(i.e orders) and dimension tables(customers, products and exchange rate). I need to perform a data gathering process to link important columns not in the **orders** table for the purpose of pivoting and visualizing. To do this I identify the columns, I identified columns from other tables that I needed for my analysis as follows:

| Table Name | Columns Required|
|------------|-----------------|
|customers|city, country,loyalty card status|
|products|coffee type, roast type,size,unit price, profit|
|exchange rate|price|

In order to link the required columns to my orders table I used **XLOOKUP** and **INDEX-MATCH**.

Below is an entity relationship diagram demonstrating related columns that made this linking possible.

-----------------------------------------------------------------------------------------------------------------------------
![Relationships between Tables](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/18cce1f78cfb0a5a74b1b746acb289ed9cbaa957/Data%20Gathering.png)

## Data Transformation
-----------------------------------------------------------------------------------------------------------------------------
As I had mentioned earlier, to add context I decided to convert the **unit price** and **profit** columns into KES. I made the assumption that the initial values were in USD. To do this I downloaded the historical exchange rates for USD/KES from 
[investing.com](https://www.investing.com/currencies/usd-kes-historical-data) and used the **price** column to apply the exchange rates to my **orders** table.

In order to obtain the ***sales metric***, I created a new column called **sales** in my **orders** table with the following calculation:

                                          unit price x quantity

In order to get robust and meaningful visualizations I used *if-statements* to convert the records for the **coffee type** and **roast type** to their full names as follows

|Coffee Type Abbreviation|Full Name|
|---|-------|
|Ara|Arabica|
|Exc|Excelsa|
|Lib|Liberica|
|Rob|Robusta|

|Roast Type Abbreviation|Full Name|
|--|--------|
|M|Medium|
|L|Light|
|D|Dark|

## Data Analysis Findings
-----------------------------------------------------------------------------------------------------------------------------

### Introduction
In reference to the objective of this project, I would like to understand sales and profitability of our different coffee types, roast types and cofee size offerings. 

Mzalendo Coffee Marketers(MCM) exports coffee to three countries: United states, United Kingdom and Ireland. Which of these countries performed best and what changes can be made to improve sales as well as profitability.

***Assumption***: The profit provided in the dataset is net profit after cost of goods and operational expenses have been deducted.

### Sales Analysis and Profit Margins
-----------------------------------------------------------------------------------------------------------------------------
MCM registered total sales of **KES 4.918 million** from the year 2019 to 2022 (4 years). Unless stated otherwise the analysis will be based on all four years.

#### Performance by Year
|Year|Recorded Sales|Growth(%)|Profit Margin|
|-------|--------------|----------|-----------|
|2019|KES 1.171 million|-|10.71%|
|2020|KES 1.362 million|16.3%|9.31%|
|2021|KES 1.593 million|16.9%|9.58%
|2022|KES 0.792 million|-50.3%(**decline**)|10.33%(**growth**)|

MCM experienced steady sales growth from 2019 to 2021. In 2022 there was a 50.3% drop in sales.
Profit margins have increased by a small margin 0f 1.02% from 2020 to 2022. This is despite the sharp decline in sales registered in 2022.

#### Performance by Country
|Country|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----------|
|United States| KES 3.718 million|76.8%|10.17%|
|Ireland|KES 0.77 million|15.7%|9.36%|
|United Kingdom|KES 0.386 million|7.5%|8.2%|

MCM's best performing market is in the USA which contributes more than **75%** of sales. Sales from Ireland and United Kingdom contribute the remaining **25%** with Ireland contributing over **60%** of the remaining sales generated by MCM. Profit margins in all three countries follow the same pattern as sales with the United States leading with **10.17%**.

#### Performance by Coffee Type
|Coffee Type|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----|
|Excelsa| KES 1.392 million|28.3%|8.39%|
|Liberica|KES 1.307 million|26.6%|7.85%|
|Arabica|KES 1.296 million|26.3%|11.07%|
|Robusta|KES 0.923 million|18.8%|13.39%|

Excelsa coffee type contributes the highest in terms of total sales. But with regard to profit margins, Robusta, which registered the lowest amount of sales had the highest profit margin of **13.39%** which is **5%** higher than profit registered from Excelsa.

#### Performance by Roast Type
|Roast Type|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----|
|Light| KES 1.85 million|37.6%|9.03%|
|Medium|KES 1.667 million|33.9%|10.5%|
|Dark|KES 1.4 million|28.5%|10.32%|

The best performing roast type is **Light** which is followed closely by the **Medium** roast type. However the **Dark** roast type which registered the lowest sales has the second highest profit margin. 

#### Performance by Coffee Size
|Coffee Size|Recorded Sales|Percentage of Total Sales|Units Sold|Profit Margin|
|-------|--------------|----------|----|---|
|2.5kg| KES 2.695 million|54.8%|877|4.93%|
|1kg|KES 1.094 million|22.2%|811|9.12%|
|0.5kg|KES 0.766 million|15.6%|953|16.67%|
|0.2kg|KES 0.361 million|7.34%|910|34.83%|

Given the higher pricing for the 2.5kg coffee package across roast type and coffee types, it is expected that it earned MCM the highest amount of sales. However with regard to profitability **2.5kg** coffee had the lowest profit margin of **4.93%** compared to the **0.2kg** package. Our best performing coffee size in terms of **units sold** is the **0.5kg** package followed closely by the **0.2kg** package.

### Units Sold
-----------------------------------------------------------------------------------------------------------------------------

The pivot tables attached below show the preferences in purchasing a certain coffee size based on Country and Coffee Type. 
I have also done an analysis by Country to understand what coffee types different countries prefer.

-----------------------------------------------------------------------------------------------------------------------------
![**UNITS SOLD ANALYSIS**](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/f12444e3c7bf46b33a8833883d282a3f43b3dc25/Units%20Sold.png)

In reference to the different **coffee size packages** being offered by MCM, the preferred coffee size for consumers who purchase the **Liberica and Robusta coffee type** is the **0.2kg** package. The **0.5kg** package is the most preferred by customers who purchase **Excelsa and Arabica**.

The **0.2kg and 0.5kg package** is the most preferred packaging for consumers who are in the **United States**. In both **Ireland and United Kingdom**, consumers prefer the **0.5kg and 2.5kg** coffee packages.

#### Preferred Coffee Type(Units Purchased)
|Country|Preferred Coffee Type(Units Purchased)|
|-------|--------------------------------------|
|United States|Arabica(**26% prevalence**)|
|Ireland|Robusta(**28.49% prevalence**)|
|United Kingdom|Arabica(**36.61% prevalence**)|

#### Loyalty Status and Units Sold

Mzalendo Coffee Marketers(MCM) has a loyalty programme for its repeat/regular customers. I wanted to understand purchasing trends based on the number of units they have purchased by coffee type and roast type. This will enable me to understand how they compare to customers who engage with MCM's brand as need based, discount seeking or impulse customers(i.e. customers not on the loyalty programme).

-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/e64272291f4e02dd85cfd79651c5980cf8634998/Loyalty%20Status.png)

MCM's **loyal customers** purchase more of the **dark roast type** across MCM's different coffee type categories. Their preferred **coffee type** **irrespective** of roast type was **Excelsa(503 units purchased)** with **Arabica(467 units purchased)** being the second most preffered coffee type.

Consumers **not on the loyalty programme** preferred the **Light roast type** across  MCM's coffee type categories. Their preferred **coffee type** **irrespective** of roast type was **Arabica(502 units purchased)** with **Liberica(492 units purchased)** being the second most prefferd coffee type.

**Arabica coffee type** is highly preferred by both loyalty groups. **Excelsa** is the **least preferred** coffee type by consumers **not on the loyalty programme** while **Liberica** is the **least preffered** by consumers in the **loyalty programme**.

### Pricing Analysis
-----------------------------------------------------------------------------------------------------------------------------

It is expected that **2.5kgs coffee** package will have a **higher amount of sales** given that the **pricing is higher** than smaller coffee size offerings. I wanted to understand what the relationship is between pricing and the units sold between different coffee types, roast types and coffee sizes. I also wanted to see if there were any gaps in the market given the performance of different coffee types, roast types and sizes across different countries.

#### Comparison of Pricing and Units Sold of different Coffee Types, Roast Types and Sizes across Countries
-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/9ce940f7fdc88f9acc0bc76acbdd0454e9c091de/Pricing%20Analysis.png)

The areas highlighted in **yellow** show coffee sizes or roast types which are currently not being exported to Ireland and United Kingdom. It is only in the United States where MCM has registered sales for all of its current product offerings across coffee sizes, roast types and coffee types.

## Assessment and Reporting of Data Analysis Findings
-----------------------------------------------------------------------------------------------------------------------------



















