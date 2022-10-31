---
{"dg-publish":true,"permalink":"/r-data-structure/"}
---

> [!meta]-
sup:: [[R\|R]]  
state:: done

# R Data Structure

[[R Type\|R Type]]s are types for the smallest objects in [[R\|R]]. Furthermore, these objects can form more complex **data structures**.

## Vector

In [[R\|R]], every single value, like `5L`, is considered a vector of length 1.
There is one rule about vectors: **a vector can only contain objects of the same type**.
Use function `c` (for "combine") to create a vector with more than 1 element.
If you combine objects of different types into a vector, the objects will be transformed into the same type.

```r
length(5L)
x <- c(2L,5)
length(x) # 2
class(x) # numeric
class(x[1]) # numeric
```

For integers and numerics, a shortcut for generating a vector is the `:` operator.

```r
c(1,2,3,4) == 1:4
```

### Indexing

Use square brackets `[]` and index (***starting from 1***) to fetch the elements from a vector. Use a colon `:` to specify a range.

```r
c(6,8)[1]
x <- c(6, 8, 7, 5, 3, 0, 9)
x[1:3]
x[c(1,4,5,8)]
```
### Type Coercion

In vectors, implicit type coercions will be done. You can also do explicit type coercions.

```r
as.character(c(6, 8))   # "6" "8"
as.logical(c(1,0,1,1))  # TRUE FALSE  TRUE  TRUE
# as.numeric("Bilbo")
# Warning message:
# NAs introduced by coercion    
```

## Matrix

Matrix is a special two-dimensional data structure in [[R\|R]]. The class of it is `"matrix" "array"`.
Like a vector, the elements in a matrix should/will be of the same [[R Type\|R Type]].
To create a matrix, using the following function

```r
M <- matrix([data =] data, [nrow =] 3, [ncol =] 2)
```

> [!rmk]
> - When the first arg is missing, e.g. `matrix(,2,2)`, the matrix is empty (with elements being `NA`)
> - The length of the first arg can be a **sub-multiple** or a **multiple** of the number of rows
> - When the second or the third arg is missing, their default is 1

### Indexing

Since a matrix is two-dimensional, the index has two arguments, like `M[1,2]`. When the argument is missing, it is interpreted as a colon `:` in [[Matlab Array - Indexing\|Matlab Array - Indexing]].

```r
M <- matrix(1:4,2,2)
M[,]
M[1,]
M[,2] <- 5
M[]
```

## Data Frame

Data frames are used to store **tabular data** (2d) in [[R\|R]]. They are represented as a special type of [list](#list) where every element of the list has to have the same length.

Data frames are usually created by reading in a dataset using the `read.table()` or `read.csv()`. However, data frames can also be created explicitly with the `data.frame()`function or they can be coerced from other types of objects like lists.

```r
students <- data.frame(c("Cedric", "Fred", "George", "Cho", "Draco", "Ginny"),
                       c(       3,      2,        2,     1,       0,      -1),
                       c(     "H",    "G",      "G",   "R",     "S",     "G"))
names(students) <- c("name", "year", "house") # name the columns
class(students) # "data.frame"
students
# =>
#     name year house
# 1 Cedric    3     H
# 2   Fred    2     G
# 3 George    2     G
# 4    Cho    1     R
# 5  Draco    0     S
# 6  Ginny   -1     G
class(students$year)    # "numeric"
class(students[,3])     # "factor"
# find the dimensions
nrow(students)  # 6
ncol(students)  # 3
dim(students)   # 6 3

# There are many twisty ways to subset data frames, all subtly unalike
students$year       # 3  2  2  1  0 -1
students[, 2]       # 3  2  2  1  0 -1
students[, "year"]  # 3  2  2  1  0 -1

# To drop a column from a data.frame or data.table,
# assign it the NULL value
students$houseFounderName <- NULL
```

## Array

An array in R is a **multi-dimensional** homogenous (of the same [[R Type\|R Type]]) data structure, like [[Matlab Array\|Matlab Array]].

```r
array(c(c(c(2, 300, 4), c(8, 9, 0)), c(c(5, 60, 0), c(66, 7, 847))), dim = c(3, 2, 2))
```

## List

A list is a multi-dimensional **heterogeneous** data structure.

```r
x <- list(1, "a", TRUE, 1 + 4i)
```

Lists are like [[Python Types - Dictionary\|dictionaries]]: you can give each value a name:

```r
x <- list(time = 1:40)
x$price = c(rnorm(40, .5 * x$time, 4))
```

```r
# You can get items in the list like so
list1$time # by name
list1[["time"]] # by name
list1[[1]] # by index
```

> [!info]
> Lists are not the most efficient data structure to work with in R; unless you have a very good reason, you should stick to [`data.frames`](<#data frame>).
> Lists are often returned by functions that perform linear regressions
