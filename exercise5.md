## Exercise 5. Data frame manipulation

Create the script "exercise5.R" and save it to the "Rcourse/Module1" directory: you will save all the commands of exercise 5 in that script.
<br>Remember you can comment the code using #.


<details>
<summary>
correction
</summary>

```{r}
getwd()
setwd("Rcourse/Module1")
setwd("~/Rcourse/Module1")
```

</details>

**1- Create the following data frame:**

|43|181|M|
|34|172|F|
|22|189|M|
|27|167|F|

<br>
With Row names: John, Jessica, Steve, Rachel.
<br>
And Column names: Age, Height, Sex.

<details>
<summary>
correction
</summary>

```{r}
df <- data.frame(Age=c(43, 34, 22, 27), 
                 Height=c(181, 172, 189, 167),
                 Sex=c("M", "F", "M", "F"),
                 row.names = c("John", "Jessica", "Steve", "Rachel"),
                 stringsAsFactors=FALSE)
```

</details>

**2- Check the structure of df with str().**

<details>
<summary>
correction
</summary>

```{r}
str(df)
```

</details>

**3- Calculate the average age and height in df**

Try different approaches:
* Calculate the average for each column separately.

<details>
<summary>
correction
</summary>

```{r}
mean(df$Age)
mean(df$Height)
```

</details>

* Calculate the average of both columns simultaneously using the apply() function.

<details>
<summary>
correction
</summary>

```{r}
# we have to remove the Sex column: we can calculate the average only with numbers
apply(df[,-3], 2, mean)
apply(df[,1:2], 2, mean)
apply(df[,-grep("Sex", colnames(df))], 2, mean)
```

</details>

**4- Add one row to df2: Georges who is 53 years old and 168 tall.**

<details>
<summary>
correction
</summary>

```{r}
# Georges= allows us to enter the row name at the same time as we add a row
df <- rbind(df, Georges=c(53, 168, "M"))
```

</details>

**5- Change the row names of df so the data becomes anonymous:** 
Use Patient1, Patient2, etc. instead of actual names.

<details>
<summary>
correction
</summary>

```{r} 
rownames(df) <- c("Patient1", "Patient2", "Patient3", "Patient4", "Patient5")
# try also the paste function!
rownames(df) <- paste("Patient", 1:5, sep="")
```

</details>

**6- Create the data frame df2 that is a subset of df which will contain only the female entries.**
 
<details>
<summary>
correction
</summary>

```{r}
# which elements are female ("F" in the "Sex" colum)
df$Sex=="F"
# retrieve rows that contain the female entries, and save in df2
df2 <- df[df$Sex=="F",]
```

</details>

**7- Create the data frame df3 that is a subset of df which will contain only entries of males taller than 170.**
 
<details>
<summary>
correction
</summary>

```{r}
# which entries are males
df$Sex=="M"
# which entries are greater than 170 in column "Height"
df$Sex=="M" & df$Height > 170
# retrieve rows that contain the males that are taller than 170, and save in df3
df3 <- df[df$Sex=="M" & df$Height > 170,]
```

</details>

## Exercise 5b

**1. Create two data frames mydf1 and mydf2 as:**

mydf1:

|1|14|
|2|12|
|3|15|
|4|10|

mydf2:

|1|paul|
|2|helen|
|3|emily|
|4|john|
|5|mark|

With column names: **"id", "age"** for mydf1, and **"id", "name"** for mydf2.

<details>
<summary>
correction
</summary>

```{r}
mydf1 <- data.frame(id=1:4, age=c(14,12,15,10))
mydf2 <- data.frame(id=1:5, name=c("paul", "helen", "emily", "john", "mark"))
```

</details>

**2- Merge mydf1 and mydf2 by their "id" column.**
Look for the help page of **merge** and/or Google it!

<details>
<summary>
correction
</summary>

```{r}
# input 2 data frames
# "by" columns indicate by which column you want to merge the data
merge(x=mydf1, y=mydf2, by.x="id", by.y="id")
mydf3 <- merge(x=mydf1, y=mydf2, by="id")
```

</details>

**3- Order mydf3 by decreasing age.**
Look for the help page of **order**.

<details>
<summary>
correction
</summary>

```{r}
# order the age column (default is increasing order)
order(mydf3$age)
# order the age column by decreasing order
order(mydf3$age, decreasing = TRUE)
# order the whole data frame by the column age in decreasing order
mydf3[order(mydf3$age, decreasing = TRUE), ]
```

</details>

## Exercise 5c

**1- Using the download.file function, download [this file](https://public-docs.crg.es/biocore/sbonnin/Rcourse/genes_dataframe.RData) to your current directory.** (Right click on "this file" -> Copy link location to get the full path).

<details>
<summary>
correction
</summary>

```{r}
# failing: download.file("https://github.com/sbcrg/CRG_RIntroduction/blob/master/genes_dataframe.RData", "genes_dataframe.RData")
download.file("https://public-docs.crg.es/biocore/sbonnin/Rcourse/genes_dataframe.RData", "genes_dataframe.RData")
```

</details>

**2- The function dir() lists the files and directories present in the current directory: check if genes_dataframe.RData was copied.**

<details>
<summary>
correction
</summary>

```{r}
dir()
```

</details>

**3- Load genes_dataframe.RData in your environment**
Use the *load* function.

<details>
<summary>
correction
</summary>

```{r}
load("genes_dataframe.RData")
```

</details>

**4- genes_dataframe.RData contains the df_genes object: is it now present in your environment?**

<details>
<summary>
correction
</summary>

```{r}
ls()
```

</details>

**5- Explore df_genes and see what it contains**
You can use a variety of functions: str, head, tail, dim, colnames, rownames, class... 
 
<details>
<summary>
correction
</summary>

```{r}
str(df_genes)
head(df_genes)
tail(df_genes)
dim(df_genes)
colnames(df_genes)
rownames(df_genes)
class(df_genes)
```

</details>

**6- Select rows for which pvalue_KOvsWT < 0.05 AND log2FoldChange_KOvsWT > 0.5. Store in the up object.**

<details>
<summary>
correction
</summary>

```{r}
# rows where pvalue_KOvsWT < 0.05 
df_genes$pvalue_KOvsWT < 0.05
# rows where log2FoldChange_KOvsWT > 0.5
df_genes$log2FoldChange_KOvsWT > 0.5
# rows that comply both of the above conditions
df_genes$pvalue_KOvsWT < 0.05 & df_genes$log2FoldChange_KOvsWT > 0.5
# select rows for which pvalue_KOvsWT < 0.05 AND log2FoldChange_KOvsWT > 0.5
up <- df_genes[df_genes$pvalue_KOvsWT < 0.05 & 
                 df_genes$log2FoldChange_KOvsWT > 0.5,]
```

</details>

How many rows (genes) were selected?


**7- Select from the up object the Zinc finger protein coding genes (i.e. the gene symbol starts with Zfp). Use the grep() function.**

<details>
<summary>
correction       
</summary>

```{r}
# extract gene symbol column
up$gene_symbol
# use grep to get the genes matching the pattern "Zfp"
up[grep("Zf", up$gene_symbol), ]
```

</details>

**8- Select rows for which pvalue_KOvsWT < 0.05 AND log2FoldChange_KOvsWT is > 0.5 OR < -0.5.**
For the selection of log2FoldChange: give the **abs** function a try! 
<br>Store in the diff_genes object.

<details>
<summary>
correction
</summary>

```{r}
# rows where pvalue_KOvsWT < 0.05
df_genes$pvalue_KOvsWT < 0.05
# rows where log2FoldChange_KOvsWT > 0.5
df_genes$log2FoldChange_KOvsWT > 0.5
# rows where log2FoldChange_KOvsWT < -0.5
df_genes$log2FoldChange_KOvsWT > -0.5
# rows where log2FoldChange_KOvsWT < -0.5 OR log2FoldChange_KOvsWT > 0.5
df_genes$log2FoldChange_KOvsWT > 0.5 | df_genes$log2FoldChange_KOvsWT > -0.5
# same as above but using the abs function
abs(df_genes$log2FoldChange_KOvsWT) > 0.5
# combine all required criteria
df_genes$pvalue_KOvsWT < 0.05 & abs(df_genes$log2FoldChange_KOvsWT) > 0.5
# extract corresponding entries
diff_genes <- df_genes[df_genes$pvalue_KOvsWT < 0.05 & 
                 abs(df_genes$log2FoldChange_KOvsWT) > 0.5,]
```

</details>

How many rows (genes) were selected?

> Go to [Missing values](https://sbcrg.github.io/CRG_RIntroduction/na).

<br>
> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)

