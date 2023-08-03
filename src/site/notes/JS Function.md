---
{"type":"note","title":"JS Functions","created":"2021-08-25T23:18:27","modified":"2022-11-18T02:32:01","dg-publish":true,"sup":["[[JavaScript]]"],"state":"done","permalink":"/js-function/","dgPassFrontmatter":true,"updated":"2022-11-18T02:32:01"}
---


# JS Functions

> [!tip] Built-in Functions
>
> The JavaScript language has many built-in functions. In fact, some of the code you are calling when you invoke a built-in browser function couldn't be written in JavaScript — many of these functions are calling parts of the background browser code, which is written largely in low-level system languages like C++, not web languages like JavaScript.
>
> And some built-in browser functions are not part of the core JavaScript language — some are defined as part of **browser APIs**, which build on top of the default language to provide even more functionality.

## Definition

Use `function` [[JS Keyword\|JS Keyword]] to define a function

```js
function myFunction(arg1, arg2) {
    doSomeOperations;
    let result = expression;
    return result;
}
```

### Return

* Functions without `return` [[JS Keyword\|JS Keyword]]/statement *return* [[JS Types - undefined\|JS Types - undefined]]
* Just like [[JS Type#typeof\|JS Type#typeof]], `return` is both a [[JS Function\|JS Function]] and a [[JS Operator\|JS Operator]]
    * This means there are two forms of syntax
        * `return x;`
        * `return(x);`
* `return` **terminate** the function: the remaining code in the function definition after `return` will not be executed
    * Such code are ==unreachable==
* It is possible to use `return` without a value, which simply exits the function
    * In this case the function also *returns* [[JS Types - undefined\|JS Types - undefined]]
* #R Never add a newline between `return` and the value
    * See [[JS Basics#^js-semicolon-newline\|JS Basics#^js-semicolon-newline]]
    * If we want the returned expression to wrap across multiple lines
        1. We can start it at the same line as `return`
        2. Or we can wrap them with parentheses and put the opening parentheses at the same line as `return`

## Invoking

Unlike [[Python\|Python]], where functions must be defined before any invoking; and unlike [[MATLAB\|MATLAB]], where functions must be listed at the end of the script; JS allows to define the functions anywhere and invoke them anywhere.

## Default values

If a function is called, but an argument is not provided, then the corresponding value becomes [[JS Types - undefined\|JS Types - undefined]]. However, we can provide its **default value** in the function definition

```js
function myFun(para1, para2 = "no text given") {
  console.log(para1 + para2);
}

myFun("Notice: "); // 'Notice: no text given'
```

Now if the `para2` parameter is not passed, it will get the value `'no text given'`. The default value can even be another function call.

#R If the default value is an expression or function, it **will and only will** be evaluated when the function is called and the respective parameter is not passed.

> [!tip] Alternative Default Parameters
>
> Sometimes it makes sense to assign default values for parameters not in the function declaration, but at a later stage. In these cases we can check if the parameter is passed during the function execution, by comparing it with `undefined`
>
> ```js
> function showMessage(text) {
>     // ...
> 
>     if (text === undefined) { // if the parameter is missing
>     text = 'empty message';
>   }
> 
>   alert(text);
> }
> 
> showMessage(); // empty message
> ```
>
> Or we could use the `
> Or we could use the `||` and `??` [[JS Operator - Logical\|logical operator]]s
> Or we could use the `
>
> ```js
> function showMessage(text) {
>   // if text is undefined or otherwise falsy, set it to 'empty'
>   text = text || 'empty';
>   //...
> }
> function showCount(count) {
>   // if count is undefined or null, show "unknown"
>   alert(count ?? "unknown");
> }
> 
> showCount(0); // 0
> showCount(null); // unknown
> showCount(); // unknown
> ```
>

## Arguments

Within every function, there is an **[[JS Type - Array\|JS Type - Array]]-like** [[JS Types - Object\|JS Types - Object]] called `arguments` that contains the values of the arguments passed to that function.

* The arguments object is not an [[JS Type - Array\|JS Type - Array]]: it lacks all Array properties and methods except length and property access `[]`

## Anonymous Function

When we don't need to store a function in a name, we can define an anonymous function

```js
function() {
    // Do something
}
```

You generally use an anonymous function along with an **event handler**, for example the following would run the code inside the function whenever the associated button is clicked:

```js
const myButton = document.querySelector('button');

myButton.onclick = function() {
  alert('hello');
}
```

With event handler, anonymous function is like a **when** statement: it executes some code when an event is triggered.

### Function Expression

Just like any other type, an anonymous function can be assigned to a [[JS Variable\|JS Variable]]. Such form of creating a function is also known as ==function expression==.

```js
/* Define */
let varFun = function() {
    // Do somethinf
};

/* Invoke */
varFun();
```

* You need a the parenthesis `()` to **execute** the function
    * Otherwise you just mention the function without causing its execution
        * #E `typeof varFun` won't execute the function
* But unlike general function declaration, function expressions are not ==hoisted==
    * i.e. the [[JS Variable\|JS Variable]] (function) need to be assigned first before being invoked.
* And just like general [[JS Variable\|JS Variable]]s, you can also assign the function to be the value of **multiple variables**

> [!ex] Callback Functions
>
> ```js
> function ask(question, yes, no) {
>   if (confirm(question)) yes()
>   else no();
> }
> 
> function showOk() {
>   alert( "You agreed." );
> }
> 
> function showCancel() {
>   alert( "You canceled the execution." );
> }
> 
> // usage: functions showOk, showCancel are passed as arguments to ask
> ask("Do you agree?", showOk, showCancel);
> ```
>
> The arguments `showOk` and `showCancel` of `ask` are called ==callback functions== or just ==callbacks==.
>
> The idea is that we pass a function and expect it to be "called back" later if necessary. In our case, `showOk` becomes the callback for “yes” answer, and `showCancel` for “no” answer.
>
> We can use Function Expressions to write the same function much shorter:
>
> ```js
> function ask(question, yes, no) {
>   if (confirm(question)) yes()
>   else no();
> }
> 
> ask(
>   "Do you agree?",
>   function() { alert("You agreed."); },
>   function() { alert("You canceled the execution."); }
> );
> ```
>

> [!tip] A Function is a Value Representing an "Action"
>
> Regular values like strings or numbers represent the **data**. A function can be perceived as an **action**. We can pass it between variables and run when we want.

## Arrow Function


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/js-arrow-function/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# n-h1

</div>




# JS Array Function

Another way to create a function and assign it to a variable (this process is called [[JS Function#Function Expression\|#Function Expression]]) is called **arrow function**, which is similar to [[Python Lambda Function\|Python Lambda Function]]

```js
let myFun = (para1, para2) => expression
```

This creates a function `myFun` that accepts arguments `para1` and `para2`, then evaluates the `expression` on the right side with their use and **returns its result**.

In other words, it’s the shorter version of the [[JS Function#Function Expression\|#Function Expression]]:

```js
let myFun = function(para1, para2) {
  return expression;
};
```

* If we have only one parameter, then parentheses around parameters can be omitted
    - <span class="alt-check alt-check-impt">This gives the simplest form of a function: `para => expression`</span>
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


</div></div>


## Function Scope

* Functions have their own local scope, in which variables and nested functions cannot be accessed from outside
* Everything in the global scope can be accessed anywhere
* Functions have **full control** of global variables, meaning that they can even modify their values and the modification is **preserved**

    ```js
    let a = 1;
    function modify() {
        a = 'hello';
    }
    console.log(a); // 1
    modify();
    console.log(a); // 'hello'
    ```

* If a same-named variable is declared inside the function then it **shadows** the outer one

    ```js
    let a = 1;
    function shadow() {
        let a = 'hello';
        console.log(a);
        a = 'world';
    }
    shadow(); // 'hello'
    console.log(a); // 1
    ```

    * This also means that you can *re-declare* a [[JS Variable\|JS Variable]] in the local scope of a function
* **Parameters are declared**
    * So you can directly use parameters in the function declaration without re-declaring them
* **Parameters are local**
    * Arguments passed to the function are assign to parameters, thus the variables being passed will stay intact, unless they are explicitly modified in the function

    ```js
    let a = 1;
    function intact(a) {
        console.log(typeof a);
        a += 10; // Here a is the local one
    }
    intact(); // 'undefined', but no error
    intact(a); // 'number', since 1 is passed to it
    console.log(a);
    ```
