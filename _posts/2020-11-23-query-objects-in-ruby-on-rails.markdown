---
layout: post
title: "Query Objects In Ruby On Rails"
date: 2020-11-23
categories: ruby
---
First time, when I heard about the query object it was a moment, when I was looking at my code and thought: "well, it doesn't look good, it's time to refactor it". I had a very huge line of working code in one of my view files. It could look totally unreadable for someone who didn't work with me and also, after couple of weeks, when I would like to check something in my code, probably I wouldn't remember what happened here. So, what is it this query object? <br>
<b>Query object</b> in Ruby is a pattern which can be very helpful to keep our code short, simple and readable for others and for ourselves also. When you have a big ActiveRecord model, which is hard to understand and, what's more, exists in a wrong file - let's decompose it!<br>
What are the most important features of the query object?
- <p>makes your code simple for you and other developers</p>
- <p>you can test it easy in isolation</p>
- <p>you can use it in many files in your application</p>
- <p>you should use it when your code has too many methods in one line</p>

Query objects are usually located in <b>app/queries</b> directory, typical file name starts with <b>_query</b> and class name starts with <b>Query</b>. <br>
I will show you an example for my own application. <br>
I had a very long line of code in my view file. It looked ugly:
<div class="code">
{% highlight ruby %}
<%= f.select :coach_id,
Coach.joins(:schedule)
  .where("schedules.#{booking_datetime.strftime("%A").
        downcase} && ?", "{#{booking_datetime.hour}}")
  .where.not(
  id: Coach.joins(:bookings).
  where(bookings: { time: booking_datetime })
).collect { |c| [ c.name, c.id ] }, 
include_blank: true %>
{% endhighlight %}
</div>
It's very hard to understand, what's going on here, right? <br>
First of all, I decided which part of code can became a query object. Then I created a special file and named it <b>available_coaches_query.rb</b>. I saved this file in my special directory <b>services</b>, where I keep specially created classes. My query object looks like this:
<div class="code">
{% highlight ruby %}
class AvailableCoachesQuery
  def self.at(booking_datetime)
    Coach.joins(:schedule)
      .where("schedules.#{booking_datetime.strftime("%A").
            downcase} && ?", "{#{booking_datetime.hour}}")
      .where.not(
       id: Coach.joins(:bookings).
       where(bookings: { time: booking_datetime })
       )
  end
end
{% endhighlight %}
</div>
Final version of code in my view file looks like this:
<div class="code">
{% highlight ruby %}
<%= f.select :coach_id,
AvailableCoachesQuery.at(booking_datetime).
collect { |c| [ c.name, c.id ] },
include_blank: true %>
{% endhighlight %}
</div>
It's short, simple to read and pretty now.