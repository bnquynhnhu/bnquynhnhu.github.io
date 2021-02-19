### Importing Libraries

Let&#39;s start by importing several libraries we&#39;ll need for exploring our data and cleaning textual data

1. **Pandas:** We will need Pandas to navigate our dataframe and check for each column&#39;s data type, null values, and unique values.
2. **NumPy:** This package is essential for any data science project. It has a lot of mathematical functions that operate on multi-dimensional arrays and data frames.
3. **Matplotlib &amp; Seaborn:** They are plotting and graphing libraries that we will use to visualize data in an intuitive way.

# Importing necessary libraries

import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

pd.set\_option(&#39;display.max\_rows&#39;, 500)

pd.set\_option(&#39;display.max\_columns&#39;, 500)

%matplotlib inline

1. Loading the data

df = pd.read\_csv(&quot;filename1.csv&quot;)

| Steps |
 | Python |
| --- | --- | --- |
|
1. View dataset
 | To learn quickly your object. | # To see first 5 rows of datasetdf.head()
# Returns the dimensionality of the DataFramedf.shape
 |
|
1. Data structure
 | Using **df.dtypes** for analyzing for columns/data types | df.dtypes ![](RackMultipart20210219-4-u5ugxk_html_876311e16a51a0dd.png) |
|
1. Drop unnecessary columns
 | # There are several features that we don&#39;t need. # Let&#39;s drop them.df.drop([&#39;col1&#39;, &#39;col2&#39;], axis=1, inplace=True) |
|
1. Rename columns
 | df.rename(columns={&#39;oldName1&#39;: &#39;newName1&#39;, &#39;oldName2&#39;: &#39;newName2&#39;}, inplace=True) |
|
1. Change data type of a column
 | _# Convert the column &quot;col1&quot; to numeric_# df[&#39;col1&#39;] = df[&#39;col1&#39;].str.replace(&#39;,&#39;, &#39;&#39;)df[&#39;col1&#39;] = pd.to\_numeric(df[&#39;col1&#39;])
_# Convert the column &quot;col1&quot; to int32_df.astype({[&#39;col1&#39;, &#39;col2&#39;]: &#39;int32&#39;}).dtypes

 |
|
1. Dealing with datetime
 |
 | # Convert object type to datetime typepd.to\_datetime(df.column\_name)

# Combine date and time columnscombined = df.date\_column.str.cat(df.time\_column, sep=&#39; &#39;)df[&#39;combined\_column&#39;] = pd.to\_datetime(combined)
 |
|
1. Dealing with missing data
 | Using **df.isnull().sum()** to find missing values of each feature in the dataset
 | # Find missing values of each feature in the data set.df.isnull().sum() ![](RackMultipart20210219-4-u5ugxk_html_dba7174952a3a7c1.gif)
# Examine missing valuesdf[df[&#39;bathrooms&#39;].isnull()]
 |
|
 | Some common methods for dealing with missing values include:
- dropping instances
- dropping attributes
- imputing the attribute mean/median, mode for all missing values
- using regression to impute attribute missing values
**df.dropna()**Drop rows with any column having NA/null data**df.fillna(value)**Replace all NA/null data with value. | # Drop all rows having missing valuesdf.drop(df.index[[index1, index2]], inplace=True)
# Drop all **rows and columns** where **ALL** elements are missing values:df.dropna(how=&#39;all&#39;)
# Drop the **columns** that only contains missing values/ drop a specified columndf.dropna(axis=&#39;columns&#39;, how=&#39;all&#39;)df.drop(&#39;col1&#39;, axis=&#39;columns&#39;, inplace=True)
# Fill all missing values with replaced value (mean, 0, median, etc)df[&#39;col1&#39;] = df[&#39;col1&#39;].fillna(df[&#39;col1&#39;].median()) df = df.fillna(0)
# To check the result, display list of columnsdf.columns |
|
1. Replacing values
 |
 | # Argument passed can also be a dictionary with separate valuesdf = df.replace({oldValue1: newValue1, oldValue2: newValue2}, inplace=True) |
|
1. Categories to numbers
 |
 |
 |
|
1. Dealing with Outliers
 |
 | df.describe()
df.col1.min(), df.col2.max()
# Visualize top 10 top\_10 =

 |
|
 | To get a feel for the type of data we are dealing with, we plot a histogram for each numeric variable. | %matplotlib inlinedf.hist(bins=50, figsize=(20,15))plt.savefig(&quot;attribute\_histogram\_plots&quot;)plt.show()
 ![](RackMultipart20210219-4-u5ugxk_html_67bfb92734b38718.gif) |
|
 | 2.6. Reset index of dataframe, if necessary | # Reset index of DataFrame to row numbers, moving index to columnsdf.reset\_index()
 |

Filter

|
1. String comparaison
 | df.query(&quot;column\_name==&#39;search\_value&#39;&quot;)
# Using with variablevar = 45df.query(&#39;column\_name == @var&#39;)
# With AND/ORdf.query(&quot;(col1==&#39;value1&#39;) or (col2==&#39;val2&#39;)&quot;)
 |
| --- | --- |
|
1. String comparaison
 | 1. To find all the values from the series that **starts** with a pattern &quot;s&quot;:SQL - WHERE column\_name LIKE &#39;s%&#39;Python - column\_name.str.startswith(&#39;s&#39;)2. To find all the values from the series that **ends** with a pattern &quot;s&quot;:SQL - WHERE column\_name LIKE &#39;%s&#39;Python - column\_name.str.endswith(&#39;s&#39;)3. To find all the values from the series that **contains** pattern &quot;s&quot;:SQL - WHERE column\_name LIKE &#39;%s%&#39;Python - column\_name.str.contains(&#39;s&#39;)
Return :NaN if value is missingTrue if there is a matchFalse if there is not
 |
|
1.
 |
 |

References:

[http://www.theanalysisfactor.com/outliers-to-drop-or-not-to-drop/](http://www.theanalysisfactor.com/outliers-to-drop-or-not-to-drop/)

[https://www.datacamp.com/community/tutorials/data-preparation-with-pandas](https://www.datacamp.com/community/tutorials/data-preparation-with-pandas)

[https://datascienceplus.com/linear-regression-in-python-predict-the-bay-areas-home-prices/](https://datascienceplus.com/linear-regression-in-python-predict-the-bay-areas-home-prices/)

[https://medium.com/@arpitpathak114/data-preprocessing-with-numpy-and-pandas-5598ef69491e](https://medium.com/@arpitpathak114/data-preprocessing-with-numpy-and-pandas-5598ef69491e)

[https://www.kdnuggets.com/2017/06/7-steps-mastering-data-preparation-python.html/2](https://www.kdnuggets.com/2017/06/7-steps-mastering-data-preparation-python.html/2)
