---
{"dg-publish":true,"permalink":"/forcats/"}
---

> [!meta]-  
sup:: [[R Package\|R Package]]  
state:: done  

# forcats

Package `forcats` contain tools for working with [[EDAV - Categorical Data\|EDAV - Categorical Data]] ([[R Type#Factors\|R Type#Factors]])

## Recode Factor Levels

To recode the levels, do not use `levels(x) <- c("A", "B")`; use `fct_recode()` in [[forcats\|forcats]] instead.

```r
library(forcats)
x <- factor(c("G234", "G452", "G136"))  
y <- fct_recode(x, Physics = "G234", Math = "G452", Chemistry = "G136")  
y
```

## Reorder Factor Levels

- `fct_inorder()`: by the order in which they first appear
- `fct_infreq()`: by number of observations with each level (largest first)
    - useful for unbinned data
- `fct_inseq()`: by numeric value of level.
- `fct_relevel(x, level1, level2, after = 4)`: by hand
    - without `after`, you are putting levels to the beginning
    - with `after = Inf`, you are putting levels to the last
- `fct_rev()`: reverse the current order
- `fct_reorder(x,y)`: by sorting along another variable
    - works with `.desc = False`
- `fct_reorder2(x,y,z)`: by sorting along another 2 variables

- [!] All the above functions return **new factors**.

## Include NA

When a factor contains NAs, NAs will not form a level. And when plotting, NA always orders first (in the top-down graph, and last in the left-right graphs). We can use `fct_explicit_na(x, "NA")` to make NA a real level with the name `"NA"`. Then we can reorder the levels including `"NA"`

```r
df <- data.frame(temperature = factor(c("cold", "warm", "hot", NA)),
                 count = c(15, 5, 22, 12))

df %>%
  mutate(temperature = fct_explicit_na(temperature, "NA") %>% # try comment this and the following lines
      fct_relevel("NA", "hot", "warm", "cold")) %>%
  ggplot(aes(x = temperature, y = count)) +
  geom_col() +
  coord_flip()
```

## Lumping

- `fct_lump_*`: lump together factor levels into "other"
    - `fct_lump_min()`: lumps levels that appear fewer than `min`
          times
        - [@] `cc |> mutate(continent_new = fct_lump_min(continent, 30))` puts all continents with less than 30 countries (items) into the "Other" category (level)
    - `fct_lump_prop()`: lumps levels that appear in fewer `prop * n` times, where `n` is the size of the data
    - `fct_lump_n()`: lumps all levels except for the `n` most frequent (or least frequent if `n < 0`)
    - `fct_lump_lowfreq()`: lumps together the least frequent
      levels, ensuring that "other" is still the smallest level
