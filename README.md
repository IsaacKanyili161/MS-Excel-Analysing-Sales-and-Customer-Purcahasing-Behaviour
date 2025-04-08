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

![Relationships between Tables]()

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

### General observations
MCM registered total sales of **KES 4.918 million** from the year 2019 to 2022 (4 years). Unless stated otherwise the analysis will be based on all four years.

Performance by Year
|Year|Recorded Sales|Growth(%)
|-------|--------------|----------|
|2019|KES 1.171 million|-|
|2020|KES 1.362 million|3.98%|
|2021|KES 1.593 million|4.7%|
|2022|KES 0.792 million|-16.3%(**decline**)|

Performance by Country:
|Country|Recorded Sales|Percentage
|-------|--------------|----------|
|United States| KES 3.718 million|76.8%|
|Ireland|KES 0.77 million|15.7%|
|United Kingdom|KES 0.386 million|7.5%|

Performance by Coffee Type:
|Coffee Type|Recorded Sales|Percentage
|-------|--------------|----------|
|Excelsa| KES 1.392 million|28.3%|
|Liberica|KES 1.307 million|26.6%|
|Arabica|KES 1.296 million|26.3%|
|Arabica|KES 0.923 million|18.8%|

Performance by Roast Type:
|Roast Type|Recorded Sales|Percentage
|-------|--------------|----------|
|Light| KES 1.85 million|37.6%|
|Medium|KES 1.667 million|33.9%|
|Dark|KES 1.4 million|28.5%|
















