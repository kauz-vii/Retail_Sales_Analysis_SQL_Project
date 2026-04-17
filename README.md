# Retail Sales Analysis SQL Project

## Project Overview

**Project Title**: Retail Sales Analysis  
**Level**: Beginner  
**Database**: PostgreSQL  

This project demonstrates fundamental SQL skills using **PostgreSQL**, focusing on retail sales data analysis. It covers database creation, table design, data cleaning (with optimized NULL detection), exploratory data analysis (EDA), and solving real-world business problems using SQL queries. The project is ideal for beginners building a strong foundation in SQL and data analysis.

---

## Objectives

1. **Set up a retail sales table**: Design and create a structured table to store retail transaction data.
2. **Data Cleaning**: Identify and remove rows containing NULL values using both traditional and optimized approaches.
3. **Exploratory Data Analysis (EDA)**: Understand the dataset through record counts, unique values, and categories.
4. **Business Analysis**: Answer key business questions using aggregation, filtering, window functions, and CTEs.

---

## Project Structure

### 1. Database Setup

- **Table Creation**: The project starts by dropping any existing table and creating a fresh `retail_sales` table.
- **Schema Design**: The table stores transaction details, customer information, product category, pricing, and sales metrics.

```sql
DROP TABLE IF EXISTS retail_sales;

CREATE TABLE retail_sales
(
    transaction_id INT PRIMARY KEY,	
    sale_date DATE,	 
    sale_time TIME,	
    customer_id	INT,
    gender VARCHAR(15),
    age INT,
    category VARCHAR(15),	
    quantity INT,
    price_per_unit FLOAT,	
    cogs FLOAT,
    total_sale FLOAT
);
```

- **Table Description**: Column metadata is explored using `information_schema`.

```sql
SELECT
    column_name,
    data_type,
    is_nullable,
    column_default
FROM information_schema.columns
WHERE table_name = 'retail_sales';
```

---

### 2. Data Exploration & Cleaning

```sql
SELECT * FROM retail_sales LIMIT 10;
SELECT COUNT(*) FROM retail_sales;
SELECT COUNT(DISTINCT customer_id) FROM retail_sales;
SELECT DISTINCT category FROM retail_sales;
```

#### NULL Detection (Optimized)

```sql
SELECT *
FROM retail_sales
WHERE to_jsonb(retail_sales)::text LIKE '%null%';
```

#### Remove NULL Rows

```sql
DELETE
FROM retail_sales
WHERE to_jsonb(retail_sales)::text LIKE '%null%';
```

---

### 3. Data Analysis & Business Queries

Includes filtering, aggregation, window functions, and CTE-based analysis to solve real business problems such as:
- Daily sales analysis
- Category-wise performance
- Top customers
- Monthly trends
- Shift-based sales distribution

---

## Findings

- Sales span multiple categories and customer age groups.
- High-value transactions (>1000) are identifiable.
- Monthly and shift-based trends reveal peak periods.
- Top customers contribute significantly to total revenue.

---

## Conclusion

This project provides hands-on experience with PostgreSQL, emphasizing clean data practices, analytical querying, and business insight generation—making it suitable for SQL and data analyst portfolios.

---

## Author – Kaushik Bhadra

This project is part of my SQL portfolio, showcasing PostgreSQL skills including data cleaning, optimized NULL handling, aggregations, window functions, and CTEs.

---

## 📢 Connect With Me

<p align="center">
  <a href="https://www.linkedin.com/in/kaushikbhadra07" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-Kaushik%20Bhadra-blue?style=for-the-badge&logo=linkedin" />
  </a>
</p>

