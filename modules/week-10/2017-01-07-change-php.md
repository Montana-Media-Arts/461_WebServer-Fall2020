---
title: Change PHP pages
module: 9
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
$stmt = $conn->prepare("INSERT INTO MyGuests (firstname, lastname, email) VALUES (?, ?, ?)");
$stmt->bind_param("sss", $firstname, $lastname, $email);

// set parameters and execute
$firstname = "John";
$lastname = "Doe";
$email = "john@example.com";
$stmt->execute();

$firstname = "Mary";
$lastname = "Moe";
$email = "mary@example.com";
$stmt->execute();

$firstname = "Julie";
$lastname = "Dooley";
$email = "julie@example.com";
$stmt->execute();

echo "New records created successfully";

$stmt->close();
$conn->close();
?>
```

So, how will it work now?

```php
//Replace the below connection parameters to fit your environment
$host = '192.168.1.8'; 
$db = 'hris';
$user = 'tr';
$pass = 'mypass';
$dsn = "$dbms:host=$host;dbname=$db";

$cn=new PDO($dsn, $user, $pass);

$q=$cn->exec('call avg_sal(@out)');
$res=$cn->query('select @out')->fetchAll();
print_r($res);
```


