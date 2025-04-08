# SQL-Basics
This covers the SQL Basics with examples on how it is done and pictorial representation of what it achieved using MYSQL.


The basic SQL topics to be covered include

[CREATE DATABASE](#create-database)

[DROP DATABASE](#drop-database)

[CREATE TABLE](#create-table)

[SELECT](#select)

[INSERT](#insert)
  

  ## CREATE DATABASE
`CREATE DATABASE IF NOT exists database_name;`


  Example 1- 
  ```sql
CREATE DATABASE IF NOT exists employees;
```
  ![image](https://github.com/user-attachments/assets/d20f3fac-7879-4d38-8ef4-85c85ad55e93)

## DROP DATABASE 
`DROP database_name;`
Example 1- 
```sql
DROP DATABASE employees;
```
![image](https://github.com/user-attachments/assets/90f63598-e76e-4a04-aa12-683c0c730c0a)

## CREATE TABLE
`CREATE TABLE IF NOT EXISTS table_name(column_name1 data_type constraints, column_name2 data_type constraints,...);`
Example 1- 
```sql
CREATE TABLE IF NOT EXISTS sales (
    Purchase_number INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    Date_of_purchase DATE NOT NULL,
    Customer_id INT,
    Item_code VARCHAR(10) NOT NULL
); 
```
![image](https://github.com/user-attachments/assets/239ca4fc-c96c-4ba6-9b2a-194cff6d471f)


Example 2- 
```sql
CREATE TABLE IF NOT EXISTS customers (
    'customer_id' INT NOT NULL,
    first_name VARCHAR(255),
    last_name VARCHAR(255),
    email_address VARCHAR(255),
    number_of_complaints INT DEFAULT 0
); 
```
![image](https://github.com/user-attachments/assets/74339827-9e28-42f7-8d56-b1d1070471d0)



## Exercises
Exercise 1- I will be setting up an entire database as in the picture below
![image](https://github.com/user-attachments/assets/7701eed5-84a8-4c83-9db6-24a3191f471a)

### Solution
```sql
CREATE DATABASE IF NOT EXISTS orders;

USE orders;

CREATE TABLE IF NOT EXISTS warehouse (
    warehouse_id INT PRIMARY KEY,
    warehouse_location VARCHAR(20)
);

CREATE TABLE IF NOT EXISTS products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(20),
    product_price INT,
    warehouse_id INT,
    FOREIGN KEY (warehouse_id)
        REFERENCES warehouse (warehouse_id)
);

CREATE TABLE IF NOT EXISTS deliveries (
    delivery_id INT PRIMARY KEY,
    delivery_date DATE,
    warehouse_id INT,
    FOREIGN KEY (warehouse_id)
        REFERENCES warehouse (warehouse_id)
);

CREATE TABLE IF NOT EXISTS order_info (
    order_info_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    product_quantity INT,
    FOREIGN KEY (product_id)
        REFERENCES products (product_id)
);

CREATE TABLE IF NOT EXISTS orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    order_date DATE,
    order_info_id INT,
    order_value INT,
    order_currency VARCHAR(10),
    FOREIGN KEY (order_info_id)
        REFERENCES order_info (order_info_id)
);
```

