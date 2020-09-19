---
title: Terminology
module: 6
jotted: true
---

# Terminology

## Database

a structured set of data held in a computer, especially one that is accessible in various ways.

<em>Oxford Languages</em>

## Tables

Tables are used to store data within the database.  They are its main component and without them, the database would serve little purpose. Tables are uniquely named within a database.  Many operations, such as queries use these names.  Typically a table is named to represent the type of data stored within.

For example, a table holding employee data may be called Employees. A table consists of rows and columns.  The columns are defined to house a specific data type, such as dates, numeric, or textual data.  Each column is also given a name.  Continuing with our example, an employee’s name may defined in the table as two columns as FirstName and LastName.

<a href="https://www.essentialsql.com/what-are-the-major-parts-of-a-database/" target="_new">Source</a>


## Columns

Columns are defined to hold a specific type of data, such as dates, numeric, or textual data.  In the simplest of definitions a column is defined by its name and data type.  The name is used in SQL statements when selecting and ordering data, and the data type is used to validate information stored.

So, a DateOfBirth column defined as a date, can be referred to in an order by clause as

ORDER BY DateOfBirth
And, if you try to add a value of “Hello Kitty” to the column, as part of its validation, it will recognize it isn’t a date, and reject it.

Columns names can’t be duplicated in a table.  So, having two “name” columns is a no no.  Though you could have two “name” columns, such as name1, and name2, you’ll learn later on, that this is frowned up, as it breaks normal form (I explain this in another post).


<a href="https://www.essentialsql.com/what-is-a-database-table/" target="_new">Source</a>

## Rows

A table can contain zero or more rows.  When there are zero, it said to be empty.  There is not practical limit on the number of rows a table can hold; however, remember the table’s primary key may have some influence on this.  What I mean, is that if your table holds states, and the primary key is the state’s abbreviation, then by definition, since there are only fifty states in the union, and you can not have duplicates in a primary key, your table is limited to fifty rows.


There is no guarantee that the rows in a table are stored in a particular order.  Use the ORDER BY clause to do so.

Also, strictly speaking, in a relational database there is no first or last row.  Yes, you can tease out a first row of a result using a keyword such as LIMIT or TOP, but those are used once the data is retrieved and sorted.  The difference here is that you’re seeing the first row of the result, not what is physically stored in the table.

<a href="https://www.essentialsql.com/what-is-a-database-table/" target="_new">Source</a>


### AutoIncrement

Auto Increment is a function that operates on numeric data types. It automatically generates sequential numeric values every time that a record is inserted into a table for a field defined as auto increment.

<a href="https://www.guru99.com/auto-increment.html#:~:text=Auto%20Increment%20is%20a%20function,field%20defined%20as%20auto%20increment." target="_new">Source</a>

## Keys

KEYS in DBMS is an attribute or set of attributes which helps you to identify a row(tuple) in a relation(table). They allow you to find the relation between two tables. Keys help you uniquely identify a row in a table by a combination of one or more columns in that table.

<a href="https://www.guru99.com/dbms-keys.html#:~:text=KEYS%20in%20DBMS%20is%20an,more%20columns%20in%20that%20table." target="_new">Source</a>

### Primary Key

What is a Primary Key?
PRIMARY KEY is a column or group of columns in a table that uniquely identify every row in that table. The Primary Key can't be a duplicate meaning the same value can't appear more than once in the table. A table cannot have more than one primary key.

Rules for defining Primary key:
Two rows can't have the same primary key value
It must for every row to have a primary key value.
The primary key field cannot be null.
The value in a primary key column can never be modified or updated if any foreign key refers to that primary key.
Example:

In the following example, <code>StudID</code> is a Primary Key.

StudID	Roll No	First Name	LastName	Email
1	11	Tom	Price	abc@gmail.com
2	12	Nick	Wright	xyz@gmail.com
3	13	Dana	Natan	mno@yahoo.com

<a href="https://www.guru99.com/dbms-keys.html#:~:text=KEYS%20in%20DBMS%20is%20an,more%20columns%20in%20that%20table." target="_new">Source</a>

### Foreign Key

FOREIGN KEY is a column that creates a relationship between two tables. The purpose of Foreign keys is to maintain data integrity and allow navigation between two different instances of an entity. It acts as a cross-reference between two tables as it references the primary key of another table.

Example:

DeptCode	DeptName
001	Science
002	English
005	Computer
Teacher ID	Fname	Lname
B002	David	Warner
B017	Sara	Joseph
B009	Mike	Brunton
In this key in dbms example, we have two table, teach and department in a school. However, there is no way to see which search work in which department.

In this table, adding the foreign key in Deptcode to the Teacher name, we can create a relationship between the two tables.

Teacher ID	DeptCode	Fname	Lname
B002	002	David	Warner
B017	002	Sara	Joseph
B009	001	Mike	Brunton
This concept is also known as Referential Integrity.

<a href="https://www.guru99.com/dbms-keys.html#:~:text=KEYS%20in%20DBMS%20is%20an,more%20columns%20in%20that%20table." target="_new">Source</a>

## Data Types

A database data type refers to the format of data storage that can hold a distinct type or range of values. When computer programs store data in variables, each variable must be designated a distinct data type. Some common data types are as follows: integers, characters, strings, floating point numbers and arrays.

<a href="https://teachcomputerscience.com/database-data-types/#:~:text=A%20database%20data%20type%20refers,floating%20point%20numbers%20and%20arrays." target="_new">Source</a>


## Indexes

Indexes are used to make data retrieval faster.  Rather than having to scan an entire table for data, an index allows the database to, essentially, directly retrieve the data being asked of it.  An index consists of keys, which in most cases directly relate to columns in a table.


For example, we could create an index using FirstName and LastName to make it quicker to look up employees by their name. Once common property of an index is uniqueness.  If an index is unique, then it can only contain unique values for its defined keys.  In our employee example, this wouldn’t be practical, as a company may have more than one John Smith working at it; however, it would make sense to create a unique index on employee number.

<a href="https://www.essentialsql.com/what-is-a-database-table/" target="_new">Source</a>

## Stored Procedures

There are many situations where queries alone are insufficient to solve a problem.  In these cases, developers rely on programming languages to process logic, to loop through records, and perform conditional comparisons as required.  These programs can be stored in the SQL database as stored procedures.

The language used to create the stored procedures are vendor specific.  T/SQL is the language used by Microsoft SQL Server; whereas, PL/SQL is used by Oracle. In each case the language provides the same basic abilities, such as being able to move record by record through a query, perform if-then logic, and call special built in functions to assist with complicated calculations.


<a href="https://www.essentialsql.com/what-is-a-database-table/" target="_new">Source</a>
