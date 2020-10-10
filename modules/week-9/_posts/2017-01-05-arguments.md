---
title: Arguments
module: 9
jotted: true
---

# Arguments

This allows us to pass in different values into our queries.

## @

Here is an example of a single parameter.

```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;
```

Here is an example of multiple parameters.

```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10)
AS
SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode
GO;
```

