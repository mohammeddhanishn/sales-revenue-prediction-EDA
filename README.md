# Sales Performance Analysis with Python

## 1. Business Question
Where does our 2026 revenue really come from, and which products, sales channels, regions, customer groups and months should the business focus on to grow it?

## 2. Dataset
- **Name:** Sales Orders 2026 (`Data (2).xlsx`, provided by the program)
- **Raw file:** `data/raw/sales_data_raw.xlsx` (untouched). **Cleaned file:** `data/cleaned/sales_data_cleaned.csv`
- **Size:** 2,000 rows x 12 columns (cleaned file has 20 columns after feature engineering)
- **Period:** 1 Jan 2026 to 31 Dec 2026

| Column | Description |
|---|---|
| Order ID, Date | Order number and order date |
| Region | North, South, East, West, Central |
| Sales Channel | Online, Retail Store, Marketplace, Corporate Sales |
| Customer Type | New or Returning |
| Product Category, Product | 6 categories, 28 products |
| Salesperson | 15 sales staff |
| Quantity, Unit Price, Discount | Units, price per unit, discount fraction (0 to 0.20) |
| Revenue | Net order value after discount |

## 3. Tools Used
Python 3, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook.

## 4. Steps Followed
1. Loaded the Excel file and inspected shape, data types and summary statistics.
2. **Cleaned** the data: the `Date` column mixed Excel dates with text (`M/D/YYYY`); all were converted to one datetime type. Checked missing values (none), duplicates (none) and text consistency. Confirmed `Revenue = Quantity x Unit Price x (1 - Discount)` within 7 cents.
3. Checked outliers with the IQR rule. **Kept them**, because high-value orders are genuine Computer sales.
4. Created features: month, quarter, weekday, gross sales, discount amount, discount band.
5. Ran EDA: KPIs, groupby summaries by category, channel, region, customer type and salesperson, and correlations.
6. Built 9 charts with titles and labels, then wrote insights and recommendations.

## 5. Key Insights
1. **Computers carry the business:** 16.9% of orders but 59.5% of revenue. The Gaming Laptop alone is about 19% of revenue.
2. **Accessories and Office Supplies** are 37% of orders but only 3.0% of revenue.
3. **Revenue is concentrated:** the top 10% of orders produce 43.9% of revenue.
4. **Corporate Sales has the highest average order value** (about 3,045, nearly double Online) from only 333 orders. Online leads by order count; Marketplace is weakest.
5. **Regional gaps come from order count, not order size.** West is last on revenue but its average order value is higher than North's.
6. **Returning customers** give 68.4% of revenue and spend about 14% more per order than new customers.
7. **Seasonality:** peak in June (about 374K), low in February (about 219K), strong November and December. First-half and second-half revenue are almost equal, so there is no growth trend.
8. **Discounts show no clear volume benefit:** 281K given away (7.5% of gross sales), about 61% of it on Computers, and discount has a 0.04 correlation with quantity.
9. **Team gaps are mostly order count** (Mei Tan leads, Ben Ho is lowest).

**Recommendations:** protect Computer sales, grow Corporate Sales with bundles, test lower discounts on Computers, drive more orders in West and Marketplace, invest in retention, and plan for the February and July dips.

## 6. Screenshots or Output
Charts are saved in `images/`:

| | |
|---|---|
| ![Revenue by category](images/01_revenue_by_category.png) | ![Monthly revenue](images/02_monthly_revenue.png) |
| ![Channel](images/03_channel.png) | ![Region and customer](images/04_region_customer.png) |
| ![Order value](images/05_order_value_boxplot.png) | ![Discount](images/06_discount.png) |
| ![Correlation](images/07_correlation.png) | ![Salesperson](images/08_salesperson.png) |
| ![Heatmap](images/09_region_category_heatmap.png) | |

## 7. How to Run or Open
```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
jupyter notebook Sales_Analysis.ipynb
```
Run from the repository root so the relative `data/` paths work. Outputs are already saved in the notebook.

## 8. Author
Your name, Your batch
