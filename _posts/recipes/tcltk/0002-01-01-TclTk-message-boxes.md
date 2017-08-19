---
title: "Message boxes in R tcltk"
author: "james_and_philippe"
comments: yes
excerpt: Use Tk message boxes in R.
image:
  credit: null
  creditlink: null
  feature: banner-tcltk.png
  teaser: banner-tcltk.png
layout: post
modified: '2017-08-19'
section: Basic techniques
share: yes
tags:
- tcltk
- GUI
- programming
categories:
- recipes
- tcltk
---

The following code demonstrates a simple "Hello World" message box.


{% highlight r %}
library(tcltk2) # For themed message boxes; library(tcltk) is fine too here
res <- tkmessageBox(title = "Greetings from R TclTk",
  message = "Hello, world!", icon = "info", type = "ok")
{% endhighlight %}

![A Tk window]({{ site.images }}/recipes-tcltk/messagebox.png)

After pressing the `OK` button, we can check the return value of the message box function.


{% highlight r %}
res               # This is a Tcl variable
## <Tcl> ok
tclvalue(res)     # Get the value from a Tcl variable
## [1] "ok"
as.character(res) # It works also that way
## [1] "ok"
{% endhighlight %}

We notice that the window size for the message box is too small to display the full title in the title bar, and unfortunately message boxes are not resizable by default (whereas tktoplevel windows are resizable by default). A simple way to fix this (which is admittedly not very elegant), is to add spaces on the end of the message to make it at least as long as the title.


{% highlight r %}
res <- tkmessageBox(title = "Greetings from R TclTk",
  message = "Hello, world!                 ", icon = "info", type = "ok")
{% endhighlight %}

![A Tk window]({{ site.images }}/recipes-tcltk/messagebox2.png)

Of course, sometimes it is desirable to have other buttons and/or other icons in a message box. The following examples illustrate some typical choices of buttons and icons.


{% highlight r %}
tkmessageBox(message = "An error has occurred!", icon = "error", type = "ok")
{% endhighlight %}

![A Tk window]({{ site.images }}/recipes-tcltk/messagebox3.png)


{% highlight r %}
tkmessageBox(message = "This is a warning!", icon = "warning", type = "ok")
{% endhighlight %}

![A Tk window]({{ site.images }}/recipes-tcltk/messagebox4.png)


{% highlight r %}
tkmessageBox(message = "Do you want to save before quitting?",
    icon = "question", type = "yesnocancel", default = "yes")
{% endhighlight %}

![A Tk window]({{ site.images }}/recipes-tcltk/messagebox5.png)

