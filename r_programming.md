# R Programming
****
#Lesson 1
```r
getwd()
```
[1] "C:/Users/rvalenciano/Documents"
```r
setwd("~/RProgramming")
read.csv("mydata.csv")
```
id  | name | age |  status 
----|---|----|----
1 |  John Jones | 23 |  single
2 | Hannah Jones | 35 |  married
3 | Carl Junior | 67 | divorced
4 | Robert Curl | 78 |  married

Now we create a new R file, called week1.R in our workdir.
```r
myfunction <- function() {
  x <- rnorm(100)
  mean(x)
}

second <- function() {

}

```
We load it into console using
```r
source("week1.R")
```

And call it with:

```r
a = myfunction()
second(4:10)
```
# Lesson 2
## Vectorized Operations

You can do operations with parallelism, and instead of writing loops, we can apply them at the same time.
For instance, sum, each element of the vector is added with the other in the same index:

```r
x <- 1:4; y <- 6:9
x + y
```
7  9 11 13

Logical Vectors: Compare all the number and retrieves which number is greater than 2.

```r
x > 2
```

Matrices
matrix(data, rows, cols, ...)
```r
x <- matrix(1:4, 2, 2); y <- matrix(rep(10, 4),2, 2)
```
So x now have its value:


    | [,1] | [,2]
--- | ---- | ----
[1,]|    1 | 3
[2,]|    2 | 4


Element Wise Operation
```r
x * y
```

    | [,1]  | [,2]
--- | ----  | ----
[1,]|    10 | 30
[2,]|    20 | 40


# Lesson 3
## R nuts and bolts
### Data Types

* character
* numeric (real numbers)
* integer
* complex
* logical 

The most basic object is a vector. Vector can contain objects of the same class, except a List. Empty vectors can be created with the function vector()

All numbers are treated as numeric (double precision numbers). If you want an integer, add L to the number, i.e 1L.
1 / 0 = Inf
0 / 0 = NaaN

Also you can use c() function to create vectors

```r
 x <- c(0.5, 0.6)
```
[1] 0.5 0.6

```r
 x <- vector('numeric', length = 10)
```
[1] 0 0 0 0 0 0 0 0 0 0
## Coertion

```r
y <- c(1,7, 'a')   #  "1" "7" "a"
z <- c(TRUE, 2)    #  1 2
w <- c("a", TRUE)  #  "a"    "TRUE"

x <- 0.6
class(x)      # "integer"
as.numeric(x) #  0 1 2 3 4 5 6
as.logical(x) # FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
```

## Lists
```r
 x <- list(1, "a", TRUE, 1 + 4i)
 ```
 
 ## Matrices, binding
 ```r
 x <- 1:3
 y<- 10:12
 cbind(x,y)
  ```
    | [,1]  | [,2]
--- | ----  | ----
[1,]|    1 | 10
[2,]|    2 | 11
[3,]|    3 | 12


```r
  rbind(x,y)
```
  
    | [,1]  | [,2] | [,3] 
--- | ----  | ---- | ----   
[1,]| 1 | 2 | 3
[2,]| 10 | 11 | 12

 ## Factors
 
 Used to represent categorical data. Like hashes
 ```r
 is.na(x)
 is.nan(x)
 ```
 
 ## Data Frames
 
 Store tabular data.
 
 * Special type of list where each element has the same length
 * Each element of the frame can be thought as a column and the length is the number of rows
 * Unlike matrices, they can store different type of data.
 * read.csv() creates a data frame.
 *
 ```r
 x <- data.frame(foo = 1:4, bar = c(T, T, F, F))
  ```
  
      | foo  | bar
--- | ----  | ----
1|    1 | TRUE
2|    2 | TRUE
3|    3 | FALSE
4|    4 | FALSE

Access the 47th row

 ```r
 x[r,] # where r is the row 
  ```

Missing numbers of a data frame in column 1
 ```r
s <- sum(is.na(a[1]))
  ```
## names
You can append names to elements like list o matrix. 
```r
x<- list(a=1, b=1, c=1)
```
## Reading tabular data
```r
data <- read.table("foo.txt") # useful for small or medium data sets with ' ' as separator
readLines # read lines of text file
source(...) # read R code files
unserialize() # reading single R objects in binary form
```

## Reading LARGE Tables

Tell read.table the type of the column.
Tell R the number of rows (nrows).

Its useful to know

* How much memory is available?
* What other applications are in use?
* Are there other users logged into the System?
* OS is 32 bit or 64 bit?
*

Calculating size in memory:

Data Frame with 1,500,000 rows and 120 columns.
= 1440000000 bytes
= 1440000000 / 2 to 20 bytes/MB
= 1,373.29MB
= 1.34 GB

## Dumping to files
```r
x <- 'foo'
y <- data.frame(a = 1, b = 'a')
dump(c('x', 'y'),file = 'data.R')
rm(x,y) # remove objects
source('data.R') # objects x and y are back again

```

## Subsets
```r
subset(a, Ozone > 31 & Temp > 90)
colMeans(subset(a, Month == 5)) 
```
