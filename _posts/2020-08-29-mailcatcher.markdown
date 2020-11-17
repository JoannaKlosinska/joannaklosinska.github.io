---
layout: post
title: "MailCatcher"
date: 2020-08-29
categories: ruby
---
When you have an application where users can sign up, it is good to have a mailer which sends confirmation email for new users. In this post I will write you about a tool which can catch all of our emails and display it in a web interface. This is a [MailCatcher][mailcatcher], which runs a very simple SMTP server. Thanks to this we can check any of our email when we work locally.<br>
Installation process is also very easy. In my opinion this is a good idea to have a tool like this, because it really helps us to test our email sending system.

[mailcatcher]: https://mailcatcher.me/