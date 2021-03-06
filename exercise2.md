## Exercise 2a. Numeric vector manipulation

Create the script "exercise2.R" and save it to the "Rcourse/Module1" directory: you will save all the commands of exercise 2 in that script.
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


**2- Create a numeric vector y which contains the numbers from 2 to 11, both included.** 
<br>Show y in the terminal.

<details>
<summary>
correction
</summary>

```{r}
y <- c(2, 3, 4, 5, 6, 7, 8, 9, 10, 11)
# same as
y <- 2:11
# show in terminal:
y
```

</details>

**3- How many elements are in y? I.e what is the length of vector y ?**

<details>
<summary>
correction
</summary>

```{r}
length(y)
```

</details>

**4- Show the 2nd element of y.**

<details>
<summary>
correction
</summary>

```{r}
y[2]
```

</details>

**5- Show the 3rd and the 6th elements of y.**

<details>
<summary>
correction
</summary>

```{r}
y[c(3,6)]
```

</details>

**6- Remove the 4th element of y: reassign. What is now the length of y ?**

<details>
<summary>
correction
</summary>

```{r}
# remove 4th element and reassign
y <- y[-4]
# length of y
length(y)
```

</details>

**7- Show all elements of y that are less than 7.**

<details>
<summary>
correction
</summary>

```{r}
# which elements of y are less than 7:
y < 7
# show those elements 
y[ y < 7 ]
```

</details>

**8- Show all elements of y that are greater or equal to 4 and less than 9.**

<details>
<summary>
correction
</summary>

```{r}
y[ y >= 4 & y < 9 ]
```

</details>


**9- Create the vector x of 1000 random numbers from the normal distribution:**
<br>***First read the help page of the rnorm() function.***

<details>
<summary>
correction
</summary>

```{r}
# help page for the rnorm function
help(rnorm)
# produce a vector of 1000 random numbers from the normal distribution
x <- rnorm(1000)
```

</details>

**10. What are the mean, median, minimum and maximum values of x?**

<details>
<summary>
correction
</summary>

```{r}
mean(x); median(x); min(x); max(x)
```

</details>

**11- Run the summary() function on x. <br>What additional information do you obtain ?**

<details>
<summary>
correction
</summary>

```{r}
summary(x)
```

</details>

**12- Create vector y2 as:**<br>

```{r}
y2 <- c(1, 11, 5, 62,  18, 2, 8)
```

**13. What is the sum of all elements in y2 ?**

<details>
<summary>
correction 
</summary>

```{r}
sum(y2)
```

</details>

**14- Which elements of y2 are also present in y ? 
<br>Note: remember the %in% operator.**

<details>
<summary>
correction
</summary>

```{r}
y2[ y2 %in% y ]
```

</details>

**15- Multiply each element of y2 by 1.5: reassign.**

<details>
<summary>
correction
</summary>

```{r}
y2 <- y2 * 1.5
```

</details>


**16- Use the function any() to check if the number 3 is present.**

<details>
<summary>
correction
</summary>

```{r}
# "Given a set of logical vectors, is at least one of the values true?"
any( y2 == 3 )
```

</details>

<br>
**If you have time**, continue with Exercise 2b below.<br>
If not:<br>
Go to [Exercise 3](https://sbcrg.github.io/CRG_RIntroduction/exercise3): Character vector manipulation !
<br>

## Exercise 2b.

**1- Create the vector myvector as:**

```{r}
myvector <- c(1, 2, 3, 1, 2, 3, 1, 2, 3)
```

**Create the same vector using the rep() function (?rep)**

<details>
<summary>
correction
</summary>

```{r}
myvector <- rep(1:3, 3)
```

</details>


**2- Reassign the 5th, 6th and 7th position of myvector with the values 8, 12 and 32, respectively.**

<details>
<summary>
correction
</summary>

```{r}
# reassign one by one
myvector[5] <- 8
myvector[6] <- 12
myvector[7] <- 32
# or reassign all at once
myvector[5:7] <- c(8, 12, 32)
```

</details>

**3- Calculate the fraction/percentage of each element of myvector (relative to the sum of all elements of the vector).
<br>sum() can be useful.**


<details>
<summary>
correction
</summary>

```{r}
# sum of all elements of the vector
mytotal <- sum(myvector)
# divide each element by the sum
myvector / mytotal
# multiply by 100 to get a percentage
(myvector / mytotal) * 100
```

</details>

**4- Add vector c(2, 4, 6, 7) to myvector (combining both vectors): reassign!**

<details>
<summary>
correction
</summary>

```{r}
# create the new vector
newvector <- c(2, 4, 6, 7)
# combine both myvector and newvector
c(myvector, newvector)
# reassign myvector
myvector <- c(myvector, newvector)
```

</details>

<br>

Go to [Exercise 3](https://sbcrg.github.io/CRG_RIntroduction/exercise3): Character vector manipulation !
<br>
> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)

