## PHP PDO wrapper to connect to MySQL.

This PHP wrapper uses the [PHP PDO Library](http://php.net/manual/en/book.pdo.php) to connect to MySQL. The PHP PDO library prevents SQL Injection by using prepared statements.

### How to use this library?

1) Put your database configuration credentials in the file DBConfig.php

2) Include the DBWrapper.php file in your project, create an object of the DBWrapper class and start using it in your application.

### Available functions

1) Select: This function is used to get results via the regular SQL SELECT command. Please note that this can not be used queries using joins as of now. It takes the following arguments:

a) table: String denoting the name of the table you want to query.
b) fields: Comma separated string for the fields you want in the result set. For example :- If you want to get id and name, you can pass this parameter as 'id, name'. If you want to get all the records in the table, you can use '*'. You can also use aggregation SQL functions like count(), sum(), max(), min() like 'count(*)'
c) condition parameters: This is an associative array used to denote the list of condition parameters used for evaluating the WHERE condition in the SQL command. For example :- Array('city'=>'chicago', 'is_active'=>1) will translate to "where city = 'chicago' and is_active = 1) in the SQL query.
d) group by: Comma separated string denoting the the fields you want to group the result by. For example, if you want to group the result set by the "city" field, you can pass this argument as "city". If you want to group the result set by the city and is_active field, you can pass this argument as "city, is_active"
e) limit: String for controlling the number of records returned by the SQL query. This uses the LIMIT expression functionality in SQL. If you want to get first 5 records, pass this argument as "LIMIT 5"
f) sort by: Comma separated string denoting the fields you want to sort the result set by. This uses the standard ORDER BY functionality in SQL. In order to order the result set by id increasing, pass this parameter as "id asc". If you want to order the result set by 2 parameters, you can pass a comma separated string such as "name asc, id desc"
g) fetch style: A constant denoting the result fetch mode. Default value is PDO::FETCH_ASSOC. For a list of fetch modes and their meaning, you can consult [this link](http://php.net/manual/en/pdostatement.fetch.php).

### Some notes

1) This wrapper uses the utf8mb4 encoding and the utf8mb4_unicode_ci collation for the database connection. You can change these if needed, in the constructor of DBWrapper class in DBWrapper.php

### Sample usage

#### Include the wrapper

```
require_once 'DBWrapper.php'; //this will only work if the file is in the same folder as the executed file. If not, put the relative path here
```

#### Connecting to the database

```
try {
	$db = new DBWrapper();

	//connection to the database succeeded. Now you can use $db to execute queries on the MySQL database.
}
catch(Exception $e) {
	//connecting to the database failed.
	//$e->getMessage() will contain the reason for the same
}
```
