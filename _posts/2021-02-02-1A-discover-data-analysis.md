---
layout: post
title: Module 1A - Get started with Microsoft data analytics - Discover Data Analysis
toc: 1
categories: [powerbi]
tags: [PowerBI,DA-100]
date: 2021-02-01
---

## I. Overview of data analysis

Data analysis is the process of identifying, cleaning, transforming, and modeling data to discover meaningful and useful information. The data is then crafted into a story through reports for analysis to support the critical decision-making process.

To analyze data, core components of analytics are divided into the following categories:

{% include toc.html %}

![](/images/powerbi/advanced_analytics.png){:.w-500 .no-border}

### Descriptive Analytics
- Descriptive analytics help answer questions about what has happened based on historical data. Descriptive analytics techniques summarize large datasets to describe outcomes to stakeholders.
Examples: 
- Generate reports to provide a view of an organization's sales and financial data.

### Diagnostic Analytics
- Diagnostic analytics help answer questions about why events happened. Diagnostic analytics techniques supplement basic descriptive analytics, and they use the findings from descriptive analytics to discover the cause of these events.
- Steps to do:
a) Identify anomalies in the data
b) Collect data that's related to these anomalies
c) Use statistical technologies to discover relationships and trends that explain these anomalies.
- Techniques to use: scatter charts, corrrelations, etc

### Predictive Analytics: 
- Predictive analytics help answer questions about what will happen in the future. Predictive analytics techniques use historical data to identify trends and determine if they're likely to recur.
- Steps to do:
  1. Define the goal
  2. Prepare the data
  3. Find insights and visualize
  4. Deploy machine learning 
  5. Itterate
- Techniques to use: statistical and machine learning techniques as K-nearest neighbors, decision trees, neural networks and regression.

### Prescriptive Analytics
- Prescriptive analytics help answer questions about which actions should be taken to achieve a goal or target. By using insights from predictive analytics, organizations can make data-driven decisions. This technique allows businesses to make informed decisions in the face of uncertainty.
- Prescriptive analytics techniques rely on machine learning strategies to find patterns in large datasets.

### Cognitive Analytics
- Cognitive analytics attempt to draw inferences from existing data and patterns, derive conclusions based on existing knowledge bases, and then add these findings back into the knowledge base for future inferences, a self-learning feedback loop. Cognitive analytics help you learn what might happen if circumstances change and determine how you might handle these situations.

# II. Roles in Data
## Business Analyst
- Closer to the **business**
- Is a specialist in **interpreting the data** that comes from visualization
- Tools: Word, Excel, Power Point/MS Project

## Data Analyst
- Implement the **advanced analytics capabilities into reports and visualizations**
- Profile, clean, and transform data
- Is responsible for designing & building scalable & effective data models, manage Power BI assets (reports, dashboards, workspace, and the underlying datasets, etc)
- Work with Data Engineer and DB Admin.
- Most of the time, data analyst spend time to prepare and model tasks.
Note: Data Analyst and Business Analyst could be the single person

## Data Engineer
- Set up data platform technologies (on-premises, in the cloud)
- Manage and secure the flow of structured and unstructured data from multiples sources
- Data can include relational db, non relational db, data streams, and file stores
- Work with business stakeholder to identify & meet data requirements, and then design & implement solutions.

## Data Scientist
- Perform advanced analytics to extract value from data.  Their work can vary from descriptive analytics to predictive analytics. Descriptive analytics evaluate data through a process known as exploratory data analysis (EDA). Predictive analytics are used in machine learning to apply modeling techniques that can detect anomalies or patterns. These analytics are important parts of forecast models.

## DB Admin
- DB Admin manages the overall health of a db and the hardware that it resides on, manages the user access to the data.
- Database (Microsoft Azure Services, MS SQL)

# III. Tasks of Data Analyst
## Prepare data
- Data preparation is the process of profiling, cleaning, and transforming raw data into enriched, trusted, and understandable data to get it ready to model and visualize.
- Data preparation involves:
  + Process duplicate data
  + Correct wrong or inaccurate data
  + Identify missing data
  + Identify outliers
  + Identify inconsistent data
  
## Model
- Determine how tables are related to each other
- Define and create relationships between table
- Model has a **direct effect on the PERFORMANCE**
- Is an iterative process

## Visualize
- Translate information into a visual context, such as a map or graph, to make data easier for the human brain to understand and pull insights from. 
Note: - keep data small -> too much data can make detecting key point difficult

## Analyse
- Understand and interpret the info that is displayed on the report
- Use the analytical capabilities of PowerBI to find insights, identify patterns and trends, predict outcomes, and then communicate those insights in a way that everyone understand.

## Manage
- Data assets (reports, dashboards, workspace, dataset, etc)
- Grant right data assets to right peope
- Management of PowerBI assets reduce the duplication of efforts and ensure security of the data.
- Database (Microsoft Azure Services, MS SQL)

# IV. Check your knowledge
![](/images/powerbi/microsoft-quiz1.png){:.w-500 .no-border}

<fieldset class="field-set" markdown="1">
<legend class="leg-title">Title</legend>
Content
</fieldset>
