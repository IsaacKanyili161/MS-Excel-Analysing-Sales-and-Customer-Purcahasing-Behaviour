# OPTIMIZING SALES AND CUSTOMER ENGAGEMENT - MZALENDO COFFEE MARKETERS

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

![Relationships between Tables](https://github.com/IsaacKanyili161/SalesAnalysis---Mzalendo-Coffee-Marketers/blob/cc7f1f52864ee668c56dda86e5b0fe98f2d461d4/Data%20Modeling.png)

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











