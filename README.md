# Project__Online_Retail_Sales_Database_Design
# Using MySQL Workbench for creating Database 'ECOMMERCE' and tables Products, Customers, Orders and Payments.

CREATE DATABASE Ecommerce;
USE Ecommerce;

# Normalized schema to 3NF and DDL scripts in creation of tables with constraints such as Primary Key, NOT Null, Unique, Check, Default and Foreign Key:

CREATE TABLE Products(
product_id INT PRIMARY KEY,
product_name VARCHAR(100),
category VARCHAR(50),
price DECIMAL(10,2) NOT NULL,
quantity INT
);

CREATE TABLE Customers(
customer_id INT PRIMARY KEY,
product_id INT,
first_name VARCHAR(100),
last_name VARCHAR(100),
email VARCHAR(50) UNIQUE,
phone VARCHAR(20),
address VARCHAR (100),
registration_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
FOREIGN KEY(product_id) REFERENCES Products(product_id)
);

CREATE TABLE Orders(
order_id INT PRIMARY KEY,
customer_id INT,
order_date DATE,
order_status VARCHAR(100),
total_amount DECIMAL(12,2),
FOREIGN KEY(customer_id) REFERENCES Customers(customer_id)
);

CREATE TABLE Payments(
payment_id INT PRIMARY KEY,
order_id INT,
payment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
amount DECIMAL(10,2) NOT NULL,
method VARCHAR(50),
status VARCHAR(50),
FOREIGN KEY(order_id) REFERENCES Orders(order_id)
);

# Populating tables with sample data:

INSERT INTO Products(product_id, product_name, category, price, quantity) VALUES
(1, 'Laptop', 'High-performance laptop', 1200.00, 50),
(2, 'Smartphone', 'Latest Android smartphone', 800.00, 100),
(3, 'Headphones', 'Noise-cancelling headphones', 150.00, 200),
(4, 'Monitor', '27-inch 4K monitor', 350.00, 75),
(5, 'Keyboard', 'Mechanical keyboard', 90.00, 120),
(6, 'Mouse', 'Wireless mouse', 40.00, 150),
(7, 'Tablet', '10-inch tablet with stylus', 600.00, 60),
(8, 'Smartwatch', 'Fitness tracking smartwatch', 200.00, 80),
(9, 'Webcam', '1080p USB webcam', 70.00, 90),
(10, 'Printer', 'Color laser printer', 300.00, 40);

INSERT INTO Customers VALUES
(101, 1, 'Alice', 'Smith', 'alice@example.com', '1234567890', '123 Elm St, City A', '2024-06-15'),
(102, 2,  'Bob', 'Johnson', 'bob@example.com', '2345678901', '456 Oak St, City B', '2023-07-12'),
(103, 3, 'Charlie', 'Williams', 'charlie@example.com', '3456789012', '789 Pine St, City C', '2024-03-15'),
(104, 4, 'Diana', 'Brown', 'diana@example.com', '4567890123', '101 Maple St, City D', '2024-05-20'),
(105, 5, 'Ethan', 'Jones', 'ethan@example.com', '5678901234', '202 Birch St, City E', '2024-06-22'),
(106, 6, 'Fiona', 'Garcia', 'fiona@example.com', '6789012345', '303 Cedar St, City F', '2024-01-05'),
(107, 7, 'George', 'Martinez', 'george@example.com', '7890123456', '404 Spruce St, City G', '2024-06-15'),
(108, 8, 'Hannah', 'Lee', 'hannah@example.com', '8901234567', '505 Walnut St, City H', '2024-05-25'),
(109, 9, 'Ivan', 'Lopez', 'ivan@example.com', '9012345678', '606 Chestnut St, City I', '2024-08-19'),
(110, 10, 'Julia', 'Gonzalez', 'julia@example.com', '0123456789', '707 Ash St, City J', '2024-11-15');

INSERT INTO Orders VALUES
(201, 101, '2024-11-15', 'Completed', 1200.00),
(202, 102, '2024-09-25', 'Pending', 800.00),
(203, 103, '2024-10-05', 'Shipped', 150.00),
(204, 104, '2024-06-14', 'Completed', 350.00),
(205, 105, '2024-04-25', 'Cancelled', 90.00),
(206, 106, '2024-12-05', 'Processing', 40.00),
(207, 107, '2024-03-22', 'Completed', 600.00),
(208, 108, '2024-10-12', 'Completed', 200.00),
(209, 109, '2024-05-15', 'Returned', 70.00),
(210, 110, '2024-12-06', 'Shipped', 300.00);

INSERT INTO Payments VALUES
(301, 201, '2025-06-12', 1200.00,'Credit Card', 'Paid'),
(302, 202, '2024-12-06', 800.00, 'PayPal', 'Paid'),
(303, 203, '2025-02-11', 150.00, 'Credit Card', 'Paid'),
(304, 204, '2025-03-12', 350.00, 'Debit Card', 'Paid'),
(305, 205, '2025-01-13', 90.00, 'Credit Card', 'Refunded'),
(306, 206, '2025-01-14', 40.00, 'PayPal', 'Pending'),
(307, 207, '2025-01-15', 600.00, 'Credit Card', 'Paid'),
(308, 208, '2025-03-19', 200.00, 'Debit Card', 'Paid'),
(309, 209, '2025-05-18', 70.00,  'Credit Card', 'Refunded'),
(310, 210, '2025-06-25', 300.00, 'Bank Transfer', 'Paid');

# Retrieving data from tables:
SELECT * FROM Products;

Products Table:

<img width="592" height="315" alt="image" src="https://github.com/user-attachments/assets/381d8a4d-aef3-4686-b038-a60777feed63" />

SELECT * FROM Customers;

Customers Table:

<img width="960" height="308" alt="image" src="https://github.com/user-attachments/assets/158a8a5e-dbcf-4c16-9d5a-af1014079df0" />


SELECT * FROM Orders;

Orders Table:

<img width="499" height="332" alt="image" src="https://github.com/user-attachments/assets/2a531eda-4195-42d0-8230-49835fa237da" />

SELECT * FROM Payments;

Payments Table:

<img width="634" height="307" alt="image" src="https://github.com/user-attachments/assets/a4799c2c-0ffb-4f63-88b8-6c39ebf2a5e1" />


# ER Diagram using dbdiagram.io:

<img width="787" height="817" alt="image" src="https://github.com/user-attachments/assets/7018ef22-a939-4e1b-9681-f6d89dd37c5f" />


# JOIN Queries
# Retrieving data from multiple tables:
SELECT p.product_id, c.first_name, c.last_name, p.product_name, o.order_status, s.method, p.price FROM Products p
JOIN Customers c
ON p.product_id = c.product_id
JOIN Orders o
ON o.customer_id = c.customer_id
JOIN Payments s
ON s.order_id = o.order_id;

<img width="678" height="286" alt="image" src="https://github.com/user-attachments/assets/c793e30f-1821-4d52-846f-9c5d8b2e2d9c" />


# 'INNER JOIN' using Products and Customers Tables:

SELECT * FROM Products p 
INNER JOIN Customers c
ON p.product_id = c.product_id;

INNER JOIN Table:

<img width="1475" height="279" alt="image" src="https://github.com/user-attachments/assets/6c0fb44a-1d8f-4c13-96fd-027de1511fa5" />

# 'INNER JOIN' with 'ORDER BY' and 'LIMIT' clause:
SELECT p.product_id, c.first_name, c.last_name, p.product_name, o.order_status, s.method, p.price FROM Products p
JOIN Customers c
ON p.product_id = c.product_id
JOIN Orders o
ON o.customer_id = c.customer_id
JOIN Payments s
ON s.order_id = o.order_id
ORDER BY p.price 
LIMIT 1;

<img width="616" height="78" alt="image" src="https://github.com/user-attachments/assets/9a4934a0-2bb9-44ae-a0fc-edd8bc194314" />

# 'INNER JOIN' with 'WHERE' clause:
SELECT p.product_id, p.product_name, c.first_name, c.last_name, c.registration_date, p.price FROM Products p
INNER JOIN Customers c
ON p.product_id = c.product_id
WHERE p.price >= 300
ORDER BY p.price DESC;

<img width="606" height="176" alt="image" src="https://github.com/user-attachments/assets/9ab35750-7fc1-44f4-a6db-a40ae2a45c98" />

# 'LEFT JOIN' using Products and Customers Tables:
SELECT * FROM Products p 
LEFT JOIN Customers c
ON p.product_id = c.product_id;

<img width="1481" height="270" alt="image" src="https://github.com/user-attachments/assets/bd285d62-c84e-4c6d-ab8a-4330a56dcf48" />

# 'RIGHT JOIN' using Products and Customers Tables:
SELECT * FROM Products p 
RIGHT JOIN Customers c
ON p.product_id = c.product_id;

<img width="1465" height="278" alt="image" src="https://github.com/user-attachments/assets/5e99e88c-706f-4f6c-a9af-abcc0a21015e" />

# 'FULL JOIN' using Products and Customers Tables:
SELECT p.product_id, p.product_name, c.first_name, c.last_name, c.registration_date, p.price FROM Products p 
LEFT JOIN Customers c
ON p.product_id = c.product_id
UNION
SELECT p.product_id, p.product_name, c.first_name, c.last_name, c.registration_date, p.price FROM Products p 
RIGHT JOIN Customers c
ON p.product_id = c.product_id;

<img width="620" height="257" alt="image" src="https://github.com/user-attachments/assets/a269c226-7c92-44bd-af46-895d476594cb" />


# 'CROSS JOIN' using Products and Customers Tables:
SELECT p.product_id, p.product_name, c.first_name, p.price FROM Products p
CROSS JOIN Customers c;

<img width="920" height="555" alt="image" src="https://github.com/user-attachments/assets/843f9af2-056d-4b17-9cd4-53d9838ebf10" />

# 'CROSS JOIN' using Multiple Tables Products, Customers, Orders and Payments:
SELECT p.product_id, c.first_name, c.last_name, p.product_name, o.order_status, s.method FROM Products p
CROSS JOIN Customers c
CROSS JOIN Orders o
CROSS JOIN Payments s;

<img width="1023" height="633" alt="image" src="https://github.com/user-attachments/assets/7eb81cf7-8d78-4ee3-aac4-069df159124b" />

# Creating Views:
CREATE VIEW SalesReport AS
SELECT 
  p.product_id, 
  c.first_name, 
  p.product_name, 
  o.order_status, 
  s.method, 
  s.amount
FROM Products p
JOIN Customers c ON p.product_id = c.product_id
JOIN Orders o ON c.customer_id = o.customer_id
JOIN Payments s ON o.order_id = s.order_id;

SELECT * FROM SalesReport;

# <img width="601" height="296" alt="image" src="https://github.com/user-attachments/assets/ee569ff4-9425-46a4-a8aa-08b053708ebc" />

# Some DDL Commands like DROP, TRUNCATE, ALTER, RENAME:

DROP DATABASE database_name;

DROP TABLE table_name;

RENAME TABLE Table_Name To New_Table_Name;

TRUNCATE TABLE table_name;

ALTER TABLE table_name
ADD column_name datatype;
