---
{"dg-publish":true,"permalink":"/js-arrow-function/","title":"JS Array Function","created":"2022-11-17T17:22:24","updated":""}
---

> [!meta]-  
sup:: [[JS Function\|JS Function]]  
state:: done

# JS Array Function

Another way to create a function and assign it to a variable (this process is called [[JS Arrow Function#Function Expression\|#Function Expression]]) is called **arrow function**, which is similar to [[Python Lambda Function\|Python Lambda Function]]

```js
let myFun = (para1, para2) => expression
```

This creates a function `myFun` that accepts arguments `para1` and `para2`, then evaluates the `expression` on the right side with their use and **returns its result**.

In other words, it’s the shorter version of the [[JS Arrow Function#Function Expression\|#Function Expression]]:

```js
let myFun = function(para1, para2) {
  return expression;
};
```

* If we have only one parameter, then parentheses around parameters can be omitted
    - [*] This gives the simplest form of a function: `para => expression`
* If there are no parameters, parentheses will be empty (but they should be present)
* For more complex expressions, like multiple expressions or statements, we should enclose them in curly braces `{}`, then use a normal `return` within them

> [!ex] Dynamically Create a Function
>
> ```js
> let age = prompt("What is your age?", 18);
> 
> let welcome = (age < 18) ?
>   () => alert('Hello') :
>   () => alert("Greetings!");
> 
> welcome();
> ```
>
