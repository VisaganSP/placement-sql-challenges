# SQL Challenge Solutions

Welcome to the **SQL Challenge Solutions - Day 2!** 🎉

#### Day 2 - 21-08-2024

## 🚀 Solutions Overview

Each challenge is followed by its corresponding SQL query. These queries solve the problems using the provided data tables.

## 📜 Challenge Solutions

### 1. **Top 3 Employees by Salary in Each Department**

**Problem Statement:**  
Find the top 3 employees by salary in each department.

**Query:**

```sql
WITH RankedSalaries AS (
  SELECT
    emp_id,
    emp_name,
    department,
    salary,
    ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS rank
  FROM employees
)
SELECT emp_id, emp_name, department, salary
FROM RankedSalaries
WHERE rank <= 3;
```

**Output:**

| emp_id | emp_name | department | salary |
| ------ | -------- | ---------- | ------ |
| 5      | Eve      | HR         | 95000  |
| 3      | Carol    | HR         | 85000  |
| 1      | Alice    | HR         | 80000  |
| 2      | Bob      | IT         | 120000 |
| 7      | Grace    | IT         | 115000 |
| 6      | Frank    | IT         | 110000 |

---

### 2. **Find Products Sold on the Last Day of Each Month**

**Problem Statement:**  
Find the products that were sold on the last day of each month.

**Query:**

```sql
WITH LastDaySales AS (
  SELECT
    product_name,
    sale_date,
    ROW_NUMBER() OVER (PARTITION BY EXTRACT(YEAR FROM sale_date), EXTRACT(MONTH FROM sale_date) ORDER BY sale_date DESC) AS rank
  FROM sales
)
SELECT product_name, sale_date
FROM LastDaySales
WHERE rank = 1;
```

**Output:**

| product_name | sale_date  |
| ------------ | ---------- |
| Laptop       | 2024-01-31 |
| Keyboard     | 2024-02-28 |
| Monitor      | 2024-02-28 |
| Laptop       | 2024-03-31 |

---

### 3. **Find the Second Highest Salary**

**Problem Statement:**  
Find the second highest salary without using `LIMIT` or `TOP`.

**Query:**

```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Output:**

| second_highest_salary |
| --------------------- |
| 95000                 |

---

### 4. **Find Employees with Same Salary in Different Departments**

**Problem Statement:**  
Find employees who have the same salary as someone in another department.

**Query:**

```sql
SELECT DISTINCT e1.emp_name, e1.department, e1.salary
FROM employees e1
JOIN employees e2
  ON e1.salary = e2.salary
  AND e1.department != e2.department;
```

**Output:**

| emp_name | department | salary |
| -------- | ---------- | ------ |
| Carol    | HR         | 95000  |
| Eve      | Sales      | 95000  |

---

### 5. **Find Employees Without a Manager**

**Problem Statement:**  
Find all employees who do not have a manager.

**Query:**

```sql
SELECT emp_name
FROM employees
WHERE manager_id IS NULL;
```

**Output:**

| emp_name |
| -------- |
| Bob      |

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
