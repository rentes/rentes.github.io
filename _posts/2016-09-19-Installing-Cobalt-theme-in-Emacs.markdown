---
layout: post
title: "Installing Cobalt theme in Emacs"
date: 2016-09-19 15:15:33
author: Miguel Rentes
comments: true
categories:
  - emacs
---

I am a big fan of discovering how other developers work and lately I have started watching the "Day in the Life" series on Youtube:

<div><iframe width="661" height="402" src="https://www.youtube.com/watch?v=vt79JcPfZQA" allowfullscreen=""></iframe></div>

On this excellent video, you can see at 00:45 the Cobalt theme in Sublime Text editor (I also use this editor at work):

<img src="/img/CobaltTheme.png" alt="Cobalt Theme in Sublime Text editor" title="Cobalt Theme in Sublime Text editor" width="750px"/>

Since I like a lot this theme and I also enjoy using Emacs, the logic step was to use this theme on Emacs as well. This theme is not installed by default on Emacs (btw <a href="https://lists.gnu.org/archive/html/emacs-devel/2016-09/msg00451.html">Emacs 25.1 is out!</a>) but you can install it quite easily. You have two options: install this theme and a group of other themes as a bundle by installing the package `color-theme-modern` from MELPA archive, or install just this theme.

To install the `color-theme-modern` package:

* Add the MELPA archive on your Emacs init file:

```
(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/"))
```

* Refresh the package archive contents:

```
M-x package-refresh-contents
```

* Search for the `color-theme-modern` package on the packages list and install it.
* Load the theme on your Emacs init file:

```
(load-theme 'cobalt t t)
(enable-theme 'cobalt)
```

* Save the Emacs init file and load it:

```
M-x eval-buffer
```

Now everytime you start Emacs, you will be using the Cobalt theme.

To install just the Cobalt theme:

* Add a diretory to where the theme will be download to. I use a directory named `themes` under my `~/.emacs.d/` directory.

```
mkdir ~/.emacs.d/themes
```

* Download the Cobalt theme .el file:

```
$ cd ~/.emacs.d/themes
$ curl -LO https://raw.githubusercontent.com/emacs-jp/replace-colorthemes/master/cobalt-theme.el
```

* Add the theme file to the Emacs custom themes load path, in the Emacs init file:

```
(add-to-list 'custom-theme-load-path
             (file-name-as-directory "~/.emacs.d/themes/"))
```

* Load the theme on your Emacs init file:

```
(load-theme 'cobalt t t)
(enable-theme 'cobalt)
```


* Finally, save the Emacs init file and load it:

```
M-x eval-buffer
```

Here is a screenshot of how the Cobalt theme looks like on Emacs:

<img src="/img/CobaltThemeEmacs.png" alt="Cobalt Theme in Emacs" title="Cobalt Theme in Emacs" width="750px"/>

<a href="https://github.com/emacs-jp/replace-colorthemes/blob/master/screenshots.md">Here</a> are the screenshots for all the themes on the `color-theme-modern` package.

Until next time, have an awesome coding fun!
