# SQL Challenge Solutions

Welcome to the **SQL Challenge Solutions - Day 1!** 🎉

#### Day 1 - 14-08-2024

## 🚀 Solutions Overview

Each challenge is followed by its corresponding SQL query. These queries solve the problems using the provided data tables.

## 📜 Challenge Solutions

### 1. **HR Heroes: Uncovering the Team Members**

**Problem Statement:**  
Find the names of employees who work in the 'HR' department.

**Query:**

```sql
SELECT Name
FROM Employees
WHERE Department = 'HR';
```

**Output:**

| Name        |
| ----------- |
| Visagan     |
| Alice Brown |

---

### 2. **Departmental Dough: Tracking Total Salaries**

**Problem Statement:**  
Calculate the total salary expenditure for each department.

**Query:**

```sql
SELECT Department, SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department;
```

**Output:**

| Department | TotalSalary |
| ---------- | ----------- |
| HR         | 102000      |
| IT         | 118000      |
| Finance    | 55000       |

---

### 3. **Customer Cash Flow: Averaging Order Amounts**

**Problem Statement:**  
Find the average order amount for each customer.

**Query:**

```sql
SELECT CustomerID, AVG(Amount) AS AverageOrderAmount
FROM Orders
GROUP BY CustomerID;
```

**Output:**

| CustomerID | AverageOrderAmount |
| ---------- | ------------------ |
| 101        | 175.00             |
| 102        | 275.00             |
| 103        | 400.00             |

---

### 4. **Order Overload: The Quest for the Second Highest Amount**

**Problem Statement:**  
Find the second highest order amount.

**Query:**

```sql
SELECT MAX(Amount) AS SecondHighestAmount
FROM Orders
WHERE Amount < (SELECT MAX(Amount) FROM Orders);
```

**Output:**

| SecondHighestAmount |
| ------------------- |
| 300                 |

---

### 5. **High Rollers: Identifying Big Spenders**

**Problem Statement:**  
Find the names of customers who have placed orders worth more than $300.

**Query:**

```sql
SELECT C.Name
FROM Customers C
JOIN Orders O ON C.CustomerID = O.CustomerID
WHERE O.Amount > 300;
```

**Output:**

| Name        |
| ----------- |
| Jane Smith  |
| Alice Brown |

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
