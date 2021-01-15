---
layout: post
title: "Timecop Gem"
date: 2021-01-15
categories: ruby
---
I discovered the <b>timecop gem</b> when I was writting tests in capybara for my application. I wanted to test how booking trainings by customers works. I needed to have a one specific date. Timecop gem was a perfect solution! <br>
You can install this gem like others - just add a line 'gem "timepcop"' to your Gemfile and run command in terminal:
<div class="code">
{% highlight ruby %}
bundle install
{% endhighlight %}
</div>
I added this line only in the test group in my Gemfile. Timecop can "freeze" time at any date you want. You need to run timecop block at the beginning of your test and you have to remember to end this block at the right moment - otherwise your date will be freeze all the time and it can cause bugs in future. I will show you a pice of my code where I use this gem:
<div class="code">
{% highlight ruby %}
require 'rails_helper'

feature 'Booking' do
  fixtures(:customers, :coaches)

  scenario 'A user successfully book a training' do
    Timecop.freeze(Date.new(2021, 1, 11)) do
      Schedule.create(coach: Coach.first, monday: ['10'])

      sign_in('foo@bar.com')

      visit '/'

      .
      .
      .

    end
  end
end
{% endhighlight %}
</div>
As you can see it is very easy - I just chose January 11th, 2021 for my date and my scenario in my test happens in this specific day. You can use the timecop in different way, like this:
<div class="code">
{% highlight ruby %}
  before do
    Timecop.freeze((Date.new(2021, 1, 11))
  end

  after do
    Timecop.return
  end
{% endhighlight %}
</div>
But I don't recommend it. It takes more lines of code and you can simply forget to write "after do" block. <br>
You can read more about this gem [here]. Timecop has a bigger functionality, but to this moment I used it only in this one case. I think that I will work with this gem more in future and then I will try to use it in different ways.

[here]: https://github.com/travisjeffery/timecop