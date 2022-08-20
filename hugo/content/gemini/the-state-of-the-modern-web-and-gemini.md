---
title: "The State of the Modern Web and Gemini"
date: 2021-02-14T14:13:27+02:00
---
As you might have notice from just about anything on my website.  I like to
keeps things simple, maybe too simple. But it has a set of advantages. As
stated my [first ever post](/gemini/new-site-new-age.md).

This goes only into technical advantages of such an approach, but of course
there are more things to consider here.

Have you ever been searching for a quick answer to your question only to open
a random site and mindlessly agree to their cookies policy? Let's face it, who 
has not. I myself try to pay at least some attention to it and click off things 
I can. However the way these things are designed is to make it as hard as can
be. Just the other day I stumbled across one where I had to manually tick off
around a few dozen companies if I did not want my cookies shared with them of
course including the major 'villains' - Facebook, Google and Amazon.

It is becoming ever increasingly difficult to browse the Web without being
constantly tracked at every step. Sites being larger than entire programmes I
use Loading CSS and JavaScript from questionable third-party sites and much
more.

## Where Gemini Comes in

The last two weeks it seems that almost every Linux video creator seems to have
talked about it to some extent. But in case you are still unsure here's a
summary:

It's a simple protocol for transfer of files mostly centred around small
inter-linked text files. It tries to be the middle-ground between Gopher and 
the Modern Web. If you don't know anything about Gopher do not worry Gemini is
much closer to it than the Web so as I will explain Gemini in more detail I'm
sure you will understand.

### What Is it For?

If you want more information you can find the on the project's [official site](https://gemini.circumlunar.space/)
(both on HTTP and gemini)

It can handle very simple text sites (called capsules) that can do some basic
text formatting based no Markdown. Three levels of headers, bullet point lists,
quotes and formatted block (code-blocks). It can also link to other files and
that is all.  Wait that is it? No images, no tables, nothing? Indeed. It was
designed with very deep minimalism in mind and so that both clients and servers
are very simple pieces of software capable of being written over the weekend by
one person.

But as you can see it is just perfect for a site like mine. Just lightly
formatted text and not much besides that. If you want to you can put links to
images on there which will be opened in your default image viewer, so this way
it is much UNIXier than modern browser which essentially act like document
readers, image viewers, video players and so on. Now for video while
technically being possible to be downloaded via Gemini it will likely not be a
pleasant experience since it does not support any form of caching and so if
your connection is slow and especially unstable it will not work very well.

It is also possible to do some scripting. But it only supports server side
scripting. So nothing runs in your browser, only on the server side. This means
no cookies, no fingerprinting and so on.

This however poses certain limitations such as no Shopping carts, no...
(I tried really hard but could no come up with any other good reasons). So it 
will never become a true replacement for the Web and neither does it try to!
It's just a way for people who want to share simple but important information
in more reasonable ways.

Last but definitely not least the protocol enforces TLS on all requests, so it
quite secure and will stay this way since it does not leave much space for
future changes. This is of course a double-edged weapon since it means that
there is not way to address it's shortcomings but also it will stay the way it
is and will not simply become just as bad as the Web is.

## How Can I Get on the Gemini-space?

OK so you are sold on the idea of Gemini and want to give it a go. How can you
do that. You'll need a special client to do that. A list of them can be found
on the [Gemini project site](https://gemini.circumlunar.space/clients.html).

There are some graphical ones and some terminal ones to suit everyone's needs.
I can personally recommend Amfora for the terminal and Lagrange for the GUI.
You can also ssh into the gemini server and try the terminal ones there if you
do not want to install them yourself.

But what now? How do I find things? There are a few gemini search engines most
notably [geminispace](gemini://geminispace.info/search)

It can search among added capsules and there is also a list of all known
capsules. So you can browse to your heart's content.

## Can I Host My Own Capsule?

Sure you can and it is quite easy to do! The only thing you need is a gemini
server. There are a couple you can search one you like but let me give you a
few recommendations. Agate is a really simple one to set-up and I see most
people using it. It has a really nice GitHub README telling you everything 
you need to get it running in a few minutes. Gemini servers require very little 
resources unlike their HTTP counterparts so you can comfortably run it from a
Raspberry Pi for example. Of course if you want other's to visit your capsule 
you need a public IP address.

## My Personal Thoughts

It is quite refreshing seeing such a project get popular in the current year 
and I am quite hopeful of it's future. Now I do not expect non tech-savvy
people to start ever using but it's good knowing something like this is out
there for people who want to use it.

It reminds a bit of the older days of the web (not that I am that old).
But still even a decade back it was a completely different place and every site
you opened could be a potential hidden gem. People were hanging out on multiple
sites and the web was a lot less centralised. It can be quite fun just 
stumbling upon someone's personal site randomly.

You might have noticed that in this article I put each of the links on their
separate line and this is because this is the way Gemini does it. Since from
now on I will be bi-hosting this as a HTTP website as well as a [gemini capsule](gemini://vintrlik.org). (This link is now dead)

> Have a great day and keep computing fun.
