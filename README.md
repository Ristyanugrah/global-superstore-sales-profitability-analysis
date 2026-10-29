# Beyond Revenue: A Data-Driven Analysis of Sales & Profitability in Global Superstore

**Final Project | Data Analytics & Business Intelligence**

An end-to-end retail analytics project focused on understanding sales performance, profitability, discount impact, product performance, customer segments, geographic markets, and shipping operations using Python and Power BI.

## Project Overview

High sales do not necessarily translate into optimal profitability. Retail businesses need to understand not only how much revenue they generate, but also which products, categories, customer segments, markets, and commercial strategies contribute to sustainable profit.

This project analyzes the Global Superstore dataset to investigate sales and profitability patterns, identify potential profit leakage, and develop data-driven recommendations for business decision-making.

The analysis covers transaction data from **January 2011 to December 2014** and examines business performance from both commercial and operational perspectives.

## Business Problem

The business operates across multiple products, categories, customer segments, and geographic markets. However, strong sales performance does not automatically guarantee healthy profit margins.

The main business question is:

**What factors influence sales and profitability, and where are the opportunities to improve overall business performance?**

The project investigates:

- Sales and profit trends over time.
- Product, category, and sub-category performance.
- Differences in profitability across markets and customer segments.
- The relationship between discount levels and profit margins.
- Products and sub-categories with low or negative profitability.
- Shipping duration and shipping-mode performance.

## Project Objectives

1. Analyze sales performance across time, markets, regions, products, categories, and customer segments.
2. Evaluate profitability using total profit and profit margin.
3. Investigate the relationship between discount strategies and profitability.
4. Identify potential profit leakage and underperforming business areas.
5. Translate analytical findings into actionable business recommendations.
6. Prepare analytical outputs that can support an interactive Power BI dashboard.

## Dataset Overview

The project uses the Global Superstore retail transaction dataset.

| Attribute | Description |
|---|---|
| Initial records | 51,290 rows |
| Original variables | 27 columns |
| Transaction period | January 2011 – December 2014 |
| Data type | Retail transaction data |
| Business domains | Sales, profit, customers, products, markets, discounts, and shipping |

### Key Variables

| Variable | Description |
|---|---|
| `Order.ID` | Order identifier |
| `Order.Date` | Date the order was placed |
| `Ship.Date` | Date the order was shipped |
| `Customer.ID` | Customer identifier |
| `Product.ID` | Product identifier |
| `Category` | Main product category |
| `Sub.Category` | Product sub-category |
| `Sales` | Transaction sales value |
| `Profit` | Profit or loss associated with a transaction |
| `Quantity` | Number of units sold |
| `Discount` | Discount applied to the transaction |
| `Shipping.Cost` | Shipping cost recorded in the dataset |
| `Market` | Geographic market |
| `Region` | Geographic region |
| `Segment` | Customer segment |
| `Ship.Mode` | Shipping method |

## Tools and Technologies

- **Python** — Data analysis and exploratory data analysis.
- **Pandas** — Data manipulation, aggregation, and transformation.
- **NumPy** — Numerical operations and derived metrics.
- **Matplotlib** — Data visualization.
- **Seaborn** — Statistical visualization.
- **Google Colab** — Notebook development and execution.
- **Power BI** — Business intelligence dashboard development.

## Analytical Workflow

The project follows an end-to-end data analytics workflow:

1. **Data Understanding** — Inspect dataset dimensions, data types, variables, business entities, and transaction dates.
2. **Data Quality Check** — Examine missing values, duplicate records, identifiers, numerical ranges, discounts, date consistency, shipping duration, and outliers.
3. **Data Preparation and Manipulation** — Convert date fields, create analytical variables, and aggregate data at different business levels.
4. **Exploratory Data Analysis (EDA)** — Investigate distributions, trends, category performance, product performance, discounts, markets, customer segments, and shipping modes.
5. **Business Case Analysis** — Investigate potential profit leakage and identify areas requiring further business attention.
6. **Dashboard Development** — Use analytical outputs to support business intelligence reporting in Power BI.
7. **Key Insights and Recommendations** — Translate findings into practical actions for improving profitability.

## Data Quality Assessment

The initial data quality checks produced the following results:

- No missing values were detected in the original dataset.
- No duplicate rows were detected.
- `Row.ID` was validated as a unique identifier at the record level.
- `Order.ID`, `Customer.ID`, and `Product.ID` contain repeated values because orders, customers, and products can appear across multiple transaction records.
- `Order.Date` and `Ship.Date` were converted to datetime format.
- No shipping dates earlier than their corresponding order dates were detected.
- The observed shipping duration ranged from 0 to 7 days.
- Discount values ranged from 0% to 85%, with no negative discounts or values exceeding 100%.
- Sales and profit outliers were identified for further investigation rather than automatically removed.

The IQR-based checks identified 5,655 potential sales outliers (11.03% of records) and 9,755 potential profit outliers (19.02%). These observations were retained during the initial assessment because extreme values can represent legitimate business transactions.

## Feature Engineering and Data Transformation

Several derived variables were created to support deeper analysis.

| Derived variable | Purpose |
|---|---|
| `Shipping.Days` | Measures elapsed calendar days between order and shipping dates |
| `Profit.Margin` | Measures profit relative to sales |
| `Order.Year` | Supports annual performance analysis |
| `Order.Month` | Supports monthly trend analysis |
| `Order.Month.Name` | Provides readable month labels |
| `Order.Year.Month` | Supports monthly time-series analysis |
| `Discount.Band` | Groups discounts into analytical ranges |
| `Profitability.Status` | Classifies transactions as profitable or loss-making |

The discount bands are defined as:

- `0%`
- `1–10%`
- `11–20%`
- `21–30%`
- `31–40%`
- `>40%`

The notebook also creates aggregated analytical tables at order, product, category, sub-category, market, customer-segment, and shipping-mode levels.

After feature engineering, the working dataset contains **51,290 rows and 35 columns**.

## Exploratory Data Analysis

### 1. Sales and Profit Trends

- Examine annual sales and profit performance from 2011 through 2014.
- Calculate year-over-year sales and profit growth.
- Compare sales growth with profit growth and profit margin.
- Explore monthly trends to identify changes in business performance.

### 2. Category and Sub-Category Performance

- Compare sales, profit, quantity, and profit margins across product categories.
- Identify high-performing and underperforming sub-categories.
- Investigate sub-categories with negative total profit.
- Evaluate whether high sales consistently translate into stronger profitability.

### 3. Product-Level Performance

- Rank products by sales and profit.
- Identify loss-making products.
- Classify products into four performance groups using median sales and profit thresholds:
  - High Sales – High Profit
  - High Sales – Low Profit
  - Low Sales – High Profit
  - Low Sales – Low Profit

This classification helps distinguish products that drive revenue from those that contribute meaningfully to profit.

### 4. Discount and Profitability

- Compare sales, profit, and profit margin across discount bands.
- Examine the relationship between discount levels and transaction profitability.
- Investigate category and discount combinations associated with negative profit.
- Identify discount policies that may require further evaluation.

The analysis is intended to identify associations and potential risk areas, rather than assume that discounts alone cause lower profitability.

### 5. Market and Customer Segment Analysis

- Compare sales, profit, order volume, and customer counts across markets.
- Evaluate profit margins by geographic market.
- Compare commercial performance across customer segments.
- Identify markets or segments that may warrant further investigation.

### 6. Shipping Performance

- Calculate average shipping duration by shipping mode.
- Compare sales, profit, shipping costs, and profit margins across shipping modes.
- Explore how operational performance differs between shipping methods.

## Key Business Metrics

The notebook calculates the following metrics:

- Total Sales
- Total Profit
- Overall Profit Margin
- Total Orders
- Total Customers
- Total Quantity Sold
- Average Discount
- Total Shipping Cost
- Average Order Value

The initial analysis reports an **overall profit margin of approximately 11.61%**.

The notebook also reports an average transaction-level profit margin of approximately **4.72%**. These figures use different aggregation approaches: the overall margin is calculated as total profit divided by total sales, whereas the transaction-level figure is the unweighted mean of individual row margins. They should not be interpreted as the same metric.

## Business Case Analysis

The business case focuses on investigating potential profit leakage and opportunities to improve profitability.

### Product Profitability

Identify products that generate substantial sales but relatively low or negative profit. Review their pricing, discount levels, product costs, and sales strategies before deciding on corrective actions.

### Sub-Category Profitability

Compare sub-category sales and profit to locate areas where revenue contribution and profitability diverge.

### Discount Risk

Examine discount bands and category-level discount patterns to identify combinations associated with weak or negative profit. Any discount policy changes should be tested against commercial objectives and customer response.

### Market Profitability

Compare market-level sales, profit, order volume, customer counts, and average discount to identify markets that may offer opportunities for profitability improvement.

### Shipping Operations

Compare shipping duration, shipping costs, and profit margins by shipping mode to understand operational trade-offs.

## Strategic Recommendations

Based on the analytical framework, the following actions are proposed for evaluation:

1. **Prioritize profitable growth.** Evaluate products using both sales contribution and profit performance rather than sales rankings alone.
2. **Review loss-making products and sub-categories.** Investigate pricing, discounting, and cost structures before making decisions about product assortment.
3. **Strengthen discount governance.** Establish category- and product-level profitability checks before approving large discounts.
4. **Tailor market strategies.** Adapt commercial initiatives to differences in market-level sales and profitability.
5. **Monitor shipping efficiency.** Compare shipping duration and shipping costs across shipping modes while considering customer requirements.
6. **Build a profitability-focused dashboard.** Track sales, profit, profit margin, discount, product performance, and shipping metrics together.
7. **Validate findings before implementation.** Confirm important observations using detailed transaction-level analysis and business context.

These are proposed actions for investigation and validation. Their business impact should be measured after implementation rather than assumed in advance.

## Data Limitations and Considerations

- The dataset represents historical transactions from 2011–2014 and does not establish current market conditions.
- Outlier detection identifies unusual observations but does not establish that they are data errors.
- The transaction-level mean profit margin differs from the overall weighted profit margin.
- The derived `Shipping.Days` variable measures the elapsed time between order and ship dates. It should not automatically be interpreted as the complete delivery time to the customer.
- Observed relationships between discounts, shipping, sales, and profit do not by themselves establish causation.
- Specific product, market, and discount findings should be supported by the corresponding analytical outputs before being used for business decisions.

## Repository Structure

A suggested repository structure is:

```text
global-superstore-sales-profitability-analysis/
├── README.md
├── global_superstore_sales_profitability_analysis.ipynb
├── data/
│   └── superstore.csv
├── outputs/
│   └── figures/
└── dashboard/
    └── power_bi_dashboard.pbix
```

The `data/`, `outputs/`, and `dashboard/` folders are suggested organizational structures. Include the relevant files only when they are available and appropriate to share.

## How to Run the Project

1. Clone or download this repository.
2. Open the notebook in Google Colab or Jupyter Notebook.
3. Install the required Python libraries if they are not already available.
4. Place `superstore.csv` in the expected working directory or update the dataset path in the notebook.
5. Run the notebook cells sequentially, from data loading through the analysis.
6. Open the Power BI dashboard file if it is included in the repository.

### Python Libraries

```bash
pip install pandas numpy matplotlib seaborn
```

## Project Outcome

This project demonstrates an end-to-end approach to retail data analytics, from data quality assessment and feature engineering to exploratory analysis and business case development.

The primary objective is to support better business decisions by evaluating profitability alongside revenue, investigating potential profit leakage, and identifying areas for further operational and commercial improvement.

## Author

**Risty Anugrah Dwi Septiana**  
Data Analyst | Business Intelligence Enthusiast

- **GitHub:** [Ristyanugrah](https://github.com/Ristyanugrah)
- **Portfolio Repository:** [Data Analytics Portfolio](https://github.com/Ristyanugrah/data-analytics-portfolio)
- **Portfolio Website:** [risty-portfolio.vercel.app](https://risty-portfolio.vercel.app/)

---

*This project was developed for data analytics and business intelligence portfolio purposes.*
