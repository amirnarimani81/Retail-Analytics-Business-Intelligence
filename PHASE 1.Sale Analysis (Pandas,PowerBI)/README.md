<h1 align="center"> Regional Sales Analytics & Business Intelligence (Python + Power BI)</h1>

<p align="center">

An end-to-end data analytics project that transforms raw retail sales data into actionable business insights using Python, Pandas, Matplotlib, and Power BI.

</p>


---

<h2> Power BI Dashboard</h2>

<p align="center">
<img src="Assets/dashboard_preview.png" width="950">
</p>

The interactive Power BI dashboard summarizes business performance through executive KPIs, sales trends, customer analytics, product performance, and regional insights.

---

# Project Overview

This project demonstrates a complete end-to-end data analytics workflow, beginning with raw business data and ending with an executive-level Power BI dashboard.

The objective is to convert fragmented retail transaction data into meaningful business intelligence that supports strategic decision-making.

The project covers every stage of the analytics lifecycle:

- Business understanding
- Data integration
- Data cleaning
- Feature engineering
- Exploratory Data Analysis (EDA)
- Business insight generation
- Interactive dashboard development

---

# Business Problem

Although company revenue has continued to increase, profit growth has remained inconsistent across products, customers, and geographic regions.

Management requires a comprehensive analysis to understand:

- What drives revenue growth?
- Which products generate the highest profit?
- Which customers create the greatest business value?
- How does profitability vary across regions?
- What seasonal trends influence demand?
- Which operational issues reduce profitability?

The ultimate goal is to support executive decision-making with reliable, data-driven insights.

---

# Project Workflow

```
Raw Excel Files
        │
        ▼
Data Integration
        │
        ▼
Data Cleaning
        │
        ▼
Feature Engineering
        │
        ▼
Exploratory Data Analysis
        │
        ▼
Business Insights
        │
        ▼
Power BI Dashboard
        │
        ▼
Strategic Recommendations
```

---

# Dataset

The analysis integrates multiple business datasets into one analytical dataset.

### Data Sources

- Sales Transactions
- Customer Information
- Product Information
- State Mapping
- Regional Mapping
- Budget Data

These datasets were merged using Python to create a unified data model suitable for analysis.

---

# Data Wrangling & Integration (Python)

Before analysis, the raw datasets required extensive preprocessing.

### Data Preparation

✔ Integrated multiple Excel worksheets
✔ Merged customer, product, region, and budget tables
✔ Removed unnecessary columns
✔ Renamed variables using Python naming conventions
✔ Converted date fields into datetie format
✔ Standardized categorical variables
✔ Validated numeric fields
✔ Prepared a clean analytical dataset for Power BI

Example:

```python
cols_to_keep = [
    'ordernumber',
    'orderdate',
    'customer names',
    'channel',
    'product name',
    'order quantity',
    'unit price',
    'line total',
    'total unit cost',
    'state_code',
    'state',
    'region',
    'latitude',
    'longitude',
    '2017 budgets']

df = df[cols_to_keep]

df = df.rename(columns={
    'ordernumber':'order_number',
    'orderdate':'order_date',
    'customer names':'customer_name',
    'product name':'product_name',
    'order quantity':'quantity',
    'unit price':'unit_price',
    'line total':'revenue',
    'total unit cost':'cost',
    'state_code':'state',
    'state':'state_name',
    'region':'us_region',
    'latitude':'lat',
    'longitude':'lon',
    '2017 budgets':'budget'})
```

---

# Data Quality Assessment

Python was used to assess and improve data quality before analysis.

The following validation steps were completed:

- Missing value detection
- Duplicate record verification
- Date validation
- Numeric type conversion
- Category standardization
- Outlier identification
- Column consistency checks

This process ensured a reliable dataset for statistical analysis and visualization.

---

# Feature Engineering

Additional business metrics were created to support deeper analysis.

Examples include:

```python
df["profit"] = df["revenue"] - df["cost"]

df["profit_margin_pct"] = (
    df["profit"] / df["revenue"]
) * 100

df["order_month"] = df["order_date"].dt.month_name()

df["order_year"] = df["order_date"].dt.year
```

Additional KPIs:

- Profit
- Profit Margin
- Monthly Revenue
- Annual Revenue
- Average Order Value
- Customer Revenue
- Regional Revenue
- Budget Variance

---


<h2>Exploratory Data Analysis (EDA) Insights</h2>
The exploratory analysis was performed to understand revenue behavior, seasonal patterns, product performance, customer purchasing behavior, pricing relationships, and sales channel contribution.
<br><br>
<hr>


<h3>1. Monthly Sales Trend Over Time</h3>

<img src="Assets/EDA/monthly_sales_trend.png" width="800">


<b>Business Issue:</b><br>
The company needs to understand whether revenue growth follows a stable pattern or is affected by seasonal fluctuations and unexpected changes.
<br><br>

<b>EDA Result:</b><br>
Monthly revenue remains relatively stable between $24M and $26M, showing recurring seasonal behavior with higher sales during late spring and early summer and lower performance during January.
<br><br>

<b>Business Insight:</b><br>
The stable seasonal pattern indicates predictable customer demand; however, the significant revenue decline observed in early 2017 requires further investigation to identify the underlying cause.
<br><br>
<hr>


<h3>2. Monthly Sales Trend (All Years Combined)</h3>

<img src="Assets/EDA/monthly_sales_all_years.png" width="800">


<b>Business Issue:</b><br>
Understanding monthly purchasing behavior helps identify high-demand and low-demand periods.
<br><br>

<b>EDA Result:</b><br>
January shows strong revenue performance (~$99M), followed by a decline toward April (~$95M). Sales recover during May and June and reach another peak around August (~$102M).
<br><br>

<b>Business Insight:</b><br>
The business follows a clear seasonal cycle consisting of a post-New Year increase, spring slowdown, and mid-year recovery.
<br><br>
<hr>


<h3>3. Top 10 Products by Revenue (in Millions)</h3>

<img src="Assets/EDA/top_products_revenue.png" width="800">


<b>Business Issue:</b><br>
Management needs to identify which products generate the largest contribution to total revenue.
<br><br>

<b>EDA Result:</b><br>
Products 26 and 25 are the strongest revenue contributors, generating approximately $118M and $110M respectively. Other products contribute significantly lower revenue.
<br><br>

<b>Business Insight:</b><br>
Revenue generation is concentrated among a small number of products, highlighting the importance of monitoring high-performing products while improving weaker product categories.
<br><br>
<hr>


<h3>4. Top 10 Products by Average Profit Margin</h3>

<img src="Assets/EDA/top_profit_margin_products.png" width="800">


<b>Business Issue:</b><br>
High revenue does not always represent high profitability; therefore, products must also be evaluated based on margin performance.
<br><br>

<b>EDA Result:</b><br>
Profit margin analysis identifies products generating stronger profitability independent of sales volume.
<br><br>

<b>Business Insight:</b><br>
The analysis separates revenue leaders from profitability leaders, helping identify products that create stronger financial value.
<br><br>
<hr>


<h3>5. Sales by Channel</h3>

<img src="Assets/EDA/sales_channel.png" width="700">


<b>Business Issue:</b><br>
The company needs to understand which sales channels contribute most to revenue.
<br><br>

<b>EDA Result:</b><br>
Wholesale contributes approximately 54% of total revenue, distributors contribute nearly 31%, and exports contribute approximately 15%.
<br><br>

<b>Business Insight:</b><br>
Revenue is highly dependent on wholesale and distribution channels, indicating potential exposure to channel concentration risk.
<br><br>
<hr>


<h3>6. Average Order Value (AOV) Distribution</h3>

<img src="Assets/EDA/aov_distribution.png" width="800">


<b>Business Issue:</b><br>
Understanding transaction size helps evaluate customer purchasing behavior.
<br><br>

<b>EDA Result:</b><br>
The AOV distribution is right-skewed, with most orders concentrated between approximately $20K and $120K, while a small number of large transactions reach $400K–$500K.
<br><br>

<b>Business Insight:</b><br>
A limited number of high-value transactions contribute significantly to revenue, showing the importance of maintaining strong relationships with large customers.
<br><br>
<hr>


<h3>7. Profit Margin % vs. Unit Price</h3>

<img src="Assets/EDA/profit_margin_vs_unit_price.png" width="800">


<b>Business Issue:</b><br>
The company needs to determine whether higher-priced products generate better profitability.
<br><br>

<b>EDA Result:</b><br>
No strong relationship was observed between unit price and profit margin percentage.

<br><br>
<b>Business Insight:</b><br>
Higher-priced products do not necessarily produce higher margins, indicating that pricing strategy and cost structure influence profitability.
<br><br>
<hr>


<h3>8. Unit Price Distribution per Product</h3>

<img src="Assets/EDA/unit_price_distribution_product.png" width="800">


<b>Business Issue:</b><br>
Product pricing consistency needs to be evaluated across the portfolio.
<br><br>

<b>EDA Result:</b><br>
Products show different pricing distributions, with some products having wider price variation.
<br><br>

<b>Business Insight:</b><br>
Products with large pricing variation may require additional evaluation of pricing strategy and market positioning.
<br><br>
<hr>


### Key Findings

- Revenue and Profit show a very strong positive relationship.
- Unit Price strongly influences both Revenue and Profit.
- Quantity has a comparatively weaker relationship with profitability.

These findings indicate that pricing strategy plays a more significant role than sales volume in driving business performance.

---

# Power BI Dashboard

The cleaned analytical dataset was imported into Power BI to build an interactive executive dashboard.

Dashboard pages include:

- Executive Overview
- Product Analytics
- Customer Analytics


<img src="Assets/EDA/monthly_sales_all_years.png" width="800">

---

# Business Recommendations

Based on the analysis, several strategic recommendations were identified:

- Investigate the early-2017 revenue decline
- Expand export operations to diversify revenue
- Reduce dependence on wholesale channels
- Optimize pricing for mid-performing products
- Improve retention of high-value customers
- Incorporate seasonal demand into inventory planning
- Monitor pricing consistency across regions

---

# Tools & Technologies

### Programming

- Python
- Pandas
- NumPy

### Visualization

- Matplotlib
- Power BI

### Data Processing

- Excel
- CSV
- Jupyter Notebook

---

# Skills Demonstrated

- Data Cleaning
- Data Wrangling
- Data Integration
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Statistical Analysis
- Business Analytics
- Data Visualization
- Dashboard Development
- KPI Design
- Business Storytelling
- Executive Reporting

---

# Final Outcome

This project delivered an end-to-end Exploratory Data Analysis (EDA) and interactive Power BI Business Intelligence solution that transformed raw retail transaction data into actionable insights.

The analysis uncovered key business patterns, including seasonal sales trends, SKU performance, channel contribution, customer purchasing behavior, pricing dynamics, and regional sales opportunities.

The generated insights support smarter business decisions by improving sales forecasting, inventory planning, store and warehouse preparation, product strategy, and operational efficiency based on historical demand patterns.

The interactive Power BI dashboard enables stakeholders to self-serve real-time business analysis, monitor key performance indicators, and explore trends without relying on manual reporting.

The developed analytical framework provides a scalable foundation for integrating new datasets and extending future analytics use cases to support continuous data-driven decision-making.