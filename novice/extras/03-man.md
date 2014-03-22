---
layout: lesson
root: ../..
title: Manual Pages
---
You can get help for any Unix command with the `man` (short for manual)
command.  For example, here is the command to look up information on `cp`:

~~~
$ man cp
~~~

The output displayed is
referred to as the "man page".

The man page will be displayed in the default file viewer 
on your system, 
usually `more`.
When you have finished reading you can return to the command prompt with
'q'.

The output of the man command is typically very complete, but concise, as it is
designed to be used as a reference. It does not provide tutorial-like
introductions to the Unix system. Man pages are divided into 
sections, which may include:

*   NAME - 
    gives the name of the command and a brief description
*   SYNOPSIS - 
    how to run the command, including optional and mandatory parameters.
    (We will explain the syntax later.)
*   DESCRIPTION -
    A fuller description based on the SYNOPSIS, 
    including a description of all the options to the command.
    This section may also include example usage
    or details about how the command works.
*   EXAMPLES -
    Some example usage.
*   SEE ALSO -
    Points out other commands that you might find useful or which complement the current command.
    Also points to alternative sources of information.

Man pages aren't very standardized, but other sections 
you might see include 
AUTHOR, REPORTING BUGS, COPYRIGHT, HISTORY, [known] BUGS, and COMPATIBILITY.

#### How to Read the Synopsis

Here is the is synopsis for the `cp` command:

<!-- 
FIXME: The following is not what I get when I run "man cp" -- I'm on Mac OS X
so I see the BSD General Commands Manual page. Can we assume that most of our
users will be on the same OS? If so the following section would require 
significant rewriting. Here's the SYNOPSIS I see:

 cp [-R [-H | -L | -P]] [-fi | -n] [-apvX] source_file target_file
 cp [-R [-H | -L | -P]] [-fi | -n] [-apvX] source_file ... target_directory
-->

~~~
SYNOPSIS
   cp [OPTION]... [-T] SOURCE DEST
   cp [OPTION]... SOURCE... DIRECTORY
   cp [OPTION]... -t DIRECTORY SOURCE...
~~~

This tells the reader that there are three ways to use the command. 
Let's look at the first usage:

~~~
cp [OPTION]... [-T] SOURCE DEST
~~~

`[OPTION]` means the `cp` command can followed by 
one or more optional options, or flags. 
We can tell they're optional because of the square brackets, and we can tell 
that one or more are welcome because of the ellipsis (...).
`[-T]` means you can use the options `-T` here if you
wish.  <!-- FIXME why is -T special? -->

`SOURCE` refers to the source file or directory, and `DEST` to the 
destination file or directory: the meaning of `SOURCE` and `DEST` 
are explained at the top of the `DESCRIPTION` section.

The other two usage examples can be read in similar ways. 
Note that to use the last one, the
`-t` option is mandatory. In fact, this option switches the order of arguments
so that the destination immediately follows it.
<!-- FIXME we need more explanation about -t -- this doesn't make sense. -->

The `DESCRIPTION` section starts with a few paragraphs explaining 
the command and its use, and then expands on all the possible options
one by one:

~~~
     The following options are available:

     -a    Same as -pPR options. Preserves structure and attributes of
           files but not directory structure.

     -f    If the destination file cannot be opened, remove it and create
           a new file, without prompting for confirmation regardless of
           its permissions.  (The -f option overrides any previous -n
           option.)

           The target file is not unlinked before the copy.  Thus, any
           existing access rights will be retained.

      ⋮          ⋮
~~~

#### Finding Help on Specific Options

If you want to skip ahead to the option you're interested in, you can 
search for it using the slash key (/).
For example, to find out about `-t`, 
you can type `/-t` followed by `RETURN`.
Using the `n` key, we can navigate to the _next_ match 
until we find the detailed information we need:

~~~
-t, --target-directory=DIRECTORY
     copy all SOURCE arguments into DIRECTORY
~~~

This means that this option has the short form `-t` and the long form
`--target-directory` and that it takes an argument. Its meaning is to copy all
the SOURCE arguments into DIRECTORY. Thus, we can give the destination
explicitly instead of relying on having to place the directory at the end.

<!-- FIXME 
I deleted the entire "man -k" section because it's insane to pick through the
results of man -k when you can just "unix command copy" or whatever you want to
do.
-->

#### Limitations of Man Pages

Man pages can be useful for a quick confirmation of how to run a command, 
but they are not always written for clarity or readability. 
If you can't find what you need in the man page&mdash;or you 
can't understand what you've found&mdash;try 
entering "unix command copy file" into your
favorite search engine; you will often find more user-friendly references
online.
