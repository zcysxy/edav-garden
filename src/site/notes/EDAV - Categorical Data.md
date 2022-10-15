---
{"dg-publish":true,"permalink":"/edav-categorical-data/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true}
---

> [!meta]-  
sup:: [[EDAV|EDAV]]  
state:: [[%wip|%wip]]  

# Categorical Data

## Ordinal vs Nominal

[Nominal vs Ordinal Scale: What is the Difference? | QuestionPro](https://www.questionpro.com/blog/nominal-vs-ordinal-scale/)
[Nominal, Ordinal, Interval, Ratio Scales with Examples | QuestionPro](https://www.questionpro.com/blog/nominal-ordinal-interval-ratio/)

## Data Formats

- cases
    - w/o counts
- counts (`Freq`)
- contingency/pivot table
    - [@] Ex:
        
        ```txt
              Favorite
        Age     bubble gum  coffee
          old   2           4 
          young 7           1
        ```
        

Conversions:

| From \\ To | cases | counts                                                             | table     |
| ---------- | ----- | ------------------------------------------------------------------ | --------- |
| cases      | -     | `as.data.frame(table())` or `group_by() %>% summarise(Freq = n())` | `table()` |
| counts     | [1]   | -                                                                  | `xtabs()` |
| table      | [1]   | `as.data.frame()`                                                  | -         |

[1]: http://www.cookbook-r.com/Manipulating_data/Converting_between_data_frames_and_contingency_tables/#counts-to-contingency-table

## Likert Data

Likert data is a special categorical data that uses a **psychometric scale** commonly involved in questionnaires. For example

- strongly agree
- agree
- don’t know
- disagree
- strongly disagree

Relative frequency stacked [[Bar Chart|Bar Chart]]s are used to present this kind of data.

[Redirect Notice](https://www.google.com/url?sa=i&url=https%3A%2F%2Ffortune.com%2F2017%2F10%2F18%2Fgender-equality-in-america%2F&psig=AOvVaw2F8I5KhWntZbau7231FeEl&ust=1665802291429000&source=images&cd=vfe&ved=0CAwQjRxqFwoTCJiJ2qDb3voCFQAAAAAdAAAAABAO)![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013225221.png)

Colors play an important role in presenting this kind of data: we use a neutral color to present a neutral category, and use two different sets of colors for categories on two sides.

Another type of [[Bar Chart|Bar Chart]], **diverging stacked bar chart**s, sometimes are more suitable. They align bars with the neutral category always in the center. By doing this, the inclination stands out.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013225854.png)

Furthermore, we can separate and even remove the neutral category.
