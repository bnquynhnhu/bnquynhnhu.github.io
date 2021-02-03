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

# II. Select a storage mode
The three different types of storage modes you can choose from:
- Import: create a local Power BI copy of your datasets from your data source
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

### Query Folding
Convert M language to the native language of the source and the transformations happens on the source side instead of on locally on your machine in Power BI.

The idea behind Query Folding is to push the logic that you built into a Power BI query back to the data source server and execute it there in it’s native language instead of doing a client side transform of the data.  Why is this important?  Let me give you an example.  Say you have a 2 billion row SQL Server table you need to connect to in Power BI, but you want to filter to only return the last year of data.  With Query Folding the filter of that data is done on the SQL Server side instead of on the client side. If Query Folding did not take place then that would mean all 2 billion rows would be brought across the network only to then filtered out on the client workstation.  So clearly the ideal situation is that all your queries get folded for the best possible performance, but Query Folding only works in certain scenarios.
Here’s the scenarios where Query Folding does not take place:
- You are using an unsupported data source. This usually makes sense. For example, if you’re connecting to a flat file that there is no backend server that the queries can be run against.
- You are using an unsupported transform type.  Generally this makes sense too.  For example, if you’re connecting to a SQL Server data source and you select a tranform in the Query Editor that doesn’t exist in SQL Server.  Maybe you choose the transform Capitalize Each Word.  Now there are ways to accomplish this in SQL Server but there is not a native T-SQL function that can capitalize the first letter of every word in a field.
- You write your own source query. When you establish a connection in Power BI to a database

Watch this video "Power BI Tutorial for Beginners: Get Data. Query Editor" to understand more about Query Editor.
[![Power BI Tutorial for Beginners: Get Data. Query Editor]](https://www.youtube.com/watch?v=hw6-DNhgOos)
{% include youtube.html content="wIsK4kQTrIg" size="5" %}
![](/images/powerbi/get-data.png)

### Query diagnostics 
- To determine what bottlenecks exist while loading/transforming/refreshing data in Power Query, running SQL statements in Query Editor, etc.

### Other techniques to optimize performance  
- **Process as much data as possible in the original data source**. Power Query and Power Query Editor allow you to process the data; however, the processing power that is required to complete this task might lower performance in other areas of your reports. Generally, a good practice is to process, as much as possible, in the native data source.
- **Use native SQL queries**. When using DirectQuery for SQL databases, such as the case for our scenario, *make sure that you are not pulling data from stored procedures or common table expressions (CTEs)*.
- **Separate date and time**, if bound together. If any of your tables have columns that combine date and time, make sure that you separate them into distinct columns before importing them into Power BI. 

# IV. Resolve data import errors
Common errors you might have:
- Query timeout expired 
- Power BI Query Error: Timeout expired
- We couldn't find any data formatted as a table (open the Excel file, select the data set, and then press Ctrl+T, and then reopen the file)
- Could not find file 
- Data type errors: specìy 

Reference
- https://blog.pragmaticworks.com/power-bi-checking-query-folding-with-view-native-query

