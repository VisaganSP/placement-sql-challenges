# 🎓 Placement Training SQL Problems

#### Day 3 - 04-09-2024

This set of SQL problems is designed for placement training, focusing on key concepts like:

- Filtering and grouping data based on specific conditions 🗂️
- Identifying unique and common elements across tables 🔍
- Exploring various scenarios such as:
  - Calculating aggregate functions 📊
  - Using joins to connect related data across different tables 🔗

These problems will help you practice writing SQL queries using a mix of basic to intermediate concepts, ensuring a solid foundation for placement exams 🛠️.

---

## Problem 1: Find the Highest Priced Product in Each Category

### Objective

Given a table of products with their respective categories and prices, find the highest-priced product in each category.

### Input Table - `products`

| product_id | product_name | category    | price |
|------------|--------------|-------------|-------|
| 1          | Laptop       | Electronics | 1500  |
| 2          | Smartphone   | Electronics | 1000  |
| 3          | Headphones   | Accessories | 200   |
| 4          | Desk Chair   | Furniture   | 300   |
| 5          | Sofa         | Furniture   | 800   |
| 6          | Mouse        | Accessories | 50    |

### Output

| product_name | category    | price |
|--------------|-------------|-------|
| Laptop       | Electronics | 1500  |
| Sofa         | Furniture   | 800   |
| Headphones   | Accessories | 200   |

### Constraints

- Assume each category has at least one product.
- Prices are positive integers.
- If multiple products have the same highest price within a category, include any one of them.

### Queries

#### Input:

```sql
INSERT INTO products (product_id, product_name, category, price)
VALUES
(1, 'Laptop', 'Electronics', 1500),
(2, 'Smartphone', 'Electronics', 1000),
(3, 'Headphones', 'Accessories', 200),
(4, 'Desk Chair', 'Furniture', 300),
(5, 'Sofa', 'Furniture', 800),
(6, 'Mouse', 'Accessories', 50);
```

---

## Problem 2: List Employees with More Than One Role

### Objective

Given a table of employees and their roles, find the employees who have been assigned more than one role.

### Input Table - `employee_roles`

| emp_id | emp_name | role         |
|--------|----------|--------------|
| 1      | Visagan  | Developer    |
| 2      | John     | Developer    |
| 3      | Alice    | Manager      |
| 2      | John     | Tester       |
| 4      | Bob      | Developer    |
| 3      | Alice    | HR           |
| 5      | Carol    | Designer     |

### Output

| emp_name |
|----------|
| John     |
| Alice    |

### Constraints

- Assume each employee can have multiple roles.
- The table contains at least one employee with more than one role.

### Queries

#### Input:

```sql
INSERT INTO employee_roles (emp_id, emp_name, role)
VALUES
(1, 'Visagan', 'Developer'),
(2, 'John', 'Developer'),
(3, 'Alice', 'Manager'),
(2, 'John', 'Tester'),
(4, 'Bob', 'Developer'),
(3, 'Alice', 'HR'),
(5, 'Carol', 'Designer');
```

---

## Problem 3: Find Customers Who Have Never Made a Purchase

### Objective

Given a table of customers and another table of orders, find all customers who have never made a purchase.

### Input Table - `customers`

| customer_id | customer_name |
|-------------|---------------|
| 1           | Visagan       |
| 2           | Mary          |
| 3           | John          |
| 4           | Anna          |
| 5           | Steve         |

### Input Table - `orders`

| order_id | customer_id | order_amount |
|----------|-------------|--------------|
| 101      | 2           | 150          |
| 102      | 3           | 200          |

### Output

| customer_name |
|---------------|
| Visagan       |
| Anna          |
| Steve         |

### Constraints

- Assume each customer has a unique ID.
- A customer may have zero or multiple orders.
- The tables contain at least one customer without an order.

### Queries

#### Input:

```sql
INSERT INTO customers (customer_id, customer_name)
VALUES
(1, 'Visagan'),
(2, 'Mary'),
(3, 'John'),
(4, 'Anna'),
(5, 'Steve');

INSERT INTO orders (order_id, customer_id, order_amount)
VALUES
(101, 2, 150),
(102, 3, 200);
```

---

## Problem 4: Calculate the Total Sales by Each Salesperson

### Objective

Given a table of sales transactions and a table of salespersons, calculate the total sales amount by each salesperson.

### Input Table - `salespersons`

| salesperson_id | salesperson_name |
|----------------|------------------|
| 1              | Visagan          |
| 2              | Tom              |
| 3              | Jerry            |
| 4              | Bob              |

### Input Table - `sales`

| sale_id | salesperson_id | sale_amount |
|---------|----------------|-------------|
| 1       | 2              | 500         |
| 2       | 3              | 800         |
| 3       | 2              | 700         |
| 4       | 4              | 400         |
| 5       | 3              | 600         |

### Output

| salesperson_name | total_sales |
|------------------|-------------|
| Tom              | 1200        |
| Jerry            | 1400        |
| Bob              | 400         |
| Visagan          | 0           |

### Constraints

- Assume each salesperson can have multiple sales.
- Sale amounts are positive integers.
- The tables contain at least one sale by each salesperson.

### Queries

#### Input:

```sql
INSERT INTO salespersons (salesperson_id, salesperson_name)
VALUES
(1, 'Visagan'),
(2, 'Tom'),
(3, 'Jerry'),
(4, 'Bob');

INSERT INTO sales (sale_id, salesperson_id, sale_amount)
VALUES
(1, 2, 500),
(2, 3, 800),
(3, 2, 700),
(4, 4, 400),
(5, 3, 600);
```

---

## Problem 5: Find Orders Placed in the Last Week of Each Month

### Objective

Given a table of orders with order dates, identify all orders placed in the last week of each month.

### Input Table - `orders`

| order_id | customer_id | order_date |
|----------|-------------|------------|
| 1        | 1           | 2024-08-25 |
| 2        | 2           | 2024-08-27 |
| 3        | 3           | 2024-08-29 |
| 4        | 4           | 2024-09-25 |
| 5        | 5           | 2024-09-30 |

### Output

| order_id | order_date |
|----------|------------|
| 3        | 2024-08-29 |
| 5        | 2024-09-30 |

### Constraints

- The `order_date` is in `YYYY-MM-DD` format.
- The last week is considered the last 7 days of the month.
- The table contains at least one order in the last week of any month.

### Queries

#### Input:

```sql
INSERT INTO orders (order_id, customer_id, order_date)
VALUES
(1, 1, '2024-08-25'),
(2, 2, '2024-08-27'),
(3, 3, '2024-08-29'),
(4, 4, '2024-09-25'),
(5, 5, '2024-09-30');
```

---

These problems provide a diverse set of challenges to help you practice essential SQL skills, with a focus on real-world scenarios and data manipulation techniques!