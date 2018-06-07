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


