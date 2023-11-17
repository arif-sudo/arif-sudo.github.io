---
title:  "Javascript Part 2"
layout: post
---

## Functions
In javascript functions consists of 2 parts
1. Function name
2. Function body

### Function expressions looks like:
```
const calculate = function () { … }
```

### Arrow funcitons
```
  const greeting = () => {console.log(‘hello world’)}
  const print = name => { console.log(`Hi, ${name}`}
  const calculate = (num1, num2) => num1+num2
```

---

## Hoisting
You can call **function declarations** before they are defined in
code.
```
// Hoisting example
console.log(x); // Output: undefined
var x = 5;

// Function hoisting
sayHello(); // Output: "Hello!"
function sayHello() {
  console.log("Hello!");
}
```
---

## Currying
Currying is a concept in functional programming where a function is transformed into a sequence of functions, each taking a single argument. The result of each function is another function that takes the next argument in the sequence. 
```
// Normal (uncurried) function
function add(a, b, c) {
  return a + b + c;
}

console.log(add(2, 3, 4)); // Output: 9

// Curried version
function curryAdd(a) {
console.log(a, "This is a")
  return function(b) {
    return function(c) {
      return a + b + c;
    };
  };
}

const curriedAdd = curryAdd(2);
console.log(curriedAdd);
console.log(curriedAdd(3)(4)); 
// Output:
2 'THIS IS a'
 ƒ (b) {
    return function(c) {
      return a + b + c;
    };
}
9

```
---

## Scope
Scope is the term used to describe which parts of our code have access to which variables. [For Loop & Timeout](https://www.freecodecamp.org/news/thrown-for-a-loop-understanding-for-loops-and-timeouts-in-javascript-558d8255d8a4/)
* Examle 1
```
// Global scope
let globalVar = "I am global";

function exampleScope() {
  // Function scope
  let localVar = "I am local";
  console.log(globalVar); // Accessing global variable
  console.log(localVar); // Accessing local variable
}

exampleScope();

for(var a = 1; a < 10; a++) {} // declared "inside" the loop
console.log(a); // prints "10" and is called "outside the loop"
```
* Example 2
```

function myFunction1() {
   var a = 'Brandon';
   console.log(a);
}
function myFunction2() {
   var a = 'Matt';
   console.log(a);
}
function myFunction3() {
   var a = 'Bill';
   console.log(a);
}
myFunction1() //Brandon
myFunction2() //Bill
myFunction3() //Matt
```
It appears the variable a is unique to each function. 

* Example 3
What will be output of this loop?
```
for(var i = 1; i < 6; i++) {
  setTimeout(function() {
     console.log(i);
  },0);
}
console.log('The loop is done!');
```
> Output: 
> The loop is done!
> 6 6 6 6 6
Every time we loop, setTimeout() is passed outside of the call stack and enters the event loop. Because of this, the engine is able to move to the next piece of code. The next piece of code happens to be the remaining iterations of the loop, followed by console.log(‘The loop is done!’).

### **Applying the principles of scope to our example**
```
for(var i = 1; i < 6; i++) {
   function timer(){ // create a unique function (scope) each time
      var k = i; // save i to the variable k which
      setTimeout(()=>{
         console.log(k);
      },0);
   }
   timer();
}
```
> Output:
> The loop is done!
> 1 2 3 4 5

We are beginning to get into the topic of closures.
Remember, each function creates a unique scope. Because of this, variables with the same name can exist in separate functions and not interfere with each other. In our most recent example, each iteration created a new and unique scope (along with a new and unique variable k). When the for loop is done, these five unique values of k are still in memory and are accessed appropriately by our console.log(k) statements. That is closure in a nutshell.
```
for(let i = 1; i < 6; i++) {
   setTimeout(()=>{
      console.log(i);
   },1000);
}
console.log('The loop is done!');
```
Just by changing var to let, we are much closer to the result we want.  
Let does 2 things:  
1. First, it makes i available only inside our for loop. If we try to log i outside of the loop, we get an error. This is because let is a block scope variable. If it is inside a block of code (such as a for loop) it can only be accessed there. var is function scoped.
2. The second thing let does for us is create a unique value of i each time the loop iterates. When our loop is over, we have created six separate values of i that are stored in memory that our console.log(i) statements can access. With var, we only had one variable that we kept overwriting.

* An example to show let vs var behavior:
```
function variableDemo() {
   var i = 'Hello World!';
   for(let i = 1; i < 3; i++) {
      console.log(i); // 1, 2, 3
   }
   console.log(i); // "Hello World!" 
   // the for-loop value of i is hidden outside of the loop with let
}

variableDemo();
console.log(i); //Error, can't access either value of i
```

---

## Events

---

## Error handling
