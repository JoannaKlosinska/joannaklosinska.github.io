---
layout: post
title: "Forms In Ruby On Rails"
date: 2020-11-17
categories: ruby
---
We can see a lot of type of forms in many web applications. Registration forms, search forms, select forms... Of course Ruby also gives us these tools. Web developers should know about every differences between methods to use them properly in their applications. <br>
Let's start from the very begging. <br>
Form methods translate to the HTML that creates all fields in a form. The most generic is <b>form_tag</b>. The syntax looks like this:
<div class="code">
{% highlight ruby %}
<% form_tag do %>
  Content
<% end %>
{% endhighlight %}
</div>
Without any arguments this creates a form tag element, which submitted, will POST to the current page. <br>
You can use <b>form_tag</b> to make a simple search form, which should looks like:
<div class="code">
{% highlight ruby %}
<%= form_tag(search_path, :method => "get") do %>
   <%= label_tag(:q, "Search for:") %>
  <%= text_field_tag(:q) %>
  <%= submit_tag("Search") %>
<% end %>
{% endhighlight %}
</div>
Next I am going to tell about <b>form_for</b>. It is designed to editing model attributes - allows user to create or update the attributes of a specific model object. It has some arguments, first of them is a model. Here you have a simple sign in form from my own application:
<div class="code">
{% highlight ruby %}
<%= form_for(resource, as: resource_name, url: registration_path(resource_name)) do |f| %>
  <%= f.label :name %>
 <%= f.text_field :name, autofocus: true %>

  <%= f.label :email %>
 <%= f.email_field :email, autofocus: true, autocomplete: "email" %>

  <%= f.label :password %>
 <%= f.password_field :password, autocomplete: "current-password" %>

 <%= f.button "Sign up", type: 'submit' %>
<% end %>
{% endhighlight %}
</div>
In some codes we can see a notation <b>remote: true</b> added in the first line:
<div class="code">
{% highlight ruby %}
<%= form_for(resource, as: resource_name, remote: true, 
    url: registration_path(resource_name)) do |f| %>
{% endhighlight %}
</div>
This means that code uses <b>Ajax</b> - a browser technology which allows to send changes that you make in a form without reload the full page. <br>
Very similar to form_for is <b>form_with</b>, both of them working in the same way. This type of form has notation "remote :true" by default. Here we can see a simple syntax of this form (example from Apidock):
<div class="code">
{% highlight ruby %}
<%= form_with model: @post do |form| %>
  ...
<% end %>
{% endhighlight %}
</div>
And this is equivalent to:
<div class="code">
{% highlight ruby %}
<%= form_with scope: :post, url: post_path(@post), method: :patch do |form| %>
  ...
<% end %>
{% endhighlight %}
</div>
When you use the same forms in different pages in your application, a good practice is creating a partial for a default form, which we can save for example in file <b>_form.html.erb</b> in our views directory. This can save many lines in our code and make it more readable. <br>
I didn't write here everything about forms in Ruby on Rails. I recommend you to write more about it. Remember that the best places from you can get information, are official documentation or sites like [Apidock] or [RailsGuides].

[Apidock]: https://apidock.com/rails
[RailsGuides]: https://guides.rubyonrails.org/
