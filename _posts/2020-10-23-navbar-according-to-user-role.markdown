---
layout: post
title: "Navbar According To User Role"
date: 2020-10-23
categories: ruby
---
I am working on my own web application, which is a calendar for booking fitness trainings. There are two types of users - customers and coaches. I wanted that every kind of user has a different navbar and I was looking for a good solution. In this post I will show you how I solved this problem. I don't say that this is the best way to do it, but I hope that it will be helpful for you. <br>
I decided to use <b>content_for</b>. <br>
First of all, I wrote codes for two variations of navbar and saved it as partials. Next, in my <b>application.html.erb</b> file, I added a logic which checks if a specific navbar should be rendered:
<div class="code">
{% highlight ruby %}
<% if content_for?(:navbar) %>
  <%= yield(:navbar) %>
<% else %>
  # code for default navbar
<% end %>
{% endhighlight %}
</div>
Finally, inside every view, where I wanted a different navbar, I added in the first line of my code:
<div class="code">
{% highlight ruby %}
<% content_for :navbar do %>
  <%= render 'navbar_for_customers' %>
<% end %>
{% endhighlight %}
</div>
Of course, I had to do the same for my coaches views:
<div class="code">
{% highlight ruby %}
<% content_for :navbar do %>
  <%= render 'navbar_for_coaches' %>
<% end %>
{% endhighlight %}
</div>
It works exactly as I wanted!