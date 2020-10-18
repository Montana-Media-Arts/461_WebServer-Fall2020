---
title: Stored Procedures with parameters
module: 10
jotted: true
---

# What needs to be changed?

## Inserting into a table

One thing, we should be mindful about is parameters.  From this example of inserting, we can learn a lot about the fields that will be analyzed before they are displyed. 

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

// prepare and bind
$stmt = $conn->prepare("INSERT INTO names (firstname, lastname, username) VALUES (?, ?, ?)");
$stmt->bind_param("sss", $firstname, $lastname, $username);

// set parameters and execute
$firstname = "John";
$lastname = "Doe";
$username = "john@example.com";
$stmt->execute();

$firstname = "Mary";
$lastname = "Moe";
$username = "mary@example.com";
$stmt->execute();

echo "New records created successfully";

$stmt->close();
$conn->close();
?>
```

So, how will it work now?

```php
//Replace the below connection parameters to fit your environment
$host = 'localhost'; 
$db = 'names';
$user = 'username';
$pass = 'pwd';
$dsn = "mysql:host=$host;dbname=$db";

$cn=new PDO($dsn, $user, $pass);

$firstname = "Bob";
$lastname = "Jones";
$username = "bob.jones@test.com";
$pwd = "test123";

$sql = 'CALL spInsertNewPerson(:firstname, :lastname, :username, :pwd)';

$stmt = $cn->prepare($sql);

$stmt->bindParam(':firstname', $firstname, PDO::PARAM_STR);
$stmt->bindParam(':lastname', $lastname, PDO::PARAM_STR);
$stmt->bindParam(':username', $username, PDO::PARAM_STR);
$stmt->bindParam(':pwd', $pwd, PDO::PARAM_STR);

$stmt->execute();
$stmt->closeCursor();

```


