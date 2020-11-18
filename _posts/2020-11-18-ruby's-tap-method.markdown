---
layout: post
title: "Ruby's Tap Method"
date: 2020-11-18
categories: ruby
---
For the first time I saw <b>the tap method</b> when I was doing Rspec exercises from [Upcase] (by the way, I really recommend this site, there are a lot of useful courses). I saw there this code snippet:
{% highlight ruby %}
def stub_invalid_person
  Person.new.tap do |person|
    allow(Person).to receive(:new).and_return person
    allow(person).to receive(:save).and_return(false)
  end	      
end
{% endhighlight %}
I felt confused, so I started to looking for information about it. On [Apidock] we can find explanation that this method "Yields <code>x</code> to the block, and then returns <code>x</code>. The primary purpose of this method is to "tap into" a method chain, in order to perform operations on intermediate results within the chain." We can also see code like this:
{% highlight ruby %}
(1..10).tap { |x| puts "original: #{x.inspect}" }.to_a.
  tap     { |x| puts "array: #{x.inspect}" }.
  select  { |x| x%2 == 0 }.
  tap    { |x| puts "evens: #{x.inspect}" }.
  map   { |x| x*x }.
  tap    { |x| puts "squares: #{x.inspect}" }
{% endhighlight %}
The tap method can be used this way:
{% highlight ruby %}
user = User.new.tap do |u|
  u.username = "Joanna"
  u.save!
end
{% endhighlight %}
To replace this code:
{% highlight ruby %}
user = User.new
user.username = "Joanna"
user.save!
{% endhighlight %}
The tap method was created for tapping into method chains. In codes above we can't see that this method allows us to save code lines, but in more expanded codes, it can be really helpful and makes our work more readable.<br>
I also read that the tap method can help with debugging - it is logic for me, because I can imagine how difficult is debug long, chained methods.<br>
In many blogs and forums you can read about Ruby's tap method. I saw that there are developers who really like to use it and also there are developers who think, that it's unnecessary. For me at this moment it's hard to say what I think about it - I need to work longer with this method. Of course it's good to know, that method like this exists and every time, when I will see it in other developers codes, I will know what is going on. 

[Apidock]: https://apidock.com/rails
[Upcase]: https://thoughtbot.com/upcase/