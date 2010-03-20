---
layout: post
title: Object.methods - A Gotcha I Hadn't Seen Before
---
There are many posts about String.each, the new block shadowing and even a post or two about some of the C level changes.

However I had not seen anyone point out this little change that could affect certain meta-programming situations. Calling .methods returns a list of all the methods which a certain object or class responds to.

For the most part this is only useful in IRB. I often call

{% highlight ruby %}
  test_object.methods - Object.methods
{% endhighlight %}

when I can't remember a method name.

The change between Ruby 1.8 and Ruby 1.9 is that .methods now returns an array of symbols where in 1.8 it returned an array of strings. For the most part no problem, but something to be aware of. .respond_to? appears to still take either a string or a symbol, so if you're just checking an object do this:

{% highlight ruby %}
  object.respond_do(:method)
{% endhighlight %}

instead of:

{% highlight ruby %}
  object.methods.include?("method")
{% endhighlight %}
