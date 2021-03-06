## Exercise 10: If statement

Create the script "exercise10.R" and save it to the "Rcourse/Module2" directory: you will save all the commands of exercise 10 in that script.
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


**1- Create vector vec2 as:**


```{r}
vec2 <- c("kiwi", "apple", "pear", "grape")
```

* Use an if statement and the %in% function to check whether "apple" is present in vec2 (in such case print "there is an apple!")

<details>
<summary>
correction
</summary>

```{r}
if("apple" %in% vec2){
	print("there is an apple there")
}
```

</details>

* Use an if statement and the %in% function to check whether "grapefruit" is present in vec2: if "grapefruit" is not found, test for a second condition (using **else if**) that checks if "pear" is found.

<details>
<summary>
correction
</summary>

```{r}
if("grapefruit" %in% vec2){
        print("there is a grapefruit there")
}else if("pear" %in% vec2){
	print("there is no grapefruit but there is a pear")
}
```

</details>

* Add an **else** section in case neither grapefruit nor pear is found in vec2.<br>
Test your **if** statement also on vec3:

```{r}
vec3 <- c("cherry", "strawberry", "blueberry", "peach")
```

<details>
<summary>
correction
</summary>

```{r}
if("grapefruit" %in% vec2){
        print("there is a grapefruit there")
}else if("pear" %in% vec2){
        print("there is no grapefruit but there is a pear")
}else{
	print("no grapefruit and no pear")
}
```

</details>

**2- If statement in for loop**

Create the following matrix:

```{r}
mat4 <- matrix(c(2, 34, 1, NA, 89, 7, 12, NA, 0, 38),
	nrow=5)
```

Loop over rows with **for** of mat4 and print row number and entire row **if** you find an NA.


<details>
<summary>
correction
</summary>

```{r}
for(k in 1:nrow(mat4)){
	# extract row
	rowk <- mat4[k,]
	if(any(is.na(rowk))){
		print(k)
		print(rowk)
	}
}
```

</details>

**3- For loop, if statement and regular expression**

Create vector vec4 as:

```{r}
vec4 <- c("Oct4", "DEPP", "RSU1", "Hk2", "ZNF37A", "C1QL1", "Shh", "Cdkn2a")
```

Loop over each element of "vec4":
* If the element is a **human gene (all upper-case characters)**, print a vector of two elements: the name of the gene and "human gene".<br>
* If the element is a **mouse gene (only the first character is in upper-case)**, print a vector of two elements: the name of the gene and "mouse gene".<br>

> Tip 1: *Use grep and a regular expression in the if statement !*<br>
> Tip 2: *When grep does not find a match, it returns an element of **length 0** !*<br>
> Tip 3: *You can also use grepl: check the help page*
<br>

<details>
<summary>
correction
</summary>

```{r}
for(gene in vec4){
	if(length(grep(pattern="^[A-Z0-9]+$", x=gene)) != 0){
		print(c(gene, "human gene"))
	}else if(length(grep(pattern="^[A-Z]{1}[a-z0-9]+$", x=gene)) != 0){
		print(c(gene, "mouse gene"))
	}
}

# With grepl
for(gene in vec4){
        if(grepl(pattern="^[A-Z0-9]+$", x=gene)){
                print(c(gene, "human gene"))
        }else if(grepl(pattern="^[A-Z]{1}[a-z0-9]+$", x=gene)){
                print(c(gene, "mouse gene"))
        }
}
```

</details>



> [back to home page](https://sbcrg.github.io/CRG_RIntroduction)
