---
{}
---


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

# Element-wise product
c(1,2,3) * c(3,2,1)
```

Note that 
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/r-basics/#1e9b8c" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# inline n-link

</div>


- The default arithmetics in [[R\|R]] are **element-wise**, unlike [[MATLAB\|MATLAB]] 

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

- <span class="alt-check alt-check-tip">Use `near(x,y)` to compare two floating point numbers.</span>

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

- <span class="alt-check alt-check-tip">It's a convention to use `<-` rather than `=` for assignment, and leave `=` only for function arguments. The reasons are compatibility and precedence (`<-` is slightly higher, and `=` is used for function arguments before the assignment)</span>

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
