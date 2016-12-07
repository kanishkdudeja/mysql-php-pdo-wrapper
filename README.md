## PHP PDO wrapper to connect to MySQL.

This PHP wrapper uses the [PHP PDO Library](http://php.net/manual/en/book.pdo.php) to connect to MySQL. The PHP PDO library prevents SQL Injection by using prepared statements.

### How to use this library?

1) Put your database configuration credentials in the file DBConfig.php
2) Include the DBWrapper.php file in your project, create an object of the DBWrapper class and start using it in your application.

### Sample usage

require_once 'DBWrapper.php'; //this will only work if the file is in the same folder as the executed file. If not, put the relative path here

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
