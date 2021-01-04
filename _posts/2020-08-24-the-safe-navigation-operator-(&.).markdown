---
layout: post
title:  "The Safe Navigation Operator (&.)"
date:   2020-08-24
categories: ruby
---
You could read [here]({% post_url 2020-08-14-the-ternary-operator %}) that it is a good habit to make your codes shorter, especially when you working on a big application. In this post I am going to write about another way how to write compact codes. We can use <b>the safe navigation operator</b>. This allows replacing 
<div class="code">
{% highlight ruby %}
a = foo && foo.bar && foo.bar.baz
{% endhighlight %}
</div>
with
<div class="code">
{% highlight ruby %}
a = foo&.bar&.baz
{% endhighlight %}
</div>
From Ruby logic we should remember that "&&" means that if both the operands are non zero, then the condtition is true. For example:
<div class="code">
{% highlight ruby %}
a = true && false
=> false
{% endhighlight %}
</div>
I will give you also an example how to use the safe navigation operator from my own application:
<div class="code">
{% highlight ruby %}
@date = params[:date]&.to_date
{% endhighlight %}
</div>
Means exactly the same as:
<div class="code">
{% highlight ruby %}
@date = params[:date] && params[:date].to_date
{% endhighlight %}
</div>
It is really simple, isn't it? It is very good when you don't need to write the same things all the time and you can make your code more compact in easy way.