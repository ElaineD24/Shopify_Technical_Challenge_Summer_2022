# Question 2

## a)

```
SELECT COUNT(*) AS NumOrderBySpeedyExpress
From Orders
INNER JOIN Shippers
ON Orders.ShipperID = Shippers.ShipperID
WHERE Shippers.ShipperName = 'Speedy Express';
```

Answer: 54

## b)

```
SELECT LastName AS EmployeeWithMostOrders FROM Employees
WHERE EmployeeID = (SELECT EmployeeID FROM (SELECT EmployeeID, COUNT(EmployeeID)
					FROM Orders
					GROUP BY EmployeeID
					ORDER BY COUNT(OrderID) DESC));
```

Answer: Peacock

## c)

```
SELECT ProductName AS TopProductInGermany 
FROM (SELECT ProductName
FROM Orders AS o, OrderDetails AS od, Customers AS c, Products AS p
WHERE c.Country = 'Germany' AND od.OrderID = o.OrderID AND od.ProductID = p.ProductID AND c.CustomerID = o.CustomerID
GROUP BY p.ProductID
ORDER BY SUM(Quantity) DESC
LIMIT 1)
```

Answer: Boston Crab Meat

