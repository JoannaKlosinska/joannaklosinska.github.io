---
layout: post
title:  "Sorting Arrays And Hashes In Ruby"
date:   2020-08-27
categories: ruby
---
If you read my previous posts, you could see there that I am working on a calendar application where users can booking dates for their trainings. There is a card on the page where user can see all of his bookings. It was important for me that have all of these reservation in good sequence. Fortunately, in Ruby we have <b>sort methods</b>.<br>
There are:
<ul class="list">
  <li>sort</li>
  <li>sort!</li>
  <li>sort_by</li>
</ul>
First of them is <b>sort</b>. We have an example below:
<div class="code">
{% highlight ruby %}
my_array = [d, a, c, b]
my_array.sort
=> [a, b, c, d]
{% endhighlight %}
</div>
As you can see, after using this method we have a new array with numbers sorted from the smallest to the bigest. It is really easy! We can also use <b>combined comparison operator <=></b> which is used to compare two objects. It returns 0 if the first operand equals the second, 1 if the first operand is greater than the second, and -1 if the first operand is less than the second. We can use it to sort values in descending order:
<div class="code">
{% highlight ruby %}
my_array = [d, a, c, b]
my_array.sort { |a, b| b <=> a } 
=> [d, c, b, a]
{% endhighlight %}
</div>
We can also use <b>sort!</b> which won't make new array but change the old one, which can be good for efficiency.<br>
The last method is <b>sort_by</b> which is the most advanced from all of them, because you can choose by which key you will sort. Here we have an example:
<div class="code">
{% highlight ruby %}
new_array = ["bb", "ccc", "a", "dddd"]
new_array.sort_by{ |word| word.length }
=> ["a", "bb", "ccc", "dddd"]
{% endhighlight %}
</div>
You can also do the same thing in different way:
<div class="code"> 
{% highlight ruby %}
new_array = ["bb", "ccc", "a", "dddd"]
new_array.sort_by(&:length)
=> ["a", "bb", "ccc", "dddd"]
{% endhighlight %}
</div>
When you have tools like this, you can do a lot of things with sorting!
