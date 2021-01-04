---
layout: post
title:  "The Ternary Operator"
date:   2020-08-14
categories: ruby
---
It is good to remember to make your codes more compact. It is very important when you working on big applications with so many files and lines of codes. Remember about this rule during your learning and you will have good habits in your future.<br>One of the ways to make your code shorter, is <b>the ternary operator</b>. You can use it in else/if statements. Here you have structure of it: 

<div class="code">
{% highlight ruby %}
if boolean?
  do_something
else
  do_something_else
end
{% endhighlight %}
</div>

Means exactly the same as:
<div class="code">
{% highlight ruby %}
boolean ? do_something : do_something_else
{% endhighlight %}
</div>

Or easier: 
<div class="code">
{% highlight ruby %}
condition ? True : false
{% endhighlight %}
</div>

I will give you also a practical example:

<div class="code">
{% highlight ruby %}
flower_price = 50

if flower_price < 100
  puts "Let's buy flowers!"
else
 puts "Don't buy flowers today :("
end
{% endhighlight %}
</div>

Instead of this, you can write just:
<div class="code">
{% highlight ruby %}
puts flower_price < 100? "Let's buy flowers!" : "Don't buy flowers today :("
{% endhighlight %}
</div>