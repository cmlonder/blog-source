---
title: "Welcome Back Clean Code"
date: 2020-01-13T07:14:38+03:00
lastmod: 2020-01-13T07:14:38+03:00
keywords: ["clean code"]
description: "An article against misleading goodbye-clean-code article"
tags: ["clean code"]
categories: ["software principles"]
author: "cemal"
toc: true
---

I recently read an [article](https://overreacted.io/goodbye-clean-code/) from Dan Abramov who is the creator of Redux.
Even if I agree his article point:

> Don’t be a clean code zealot. Clean code is not a goal. It’s an attempt to make some sense out of the immense complexity of systems we’re dealing with. 

I don't agree how misleading his article title and how not descriptive his example. Because this kind of titles "Goodbye Clean Code"
gives power to another kind of zealots who hates some Software Principles or hates someone around him mentioning this kind of
principles. When you title your article like this, it is too easy being used as a power in social medias to be offensive against
software principles just by mentioning your article without any arguments to use with your own. Also think about how many people exist who
never know Clean Coding principles but using your article just as a weapon against it instead of his own experiences.
Rather I like the people who has deep knowledge of Clean Coding and Refactoring and can give some advice where to use them 
properly and giving me awareness of it (which is probably aim of this article but I find it misleading and insufficient)

Just for an idea, you can google "OOP sucks" or ironically "Goodbye Redux" to see
how zealots use this kind of titles where I both like OOP and Redux. 

Dan mentions 2 points to give you the awareness beside his title, lets have a look at them:

> Firstly, I didn’t talk to the person who wrote it. I rewrote the code and checked it in without their input. Even if it was an improvement (which I don’t believe anymore), this is a terrible way to go about it

I think this is the right way you should do when you are truly doing refactoring. You don't have to talk the person directly 
if you are doing refactoring, you should be in trust with unit tests. And if the code has a little indicators of clean coding
than you should have general idea why the code is structured like that or your team must have some documentations for exceptions.
What if the person who writes the line leaves the job? You still contact them personally? No, we don't. We make unit & integration tests,
properly structure our code with internally documenting (in our code) and finally we may have externally documentation for exceptional cases.

And Dan's second mention:

>  For example, we later needed many special cases and behaviors for different handles on different shapes

When I first read these lines, I say myself "finally I will see the point and understand what happened in above code, and
satisfied with his argument in title". It did not happen. He gave me lots of lines above which than I was expecting to see some evidence or
some real results. But instead I read something like "special cases" which does not give me the idea. 

* What special cases did he need? 
* What should we learn when we refactored like above? 
* Which points we should be more careful? 
* How did your "refactorings" are merged, any Pull Request? Who is the reviewer, where is the discussion, did your boss call only you? 

As I said before, I know his point. But title, arguments he show and how article is being mentioned in twitter, reddit and 
lots of other social medias is dangerous. If you trust that who uses this article has deep knowledge in software principles, 
software architectures etc. than we don't have any discussions here. When I start searching if there are some people thinking like me
than I see this [discussion](https://www.reddit.com/r/programming/comments/eng355/goodbye_clean_code/) on reddit and it 
pleased me that they exist. 

If Dan wants to say "Great power comes with great responsibility", I agree. But it is already mentioned by Stan Lee and can
be applied in any area of our live with example real life scenarios. If we know all this kind of principles, we should be careful when & where to apply them.
But to get this experience we should first read & get deep knowledge of them, make some mistake and learn from our mistakes. 
Otherwise it is too easy for people never read refactoring, clean coding, YAGNI, DRY etc. and only mentioning around this 
kind of articles as an excuse of not knowing this principles.