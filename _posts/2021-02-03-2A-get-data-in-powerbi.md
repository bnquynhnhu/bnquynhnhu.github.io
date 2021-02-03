---
layout: post
title: Module 2A - Prepare data for analysis - Get data in Power BI
toc: 1
categories: [powerbi]
tags: [PowerBI,DA-100]
date: 2021-02-03
---

## I. Get data from different data sources:

To connect data, you can just select the Get Data button in the lower-left corner of the home page.

![](/images/powerbi/get-data.png)

### 1.	Content Pack Library
  -	Data from services
    * SaaS services that you already use, e.g. Marketo, Salesforce, Github, GoogleAnalytics, SharePoint, OneDrive, Dynamics 365
    *	Growing number of supported SaaS solutions
  -	Data from your organization
    *	Content published by others in your org (organizational content packs)
### 2. Import or Connect to Data
  -	Database:
    *	Azure data services, e.g. Azure HDInsight (Hadoop), Azure Stream Analytics (ASA), Azure Machine Learning (AML) etc.
    *	Data sources on cloud such as Azure SQL Database, Azure SQL Data Warehouse and etc.
    *	On-premises data sources, such as SQL Server, Oracle, MySQL, etc.
  -	Data from files
    *	Import data from local files as Text, CSV, Excel and Power BI Desktop files.

After you connect to data source, you have the option to select the **Load** button to automatically load your data into the Power BI model without making any changes to it or select the Transform Data button to launch the Power Query Editor, where you can review and clean your data before loading it into the Power BI model.

# II. Get data from files
- Flat file: 
  * file has only one data table and every row of data is in the same structure. 
  * does not contain hierarchies.
- Which file location to export and store data: 
  * There are some options: Local (create new dataset, data is loaded, link does not remain), OneDrive business (any changes in data, auto-updated to PowerBI), OneDrive personal (same benefits as Buz, just need to sign in), SharePoint, etc.
  * Most effective way: SharePoint, OneDrive. If data is not changed regularly, saving files in local computer is OK.
- How to import?
  * Select "Get Data"
  * Selct File Type (Excel, SharePoint,...), select file, press "Open"
  * Select tables or entity
  * There are two options: Load (load data into PowerBI, no change), Transform (Review data, change data such as such as deleting unnecessary rows or columns, grouping your data, removing errors, etc)
- Change the source file:
  * Data source settings  
  * Query settings  
  * Advanced Editor 

# III. Get data from relational data sources
- Connect to many relational databases (in the cloud, on-premises)
- How to import?
  * Select "Get Data"
  * Enter your database server name and a database name (There is an option to choose "Import data by writing an SQL query" at this step)
  * Next step is to sign in with a username and password. There are three sign-in options: 
    . Windows - Use your Windows account (Azure Active Directory credentials).
    . Database - Use your database credentials.  
    . Microsoft account - Use your Microsoft account credentials. This option is often used for Azure services. 
  * Select tables or entity
  * There are two options: Load or Transform
- Change data source settings: Tranform Data -> Data Source Settings
- Write SQL:
  * avoid using the wildcard character to specify columns
  * queries should have a WHERE clause to filter
  * best practice: write query in a view

# IV. Get data from a NoSQL database
- NoSQL = non-SQL = not only SQL = non-relational
- Connect to a NoSQL database (Azure Cosmos DB) 
  * Select "Get Data" -> "Azure" -> "Azure Cosmo DB"
  * Enter  database credentials: URL (you can get the URL from the Keys blade of your Azure portal), database (optinal), collection (optinal). For the first time, you might be asked to input account key (Primary Key of your Azure portal)
  * If the connection is successful, a list of databases is displayed.
  * Select the table to import
  * To pull JSON element out, click "Edit" to open the records in Power Query.  
  * In Power Query, select the Expander button to the right side of the Column1 header, select the fields, it will blow up the JSON files.
  * Select Close & Apply to load the data into Power BI Desktop. 

# V. Get data from online services

# VI. Get data from Azure Analysis Services

# VII. Select a storage mode
The three different types of storage modes you can choose from:
- Import: 
  * Create a local Power BI copy of your datasets from your data source. 
  * Default option. 
  * This will import the data into Power BI on a scheduled interval (manually).
- DirectQuery: create a direct connnection to the data source. This method is useful when you do not want to save local copies of your data because your data is huge. With this mothode, your data is always up-to-date. However, its downside is the performance by having to load large amounts of data.
- Dual (Composite): you can identify some data to be directly imported and other data that must be queried.

<table>
  <thead>
    <tr>
      <th></th>
      <th>Import mode</th>
      <th>Direct query</th>
    </tr>
  </thead>
  <tr>
    <td>Size</td>
    <td>Up to 1GB per dataset </td>
    <td>Data is on-premise, no PowerBI service limitation</td>
  </tr>
  <tr>
    <td>Data Source</td>
    <td>Data come from multiple sources</td>
    <td>Data come from single source</td>
  </tr>
  <tr>
    <td>Performance</td>
    <td>No noticeable delay since the data model is already cached</td>
    <td>Slow in query response</td>
  </tr>
  <tr>
    <td>Refresh frequency</td>
    <td>Data refresh need to be done once in a day or week or month or interval of hours.0</td>
    <td>Near to real time data processing. Use if the objective is to always have fresh data.</td>
  </tr>
  <tr>
    <td>DAX</td>
    <td>DAX support</td>
    <td>Many limitations to DAX</td>
  </tr>
</table>

# III. Fix performance issues
There exists some techniques to optimize query performance:

### Optimize performance in Power Query

#### Query Folding
Convert M language to the native language of the source and the transformations happens on the source side instead of on locally on your machine in Power BI.

The idea behind **Query Folding** is to push the logic that you built into a Power BI query back to the data source server and execute it there in it’s native language instead of doing a client side transform of the data.  This technique is useful when dealing with huge dataset. 
Example: Instead of loading 2 billions rows of sales data to Power BI to filter only last year of data, with Query Folding, filter of that data is done on SQL Server side.

Here’s the scenarios where Query Folding does not take place:
- using an unsupported data source
- using an unsupported transform type
- You write your own source query.

#### Query diagnostics 
- To determine what bottlenecks exist while loading/transforming/refreshing data in Power Query, running SQL statements in Query Editor, etc.

#### Other techniques to optimize performance  
- **Process as much data as possible in the original data source**
- **Use native SQL queries**, *make sure not pulling data from stored procedures or common table expressions (CTEs)*.
- **Separate date and time**, if bound together. If any of your tables have columns that combine date and time, make sure that you separate them into distinct columns before importing them into Power BI. 

# IV. Resolve data import errors
Common errors you might have:
- **Query timeout expired**: config timespan 
- **Power BI Query Error: Timeout expired** = pulled too much data according to your organization’s policies =>  resolve by pulling fewer columns or rows from a single table, avoid using complex queries (group, aggregation, join, subquery, nested query) => implement them in Power BI
- We couldn't find any data formatted as a table (open the Excel file, select the data set, and then press Ctrl+T, and then reopen the file)
- Could not find file 
- Data type errors: convert column type explicitly by using CAST function in SQL (SELECT CAST(CustomerPostalCode as varchar(10)) FROM Sales.Customers)

Reference
- https://blog.pragmaticworks.com/power-bi-checking-query-folding-with-view-native-query

