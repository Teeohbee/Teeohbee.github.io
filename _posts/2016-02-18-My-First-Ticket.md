---
layout: post
title: My First Ticket
---

{% highlight %}
As an ads ops
When I work with our sites
Then I would like to use the new GPT tags for serving ads
{% endhighlight %}

This was my first ticket. Such responsibility. Much cool. Many wow. So where to start?

A little googling and light reading later, I understood that Google were deprecating their previous ad library, the DART implementation, in favour of the newer Google Publisher Tag, or GPT library. This was a small javascript library that then allowed you to access and display google ads of various sizes on your site. The javascript and implementation looked fairly straight forward. Within the Head of your HTML, you load the library and instantiate it, then define the various ad slots that are to appear on that particular page. Then in the body, you simply create a div element that holds a small script to load the specific ad for that location. To get this up and running on a small site in raw HTML / Javascript would have been perfectly simple.

Unfortunately, the key factor in determining the difficulty of actually making this change lies in line 2 of the user story, specifically the use of the plural - sites. I was not to be working on just one small site, directly in the HTML and Javascript, this was to be done on the CMS level. A CMS covering multiple sites. A CMS that itself included and relied upon multiple plugins and controls. A CMS that was written largely in C#... with just a little VB thrown in for good measure...

Welcome to web development!
