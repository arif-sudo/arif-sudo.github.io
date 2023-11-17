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
{% highlight language %}
// Hoisting example
console.log(x); // Output: undefined
var x = 5;

// Function hoisting
sayHello(); // Output: "Hello!"
function sayHello() {
  console.log("Hello!");
}

{% endhighlight %}
---

## Currying

---

## Scope

---

## Events

---

## Error handling
