---
title: "Javascript"
layout: post
---

## Variable declaration
* Let
* Var
* Const

---

## Data types
1. Primitive data types
  * Number
  * String
  * Boolean
  * Undefined -> let lastname (has one and only one value in it: undefined)
  * Null -> const obj = null (tpyeof return 'object' )
  * Symbol -> const country = Symbol('China')
  * BigInt -> const bigNum = BigInt('123456789123456789123456789')

   
2. Object data types
  * Objects
  * Arrays
  * Functions

> There is no function data type in JS. However, if you use the typeof operator to find the data type of a function, you will see that it returns `function`.

---

## Typeof operator
Typeof operator always returns string.

if ( typeof x === undefined )  -  WRONG  
if ( typeof x === 'undefined' )  -  CORRECT

---

## Type conversion & type coersion
1. **Type conversion** is when you manually convert a value from one type to another using some methods (it is known as Explicit Conversion)
2. **Type coercion** is when JS converts a value from one type to another automatically (it is known as Implicit Conversion)

---

## Type Conversion
1. String()  
  String(676)  
2. toString()  
  num.toString()
3. toFixed()  
  const num = 601.488  
  num.toFixed(2) => 601.49
4. Number()  
  Number('123')  
5. parseInt()  
  parseInt('123SomeText')  
6. parseFloat()  
  parseFloat('3.14Pi')

---

## Basic array methods
* pop() - removes the last element from an array and returns the value that was removed
* push() - adds a new element to an array as a last element of array and returns the new array length.
* shift() - removes the first array element and "shifts" all other elements to a lower index.
* unshift() - adds a new element to an array at the beginning and returns the new array length.

---

## Slice
* slice() - lets us to extract a slice of an array into new array without changing the original array.  
  const letters = ['B', 'E', 'U']  
  letters.slice(1) -> [ 'E', 'U']  
  const lettersCopy = letters.slice() -> Gets exact same copy of letters array  

* The slice method can take two arguments. Then the method will select elements from the start argument, and up to (but not including) the end argument.  
  letters.slice(0, 2) => [ 'B', 'E']

* The slice() method can take negative value as an argument.
  letters.slice(-1) - the last element of array  
  letters.slice(-2) - the last two elements of array  
  letters.slice(0, -1) => [ 'B', 'E'] (start slicing from index 0, and slice everything except the last element) 
  
{% comment %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
{% endcomment %}
