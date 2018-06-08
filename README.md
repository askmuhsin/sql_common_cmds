# SQL generally used commands
#### Install	-->	[link](https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial)
#### MySQL startup   -->	`mysql -u root -p`
#### Interview questions -->	[link](https://www.toptal.com/sql/interview-questions)
#### Useful Cheatsheet	-->	[link](https://github.com/treehouse/cheatsheets)
#### Create & Delete db
Check available dbs
```
SHOW DATABASES;
```
Create dbs
```
CREATE DATABASE db_name;
```
Delete dbs
```
DROP DATABASE db_name;
```
Access db
```
USE db_name;
```
See overview of the tables
```
SHOW tables;
```
#### db queries
_Comments_ in SQL (-- / /\*...\*/)
```
--Select all:
SELECT * FROM Customers;
```

_SELECT_ is used to select data from a db. The result is stored in a result-set.
```
SELECT * FROM table;
SELECT DISTINCT col_1, col_2 FROM table;
SELECT COUNT (col_name) FROM table;
SELECT * FROM table WHERE col_name='value';
SELECT * FROM table ORDER BY col_1 ASC, col_2 DESC;
```

_INSERT INTO_ statement is used to insert new **records** in a **table**.
```
INSERT INTO table_name (col_1, col_2, col_3) VALUES (val_1, val_2, val_3);
```
Inserting without specifying column name (make sure values are in same order).
```
INSERT INTO table_name VALUES (val_1, val_2, val_3, ...);
```
---

Combine _AND, OR and NOT_ with _WHERE_.
```
SELECT col_1, col_2 FROM table_name WHERE condition_1 AND condition_2 AND condition_3;
```
Example
```
SELECT * FROM Customers WHERE Country='Germany' AND (City='Berlin' OR City='Munchen');
```

The _MAX()_ function returns the largest value of the selected column.
The _MIN()_ returns minimum selected column.

_COUNT(), AVG(), SUM()_, return number of elements; avg, and sum returns on numerical vals.

_TOP_
```
SELECT TOP 3 * FROM col_name;
```

_LIMIT_
```
SELECT col_name
FROM table
WHERE condition
LIMIT 3;
```
---

The _LIKE_ operator is used in a _WHERE_ clause to search for a specified pattern in a column.
There are two wildcards used in conjunction with the LIKE operator:
% - The percent sign represents zero, one, or multiple characters
_ - The underscore represents a single character

_EXAMPLE_
```
WHERE CustomerName LIKE 'a%'    Finds any values that start with "a"
WHERE CustomerName LIKE '%a'    Finds any values that end with "a"
WHERE CustomerName LIKE '%or%'  Finds any values that have "or" in any position
WHERE CustomerName LIKE '_r%'   Finds any values that have "r" in the second position
WHERE CustomerName LIKE 'a_%_%' Finds any values that start with "a" and are at least 3 characters in length
WHERE ContactName LIKE 'a%o'    Finds any values that start with "a" and ends with "o"
```

---

_IN_ can be used as a shorthand from multiple OR conditions.
```
SELECT col_name
FROM table
WHERE col_name IN (val_1, val_2);
```
Similar _NOT IN_.

---

_BETWEEN_
```
SELECT * FROM Orders
WHERE OrderDate BETWEEN #07/04/1996# AND #07/09/1996#;
```

---

_Aliases_ can be useful when:

* There are more than one table involved in a query
* Functions are used in the query
* Column names are big or not very readable
* Two or more columns are combined together

```
SELECT column_name AS alias_name
FROM table_name;
Alias Table Syntax
SELECT column_name(s)
FROM table_name AS alias_name;

SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;

SELECT CustomerName, CONCAT(Address,', ',PostalCode,', ',City,', ',Country) AS Address
FROM Customers;
```

---

_SQL Joins_

SELECT column_name(s)
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;

SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM ((Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);

**Types of SQL Joins**
Here are the different types of the JOINs in SQL:

* (INNER) JOIN: Returns records that have matching values in both tables
* LEFT (OUTER) JOIN: Return all records from the left table, and the matched records from the right table
* RIGHT (OUTER) JOIN: Return all records from the right table, and the matched records from the left table
* FULL (OUTER) JOIN: Return all records when there is a match in either left or right table

![img_visual]()

---

_UNION_, _UNION ALL_
The UNION operator is used to combine the result-set of two or more SELECT statements.

* Each SELECT statement within UNION must have the same number of columns
* The columns must also have similar data types
* The columns in each SELECT statement must also be in the same order

```
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION ALL
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

---

_GROUP BY_
The GROUP BY statement is often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to group the result-set by one or more columns.
```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;
```

---

_HAVING_
The HAVING clause was added to SQL because the WHERE keyword could not be used with aggregate functions.

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

---

_EXISTS_
* The EXISTS operator is used to test for the existence of any record in a subquery.
* The EXISTS operator returns true if the subquery returns one or more records.
```
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```

---

The _SELECT INTO_ statement copies data from one table into a new table.

```
SELECT column1, column2, column3, ...
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;
```

The _INSERT INTO SELECT_ statement copies data from one table and inserts it into another table.
* INSERT INTO SELECT requires that data types in source and target tables match
* The existing records in the target table are unaffected
```
INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```

---

The MySQL _IFNULL()_ function lets you return an alternative value if an expression is NULL:
```
SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))
FROM Products
```

---
