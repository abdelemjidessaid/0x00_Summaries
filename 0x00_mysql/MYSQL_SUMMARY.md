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

Replace `user_password` with your password.

### Grant privileges:


To grant privileges for a user, next steps will show you how to do it.

* Grant all privileges on a specified database.

    ```
    $ GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'localhost';
    ```

Replace `dbname` with your specific database name.