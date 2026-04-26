# Customer Shopping Behaviour Analysis

A Databricks notebook that analyses customer shopping behaviour using **pandas**, **PySpark**, and **Databricks SQL**. The project covers data cleaning, feature engineering, Delta Lake storage, and a series of SQL queries to extract business insights.

---

## Project Structure

```
customer-shopping-analysis/
├── customer_shopping_behavior.py   # Main analysis script
├── README.md
```

---

## Dataset

**File:** `customer_shopping_behavior.csv`

The dataset contains customer transaction records including:

- Customer demographics (age, gender)
- Purchase details (item, category, amount)
- Shopping behaviour (frequency, subscription status, discounts)
- Product feedback (review rating)
- Shipping information

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python / pandas | Data loading, cleaning, feature engineering |
| PySpark | Converting pandas DataFrame to Spark |
| Databricks Delta Lake | Storing data as a managed Delta table |
| Databricks SQL | Business analysis queries |

---

## Data Processing Steps

### 1. Cleaning
- Fills missing `Review Rating` values with the **category-level median**
- Standardises column names to lowercase with underscores

### 2. Feature Engineering
- **`age_group`** — Quartile-based binning into `Young Adult`, `Adult`, `Middle-aged`, `Senior`
- **`purchase_frequency_days`** — Maps frequency labels (e.g. `Weekly`, `Monthly`) to numeric day values

### 3. Delta Table
- Converts the cleaned pandas DataFrame to a Spark DataFrame
- Writes to a managed Delta table: `customer_shopping_behavior`

---

## SQL Analyses

| Analysis | Description |
|---|---|
| Revenue by gender | Total spend split by Male/Female |
| Discounted high-value customers | Customers using discounts who spent ≥ average |
| Top 5 rated products | Items ranked by average review rating |
| Shipping type vs spend | Avg purchase amount for Standard vs Express |
| Subscription status breakdown | Customer count, avg & total revenue by subscription |
| Discount rate by item | % of orders with a discount per product |
| Customer segmentation | New / Returning / Loyal based on purchase history |
| Top 3 items per category | Best-selling items per category using window functions |
| Repeat buyers by subscription | Customers with more than 5 previous purchases |
| Revenue by age group | Total revenue across the four age bands |

---

## Getting Started

### Prerequisites
- Databricks workspace with a running cluster
- CSV file uploaded to `/Workspace/customer_shopping_behavior.csv`

### Running the Notebook
1. Upload `customer_shopping_behavior.py` to your Databricks workspace
2. Attach it to a cluster
3. Run all cells in order

---

## Notes

- The `%sql` magic commands are Databricks-specific and will not run in a standard Jupyter environment
- The Delta table is written in **overwrite** mode — re-running the script will replace existing data

---

## License

This project is for educational and analytical purposes.
