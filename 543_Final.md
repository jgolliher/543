# <center>Data Management Final Project</center>
### <center>Kyle Cunningham, John Golliher, Kizer Harris, and Kenny Miller</center>
### <center>March 7, 2021</center>

## Assignment

Write a tutorial on the Python programming language intended for competent SAS programmers. That is, *how do you go from knowing SAS to knowing Python?*

Focus on the following areas:
	
* Data Import
* Data Manipulation

Bonus points for going into **Data Analysis as well.**

***

Highlight similarities between SAS and Python as well as differences between the languages. Think about:

* Syntax
* Libraries/Functions
* Variables
* Flow Control (Looping and Branching)

***

Provide references to where the reader can get more in-depth information.

This should be *no more* than 5 pages. Use of pictures, tables, code snippets, examples, etc. are encouraged.

***

Submissions may be made by groups or individuals. Group submissions will result in the same grade assigned to all group members. Every member of the group should independently submit his/her own copy of the group submission. Please identify the members of the group at the very beginning of the source code.

***

## Importing Data 

Importing data into SAS requires users to follow a few conventions. Notably, creating a *library* as well as specififying the output table, file type, and *guessingrows*. 

Let's use the csv file `SECswim.csv` as an example. In SAS, you would run the following:

**SAS CODE:**

```{SAS}
LIBNAME jg base "~/sasuser.v94"; 

PROC IMPORT FILE = "~/sasuser.v94/SECSwim.csv" out=jg.swim dbms=csv replace;
	guessingrows=max;
```
SAS *requires* users to specify the library with the `LIBNAME` statement, which provide a place to save steps and a place to work with data. Importing data into python, however, involves the following code.

**Python Code**

```{Python}
import pandas as pd

SECSWIM = pd.read_csv("SECSwim.csv")
```
**Note:** The line `import pandas as pd` imports the Python library *Pandas*, which is the de facto data frame and data manipulation library for Python.

A convenient piece of Python is its use of more specified functions for reading in data. For example `pd.read_csv` will read in *comma separated values* documents **without** the need to specify inside the function what kind of data it is importing. Python is more specialized here– the `PROC IMPORT FILE` command in SAS requires users to specify the format in which the file stores data because it is a general purpose command. The Python command `pd.read_csv` is built specifically to read *csv* files, which decreases the amount of time spent writing out arguments.

That is not to say, however, that the Python command lacks the ability to specify arguments. Quite the contrary, really. 

***

## Data Manipulation

This is text.
*This is italicized text*
**This is bolded text**
`This is text that looks like code`

```{Python
This is a code chunk
```

***

## Data Analysis

Once data has been imported and manipulated to user specifications in either *SAS* or *Python*, the next step is analysis. Nearly every type of analysis that can be done in *SAS* can be done in *Python* and vice-versa. 

Let's say, that for example, you wish to run *Ordinary Least Squares Regression* on the **SECswim** data to predict a swimmer's `PrelimTime` (the time he/she swam in the preliminary heats) from his/her `SeedTime` (the time he/she was entered into the meet with). 

For the purpose of this illustration we will use `LogSeedTime` and `LogPrelimTime` as the data must be transformed via *the natural log* to better explain the variation.

**SAS Code**

```{SAS}
PROC REG DATA=jg.swim;
	MODEL LogPrelimTime = LogSeedTime;
RUN;
```
<center>
Analysis of Variance

| Source         | DF   | SSE       | MSE       | F Value   | Pr > F    |
| ---------------| -----|-----------|-----------|-----------|-----------|
| Model          | 1    | 922.12459 | 922.12459 | 4001570   |<.0001     |
| Error          | 1763 | 0.040627  | 0.00023044|           |           |
| Corrected Total| 1764 | 922.53086 |           |           |           |


| Description    | Value   | 
| ---------------| --------|
| Root MSE       | 0.01518 | 
| Dependent Mean | 4.45193 | 
| Coeff Var      | 0.34098 | 
| R-Square       | 0.9996  | 
| Adj R-Square   | 0.9996  | 

Parameter Estimates

| Variable    | DF| Para Est.| Std. Err. | t Value | Pr > t|
| ------------|--- |----------|-----------|---------|---------|
| Intercept   | 1 | -0.00583 | 0.00226   | -2.58   | 0.0099  |
| LogSeedTime | 1 | 1.00005  | 0.00049993| 2000.39 | <.0001  |


</center>

One of the convienent things about *SAS* is that it gives you all of this output as soon as you run the *OLS* model. Furthermore, it gives you the *diagnostic plots*, *residuals plot*, and the *fit plot*. This is a difference over *Python*, which will require you to ask for each of these one-by-one. 

**Python Code**

```{Python}
mport pandas as pd 
import statsmodels.formula.api as sm 

SEC = pd.read_csv('SECswim.csv')


result = sm.ols(formula="LogPrelimTime ~ LogSeedTime",data=SEC).fit()
print(result.params)
print(result.summary())
```
This will give the same output as SAS as they follow the same process for obtaining *OLS*. The biggest difference being that *Python* requires users to import secondary libraries in order to accomplish *OLS* while *SAS* can do it natively. 

***

## Syntax

This is text.

*This is italicized text*

**This is bolded text**

`This is text that looks like code`

```{Python
This is a code chunk
```

***

## Libraries/Functions

*Python* is an extremely useful tool when it comes to the libraries that it provides. Libraries in Python do not hold files of data, but rather contain pre-combined code that drastically cut down the time needed to code.  These libraries, unlike *SAS*, have to be installed and then loaded into each python session before being utilized.  For example, you would download *pandas* in your terminal with a code such as `pip3 install pandas`.  Then you would load the library in Python with the command: `import pandas as pd`. The libraries in Python are extremely broad and allow for a multitude of data manipulation.  Some of the most popular libraries in Python are Numpy, Pandas, and Matplotlib.  These libraries are extremely beneficial opposed to what SAS has to offer as they allow for great data visualization. 

The functions within the libraries are used to perform certain tasks very similar to SAS.  SAS has generic functions already and so does Python.  However, Python can run certain functions within the different libraries.  For example if you wanted to create a data frame using the pandas command your function would be `pd.Dataframe()`.  Functions can also be created in python quite easily.  Then they will only be used when they are called.  For example, below a function called `foo` has been created that returns certain messages based upon the value of ‘x’. 


```{Python
def foo(x):
	if(x == 1 ):
		return('hello')
	elif(x == 2):
		return('world')
	elif(x == 3):
		return("!")
```

***

## Variables 

This is text.

*This is italicized text*

**This is bolded text**

`This is text that looks like code`

```{Python
This is a code chunk
```

***

## Flow Control


This is text.

*This is italicized text*

**This is bolded text**

`This is text that looks like code`

```{Python
This is a code chunk
```

***
