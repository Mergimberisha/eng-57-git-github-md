## SQL day 1 with Astha


```SQL

SELECT * FROM Customers
WHERE City='Paris'

SELECT COUNT (EmployeesID) AS "Number of Employees" FROM Employees
SELECT * FROM Employees
WHERE City='London'

SELECT CustomerID, City FROM Customers
WHERE Country = 'France'

SELECT COUNT(*) FROM Products

SELECT p.productName, p.UnitPrice
FROM Products p
WHERE  p.CategoryID=1  AND p.Discountinued=0

SELECT ProductName, UnitPrice FROM Products
WHERE UnitsInStock > 0 AND UnitPrice> 29.99

SELECT ProductName, UnitPrice FROM Products
WHERE UnitsInStock > 0 OR UnitPrice> 29.99

SELECT DISTINCT cust.Country
FROM Customers cust
WHERE cust .ContactTitle='Owner' AND cust.Country LIKE '[^MSD]%'

SELECT *
FROM EmployeeTerritories
WHERE TerritoryID BETWEEN 06800 AND 09999

SELECT * FROM Categories
WHERE Categories LIKE '[bs]%'

SELECT * FROM Orders

SELECT count(*) as "NumberOfOrders"
FROM Orders o
WHERE EmployeeID IN (5,7)


SELECT o.UnitPrice, o.Quantity, o.UnitPrice*o.Quantity AS "Gross Total"
FROM [Order Details] o

Gross Total = 20*1=20 * quantity
Net Total = 20*1*(1-2-/100)=16
= unit price * quantity *(1-discount/100)

SELECT * FROM [Order Details]

SELECT o.UnitPrice, o.Quantity, o.Discount, o.UnitPrice * o.Quantity AS "Gross Total", o.UnitPrice * o.Quantity * (1 - o.Discount) AS "Net Total"
FROM [Order Details] o
ORDER BY "Net Total" DESC



SELECT o.OrderID, o.UnitPrice, o.Quantity, o.Discount, SUM(o.UnitPrice * o.Quantity) AS "Gross Total"
FROM [Order Details] o
GROUP BY o.OrderID, o.UnitPrice, o.Quantity, o.Discount
ORDER BY "Gross Total" DESC


SELECT c.PostalCode AS "Post Code",
LEFT(c.PostalCode, CHARINDEX(' ',c.PostalCode)-1) AS "Postal Code Region",
CHARINDEX(' ', c.PostalCode) AS "Space Found", c.Country
FROM Customers c
WHERE Country = 'UK'

SELECT p.ProductName
FROM Products p
WHERE p.ProductName LIKE '%''%'

SELECT p.ProductName
FROM Products p
WHERE CHARINDEX('''',p.ProductName)>0

SELECT DATEADD(d,5,OrderDate) AS "Due Date",
DATEDIFF(d,OrderDate,ShippedDate) AS "Ship Days"
FROM Orders


SELECT * FROM Employees

SELECT FirstName + '' + LastName AS "Name",
DATEDIFF(YY, BirthDate, GetDate()) AS "Age"
FROM Employees



SELECT FirstName + '' + LastName AS "Name",
DATEDIFF(DD, BirthDate, GetDate())/365.25 AS "Age"
FROM Employees

SELECT CASE
WHEN DATEDIFF(d,OrderDate,ShippedDate) < 10 THEN 'On Time'
ELSE 'Overdue'
END AS "Status"
FROM Orders

SELECT DATEDIFF(d,OrderDate,ShippedDate) AS "Days For Delivery",
CASE
WHEN DATEDIFF(d,OrderDate,ShippedDate) < 10
THEN 'On Time'
ELSE 'Overdue'
END AS "Status"
FROM Orders

SELECT *  FROM products

SELECT SUM(p.UnitsOnOrder) AS "Total On Order",
AVG(p.UnitsOnOrder) AS "Avg On Order",
MIN(p.UnitsOnOrder) AS "Min On Order",
MAX(p.UnitsOnOrder) AS "Max On Order"
FROM Products p

SELECT p.supplierID,
SUM(p.UnitsOnOrder) AS "Total On Order",
AVG(p.UnitsOnOrder) AS "Avg On Order",
MAX(p.UnitsOnOrder) AS "Max On Order"
FROM Products p
GROUP BY p.SupplierID

SELECT TOP 1 CategoryID,
AVG(ReorderLevel) AS "avg on reorder level"
FROM Products
GROUP BY CategoryID
ORDER BY "Avg on reorder level" DESC

SELECT p.supplierID,
SUM(p.UnitsOnOrder) AS "Total On Order",
AVG(p.UnitsOnOrder) AS "Avg On Order"
FROM Products p
GROUP BY p.SupplierID
HAVING AVG(UnitsOnOrder) > 5
ORDER BY "Total On Order"

SELECT p.SupplierID,s.CompanyName AS "Supplier Name", AVG(p.UnitsOnOrder) AS "Average Units On Order"
FROM Products p INNER JOIN Suppliers s
ON p.SupplierID=s.SupplierID
GROUP BY p.SupplierID, s.CompanyName

SELECT * FROM Suppliers

SELECT p.ProductName, p.UnitPrice, s.CompanyName AS "Supplier", CategoryName AS "Category"
FROM Products p
INNER JOIN Suppliers s ON p.SupplierID = s.SupplierID
INNER JOIN Categories c ON p.CategoryID = c.CategoryID

SELECT o.OrderID, o.OrderDate, o.Freight,
e.FirstName+' '+e.LastName AS "Employee Name",
c.CompanyName
FROM Orders o
INNER JOIN Customers c ON o.CustomersID = c.CustomerID
INNER JOIN Employees e ON o.EmployeeID = e.EmployeeID

```
