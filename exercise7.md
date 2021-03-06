## Exercise 7: Library and packages

Create the script "exercise7.R" and save it to the "Rcourse/Module2" directory: you will save all the commands of exercise 7 in that script.
<br>Remember you can comment the code using #.


<details>
<summary>
correction
</summary>

```{r}
getwd()
setwd("Rcourse/Module2")
setwd("~/Rcourse/Module2")
```

</details>

**1- Install and load the packages ggplot2 and WriteXLS**

<details>
<summary>
correction
</summary>

```{r}
# Install the 2 packages at once
install.packages(pkgs=c("ggplot2", "WriteXLS"))
# Load in the environment (one by one)
library("ggplot2")
library("WriteXLS")
```

Check with sessionInfo() that the packages were loaded.

</details>

**2- ggplot2 loads automatically the diamonds dataset in the working environment: you can use it as an object after ggplot2 is loaded.**

What are the dimensions of diamonds? What are the column names of diamond?

<details>
<summary>
correction
</summary>

```{r}
# Dimensions of diamonds
dim(diamonds)
# Column names of diamonds
colnames(diamonds)
```

</details>

You can read the help page of the diamonds dataset to understand what it contains!<br>

Note: diamonds is a data frame: you can test it with is.data.frame(diamonds) (returns TRUE).

**3- Select the columns carat, cut, color and price of diamonds and store in the object diams1.**

<details>
<summary>
correction
</summary>

```{r}
# Select columns
diams1 <- diamonds[,c("carat", "cut", "color", "price")]
```

</details>

**4- Install and load the package dplyr from the Console.**

<details>
<summary>
correction
</summary>

```{r}
# Install package
install.packages(pkgs="dplyr")
# Load package
library("dplyr")
```

</details>

**5- Use the function "sample_n" from the dplyr package to randomly sample 200 lines of diams1: save in diams object.**

<details>
<summary>
correction
</summary>

```{r}
# Subset data frame
diams <- sample_n(tbl=diams1, size=200)
```

</details>

**-6.Save diams into 2 files:**

* diamonds200.txt with write.table
* diamonds200.xls with WriteXLS 
  
Note: read about and play with the different options of both functions and check the output files.

<details>
<summary>
correction
</summary>

```{r}
# Write a text file with write.table
write.table(x=diams, 
	file="diamonds200.txt",
        row.names=FALSE,
        quote=FALSE,
        sep="\t")
# Write an Excel file with WriteXLS
WriteXLS(x=diams, 
	ExcelFileName="diamonds200.xls", 
	row.names=FALSE, 
	col.names=TRUE, 
	FreezeRow=1, 
	BoldHeaderRow=TRUE)

```

</details>


> Go to [Regular expressions](https://sbcrg.github.io/CRG_RIntroduction/regex).

> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)
