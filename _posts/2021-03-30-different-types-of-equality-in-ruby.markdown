---
layout: post
title: "Different Types Of Equality In Ruby"
date: 2021-03-30
categories: ruby
---
In Ruby there are a few ways of checking equality between objects. Of course, every of them means something different. In this post I will write something about this subject. <br>
Firstly, I will write about symbol which is the most known for me and I use it the most - "==". This sign can compare two objects and return true if these entities are the same. I use it mainly in "if/else" statements. <br>
The second sign is "===". I saw it for the first time and read about it recently. It calls the Case Equality Operator (Case Subsumption Operator). This method is invoked on the given pattern, not on the specific elements of the collection. Let's look at the example: <br>
<div class="code">
{% highlight ruby %}
(1..3) == 2 #=> false
(1..3) === 2 #=> true
{% endhighlight %}
</div>
The last type of equality about which I would like to write, is ".eql?". It returns true when you compare two objects and they have the same value. The example below shows how it works:
<div class="code">
{% highlight ruby %}
1.eql? 1 #=> true
1.eql? 1.0 #=> false
{% endhighlight %}
</div>