---
{"dg-publish":true,"permalink":"/r-control-statement/"}
---

> [!meta]-
sup:: [[R\|R]]  
state:: done

# Control Statement

## for

```r
for (i in 1:4) {
    print(i)
}
```

## while

```r
a <- 10
while (a > 4) {
    cat(a, "...", sep = " ")
    a <- a - 1
}
```

> [!warning]
> Keep in mind that for and while loops run slowly in [[R\|R]].
> Operations on entire vectors (i.e. a whole row, a whole column)
> or `apply()`-type functions are preferred

## if/else

```r
if (4 > 3) {
    print("4 is greater than 3")
} else if (4 == 3) {
    print("4 is equal to 3")
} else {
    print("4 is less than 3")
}
```
