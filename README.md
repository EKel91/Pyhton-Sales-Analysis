#Sales Performance Analysis — Python

**Tools:** Python, pandas, matplotlib, seaborn  
**Dataset:** Superstore Sales Data


# Pyhton-Sales-Analysis
Sales Performance Analysis (Python)

**Project Overview**

* Objective:
To analyze sales performance using Python in order to understand business trends, identify key revenue drivers, and evaluate growth over time.

Tools Used:<br>
* Python
* pandas (data manipulation)
* matplotlib & seaborn (visualization)
* Jupyter Notebook

Dataset:<br>
Superstore sales data containing order details, products, regions, categories, and sales values.

**Business Questions**

This analysis answers the following questions:
* How are sales trending over time?
* Which regions generate the highest sales?
* What products contribute most to revenue?
* How is sales growth changing month-over-month?

**Data Preparation**

Steps Taken:
* Loaded CSV data using pandas
* Converted date columns to datetime
* Created derived time fields (Year, Month, YearMonth)
* Aggregated data using groupby

**Sample Code**
```python
  import pandas as pd
  df = pd.read_csv("Superstore.csv",encoding="latin1")
  df["Order Date"] = pd.to_datetime(df["Order Date"])
  df["YearMonth"] = df["Order Date"].dt.to_period("M")
```
**Analysis & Visualizations**

A. Monthly Sales Thrend<br>
Goal: Understand the overall business performance overtime
method:
* Grouped Sales by Month
* Visualize using a line chart
```python
Monthly_Sales = df.groupby("YearMonth" as_index=False)["Sales"].sum()
```
Insight:<br>
Sales fluctuate month-to-month, with noticeable peaks toward later periods, indicating seasonal or growth-driven increases.

B. Sales by Region<br>
Goal: Identify top-performing regions
```python
region_sales = df.groupby("Region" as_index=False)["Sales"].sum()
```
Insight:<br>
The West and East regions generate the highest revenue, while the South region underperforms, suggesting potential growth opportunities.

C. Top5 products by Sales<br>
Goal: Identify key revenue drivers.
```python
top5 = (df.groupby("Product Name", as_index=False).["Sales"].sum()
      .sort_values(by="Sales",ascending=False).head(5))
```
Insight:<br>
A small number of products contribute disproportionately to total sales, following the Pareto (80/20) principle.

D. Month-over-Month (MoM) Growth<br>
Goal: Measure business momentum<br>
```python
Monthly_Sales["Month_over_Month"] = Monthly_Sales["Sales"].pct_change()
```
Insight:<br>
Growth rates vary significantly, indicating periods of expansion and contraction. This highlights the importance of monitoring trends, not just totals.

**Key Insights Summary<br>**
* Sales show an overall upward trend with seasonal fluctuations<br>
* Regional performance varies significantly<br>
* Revenue is driven by a small set of top products<br>
* Month-over-month growth is volatile, requiring close monitoring<br>

**Business Recommendations**<br>
* Focus marketing and inventory efforts on top-performing products<br>
* Investigate underperforming regions for improvement opportunities<br>
* Use MoM growth tracking for early detection of performance changes<br>

**Skills Demonstrated**<br>
✔ Data cleaning & transformation<br>
✔ SQL-style analysis using pandas<br>
✔ Time series analysis<br>
✔ Data visualization<br>
✔ Business insight generation<br>


