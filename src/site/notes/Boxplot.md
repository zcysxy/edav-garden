---
{"dg-publish":true,"permalink":"/boxplot/","title":"Boxplot","created":"2022-09-13T16:24:30","updated":"2022-12-10T19:37:21"}
---

> [!meta]-
sup:: [[EDAV\|EDAV]]  
state:: done  

# Boxplot

Boxplots display individual outliers and robust statistics for the data, useful for identifying outliers and for **comparisons of distributions** across subgroups.

- Boxplots follow the 5-data summary
    - min, first quartile/ lower hinge, median, third quartile/ upper hinge, max
        - Sometimes quartiles are different than hinges 
{ #f281ji}

            - **Hinge**
                - The lower hinge is the median of the lower half of the data up to the median, and including the median if and only if the median is a real data point
                    - i.e., the median is not the average of two points; i.e., the size of the data is odd
                - The upper hinge is the median of the upper half of the data up to the median, and including the median if and only if the median is a real data point
            - **Quartile**
                - Quartiles are special **percentiles**
                - For $k$th percentile:
                    1. Rank the data
                    2. Find $k$% of the sample size
                    3. If this is an integer, **add 0.5**; if it isn't an integer round **up**
                    4. Find the datum in this position; If your depth ends in 0.5, then take the midpoint between the two data points
            - <span class="alt-check alt-check-impt">Therefore, the hinges are the same as the quartiles *unless* the remainder when dividing the sample size by 4 is 3</span>
- Area != number of data points; each area contains the same number of points
{ #blnqta}

    - Area represents the **density**
- Outliers: data outside the **fences**
    - fences: upper-hinge + 1.5 x **H-spread**, lower-hinge - 1.5 x H-spread
    - H-spread/ interquartile/ forth spread: upper-hinge - lower-hinge
- A multiple-class boxplot should be **re-ordered by the median**
{ #dw30i4}


## Elements

- Box width
    - A disadvantage of boxplots is that they don't convey information on how big the different groups are
    - Set `varwidth = TRUE` in [[ggplot2\|ggplot2]], the width of boxes will be proportional to $\sqrt{n}$
- Extreme outliers
    - We can define **outer fences** to be over 3 times the box length away from the box; then outliers outside outer fences are extreme outliers
