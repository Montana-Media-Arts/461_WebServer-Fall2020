---
title: Create First Database
module: 6
jotted: true
---

# Create

## MS SQL Server

Use MS Management Studio to create a database.  Expand the server and create a new database.

### Create Tables

Expand the new database and right-click and create a new table.  Add some columns and select save.

If you have trouble saving, follow these steps to get it to save:


To change the Prevent saving changes that require the table re-creation option, follow these steps:

1. Open SQL Server Management Studio (SSMS).
2. On the Tools menu, click Options.
3. In the navigation pane of the Options window, click Designers.
Select or clear the Prevent saving changes that require the table re-creation check box, and then click OK.

**Note** If you disable this option, you are not warned when you save the table that the changes that you made have changed the metadata structure of the table. In this case, data loss may occur when you save the table.

## MySQL

Open Workbench and then create a new Schema.  Their databases are called Schemas because it means the same thing as a database.  Give it a name and click Save.

### Create Tables

After the Schema is created, then right-click and create a new Table.  Let's add some columns with different datatypes and save the table.

