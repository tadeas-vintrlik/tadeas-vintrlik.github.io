---
date: '2025-07-30T20:29:55+02:00'
draft: true
title: 'Why should I learn awk?'
---

## Why awk?

This is a first article in my series on the awk language. I had decided to write this because I feel the language is quite unkown or underrated considering it's usefulnes. In my opinion it is one of the best things to come out of *UNIX* and is essentialy omnipresent and yet underutilised. It is essentisentially a very advanced text filter (like *grep* or *sed*) and therefore integrates perfectly with the usual *UNIX* workflow. I personally believe the lack of knowledge of *awk* is why people say that *bash* scripting is not good for data processing. While for more advanced tasks *Python*, *R* or other are certainly a better choice; for simple, especially ad-hoc data processing *awk* is invaluable.

Did I get your attention? Ready to learn you some *awk*? Good, let's get started.

### Things might get AWKward

The only drawback I see with awk is the ammount of different implementations. You will most likely encouter the original POSIX implementation by the brilliant Brian Kernighan. If you are on GNU/Linux it is quite likely that you will have GNU awk or gawk for short (which is most likely symlinked to awk). Other implementations such as mawk exist. In this article I will be using the original POSIX implementation but I might sometimes mention differences in the GNU version, they are mostly compatible but it adds some quality of life improvements.

### Do I have awk installed?

Most likely if you are on GNU/Linux or MacOS, you can try the following:

```bash
$ awk --version
awk version 20200816
```

You might seem more something along these lines:

```
$ awk --version
GNU Awk 5.1.0, API: 3.0 (GNU MPFR 4.1.0, GNU MP 6.2.1)
Copyright (C) 1989, 1991-2020 Free Software Foundation.
```

## What makes awk great (for file processing)

I would say that for me the most defining features of the language is it's design when it comes to line processing. The entire language was designed as a domain specific language for this very purpose.
There is no need to use looping constructs to iterate lines. That logic is baked into the syntax and makes sequential line processing absolutely trivial. Let's see on the following example.


## Our first awk command

You can also write awk scripts directly you will invoke it quite often directly from your shell or as a powerfull tool inside a shell script.

```bash
$ awk '{ print }' /etc/passwd
nobody:*:-2:-2:Unprivileged User:/var/empty:/usr/bin/false
root:*:0:0:System Administrator:/var/root:/bin/sh
daemon:*:1:1:System Services:/var/root:/usr/bin/false
```

So how does this work?

You invoke awk with two arguments.
1. The programme to execute
2. The input file (`/etc/passwd` the *UNIX* standard file with user details in our case)


I generally recommend using single quote for the programme since string literals must always use double quotes in awk.

Now let's look on the programme in more detail. The entire body of the programme is a single action statement. This action statement will be evaluated on every line and print it's entire contents.

An awk programme is essentially a sequence of pattern-action statements. This take on the following form  ``pattern { action }``. For each line where the pattern is found action will be executed. Our first programme is just a single pattern-action statement with an empty pattern (so it maches all lines). If we want to we can filter out just the daemon user:

```bash
$ awk '/daemon/{ print }' /etc/passwd
daemon:*:1:1:System Services:/var/root:/usr/bin/false
```

This searches the line for an occurence of the word `daemon`.

Awk essentially splits the entire file into records (lines) and fields. You can imagine it like the following:

```bash
Field1 Field2 Field3 # Record1
Field1 Field2 Field3 # Record2
Field1 Field2 Field3 # Record3
```

That make it very good for working with table-like content such as TSV (tab-seperated), CSV (comma-separated), docker and kubernetes output (more on that later).
By default it would separate the files by whitespace (spaces and tabs). It actually uses the IFS (Interal Field Sepeator) environment variable.

But you might notice that the /etc/passwd file is not seperated by whitespace but colons instead. We can also redefine it by using the `-F` argument to awk.
So what if want to print the user's default shell? That is the 7th field. You can specify just that by doing the following:

```bash
$ awk -F ":" '/daemon/{ print $7 }' /etc/passwd
/usr/bin/false
```

Quite neat isn't it? Let me show you one more thing before we continue.
There are two special pattern in awk `BEGIN` and `END`. These have special meaning and are executed only once before and after processing all of the record respectively.
This can be useful to print headers, footers, set variables and output summaries.

Now what if we wanted to output multiple fields? Let's say the shell and the home directory:

```bash
$ awk -F ":" '/daemon/{ print $6, $7 }' /etc/passwd
/var/root /usr/bin/false
```

Now that works quite nicelly with one small expection. It is space seperated while the original was colon separated. Why is that?
Awk actually uses the `OFS` or **O**utput **F**ield **S**eparator variable to determine what to print between records. We can of course modify it and this is where the special patterns come in handy:

```
$ awk -F ":" 'BEGIN{OFS=":"} /daemon/{ print $6, $7 }' /etc/passwd
/var/root:/usr/bin/false
```

I will split this onto multiple lines so it is easier to read:

```bash
$ awk -F ":" '
BEGIN{OFS=":"}
/daemon/{ print $6, $7 }
' /etc/passwd
/var/root:/usr/bin/false
```

Now we have two pattern-match statements. One `BEGIN` which as we know has a special meaning is executed once before processing all the lines. It sets the value of OFS to colon to match the input.
You could also do `BEGIN{OFS=FS}` instead. Please note the difference the `IFS` environment variable and `FS` awk variable. Instead of using the `-F` parameter you might also set the `FS` in the `BEGIN`:

```bash
$ awk '
BEGIN{FS=":"; OFS=FS}
/daemon/{ print $6, $7 }
' /etc/passwd
/var/root:/usr/bin/false
```

Please notice that the two action statements are separated by a semicolon. First you set Field Separator to equal ":" and the you set Output Field Separator to equal the value of Field Separator.

TODO: Example with summing values in CSV. 
TODO: Maybe the title is not right?
