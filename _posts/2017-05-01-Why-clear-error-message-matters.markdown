---
layout: post
title: "Why a clear error message matters"
date: 2017-05-02 00:09:40
author: Miguel Rentes
comments: true
categories: software
---

Last month I was getting an error while uploading several files to a Linux server at work. 

<img src="/img/FilezillaUploadWrongError.png" alt="Filezilla Upload Error Window" title="Filezilla Upload Error Window" width="750px"/>

For some reason, the upload was always stopping at the same byte count. Not only that but the error message was saying that the upload failed but the next line stated it was successful. This is confusing to the end user in my opinion. Apart from that, the error message didn't say much else.

I was thinking of a few causes for this error, namely:

1) a filesystem limit was set that prevented uploads greater in size than the zip file I was trying to upload (~ 4GiB);<br/>
2) a bug in my FTP client (FileZilla)... this seemed to me really far-fetched, but it could happen;<br/>
3) a network problem seemed the natural cause;<br/>
4) a user disk quota exceeded on the Linux server;<br/>
5) a control group configuration limiting disk I/O resources on the Linux server.<br/>

The next thing I did was to divide my zip file into smaller ones (700MiB each) to check if my first hypothesis was correct.

<img src="/img/FilezillaUploadError.png" alt="Filezilla Upload Error Window with smaller zip files" title="Filezilla Upload Error Window with smaller zip files" width="750px"/>

Hum... no luck FTP'ing all zip files to the Linux server. At this point I tried option number 2), downloaded WinSCP (I was working from a Windows machine) and tried again.

<img src="/img/WinSCPUploadErrorMessage.png" alt="WinSCP Upload Error Window" title="WinSCP Upload Error Window" width="750px"/>

No luck again, but this time the error message was clear and to me a lot better, because:

* it states there is an error (and doesn't say the upload was successful at the next line);
* it lists several possible causes for the problem I was facing.

And there it was: after reading the possible causes I first checked if the ```/var``` partition was full because it seemed the most probable error cause, and indeed it was. Problem solved!

<img src="/img/BatmanRobinMeme.jpg" alt="The real cause of a problem is not always the obvious one" title="The real cause of a problem is not always the obvious one" width="750px"/>

This simple error message saved me precious work time, and it showed me how important a clear error message can be (and even better if it contains a list of possible error causes). Sometimes the "natural cause" is not the real cause for a problem, and if we have a great error message to help us out, we can avoid wasting a lot of time. Always code your error messages to provide this kind of feedback to your end users, as it is better to loose 5 minutes coding a good error message then having your end user wasting half an hour (or even more time) trying to figure out what is wrong.

Until next time, have an awesome coding fun!