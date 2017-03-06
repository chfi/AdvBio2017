## Part 1

Order the employees by who has been the best at selling the products supplied by New Orleans Cajun Delights.

```sql
SELECT Employees.FirstName,Employees.LastName,sum(OrderDetails.Quantity*Products.Price) AS TotalSoldValue
FROM OrderDetails
JOIN Orders
ON Orders.OrderID=OrderDetails.OrderID
JOIN Employees
ON Orders.EmployeeID=Employees.EmployeeID
JOIN Products
ON Products.ProductID=OrderDetails.ProductID
JOIN Suppliers
ON Suppliers.SupplierID=Products.SupplierID
WHERE Suppliers.SupplierID=2
GROUP BY Employees.EmployeeID
ORDER BY TotalSoldValue DESC;
```

## Part 2

```sql
CREATE TABLE Samples
(
SampleID INTEGER NOT NULL AUTO_INCREMENT,
PhenoA FLOAT,
PhenoB BOOLEAN NOT NULL,
PhenoC INTEGER,
PRIMARY KEY (SampleID)
);

CREATE TABLE Mutations
(
MutationID INTEGER NOT NULL AUTO_INCREMENT,
SampleID INTEGER NOT NULL,
Chromosome INTEGER NOT NULL,
Position INTEGER NOT NULL,
Genotype SMALLINT NOT NULL,
PRIMARY KEY (MutationID),
FOREIGN KEY (SampleID) REFERENCES Samples(SampleID)
);
```
