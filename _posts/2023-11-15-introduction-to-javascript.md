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
  {% highlight language %}
  1. students.forEach(myFunction);
     function myFunction(student) {  
       console.log(`${student} is a great student`)
     }  
  2. students.forEach(function (student) {  
       console.log(`${student} is a great student`)  
     });   
  3. students.forEach((student) => console.log(`${student} is a great student`));  
  {% endhighlight %}
> You **can’t** use continue and break statements with forEach loop, because forEach loop always loop whole array

---

## Using for loop with arrays

{% highlight language %}
for (const student of students) {  
  console.log(`${student} is a great student`)  
}
{% endhighlight %}

### map
* map() - creates a new array from calling a function or a callback function for each array element. map() does not mutate the original array and does not execute the function for empty elements
{% highlight language %}
  const numbers = [ 1, 11, 32, 5 ];  
  const tripleNumbers = numbers.map( (item) => item * 3 )
  // Output: [ 3, 33, 96, 15 ]
{% endhighlight %}

### filter
* filter() - creates a new array filled with elements that satisfy certain condition. filter() does not mutate the original array and does not execute the function for empty elements

{% highlight language %}
  const ages = [ 32, 33, 12, 40 ];  
  const adult = ages.filter(item => item >= 18)
  // Output: [ 32, 33, 40 ]
{% endhighlight %}

### Reduce
* reduce() -executes a reducer function for each array element The reduce() method returns a single value: the function’s final result. It does not execute the function for empty array elements and does not change the original array. A reduce function can take 2 parameters: a reducer function and initialValue. (reducer function is required, but initialValue is optional) The reducer function can accept four parameters  
1. total: It is required parameter and used to specify the initialValue, or the previously returned value of the function.<br>
2. currentValue: It is required parameter and used to specify the value of the current element.<br>
3. currentIndex: It is optional parameter and used to specify the array index of the current element.<br>
4. arr: It is optional parameter and used to specify the array the current element belongs to.

reduce() example  
1. {% highlight language %}
 const numbers = [1,7, 28, 30, 4, 40, 3, 6];  
 numbers.reduce ( (total, cur, i, arr) => {
  console.log(`Iteration: ${i} : ${total}`)  
  return total + cur;  
}, 0)  
{% endhighlight %}
2. {% highlight language %}
 [1, 2, 3, 4].reduce((a, b) => a + b, 0)  
  // Output: 10  
{% endhighlight %}

---

## Find & findIndex methods
* find() - method returns the value of the first element that passes a test. It returns undefined if no elements are found. This method does not change the original array and does not execute the callback function for empty elements
{% highlight language %}
  const numbers = [21, 11, 32, 5];
  numbers.find(number => number <= 18)
  // Output: 11    
{% endhighlight %}

* findIndex() - method works almost the same way as find(). It returns the index of the first element that passes a test. It returns -1 if no match is found. This method does not execute the function for empty elements and does not change the original array.
{% highlight language %}
  const numbers = [21, 11, 32, 5];
  numbers.findIndex(number => number <= 18)
  // Output: 1    
{% endhighlight %}

---

## Some & every
* some() - checks whether at least one element in the array passes the test provided callback function. This method does not change the original array and does not execute the callback function for empty elements. It returns true if, in the array, it finds an element for which the provided function returns true, otherwise it returns false.
{% highlight language %}
  const numbers = [1, 2, 3, 4, 5];
  numbers.some((element) => element % 2 === 0);
  // Output: true      
{% endhighlight %}

* every() - checks whether all elements in the array pass the test provided by theccallback function. It returns a boolean value.
{% highlight language %}
  const numbers = [1, 2, 3, 4, 5];
  numbers.every((element) => element > 40 );
  // Output: true      
{% endhighlight %}

---

## Flat method
* flat() - flattens the elements of a nested array to a specific depth. 
{% highlight language %}
  const arr1 = [0, [1, 2], [3, 4]];
  arr1.flat(); // [0, 1, 2, 3, 4]
  const arr2 = [0, 1, 2, [8, [5, [3, 4]]]];
  arr2.flat(2); // [0, 1, 2, 8, 5, [3, 4]] 
{% endhighlight %}

> The depth level specifying how deep a nested array structure should be flattened.
> Defaults to 1. ([ ] – depth is 1, [[ ]] –depth is 2 and etc.)

{% highlight language %}
  const veryDeep = [1, [2, 2, [3, [4, [5, [6]]]], 1]];
  veryDeep.flat (Infinity); // [1, 2, 2, 3, 4, 5, 6, 1]
{% endhighlight %}

---

## Sort method
* sort() - sorts the elements of an array. This method overwrites the original array. It sorts the elements as strings in alphabetical and ascending order.
{% highlight language %}
  letters.sort()
{% endhighlight %}

For sorting numbers, you can use below syntax:
{% highlight language %}
  numbers.sort(function(a, b){return a-b}); (ascending order)
  numbers.sort(function(a, b){return b-a}); (descending order)
{% endhighlight %}

---

# Data Structure

## Array destructuring
The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct
variables.
{% highlight language %}
  a) const arr = ['James', 'Bond', 7];
     const [name, surname, code ] = arr;
  b) obj = {
      name : 'Mike',
      favoriteNumbers : [4, 6, 10]
     }
const [firstNumber, , secondNumber] = obj.favoriteNumbers // 4,10
{% endhighlight %}

---

## Object destructring

{% highlight language %}
  obj = {
   name : 'Mike',
   surname: 'Doe',
   favoriteNumbers : [4, 6, 10]
}
const {name, surname, favoriteNumbers } = obj;
const {name: ad, favoriteNumbers: number } = obj
{% endhighlight %}

---

## Spread or Rest operator (…)
{% highlight language %}
  const numbers = [1, 2, 3, 4, 5, 6]
  const numbers2 = [7, 8, 9, 0]
  const library = 'react'
  const digits = […numbers, …numbers2] //merge arrays
  const letters = […library]
  const copyNumbers = […numbers] // creates a copy of the aray
  const [a, b, …others] = numbers (rest operator)
{% endhighlight %}

---

## Rest parameters
{% highlight language %}
  function sum(...theArgs) {
    return theArgs.reduce((previous, current) => { return previous + current; });
}
console.log(sum(1, 2, 3));// expected output: 6
console.log(sum(1, 2, 3, 4));// expected output: 10
{% endhighlight %}

{% comment %}
Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
{% endcomment %}
