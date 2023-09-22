<h1 align="center"> MySQL Summary </h1>
<br><br>
Simple information about what I learned in MySQL.
<br><br>

### Accessing MySQL:

```
sudo mysql -u username -p
```

### Creating a user:


To create a user in a specific database, you should enter next command:

```
USER dbname;
```

Replace `dbname` with your specific database name.
User creation:

```
CREATE USER 'username'@'host' IDENTIFIED BY 'user_password';
```

Replace `user_password` with your password and `host` with your host.

### Grant privileges:


To grant all privileges for a user, next steps will show you how to do it.

* Grant all privileges on a specified database.

    ```
    GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'localhost';
    ```
    Replace `dbname` with your specific database name, `username` with your user name and `localhost` with your host.

* Grant all privileges on all databases.

    ```
    GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost';
    ```
    Replace `username` with your specific user name and `localhost` with your host.

* Grant SELECT privilege on a specified database.

    ```
    GRANT SELECT ON dbname.* TO 'username'@'localhost';
    ```
    Replace `dbname` with database name, `username` with the user name and `localhost` with your host.

And so on...


### Create:

To create users, databases and tables:

* Create databases:

    ```
    CREATE DATABASE dbname;
    ```
    Replace `dbname` with your database name.

* Create tables:

    ```
    CREATE TABLE tablename (column0 datatype, column1 datatype, ....);
    ```
    Replace `tablename` with table name, `column0, column1` with your column names and `datatype` with your data types.

### Use:

To use a specific database and execute commands on it.

* Use a database:

    ```
    USE dbname;
    ```
    `dbname`: the specific database name.

### Drop:

To drop ot ommit or delete a (database, table, column):

* Drop database:

    ```
    DROP DATABASE dbname;
    ```
    `dbname`: database name.

* Drop table:

    ```
    DROP TABLE tablename;
    ```
    `tablename`: table name.

### Rename:

To rename a (database, table, column):

* Rename a database:
    ```
    RENAME DATABASE dbname TO newname;
    ```
    - `dbname`: database name.
    - `newname`: the new database name.

* Rename a table:
    ```
    RENAME TABLE tablename TO newname;
    ```
    - `tablename`: the table name.
    - `newname`: the new table name.

* Rename a column:
    ```
    ALTER TABLE tablename;
    RENAME COLUMN oldname TO newname;
    ```
    - `tablename`: the table name.
    - `oldname`: the old column's name.
    - `newname`: the new column's name.

    ##### Remember:
    If you want to change the name of a column, you need to alter the `table` first.

### Modify:

To modify the data type of a column.

Let's suppose we have a database named `users`, let's create it.

```
CREATE DATABASE users;
```

And in this database contains a table of `employees`, let's create it.

```
CREATE TABLE employees (first_name VARCHAR(50), last_name VARCHAR(50), email INT);
```

In this table of `employees` we have a column of employees its type `INT`.

* Modify the column's datatype from `INT` to `VARCHAR(50)`:

    ```
    ALTER TABLE emplyees;
    MODIFY COLUMN email VARCHAR(50);
    ```

To modify the position of a column.

* Modify the position of `email` column to be first:

    ```
    ALTER TABLE employees;
    MODIFY email VARCHAR(50) FIRST;
    ```

* Modify the position of `email` column to be after `first_name`'s column:

    ```
    ALTER TABLE employees;
    MODIFY email VARCHAR(50) AFTER first_name;
    ```

* Modify the position of `email` column to be before `first_name`'s column:

    ```
    ALTER TABLE employees;
    MODIFY email VARCHAR(50) BEFORE first_name;
    ```

* Modify the position of `email` column to be last `first_name`'s column:

    ```
    ALTER TABLE employees;
    MODIFY email VARCHAR(50) LAST;
    ```


### Add:

To add a column into a table.

* Add column `id` into `employees` table:

    ```
    ALTER TABLE employees;
    ADD COLUMN id INT FIRST;
    ```

* Add a constaint to a specific column:

    ```
    ALTER TABLE employees ADD CONSTRAINT UNIQUE(column_name);
    ```

### Insert:

To insert data into a table, we user `INSERT` keyword.

* Let's insert some data into `employees` table:

    ```
    INSERT INTO employees (id INT, first_name VARCHAR(50), last_name VARCHAR(50))
    VALUES (0, "Abdelemjid", "Essaid", "abdelemjidessaid@gmail.com");
    ```
* Let's display data that inserted.

    ```
    SELECT * FROM employees;
    ```
    The result:

    ```
    +------+------------+-----------+
    | id   | first_name | last_name |
    +------+------------+-----------+
    |    0 | Abdelemjid | Essaid    |
    +------+------------+-----------+
    1 row in set (0.00 sec)
    ```


### Where:

To set a condition while (Inserting, Updating, Reading or Deleting) data from tables.

* For exmaple let's display the `first_name` of employee's id = 0:

    ```
    SELECT first_name FROM employees WHERE id = 0;
    ```
    The result:

    ```
    +------------+
    | first_name |
    +------------+
    | Abdelemjid |
    +------------+
    1 row in set (0.00 sec)
    ```

### Update:

To update data into a (database, table or column).

* Update the `last_name` of employee's `id` 0:

    ```
    UPDATE employees SET last_name = "Es-said" WHERE id = 0;
    ```
    Let's display the data:

    ```
    SELECT * FROM employees;
    ```
    The result:

    ```
    +------+------------+-----------+
    | id   | first_name | last_name |
    +------+------------+-----------+
    |    0 | Abdelemjid | Es-said   |
    +------+------------+-----------+
    1 row in set (0.00 sec)
    ```

### Delete:

To delete data from (Table, Column).

* Delete column's id of 0 from table of `employees`:

    ```
    DELETE FROM employees WHERE id = 0;
    ```
    Display data of emplyees table:

    ```
    SELECT * FROM employees;
    ```
    The result:

    ```
    +------+------------+-----------+
    | id   | first_name | last_name |
    +------+------------+-----------+
    0 row in set (0.00 sec)
    ```

### Autocommit:

In MySQL, autocommit is a configuration setting that determines whether each SQL statement is automatically committed or not. When autocommit is enabled, each individual SQL statement is treated as a transaction and is automatically committed immediately after it is executed. This means that changes made by the statement are permanently saved to the database.

By default, autocommit is usually enabled in MySQL. However, you can explicitly control the autocommit behavior using the following statements:

* Set autocommit to `on`:

    ```
    SET AUTOCOMMIT = 1;
    ```
    Or
    ```
    SET AUTOCOMMIT = ON;
    ```

* Set autocommit to `off`:

    ```
    SET AUTOCOMMIT = 0;
    ```
    Or
    ```
    SET AUTOCOMMIT = OFF;
    ```

### Commit:

In MySQL, the COMMIT statement is used to permanently save the changes made within an active transaction. It marks the end of the transaction and makes all the modifications made within the transaction permanent in the database.

* Let's `insert` some data into a employees table and `commit` changes:

    ```
    INSERT INTO employees VALUES (1, "Abderahim", "Essaid");
    COMMIT;
    ```

### Rollback:

In MySQL, the ROLLBACK statement is used to undo changes made in an active transaction and restore the database to its previous state. It discards all the modifications made within the transaction and releases any locks held during the transaction.

* Let's set `AUTOCOMMIT` mode to `OFF` and delete an employee of id = 0,
  then `ROLLBACK` to backup our data:

    ```
    SET AUTOCOMMIT = OFF;
    DELETE FROM employees;
    ```
    For example here we forgot to set the condition to delete the employee of id = 0, cause to lose all employees.

    So we need to `ROLLBACK` to backup our employees data.

    ```
    ROOLBACK;
    ```

    #### Remember:

    If `AUTOCOMMIT` statement was set to `ON` we could not backup our data.


### Current_date, Current_time and Now Functions:

To get the current time or current date or current datetime you should use these functions.

* Let's create a table the holds current_date, current_time and current_date_time:

    ```
    CREATE TABLE date_time (cur_date DATE, cur_time TIME, cur_date_time DATETIME);
    ```
    Let's user these 3 functions and display the result:

    ```
    INSERT INTO date_time VALUES (CURRENT_DATE(), CURRENT_TIME(), NOW());
    SELECT * FROM date_time;
    ```
    The result:

    ```
    +------------+----------+---------------------+
    | cur_date   | cur_time | cur_date_time       |
    +------------+----------+---------------------+
    | 2023-09-22 | 18:11:36 | 2023-09-22 18:11:36 |
    +------------+----------+---------------------+
    1 row in set (0.00 sec)

    ```


### Unique Constraint:

If you want to avoid dupplication in a table, you should set the specific column as `UNIQUE`.

* Let's create a table with `UNIQUE` column.

    ```
    CREATE TABLE products (
        product_id INT, 
        product_name VARCHAR(50) UNIQUE, 
        product_price DECIMAL(5, 2)
    );
    ```

    Let's insert some data int `products` table:

    ```
    INSERT INTO products VALUES 
    (0, "burger", 0.86),
    (1, "fries", 1.20),
    (2, "soda", 1.50),
    (3, "ice cream", 0.55);
    SELECT * FROM products;
    ```

    The result:

    ```
    +------------+--------------+---------------+
    | product_id | product_name | product_price |
    +------------+--------------+---------------+
    |          0 | burger       |          0.86 |
    |          1 | fries        |          1.20 |
    |          2 | soda         |          1.50 |
    |          3 | ice cream    |          0.55 |
    +------------+--------------+---------------+
    4 rows in set (0.00 sec)
    ```

    Let's try to insert an exist product:

    ```
    INSERT INTO products VALUES (4, "fries", 2.30);
    ```

    The result:

    ```
    ERROR 1062 (23000): Duplicate entry 'fries' for key 'products.product_name'
    ```

