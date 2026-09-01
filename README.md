# Sales Performance Scorecard Analysis (Power BI)

## Project Overview

This project demonstrates an end-to-end Power BI analytics solution built using multi-currency sales transaction data. The objective was to transform raw sales and billing records into actionable business intelligence through data cleansing, modeling, financial reconciliation, performance management, and executive dashboards.

The solution enables stakeholders to evaluate sales team performance, monitor target achievement, identify billing discrepancies, and analyze sales trends across products, countries, and regions.

---

## Business Requirements

The project addresses the following business objectives:

- Standardize sales transactions across multiple currencies
- Clean and normalize inconsistent order dates
- Reconcile sales transactions against billing records
- Track Actual vs Target performance for Sales Executives and Regional Managers
- Calculate incentive payouts based on achievement percentage
- Identify regional and product-level sales trends
- Analyze country-level contributions to revenue
- Provide interactive dashboards for business users

---

## Dataset

Data Sources:

- Sales_Data
- Bill Details
- Sales Team Target
- Reference Data

Special Handling:

- Order Number was not unique across the dataset.
- A Composite Key was created using:

Order Number + Order Date

This unique key was used for reconciliation and relationship management across datasets.

---

## Data Modeling

The solution follows a dimensional modeling approach.

### Fact Tables

- Sales_Data
- Bill Details

### Dimension Tables

- Date Table
- Sales Executive Dimension
- Year Dimension
- Sales Team Mapping

### Relationships

- Composite Order Key for transaction matching
- Sales Executive dimension for performance analysis
- Year dimension for target tracking
- Date dimension for time intelligence

---

## Key Features

### Performance Scorecard

- Actual Sales
- Target Sales
- Achievement Percentage
- Incentive Calculations
- Sales Executive Performance
- Regional Manager Performance

### Financial Reconciliation

- Sales vs Billed Amount
- Variance Analysis
- Mismatch Identification

### Sales Analytics

- Monthly Sales Trends
- Regional Contributions
- Top Performing Sales Executives
- Product Contribution Analysis
- Top Countries by Revenue

### Management Insights

- Manager-level Rollups
- Territory Performance
- Team Performance Monitoring

---

## DAX Measures Implemented

### Actual Sales

```DAX
Actual Sales =
SUM(Sales_Data[Total Sales (USD)])
```

### Target Sales

```DAX
Target Sales =
SUM('Sales Exec Target'[Target])
```

### Achievement %

```DAX
Achievement % =
DIVIDE([Actual Sales],[Target Sales])
```

### Incentive %

```DAX
Incentive % =
SWITCH(
    TRUE(),
    [Achievement %] >= 1, 0.05,
    [Achievement %] >= 0.8, 0.03,
    [Achievement %] >= 0.7, 0.01,
    0
)
```

### Incentive Amount

```DAX
Incentive Amount =
[Actual Sales] * [Incentive %]
```

---

## Dashboard Pages

### Team Performance

Features:

- Sales Executive Performance Matrix
- Top Performers by Sales
- Target vs Actual Analysis
- Incentive Tracking
- Year-wise Performance Comparison

### Regional Manager Dashboard

Features:

- Manager Scorecards
- Manager Achievement %
- Territory Analysis
- Monthly Sales Trends
- Team Aggregation Metrics

### Product & Geography Analysis

Features:

- Product Contribution
- Country-Level Performance
- Regional Distribution
- Product Revenue Analysis

---

## Dashboard Screenshots

### Team Performance Dashboard

Screenshots/team-performance.png

---

### Regional Manager Dashboard

Screenshots/rm-performance.png

---

### Product & Geography Dashboard

Screenshots/product-geography.png

---

## Skills Demonstrated

- Power BI
- DAX
- Power Query
- Data Modeling
- Star Schema Design
- KPI Development
- Dashboard Design
- Data Visualization
- Sales Analytics
- Financial Reconciliation
- Business Intelligence

---

## Key Learnings

- Designing a dimensional data model
- Building reusable DAX measures
- Managing many-to-many relationship challenges
- Creating performance scorecards
- Implementing time intelligence calculations
- Building executive-level dashboards

---

## Author

Shiv Sagar

Data Analyst | Power BI Developer
