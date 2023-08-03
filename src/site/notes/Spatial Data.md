---
{"dg-publish":true,"permalink":"/spatial-data/","title":"Spatial Data","created":"2022-11-10T16:21:11","updated":"2022-11-10T20:13:28"}
---


# Spatial Data

Spatial data is any type of data that directly or indirectly references a specific geographical area or location. Sometimes called geospatial data or geographic information.

Best case for mapping spatial data: when **geography** matters. Do not overuse it.

## Graphs

- [[Choropleth\|Choropleth]]
- [[Geographic Coordinate\|Geographic Coordinate]]

## sf and tmap

[[R Package\|R Package]] `sf` is for reading shape files (`.shp`). To see the read map, use function `st_geometry()` and plot the returned object.

[[R Package\|R Package]] `tamp` is for plotting maps (generated by `sf`) together with other data. The general workflow is

1. Get the spatial data by reading the shape file using `sf`
2. Combine spatial data and other data
    - e.g. use `left_join()`
3. plot the combined data using `tmap`