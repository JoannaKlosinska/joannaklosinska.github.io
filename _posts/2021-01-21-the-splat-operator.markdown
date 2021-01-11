---
layout: post
title: "The Splat Operator"
date: 2021-01-11
categories: ruby
---
In today post I will write about the splat operator. Ruby has two splat operators - the single splat and the double splat. I will start with the single splat (*). <br>
First of all let's think in which situation we can use it. It is very useful, when we don't want to specify how many arguments passed to a method. Look at the example below:
<div class="code">
{% highlight ruby %}
def do_something(*arg)
  arg.each { |x| puts x }
end

do_something(1, 2, 3)
=> 1
=> 2
=> 3
{% endhighlight %}
</div>
Secondly, a parameter with the splat operator takes only these arguments for which there where no other parameters. We can see how it works in the example below:
<div class="code">
{% highlight ruby %}
def new_method(first_arg, *other_args)
  puts "This is #{first_arg}."
  puts other_args
end

new_method("first arg", "second arg", "third arg")
=> This is first arg.
=> second arg
=> third arg
{% endhighlight %}
</div>
One method can't have two parameters with the splat operator - this situation always produces an error. A parameter with the splat operator is optional, so if we don't give any arguments to a method, everything will work without any problems. Usually developers put splatted arguments at the end of the argument list, but it's not a requirement - you can put them anywhere in this list. <br>
It's time to write about double splat operator (**). It's similar to single splat, but it takes key/values pairs as arguments. Check the example:
<div class="code">
{% highlight ruby %}
def do_something_else(**args)
  args.each { |key, value| puts value }
end

do_something_else('a': 1, 'b': 2, 'c': 3)
=> 1
=> 2
=> 3
{% endhighlight %}
</div>
If we try to write, for example, string as an argument, we will get an error. As we can see, double splat is similar to a hash - the biggest difference is that double splat is optional, so if we don't give any arguments, it not produces any errors (the same like single splat). Double splat has to be the last element in argument list, in other case it gives us an error (opposite than single splat).