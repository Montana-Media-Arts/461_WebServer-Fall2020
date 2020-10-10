---
title: Change ASP.NET Code
module: 9
jotted: true
---

# What needs to be changed?

If this is our query in ASP.NET

```csharp
string myQuery = "SELECT SubjectID AS 'Subject ID', " +
                  " SubjectName as 'Subject Name' , " +
                "Active " +
                "FROM Subjects " +
                " ORDER BY SubjectName DESC";
```

This all gets put into a stored procedure and then the query looks like this

```csharp
string myQuery = "spGetAllSubjects";
```

Then, the following line also must be updated.

```csharp
myCommand.CommandType = CommandType.Text;
```

so that it looks like this now.

```csharp
myCommand.CommandType = CommandType.StoredProcedure;
```

Now, let's also change it so that there is a database class that we can refer and also helper classes so that we can get our data by calling a method in those class.

1. Create a database class and add the query types.
2. Create a secondary class that can be called in your main .cs file.

And that is it!
