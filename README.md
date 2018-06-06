# SQL generally used commands
### Install	--> [link](https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial)
### MySQL startup   --> `mysql -u root -p`
### Interview questions --> [link](https://www.toptal.com/sql/interview-questions)
### Create & Delete db
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
### db queries
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

Combine _AND, OR and NOT_ with _WHERE_.
```
SELECT col_1, col_2 FROM table_name WHERE condition_1 AND condition_2 AND condition_3;
```
Example
```
SELECT * FROM Customers WHERE Country='Germany' AND (City='Berlin' OR City='Munchen');
```
