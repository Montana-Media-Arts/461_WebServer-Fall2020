---
title: Connect to PHP
module: 7
jotted: true
---


# Connect PHP to MySQL

In PHP, we use a different driver to connect to MySQL.

To connect to the database server, it would look like this.

```php
<?php

$servername = "localhost";
$username = "username";
$password = "password";

// Create connection
$conn = new mysqli($servername, $username, $password);

// Check connection
if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";

?>

```

After a connection is successfully made, then you can retrieve data.

```php
$sql = "SELECT name, dob, breed, type, licenseNumber FROM pets";

$result = $conn->query($sql);

if ($result->num_rows > 0) {
  // output data of each row
  while($row = $result->fetch_assoc()) {
    echo "name: " . $row["name"]. " - dob: " . $row["dob"]. " - breed: " . $row["breed"]. " - type: " . $row["type"]. " - license number " . $row["licenseNumber"]. "<br>";
  }
} else {
  echo "0 results";
}
$conn->close();
?>
```

# Connect PHP to MS SQL Server

What if we want to connect to a MS SQL Server in php?

```php
   function OpenConnection()  
    {  
        try  
        {  
            $serverName = "tcp:myserver.database.windows.net,1433";  
            $connectionOptions = array("Database"=>"pets",  
                "Uid"=>"MyUser", "PWD"=>"MyPassword");  
            $conn = sqlsrv_connect($serverName, $connectionOptions);  
            if($conn == false)  
                die(FormatErrors(sqlsrv_errors()));  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```

To get data out, it might look something like this

```php
function ReadData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
            $tsql = "SELECT * FROM pets";  
            $getPets = sqlsrv_query($conn, $tsql);  
            if ($getProducts == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
            $petCount = 0;  
            while($row = sqlsrv_fetch_array($getPets, SQLSRV_FETCH_ASSOC))  
            {  
                echo($row['name']);  
                echo("<br/>");  
                $petCount++;  
            }  
            sqlsrv_free_stmt($getPets);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```