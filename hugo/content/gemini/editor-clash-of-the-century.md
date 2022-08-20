---
title: "Editor Clash of the Century"
date: 2020-12-08T14:10:32+02:00
searchHidden: true
---
If you spend any amount of time in the computer science or as I prefer to call
it Hacker community (in the original meaning of the word) you likely have heard
of this feud old as the culture itself. Emacs vs Vi editors and their
descendants.

To make the terminology clear in the beginning from now if I use the term Emacs
I specifically refer to the GNU implementation of the Emacs editor as this is
the most widespread one today and the one I have most experience with. When I
say Vim it could refer to both Vim or Neovim (I personally use the latter).
With this out of the way let us get started. I doubt anyone clicking on this
article expected a clear answer which of the two is better. If you did I am
sorry to disappoint you. First I think it is important to explain my history
with the two.

## Choosing "The Editor for a Lifetime"

It might have been some two years ago at this point when I first heard about
vi. It was about the time I started to get into *nix systems more seriously
(although I had been using them for some three years before). I did the usual
ordeal of the inexperienced opening up vi only to realise I can not even type 
at all! After a quick read I realised I was dealing with a much more powerful 
tool than I imagined and quickly understood why all those people were telling
me to learn it and how it would increase my productivity. From this I of course
quickly discovered Vim which I was then using for about 3 months.  I was not
particularly efficient with it but it was certainly better than using all the
editors I had used prior (Geany was my editor of choice beforehand). It was of
course inevitable to encounter Emacs the more I learned and read about Vim.

At first I didn't really pay much attention to it as I had heard that editor
relies heavily on user configuration (and lots of it) and also I was not
interested in having Tetris (Among others) in my text editor. If you don't
believe go DuckDuck it yourself. Eventually however I got curious and wanted to
uncover the big unknown that was Emacs to me at the time and decided to give it
a go. It was at a time when I was not editing large quantities of text files 
and I like experimenting with bizarre things.

What greeted was antique looking white screen with no idea how to control it.
Unlike Vim however you could use your arrow keys to move around which made it a
little more friendly. That was until I realised what kind of keybindings (or
rather key chords in the case of Emacs) are used. C-x C-s if for saving a file 
for example where C stands for control and the dash means to hold the control
while pressing the other key. This one is relatively good compared to some
others like one of my favourites C-c C-x C-o (this stops the clock in an org
buffer). If you did not understand every other word in the last parentheses do
not worry I will explain all this later.

I gave my best to try Vanilla Emacs (Without many modifications) for as long as
I could. After about a week I got tired however and decided to try out one of
the Emacs distributions (yes it has entire distributions). The first one and
arguably most famous I stumbled open was Spacemacs. Maybe I was just unlucky or
ignorant but at the time Spacemacs had some weird bugs I found quite annoying
and most importantly had so many things on top of Emacs I could barely tell it 
was the same thing anymore. Not to give you the wrong impression about
Spacemacs it is the most widely used Emacs distribution and likely for good
reasons but it was not what I was after. Then I found Doom Emacs. The premise
is simple relatively minimal Emacs configuration made to be familiar for a Vim
user. This sounded like a good place to start

I really liked Doom Emacs. To be honest if anyone asks me how to get started
with Emacs this is the place I will direct him. After using it for a weeks
however and learning how the editor works I quickly started to realise
something. It came with vi-like keybindings (often called evil mode in Emacs)
which are of course very comfortable to use, however they were not how Emacs
was meant to be used and a lot resources and manuals (I personally consider
Emacs more of a manual for itself than a text editor, more on that later) were
made with the original bindings with mind. I however found great difficulty
using them due to my history of RSI from a relatively early age. I found a
great compromise in god-mode which are essentially Emacs bindings with the
modal take of vi. If you are in insert mode every letter you press will be
typed on your screen. If you are in command mode just pressing x s will be 
interpreted as C-x C-s. So problem solved? For now at least.

## How Emacs differs from Vim

Now a large part of this article was concerned about Emacs and I intend to
continue in this fashion since lately less and less people known about Emacs
and this will be a dive into Emacs for people familiar with Vim as I feel
somewhat experienced in both to compare the two (highly subjectively of
course!) The most important distinction to understand is this. Sometimes people
call Emacs an extensible text editor. I disagree, the text editor itself is an
extension. What on earth is it then?

### My Emacs has a lisp!

There is a quite large family of programming languages called Lisp. Have not
heard of it? I would not be that surprised. The first dialect (you could say
version) of Lisp was designed in the late 50s and still remains somewhat
relevant today. You might have heard of Clojure. Why I am talking about this?
Emacs is configured in a language called Emacs Lisp or Elisp for short. For
those who have absolutely no idea what Lisp looks like here is a short example
of a factorial function in Elisp:

```elisp
(defun factorial (x)
  (cond
   ((zerop x) 1)
   (t (* x (factorial (- x 1))))))
```

If this looks outlandish and bizarre to you and you are wondering why on Earth
there are so many closed parentheses at the end you are not alone. I was 
curious however and decided to give it a go. You might notice that the
definition is recursive and Lisp languages are quite famous for that. Most of
them are multi-paradigm with heavy focus on the functional and declarative
paradigms in particular. My very limited knowledge of Haskell was quite handy
I picked up on it quite fast. You might have notice I use a lot of parentheses
in my writing I wonder if Lisp played a role in that...

Now if you are sharp enough you might have thought to yourself: "Wait wasn't
the talking about configuring an editor and isn't that a factorial function,
just how much can you do with Elisp!?". Well as it turns out. Absolutely
anything. Not only is it Turing complete as it turns out it is quite powerful.
People have even written a web browser and Tetris (remember the first
paragraph?) using Elisp. You can even use a Window Manager in Emacs and boot
straight into Emacs! I even did that for a moment.

Around this time I got confident in Emacs enough to try and create my own
configuration from scratch. I however do not use Emacs anymore, why?

## Why I left Emacs

Emacs is a fine piece of software that is infinitely capable. It also has a
scope which I have not seen and likely will never see again. It tries to do way
too many things and it shows. It was quite some time ago it reached over a
million lines of code Elisp and quite a few in C as well (for core functions
which need be very fast and the Elisp interpreter). I dare say there are even
parts that people completely forgot about...  I decide to try and setup mpd
(music player daemon) for my music playback. In short it runs a daemon in a
background and you can connect to it with all kinds of clients. Naturally I
wanted to do it with Emacs since around this point I basically never left it
except for web browsing that required a very modern browser.

If I did not have to I did not like to download extensions And as it turns out
there already was an interface for interacting with MPD!  Great, right? Well
not quite. The interface was terrible (I still do not get how it works) it uses
completely different Genres then MPD and I could not figure how to play a 
single song not an entire album. Also it did not detect songs without metadata 
and the list goes on. I tried searching and all I could find were people
recommending other extensions that did the same thing but better. I decided not 
to give in to that quite yet and try to modify the source to fit my needs. 
After getting fed up after about two hours of trying to figure out how it works 
I was heavily frustrated.

I managed to get files that did not have any metadata to show up but that was
about it. I realised that not only is this piece of software absolutely
unusable. It is part of the base install! And God knows how many similar things
were in there without me (or perhaps anyone since quite a few were abandoned)
knowing.

While god-mode was certainly better it still was not quite the Vim level of
comfort and again started editing for a few hours a day and my RSI got
considerably worse. I decided I could not go with this any longer. I installed
Neovim after a friend of mine recommended it to me after learning about the
state of the Vim code base and it was pretty much a drop-in replacement.  Since
most of my editing lately is either C or Shell I do not have a need for a fancy
IDE and thus Vim seems like the right tool for the job and after all is that
not what it is all about? Does that mean I will never use Emacs again? I do not
know yet my work-flow has changed quite considerably after quitting Emacs.

After all I did almost everything in Emacs. Editing files, controlling
multimedia, reading and writing emails, IRC, and RSS. Most of these things I
replaced with simple terminal applications that do exactly what I want and very
little else. In the future I might end up having a much more complicated
language and build setup where I think Emacs would shine much more (Especially
if I end up writing Clojure since Emacs is hands down better for editing Lisp).
If you edit code I think Vim is the best tool you could ask for (Maybe I'm
mistaken? Prove me wrong if that is the case!). For people who do a lot of
typing that is not code perhaps Emacs could be a better choice.

## Org-mode

Do you seriously think I could write an article on Emacs without mentioning
org-mode at least once? You would be dead wrong. So what is org-mode? Or maybe
rather what even are modes? In Emacs you have buffers with major and minor
modes. You can only have one major mode at a time and multiple minor
modes. These change how Emacs behaves. An example of a major could be c-mode 
for editing C code, text-mode for plain text files and so on while a minor mode
might be a spell-checker for example. So what is org-mode? It is a mode of time
and task organisation but it can be used to write markdown documents as well. A
little confusing? It was to me at first as well. It is an insanely powerful
tool for managing your to-do lists.  Since Emacs can have integration of email 
and you can link an email and a link to a particular function in a file with a 
time where it is scheduled to be done. It can also track how much time you 
spent on a particular task and much more. And of course since it is in Emacs it
is extensible.

## The self-documenting editor

This is another title that Emacs holds and rightfully so. Every part of the
editor is documented some more some less. But this GNU we are talking about so
it almost has more documentation than code! This one of the good things that
Emacs taught me. To comment everything. Sometimes it would even highlight an
Elisp function definition if it did not have a documentation string but was
otherwise correct! Don't know what particular keybindings does? Just use the
describe-key function. Don't know what a particular function does? The
describe-function has you back! For every function you can lookup the
definition which is something that very much fits with the open source
philosophy of learning from work of others.

## The conclusion

Even though this post a lot longer that I initially planned I still feel as
though I haven't done the topic justice (and likely nobody never will). And
that is okay with me. I didn't go into writing this with that goal anyway, that 
would be quite naive. If you learned something I'm glad. If I got you curious
about Emacs? Great. I'm not trying to convert to anyone here. I think more
people should try it out however. I think we have forgotten just how powerful
classical editors are and people are so shocked by seeing Visual Soydio Code
having a feature Emacs has had since the early 90s. I think it is useful
understanding the different take on things that Emacs has and also seeing the
vital and first component of the GNU operating system in action. Have I
cemented your belief that Emacs is not for you? That is good as well.

> Have a great day and keep computing fun.
