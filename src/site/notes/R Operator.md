---
{"dg-publish":true,"permalink":"/r-operator/"}
---

> [!meta]-
sup:: [[R\|R]]  
state:: done  

# Operator

## Arithmetic

```r
10L + 66L # integer
2.0 * 2L # numeric
1 / 2
c(1,2,3)^2

# Remainder
3 %% 2 # 1 (numeric)
3L %% 2L # 1 (integer)

# Integer Division
5 %/% 2
5 == 2 * (5 %/% 2) + (5 %% 2) # TRUE

# Inner product
c(1,2,3) * c(3,2,1)s
```

Note that 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

$<div class="markdown-embed-title">

# inline n-link

</div>



> [!meta]-
sup:: [[R\|R]]  
state:: done

# R Basics

- Comments start with `#`
    - No specific syntax for multi-line comments
- Index starts from ***1***
- The naming convention of files and variables is **snake_case**
- Print variables using `print`
- Assign a value to a variable using
    - `x <- 1` (preferred traditionally)
    - `1 -> x`
    - `x = 1`
- Variables in [[R\|R]] are dynamic typing like [[Python\|Python]]
- The default arithmetics in [[R\|R]] are **element-wise**, unlike [[MATLAB\|MATLAB]] ^1e9b8c
- The interactive shell of [[R\|R]] uses an indicator `[x]` to show the index of the printed vector
    - example:
  
  ```R
    > x <- 11:30
    > x
     [1] 11 12 13 14 15 16 17 18 19 20 21 22
    [13] 23 24 25 26 27 28 29 30
    ```
- Use function `View()` to view data in a specific RStudio viewer


</div></div>
. There are special operators for matrix arithmetics.

```r
A %*% B
```

## Comparison

```r
1 > 2
2 <= 3
TRUE == TRUE
FALSE != FALSE

# Element-wise comparison
c(1,2,3) == c(1,2,4) # TRUE  TRUE FALSE
c(1,2,3) == 1 # TRUE FALSE FALSE

# Identify if an element belongs to a vector.
1 %in% c(1,2,3)
```

- [~] Use `near(x,y)` to compare two floating point numbers.

## Logic

```r
TRUE | FALSE # or
TRUE || FALSE # or
TRUE & FALSE # and
TRUE && FALSE # and
!TRUE # not

# Element-wise logic operations
c(TRUE, FALSE, FALSE) | c(FALSE, TRUE, FALSE) # TRUE TRUE FALSE
```

## Assignment

```r
x <- 1
y = 1
z <<- 1
1 -> u
1 ->> w
cat(x, y, z, u, w)
```

- [~] It's a convention to use `<-` rather than `=` for assignment, and leave `=` only for function arguments. The reasons are compatibility and precedence (`<-` is slightly higher, and `=` is used for function arguments before the assignment)

The special assignment operators `<<-` and `->>` are **looking up** operators, and can maintain states. They can assign value to the variables in the parent scopes. See the example

```r
new_counter <- function() {
  i <- 0
  function() {
    i <<- i + 1 # see if you change <<- to <-
    i
  }
}

counter_one <- new_counter() # outer function, with i = 0
counter_two <- new_counter()

counter_one() # call ther inner function, i is changed to 1
counter_one() # i is changed to 2, the state is maintained
counter_two()
```

## Other

```r
# Colon for sequence generating
all(1:4 == seq(1,4,1))
```

- [[R Operator - Pipe\|R Operator - Pipe]]
