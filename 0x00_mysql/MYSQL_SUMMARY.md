<h1 align="center"> MySQL Summary </h1>
<br><br>
Simple information about what I learned in MySQL.
<br><br>

### Accessing MySQL:

```
$ sudo mysql -u username -p
```

### Creating a user:


To create a user in a specific database, you should enter next command:

```
$ USER dbname;
```

Replace `dbname` with your specific database name.
User creation:

```
$ CREATE USER 'username'@'host' IDENTIFIED BY 'user_password';
```

Replace `user_password` with your password and `host` with your host.

### Grant privileges:


To grant all privileges for a user, next steps will show you how to do it.

* Grant all privileges on a specified database.

    ```
    $ GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'localhost';
    ```
    Replace `dbname` with your specific database name, `username` with your user name and `localhost` with your host.

* Grant all privileges on all databases.

    ```
    $ GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost';
    ```
    Replace `username` with your specific user name and `localhost` with your host.

* Grant SELECT privilege on a specified database.

    ```
    $ GRANT SELECT ON dbname.* TO 'username'@'localhost';
    ```
    Replace `dbname` with database name, `username` with the user name and `localhost` with your host.

And so on...


### Create:

To create users, databases and tables:

* Create databases:

    ```
    $ CREATE DATABASE dbname;
    ```
    Replace `dbname` with your database name.

* Create tables:

    ```
    $ CREATE TABLE tablename (column0 datatype, column1 datatype, ....);
    ```
    Replace `tablename` with table name, `column0, column1` with your column names and `datatype` with your data types.

### Use:

To use a specific database and execute commands on it.

* Use a database:

    ```
    $ USE dbname;
    ```
    `dbname`: the specific database name.

### Drop:

To drop ot ommit or delete a (database, table, column):

* Drop database:

    ```
    $ DROP DATABASE dbname;
    ```
    `dbname`: database name.

* Drop table:

    ```
    $ DROP TABLE tablename;
    ```
    `tablename`: table name.

### Rename:

To rename a (database, table, column):

* Rename a database:
    ```
    $ RENAME DATABASE dbname TO newname;
    ```
    - `dbname`: database name.
    - `newname`: the new database name.

* Rename a table:
    ```
    $ RENAME TABLE tablename TO newname;
    ```
    - `tablename`: the table name.
    - `newname`: the new table name.

* Rename a column:
    ```
    $ ALTER TABLE tablename;
    $ RENAME COLUMN oldname TO newname;
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
$ CREATE DATABASE users;
```

And in this database contains a table of `employees`, let's create it.

```
$ CREATE TABLE employees (email, INT);
```

In this table of `employees` we have a column of employees its type `INT`.

* Modify the column's datatype from `INT` to `VARCHAR(50)`:

    ```
    $ ALTER TABLE emplyees;
    $ MODIFY COLUMN email VARCHAR(50);
    ```
    