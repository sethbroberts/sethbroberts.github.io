In our last installment, we talked about permutations, and how permutations can be thought of as bijective mappings from a set to itself. When viewed this way, we can understand what it means to "compose permutations": first do one, then do the other, and this gives a 3rd mapping that is itself another permutation.

So now let's consider what happens when you compose a permutation with itself. Here is an example. Take this permutation:

{% highlight bash %}
1 2 3
2 3 1
{% endhighlight %}

It maps 1->2, 2->3, and 3->1. Now compose this permutation with itself. So, 1->2->3. Also, 2->3->1. Finally, 3->1->2. So we end up with the following permutation:

{% highlight bash %}
1 2 3
3 1 2
{% endhighlight %}

Now, compose this resulting permutation with the one we started with. So, 1->3->1. 2->1->2. 3->2->3. Interesting, now we have the "identity" permutation as a result of the last operation:

{% highlight bash %}
1 2 3
1 2 3
{% endhighlight %}

OK, last time. Do it once more. Take the last result, compose it with the permutation we started with. 1->1->2. 2->2->3. 3->3->1. So the final result is:

{% highlight bash %}
1 2 3
2 3 1
{% endhighlight %}

That's the permutation we started with. Interesting. Notice we did NOT actually visit all the permutations, only a subset of them. In the last blog post, I labelled all the possible permutations of the set {1, 2, 3} as a), b), c), d), e), and f). In the above, we started with permutation d), composed it with itself, that gave us permutation e). We then composed e) with d) and got a). Finally we composed a) with d) and got d). We never "saw" b), c), or f).

Here's another way of looking at it. By applying the permutation to itself over and over, we eventually come back to where we started. But we've only seen a subset of the possible permutations. Look at this table of possibilities:

{% highlight bash %}
.   |  a)    b)    c)    d)    e)    f)
----|-----------------------------------
a)  |  a)    .     .     d)    e)    .
    |
b)  |  .     .     .     .     .     . 
    |
c)  |  .     .     .     .     .     . 
    |
d)  |  d)    .     .     e)    a)    . 
    |
e)  |  e)    .     .     a)    d)    . 
    |
f)  |  .     .     .     .     .     . 

{% endhighlight %}

This is the same table from the last post, showing all possible binary operations of composing two permutations (row by column). I've simplified the table to show just the permutations we visited.

It turns out that this "sub table" has all the properties of the group we mentioned last time. Only it's a "subset" of the original group. This is called a subgroup.

You can find other subgroups by doing the same thing with a different permutation. Pick one. Compose it with itself until you get the original permutation as a result. The list of all the permutations you visited, together with the binary operation of composition, is a subgroup.


