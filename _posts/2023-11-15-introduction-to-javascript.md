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

if(typeof x === undefined) - WRONG
if(typeof x === 'undefined') - CORRECT

---

## Type conversion & type coersion
1. **Type conversion** is when you manually convert a value from one type to another using some methods (it is known as Explicit Conversion)
2. **Type coercion** is when JS converts a value from one type to another automatically (it is known as Implicit Conversion)

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.


{% comment %}
To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
{% endcomment %}
