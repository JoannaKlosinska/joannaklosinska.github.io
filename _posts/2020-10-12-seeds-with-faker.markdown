---
layout: post
title: "Seeds With Faker"
date: 2020-10-12
categories: ruby
---
When you do your own application, it is good idea to make some sample users to show how they profiles look and work. You can, of course, sign up your own users by hand, but it takes time and also Ruby has solution which makes these users for us.<br>
First of all, we need to install special gem - [Faker][faker]. It is very clever tool which allows us to make sample users with semi-realistic names and email addresses. Of course Faker can generate a lot of types of data, not only users. It can makes for us movie titles, datetimes or quotes and all of it will look real. I will show you some examples below, so you could see in how many different ways it works and how easy it is.<br>
<b>Addresses:</b>
<div class="code">
{% highlight ruby %}
Faker::Address.city   #=> "Imogeneborough"
Faker::Address.street_address   #=> "282 Kevin Brook"
Faker::Address.zip_code   #=> "58517" or "23285-4905"
Faker::Address.full_address   #=> "282 Kevin Brook, Imogeneborough, CA 58517"
{% endhighlight %}
</div>
<b>Names:</b>
<div class="code">
{% highlight ruby %}
Faker::Name.name    #=> "Tyshawn Johns Sr."
Faker::Name.first_name    #=> "Kaci"
Faker::Name.female_first_name   #=> "Natasha"
Faker::Name.initials    #=> "NJM"
{% endhighlight %}
</div>
<b>Movies:</b>
<div class="code">
{% highlight ruby %}
Faker::Movie.title    #=> "The Lord of the Rings: The Two Towers"
Faker::Movie.quote    #=> "Bumble bee tuna"
{% endhighlight %}
</div>
Ordinarily, you would like to use Faker gem only in development environment, but when you work on an application, for example, only for yourself or to your portfolio, I think that you can use it on your production site as well.<br>
When we installed Faker gem, we can add a Ruby program to seed the database with sample users, for which Rails uses the standard file <b>db/seeds.rb</b>. Firstly, I will create a main sample user:
<div class="code">
{% highlight ruby %}
User.create!(name: "Sample User",
            email: "sampleuser@mail.org",
            passowrd: "password",
            password_confirmation: "password")
{% endhighlight %}
</div>
I need to say here, that in your own application your sample user could look different, because your sign up page could require different things, for example last name, country etc. This is only an example from my own application.<br>
After that, in the same file, I will add 30 sample users, using the Faker gem to generate data:
<div class="code">
{% highlight ruby %}
30.times do |n|
  name = Faker::Name.name
  email = "sample-#{n+1}@mail.org"
  password = "password"
  User.create!(name: name,
              email: email,
              password: password,
              password_confirmation: password)
  end
{% endhighlight %}
</div>
The last thing you need to do is reset the database and then invoke our code, which we wrote above:
<div class="code">
{% highlight ruby %}
$ rails db:migrate:reset
$ rails db:seed
{% endhighlight %}
</div>
That is all!



[faker]: https://github.com/faker-ruby/faker