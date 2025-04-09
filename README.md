# OPTIMIZING SALES AND CUSTOMER ENGAGEMENT - MZALENDO COFFEE MARKETERS
-----------------------------------------------------------------------------------------------------------------------------

![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/eebb5354801e5971468f78c85b7fdacf03aef79d/Cover%20Photo.png)

## TABLE OF CONTENTS
-----------------------------------------------------------------------------------------------------------------------------

- [OVERVIEW](#overview)

- [BUSINESS PROBLEM STATEMENT](#business-problem-statement)

- [DATA SOURCES](#data-sources)

- [TOOLS](#tools)

- [DATA CLEANING AND PREPARATION](#data-cleaning-and-preparation)

- [DATA MODELING](#data-modeling)

- [DATA TRANSFROMATION](#data-transformation)

- [DATA ANALYSIS FINDINGS](#data-analysis-findings)

    - [Sales Analysis and Profit Margins](sales-analysis-and-profit-margins)

- [RECOMMENDATIONS](#recommendations)

## OVERVIEW
-----------------------------------------------------------------------------------------------------------------------------
This project showcases a Sales Dashboard for a Coffee Marketing Company and displays metrics focusing on profitability across products, customer purchasing behavior and overall sales performance.

Below is a snapshot of the unfiltered dashboard. I have also attached the Excel file if you want to interact with the analysis further. I have also provided pivot tables which I found supported the findings of the project. Most of the indepth analysis in this project was achieved through pivot tables. The dashboard provided summary level insights while the pivot tables enabled me to access granular details about the data.

-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/785da519e6e30703f08e48a2046ffb7e9212d7c5/Sales%20Dashboard.png)

## BUSINESS PROBLEM STATEMENT
-----------------------------------------------------------------------------------------------------------------------------
Mzalendo Coffee Marketers(MCM) seeks to improve its sales and customer engagement strategy by developing an interactive Excel dashboard. This dashboard should provide stakeholders with insights into sales performance, customer purchasing behavior, and product profitability. The goal is to identify trends, optimize pricing strategies, and enhance customer loyalty.

## DATA SOURCES
-----------------------------------------------------------------------------------------------------------------------------
I obtained the data from an Excel Tutorial Project by Mo Chen, a data analyst content creator. Here is the link to the tutorial as well as the dataset used for this project:

[Tutorial](https://www.youtube.com/watch?v=m13o5aqeCbM)

[Dataset](https://github.com/mochen862/excel-project-coffee-sales)

#### *Considerations*
I decided to switch the context of the data and be a creative by **attaching the dataset to a fictional company name and altering the numerical columns** for **unit price and profits** from **USD to KES**. In the [Data Transformation](#data-transformation) section, I provide more insights on how I executed this. This analysis draws inspiration from the tutorial but I used my own unique approach to provide value to whoever would like to use the same dataset to learn.

## TOOLS
-----------------------------------------------------------------------------------------------------------------------------
This project is purely Microsoft Excel based. I performed my data cleaning, data transformations, analysis and visualization using Microsoft Excel.

## DATA CLEANING AND PREPARATION
-----------------------------------------------------------------------------------------------------------------------------
For this analysis, I paid close attention to any duplicate data points as well as any missing data that could potentially skew the results of my analysis. There were no duplicates. There were several missing data points for the **Phone number(130)** and **Email(204)** columns. These columns will not have an impact on my analysis hence I will ignore the missing values and proceed. Since no grouping or aggregation is being done based on these columns, I will not exclude the records from analysis.

## DATA MODELING
-----------------------------------------------------------------------------------------------------------------------------
I have two types of tables for my analysis: the transaction table(i.e. orders) and dimension tables(i.e. customers, products and exchange rate). I need to perform data gathering to link important columns not in the **orders** table for the purpose of pivoting and visualizing. To do this, I identified columns from other tables that I needed for my analysis as follows:

| Table Name | Columns Required|
|------------|-----------------|
|customers|city, country,loyalty card status|
|products|coffee type, roast type,size,unit price, profit|
|exchange rate|price|

In order to link the required columns to my orders table, I used **XLOOKUP** and **INDEX-MATCH**.

Below is an entity relationship diagram demonstrating related columns that made this linking possible.

-----------------------------------------------------------------------------------------------------------------------------
![Relationships between Tables](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/18cce1f78cfb0a5a74b1b746acb289ed9cbaa957/Data%20Gathering.png)

## DATA TRANSFORMATION
-----------------------------------------------------------------------------------------------------------------------------
As I had mentioned earlier, to switch context I decided to convert the **unit price** and **profit** columns into KES. I made the assumption that the initial values were in USD. To do this I downloaded the historical exchange rates for USD/KES from [investing.com](https://www.investing.com/currencies/usd-kes-historical-data) and used the **price** column to apply the exchange rates to my **orders** table.

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

## DATA ANALYSIS FINDINGS
-----------------------------------------------------------------------------------------------------------------------------

#### Introduction
In reference to the objective of this project, I would like to understand sales and profitability of MCM's different coffee types, roast types and cofee size offerings. 

Mzalendo Coffee Marketers(MCM) exports coffee to three countries: United states, United Kingdom and Ireland. Which of these countries performed best and what changes can be made to improve sales as well as profitability?

***Assumption***: The profit provided in the dataset implies net profit(profit after cost of goods and operational expenses have been deducted).

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
Profit margins have increased by a small margin 0f 1.02% from 2020 to 2022.

#### Performance by Country
|Country|Recorded Sales|Percentage of Total Sales|Profit Margin|
|-------|--------------|----------|----------|
|United States| KES 3.718 million|76.8%|10.17%|
|Ireland|KES 0.77 million|15.7%|9.36%|
|United Kingdom|KES 0.386 million|7.5%|8.2%|

MCM's best performing market is in the USA which contributes more than **75%** of sales. Sales from Ireland and United Kingdom contribute the remaining less than **25%**.

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

The best performing roast type by sales is **Light** which is followed closely by the **Medium** roast type. However, the **Dark** roast type which registered the lowest sales has the second highest profit margin. 

#### Performance by Coffee Size
|Coffee Size|Recorded Sales|Percentage of Total Sales|Units Sold|Profit Margin|
|-------|--------------|----------|----|---|
|2.5kg| KES 2.695 million|54.8%|877|4.93%|
|1kg|KES 1.094 million|22.2%|811|9.12%|
|0.5kg|KES 0.766 million|15.6%|953|16.67%|
|0.2kg|KES 0.361 million|7.34%|910|34.83%|

Given the higher pricing for the 2.5kg coffee package across roast types and coffee types, it is expected that it earned MCM the highest amount of sales. However, with regard to profitability **2.5kg** coffee had the lowest profit margin of **4.93%** compared to the **0.2kg(34.83%)** package. MCM's best performing coffee size in terms of **units sold** is the **0.5kg** package followed closely by the **0.2kg** package.

### Units Sold
-----------------------------------------------------------------------------------------------------------------------------

The pivot tables attached below show the preferences in purchasing a certain coffee sizes based on Country and Coffee Type. 
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

Mzalendo Coffee Marketers(MCM) has a loyalty programme for its repeat/regular customers. I wanted to understand purchasing trends based on the number of units they have purchased by coffee type and roast type. This will enable me to understand how they compare to customers who engage with MCM's brand on a need basis, seeking discounts or engaging in impulse buying(i.e. customers not on the loyalty programme).

-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/e64272291f4e02dd85cfd79651c5980cf8634998/Loyalty%20Status.png)

MCM's **loyal customers** purchase more of the **dark roast type** across MCM's different coffee type categories. Their preferred **coffee type** **irrespective** of roast type was **Excelsa(503 units purchased)** with **Arabica(467 units purchased)** being the second most preferred coffee type.

Consumers **not on the loyalty programme** preferred the **Light roast type** across  MCM's coffee type categories. Their preferred **coffee type** **irrespective** of roast type was **Arabica(502 units purchased)** with **Liberica(492 units purchased)** being the second most preferred coffee type.

**Arabica coffee type** is highly preferred by both loyalty groups. **Excelsa** is the **least preferred** coffee type by consumers **not on the loyalty programme** while **Liberica** is the **least preffered** by consumers in the **loyalty programme**.

### Pricing Analysis
-----------------------------------------------------------------------------------------------------------------------------

***Note***: For Pivot Tables in this section:
- L stands for Light roast type 
- M stands for Medium roast type
- D stands for Dark roast type

It is expected that **2.5kgs coffee** package will have a **higher amount of sales** given that the **pricing is higher** than smaller coffee size offerings. I wanted to understand what the relationship is between pricing and the units sold between different coffee types, roast types and coffee sizes. I also wanted to see if there were any gaps in the market given the performance of different coffee types, roast types and sizes across different countries.

#### Comparison of Average Pricing across different Coffee Types and Roast Type
-----------------------------------------------------------------------------------------------------------------------------

![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/a03441911f20bb4e5eb3a4f8b790681374ca17c0/AVG%20Price%20-%20Type%20%26%20Roast(Size%20excluded).png)

On average **Liberica** is the highest priced coffee type across different roast types while **Robusta** is the cheapest coffee type marketed by MCM.

#### Comparison of Pricing and Units Sold across different Coffee Types, Roast Types and Sizes
-----------------------------------------------------------------------------------------------------------------------------

![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/9258bbfd96da7ffea0bea697a597e75c712370b4/General%20Pricing%20-%20Units%20Sold.png)

MCM's dark roast variety is the cheapest across its different coffee types and coffee sizes.

The light roast is the highest priced roast type across MCM's different coffee types and coffee sizes.

#### Comparison of Pricing and Units Sold of different Coffee Types, Roast Types and Sizes across Countries
-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/9ce940f7fdc88f9acc0bc76acbdd0454e9c091de/Pricing%20Analysis.png)

The areas highlighted in **yellow** show coffee sizes or roast types which are currently not being exported to Ireland and United Kingdom. It is only in the United States where MCM has registered sales for all of its current product offerings across coffee sizes, roast types and coffee types.

The table below provides a summary based on Coffee Type of Roast Types and Coffee Sizes not currently being exported to Ireland and United Kingdom:

|------|Ireland|United Kingdom|
|------|-------|--------------|
|Arabica| 0.2kgs Medium| 1kg light, 0.2kg light|
|Excelsa|-|0.2kg light|1kg dark|
|Liberica|0.5kg medium|0.5kg dark,1kg dark|
|Robusta|2.5kg medium|0.2kg light,0.5kg dark|

## RECOMMENDATIONS
-----------------------------------------------------------------------------------------------------------------------------
### 1.Addressing 2022 Sales Decline

**Finding**: Sales dropped by **50.3%** in 2022 despite a slight increase in profit margin(0.75% increase)

#### A. What is the Root Cause?

- It is essential to **investigate the root cause** of this change to differentiate this event from underlying, ongoing business trends such as customer behavior, product pricing, or regional changes in the coffee market.
- Isolating the cause of the sharp decline will prevent drastic decisions being taken with regard to how MCM markets its products if at all this is not an ongoing trend.

#### B. Consider the underperfroming regions - Ireland and United Kingdom

Currently, Ireland and United Kingdom accounts for less than 25% of sales that MCM makes. More than 75% of the sales made come from the United States.

#### Sales Growth by Country and Coffee Type - 2019-2022
-----------------------------------------------------------------------------------------------------------------------------
![](https://github.com/IsaacKanyili161/Sales-Analysis-Mzalendo-Coffee-Marketers/blob/070bc08bdc360fb575993a8130d0c7ffb12addbd/Sales%20Growth%20-%20Coffee%20Type%20and%20Country.png)

On closer inspection, I noticed that the United Kingdom registered a decline in sales since 2021 and not only in 2022 like Ireland and United States. All four of the coffee types marketed by MCM registered a sales decline from 2021. Additionally, **no sales** were made for the Robusta coffee type in 2022.This appears as "#NULL!" in the pivot table above.

These findings showed a worrying trend in the United Kingdom which needs to be investigated further to ensure the trend does not persist.

### 2. Reassessing Mzalendo Coffee Marketer's Product Portfolio by Profitability and Sales Volume

**A**

**Finding**: Referring back to the **Sales Growth by Country and Coffee Type - 2019-2022** pivot table, you will notice that sales for **Liberica** droped by more than **50%** in all three countries. A similar trend is observed for **Arabica** in both Ireland and the United Kingdom. As mentioned earlier, Liberica had the highest prices on average across the different roast types. 

**Recommendation**: Despite Liberica and Arabica registering the 2nd and 3rd highest sales respectively, their is a need to do a price review to ensure continued profitability and penetration of these coffee types in all three countries.

**B**

**Finding**: **Excelsa leads in sales (28.3%)**, but **Robusta is the most profitable coffee type (13.39% margin)**. Similarly, **smaller packages (0.2kg and 0.5kg) are more profitable** than the 2.5kg package.

**Recommendation**:
- **Boost promotional and marketing campaigns for Robusta and Arabica**, especially in higher-margin coffee sizes like 0.2kg and 0.5kg.

- **Re-evaluate the pricing or cost structure of the 2.5kg size**. Its low profit margin (4.93%) suggests high cost-to-revenue inefficiency. Either raise price points or reduce cost inputs.

### 3. Capitalize on Regional Preferences and filling product gaps
**Finding**: The U.S. dominates sales (76.8%), with Arabica preferred. Ireland prefers Robusta while the United Kingdom favors Arabica.

**Recommendations**:
- **United States**: Maintain product diversity, but commit more resources in terms of production, marekting and promotion on Arabica in smaller sizes (0.2kg and 0.5kg), which are both preferred and more profitable.

- **Ireland**: Increase availability of Robusta in 0.2kg and 0.5kg, matching customer preferences. Currently, Exelsa is not exported to Ireland. This presents an excellent gap to test a new product as well as marketing and promotional methodology.

- **United Kingdom**: Fill product gaps such as Arabica 1kg Light and Robusta 0.5kg Dark. The 1kg packaging is also not being sold in the United Kingdom for Arabica Light,Excelsa Dark and Liberica Dark. These changes can be made in phases to test consumers' reaction as they already have a preference for the Arabica Coffee Type.

### 4. Leverage Loyalty Program Insights
**Finding**: Loyal customers prefer Excelsa and Dark roasts; non-loyal customers prefer Arabica and Light roasts.

**Recommendations**:

- Develop loyalty based product bundles: Work on exclusive branding and promotional campaigns to offer exclusive Dark roast or Excelsa bundles to loyal customers to drive repeat purchases. These bundles could also include discounts for other product offerings to improve sales for other coffee types,sizes and roast types.

- Convert non-loyal buyers with targeted campaigns offering first-time discounts on larger sizes of Arabica or introductory Dark roast packs. Given the prevalence of Excelsa for loyal customers, you could also upsell this coffee type by offering free samples of Excelsa bundled with loyalty card status to potentially improve Excelsa sales and add to the list of potential loyal customers.

These recommendations are not exhaustive as more data can be used to identify relationships which could be hidden as well as other root causes of the sales decline observed from 2021 to 2022.

---------------------------------------------------- END OF PROJECT --------------------------------------------------------





























