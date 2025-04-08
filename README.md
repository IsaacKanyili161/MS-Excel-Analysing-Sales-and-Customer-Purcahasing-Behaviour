# OPTIMIZING SALES AND CUSTOMER ENGAGEMENT - MZALENDO COFFEE MARKETERS

![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/eebb5354801e5971468f78c85b7fdacf03aef79d/Cover%20Photo.png)

## Overview
This project showcases a Sales Dashboard for a Coffee Marketing Company displaying metrics focusing on profitability across products, customer purchasing behavior and overall sales performance.

## Business Problem Statement
Mzalendo Coffee Marketers seeks to improve its sales and customer engagement strategy by developing an interactive Excel dashboard. This dashboard should provide stakeholders with insights into sales performance, customer purchasing behavior, and product profitability. The goal is to identify trends, optimize pricing strategies, and enhance customer loyalty.

## Data Sources
I obtained the data from an Excel Tutorial Project by Mo Chen, a data analyst content creator. Here is the link to the tutorial as well as the dataset used for this analysis:

[Tutorial](https://www.youtube.com/watch?v=m13o5aqeCbM)

[Dataset](https://github.com/mochen862/excel-project-coffee-sales)

#### *Considerations*
I decided to give this project context by **attaching the dataset to a fictional company name and altering the numerical columns** for **unit price and profits** from **USD to KES**. In the [Data Transformation](#data-transformation) section, I provide more insights on how I executed this. This analysis draws inspiration from the tutorial but I used my own unique approach to provide value to whoever would like to use the same dataset to learn.

## Tools
This project is purely Microsoft Excel based. I performed my data cleaning, data transformations, analysis and visualization using Microsoft Excel.

## Data Cleaning and Preparation
For this analysis, I paid close attention to any duplicate data points as well as any missing data that could potenitally skew the results of my analysis. There were no duplicates. There were several missing data points for the **Phone number(130)** and **Email(204)** columns. These columns will not have an immediate impact on my analysis hence I will ignore the missing values and proceed. Since no grouping is being done with these columns, I will retain other fields for records with missing values.

## Data Modeling
I have two types of tables for my analysis: the transaction table(i.e orders) and dimension tables(customers, products and exchange rate). I need to perform a data gathering process to link important columns not in the **orders** table for the purpose of pivoting and visualizing. To do this I identify the columns, I identified columns from other tables that I needed for my analysis as follows:

| Table Name | Columns Required|
|------------|-----------------|
|customers|city, country,loyalty card status|
|products|coffee type, roast type,size,unit price, profit|
|exchange rate|price|

In order to link the required columns to my orders table I used **XLOOKUP** and **INDEX-MATCH**.

Below is an entity relationship diagram demonstrating related columns that made this linking possible.

![Relationships between Tables](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/18cce1f78cfb0a5a74b1b746acb289ed9cbaa957/Data%20Gathering.png)

## Data Transformation
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

## Data Analysis

### Introduction
In reference to the objective of this project, I would like to understand sales and profitability of our different coffee types, roast types and cofee size offerings. 

Mzalendo Coffee Marketers(MCM) exports coffee to three countries: United states, United Kingdom and Ireland. Which of these countries performed best and what changes can be made to improve sales as well as profitability.

***Assumption***: The profit provided in the dataset is net profit after cost of goods and operational expenses have been deducted.

### Sales Analysis and Profit Margins
MCM registered total sales of **KES 4.918 million** from the year 2019 to 2022 (4 years). Unless stated otherwise the analysis will be based on all four years.

#### Performance by Year
|Year|Recorded Sales|Growth(%)|Profit Margin|
|-------|--------------|----------|-----------|
|2019|KES 1.171 million|-|10.71%|
|2020|KES 1.362 million|16.3%|9.31%|
|2021|KES 1.593 million|16.9%|9.58%
|2022|KES 0.792 million|-50.3%(**decline**)|10.33%(**growth**)|

#### Performance by Country
|Country|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----------|
|United States| KES 3.718 million|76.8%|10.17%|
|Ireland|KES 0.77 million|15.7%|9.36%|
|United Kingdom|KES 0.386 million|7.5%|8.2%|

#### Performance by Coffee Type
|Cofee Type|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----|
|Excelsa| KES 1.392 million|28.3%|8.39%|
|Liberica|KES 1.307 million|26.6%|7.85%|
|Arabica|KES 1.296 million|26.3%|11.07%|
|Robusta|KES 0.923 million|18.8%|13.39%|

#### Performance by Roast Type
|Roast Type|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----|
|Light| KES 1.85 million|37.6%|9.03%|
|Medium|KES 1.667 million|33.9%|10.5%|
|Dark|KES 1.4 million|28.5%|10.32%|

#### Performance by Coffe Size
|Coffee Size|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----|
|2.5kg| KES 2.695 million|54.8%|4.93%|
|1kg|KES 1.094 million|22.2%|9.12%|
|0.5kg|KES 0.766 million|15.6%|16.67%|
|0.2kg|KES 0.361 million|7.34%|34.83%|

### Units Sold and Pricing Analysis

The pivot tables attached below show the preferences in purchasing a certain coffee size based on Country and Coffee Type. 
I have also done an analysis by Country to understand what coffee types different countries prefer.

![**UNITS SOLD ANALYSIS**](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/8bf9c96d5c7e645a5de77f0a731ca698478d285d/Unit%20Analysis%20-%20Coffee%20Sales.png)

















