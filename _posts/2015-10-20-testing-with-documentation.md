Say you're learning to code. You've heard about test-driven development. You agree that it's a really great idea. But you're not sure how to do it. Or maybe you don't have much time, maybe because you are trying to solve a toy problem in less than an hour. 

You've also heard that documenting your code for other developers / your future-self developer is really important. But you also know that great code should be self-documenting. So, what other stuff should you document?

[doctest][doctest] is a package for JavaScript (can also be used with CoffeScript), inspired by Python's [doctest][doctest2], that allows you to do both testing and documentation simultaneously. 

This is a cool idea. There are other packages that do something similar (e.g., [SpeckJS][SpeckJS]). These other packages are definitely worth checking out if you are interested in this basic idea. This post focuses on [doctest][doctest] because of its simplicity and similarity to Python's doctest.

To install doctest for use with [node][node], type:

> $ npm install -g doctest

Now you're ready to go. 

Our simple example is to write a function that calculates the factorial of a number. We will put our code into a file called factorial.js.

Step 1, add a failing test. With doctest, you do this by adding comments that look like a [node][node] REPL session. In the factorial.js file, we add the following

{% highlight javascript %}
// factorial :: Number -> Number
// calculate factorial of input number
//
// test 1: if input is not +integer or 0, return undefined
// > factorial('hey this is not a number')
// undefined
//
var factorial = function (n) {
  return null;
};
{% endhighlight %}

Now, go to the command line and type

> $ doctest factorial.js

You should see something like

{% highlight bash %}
retrieving factorial.js...
running doctests in factorial.js...
x
FAIL: expected undefined on line 6 (got "hey this is not a number")
{% endhighlight %}

Step 2, test is failing, so fix it. Back in factorial.js, add some code.

{% highlight javascript %}
// factorial :: Number -> Number
// calculate factorial of input number
//
// test 1: if input is not +integer or 0, return undefined
// > factorial('hey this is not a number')
// undefined
//
var factorial = function (n) {
  if (typeof n !== 'number') {
    return;
  }
  if (n < 0 || n !== ~~n) {
    return;
  }
  return null;
}; 
{% endhighlight %}

On the command line,

> $ doctest factorial.js

Now you should see

{% highlight bash %}
retrieving factorial.js...
running doctests in factorial.js...
.
{% endhighlight %}

This means that the code passed the test, yay! Now clean up the code as necessary and repeat. After several more rounds, you might have something like this in factorial.js

{% highlight javascript %}
// factorial :: Number -> Number
// calculate factorial of input number
//
// test 1: if input is not +integer or 0, return undefined
// > factorial('hey this is not a number')
// undefined
//
// test 2: given valid input, return a number
// > typeof factorial(3)
// "number"
// 
// tests 3/4: for input 0 or 1, should return 1
// > factorial(0)
// 1
// > factorial(1)
// 1
//
// tests 5/6/7: for input n, return n!
// > factorial(3)
// 6
// > factorial(4)
// 24
// > factorial(5)
// 120
//
var factorial = function (n) {
  if (typeof n !== 'number') {
    return;
  }
  if (n < 0 || n !== ~~n) {
    return;
  }
  if (n === 0 || n === 1) {
    return 1;
  }
  return n*(factorial(n-1));
}; 
{% endhighlight %}

You've documented the expected behavior of the function and set up a number of tests simultaneously. Once you're done, when you run doctest factorial.js from the command line, you should see

{% highlight bash %}
retrieving factorial.js...
running doctests in factorial.js...
.......
{% endhighlight %}

Good job, you've passed all your tests!

You can structure your comments differently if it makes things easier to read:

{% highlight javascript %}
/*
factorial, function to calculate the factorial of a number

if input is not +integer or 0, return undefined
> factorial('hey this is not a number')
undefined

given valid input, return a number
> typeof factorial(3)
"number"

for input 0 or 1, return 1
> factorial(0)
1
> factorial(1)
1

for input n, return n!
> factorial(3)
6
> factorial(4)
24
> factorial(5)
120
*/
var factorial = function (n) {
  if (typeof n !== 'number') {
    return;
  }
  if (n < 0 || n !== ~~n) {
    return;
  }
  if (n === 0 || n === 1) {
    return 1;
  }
  return n*(factorial(n-1));
};
{% endhighlight %}

Just make sure you maintain the basic idiom of '>' followed by function invocation, then on next line expected result. There are also ways to test with expressions that are expected to throw errors, see the [documentation][doctest] for more info. Finally, there is an [integration][gruntIntegration] with grunt as well.

[node]: https://nodejs.org/en/download
[doctest]: https://github.com/davidchambers/doctest
[doctest2]: https://docs.python.org/2/library/doctest.html
[SpeckJS]: https://speckjs.github.io/
[gruntIntegration]: https://github.com/paolodm/grunt-doctest
