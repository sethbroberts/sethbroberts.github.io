You probably know what permutations are. Here is an example. What are all the permutations of the set {1, 2, 3}? There are six possible permutations, I've labelled them as a) through f).

{% highlight bash %}
a) 1 2 3
b) 1 3 2
c) 2 1 3
d) 2 3 1
e) 3 1 2
f) 3 2 1
{% endhighlight %}

You can think of them as all possible re-orderings of the members of this set (including the original order). In general, given a set of n elements, there are n! possible permutations: n * (n-1) * (n-2) * ... * 2 * 1. Simple enough.

Another way to think of permutations is as bijections from a set to itself. A bijection is a mapping, or a way of associating one thing to another. Here is an example

{% highlight bash %}
1 2 3
2 3 1
{% endhighlight %}

Note how every member of the set on the top is associated with exactly one other member of the same set on the bottom (1 goes to 2, 2 goes to 3, 3 goes to 1). No two distinct elements of the set are mapped to the same destination. Furthermore, each member of the original set is on the "receiving end" of the mapping (i.e., no member is "left out" of being a target of something). This is the essence of a bijection; the one shown above corresponds to the permutation labelled d) in the previous example.  

So, we can actually represent all six of the permutations in our first example as bijections, or special kinds of mappings. Using the same labels we started with, we get

{% highlight bash %}
a)        b)        c)        d)        e)        f)
1 2 3     1 2 3     1 2 3     1 2 3     1 2 3     1 2 3
1 2 3     1 3 2     2 1 3     2 3 1     3 1 2     3 2 1
{% endhighlight %}

Now we have a way of composing permutations. What does that mean? It means that you can put two permutations together, and get another permutation. Let's illustrate this by doing permutation b) first, and then c), and seeing what we get. 

We will do this by looking at what happens to individual elements in the set. Permutation b) maps element 1 to element 1, then permutation c) maps element 1 to element 2. Similarly, 2 gets mapped to 3, and then 3 gets mapped to 3. Finally, 3 gets mapped to 2, then 2 gets mapped to 1. 

So, by putting these operations together, 1 ends up at 2, 2 ends up at 3, and 3 ends up at 1. In other words, b) followed by c) is the same thing as d). We can indicate this result, and other similar results, using a table. The (i,j)th entry is what happens when you do the permutation in row i and then do the permutation in column j. The example we just walked through above corresponds to row b) and column c) -- you can see that element d) is sitting at this row / column.

{% highlight bash %}
.   |  a)    b)    c)    d)    e)    f)
----|-----------------------------------
a)  |  a)    b)    c)    d)    e)    f)
    |
b)  |  b)    a)    d)    c)    f)    e)
    |
c)  |  c)    e)    a)    f)    b)    d)
    |
d)  |  d)    f)    b)    e)    a)    c)
    |
e)  |  e)    c)    f)    a)    d)    b)
    |
f)  |  f)    d)    e)    b)    c)    a)

{% endhighlight %}

Here we have an example of a mathematical structure called a [group][group theory]. A group is a set (e.g., the permutations a) - f) ) together with a binary operation (e.g., two permutations can be composed together) that satisfies a few properties:

1. closure: put any two things in the set together using the binary operation, you get another thing in the same set. For example, using the permutation table above, compose permutations b) and e), that gives f), another permutation. 

2. identity: there is an element (call it I) in the set such that, for any element x, x put together with I via our binary operation gives x as the result. In the example above, a) is that element. So, composing permutation b) with a) gives b).

3. inverses: for any element q in the set, there is an element p, such that when you combine p and q with the binary operation, you get the identity element I as a result. For example, compose e) with d), this gives a), the identity element. So d) is the inverse of e).

4. associativity: if p, q, and r are in the set, and '*' is the symbol for our binary operation, [p * q] * r = p * [q * r]. For example, [b) composed with c)] composed with f) = [d)] composed with f) = c). Also b) composed with [ c) composed with f) ] = b) composed with [d)] = c), same result.

If you study the above table, you will see that all of these properties are exemplified. [Group theory][group theory] in mathematics is the study of structures like these. It is a fascinating subject, having a beauty all its own (lots of symmetry floating around) and applications in fields such as physics, music, and materials science.


[group theory]: https://en.wikipedia.org/wiki/Group_theory

