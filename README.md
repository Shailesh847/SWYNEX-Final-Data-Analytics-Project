# Customer Marketing Analytics Case Study

## SWYNEX Technologies Internship Project

**Author:** Shailesh Kumar Verma  
**Role:** Data Analyst Intern  
**Tools:** Microsoft Excel, MySQL, Power BI  
**Dataset:** Customer Marketing Campaign Dataset  
**Records:** 2,240 Customers  
**Columns:** 29  

---

## Project Overview

This project was completed as part of my Data Analyst Internship at **SWYNEX Technologies**.

The project covers the complete data analytics workflow, starting from raw customer marketing data and ending with an interactive Power BI dashboard and business insights.

Instead of treating data cleaning, SQL analysis, and dashboard creation as separate activities, I combined all three tasks into one end-to-end analytics case study.

### Project Workflow

Raw Customer Data
       ↓
Data Cleaning & Validation
       ↓
SQL Exploratory Data Analysis
       ↓
Identify Patterns & Anomalies
       ↓
Power BI Dashboard
       ↓
Business Insights
       ↓
Final Analytics Case Study

The project answers three main questions:

Who are the customers?
What do they buy and how do they purchase?
How do they respond to marketing campaigns?

Business Problem

A retail-style business has customer data containing demographic information, purchasing behaviour, product spending, website activity, and marketing campaign responses.

However, raw data may contain missing values, inconsistent information, and potential anomalies. Without properly preparing and analysing this data, it becomes difficult to understand customer behaviour and evaluate campaign response.

The objective of this project was to:

Clean and validate the customer dataset.
Explore the data using SQL.
Identify meaningful customer and purchasing patterns.
Analyse marketing campaign responses.
Build an interactive Power BI dashboard.
Convert analytical findings into clear business insights.
Document the complete analytics workflow.
Dataset Information

The project uses a customer marketing campaign dataset containing:

2,240 customer records
29 columns

The dataset contains information related to:

Customer Demographics
Customer ID
Year of Birth
Age
Education
Marital Status
Income
Household Information
Number of Children
Number of Teenagers
Customer Enrollment Date
Product Spending
Wines
Fruits
Meat Products
Fish Products
Sweet Products
Gold Products
Purchase Behaviour
Deals Purchases
Web Purchases
Catalog Purchases
Store Purchases
Website Visits
Marketing Campaigns
Campaign 1 Acceptance
Campaign 2 Acceptance
Campaign 3 Acceptance
Campaign 4 Acceptance
Campaign 5 Acceptance
Overall Campaign Response
Other Information
Recency
Complaints
Cost Contact
Revenue

# Task 1: Data Cleaning & Preparation
Objective

The first task was to determine whether the raw dataset was clean and ready for analysis.

The main focus was on identifying:

Duplicate records
Missing values
Inconsistent categories
Incorrect formats
Potential outliers
Data type issues
Data Cleaning Process
1. Checked Customer IDs

I checked the customer ID column to identify duplicate customer records.

Result:

Total Customers: 2,240
Duplicate IDs: 0

This confirmed that each customer ID was unique.

2. Handled Missing Income Values

The dataset contained 24 missing Income values.

Instead of replacing these values with zero or an estimated average, the missing values were retained as NULL.

The Income column was temporarily converted to text so that blank and whitespace values could be identified correctly.

After cleaning:

Missing Income: 24
Customer records lost: 0
Income data type: DECIMAL

This approach preserved the original information without creating artificial income values.

3. Standardized Education Categories

Some education categories represented similar education levels.

The categories were standardized as follows:

Original Value	Standardized Value
Graduation	Graduate
2n Cycle	Graduate
Basic	Basic
Master	Master
PhD	PhD

Final education categories:

Basic
Graduate
Master
PhD
4. Standardized Marital Status

Some marital-status values were inconsistent or represented similar groups.

The categories were standardized as follows:

Original Value	Standardized Value
Together	Married
Widow	Widowed
Alone	Single
Absurd	Single
YOLO	Single

Final categories:

Single
Married
Divorced
Widowed
5. Created Age Column

Age was calculated using the customer's year of birth.

Age = 2025 - Year_Birth

This created a new Age column for customer segmentation and analysis.

6. Standardized Customer Dates

The customer enrollment date was formatted consistently using:

YYYY-MM-DD

This made the date field easier to use in SQL and Power BI.

7. Checked Potential Age Anomalies

Customers with an age above 100 were investigated.

There were:

3 records with Age > 100

These values were treated as potential anomalies, rather than automatically deleting them, because their correctness could not be independently verified.

8. Checked Income Anomalies

The highest recorded income was:

666,666

This value was flagged as a potential anomaly and retained rather than automatically removed.

Task 1 Result

After cleaning and validation:

Data Quality Check	Result
Total Customers	2,240
Duplicate IDs	0
Missing Income	24
Age > 100	3
Highest Income	666,666
Customer Records Lost	0

The cleaned dataset was then prepared for SQL analysis.

# Task 2: SQL Exploratory Data Analysis

Objective

After cleaning the dataset, the next question was:

What is the data actually telling us?

The cleaned dataset was exported and imported into MySQL Workbench for exploratory data analysis.

SQL Analysis Process

The SQL analysis covered:

Customer counts
Age analysis
Income analysis
Education distribution
Marital status distribution
Product spending
Purchase channels
Website behaviour
Campaign responses
Campaign acceptance
Age segmentation
Income segmentation
Top-spending customers
Potential anomalies
SQL Techniques Used

The analysis involved:

SELECT
WHERE
GROUP BY
ORDER BY
COUNT()
SUM()
AVG()
MIN()
MAX()
CASE
Filtering
Derived calculations
Segmentation
Key SQL Findings
Customer Overview

The dataset contains:

2,240 customers
Average Age: 56.19 years
Average Income: approximately 52,247
Average Total Spending: 605.80
Education Distribution
Education	Customers
Graduate	1,330
PhD	486
Master	370
Basic	54

Graduate customers represent the largest education group.

Age Distribution

The dataset is concentrated among older customers.

Age Group	Customers
60+	860
50–59	685
40–49	506
30–39	187
Under 30	2

Customers aged 50 and above represent approximately 69% of the dataset.

Marital Status
Marital Status	Customers
Married	1,444
Single	487
Divorced	232
Widowed	77

Married customers form the largest group.

Income vs Spending

Customers were divided into three income groups:

Low Income
Medium Income
High Income

Average spending was:

Income Group	Average Spending
High Income	1,210.37
Medium Income	298.24
Low Income	97.51

The analysis shows that average spending varies substantially across income groups.

This is an observed association in the dataset and should not be interpreted as proof that income directly causes higher spending.

Product Spending Analysis

Total spending across six product categories was analysed.

Product Category	Total Spending
Wines	680,816
Meat Products	373,968
Gold Products	98,609
Fish Products	84,057
Sweet Products	60,621
Fruits	58,917
Key Finding

Wines recorded the highest total spending at 680,816, representing roughly half of the spending across the six product categories.

Purchase Channel Analysis

Purchases were analysed across:

Store
Web
Catalog
Purchase Channel	Purchases
Store	12,970
Web	9,150
Catalog	5,963
Key Finding

Store purchases were the highest purchase channel in the dataset.

Campaign Response Analysis

The overall campaign response was analysed using the Response field.

Response	Customers
Responded	334
Did Not Respond	1,906
Overall Response Rate

14.91%

This means that 334 out of 2,240 customers responded to the campaign.

Campaign Acceptance

Acceptance counts were analysed for the five campaigns.

Campaign	Acceptance Count
Campaign 1	144
Campaign 2	30
Campaign 3	163
Campaign 4	167
Campaign 5	163

Campaign 4 recorded the highest raw acceptance count at 167.

However, these are raw acceptance counts, not campaign effectiveness rates. Since campaign exposure or audience size was not available, effectiveness cannot be directly compared using these counts alone.

# Task 3: Power BI Interactive Dashboard
Objective

The third task focused on converting the SQL analysis into an interactive and easy-to-understand Power BI dashboard.

The dashboard was designed as a three-page analytical story:

Page 1
Who are the customers?
        ↓
Page 2
What do they buy and how do they purchase?
        ↓
Page 3
How do they respond to marketing campaigns?
Dashboard Page 1: Customer Marketing Overview
Purpose

This page focuses on customer demographics and overall customer characteristics.

KPIs
Total Customers: 2,240
Average Age: 56.19
Average Income: 52,247
Average Spending: 605.80
Visuals
Education Distribution
Age Group Distribution
Marital Status Distribution
Income Group vs Average Spending
Interactive slicers
Slicers
Education
Marital Status
Age Group
Income Group
Key Insight

The customer base is mainly older, married, and Graduate-educated, with average spending varying substantially across income groups.

Dashboard Page 2: Product & Purchase Analysis
Purpose

This page focuses on what customers spend money on and how they make purchases.

Visuals
Product Spending by Category
Purchase Channel Analysis
Website Visits vs Web Purchases
Top 10 Customers by Total Spending
Key Findings
Wines had the highest spending at 680,816.
Meat was the second-highest category at 373,968.
Store purchases were highest at 12,970.
Web purchases reached 9,150.
Catalog purchases reached 5,963.
A Top 10 view identifies the highest-spending customers.
Dashboard Page 3: Campaign Performance
Purpose

This page analyses how customers responded to marketing campaigns.

KPIs / Visuals
Overall Campaign Response Rate
Responders vs Non-Responders
Campaign Acceptance Counts
Response by Education
Response by Income Group
Interactive filters
Key Findings
Overall response rate: 14.91%
Responders: 334
Non-responders: 1,906
Campaign acceptance counts varied across the five campaigns.
Response patterns were explored across education and income groups.
Interactive Dashboard Features

The Power BI dashboard includes:

KPI cards
Charts
Slicers
Interactive filters
Customer segmentation
Product analysis
Campaign analysis
Top customer analysis
Data modelling
DAX measures

The dashboard allows users to filter the data and explore different customer segments without changing the underlying analysis.

Key Business Insights
1. Customer Age Profile

Approximately 69% of customers are aged 50 or above, making older customers a major segment of the dataset.

2. Education Profile

Graduate customers form the largest education group with 1,330 customers, approximately 59% of the dataset.

3. Income and Spending

Average spending varies substantially across income groups:

High Income: 1,210.37
Medium Income: 298.24
Low Income: 97.51

4. Product Spending

Wines recorded the highest spending at 680,816, representing roughly half of spending across the six product categories.

5. Purchase Channels

Store purchases were highest at 12,970, followed by:

Web: 9,150
Catalog: 5,963

6. Campaign Response

The overall campaign response rate was 14.91%, with 334 customers responding out of 2,240.

7. Campaign Acceptance

Campaign acceptance counts ranged from 30 to 167.

Campaign 4 recorded the highest raw acceptance count, but campaign effectiveness cannot be determined from raw counts alone because campaign exposure data was not available.

Overall Business Story

The three dashboard pages create a connected analytical story.

Page 1 — Customer

The customer base is mainly older, married, and has a large Graduate-educated segment. Average spending varies considerably across income groups.

Page 2 — Behaviour

Wine and Meat have the highest product spending, while Store is the largest purchase channel.

Page 3 — Marketing

The overall campaign response rate is 14.91%, with response patterns varying across campaigns, education, and income groups.

Together, these findings provide a structured view of:

Customer Profile
      ↓
Customer Behaviour
      ↓
Purchasing Patterns
      ↓
Marketing Response
      ↓
Business Insights

Limitations

This analysis is based only on the information available in the customer marketing dataset.

The analysis identifies patterns and associations but does not establish causal relationships between variables.

Campaign acceptance counts were analysed as raw counts because campaign exposure or audience size was not available. Therefore, campaign effectiveness cannot be directly compared using acceptance counts alone.

Further Analysis Opportunities

The project could be extended with:

Campaign-level response rates
Customer Lifetime Value analysis
Customer segmentation
Customer retention analysis
Purchase frequency analysis
Customer value segmentation
Statistical correlation analysis
Deeper website engagement analysis
Campaign effectiveness analysis using campaign exposure data
Tools & Technologies
Microsoft Excel

Used for:

Initial data cleaning
Data preparation
Data validation
Supporting data checks
Cleaned dataset export
MySQL Workbench

Used for:

Data import
Data validation
Missing-value checks
Exploratory Data Analysis
Aggregations
Customer segmentation
Campaign analysis
Anomaly checks
Power BI

Used for:

Data modelling
DAX measures
KPI cards
Interactive charts
Slicers
Customer segmentation
Dashboard development
Business storytelling
Microsoft Word

Used for:

Final project documentation
Analytics case study
Business insights
Project conclusion
Skills Demonstrated

Through this project, I practised:

Data Cleaning
Data Preparation
Data Validation
Exploratory Data Analysis
SQL
MySQL
Excel
Power BI
DAX
Data Modelling
Customer Segmentation
Data Visualization
KPI Development
Dashboard Design
Business Analysis
Business Storytelling
Analytical Documentation

Project Deliverables

This repository contains the complete work completed across the three internship tasks:

Task 1

Data Cleaning & Preparation

Excel-based data cleaning, validation, standardization, anomaly checking, and data dictionary.

Task 2

SQL Exploratory Data Analysis

MySQL-based data validation, customer analysis, product spending analysis, purchase behaviour analysis, segmentation, and campaign analysis.

Task 3

Interactive Power BI Dashboard

Three-page Power BI dashboard covering customer demographics, product and purchase behaviour, and campaign performance.

Final Project

A complete analytics case study combining:

Data Cleaning + SQL Analysis + Power BI Dashboard + Business Insights = Complete Analytics Project

What I Learned

This project helped me understand that data analysis is not only about creating charts or writing SQL queries.

The complete process starts with understanding whether the data is reliable.

I learned how to:

Inspect and clean raw data.
Handle missing values carefully.
Identify duplicate records and potential anomalies.
Use SQL to explore customer and business data.
Create meaningful customer segments.
Calculate business metrics using SQL and DAX.
Build an interactive Power BI dashboard.
Convert analytical results into business insights.
Present technical findings in simple language.
Connect multiple stages of an analytics project into one complete workflow.

One of the most important lessons from this project was that good analysis starts with good data preparation and ends with clear communication of insights.

Conclusion

This project demonstrates an end-to-end data analytics workflow using Excel, MySQL, and Power BI.

Starting with a raw customer marketing dataset, I cleaned and validated the data, performed exploratory analysis using SQL, identified customer and purchasing patterns, built an interactive three-page Power BI dashboard, and translated the findings into business insights.

The project gave me practical experience across the full analytics lifecycle:

Raw Data
   ↓
Data Cleaning
   ↓
Data Validation
   ↓
SQL Analysis
   ↓
Data Visualization
   ↓
Dashboard
   ↓
Business Insights
   ↓
Final Analytics Case Study

This internship project strengthened my practical understanding of Data Analytics, SQL, Excel, Power BI, DAX, Data Visualization, and Business Analysis.

Author

Shailesh Kumar Verma

Data Analyst Intern | Data Analytics | SQL | Power BI | Excel

Related Task Repositories
Task 1 — Data Cleaning & Preparation

https://github.com/Shailesh847/SWYNEX-Data-Cleaning-Preparation

Task 2 — SQL Exploratory Data Analysis

https://github.com/Shailesh847/SWYNEX-Exploratory-Data-Analysis

Task 3 — Interactive Power BI Dashboard

https://github.com/Shailesh847/SWYNEX-Interactive-Dashboard

Final Project
SWYNEX Customer Marketing Analytics Case Study
