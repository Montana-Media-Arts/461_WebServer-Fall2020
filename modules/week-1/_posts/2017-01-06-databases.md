---
title: Databases
module: 1
---

# Databases

<div class="tab">
  <button class="tablinks" onclick="openTab(event, 'SQLServer')">MS SQL Server</button>
  <button class="tablinks" onclick="openTab(event, 'MySql')">MySQL</button>
   <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 </div>

<div id="SQLServer" class="tabcontent" style="display:block">
<p>Microsoft SQL Server is a relational database management system (RDBMS) that supports a wide variety of transaction processing, business intelligence and analytics applications in corporate IT environments. Microsoft SQL Server is one of the three market-leading database technologies, along with Oracle Database and IBM's DB2.</p>

<p>Like other RDBMS software, Microsoft SQL Server is built on top of SQL, a standardized programming language that database administrators (DBAs) and other IT professionals use to manage databases and query the data they contain. SQL Server is tied to Transact-SQL (T-SQL), an implementation of SQL from Microsoft that adds a set of proprietary programming extensions to the standard language.</p>

<p>Inside SQL Server's architecture—How SQL Server works  </p>         

<p>Like other RDBMS technologies, SQL Server is primarily built around a row-based table structure that connects related data elements in different tables to one another, avoiding the need to redundantly store data in multiple places within a database. The relational model also provides referential integrity and other integrity constraints to maintain data accuracy. Those checks are part of a broader adherence to the principles of atomicity, consistency, isolation and durability, collectively known as the ACID properties, and are designed to guarantee that database transactions are processed reliably.</p>

<p>The core component of Microsoft SQL Server is the SQL Server Database Engine, which controls data storage, processing and security. It includes a relational engine that processes commands and queries and a storage engine that manages database files, tables, pages, indexes, data buffers and transactions. Stored procedures, triggers, views and other database objects are also created and executed by the Database Engine.</p>

<p>Sitting beneath the Database Engine is the SQL Server Operating System, or SQLOS. SQLOS handles lower-level functions, such as memory and I/O management, job scheduling and locking of data to avoid conflicting updates. A network interface layer sits above the Database Engine and uses Microsoft's Tabular Data Stream protocol to facilitate request and response interactions with database servers. And at the user level, SQL Server DBAs and developers write T-SQL statements to build and modify database structures, manipulate data, implement security protections and back up databases, among other tasks.</p>

<p><a href="https://youtu.be/pF8n-8DPvjc" data-lity> What is SQL Server Video</a></p>

<p>SQL Server services, tools and editions</p>

<p>Microsoft also bundles a variety of data management, business intelligence (BI) and analytics tools with SQL Server. In addition to the R Services and now Machine Learning Services technology that first appeared in SQL Server 2016, the data analysis offerings include SQL Server Analysis Services, an analytical engine that processes data for use in BI and data visualization applications, and SQL Server Reporting Services, which supports the creation and delivery of BI reports.</p>

<p>On the data management side, Microsoft SQL Server includes SQL Server Integration Services, SQL Server Data Quality Services and SQL Server Master Data Services. Also bundled with the DBMS are two sets of tools for DBAs and developers: SQL Server Data Tools, for use in developing databases, and SQL Server Management Studio, for use in deploying, monitoring and managing databases.</p>

<p><a href="https://searchsqlserver.techtarget.com/definition/SQL-Server" target="_new"><em>Reference</em></a></p>
</div>

<div id="MySql" class="tabcontent">
<p>MySQL is a full-featured relational database management system (RDBMS) that competes with the likes of Oracle DB and Microsoft’s SQL Server. MySQL is sponsored by the Swedish company MySQL AB, which is owned by Oracle Corp. However, the MySQL source code is freely available because it was originally developed as freeware. MySQL is written in C and C++ and is compatible with all major operating systems.</p>

<p>MySQL was a free-software database engine originally developed and first released in 1995. MySQL is named after My, the daughter Michael Widenius, of one of the product’s originators. It was originally produced under the GNU General Public License, in which source code is made freely available.</p>

<p>MySQL is very popular for Web-hosting applications because of its plethora of Web-optimized features like HTML data types, and because it's available for free. It is part of the Linux, Apache, MySQL, PHP (LAMP) architecture, a combination of platforms that is frequently used to deliver and support advanced Web applications. MySQL runs the back-end databases of some famous websites, including Wikipedia, Google and Facebook- a testament to its stability and robustness despite its decentralized, free-for-all philosophy.</p>

<p>MySQL was originally owned by Sun Microsystems; when the company was purchased by Oracle Corp. in 2010, MySQL was part of the package. Although MySQL is technically considered a competitor of Oracle DB, Oracle DB is mainly used by large enterprises, while MySQL is used by smaller, more Web-oriented databases. In addition, MySQL differs from Oracle's product because it's in the public domain.</p>

<p><a href="https://www.techopedia.com/definition/3498/mysql" target="_new"><em>Reference</em></a></p>

</div>

<div id="ToDo" class="tabcontent">
    <p>Install the following</p>
    <ol>
        <li>Install <a href="https://go.microsoft.com/fwlink/?linkid=866662" target="_new">MS SQL Server</a></li>
        <li>Install <a href="https://dev.mysql.com/downloads/" target="_new">MySQL</a></li>
    </ol>
</div>