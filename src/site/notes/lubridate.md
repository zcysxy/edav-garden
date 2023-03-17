---
{"dg-publish":true,"permalink":"/lubridate/"}
---

> [!meta]-  
sup:: [[R Package\|R Package]]  
state:: done  

# lubridate

> Lubridate provides tools that make it easier to parse and manipulate dates. These tools are grouped below by common purpose. More information about each function can be found in its help documentation.

Lubridate comes with useful functions to

- Convert data to [[R Type - Date\|Date class]]
    - `ymd()`, `ydm()`, `mdy()`, `myd()`, `dmy()` transform string with the right order to Date class
        - [@] `mdy("April 13, 1907")` returns `"1907-04-13"`
- Extract information from data of [[R Type - Date\|Date class]]
    - `year()`
    - `month()`
        - `month(date, label = TRUE)` returns a [[R Type#Factors\|factor]] with levels being twelve months
    - `yday()` returns the day of the year of a date
        - [@] `yday(Sys.Date())` returns `298`
    - `week()` returns the week of the year of a date
