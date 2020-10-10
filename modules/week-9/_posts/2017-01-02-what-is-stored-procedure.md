---
title: What is a stored procedure?
module: 9
jotted: false
---

# Define

A stored procedure is a prepared SQL code that you can save, so the code can be reused over and over again.

So if you have an SQL query that you write over and over again, save it as a stored procedure, and then just call it to execute it.

You can also pass parameters to a stored procedure, so that the stored procedure can act based on the parameter value(s) that is passed.

## Example

```sql
CREATE PROCEDURE procedure_name
AS
sql_statement
GO;

EXEC procedure_name;
```

<a href="https://www.w3schools.com/sql/sql_stored_procedures.asp" target="_new">Source</a>

## Why use them?

There are at least four advantages I can think of to use an SP in a database application.

Firstly, it reduces the network traffic and overhead. In a typical PHP database web application, there are four layers:

1. The client layer, which is normally a web browser. It receives user interactions and presents the data in a UI.
2. The web server layer, which handles and dispatches user requests and sends back responses to the client layer.
3. The PHP layer, which handles all PHP interpretation, does the application logic and generates the PHP part of response.
4. The database layer, which handles all database queries, including but not limited to a SELECT query, an INSERT statement, etc.