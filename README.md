# Overview

This project demonstrates the end-to-end design and implementation of a modern Business Intelligence analytics system built using PostgreSQL, dbt, and Power BI. The objective was to transform raw transactional ecommerce data into a structured analytics warehouse, engineer meaningful business metrics, and deliver an executive-ready dashboard.

The system follows a layered architecture commonly used in modern analytics engineering teams: staging, dimensional modeling, metric computation, presentation layer modeling, and BI visualization.

This project represents a complete analytics lifecycle — from raw data ingestion to business insight delivery.



## Dataset Description

The dataset consisted of transactional ecommerce records stored in CSV format. It contained fields such as:

- Transaction ID

- Transaction Date

- Customer Identifier (User Name)

- Country

- Product Category

- Purchase Amount

- Payment Method

The dataset represented 50,000 unique transactions across different countries like USA, Germany, and Brazil.

During exploration, it became evident that the dataset exhibited unusual behavioral characteristics:

- Every customer was a repeat purchaser

- 100% repeat purchase rate

- Extremely high order frequency per customer

- Highly stable monthly revenue patterns

- Minimal customer churn behavior

These properties shaped the direction of the business analysis and modeling strategy.



## System Architecture

The solution was built using a layered warehouse approach:

Raw CSV Data -  PostgreSQL Database  -  dbt Staging Layer  -  Star Schema  -  Metrics Layer  -  Presentation Layer  -  Power BI Dashboard




## Data Engineering & Modeling

The first phase focused on building a clean analytical foundation.

A staging model was created to standardize and prepare raw transaction data. From there, a dimensional star schema was implemented :

- A fact table (fact_orders) containing one row per transaction

- A customer dimension table (dim_customers) containing one row per customer




## Metrics & Business Analysis

After establishing the star schema, a comprehensive metrics layer was engineered to support business decision-making.

### Executive KPIs (Key Performance Indicators) An aggregated KPI overview was developed including :

- Total Orders

- Total Customers

- Total Revenue

- Average Order Value

These served as the foundation for executive reporting.



## Revenue Trend & Growth Analysis

Monthly revenue aggregation revealed structured growth cycles with noticeable expansion and contraction periods. Monthly growth rates showed volatility ranging from significant positive spikes to sharp declines, indicating strong seasonal behavior.

Revenue volatility was measured using standard deviation and coefficient of variation, which showed moderate variability (~16%). This suggests revenue stability despite growth fluctuations.



## Customer Behavior & Retention

Repeat purchase rate analysis revealed an unusually high behavioral consistency — 100% of customers were repeat purchasers. Cohort analysis confirmed near-perfect retention across observed periods.

This suggests the dataset resembles a B2B or subscription-style purchasing model rather than typical consumer ecommerce behavior.

Customer Lifetime Value (CLV) Customer lifetime value analysis showed balanced revenue contribution across the customer base, with moderate concentration among top spenders.


## RFM Segmentation

An RFM (Recency, Frequency, Monetary) model was implemented to classify customers into value tiers. Due to PostgreSQL percentile limitations, NTILE-based segmentation was implemented for robust production compatibility.

This allowed classification into:

- VIP customers

- High-value customers

- Standard customers

The analysis confirmed revenue distribution was not highly concentrated, indicating relatively uniform purchasing behavior.



## Presentation Layer & BI Integration

To support dashboard consumption, a presentation layer was created in dbt. This layer provided BI-ready views including:

- Executive dashboard summary

- Revenue trend view

- Customer segmentation view

- Growth and volatility metrics

The system was then connected directly to Power BI via PostgreSQL, where a structured executive dashboard was developed featuring :

- KPI cards

- Revenue trend line charts

- Growth rate analysis

- Revenue by country

- Customer segment distribution

This completed the full transformation from raw data to business insight visualization.



## Key Findings

The analysis revealed several important insights about the dataset :

- Extremely high customer retention

- Consistent high order frequency

- Moderate but controlled revenue volatility

- Stable geographic distribution

- Balanced revenue concentration

- While the dataset did not reflect traditional ecommerce churn dynamics, it provided strong modeling practice for star schema design, behavioral analytics, and metric engineering.


## Technologies Used

- PostgreSQL

- dbt Core (v1.11)

- SQL

- Power BI

- Python (environment setup)



## Conclusion

This project successfully delivered a full-stack BI analytics system using modern data tooling. From warehouse modeling to executive dashboard delivery, the workflow followed industry best practices in analytics engineering.

It represents a strong foundational implementation of a BI-focused data platform and provides a base architecture that can be extended into production-grade systems, automated pipelines, or advanced analytical modeling.
