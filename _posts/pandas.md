### Importing Libraries 

Let’s start by importing several libraries we’ll need for exploring our
data and cleaning textual data

1.  **Pandas:** We will need Pandas to navigate our dataframe and check
    for each column’s data type, null values, and unique values.

2.  **NumPy:** This package is essential for any data science project.
    It has a lot of mathematical functions that operate on
    multi-dimensional arrays and data frames.

3.  **Matplotlib & Seaborn:** They are plotting and graphing libraries
    that we will use to visualize data in an intuitive way.

> \# Importing necessary libraries
> 
> import pandas as pd
> 
> import numpy as np
> 
> import matplotlib.pyplot as plt
> 
> import seaborn as sns
> 
> pd.set\_option('display.max\_rows', 500)
> 
> pd.set\_option('display.max\_columns', 500)
> 
> %matplotlib inline

1.  Loading the data

> df = pd.read\_csv("filename1.csv")

<table>
<thead>
<tr class="header">
<th>Steps</th>
<th></th>
<th>Python</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li><p>View dataset</p></li>
</ol></td>
<td>To learn quickly your object.</td>
<td><p># To see first 5 rows of dataset</p>
<p>df.head()</p>
<p># Returns the dimensionality of the DataFrame</p>
<p>df.shape</p></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li><p>Data structure</p></li>
</ol></td>
<td>Using <strong>df.dtypes</strong> for analyzing for columns/data types</td>
<td><p>df. dtypes</p>
<p><img src="media/image1.png" style="width:3.21875in;height:0.82292in" /></p></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td><ol type="a">
<li><p>Drop unnecessary columns</p></li>
</ol></td>
<td><p># There are several features that we don't need.</p>
<p># Let's drop them.</p>
<p>df.drop(['col1', 'col2'], axis=1, inplace=True)</p></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td><ol start="2" type="a">
<li><p>Rename columns</p></li>
</ol></td>
<td><p>df.rename(columns={'oldName1': 'newName1',</p>
<p>'oldName2': 'newName2'},</p>
<p>inplace=True)</p></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td><ol start="3" type="a">
<li><p>Change data type of a column</p></li>
</ol></td>
<td><p><em># Convert the column &quot;col1&quot; to numeric</em></p>
<p># df['col1'] = df['col1'].str.replace(',', '')</p>
<p>df['col1'] = pd.to_numeric(df['col1'])</p>
<p><em># Convert the column &quot;col1&quot; to int32</em></p>
<p>df.astype({['col1', 'col2']: 'int32'}).dtypes</p></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li><p>Dealing with datetime</p></li>
</ol></td>
<td></td>
<td><p># Convert object type to datetime type</p>
<p>pd.to_datetime(df.column_name)</p>
<p># Combine date and time columns</p>
<p>combined = df.date_column.str.cat(df.time_column, sep=' ')</p>
<p>df['combined_column'] = pd.to_datetime(combined)</p></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li><p>Dealing with missing data</p></li>
</ol></td>
<td>Using <strong>df.isnull().sum()</strong> to find missing values of each feature in the dataset</td>
<td><p># Find missing values of each feature in the data set.</p>
<p>df.isnull().sum()</p>
<p># Examine missing values</p>
<p>df[df['bathrooms'].isnull()]</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Some common methods for dealing with missing values include:</p>
<ul>
<li><p>dropping instances</p></li>
<li><p>dropping attributes</p></li>
<li><p>imputing the attribute mean/median, mode for all missing values</p></li>
<li><p>using regression to impute attribute missing values</p></li>
</ul>
<p><strong>df.dropna()</strong></p>
<p>Drop rows with any column having NA/null data</p>
<p><strong>df.fillna(value)</strong></p>
<p>Replace all NA/null data with value.</p></td>
<td><p># Drop all rows having missing values</p>
<p>df.drop(df.index[[index1, index2]], inplace=True)</p>
<p># Drop all <strong>rows and columns</strong> where <strong>ALL</strong> elements are missing values:</p>
<p>df.dropna(how='all')</p>
<p># Drop the <strong>columns</strong> that only contains missing values/ drop a specified column</p>
<p>df.dropna(axis='columns', how='all')</p>
<p>df.drop('col1', axis='columns', inplace=True)</p>
<p># Fill all missing values with replaced value (mean, 0, median, etc)</p>
<p>df['col1'] = df['col1'].fillna(df['col1'].median())</p>
<p>df = df.fillna(0)</p>
<p># To check the result, display list of columns</p>
<p>df.columns</p></td>
</tr>
<tr class="odd">
<td><ol start="8" type="1">
<li><p>Replacing values</p></li>
</ol></td>
<td></td>
<td><p># Argument passed can also be a dictionary with separate values</p>
<p>df = df.replace({oldValue1: newValue1, oldValue2: newValue2}, inplace=True)</p></td>
</tr>
<tr class="even">
<td><ol start="9" type="1">
<li><p>Categories to numbers</p></li>
</ol></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="10" type="1">
<li><p>Dealing with Outliers</p></li>
</ol></td>
<td></td>
<td><p>df.describe()</p>
<p>df.col1.min(), df.col2.max()</p>
<p># Visualize top 10</p>
<p>top_10 =</p></td>
</tr>
<tr class="even">
<td></td>
<td>To get a feel for the type of data we are dealing with, we plot a histogram for each numeric variable.</td>
<td><p>%matplotlib inline</p>
<p>df.hist(bins=50, figsize=(20,15))</p>
<p>plt.savefig(&quot;attribute_histogram_plots&quot;)</p>
<p>plt.show()</p></td>
</tr>
<tr class="odd">
<td></td>
<td>2.6. Reset index of dataframe, if necessary</td>
<td><p># Reset index of DataFrame to row numbers, moving index to columns</p>
<p>df.reset_index()</p></td>
</tr>
</tbody>
</table>

Filter

<table>
<thead>
<tr class="header">
<th><ol start="3" type="1">
<li><p>String comparaison</p></li>
</ol></th>
<th><p>df.query(&quot;column_name=='search_value'&quot;)</p>
<p># Using with variable</p>
<p>var = 45</p>
<p>df.query('column_name == @var')</p>
<p># With AND/OR</p>
<p>df.query(&quot;(col1=='value1') or (col2=='val2')&quot;)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li><p>String comparaison</p></li>
</ol></td>
<td><p>1. To find all the values from the series that <strong>starts</strong> with a pattern &quot;s&quot;:</p>
<p>SQL - WHERE column_name LIKE 's%'</p>
<p>Python - column_name.str.startswith('s')</p>
<p>2. To find all the values from the series that <strong>ends</strong> with a pattern &quot;s&quot;:</p>
<p>SQL - WHERE column_name LIKE '%s'</p>
<p>Python - column_name.str.endswith('s')</p>
<p>3. To find all the values from the series that <strong>contains</strong> pattern &quot;s&quot;:</p>
<p>SQL - WHERE column_name LIKE '%s%'</p>
<p>Python - column_name.str.contains('s')</p>
<p>Return :</p>
<p>NaN if value is missing</p>
<p>True if there is a match</p>
<p>False if there is not</p></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td></td>
</tr>
</tbody>
</table>

References:

<http://www.theanalysisfactor.com/outliers-to-drop-or-not-to-drop/>

<https://www.datacamp.com/community/tutorials/data-preparation-with-pandas>

<https://datascienceplus.com/linear-regression-in-python-predict-the-bay-areas-home-prices/>

<https://medium.com/@arpitpathak114/data-preprocessing-with-numpy-and-pandas-5598ef69491e>

<https://www.kdnuggets.com/2017/06/7-steps-mastering-data-preparation-python.html/2>
