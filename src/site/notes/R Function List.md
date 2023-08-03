---
{"title":"R Function List","alias":null,"type":"note","created":"2022-09-10T18:13:18","modified":"2022-12-12T14:25:06","dg-publish":true,"sup":["[[R\\|R]]"],"state":"[[%watch]]","related":["[[R Function\\|R Function]]"],"permalink":"/r-function-list/","dgPassFrontmatter":true,"updated":"2022-12-12T14:25:06"}
---


# R Function List

## Statistics

- `sum`
- `min`, `max`
- `length`
- `mean`
- `median`
- `var`
- `sd` standard deviation
- `cor`
- `lm` linear model
- `summary`
- `coef`

```r
x = c(4,6,12,9,21,14)
mean(x)
var(x)
median(x)

y = c(10,13,22,15,30,15)
cor(x,y)
```

## Generation

- `vector`
    - <span class="alt-check alt-check-ex">`vector("numeric", length = 10)` generates a vector having 10 zeros</span>
- `seq([from =] a, [to =] b, [by =] stepsize)`

```r
seq(1,10,3)
```

### Matrix

- `matrix(data,nrow,ncol)`
- `rbind(first_row, second_row, ...)`
- `cbind(first_column, second_column, ...)`
- `solve` *can* give the inverse of the matrix
- `dim`
    - A matrix can be created directly from a vector by adding a dimension attribute

```r
# Turn a vector into a matrix by adding a dimension attribute
m <- 1:10
dim(m) <- c(2,5)
m
```

## Manipulation

- `sort`
- `head(vec,n)`
- `tail(vec,n)`

```r
x <- c(6, 8, 7, 5, 3, 0, 9)
head(x,2)
tail(x,3)
```

### For Matrices

- `t` transpose
- `det`

## Logic

- <span class="alt-check alt-check-tip">The argument of the below functions is **conditional expressions**</span>
- `which`
- `any`

```R
x <- c(6, 8, 7, 5, 3, 0, 9)
which(x %% 2 == 0) # return indexes
any(x == 10)
```

## Plot

- `plot`
    - [Quick-R: Graphical Parameters](https://www.statmethods.net/advgraphs/parameters.html)
- `stem`
- `hist`
- `barplot`
