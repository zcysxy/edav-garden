---
{}
---


# rvest

- `robotstxt::paths_allowed(url)` checks if a page is reachable
- `read_html(url)` gets the content of the [[HTML\|HTML]] page, returns a [[XML\|XML]] object
- `html_table()` get the tables out of a fetched HTML page, returns a [[R Data Structure#List\|R Data Structure#List]] of tibbles (dataframes)
    - <span class="alt-check alt-check-ex">Process a table: `mytable %>% filter(X1 == "Version:") %>% pull(X2)`</span>
- `html_elements()` get specific elements, returns a list
    - `html_elements(x, "h2")`
    - `html_elements(x, "#current_visitors")`
    - `html_elements(x, ".data")`
- `html_element()` works like `html_elements()`, except that it returns a single node
- `html_text()` get the text out of nodes

- <span class="alt-check alt-check-rmk">rvest doesn't work with dynamically loaded content</span>
    - Download the loaded page as a local file
    - Use another package `RSelenium`
