Coding Challenge #43 - tr
This week’s challenge is to build your own version of the Unix command line tool tr!
John Crickett
Dec 30, 2023

The Unix command line tools are a great metaphor for good software engineering and they follow the Unix Philosophies of:

    Writing simple parts connected by clean interfaces - each tool does just one thing and provides a simple CLI that handles text input from either files or file streams.

    Design for simplicity; add complexity only where you must.

    Design programs to be connected to other programs - each tool can be easily connected to other tools to create incredibly powerful compositions.

You can read more about the Unix Philosophy on the Coding Challenges blog.

Following these philosophies has made the simple Unix command line tools some of the most widely used software engineering tools - allowing us to create very complex text data processing pipelines from simple command line tools. There’s even a Coursera course on Data Engineering with Bash!

New Year Deal: 20% Off All Courses

To celebrate the new year I’m offering 20% off all my courses from now until midnight (GMT) January 7th 2024. Use the code NEWYEAR2024 to claim the discount when purchasing:

    Build Your Own Redis (Python)

    Build Your Own Shell (Go)

You can also get 20% off an annual subscription to the Coding Challenges newsletter - paid subscribers get 20% off all my courses at any time.
The Challenge - Building tr

The functional requirements for tr are concisely described by it’s man page - give it a go in your local terminal now:

% man tr

NAME
     tr – translate characters

SYNOPSIS
     tr [-Ccsu] string1 string2
     tr [-Ccu] -d string1
     tr [-Ccu] -s string1
     tr [-Ccu] -ds string1 string2

DESCRIPTION
     The tr utility copies the standard input to the standard output with
     substitution or deletion of selected characters.

The TL/DR version is tr swaps, squeezes or deletes characters.
Step Zero

In this introductory step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that please use curl to do the following:

% curl https://www.gutenberg.org/cache/epub/132/pg132.txt -o test.txt

Step 1

In this step your goal is to support translating from one character to another, when reading from the standard input. For this your program should start up and wait for a line of input from the user. It will then output the line having made the substitution specified, for example:

% cctr c C
coding challenges
Coding Challenges

Type CTRL-D to send the EOF and terminate cctr.

Step 2

In this step your goal is to support translation of a range of characters. As is common ranges are specified by the start and end separated by a hyphen. For example the upper case letters are A-Z and the lower case letters a-z. When you’ve implemented this it should look something like this:

% head -n3 test.txt
The Project Gutenberg eBook of The Art of War

This ebook is for the use of anyone anywhere in the United States and

% head -n3 test.txt | cctr A-Z a-z
the project gutenberg ebook of the art of war

this ebook is for the use of anyone anywhere in the united states and

Where we can see the first three lines as published by Project Gutenberg, then the same translated to lowercase in the second example.

Step 3

There is another way to specify the translation we just did:

% head -n3 test.txt | cctr "[:upper:]" "[:lower:]"
the project gutenberg ebook of the art of war

this ebook is for the use of anyone anywhere in the united states and

In this step your goal is to support the [:class:] specifier as shown above. You can find the full list of classes in the man entry, I’d suggest at least supporting the following:

[:class:]  Represents all characters belonging to the defined character
                class.  Class names are:

                alnum        <alphanumeric characters>
                alpha        <alphabetic characters>
                blank        <whitespace characters>
                cntrl        <control characters>
                digit        <numeric characters>
                lower        <lower-case alphabetic characters>
                print        <printable characters>
                punct        <punctuation characters>
                rune         <valid characters>
                space        <space characters>
                special      <special characters>
                upper        <upper-case characters>

Step 4

In this step your goal is to support deleting characters with the -d option. From the man page we get:

tr [-Ccu] -d string1

-d      Delete characters in string1 from the input.

So once implemented you should be able to do:

% head -n3 test.txt | cctr -d War
The Poject Gutenbeg eBook of The At of

This ebook is fo the use of nyone nywhee in the United Sttes nd

Notice all instances of the characters W, a and r have been removed. Don’t forget to support the classes too, for example:

% head -n3 test.txt | cctr -d "[:upper:]"
he roject utenberg eook of he rt of ar

his ebook is for the use of anyone anywhere in the nited tates and

Step 5

In this step your goal is to support squashing characters with the -s option. From the man page we get:

tr [-Ccu] -s string1

-s      Squeeze multiple occurrences of the characters listed in the last
        operand (either string1 or string2) in the input into a single
        instance of the character.  This occurs after all deletion and
        translation is completed.

When used that looks like this:

% cctr -s AB
AAABBBCCC
ABCCC

Or using the classes and out test file:

% head -n10 test.txt | cctr -ds "[:alnum:]" "[:space:]"

. , -

 ... ,

 .

Step 6

In this step your goal is ensure your solution scales, check that it can handle a large amount of input. you can do that like this:

% seq 1 3000 | xargs -Inone cat test.txt | tr "[:upper:]" "[:lower:]" > result.txt

Going Further

If you want to take this Coding Challenge further, go ahead and implement the remaining functionality of tr.