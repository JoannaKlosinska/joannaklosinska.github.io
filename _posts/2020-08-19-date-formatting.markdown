---
layout: post
title:  "Date Formatting"
date:   2020-08-19
categories: ruby
---
I am working on application which will be a calendar for booking fitness trainings. I was looking for a method to help me write dates properly. In Ruby you can use <b>strftime</b> method which can show your date just as you like. It can format year, day, time etc. On <b>[APIdock]</b> you can find a lot of combinations of dates formatting. I will show you here only few of them, but you could see how simple and smart it is.<br>
Our sample date is 19.08.2020 and time is 9:07.

{% highlight ruby %}
b = Booking.new
b.time.strftime("%Y/%m/%d") 
{% endhighlight %}
Formats date to <b>2020/08/19</b>

{% highlight ruby %}
b = Booking.new
b.time.strftime("%d-%B-&Y")
{% endhighlight %}
Formats date to <b>19-August-2020</b>

{% highlight ruby %}
t = Time.new
t.strftime("%I:%M%p")
{% endhighlight %}
Formats time to <b>09:07AM</b>

[APIdock]: https://apidock.com/ruby/DateTime/strftime