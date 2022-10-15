---
{"dg-publish":true,"permalink":"/dplyr/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true}
---

> [!meta]-
sup:: [[R Package|R Package]], [[EDAV|EDAV]]  
state:: done  
source: [5 Data transformation | R for Data Science](https://r4ds.had.co.nz/transform.html)

# dplyr

Data transformation is a pre-process of getting the data in the right form to present. Typically, in R, we use `dplyr` package to do this task.

Main functions in `dplyr` are called **verbs** and work similarly:

1. The first argument is a **data frame**
2. The subsequent arguments describe what to do with the data frame, using the variable names (without quotes)
3. The result is a **new data frame**

## filter()

`filter()` allows you to subset observations based on their values.
The first argument is the name of the data frame.
The second and subsequent arguments are the expressions that filter the data frame (returned data frame should satisfy these expressions).

```r
jan1 <- filter(flights, month == 1, day == 1)
```

- [!] Multiple arguments to `filter()` are combined with "and": every expression must be true in order for a row to be included in the output.
- [!] Don't use short-circuiting logical operators here. Because the expressions in `filter()` filter all the data items.
- [!] `filter()` filters out both `FALSE` and `NA`

## arrange()

`arrange()` takes a data frame and a set of column names (or more complicated expressions) to order rows. If you provide more than one column name, each additional column will be used to break ties in the values of the preceding columns.

```r
arrange(flights, year, desc(month), day)
```

- `desc()` is used to reverse the order
- Missing values `NA` are always sorted at the end

## select()

`select()` is used to select columns (variables). Some ways to fill the arguments

- `A,B,C`
- `alias = A` renames the column
- `A:B` selects all columns between `A` and `B` (inclusive)
- `-(A:B)` selects all columns except those from `A` to `B`
- `starts_with("abc")` matches names that begin with `abc`
- `ends_with("xyz")` matches names that end with `xyz`
- `contains("ijk")` matches names that contain `ijk`
- `matches("(.)\\1")` selects variables that match a [[Regular Expression|Regular Expression]]
- `num_range("x", 1:3)` matches `x1`, `x2` and `x3`
- `everything()` matches all columns, only useful when you want to **move some columns to the start**

## mutate()

`mutate()` adds new columns at the end of the data frame.

```r
mutate(flights_sml,
  gain = dep_delay - arr_delay,
  speed = distance / air_time * 60,
  gain_per_hour = gain / hours # refers to a column just created
)
```

`mutate()` keeps the old columns. To only keep the new variables, use `transmute()`.

## summarise()

`summarise()` or `summarize()` collapses a data frame to a single row, with values calculated by functions that take the whole data as the argument, like `mean` and `sum`.

`summarise()` is more useful paired with function `group_by()`. `group_by()` returns a **grouped data frame** (you can think it adds a new column `group`). When applied to a grouped data frame, `summarise()` will summarize each group.

> [!rmk] Ungroup
>
> Grouped data frame has a `groups` attribute, while `summarise()` will remove it.
> If the data frame is grouped by multiple variables, `summarise()` will remove one group variable.
>
> You can also use `ungroup()` to manually remove the groups.

Useful summary functions:

- `mean()`, `median()`, `sum()`
    - use option `na.rm = TRUE` to remove the NAs before aggregation
- `n()`, `n_distinct(var)` for count
    - `n()` includes NAs, use `sum(!is.na(x))` to count non-NAs
- `min()`, `max()`, `quantile(x, 0.25)`
