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

---

## Splice
* splice() - is so similar to slice method, but the main difference is that splice() actually changes the original array. This method returns the deleted part of the array  
  letters -> ['B', 'E', 'U']<br>
  letters.splice(1) -> [ 'E', 'U'] (letters -> ['B'])<br>
  letters.splice(-1) -> removes the last element of letters array<br>
  const letters2 = letters.splice() -> [ ]  ( an empty array )

* The splice() method can add new elements into the array<br>
  letters -> ['B', 'E', 'U']<br>
  letters.splice(1, 1, 'M') -> letters -> [ 'B', 'M', 'U'] ( But method itself returns ['E'] )

---

## Reverse & Concat methods
* reverse() - method reverses the order of the elements in an array and changes the original array.  
  letters -> ['B', 'E', 'U']  
  letters.reverse() = > ['U', 'E', 'B']

> If you want to reverse an array without mutating original array, you can use slice and reverse methods together.
  const newLetters = letters.slice().reverse();

* concat() - joins two or more arrays and returns a new array, containing the joined arrays.<br>This method does not change the existing arrays.<br>
  const students1 = ["Cecilie", "Lone"]<br>
  const students2 = ["Emil", "Tobias", "Linus"]<br>
  const students3 = ["Mike", "Neil"]<br>
  const students = students1.concat(students2, students3) -> ['Cecilie', 'Lone', 'Emil', 'Tobias', 'Linus', 'Mike', 'Neil']

---

## Join & at methods
* join() - method returns an array as a string and does not change the original array. It takes a separator as an argument The default separator is comma.  
  letters.join() => 'B,M,U'<br>
  letters.join('_') => 'B_M_U'<br>

* at() - takes an integer value and returns the item at that index, allowing for positive and negative integers. **letters.at(0)** is equivalent syntax of **letters[0]**. However, it is really handful if you want to get the last element of an array. Instead of using **array[array.length-1]**, you can call **array.at(-1)**

* forEach() - method calls a function or a callback function for each element in an array. This method is not executed for empty elements.
  1. students.forEach(myFunction);<br>
     function myFunction(student) {  
       console.log(`${student} is a great student`)
     }  
  2. students.forEach(function (student) {  
       console.log(`${student} is a great student`)  
     });   
  3. students.forEach((student) => console.log(`${student} is a great student`));  


{% comment %}
Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
{% endcomment %}
