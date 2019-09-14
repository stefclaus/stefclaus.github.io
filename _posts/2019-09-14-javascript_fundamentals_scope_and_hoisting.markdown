---
layout: post
title:      "Javascript Fundamentals: Scope and Hoisting"
date:       2019-09-14 18:09:13 +0000
permalink:  javascript_fundamentals_scope_and_hoisting
---

This blog post will explain both scope and hoisting in Javascript, and it will explain how ES6 syntaxes 'let' and 'const' impact both hoisting and scope, and how those syntaxes compare to to the pre-ES6 'var'. 


**Var, Let, and Const Basics**

Pre ES6, the only way to declare a variable was with Var. But var has some issues--namely, it will allow to you declare the same variable twice without throwing an error (it will just happily return the most-recently-declared variable value) instead of letting you know that that variable has already been assigned somewhere else. Not good!

**Let**: Unlike with var, assigning let to a variable a second time will throw an error. This is good! However, just like with var, let will allow you to ressign a variable. 

Just to make that super clear with an example:

Let will allow you to do this:

```
let name = 'Stef Claus'
name = 'Stefanie Claus'
```

But not this!

```
let name = 'Stef Claus'
let name = 'Stefanie Claus'
```


**Const**:

Like with let, const won't let you assign a variable a second time. However, unlike let you can't reassign it either. Using the same examples as above: 

Const will NOT allow you to do this:

```
let name = 'Stef Claus'
name = 'Stefanie Claus'
```

And it will also not allow you to do this!

```
let name = 'Stef Claus'
let name = 'Stefanie Claus'
```

All of these behaviors give us good use cases for var, let, and const.

Var should be not be used with ES6, although it is important for beginner users to understand it to be able to look at legacy code.

Let is great in cases where you know your variable is going to change--a counter, for example.

Const should be used for everything else.

**Scope**
 
 First off, what is scope? Scope is the concept of *where something is available*.  
 
 At any point in your Javascript, you may or may not be able to access a variable or method. If you can access the variable or method you have your eye on, you're said to be in scope. If you can't, you're out of scope. 
 
 There are three different types of scope:
 
Global Scope: Variable and fucntions declared in the global context are avaiable anywhere in your code. This is sort of the default state for functions and varibles:  If a variable or function is not declared inside a function or block, it's in the global execution context.
 
 Function Scope: When you declare a new function, you create a new scope: varibables and other functions declared in that function will only be availble inside that function. (The exception here is that if you don't use any keyword to declare your variable, in which case that variabale will have a global scope. This is bad practice.)
 
 Block scope: A block also creates its own scope--but not with var. Here's an example to make that a bit clearer: 
 
```
if (true) {

  var myFirstVar = 'Colony Club is the best place to code';

  const mySecondVar = 32;
 
  let myThirdVar = 2019;
}
``` 
 
In this case, only myFirstVar will be available outside of the block. Calling mySecondVar and myThirdVar will both return uncaught reference errors.
 
** Hoisting** 

To understand hoising, you need to understand that JavaScript runs in two distinct phases: a compilation phase and an execution phase. 

During the compliation phase, JavaScript ignores all function invocation and just stores everything in memory. Then in the execution phase, Javascript moves throught the functions stored in memory and invokes them. This is what hoising is--it can sort of feel like JavaScript is 'hoisting' all variable declartaions to the top of our code  (even though that's not excatly what is happening.)

With var, is that JavaScript will allow you to reference variables before they've been initalized. (We don't see that issue with const and let).

Consider the below code, taken from an example from the Flatiron curriculum.

```
function myFunc () {
  console.log(hello);
	
  var hello = 'World!';

 
  return hello;
	

```

This will output:
```
// LOG: undefined
// => "World!"
```

Yikes, what happened to our nice console.log? 

We see LOG: undefined because var gets assigned 'unknown' during the complitaion phase. Then it begins the executiton phase step-by-step, which means that when it reaches the console.log line, it is still unknown, but it is known during the return line.

This gets cleared up when we use let or const. Consider the same code, but using const:

```
function myFunc () {
  console.log(hello);
	
  const hello = 'World!';
 
  return hello}
```

This returns: 

```
Uncaught ReferenceError: Cannot access 'hello' before initialization
```

Helpful! Now we know what to do next.

Rearranging the code to be in line with best practices (putting our declarations at the top):

```

function myFunc () {
  const hello = 'World!';

  console.log(hello);	
 
  return hello}
```


```LOG: World!
"World!" ```

This is much more what we would expect!

**Bottom line:
**
It is considered ES6 best practice to always use const and let, and to declare your variables at the top of their scope.




