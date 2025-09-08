# Joins

# task-4-.Use-INNER-LEFT-RIGHT-FULL-JOIN

---

# **Combination Joins in SQL 

## 🛠 Step 1 – Create the Database

We first create a new database to store our tables.

sql
CREATE DATABASE combine_data;
USE combine_data;


This ensures all the tables and data we create are kept in one place.

---

## 🛠 Step 2 – Create the Customers Table

The *Customers* table stores customer details like ID, name, and country.

sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    Country VARCHAR(50)
);


We then insert some sample data, including customers from different countries:

sql
INSERT INTO Customers (CustomerID, CustomerName, Country) VALUES
(1, 'John Smith', 'USA'),
(2, 'Priya Sharma', 'India'),
(3, 'Ahmed Khan', 'UAE'),
...
(10, 'Sai', 'USA');


---

## 🛠 Step 3 – Create the Orders Table

The *Orders* table stores order details, including which customer placed the order.

sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    Product VARCHAR(50),
    Amount DECIMAL(10,2)
);


Sample order data is inserted, including some orders with customers who are not in the Customers table.

sql
INSERT INTO Orders (OrderID, CustomerID, Product, Amount) VALUES
(101, 1, 'Laptop', 800),
(102, 3, 'Phone', 500),
...
(109, 6, 'Earbuds', 700);


This setup allows us to test joins where:

* Some customers *have no orders*.
* Some orders *don’t have a matching customer*.

---

## 🔍 Step 4 – Running Join Queries

### *1. INNER JOIN*

Returns only matching records between Customers and Orders.

sql
SELECT Customers.CustomerID, CustomerName, Product, Amount
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;


*Use case:* Find customers who have placed at least one order.

---

### *2. LEFT JOIN*

Returns all customers, even those without orders. Missing order details appear as NULL.

sql
SELECT Customers.CustomerID, CustomerName, Product, Amount
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;


*Use case:* View a complete customer list with their orders (if any).

---

### *3. RIGHT JOIN*

Returns all orders, even if the customer does not exist in the Customers table.

sql
SELECT Customers.CustomerID, CustomerName, Product, Amount
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;


*Use case:* Identify orders that may not have proper customer records.

---

### *4. FULL OUTER JOIN (MySQL Alternative)*

MySQL does not support FULL OUTER JOIN directly, so we combine LEFT JOIN and RIGHT JOIN with UNION.

sql
SELECT Customers.CustomerID, CustomerName, Product, Amount
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
UNION
SELECT Customers.CustomerID, CustomerName, Product, Amount
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;


*Use case:* Get a complete picture of all customers and all orders.

---

## 🎯 Key Learnings

* *INNER JOIN* → Matching rows only.
* *LEFT JOIN* → All from left table, matched where possible.
* *RIGHT JOIN* → All from right table, matched where possible.
* *FULL JOIN* → All rows from both tables, matched where possible.





<img width="914" height="614" alt="Image" src="https://github.com/user-attachments/assets/5b8778ac-b353-40ab-a43f-331a33621a92" />
<img width="1142" height="557" alt="Image" src="https://github.com/user-attachments/assets/cadba4be-aea8-428b-9b67-448976fcb882" />
<img width="1027" height="592" alt="Image" src="https://github.com/user-attachments/assets/558d129c-5907-4c55-9820-b41ed0f388ee" />
<img width="1176" height="532" alt="Image" src="https://github.com/user-attachments/assets/42c12aa8-1549-4ff4-a7ef-8651d36e7141" />
<img width="1008" height="561" alt="Image" src="https://github.com/user-attachments/assets/6aa59f34-96fc-4d9a-b4d8-b05b37a5f540" />


---
