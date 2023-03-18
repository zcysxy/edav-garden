---
{"dg-publish":true,"permalink":"/r-function/","title":"R Function","created":"2022-09-08T19:18:55","updated":""}
---

> [!meta]-
sup:: [[R\|R]]  
state:: done

# R Function

To define a function

```r
jiggle <- function(x) {
    x = x + rnorm(1, sd=.1)
    return(x)
}
jiggle(5)
```

The return function is not necessary; it can be any statement that returns a result. For example

```r
f <- function(x) { x*x }
f(4)
```
