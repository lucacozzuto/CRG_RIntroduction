## Exercise 8: Regular expressions

Create the script "exercise8.R" and save it to the "Rcourse/Module2" directory: you will save all the commands of exercise 8 in that script.
<br>Remember you can comment the code using #.


<details>
<summary>
correction
</summary>

```{r}
getwd()
setwd("~/Rcourse/Module2")
```

</details>


**1- Play with grep**

* Create the following data frame

```{r}
df2 <- data.frame(age=c(32, 45, 12, 67, 40, 27), 
	citizenship=c("England", "India", "Spain", "Brasil", "Tunisia", "Poland"), 
	row.names=paste(rep(c("Patient", "Doctor"), c(4, 2)), 1:6, sep=""),
	stringsAsFactors=FALSE)

```

Using grep: create a smaller data frame df3 that contains only the Patient but NOT the Doctor information.

<details>
<summary>
correction
</summary>

```{r}
# Select row names
rownames(df2)
# Select only rownames that correspond to patients
grep("Patient", rownames(df2))
# Create data frame that contains only those rows
df3 <- df2[grep("Patient", rownames(df2)), ]
```

</details>

**2- Play with gsub**

Build this vector of file names:

```{r}
vector1 <- c("L2_sample1_GTAGCG.fastq.gz", "L1_sample2_ATTGCC.fastq.gz", 
	"L1_sample3_TGTTAC.fastq.gz", "L4_sample4_ATGGTA.fastq.gz")
```

Use gsub and an appropriate regular expression to remove all but "sample1", "sample2", "sample3" and "sample4" from vector1.

<details>
<summary>
correction
</summary>

```{r}
# | is used as OR
gsub(pattern="L[124]{1}_|_[ATGC]{6}.fastq.gz", 
	replacement="", 
	x=vector1)
```

</details>

> Go to [For loops](https://sbcrg.github.io/CRG_RIntroduction/forloop).

> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)
