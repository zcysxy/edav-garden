---
{"title":"R Statement","alias":null,"type":"note","created":"2022-09-08T19:07:28","modified":"2022-09-08T19:07:33","dg-publish":true,"sup":[["R","r"]],"state":"done","permalink":"/r-control-statement/","dgPassFrontmatter":true,"updated":"2022-09-08T19:07:33"}
---


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
