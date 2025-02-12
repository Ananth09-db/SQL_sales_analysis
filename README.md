# Retail Sales Analysis

## Project Overview
This project aims to analyze retail sales data using SQL. The dataset contains transactional details such as sales date, time, customer demographics, product categories, and sales figures. The goal is to clean the data, modify it where necessary, and derive actionable insights through SQL queries.

## Dataset Information
The dataset includes the following fields:
- `transactions_id`: Unique identifier for each transaction
- `sale_date`: Date of the transaction
- `sale_time`: Time of the transaction
- `customer_id`: Unique identifier for the customer
- `gender`: Gender of the customer
- `age`: Age of the customer
- `category`: Product category
- `quantity`: Number of units purchased
- `price_per_unit`: Price per unit of the product
- `cogs`: Cost of goods sold
- `total_sale`: Total sale amount

## Data Cleaning and Preparation
The following steps were performed to clean and prepare the dataset:
- Removed NULL values from key fields
- Ensured consistency in data types
- Checked for duplicate records
- Standardized category names if necessary

## Business Questions and SQL Queries

### 1. What is the total number of transactions?
```sql
SELECT COUNT(*) AS total_transactions FROM retail_sales;
```

### 2. What is the total revenue generated from sales?
```sql
SELECT SUM(total_sale) AS total_revenue FROM retail_sales;
```

### 3. What is the average purchase amount per transaction?
```sql
SELECT AVG(total_sale) AS avg_transaction_amount FROM retail_sales;
```

### 4. What are the top 5 product categories by total sales?
```sql
SELECT category, SUM(total_sale) AS total_sales
FROM retail_sales
GROUP BY category
ORDER BY total_sales DESC
LIMIT 5;
```

### 5. What is the most common purchase time?
```sql
SELECT HOUR(sale_time) AS purchase_hour, COUNT(*) AS purchase_count
FROM retail_sales
GROUP BY purchase_hour
ORDER BY purchase_count DESC
LIMIT 1;
```

### 6. How does revenue vary by customer age group?
```sql
SELECT
    CASE
        WHEN age BETWEEN 18 AND 25 THEN '18-25'
        WHEN age BETWEEN 26 AND 35 THEN '26-35'
        WHEN age BETWEEN 36 AND 45 THEN '36-45'
        WHEN age BETWEEN 46 AND 60 THEN '46-60'
        ELSE '60+'
    END AS age_group,
    SUM(total_sale) AS total_revenue
FROM retail_sales
GROUP BY age_group
ORDER BY total_revenue DESC;
```

### 7. What is the total quantity of products sold?
```sql
SELECT SUM(quantity) AS total_quantity_sold FROM retail_sales;
```

### 8. What are the top 5 customers by total spending?
```sql
SELECT customer_id, SUM(total_sale) AS total_spent
FROM retail_sales
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 5;
```

### 9. Which day of the week has the highest sales?
```sql
SELECT DAYNAME(sale_date) AS day_of_week, SUM(total_sale) AS total_sales
FROM retail_sales
GROUP BY day_of_week
ORDER BY total_sales DESC
LIMIT 1;
```

### 10. What is the gender distribution of customers?
```sql
SELECT gender, COUNT(*) AS customer_count
FROM retail_sales
GROUP BY gender;
```

## How to Use This Repository
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/SQL_sales_analysis.git
   ```
2. Import the SQL file into your database.
3. Run the queries to analyze the dataset.
4. Modify or expand the analysis as needed.

## Future Enhancements
- Integrate with Power BI for visualization
- Predictive analytics for customer purchase trends
- Implement SQL stored procedures for automation

## Contributors
- **Ananth J**  
  [LinkedIn](https://www.linkedin.com/in/ananth-j-6413732a5)  
  [Email](mailto:ananthj575@gmail.com)

## License
This project is open-source and available for educational and analytical purposes.

