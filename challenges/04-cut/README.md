Coding Challenge #4 - Build your own cut!
John Crickett
Apr 6, 2023

This weeks challenge is to build your own version of the Unix command line tool cut!

The Unix command line tools are a great metaphor for good software engineering and they follow the Unix Philosophies of:

    Writing simple parts connected by clean interfaces - each tool does just one thing and provides a simple CLI that handles text input from either files or file streams.

    Design programs to be connected to other programs - each tool can be easily connected to other tools, via files and streams, to create incredibly powerful compositions.

Following these philosophies has made the simple unix command line tools some of the most widely used software engineering tools which can be chained together to create far more complex and powerful set of tools that you’d expect.

You can read more about the Unix Philosophy in the excellent book The Art of Unix Programming.

The Challenge - Building cut

The functional requirements for cut are concisely described by it’s man page - give it a go in your local terminal now:

man cut

The TL/DR version is: cut - cuts out the selected portions from each line in a file.
Step Zero

In this introductory step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that here’s what I’d like you to do to be ready to test your solution, download the text from my Dropbox.

Step 1

In this step your goal is to implement a simple version of cut that will open the provided tab separated file and print out the second field (-f2) from each line. The result should look something like this:

cut -f2 sample.tsv
f1
1
6
11
16
21

Step 2

In this step your goal is to extend your code to support the -d option to allow the user to specify what character to use as the delimiter between fields. If no delimiter is provided then tab should still be used, we can test this first with a comma as the delimiter:

cut -f1 -d, fourchords.csv | head -n5
Song title
"10000 Reasons (Bless the Lord)"
"20 Good Reasons"
"Adore You"
"Africa"

Here we again seeing how the Unix command line tools can be chained (piped) together to create more powerful data processing pipelines. With the head command allowing us to limit the output to the first five lines.

Then check we still default to a tab:

cut -f1 sample.tsv
f0
0
5
10
15
20

Step 3

In this step your goal is to add support for the -f option. This option specifies a list of fields to be printed out. Output fields are separated by a single occurrence of the field delimiter character.

The field list is a comma or whitespace separated list of fields, i.e. -f1,2 or -f “1 2”. The first field is field number 1.

Here’s a couple of tests on this:

cut -f1,2 sample.tsv
f0      f1
0       1
5       6
10      11
15      16
20      21

and

cut -d, -f"1 2" fourchords.csv | head -n5
Song title,Artist
"10000 Reasons (Bless the Lord)",Matt Redman and Jonas Myrin
"20 Good Reasons",Thirsty Merc
"Adore You",Harry Styles
"Africa",Toto

Step 4

In this step your goal is to support reading from the standard input stream if no filename is provided or if the single dash is provided ‘-’.

tail -n5 fourchords.csv | cut -d, -f"1 2"
"Young Volcanoes",Fall Out Boy
"You Found Me",The Fray
"You'll Think Of Me",Keith Urban
"You're Not Sorry",Taylor Swift
"Zombie",The Cranberries

or

tail -n5 fourchords.csv| cut -d, -f"1 2" -
"Young Volcanoes",Fall Out Boy
"You Found Me",The Fray
"You'll Think Of Me",Keith Urban
"You're Not Sorry",Taylor Swift
"Zombie",The Cranberries

Step 5

In this step we’re going to revisit the first coding challenge and use our wc tool, combining it with our new cut tool to build a simple command line data engineering pipeline. We’ll test that by seeing how many unique artists are in the data set, again piping together Unix command line tools.

cut -f2 -d, fourchords.csv | uniq | wc -l
155

Share Your Solutions!

Even though this is only the first coding challenge I’ve already been asked to share model solutions in as many programming languages as possible - which is an awesome idea, but I just don’t have the time and don’t know even half the programming languages out there so I’d like your help!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message via Twitter or LinkedIn or just post about it there and tag me.

I’ll take a look at every solution and I’ll mention the best solution in the follow week’s newsletter.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John

P.S. This is on the Coding Challenges website as: Build You Own cut.