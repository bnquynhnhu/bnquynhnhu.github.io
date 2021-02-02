---
layout: post
title: Get started building with Power BI
toc: 1
categories: [powerbi]
tags: [PowerBI,DA-100]
date: 2021-02-01
---

# I. Introduction of Power BI
- Is a collection of software services, apps, and connectors that work together to turn your unrelated sources of data into coherent, visually immersive, and interactive insights.

# II. The parts of Power BI

![](/images/powerbi/pbi-intro_02.png)

# III. The flow of work in Power BI
Here is a common workflow of Power BI:
- User creates a report in **Power BI Desktop**
- He/she then publishes the report to **Power BI Service** and then shares it to others
- Other users can view/consume the report on **Power BI Mobile apps**

# IV. Building Blocks in Power BI
- **Visualizations** is a visual representation of data, like a chart, a map, etc
- **Dataset** is a collection of data that Power BI uses to create its visualizations.
- **Reports** is a collection of visualizations that appears together on one or more pages. A reports has many pages, each page has many visualizations.
- **Dashboard** is a collection of visuals from a SINGLE PAGE that you can share with others. A dashboard must fit a single page, called canvas.
- **Tiles** is SINGLE VISUALIZATION from a report or dashboard. It is a rectangular box that holds an individual visual.

<table>
<thead>
  <tr>
    <th></th>
    <th>Import mode</th>
    <th>Direct query</th>
  </tr>
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
</thead>
