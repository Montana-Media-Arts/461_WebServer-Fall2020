---
title: Basic Queries
module: 7
jotted: true
---

# Basic Queries

If you recall, we already started looking at these.  The basic syntax is as follows.

## SELECT

SELECT [column names] or * for all column names FROM [table name]

optionally you can add the following
- ORDER BY (you can also say ASC or DESC)
- WHERE [column name] (you can use =, <, >, <=, >=, !=)

Example:

```sql
SELECT * FROM pets ORDER BY PetName;

SELECT name, dob, breed, type, licenseNumber FROM pets ORDER BY PetName;

```

## INSERT

INSERT INTO [table name] (column names - you don't have to use them all unless they don't allow nulls) VALUES( the values are entered based on their data type)
- if the data type is a string, you must use single `'` quotes unless you use a variable.
- if you use a variable it is specified like this @variableName

Example:

```sql

INSERT INTO pets (name, dob, breed, type, licenseNumber) VALUES('Alice', '7/24/2020', 'Leonberger', 'dog', 3353322);

```

## UPDATE

UPDATE [table name]
SET [column name] = (value based on data type),
[column name] = (value based on data type),
... this continues for as many columns as you want to update.
WHERE [column name] (you can use =, <=,>=, != if the data type matches)
(if it's a string, you must use single `'` quotes)

Example:

```sql

UPDATE pets name = 'Olivia',
dob = '9/23/2012',
breed = 'King Charles',
type = 'dog'
licenseNumber = 329999
WHERE petID = 4;

```

## DELETE

DELETE FROM [table name]
WHERE [column name] (you can use =, <=,>=, != if the data type matches)
(if it's a string, you must use single `'` quotes)

Example:

```sql

DELETE FROM pets 
WHERE petID = 4;

```
