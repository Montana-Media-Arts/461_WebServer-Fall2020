---
title: Arguments
module: 10
jotted: true
---

# Arguments

This allows us to pass in different values into our queries.

## in or out

Here is an example of a single parameter.

```sql
CREATE PROCEDURE `spInsertNewPerson`(in firstname varchar(45))
BEGIN
 INSERT INTO people(firstname) VALUES(firstname);
END
```

Here is an example of multiple parameters.

```sql
CREATE PROCEDURE `spInsertNewPerson`(in firstname varchar(45), in lastname varchar(45),
 in username varchar(45), in pwd varchar(45))
BEGIN
 INSERT INTO people(firstname, lastname, username, pwd) VALUES(firstname, lastname, username, pwd);
END
```

