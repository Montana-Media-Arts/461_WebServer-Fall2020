---
title: Abstract the Code
module: 10
jotted: true
---

# Abstract the code

Just like in other languages, we don't want to duplicate code if we don't have to.  So, we are going to separate out our code into different files and then include them.

Let's take the following.

```php
$servername = "localhost";
$username = "username";
$password = "pwd";
$dbname = "names";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);
```

And put that into it's own file and give it a name like **mysqliconnection.php**.

Now, in a file which needs this database connection, we can add the following line.

```php
<?php require('mysqliconnection.php'); ?>
```

We can do the same thing for our PDO connection.

This code.

```php
$host = 'localhost'; 
$db = 'names';
$user = 'username';
$pass = 'pwd';
$dsn = "mysql:host=$host;dbname=$db";

$cn=new PDO($dsn, $user, $pass);
```

Can go into a new file called **pdoconnection.php**

and then the required statement might look like this.

```php
<?php require('pdoconnection.php'); ?>
```


