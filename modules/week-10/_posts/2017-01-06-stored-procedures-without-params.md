---
title: Stored Procedures without parameters
module: 10
jotted: true
---

# What needs to be changed?

## SELECT FROM TABLE

Recall, getting information from a table using a direct query statement in PHP. Now, to call a stored procedure, it might look like this.

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "myDB";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);
}

$sql = "SELECT firstname, lastname, username, pwd FROM people";

$result = $conn->query($sql);

if ($result->num_rows > 0) {
  // output data of each row
  while($row = $result->fetch_assoc()) {
    echo "first name: " . $row["firstname"]. " - last name: " . $row["lastname"]. " - username: " . $row["username"]. " - pwd: " . $row["pwd"]. " -  "<br>"
  }
} else {
  echo "0 results";
}
$conn->close();
?>

```

So, how will it work now?  We have to use PDO to access our database.  What is PDO you say? Well here is what php.net says:

The PHP Data Objects (PDO) extension defines a lightweight, consistent interface for accessing databases in PHP. Each database driver that implements the PDO interface can expose database-specific features as regular extension functions. Note that you cannot perform any database functions using the PDO extension by itself; you must use a database-specific PDO driver to access a database server.

PDO provides a data-access abstraction layer, which means that, regardless of which database you're using, you use the same functions to issue queries and fetch data. PDO does not provide a database abstraction; it doesn't rewrite SQL or emulate missing features. You should use a full-blown abstraction layer if you need that facility.

Don't forget to uncomment the pdo_mysql extension in your php.ini file.  This allows us to call stored procedures. 

```php
$host = 'localhost'; 
$db = 'names';
$user = 'username';
$pass = 'pwd';

try {
    $pdo = new PDO("mysql:host=$host;dbname=$db", $user, $pass);
    
    // execute the stored procedure
    $sql = 'CALL spGetAllPeople()';
    
    // call the stored procedure
    $q = $pdo->query($sql);
    $q->setFetchMode(PDO::FETCH_ASSOC);

} catch (PDOException $e) {
    die("Error occurred:" . $e->getMessage());
}

while ($r = $q->fetch())
{
    echo $r['firstname'] . $r['lastname'] . "<br />";

}

```


