# 📚 Northwind DB Analysis using MySQL Workbench
This project explores the Northwind Traders relational database using MySQL and MySQL Workbench. The aim was to explore and manipulate data using SQL queries and demonstrate practical data analysis skills including querying, joining tables, aggregating data, and generating insights relevant to sales, customers, products and suppliers.

### 🎯 Key Skills Demonstrated:
`MySQL` &nbsp; `SQL querying and joins` &nbsp; `Exploratory data analysis` &nbsp; `Query structuring` &nbsp; `Data aggregation and filtering` &nbsp; `String manipulation`

### 🧰 Tools & Technologies
- **SQL:** MySQL
- **Environment:** MySQL Workbench


---
### 🔎 SQL Process

This section outlines how I explored the Northwind database using SQL, including the operations applied and queries developed to analyse the data.
---
#### 🧭 Approach

- Explored table structures and relationships using the EER diagram.
- Identified key fields for joining tables across `customers` `orders` `order details` `
  products`.
- Practiced filtering, grouping and aggregating data to analyse the dataset.

#### 1. Practical Basic SQL Queries 

| Task | Objective | SQL Query |
| :--- | :--- | :--- |
| 1. Full Customer Data | Retrieve all columns from the `Customers` table. | `select * from customers;` |
| 2. Customer Names and Cities | Retrieve only `CustomerName` and `City` from the `Customers` table. | `select CustomerName, City from customers;` |
| 3. Unique Cities | Retrieve distinct city values from the `City` column. | `select distinct City,from customers;` |
| 4. High-Value Products | Retrieve all columns from `Products` where `Price` is greater than 50. | `SELECT * FROM products,WHERE price >50;` |
| 5. International Customers | Retrieve all columns from `Customers` where `Country` is 'USA' or 'UK'. | `Select * From Customers Where country = "usa" or country ="UK";` |
| 6. Recent Orders Report | Retrieve all columns from `Orders`, sorted by `OrderDate` in descending order. | `SELECT * From orders order by OrderDate desc;` |
| 7. Mid-Range Products | Retrieve all columns from `Products` where `Price` is between 20 and 50, ordered by descending `Price`. | `select * from products where price between '20' And '50' order by price Desc;` |
| 8. Local Marketing (USA) | Retrieve all columns from `Customers` where `Country` is 'USA' AND City is 'Portland' OR 'Kirkland'. | `select * from customers where country = "USA" AND city = 'Portland' OR city='Kirkland' order by CustomerName ASC;` |
| 9. UK or London Customers | Retrieve all columns from `Customers` where `Country` is 'UK' OR City is 'London'. | `Select * from customers where country = 'UK' OR city= 'London' order by CustomerName Desc;` |
| 10. Product Inventory | Retrieve all columns from `Products` where `CategoryID` is 1 or 2. | `select * from products where categoryID= '1' OR categoryid= '2' order by ProductName ASC;` |

#### Example Basic Queries
**1. Select suppliers from Countries with names including 'land'**
```sql
SELECT* From Suppliers WHERE Country Like "%land%";
```
**2. Number of Orders per Product**
```sql
SELECT ProductName, Price, SUM(Quantity) AS "Total Quantity of Orders" FROM Products LEFT JOIN Order_details  
ON Products.ProductID=Order_details.ProductID GROUP BY ProductName, Price;
```
#### 2.Practical JOIN Queries

| Task | Objective | SQL Query |
| :--- | :--- | :--- |
| 1. Products to Suppliers | Find the supplier name for each product. | `select ProductName, SupplierName From products join suppliers on products.SupplierID = Suppliers.SupplierID;` |
| 2. Classifying Products | Find the category name for each product. | `Select ProductName, CategoryName From Products Join Categories on products.CategoryID = Categories.CategoryID;` |
| 3. Meat/Poultry Report | Retrieve all products belonging to the 'Meat/Poultry' category. | `Select ProductName, CategoryName From Products Join Categories on products.CategoryID = Categories.CategoryID where CategoryName = "Meat/Poultry";` |
| 4. Complete Order Overview | Retrieve `OrderID`, `OrderDate`, `CustomerName`, and `EmployeeName` for all orders. | `select OrderID, OrderDate, CustomerName, concat_ws(" ",FirstName, LastName) as EmployeeName from orders join Customers on orders.CustomerID = customers.CustomerID join employees on orders.EmployeeID = Employees.EmployeeID;` |
| 5. Supply Chain Overview | Retrieve `ProductName`, `CategoryName`, and `SupplierName` for all products. | `select ProductName, categories.CategoryName, suppliers.SupplierName from Products join Categories on products.CategoryID = Categories.CategoryID join Suppliers on products.SupplierID = suppliers.SupplierID;` |
| 6. Yearly Order Summary – 1996 | Create a report for all orders of 1996, including customer and product information. | `select CustomerName, orders.CustomerID, OrderDate, ProductName from Orders Join Customers on orders.CustomerID = customers.CustomerID join order_details on orders.OrderID = order_details.OrderID join products on order_details.ProductID = products.ProductID Where OrderDate LIKE "1996%";` |
| 7. Product Count by Category | Retrieve all categories along with the number of products in each category. | `select CategoryName, count(ProductName) as TotalQuantity from products join Categories on categories.CategoryID = products.CategoryID group by CategoryName;` |
| 8. Sales Volume Breakdown | Retrieve product prices, names, and the total quantity ordered for each product. | `select Price, sum(Quantity), ProductName from Products join order_details on products.productid = order_details.productID group by ProductName, Price;` |

#### Example JOIN Queries
**1. Create an Order List with Customer and Employee Information** 
```sql
SELECT OrderID, OrderDate, CustomerName, CONCAT(FirstName,' ',LastName) AS EmployeeName FROM Orders INNER JOIN Customers  
ON Orders.CustomerID=Customers.CustomerID INNER JOIN Employees ON Orders.EmployeeID=Employees.EmployeeID;
```
**2. Number of Orders per Product**
```sql
SELECT ProductName, Price, SUM(Quantity) AS "Total Quantity of Orders" FROM Products LEFT JOIN Order_details  
ON Products.ProductID=Order_details.ProductID GROUP BY ProductName, Price;
```
--- 
## 📌 How to Use

1. Download or clone this repository.
2. Open Mysql and ceate schemas. 
3. Copy Queries and analyse. 

---
## 🤝 Contact

* [Project created by **EvaRuttkay**.](https://github.com/EvaRuttkay)
  
* [Link to LinkedIn](https://www.linkedin.com/in/evaruttkay)
