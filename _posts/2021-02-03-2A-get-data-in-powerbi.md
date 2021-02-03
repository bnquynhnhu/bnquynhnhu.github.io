---
layout: post
title: Module 2A - Prepare data for analysis - Get data in Power BI
toc: 1
categories: [powerbi]
tags: [PowerBI,DA-100]
date: 2021-02-03
---

## I. Get data from different data sources:

![](/images/powerbi/get-data.png)

1.	Microsoft AppSource
  -	Data from services
    * SaaS services that you already use, e.g. Marketo, Salesforce, Github, GoogleAnalytics, SharePoint, OneDrive, Dynamics 365
    *	Growing number of supported SaaS solutions
  -	Data from your organization
    *	Content published by others in your org (organizational content packs)
2. Import or Connect to Data
  -	Database:
    *	Azure data services, e.g. Azure HDInsight (Hadoop), Azure Stream Analytics (ASA), Azure Machine Learning (AML) etc.
    *	Data sources on cloud such as Azure SQL Database, Azure SQL Data Warehouse and etc.
    *	On-premises data sources, such as SQL Server, Oracle, MySQL, etc.
  -	Data from files
    *	Import data from local files as Text, CSV, Excel and Power BI Desktop files.
    
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