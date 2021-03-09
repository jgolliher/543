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

Depending on the goal 

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

This is text.
*This is italicized text*
**This is bolded text**
`This is text that looks like code`

```{Python
This is a code chunk
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


