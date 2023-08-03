---
{"title":"lubridate","alias":null,"type":"note","created":"2022-11-03T22:36:27","modified":"2022-11-03T22:48:34","dg-publish":true,"sup":{},"state":"done","permalink":"/lubridate/","dgPassFrontmatter":true,"updated":"2022-11-03T22:48:34"}
---


# lubridate

> Lubridate provides tools that make it easier to parse and manipulate dates. These tools are grouped below by common purpose. More information about each function can be found in its help documentation.

Lubridate comes with useful functions to

- Convert data to [[R Type - Date\|Date class]]
    - `ymd()`, `ydm()`, `mdy()`, `myd()`, `dmy()` transform string with the right order to Date class
        - <span class="alt-check alt-check-ex">`mdy("April 13, 1907")` returns `"1907-04-13"`</span>
- Extract information from data of [[R Type - Date\|Date class]]
    - `year()`
    - `month()`
        - `month(date, label = TRUE)` returns a [[R Type#Factors\|factor]] with levels being twelve months
    - `yday()` returns the day of the year of a date
        - <span class="alt-check alt-check-ex">`yday(Sys.Date())` returns `298`</span>
    - `week()` returns the week of the year of a date
