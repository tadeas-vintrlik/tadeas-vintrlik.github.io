---
title: "New Site New Age"
date: 2020-11-22T13:57:42+02:00
searchHidden: true
---
Today I had a bit of free time on my hands and I decided to revisit this crappy
site of mine. After a few busy weeks in school where nothing happened on this
site in the semi-broken state I left it was asking for a change.

The reason for changing the site, however goes much deeper as I yet again
jumped the boat from Emacs to Vim. The reason for that will require a post of
its own. However with this switch came a nuisance in editing this site. It was
centred around org-mode files which were exported to HTML. This was quite
simple and quick in Emacs. With Vim this would require a different approach.
While few org-mode plug-ins exist none of them even come near for my needs.

One of the first options that came to my mind were Markdown files, this seems
like the obvious choice since org files are a different style of mark-down
languages (unlike HTML, which is a mark-up language). For the time being I
decided to write the pages directly in HTML as it is negligibly less efficient
than org-mode was for me. The issue however comes with files which I do not 
edit by hand such as my watch-list file. I have a small script that detects 
last played episode and after finishing it will mark so in the file. This would
also deserve an entire post, you can expect this one quite soon!

## Keeping blogging simple

As you might know I quite dislike over-complicating, unnecessary GUI,
proprietary formats, libraries for the most basic of things and other vices of
modern day computing, it quite shows on this site honestly. So using some kind
of framework or what have you for writing a blog was of course out of the
question. I was certain there had to be an easy way. And sure enough I came up
with a really minimal solution using POSIX shell.

> This Script Destroys Soy!
```sh
date="`date +%F`.gmi"
filename="./blog/$date"
date_pretty="`LC_ALL=en_US.utf8 date +"%B %d %Y"`"
echo "Enter the title:" && read title
entry_template="# $date_pretty
=> ./blog.gmi Back

## $title

> Have a great day and keep computing fun.

=> gemini://vintrlik.org/cgi-bin/gemlikes/view?$date Comments

=> ./blog.gmi Back
"

# Include the link in the blog index
[ ! -f "./blog/$date" ] && awk -v date="$date" -v title="$title" '{
		if (NR==4) {
			print;
			printf "\n=> ./" date " " title "\n";
		} else {
		print;
	}
}' ./blog/index.gmi > /tmp/gemini && mv /tmp/gemini ./blog/index.gmi

[ ! -f "./blog/$date" ] && echo "$entry_template" > "$filename"
$EDITOR "./blog/$date"
```

EDIT: as of 7th July 2021 this script is now for gemini files as this site is
primarily Gemini based now

It creates a new HTML file with a template, that is named using today's date. A
link to this page will be appended to the index file in the blog root
directory. Yes, it's that simple. A few lines of a shell script. Now this is of
course only possible because I write the HTML by hand and know exactly what it
looks like, but this is exactly the advantage of a minimalist approach that I
like. If you want to use it yourself you might have to change a few things. I
did not make it as a drop-in solution. However it should not be too difficult.
I also have a slightly altered version for keeping a diary.

As you see there is absolutely no reason to over-complicate some things and
keeping it simple comes with many benefits some if which I haven't even touched
on.

> Have a great day and keep computing fun.
