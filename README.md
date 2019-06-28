# Data Cleaning with Python and Pandas

In this project, I discuss useful techniques to clean a messy dataset with Python and Pandas. I discuss `principles of tidy data` and `signs of an untidy data`. I discuss EDA and present ways to deal with `outliers` and `missing and negative numerical values`. I discuss how to check for missing values with `ASSERT` statement. I present how to reshape data using the Pandas `melt()` function.


===============================================================================


## Table of Contents:-

This project is divided into various sections which are listed below:-


1.	Introduction to Python data cleaning

2.	Tidy data format

3.	Signs of an untidy dataset

4.	Python data cleansing – prerequisites

5.	Import the required Python libraries

6.	The source dataset

7.	Exploratory data analysis (EDA)

8.	Visual exploratory data analysis (Visual EDA)

9.	Findings of EDA and Visual EDA

10.	Split the ‘age_sex’ column into two separate columns

11.	Reorder the column labels

12.	Dealing with negative numerical values

13.	Dealing with outliers

14.	Dealing with missing numerical values

15.	Check with ASSERT statement

16.	Reshaping the data into tidy data format

17.	Summary

18.	References


===============================================================================

## 1. Introduction to Python data cleaning


Whenever we have to work with a real world dataset, the first problem that we face is to clean it. The real world dataset never comes clean. It consists lot of discrepancies in the dataset. So, we have to clean the dataset for further processing. 


Cleaning data is the process of preparing the dataset for analysis. It is very important because the accuracy of machine learning or data mining models are affected because of poor quality of data. 


So, data scientists spend a large amount of their time cleaning the dataset and transform them into a format with which they can work with. In fact, data scientists spend 80% of their time cleaning the data.


A very common scenario is that the dataset contains missing values coded as `NaN`. Also, the missing values are coded in different ways. The dataset may contain negative or invalid values. It may contain outliers. It may be in the untidy format. All of these are examples of a messy dataset. 


In this project, I present several useful ways to handle these discrepancies in the dataset.


===============================================================================


## 2. Tidy data format


Data comes in a wide variety of shapes and formats. Hadley Wickham, the Chief Scientist at RStudio, write a paper about tidy data 
in 2014 that formalizes the shape of the data. So, it gives us a goal when formatting the data. 


He states in his paper that –


`Tidy data provides a standard way to organize data values within a dataset.`


There are three principles of tidy data. These are as follows:-


•	**Columns represent separate variables**


•	**Rows represent individual observations**


•	**Observational units form tables.**


Tidy data makes it easier to fix common data problems. So, we need to transform the untidy dataset into tidy data. 


Before we look into the details of cleaning the dataset, we have to understand what constitutes an untidy data. We need to diagnose 
our data and find common signs of a messy dataset.


===============================================================================


## 3. Signs of an untidy dataset


We have to take a closer look to find common signs of a messy dataset. These common signs are as follows:-


•	**Missing numerical data**


Missing numerical data needs to be identified and addressed. Either they need to be deleted or replaced with a suitable test statistic.


•	**Untidy data**


Untidy dataset can contain multiple problems. They prevent us from transforming the messy dataset into a clean dataset that is suitable for analysis.


•	**Unexpected data values**


Mismatched data types of a column and data values can cause potential problems. They need to be investigated and solved.


•	**Inconsistent column names**


Column names contain inconsistent capitalizations and bad characters. They need to be addressed properly.


•	**Outliers**


Outliers need to be detected. They pose potential problems needs to be investigated and removed.


•	**Duplicate rows and columns**


Duplicate rows and columns make data redundant. They can bias an analysis. Hence, they needs to be found and dropped.



===============================================================================


## 4. Python data cleaning - prerequisites


We need three Python libraries for the data cleaning process – NumPy, Pandas and Matplotlib.



•	**NumPy** – NumPy is the fundamental Python library for scientific computing. It adds support for large and multi-dimensional arrays and matrices. It also supports large collection of high-level mathematical functions to operate on these arrays.


•	**Pandas** - Pandas is a software library for Python programming language which provide tools for data manipulation and analysis tasks. It will enable us to manipulate numerical tables and time series using data structures and operations.


•	**Matplotlib** - Matplotlib is the core data visualization library of Python programming language. It provides an object-oriented API for embedding plots into applications.



===============================================================================


## 5. Import Python libraries


We have seen that we need three Python libraries – NumPy, Pandas and Matplotlib for the data cleansing process. We need to import these libraries before we actually start using them. We can import them with their usual shorthand notation as follows:-


`import numpy as np`

`import pandas as pd`

`import matplotlib.pyplot as plt`

`%matplotlib inline`


===============================================================================

## 6. The source dataset


For this project, I have created a fictitious dataset. The dataset consists of details of my facebook friends.


===============================================================================

## 7. Exploratory data analysis


Now, it is time to understand the data. We should diagnose the data for any discrepancies by doing exploratory data analysis. 
We should proceed as follows:-


•	**df.shape attribute**

We can check the dimensions of the data with **df.shape** attribute.


•	**df.head()** and **df.tail()** methods

We can view the top five and bottom five rows of the dataset with **df.head()** and **df.tail()** methods respectively.


•	**df.info()** method

We can get a concise summary of the dataset with **df.info()** method. This method prints information about a DataFrame including the index dtype and column dtypes, non-null values and memory usage.


•	**df.dtypes** attribute

We can check the data types of each column in the dataframe with **df.dtypes** attribute. The above command returns the data type of each column.


•	**df.describe()** method

We can view the summary statistics of numerical columns with **df.describe()** method. It enable us to detect outliers in the data 
which require further investigation.


•	**df.columns** attribute

We can get the column labels of the dataframe with **df.columns** attribute.



===============================================================================


## 8. Visual exploratory data analysis


Now, we should conduct data visualization to find discrepancies in the data. Data visualization is a great way to find errors in the data and detect outliers. They help us to detect patterns in the data.


We can use various types of plots for data visualization purpose. These plots are listed below:-


•	**Bar plot**

A bar plot is a plot that presents data with rectangular bars with lengths proportional to the values that they represent.


•	**Histograms**

We use histograms for plotting continuous data counts. A histogram is a representation of the distribution of data.

In this case, we use histograms for plotting distribution of data values of height (cm) and weight (kg) columns.


•	**Box plot**

We can visualize basic summary statistics with box plot. Box plot let us to detect outliers in the data. They help us to find minimum and maximum values. They present 25th, 50th, 75th percentiles. 50th percentile value is the median value.


•	**Scatter plot**

Scatter plot help us to explore relationship between two numeric variables. It help us to identify potentially bad data.
We should draw a scatter plot of height(cm) and weight(kg) column.


===============================================================================


## 9. Findings of EDA and Visual EDA


We can summarize the findings of EDA and visual EDA as follows:-


1.	The dataset has 10 rows and 10 columns.

2.	The age and sex columns are combined together. There should be two separate columns of age and sex.

3.	All the invalid values (the values coded as "xx") and missing values in height (cm), weight (kg), spend_A, spend_B and 
	spend_C columns are coded as "NaN". The use of the keyword errors='coerce' in pd.to_numeric() method enable us to convert 
	all the invalid values into NaN.
	
4.	The data types of columns height (cm), weight(kg) and spend_C columns are converted into float64.

5.	In the height (cm) column, there is a value of 0.0. It is not possible as height cannot be 0. So, we need to resolve it.

6.	In the weight (kg) column, there is a negative value of -60 and a very high value of 160. Both are invalid values. Hence, we 		need to solve the issue.

7.	The three columns spend_A, spend_B and spend_C denote spending at three supermarkets A,B and C. These columns must contain 		positive real numbers. The missing values in these columns denote nothing spend in that market. We need to handle these missing 	values properly.

8.	In the spend_B column, there is a negative value -100. The amount spent cannot be negative. So, we need to take care of that.



===============================================================================


## 10. Split the ‘age_sex’ column


We should split the 'age_sex' column into two separate columns. 

We can do this using the **df.str.split()** function as follows:-

`df[['age','sex']] = df.age_sex.str.split("_", expand = True)`


Now, there is no need for the age_sex column. So, we should drop that column.

We can drop 'age_sex' column using the **df.drop()** method as follows:-

`df.drop(['age_sex'], axis=1)`


===============================================================================


## 11. Reorder the column labels


We should reorder the columns for more pleasing visual appearance.

We can do it as follows:-


`df = df[['fname','lname','age','sex','section','height(cm)','weight(kg)','spend_A','spend_B','spend_C']]`


===============================================================================



## 12. Dealing with negative numerical values


We have seen that, in the weight(kg) column, there is a negative value of -60. It is invalid value because weight cannot be negative. There is a high probability that weight is 60 kg and it is mistyped as -60. So, I will replace the negative value of -60 with positive value of 60.


We can do it as follows:-


`df['weight(kg)'].replace(-60, 60, inplace=True)`


Similarly, in the spend_B column, there is a negative value -100. The amount spent cannot be negative. So, we need to replace this negative value of -100 with positive value of 100.


We can do it as follows:-


`df['spend_B'].replace(-100,100, inplace=True)`


===============================================================================



## 13. Dealing with outliers


In the height(cm) column, there is a value of 0.0. It is not possible as height cannot be 0. So, we need to resolve it.
I will replace the 0.0 value with the mean of the height(cm) column. It can be done as follows:-


`mean = df['height(cm)'].mean()`


`df['height(cm)'].replace(0.0, mean, inplace=True)`


In the weight(kg) column, there is a very high absurd value of 160. It is not possible to have so much weight. Hence, it is invalid value. There is a high chance that the weight is 60 kg and it is mistakenly typed as 160 kg. So, I will replace the 160 data value 
with 60.


It can be done as follows:-


`df['weight(kg)'].replace(160.0, 60.0, inplace=True)`


===============================================================================


## 14. Dealing with missing numerical values


The following commands help us to deal with missing numerical values.


1.	**df.isnull()**

	The above command checks whether each cell in a dataframe contains missing values or not. If the cell contains missing value, it 	 returns True otherwise it returns False. 
	

2.	**df.isnull.sum()**

	The above command returns the total number of missing values in each column in the dataset.


3.	**isna()** and **notna()** functions to detect **NA** values

	Pandas provides isna() and notna() functions to detect ‘NA’ values. These are also methods on Series and DataFrame objects.


- Examples of isna() and notna() commands

### detect ‘NA’ values in the dataframe	

`df.isna()`


### detect ‘NA’ values in a particular column in the dataframe

`pd.isna(df[‘col_name’])`


`df[‘col_name’].notna()`



### Encode missing numerical values


Missing values are encoded in different ways. They can appear as `NaN`, `NA`, `?`, zero `0`, ‘xx’, minus one `-1` or a blank space “ ”. We need to use various pandas methods to deal with missing values. But, pandas always recognize missing values as `NaN`.  So, it is essential that we should first convert all the `?`, zeros `0`, `xx`, minus ones `-1` or blank spaces “ ” to `NaN`. If the missing values isn’t identified as `NaN`, then we have to first convert or replace such non `NaN` entry with a `NaN`.


### Convert '?' to ‘NaN’

`df[df == '?'] = np.nan`



	
### Handle missing numerical values


There are several methods to handle missing values. Each method has its own advantages and disadvantages. The choice of the method is subjective and depends on the nature of data and the missing values. The summary of the options available for handling missing values is given below:-


•	Drop missing values with dropna() method


•	Fill missing values with a test statistic


I have discussed each method in below sections:-


### Drop missing values with dropna() method


This is the easiest method to handle missing values. In this method, we drop labels or columns from a data set which refer to missing values. 


We can drop labels or rows from a dataset containing missing values as follows:-

`df.dropna (axis = 0)`


We can drop columns from a dataset containing missing values as follows:-

`df.dropna (axis = 1)`


This is the Pandas dataframe dropna() method. An equivalent dropna() method is available for Series with same functionality.


To drop a specific column from the dataframe, we can use drop() method of Pandas dataframe.


We can drop specific col_name column from Pandas dataframe as follows:-

`df.drop(‘col_name’, axis = 1)`
 

**A note about axis parameter** 


Axis value may contain (0 or ‘index’) or (1 or ‘columns’). Its default value is 0.


We set axis = 0 or ‘index’ to drop rows which contain missing values.


We set axis = 1 or ‘columns’ to drop columns which contain missing values.


After dropping the missing values, we can again check for missing values and the dimensions of the dataframe.


We can again check the missing values in each column as follows:-


`df.isnull.sum()`  


We can again check the dimensions of the dataset as follows:-


`df.shape`


But, this method has one disadvantage. It involves the risk of losing useful information. Suppose there are lots of missing values in our dataset. If drop them, we may end up throwing away valuable information along with the missing data. It is a very grave mistake as it involves losing key information. So, it is only advised when there are only few missing values in our dataset.


So, it's better to develop an imputation strategy so that we can impute missing values with the mean or the median of the row or column containing the missing values.



### Fill missing values with a test statistic

In this method, we fill the missing values with a test statistic like mean, median or mode of the particular feature the missing value belongs to. One can also specify a forward-fill or back-fill to propagate the next values backward or previous value forward.


We can fill missing values with a test statistic like mean as follows:-


`mean = df['col_name'].mean()`


`df['col_name'].fillna(value = mean, inplace = True )`



### We can also use replace() in place of fillna()


`df[‘col_name’].replace(to_replace = NaN, value = mean, inplace = True)`


If we choose this method, then we should compute the mean value on the training set and use it to fill the missing values in the training set. Then we should save the mean value that we have computed.  Later, we will replace missing values in the test set with 
the mean value to evaluate the system.



===============================================================================


## 15. Check with ASSERT statement


Finally, we can check for missing values programmatically. If we drop or fill missing values, we expect no missing values. We can 
write an assert statement to verify this. So, we can use an assert statement to programmatically check that no missing or unexpected 
'0' value is present. This gives confidence that our code is running properly.


Assert statement will return nothing if the value being tested is true and will throw an AssertionError if the value is false.


Asserts

•	assert 1 == 1   (return Nothing if the value is True)


•	assert 1 == 2   (return AssertionError if the value is False)



### assert that there are no missing values in the dataframe


`assert pd.notnull(df).all().all()`


### assert that there are no missing values for a particular column in dataframe


`assert df.column_name.notnull().all()`


### assert all values are greater than 0


`assert (df >=0).all().all()`


### assert no entry in a column is equal to 0


`assert (df['column_name']!=0).all().all()`


===============================================================================


## 16. Reshaping the data into tidy data format

When we take a closer look at the dataframe, we can see that our dataframe is not in the tidy data format.


The columns spend_A, spend_B and spend_C contain values of amount spent rather than variables. We should reorganize our dataframe into tidy data format.


We can convert it into the tidy data format using the **pd.melt()** function as follows:-


`pd.melt(frame=df, id_vars=['fname','lname','age','sex','section','height(cm)','weight(kg)'],`

			`value_vars=['spend_A','spend_B','spend_C'], var_name='expenditure',`
			
			`value_name='amount')`


===============================================================================



## 17. Summary


In this project, I present useful techniques to clean a messy dataset with Python and Pandas.


I start with the data cleaning process and emphasize the importance of a clean dataset. Then, I discuss tidy data format and signs 
of a messy dataset.


Then, I diagnose the dataset with exploratory data analysis (EDA) and visual exploratory data analysis (Visual EDA). I summarize my findings of EDA and Visual EDA.


Then, I start the data cleaning process. First of all, I split the ‘age_sex’ column into two separate columns. Then, I reorder the column labels.


Then, I discuss several ways to deal with negative numerical values, outliers and missing numerical values. Then, I programmatically check with ASSERT statement that there are no missing or negative values in the dataset.


In the last step, I reshape the data into tidy data format using 'pd.melt()' function.



===============================================================================


## 18. References

The ideas and techniques in this project have been taken from the following books and websites:-


i.	Pandas documentation

ii.	Python Machine Learning by Sebastian Raschka

iii.	Hands-On Machine Learning with Scikit Learn and Tensorflow by Aurélien Géron

iv.	http://pandas.pydata.org/pandas-docs/stable/missing_data.html

v.	https://www.datacamp.com/courses/cleaning-data-in-python

vi.	https://realpython.com/python-data-cleaning-numpy-pandas/

vii.	https://data-flair.training/blogs/python-data-cleansing/


