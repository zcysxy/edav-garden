---
{"dg-publish":true,"permalink":"/r-type-date/","title":"R Type - Date","created":"2022-11-03T16:19:58","updated":""}
---

> [!meta]-  
sup:: [[R Type\|R Type]]  
state:: done  

# Date

`"Date"` is a special data **class** for date values in [[R\|R]]. Strictly saying, `Date` is not an [[R Type\|R Type]], but a class. A class is an **attribute** assigned to an object regardless of its internal storage structure. To see this, execute the following code

```r
x <- as.Date("2022-11-03")
class(x)  # "Date"
typeof(x) # "double"
```

- [!] The only *correct* date format: `YYYY-MM-DD`

## Conversion to Date

- Use `as.Date(x)` to convert to Date class
    - You need to specify the format of `x` if it is not in `YYYY-MM-DD`
        - [@] `as.Date("1/12/2019", format="%m/%d/%Y")`
        - Pay attention to the format: wrong format may give the wrong date
            - [@] `as.Date("1/12/2019", format="%m/%d/%y")` gives `"2020-01-12"` because `%y` is for a two-digit year, and is replaced by `20` here
        - See [[R Type - Date#Conversion Specification\|#Conversion Specification]] for the conversion specification reference
- A similar function: `reader::parse_date`
    - `parse_date` will return `NA` for `parse_date("1/12/2019", format="%m/%d/%y")`
- Use package [[lubridate\|lubridate]]

### Conversion Specification

|Conversion specification| Description                                        | Example            |
| ------------------------ | -------------------------------------------------- | ------------------ |
| %A                       | Full weekday                                       | Sunday, Thursday   |
| %b or %h                 | Abbreviated month                                  | May, Jul           |
| %B                       | Full month                                         | May, July          |
| %d                       | Day of the month (01-31)                           | 27, 07             |
| %j                       | Day of the year (001-366)                          | 148, 188           |
| %m                       | Month (01-12)                                      | 05, 07             |
| %U                       |Week (01-53) with Sunday as the first day of the week| 22, 27             |
| %w                       | Weekday (0-6) with Sunday as 0                     | 0, 4               |
| %W                       |Week (00-53) with Monday as the first day of the week| 21, 27             |
| %x                       | Date, locale-specific                              |                    |
| %y                       | Year without century (00-99)                       | 84, 05             |
| %Y                       | Year with century                                  | 1984, 2005         |
| %C                       | Century                                            | 19, 20             |
| %D                       | Date formatted %m/%d/%y                            | 05/27/84, 07/07/05 |
| %u                       | Weekday (1-7) Monday is 1                          | 7, 4               |
| %n                       | Newline on output or arbitrary whitespace on input |                    |
|%t| Tab on output or arbitrary whitespace on input     |                    |

- [~] See `?strptime` for the reference inside [[R\|R]].

## Date Operation

Date class supports the following operations

```R
# Subtraction
as.Date("2022-11-01") - as.Date("2020-11-01")
# Time difference of 730 days 

# Addition
as.Date("2022-11-01") + 7
# "2022-11-08"

# Comparison
as.Date("2022-11-01") < as.Date("2020-11-01")
# False
```

### scale_x_date

Since dates can be calculated and compared, it is easy to specify the limits and breaks in [[ggplot2\|ggplot2]].

- `base + sacle_x_date(limits = c(ymd("2022-01-01"), ymd("2022-11-03")))`
- `base + sacle_x_date(limits = c(Sys.Date() - 19, NA))`
- `base + sacle_x_date(breaks = "1 week"))`
- `base + scale_x_date(date_labels = "%b %d")`

## Other Functions

- `Sys.date()` returns today's date
- `weekdays()`, `months()`, and `quarters()` return the weekday, month, and quarter of the date respectively
