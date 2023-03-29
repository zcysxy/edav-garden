---
{"dg-publish":true,"permalink":"/matlab/","created":"2022-02-22T20:20:09","updated":"2023-03-28T20:31:28"}
---

> [!meta]-
> sup:: [[Language\|Language]]  
> state:: [[%wip\|%wip]]  
> doc: [MATLAB Documentation](https://www.mathworks.com/help/matlab/index.html)  

# MATLAB

**ALL IN ALL**: [[Matlab Everything\|Matlab Everything]]

## [[Matlab Basics\|Matlab Basics]]

* [[Matlab Desktop\|Matlab Desktop]]

## [[Matlab Array\|Matlab Array]]

## [[Matlab Types\|Matlab Types]]

## [[Matlab Function\|Matlab Function]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




> [!meta]-
sup:: [[MATLAB\|MATLAB]]
state:: [[%wip\|%wip]]


# Matlab Functions List

> [!rmk] 说明
> 
> * ~~以下只列出我笔记中提及的函数~~
> * 无单独笔记的函数
>     * 只有一种 syntax 且无需多余说明
>     * 用法重复
>     * 使用情形少
>         * 这种函数只保留最基本 syntax
> * 符号说明
>     * `...` 为可变长度参数省略
>     * `__` 为同之前语法
>     * `<>` 为有默认值的可选参数
>     * `<[]>` 为方括号 `[]` 可省, 即这里的参数可以是可变长度参数, 也可以是一个数组
> 

## Basics

* [[Matlab Functions - save, load\|save, load]]
* [[Matlab Functions - exist\|exist]]
* [[Matlab Functions - iskeyword\|iskeyword]]
* [[Matlab Functions - clear\|clear]]
* [ ] [[Matlab Functions - isequal\|isequal]]

## Array Related

* [[Matlab Functions - linspace\|linspace]]
* [[Matlab Functions - logspace\|logspace]]
* isempty
* isscalar
* isvector
* issparse

## Graphics Related

* [[Matlab Functions - fplot\|fplot]]

## Mathematics

* [[Matlab Random Number Generation\|Matlab Random Number Generation]]

![20210126031035](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20210126031035.png)

![20210126032351](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20210126032351.png)

### Matrix Manipulation

* [[Matlab Function - spdiags\|Matlab Function - spdiags]]

## Identity Test

![20210126225733](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20210126225733.png)


</div></div>


## [[Matlab Operations\|Matlab Operations]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




> [!meta]-
sup:: [[MATLAB\|MATLAB]], [[Matlab Operations\|Matlab Operations]]
state:: done


# Operator

* [Arithmetic Operations](#matlab-arithmetic-operations)<!--fix TOC-->
* [Relational Operations](#matlab-relational-operations)
* [Logical Operations](#matlab-logical-operations)
* [String and Character Formatting](#string-and-character-formatting)
* [Other](#other)
* [Operator Precedence](#operator-precedence)

## [[Matlab Arithmetic Operations\|Matlab Arithmetic Operations]]

| Symbol | Role                                             |
|:------:| ------------------------------------------------ |
| `+`    | Addition; Unary plus                             |
| `-`    | Subtraction; Unary minus                         |
| `.*`   | Element-wise multiplication                      |
| `*`    | Matrix multiplication                            |
| `./`   | Element-wise right division                      |
| `/`    | Matrix right division                            |
| `.\`   | Element-wise left division                       |
| `\`    | Matrix left division (also known as *backslash*) |
| `.^`   | Element-wise power                               |
| `^`    | Matrix power                                     |
| `.'`   | Transpose                                        |
| `'`    | Complex conjugate transpose                      |

## [[Matlab Relational Operations\|Matlab Relational Operations]]

| Symbol | Role                     |
|:------:| ------------------------ |
| `==`   | Equal to                 |
| `~=`   | Not equal to             |
| `>`    | Greater than             |
| `>=`   | Greater than or equal to |
| `<`    | Less than                |
| `<=`   | Less than or equal to    |

## [[Matlab Logical Operations\|Matlab Logical Operations]]

|      Symbol       | Role                                     |
|:-----------------:| ---------------------------------------- |
|        `&`        | Find logical AND                         |
|  <code>\|</code>  | Find logical OR                          |
|       `&&`        | Find logical AND (with short-circuiting) |
| <code>\|\|</code> | Find logical OR (with short-circuiting)  |
|        `~`        | Find logical NOT                         |

## String and Character Formatting

|  Symbol  | Effect on Text                 |
|:--------:| ------------------------------ |
|   `''`   | Single quotation mark          |
|   ``   | Cell delimiter                                |
| `%{ %}` | Block comments that extend beyond one line    |
|   `!`   | Operating system command                      |
|   `?`   | Metaclass for MATLAB class                    |
|   `~`   | Argument placeholder to suppress specific input or output arguments     |
|  `< &`  | Specify superclasses                          |
|  `.?`   | Specify fields of name-value structure when using function argument validation        |

## Operator Precedence

1. `()`
2. `~`, sign `+`, `-`
3. `^`, `.^`, transpose `'`, `.'`
4. `.*`, `*`, `./`, `/`, `.\`, `\`
5. `+`, `-`
6. `:`
7. `<`, `<=`, `==`, `>=`, `>`, `~=`
8. `&`
9. `|`
10. `&&`
11. `||`


</div></div>


## [[Matlab Control Statements\|Matlab Control Statements]]

## [[Matlab Math\|Matlab Math]]

## [[Matlab Graphics\|Matlab Graphics]]

## Other

* [[Matlab Command-Function Duality\|Matlab Command-Function Duality]]
* [[Matlab Function Precedence Order\|Matlab Function Precedence Order]]
* [[Matlab Compatible Array Sizes\|Matlab Compatible Array Sizes]]
* [[Matlab Variable Scope\|Matlab Variable Scope]]
* [[Matlab Timing\|Matlab Timing]]

## Self Teaching

1. [x] Matlab语言、功能、环境基本介绍
2. [x] 表达式、数组和矩阵的基本运算
3. [x] 高维数组及运算
4. [x] 字符串、元胞、结构体
5. [x] Matlab程序设计
6. 数值计算
7. 可视化
8. 图形界面、输入输出

## [[!todo#A\|!todo#A]]

* [ ] 文件 I/O (WZL CH12)
* [ ] 字符
    * [ ] string
    * [ ] [[Matlab Types - Character\|Matlab Types - Character]]
* [ ] Table
