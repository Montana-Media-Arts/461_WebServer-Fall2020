---
title: Connect ASP.NET
module: 7
jotted: false
---

# Connect MS SQL Server to ASP.NET

This needs to go in the web.config file inside the configuration tag.

```xml
 <connectionStrings>
    <add name="ConnectionString" connectionString="Data Source=(local);Initial Catalog=<databasename>;user id=; password=" providerName="System.Data.SqlClient" />
  </connectionStrings>

```

Your file will require the following imports.

```csharp
using System.Configuration;
using System.Data;
using System.Data.SqlClient;
```

Then, we need to connect to our database like this:

```csharp
string myConnectionString = ConfigurationManager.ConnectionStrings["ConnectionString"].ToString();
SqlConnection myConnection;

myConnection = new SqlConnection(myConnectionString);
myConnection.Open();

```

To execute a SELECT, we need the following

```csharp
string myQuery = "SELECT * FROM pets";

DataSet myDataSet = new DataSet();
SqlCommand myCommand = new SqlCommand(myQuery);
myCommand.Connection = myConnection;
myCommand.CommandType = CommandType.Text;

SqlDataAdapter myAdapter = new SqlDataAdapter(myCommand);
myAdapter.Fill(myDataSet);
myConnection.Close();

dataGrid.DataSource = myDataSet.Tables[0];
dataGrid.DataBind();

```

Then, we can get specific data out of the dataset like an array.

```csharp
 
 txtPetName.Text = myDataSet.Tables[0].Rows[0]["name"].ToString();

```

# Connect MySQL to ASP.NET

First, you need the <a href="https://dev.mysql.com/downloads/connector/net/" target="_new">MySQL Connector</a>.

This time the connection string is a little different because of the port

```xml

<connectionStrings>
    <add name="constr" connectionString="Data Source=localhost;port=3306;Initial Catalog=SampleDB;User Id=mudassar;password=pass@123"/>
</connectionStrings>

```

Your page will require the following imports.

```csharp

using System.Data;
using System.Configuration;
using MySql.Data.MySqlClient;

```

To open the database, it would look like this.

```csharp
string myConnectionString = ConfigurationManager.ConnectionStrings["ConnectionString"].ToString();
MySqlConnection myConnection;

myConnection = new MySqlConnection(myConnectionString);
myConnection.Open();


```

Then, to get data out and display it on the page, it will look like this


```csharp
    
    string myQuery = "SELECT * FROM pets";

    DataSet myDataSet = new DataSet();
    MySqlCommand myCommand = new MySqlCommand(myQuery);
    myCommand.Connection = myConnection;
    myCommand.CommandType = CommandType.Text;

    MySqlDataAdapter myAdapter = new MySqlDataAdapter(myCommand);
    myAdapter.Fill(myDataSet);
    myConnection.Close();

    dataGrid.DataSource = myDataSet.Tables[0];
    dataGrid.DataBind();
            
```
