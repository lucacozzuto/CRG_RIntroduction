<h2>Repetitive execution</h2>

**Loops** are used to repeat a specific block of code.

<h3>"for" loop</h3>

Structure of the **for loop**:

```{r}
for(i in vector_expression){
    action_command
}
```

3 main elements:
* **i** is the loop variable: it is updated at each iteration.
* **vector_expression**: value attributed to **i** at each iteration (the number of iterations is the **length of vector_expression**).
* **action_command**: what is to be done at each iteration.

Note the usage of **curly brakets {}** to start and end the loop!
<br><br>
<img src="images/forloop1.png" width="300"/><img src="images/forloop2.png" width="450"/>


* Example:

```{r}
for(i in 2:5){
	y <- i*2
	print(y)
}

```

* Example of a **for loop** that iterates over a character vector:

```{r}
# Character vector
myfruits <- c("apple", "pear", "grape")
# For loop that prints the current element and its number of characters
for(j in myfruits){
	print(j)
	print(nchar(j))
}
```

* Example of a **for loop** that iterates over each row of a matrix, and prints the minimum value of that row :

```{r}
# Matrix
mymat <- matrix(rnorm(800), 
	nrow=50)
# For loop over mymat rows
for(i in 1:nrow(mymat)){
	print(i)
	print(min(mymat[i,]))
}
```

Go to [Exercise 9](https://sbcrg.github.io/CRG_RIntroduction/exercise9): For loops.
<br>

> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)
