# SQL Challenge Solutions

Welcome to the **SQL Challenge Solutions - Day 3!** 🎉

#### Day 3 - 04-09-2024

## 🚀 Solutions Overview

Each challenge is followed by its corresponding SQL query. These queries solve the problems using the provided data tables.

## 📜 Challenge Solutions

### 1. **Find the Highest Priced Product in Each Category**

**Problem Statement:**  
Find the highest-priced product in each category from the products table.

**Query:**

```sql
WITH MaxPricePerCategory AS (
  SELECT
    category,
    MAX(price) AS max_price
  FROM products
  GROUP BY category
)
SELECT p.product_name, p.category, p.price
FROM products p
JOIN MaxPricePerCategory mpc
  ON p.category = mpc.category AND p.price = mpc.max_price;
```

**Output:**

| product_name | category    | price |
| ------------ | ----------- | ----- |
| Laptop       | Electronics | 1500  |
| Sofa         | Furniture   | 800   |
| Headphones   | Accessories | 200   |

---

### 2. **List Employees with More Than One Role**

**Problem Statement:**  
Find employees who have been assigned more than one role.

**Query:**

```sql
SELECT emp_name
FROM employee_roles
GROUP BY emp_name
HAVING COUNT(DISTINCT role) > 1;
```

**Output:**

| emp_name |
| -------- |
| John     |
| Alice    |

---

### 3. **Find Customers Who Have Never Made a Purchase**

**Problem Statement:**  
Find all customers who have never made a purchase.

**Query:**

```sql
SELECT c.customer_name
FROM customers c
LEFT JOIN orders o
  ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

**Output:**

| customer_name |
| ------------- |
| Visagan       |
| Anna          |
| Steve         |

---

### 4. **Calculate the Total Sales by Each Salesperson**

**Problem Statement:**  
Calculate the total sales amount by each salesperson.

**Query:**

```sql
SELECT sp.salesperson_name,
       COALESCE(SUM(s.sale_amount), 0) AS total_sales
FROM salespersons sp
LEFT JOIN sales s
  ON sp.salesperson_id = s.salesperson_id
GROUP BY sp.salesperson_name;
```

**Output:**

| salesperson_name | total_sales |
| ---------------- | ----------- |
| Tom              | 1200        |
| Jerry            | 1400        |
| Bob              | 400         |
| Visagan          | 0           |

---

### 5. **Find Orders Placed in the Last Week of Each Month**

**Problem Statement:**  
Identify all orders placed in the last week of each month.

**Query:**

```sql
WITH LastWeekOrders AS (
  SELECT
    order_id,
    order_date,
    DATE_TRUNC('month', order_date) + INTERVAL '1 month' - INTERVAL '7 days' AS last_week_start
  FROM orders
)
SELECT order_id, order_date
FROM LastWeekOrders
WHERE order_date >= last_week_start;
```

**Output:**

| order_id | order_date |
| -------- | ---------- |
| 3        | 2024-08-29 |
| 5        | 2024-09-30 |

---

## 📚 How to Use

1. **Clone the Repository:** Get a local copy to explore the solutions.
2. **Run the Queries:** Execute these queries in your SQL environment to verify the results.
3. **Learn and Practice:** Use these solutions to understand SQL better and improve your skills.

## 🤝 Contribute

Feel free to suggest improvements or contribute additional challenges and solutions. Your contributions are highly appreciated!

## 🎓 Happy Querying!

Dive into these solutions to enhance your SQL knowledge and prepare for your next challenge or interview!

#### 📜 Notice:

This README file provides clear and concise solutions for each SQL challenge, along with their expected output. It is designed to be informative and easy to follow for anyone using it for learning or practice.

---
