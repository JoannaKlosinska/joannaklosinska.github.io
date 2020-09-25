---
layout: post
title: "Deploying On Heroku"
date: 2020-09-10
categories: ruby
---
If you create your own application, there will be a day when you would like to deploy it to production. It is a very good idea when you do it before finish your work - I didn't make so many application yet, but I had situations thats my application worked good locally and then it had problems in production. Deploying early and often allows us to catch any problems early during our development cycle.<br>
I use <b>[Heroku][heroku]</b> - a platform which is built specifically for deploying Rails and other web applications. Heroku makes this process very easy, as long as your source code is under version control with Git.<br>
Heroku installation is also nothing difficult. First of all you have to of course sign up <b>[here]</b>. Next open a terminal on your computer and you can check firstly that your system has already the Heroku installed:
{% highlight ruby %}
$ heroku --version
{% endhighlight %}
This command will display current version number if heroku command-line interface is available, but usually it will be necessary to install the Heroku by hand.<br>
If you have macOS, you can use this command to installation:
{% highlight ruby %}
$ brew install heroku/brew/heroku
{% endhighlight %}
But you need to install <b>[Homebrew][homebrew]</b> first (it is also very easy and useful!).<br>
Next, log in with email address and password you used when signing up:
{% highlight ruby %}
$ heroku login
{% endhighlight %}
Now you just need to create a place on the Heroku servers for the sample app to live:
{% highlight ruby %}
$ heroku create
{% endhighlight %}
In the end deploy your code: 
{% highlight ruby %}
$ git push heroku master
{% endhighlight %}
Any time when you want to deploy changes in your application, use <b>git push heroku</b>. And that is all!



[heroku]: https://www.heroku.com/
[here]: https://signup.heroku.com/dc
[homebrew]: https://brew.sh/
