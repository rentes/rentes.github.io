---
layout: post
title:  "Wisdom of the Ancients"
date:   2015-09-03 15:05:35
author: Miguel Rentes
comments: true
categories:
  - programming
  - stackoverflow
---

Recently, this happened to me:

![Wisdom of the Ancients](https://imgs.xkcd.com/comics/wisdom_of_the_ancients.png ""All long help threads should have a sticky globally-editable post at the top saying 'DEAR PEOPLE FROM THE FUTURE: Here's what we've figured out so far ...'")

More specifically, the problem occurred when running a simple X/Motif C application linked with the Motif library libXm and the X Toolkit Intrinsics library libXt:

```c
$ gcc -Wall -o push push.o -lXt -lXm
$ ./push
Error: No realize class procedure defined
```

This error led me (of course) to search the web for the cause, but all I could find was a thread of September 2009 on the fixunix forum:

<a href="http://fixunix.com/motif/93690-help-no-realize-class-procedure-defined.html#post308162" target="_blank"><img src="/img/fixUnixThread.png" alt="FixUnix thread" title="Click to open FixUnix thread" width="750px"/></a>

After performing several different experiments, I thought the problem could be the order in which the libraries were being passed to the gcc linker.
After reading a nicely detailed [stackoverflow thread on it][stackoverflow-gcc-link-libraries-order], I found the solution was pretty simple: I just had to switch the order of the libraries:

```c
$ gcc -Wall -o push push.o -lXm -lXt
```

and the problem was fixed.

I then went back to the fixunix forum to answer the thread so that my findings could (possibly) be of some use if someone else comes across this error.
But then I was a bit surprised to find that the forum was closed to new replies or new user registrations:

<img src="/img/fixUnixNoRegistration.png" alt="FixUnix Registration Disabled" title="FixUnix Registration Disabled" width="750px"/>

The alternative? Writing a post on stackoverflow of course! Here it is:

<a href="http://stackoverflow.com/questions/32373700/no-realize-class-procedure-defined/" target="_blank" alt="No realize class procedure defined stackoverflow thread" title="Click to open stackoverflow thread">No realize class procedure defined</a>

All in all, this error taught me two important lessons: always share your findings (even if they only occur years later, or if you have to submit the answer to another forum) and never close a forum to another's contribution! At least explore the possibility of migrating the threads contents to another platform where anyone can share their experiences and help each other.

Until next time, have a lot of coding fun!

[stackoverflow-gcc-link-libraries-order]: http://stackoverflow.com/questions/45135/why-does-the-order-in-which-libraries-are-linked-sometimes-cause-errors-in-gcc
