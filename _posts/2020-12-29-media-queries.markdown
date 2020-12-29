---
layout: post
title: "Media Queries"
date: 2020-12-29
categories: css
---
This is my first post about different subject than programming in Ruby and Ruby On Rails. I spend my time on study miscellaneous technologies. One of them is learning how to use CSS to style my applications. I try to make them nice to use. Today I will write about how to make our websites to look good in every screen - on laptops, tablets or mobile phones. <br>
<b>Responsive web design</b> is about creating web pages look great on all devices. It is very important nowadays, because many people want to use applications or check websites not only on desktop, but increasingly do it only on their mobile phones. <br>
I used only CSS and HTML to style my own application. I decided to make it suitable for any device. <b>Media Queries</b> is very popular and simple way to make our site responsive. It uses the @media rule to include a block of CSS properties only if a certain condition is true. Here we have an example:
{% highlight ruby %}
// media queries //
@media only screen and (max-width: 320px) {
  h2 {
    font-size: 20px;
  }
}
{% endhighlight %}
In this short and simple code we can see, that font size in h2 tags will have 20px, only for screens with max-width to 320px. 
In my file <b>dashboards.scss</b>, where I have all CSS code, I added media queries for every screen size and change things, which didn't look good on smaller or bigger devices. Of course, I didn't have to change everything, but I, for example, overwrited navbar or font size. Very helpful was [this site][this_site] where you can find a list of many different devices and media queries that would specifically target that device. <br>
I also used a <b>Safari</b> browser to check, how my application looks on smaller and bigger screens. You can find this tool in toolbar, when you click on <b>Develop</b> and then <b>Enter Responsive Design Mode</b>. What's more, I opened my application on different browsers (in my case it was Safari, Google Chrome and Firefox). I really recommend it, because after that I saw, that there are things, which look a little different on these browsers and I changed them to look the same or very similar. <br>
There are two groups of developers - first of them says that the best practice is firstly create CSS for smaller devices and then write media queries for bigger screens. The second group says, of course, that the opposite way is the best one. In my application I firstly created CSS for bigger screen, but maybe I will try another method next time.

[this_site]: https://css-tricks.com/snippets/css/media-queries-for-standard-devices/