---
title: Lookup Tables
module: 6
jotted: true
---

# Lookup Tables

## Define

Consider a situation, where an organization needs to maintain a database to store its employee information. A SQL table is created with the fields (Emp ID, Name, Membership). Only four membership options are present in the organization, so the membership field can hold a value out of the four different options. In case of thousand records, the membership field will be repeating among all the records and this field is a kind of static field, which does not change frequently. So, the user can choose to create a child table i.e., lookup table containing Emp id and membership fields of the main table. So, we can easily reference the fields of the child table with the main table of the database.

The following SQL query attempts to create a lookup table in SQL for the main table Employee:

CREATE TABLE Employee (EmpId int NOT NULL, name character varying NOT NULL, membership character varying NOT NULL );
CREATE TABLE links_type_lookup (EmpId int NOT NULL, membership character varying NOT NULL);
ALTER TABLE ONLY links_type_lookup ADD CONSTRAINT links_type_lookup_pkey PRIMARY KEY (EmpId);

Some of the features possessed by the lookup tables are:

They contain the descriptive data related to the main table.
They are relatively smaller than the main table.
They are generally insert-and-read tables as they are updated rarely.
They generally store data in the form of key-value pair.

## Importance

Importance of Using Lookup Tables in SQL Server
Lookup tables play a considerable role in maintaining the data integrity of the entire database. Users are advised to make use of lookup tables to easily manage large database. Some of the advantages of using lookup table in SQL are:

Storage Management
Since, lookup tables store the frequently repeating data as a reference to the main table. So, it prevents the repetition of same data in the main table and helps to save the memory.

Better Performance
When a query is made, the data can be easily referenced from the lookup table. So, it improves the performance of the system by utilizing less I/O resources, memory & CPU utilization.

Easy Data Modification
If any changes are to be made to a field, then they can be easily made at once on the lookup table. It will automatically update the referenced fields of the main table. So, in this way lookup tables help to easily modify the data by maintaining data integrity.

Faster Search
As the lookup table in SQL server has small size due to limited columns, so it becomes easy for user to search within the limited data from the lookup table and save time.

<a href="https://www.sqlmvp.org/lookup-table-in-sql-server/" target="_new">Source</a>