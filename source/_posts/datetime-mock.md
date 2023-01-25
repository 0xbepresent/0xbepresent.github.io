---
title: How to mock the python datetime module
date: 2015-01-10
---

I've been working with some methods to test my code for the last months. Now, I'm going to talk about of how to mock the python datetime module. </br>

<a href="https://pypi.python.org/pypi/mock/">Mock is a library</a> which help us to change the behavior in a specific module or function. It means that if we need to change the result of a specific module, we can do it with mock library. </br>

Imagine, that you have a function which it use the "datetime.datetime.today()" and in the function you have to test a specific day, I mean, you can't move the time in your server or something like that, just for "datetime.datetime.today()" would return the value whatever you want. So, in that situation we can mock the datetime module. </br>

I did <a href="https://gist.github.com/0xbepresent/ba6e307cf709f153c6ba">a function</a> which you can use in your test. For example:

<img class="center" src="/images/mock_datetime.png"/>

We can see the fragment code that is in the 'with' section, the function datetime.datetime.today() will return a specific today (2014-1-1). </br>

You can use the <a href="https://gist.github.com/0xbepresent/ba6e307cf709f153c6ba">Github Gist</a> and of course, you can contribute on it!.
