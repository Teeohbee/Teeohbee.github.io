---
layout: post
title: My First Ticket
---

```
As an ads ops
When I work with our sites
Then I would like to use the new GPT tags for serving ads
```

This was my first ticket. Such responsibility. Much cool. Many wow. So where to start?

A little googling and light reading later, I understood that Google were deprecating their previous ad library, the DART implementation, in favour of the newer Google Publisher Tag, or GPT library. This was a small javascript library that then allowed you to access and display google ads of various sizes on your site. The javascript and implementation looked fairly straight forward. Within the Head of your HTML, you load the library and instantiate it, then define the various ad slots that are to appear on that particular page. Then in the body, you simply create a div element that holds a small script to load the specific ad for that location. To get this up and running on a small site in raw HTML / Javascript would have been perfectly simple.

Unfortunately, the key factor in determining the difficulty of actually making this change lies in line 2 of the user story, specifically the use of the plural - sites. I was not to be working on just one small site, directly in the HTML and Javascript, this was to be done on the CMS level. A CMS covering multiple sites. A CMS that itself included and relied upon multiple plugins and controls. A CMS that was written largely in C#... with just a little VB thrown in for good measure...

Welcome to web development!

My coding education and practice so far at this point had excluded one vital part of the puzzle of web development, coming to a large project that isn't your own and making changes. Through my experience working on this ticket, I've managed to break down my approach into 4 steps:

1. Understand What It Does
2. Break It
3. Fix It
4. Start Making Changes (Slowly)

1. Understand What It Does
This was probably the hardest step for me. It felt a little like gazing up at a gargantuan oppressive skyscraper, before stepping inside to find a maze of corridors and rooms with little direction. Where to even begin?

Part of the answer it turned out was sat next to me, a colleague with far more experience with the current codebase than me. They were fortunately willing to be my guide, and saved me a lot of blank staring at functions that might not have beared any significance to the task at hand. I feel this should be the first step of any programmer interacting with someone else's work - grab the author, or at least someone who knows more about it than you. This can help immensely in breaking down a large codebase and quickly helping you focus on the code you're interested in.

The next step was more granular, with the help of my colleage I'd honed in on the area of interest. I'd seen function names and variables that I recognised but still wasn't entirely sure how it all fit together. Now you need to debug. Set a few break points on areas you think are interesting, build, run and see what happens. Stepping through the code as it's running is invaluable in determining what calls on what, mapping dependencies and generally putting back together the puzzle pieces to form a picture of what you're dealing with.

2. Break It
So you've stepped through the code, seen the processes firing off and got a map of how it all works in your head? No, you don't. Unless the code is immensely simple, you'll never reach that level of code understanding enlightenment simply by reading through line by line and having a few debug run throughs.

To get to grips with a codebase, one must break it. To truly get to grips with a codebase, one must break it and understand why it broke.

The experience of having your program break because of something you've done, changed or added is an invaluable one
