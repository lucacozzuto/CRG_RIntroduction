## Exercise 3a. Character vector manipulation

Create the script "exercise3.R" and save it to the "Rcourse/Module1" directory: you will save all the commands of exercise 3 in that script.
<br>Remember you can comment the code using #.

**1- Go to Rcourse/Module1
First check where you currently are with getwd();
then go to Rcourse/Module1 with setwd()**

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

**2- Create vector w as:**

```{r}
w <- rep(x=c("miRNA", "mRNA"), times=c(3, 2))
```

**3- View vector w in the console: how does function rep() work ?** 
<br>Play with the **times** argument.

<details>
<summary>
correction
</summary>

```{r}
rep(x=c("miRNA", "mRNA"), times=c(3, 4))
rep(x=c("miRNA", "mRNA"), times=c(10, 2))
```

</details>

**4- What is the output of table(w) ? What does the table function do ?**

**5- Type w[grep(pattern="mRNA", x=w)] and w[w == "mRNA"]**
<br> Is there a difference between the two outputs?

<details>
<summary>
correction
</summary>

```{r}
w[grep(pattern="mRNA", w)]
w[w == "mRNA"]
# no difference between the outputs
```

</details>

**6- Now type w[grep(pattern="RNA", w)] and w[w == "RNA"]**
<br> Is there a difference between the two outputs?

<details>
<summary>
correction
</summary>

```{r}
w[grep(pattern="RNA", w)]
w[w == "RNA"]
# grep outputs 5 values but == outputs none
```

</details>

What is the difference between **==** and **grep** ?


<details>
<summary>
correction
</summary>

>= looks for exact matches.
<br>
grep looks for **patterns**.

</details>


**7- Create vector g as:**

```{r}
g <- c("hsa-let-7a", "hsa-mir-1", "CLC", "DKK1", "LPA")
```

How many elements do w and g contain?

<details>
<summary>
correction
</summary>

```{r}
length(w); length(g)
```

</details>

**8- Do vectors w and g have the same length? Use the function identical() to check this.**

<details>
<summary>
correction
</summary>

```{r}
identical(x=length(w), y=length(g))
```

</details>

**9- Name the elements of g using the elements of w.**<br> 
(i.e. the names of each element of g will be the elements of w).

<details>
<summary>
correction
</summary>

```{r}
names(g) <- w
```

</details>

**If you have time**, continue with Exercise 3b below.<br>

## Exercise 3b.

**1- Use the sub() function to replace miRNA with microRNA in the *names* of g.**

<details>
<summary>
correction
</summary>

```{r}
names(g) <- sub(pattern="miRNA", replacement="microRNA", x=names(g))
```

</details>

**2- Count how many microRNAs and mRNAs there are in g based on the column names.**

<details>
<summary>
correction
</summary>

```{r}
table(names(g))
```

</details>

**3- Create vector tt as:**

```{r}
tt <- "Introduction to R course"
```

How many characters does tt contain? Use nchar().

<details>
<summary>
correction
</summary>

```{r}
nchar(tt)
```

</details>

**4- Remove "Introduction to R" from tt.**
<br>You can try with either substr() or gsub()

<details>
<summary>
correction
</summary>

```{r}
substr(x=tt, start=17, stop=nchar(tt))
gsub(pattern="Introduction to R", replacement="", x=tt)
```

</details>

> Go to [Factors](https://sbcrg.github.io/CRG_RIntroduction/factor)
<br>
> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)

