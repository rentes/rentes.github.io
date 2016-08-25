---
layout: post
title: "Editing remote files with Emacs under Windows"
date: 2016-08-25 19:11:35
author: Miguel Rentes
comments: true
categories:
  - emacs
  - windows
  - ssh
---

Recently I had the need to edit remote files under Windows 10, and I used one of my favourite editors, which is emacs. In order to accomplish this, I only had to include these lines on the emacs init.el configuration file:

```
(require 'tramp)
(set-default 'tramp-auto-save-directory "C:\\Users\\<username>\\AppData\\Local\\Temp")
(set-default 'tramp-default-method "plink")
```

Replace `<username>` with your Windows user.

Don't forget to check that the environmet variable `%Path%` contains the folder where plink.exe is.

After reloading the init.el configuration file using the command:

```
M-x load-file
```

then pressing return twice to accept the default filename, I could now edit remote files using the command to open a file:

```
C-x C-f
```

and specify the connection string:

```
/<remote username>@<remote host>:
```

then pressing return and entering the remote username password. _Et voilá!_ 

Until next time, have a lot of coding fun!
