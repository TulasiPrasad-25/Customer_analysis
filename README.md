# 🛍️ Customer Shopping Behavior Analysis

A full-stack data analytics project that explores customer purchasing patterns using Python, SQL, and Power BI — built to surface actionable business insights from 3,900 retail transactions.

---

## 📌 Business Problem

A retail company wants to understand how its customers shop in order to improve sales, customer satisfaction, and long-term loyalty. This project answers the central question:

> *"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

---

## 📁 Project Structure

```
customer-shopping-behavior-analysis/
│
├── customer_shopping_behavior.csv          # Raw dataset (3,900 rows × 18 columns)
├── Customer_Shopping_Behavior_Analysis.ipynb  # Python EDA + preprocessing + DB integration
├── customer_behavior_sql_queries.sql       # 10 business SQL queries (PostgreSQL)
├── customer_behavior_dashboard.pbix        # Interactive Power BI dashboard
├── Customer_Shopping_Behavior_Analysis.pdf # Project report with findings
└── README.md
```

---

## 📊 Dataset Overview

| Property | Details |
|---|---|
| Rows | 3,900 |
| Columns | 18 |
| Missing Values | 37 (Review Rating column) |

**Features include:**
- **Demographics** — Age, Gender, Location, Subscription Status
- **Purchase Details** — Item Purchased, Category, Purchase Amount (USD), Season, Size, Color
- **Behavior** — Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type, Payment Method

---

## 🐍 Python — Data Preparation & EDA

**Notebook:** `Customer_Shopping_Behavior_Analysis.ipynb`

Steps performed:

1. **Data Loading** — Imported dataset using `pandas`
2. **Initial Exploration** — `df.info()`, `df.describe()` for structure and statistics
3. **Missing Data Handling** — Imputed 37 null values in `Review Rating` using the median rating per product category
4. **Column Standardization** — Renamed all columns to snake_case; aliased `purchase_amount_(usd)` → `purchase_amount`
5. **Feature Engineering**
   - `age_group` — quartile-based binning into Young Adult, Adult, Middle-aged, Senior
   - `purchase_frequency_days` — mapped frequency labels (Weekly, Monthly, etc.) to integer day values
6. **Redundancy Check** — Verified `discount_applied` and `promo_code_used` were identical; dropped `promo_code_used`
7. **Database Integration** — Loaded cleaned DataFrame into PostgreSQL via SQLAlchemy (MySQL and MS SQL Server alternatives included)

**Libraries:** `pandas`, `sqlalchemy`, `psycopg2-binary`

---

## 🗄️ SQL — Business Analysis

**File:** `customer_behavior_sql_queries.sql` | **Database:** PostgreSQL

| # | Query | Key Finding |
|---|---|---|
| Q1 | Revenue by Gender | Male: $157,890 · Female: $75,191 |
| Q2 | High-Spending Discount Users | 839 customers used discounts yet spent above average |
| Q3 | Top 5 Products by Rating | Gloves (3.86), Sandals (3.84), Boots (3.82) |
| Q4 | Shipping Type Comparison | Express avg: $60.48 · Standard avg: $58.46 |
| Q5 | Subscribers vs. Non-Subscribers | Similar avg spend (~$59); non-subscribers dominate volume (2,847 vs 1,053) |
| Q6 | Discount-Dependent Products | Hat (50%), Sneakers (49.66%), Coat (49.07%) |
| Q7 | Customer Segmentation | Loyal: 3,116 · Returning: 701 · New: 83 |
| Q8 | Top 3 Products per Category | Jewelry, Blouse, Sandals, Jacket lead their categories |
| Q9 | Repeat Buyers & Subscriptions | 2,518 repeat buyers are non-subscribers vs 958 subscribers |
| Q10 | Revenue by Age Group | Young Adult: $62,143 · Middle-aged: $59,197 · Adult: $55,978 · Senior: $55,763 |

**SQL techniques used:** Aggregate functions, subqueries, CTEs, window functions (`ROW_NUMBER OVER PARTITION BY`), `CASE WHEN` segmentation, conditional aggregation.

---

## 📈 Power BI Dashboard

**File:** `customer_behavior_dashboard.pbix`

The interactive dashboard includes:

- **KPI Cards** — Total Customers (3.9K), Average Purchase Amount ($59.76), Average Review Rating (3.75)
- **Donut Chart** — Customer distribution by Subscription Status (27% Yes / 73% No)
- **Bar Charts** — Revenue and Sales by Category, Revenue and Sales by Age Group
- **Filters/Slicers** — Subscription Status, Gender, Category, Shipping Type

---

## 💡 Business Recommendations

| Area | Recommendation |
|---|---|
| Subscriptions | Promote exclusive perks to convert the 73% non-subscriber base |
| Loyalty Programs | Reward repeat buyers (3,116 loyal customers) to deepen engagement |
| Discount Strategy | Review discount policy on Hat, Sneakers, and Coat — high dependency may erode margins |
| Product Campaigns | Spotlight top-rated products (Gloves, Sandals, Boots) in marketing |
| Targeted Marketing | Prioritize Young Adult and Middle-aged segments for highest revenue ROI |
| Shipping | Leverage Express shipping association with higher spend in upsell flows |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas sqlalchemy psycopg2-binary
```

### Run the Notebook
```bash
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

### Load Data into PostgreSQL
Update the connection credentials in the notebook's DB Integration cell, then run it to push the cleaned DataFrame into your local PostgreSQL instance.

### Run SQL Queries
Open `customer_behavior_sql_queries.sql` in pgAdmin or any PostgreSQL client and execute against the `customer_behavior` database.

### View Dashboard
Open `customer_behavior_dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python (pandas) | Data cleaning & feature engineering |
| PostgreSQL | Structured query analysis |
| SQLAlchemy | Python ↔ database integration |
| Power BI | Interactive dashboard & visualization |
| Jupyter Notebook | EDA and reproducible analysis |

---

## 👤 Author

**Tulasi Prasad**  
B.Tech CSE (AI & Data Science)
📧 tulasiprasad2526@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/tulasi-prasad-077350284) · [GitHub](https://github.com/TulasiPrasad-25)
