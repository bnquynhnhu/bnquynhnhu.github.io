### Importing Libraries 

Let's start by importing several libraries we'll need for exploring our
data and cleaning textual data

1.  **Pandas:** We will need Pandas to navigate our dataframe and check
    for each column's data type, null values, and unique values.

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
> pd.set\_option(\'display.max\_rows\', 500)
>
> pd.set\_option(\'display.max\_columns\', 500)
>
> \%matplotlib inline

1.  Loading the data

> df = pd.read\_csv(\"filename1.csv\")

+-----------------------+-----------------------+-----------------------+
| Steps                 |                       | Python                |
+=======================+=======================+=======================+
| 1.  View dataset      | To learn quickly your | \# To see first 5     |
|                       | object.               | rows of dataset       |
|                       |                       |                       |
|                       |                       | df.head()             |
|                       |                       |                       |
|                       |                       | \# Returns the        |
|                       |                       | dimensionality of the |
|                       |                       | DataFrame             |
|                       |                       |                       |
|                       |                       | df.shape              |
+-----------------------+-----------------------+-----------------------+
| 2.  Data structure    | Using **df.dtypes**   | df. dtypes            |
|                       | for analyzing for     |                       |
|                       | columns/data types    | ![](media/image1.png) |
|                       |                       | {width="3.21875in"    |
|                       |                       | height="0.82291666666 |
|                       |                       | 66666in"}             |
+-----------------------+-----------------------+-----------------------+
| 3.                    | a)  Drop unnecessary  | \# There are several  |
|                       |     columns           | features that we      |
|                       |                       | don\'t need.          |
|                       |                       |                       |
|                       |                       | \# Let\'s drop them.  |
|                       |                       |                       |
|                       |                       | df.drop(\[\'col1\',   |
|                       |                       | \'col2\'\], axis=1,   |
|                       |                       | inplace=True)         |
+-----------------------+-----------------------+-----------------------+
| 4.                    | b)  Rename columns    | df.rename(columns={\' |
|                       |                       | oldName1\':           |
|                       |                       | \'newName1\',         |
|                       |                       |                       |
|                       |                       | \'oldName2\':         |
|                       |                       | \'newName2\'},        |
|                       |                       |                       |
|                       |                       | inplace=True)         |
+-----------------------+-----------------------+-----------------------+
| 5.                    | c)  Change data type  | *\# Convert the       |
|                       |     of a column       | column \"col1\" to    |
|                       |                       | numeric*              |
|                       |                       |                       |
|                       |                       | \# df\[\'col1\'\] =   |
|                       |                       | df\[\'col1\'\].str.re |
|                       |                       | place(\',\',          |
|                       |                       | \'\')                 |
|                       |                       |                       |
|                       |                       | df\[\'col1\'\] =      |
|                       |                       | pd.to\_numeric(df\[\' |
|                       |                       | col1\'\])             |
|                       |                       |                       |
|                       |                       | *\# Convert the       |
|                       |                       | column \"col1\" to    |
|                       |                       | int32*                |
|                       |                       |                       |
|                       |                       | df.astype({\[\'col1\' |
|                       |                       | ,                     |
|                       |                       | \'col2\'\]:           |
|                       |                       | \'int32\'}).dtypes    |
+-----------------------+-----------------------+-----------------------+
| 6.  Dealing with      |                       | \# Convert object     |
|     datetime          |                       | type to datetime type |
|                       |                       |                       |
|                       |                       | pd.to\_datetime(df.co |
|                       |                       | lumn\_name)           |
|                       |                       |                       |
|                       |                       | \# Combine date and   |
|                       |                       | time columns          |
|                       |                       |                       |
|                       |                       | combined =            |
|                       |                       | df.date\_column.str.c |
|                       |                       | at(df.time\_column,   |
|                       |                       | sep=\' \')            |
|                       |                       |                       |
|                       |                       | df\[\'combined\_colum |
|                       |                       | n\'\]                 |
|                       |                       | =                     |
|                       |                       | pd.to\_datetime(combi |
|                       |                       | ned)                  |
+-----------------------+-----------------------+-----------------------+
| 7.  Dealing with      | Using                 | \# Find missing       |
|     missing data      | **df.isnull().sum()** | values of each        |
|                       | to find missing       | feature in the data   |
|                       | values of each        | set.                  |
|                       | feature in the        |                       |
|                       | dataset               | df.isnull().sum()     |
|                       |                       |                       |
|                       |                       | \# Examine missing    |
|                       |                       | values                |
|                       |                       |                       |
|                       |                       | df\[df\[\'bathrooms\' |
|                       |                       | \].isnull()\]         |
+-----------------------+-----------------------+-----------------------+
|                       | Some common methods   | \# Drop all rows      |
|                       | for dealing with      | having missing values |
|                       | missing values        |                       |
|                       | include:              | df.drop(df.index\[\[i |
|                       |                       | ndex1,                |
|                       | -   dropping          | index2\]\],           |
|                       |     instances         | inplace=True)         |
|                       |                       |                       |
|                       | -   dropping          | \# Drop all **rows    |
|                       |     attributes        | and columns** where   |
|                       |                       | **ALL** elements are  |
|                       | -   imputing the      | missing values:       |
|                       |     attribute         |                       |
|                       |     mean/median, mode | df.dropna(how=\'all\' |
|                       |     for all missing   | )                     |
|                       |     values            |                       |
|                       |                       | \# Drop the           |
|                       | -   using regression  | **columns** that only |
|                       |     to impute         | contains missing      |
|                       |     attribute missing | values/ drop a        |
|                       |     values            | specified column      |
|                       |                       |                       |
|                       | **df.dropna()**       | df.dropna(axis=\'colu |
|                       |                       | mns\',                |
|                       | Drop rows with any    | how=\'all\')          |
|                       | column having NA/null |                       |
|                       | data                  | df.drop(\'col1\',     |
|                       |                       | axis=\'columns\',     |
|                       | **df.fillna(value)**  | inplace=True)         |
|                       |                       |                       |
|                       | Replace all NA/null   | \# Fill all missing   |
|                       | data with value.      | values with replaced  |
|                       |                       | value (mean, 0,       |
|                       |                       | median, etc)          |
|                       |                       |                       |
|                       |                       | df\[\'col1\'\] =      |
|                       |                       | df\[\'col1\'\].fillna |
|                       |                       | (df\[\'col1\'\].media |
|                       |                       | n())                  |
|                       |                       |                       |
|                       |                       | df = df.fillna(0)     |
|                       |                       |                       |
|                       |                       | \# To check the       |
|                       |                       | result, display list  |
|                       |                       | of columns            |
|                       |                       |                       |
|                       |                       | df.columns            |
+-----------------------+-----------------------+-----------------------+
| 8.  Replacing values  |                       | \# Argument passed    |
|                       |                       | can also be a         |
|                       |                       | dictionary with       |
|                       |                       | separate values       |
|                       |                       |                       |
|                       |                       | df =                  |
|                       |                       | df.replace({oldValue1 |
|                       |                       | :                     |
|                       |                       | newValue1, oldValue2: |
|                       |                       | newValue2},           |
|                       |                       | inplace=True)         |
+-----------------------+-----------------------+-----------------------+
| 9.  Categories to     |                       |                       |
|     numbers           |                       |                       |
+-----------------------+-----------------------+-----------------------+
| 10. Dealing with      |                       | df.describe()         |
|     Outliers          |                       |                       |
|                       |                       | df.col1.min(),        |
|                       |                       | df.col2.max()         |
|                       |                       |                       |
|                       |                       | \# Visualize top 10   |
|                       |                       |                       |
|                       |                       | top\_10 =             |
+-----------------------+-----------------------+-----------------------+
|                       | To get a feel for the | \%matplotlib inline   |
|                       | type of data we are   |                       |
|                       | dealing with, we plot | df.hist(bins=50,      |
|                       | a histogram for each  | figsize=(20,15))      |
|                       | numeric variable.     |                       |
|                       |                       | plt.savefig(\"attribu |
|                       |                       | te\_histogram\_plots\ |
|                       |                       | ")                    |
|                       |                       |                       |
|                       |                       | plt.show()            |
+-----------------------+-----------------------+-----------------------+
|                       | 2.6. Reset index of   | \# Reset index of     |
|                       | dataframe, if         | DataFrame to row      |
|                       | necessary             | numbers, moving index |
|                       |                       | to columns            |
|                       |                       |                       |
|                       |                       | df.reset\_index()     |
+-----------------------+-----------------------+-----------------------+

Filter

+-----------------------------------+-----------------------------------+
| 3.  String comparaison            | df.query(\"column\_name==\'search |
|                                   | \_value\'\")                      |
|                                   |                                   |
|                                   | \# Using with variable            |
|                                   |                                   |
|                                   | var = 45                          |
|                                   |                                   |
|                                   | df.query(\'column\_name ==        |
|                                   | \@var\')                          |
|                                   |                                   |
|                                   | \# With AND/OR                    |
|                                   |                                   |
|                                   | df.query(\"(col1==\'value1\') or  |
|                                   | (col2==\'val2\')\")               |
+===================================+===================================+
| 1.  String comparaison            | 1\. To find all the values from   |
|                                   | the series that **starts** with   |
|                                   | a pattern \"s\":                  |
|                                   |                                   |
|                                   | SQL - WHERE column\_name LIKE     |
|                                   | \'s%\'                            |
|                                   |                                   |
|                                   | Python -                          |
|                                   | column\_name.str.startswith(\'s\' |
|                                   | )                                 |
|                                   |                                   |
|                                   | 2\. To find all the values from   |
|                                   | the series that **ends** with a   |
|                                   | pattern \"s\":                    |
|                                   |                                   |
|                                   | SQL - WHERE column\_name LIKE     |
|                                   | \'%s\'                            |
|                                   |                                   |
|                                   | Python -                          |
|                                   | column\_name.str.endswith(\'s\')  |
|                                   |                                   |
|                                   | 3\. To find all the values from   |
|                                   | the series that **contains**      |
|                                   | pattern \"s\":                    |
|                                   |                                   |
|                                   | SQL - WHERE column\_name LIKE     |
|                                   | \'%s%\'                           |
|                                   |                                   |
|                                   | Python -                          |
|                                   | column\_name.str.contains(\'s\')  |
|                                   |                                   |
|                                   | Return :                          |
|                                   |                                   |
|                                   | NaN if value is missing           |
|                                   |                                   |
|                                   | True if there is a match          |
|                                   |                                   |
|                                   | False if there is not             |
+-----------------------------------+-----------------------------------+
| 2.                                |                                   |
+-----------------------------------+-----------------------------------+

References:

<http://www.theanalysisfactor.com/outliers-to-drop-or-not-to-drop/>

<https://www.datacamp.com/community/tutorials/data-preparation-with-pandas>

<https://datascienceplus.com/linear-regression-in-python-predict-the-bay-areas-home-prices/>

<https://medium.com/@arpitpathak114/data-preprocessing-with-numpy-and-pandas-5598ef69491e>

<https://www.kdnuggets.com/2017/06/7-steps-mastering-data-preparation-python.html/2>
