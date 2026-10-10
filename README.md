# Olist Brazilian E-Commerce: Exploratory Data Analysis

A beginner-friendly EDA project on the Brazilian E-Commerce (Olist) dataset. The project covers data merging, cleaning, feature engineering and exploratory analysis using Python.

## Dataset

Source: [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

Three tables were used:

- `olist_customers_dataset.csv`
- `olist_orders_dataset.csv`
- `olist_order_payments_dataset.csv`

## Tools Used

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook

## Project Files

| File | Description |
|---|---|
| `01_Brazilian_Olist_Data_Wrangling.ipynb` | Merging and cleaning the raw data |
| `02_Brazillian_Olist_Ecommerce_EDA.ipynb` | Feature engineering and EDA |
| `Brazillian_cleaned_olist_dataset.csv` | Cleaned dataset created in notebook 01 |
| `olist_*_dataset.csv` | Raw datasets (customers, orders, payments) |

## What I Did

### 1. Data Wrangling (Notebook 01)
- Merged the customers, orders and payments tables using inner joins (103,886 rows, 16 columns).
- Converted date columns to `datetime` format.
- Renamed columns and standardised text in categorical columns.
- Checked for duplicate rows (none found).
- Removed invalid records (`Not_Defined` payment type and payment value <= 0), leaving 103,877 rows.
- Filled missing `order_approved_at` values using the purchase timestamp.
- Exported the cleaned dataset to CSV.

### 2. Feature Engineering (Notebook 02)
- `delivery_time_days`: days taken from purchase to delivery
- `delivery_delay_days`: estimated delivery date minus actual delivery date
- `is_late`: flag for late deliveries (1 = late, 0 = on time or early)
- `purchase_year`, `month`, `day`, `purchase_hour`: time features from the purchase timestamp
- `avg_emi_amount`: payment value divided by installments
- `approval_time_hours`: hours between purchase and approval

### 3. Exploratory Data Analysis (Notebook 02)
- **Missing values and outliers:** checked missing values and detected outliers using the IQR method.
- **Univariate analysis:** summary statistics (median, skewness, IQR), histograms, boxplots, and counts of order status, payment type, states and cities.
- **Time trends:** orders by year, month, day of week and hour of day.
- **Bivariate analysis:** payment type vs value and installments, delivery time by state, late delivery by state and month, and a correlation heatmap.
- **Multivariate analysis:** month vs year and day vs hour heatmaps.
- **Business KPIs:** total revenue, average order value, late delivery rate, repeat customers, top states by revenue and monthly revenue trend.

## Key Insights

1. The business grew year by year (47,520 payment records in 2017 and 56,011 in 2018).
2. Sao Paulo (SP) has the most orders (about 41.7K), followed by RJ and MG.
3. Credit Card is the most used payment method (about 74%) and the only one that uses installments.
4. Voucher payments are small (about 66 BRL on average) compared to other payment types (143 to 163 BRL).
5. About 8% of orders were delivered late, and the average delivery time is about 12 days.
6. Remote states like RR, AP and AM take 26 to 29 days on average, while SP takes only about 8 days.
7. Only about 3K out of 96K customers placed more than one order, so customer retention is low.

## Conclusion

Olist is growing, but delivery is slow in remote states and very few customers come back. Faster delivery in these states and loyalty offers could help improve the business.

## How to Run

1. Clone this repository.
2. Install the required libraries: `pip install pandas numpy matplotlib seaborn jupyter`
3. Run `01_Brazilian_Olist_Data_Wrangling.ipynb` first, then `02_Brazillian_Olist_Ecommerce_EDA.ipynb`.

## Author

**Shrikant Pedde**
[LinkedIn](https://linkedin.com/in/shrikant-pedde-535624320) | [GitHub](https://github.com/shrikantpedde)
