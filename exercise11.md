## Exercise 11: Base plots

Create the script "exercise11.R" and save it to the "Rcourse/Module3" directory: you will save all the commands of exercise 11 in that script.
<br>Remember you can comment the code using #.


<details>
<summary>
correction
</summary>

```{r}	
getwd()
setwd("~/Rcourse/Module3")
```

</details>

### 11a- scatter plot

**1- Create the following data frame**

```{r}
genes <- data.frame(sample1=rnorm(300),
                    sample2=rnorm(300))
```

**2- Create a scatter plot showing sample1 (x-axis) vs sample2 (y-axis) of genes.**

<details>
<summary>
correction
</summary>

```{r}	
plot(genes$sample1, genes$sample2)
```

</details>

**3- Change the point type and color.**

<details>
<summary>
correction
</summary>

```{r}
plot(genes$sample1, 
     genes$sample2, 
     col="lightblue", 
     pch=3)
```

</details>

**4- Change x-axis and y-axis labels to "Sample 1" and "Sample 2", respectively.**

<details>
<summary>
correction
</summary>

```{r}
plot(genes$sample1, 
     genes$sample2, 
     col="lightblue", 
     pch=3,
     xlab="Sample 1", 
     ylab="Sample 2")
```

</details>

**5- Add a title to the plot.**

<details>
<summary>
correction
</summary>

```{r}
plot(genes$sample1, 
     genes$sample2, 
     col="lightblue", 
     pch=3,
     xlab="Sample 1", 
     ylab="Sample 2",
     main="scatter plot")
```

</details>

**6- Add a vertical red line that starts at the median expression value of sample 1. Do it in two steps:**<br>
a. calculate the median expression of genes in sample 1.<br>
b. plot a vertical line using abline().

<details>
<summary>
correction
</summary>

```{r}
# median expression of sample1
med1 <- median(genes$sample1)

# plot
plot(genes$sample1, 
     genes$sample2, 
     col="lightblue", 
     pch=3,
     xlab="Sample 1", 
     ylab="Sample 2",
     main="scatter plot")

# vertical line
abline(v=med1, col="red")
```

</details>

### 11b- bar plot + pie chart

**1- Create the following vector**

```{r}
genes_significance <- rep(c("enriched", "depleted", "none"), c(20, 32, 248))
```


**2- The vector describes whether a gene is up- (enriched) or down- (depleted) regulated, or not regulated (none).**<br>
Produce a barplot that displays this information: how many genes are enriched, depleted, or not regulated.

<details>
<summary>
correction
</summary>

```{r}
barplot(table(genes_significance))
```

</details>

**3- Color the bars of the boxplot, each in a different color (3 colors of your choice)**

<details>
<summary>
correction
</summary>

```{r}
barplot(table(genes_significance), 
  col=c("blue", "red", "grey"))
```

</details>

**4- Use the argument "names.arg" in barplot() to rename the bars:**
Change depleted to "Down", enriched to "Up", none to "Not significant"

<details>
<summary>
correction
</summary>

```{r}
barplot(table(genes_significance), 
  col=c("blue", "red", "grey"), 
  names.arg=c("Down", "Up", "Not significant"))
```

</details>

**5- The "las" argument allow to rotate the x-axis labels for a better visibility.**
Try value 2 for las: what happens? 

<details>
<summary>
correction
</summary>

```{r}
barplot(table(genes_significance), 
  col=c("blue", "red", "grey"), 
  names.arg=c("Down", "Up", "Not significant"), 
  las=2)
```

</details>

**6- Create a pie chart of the same information (Enriched, Depleted, None)**

<details>
<summary>
correction
</summary>

```{r}
pie(table(genes_significance))
```

</details>

Change the color of the slices, modify the labels, and add a title.

<details>
<summary>
correction
</summary>

```{r}
pie(table(genes_significance), 
    col=c("blue", "red", "grey"), 
    main="pie chart", 
    labels=c("Down", "Up", "Not significant"))
```

</details>

## 11c- histogram

**1- Use genes object from exercise 11a to create a histogram of the gene expression distribution of sample 1.**

<details>
<summary>
correction
</summary>

```{r}
hist(genes$sample1)
```

</details>

**2- Repeat the histogram but change argument breaks to 50.**<br>
What is the difference ?

<details>
<summary>
correction
</summary>

```{r}
hist(genes$sample1, 
  breaks=50)
```

</details>

**3- Color this histogram in light blue.**

<details>
<summary>
correction
</summary>

```{r}
hist(genes$sample1, 
  breaks=50, 
  col="lightblue")
```

</details>

**4- Zoom in the histogram: show only the distribution of expression values from 0 to 2 (x-axis) using the xlim argument.**

<details>
<summary>
correction
</summary>

```{r}
hist(genes$sample1, 
  breaks=50, 
  col="lightblue",
  xlim=c(0, 2))
```

</details>

**5- Save the histogram in a pdf file.**

<details>
<summary>
correction
</summary>

```{r}
pdf("myhistogram.pdf")

hist(genes$sample1, 
    breaks=50, 
    col="lightblue", 
    xlim=c(0, 2))

dev.off()
```

</details>

Go to [ggplot2](https://sbcrg.github.io/CRG_RIntroduction/ggplot2)

> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)
