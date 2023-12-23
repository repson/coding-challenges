Coding Challenge #9 - grep
This week your challenge is to build your own version of the Unix command line tool grep.
John Crickett
May 13, 2023

This week your challenge is to build your own version of the Unix command line tool grep.

The Unix command line tools are a great metaphor for good software engineering and they follow the Unix Philosophies of:

    Writing simple parts connected by clean interfaces - each tool does just one thing and provides a simple CLI that handles text input from either files or file streams.

    Design for simplicity; add complexity only where you must.

    Design programs to be connected to other programs - each tool can be easily connected to other tools to create incredibly powerful compositions.

Following these philosophies has made the simple Unix command line tools some of the most widely used software engineering tools which can be chained together to create far more complex and powerful set of tools that you’d expect.

You can read more about the Unix Philosophy on the Coding Challenges blog.

Following these philosophies has made the simple Unix command line tools some of the most widely used software engineering tools - allowing us to create very complex text data processing pipelines from simple command line tools. There’s even a Coursera course on Data Engineering with Bash!
The Challenge - Building grep

The functional requirements for grep are concisely described by it’s man page - give it a go in your local terminal now:

% man grep
The grep utility searches any given input files, selecting lines that
match one or more patterns.  By default, a pattern matches an input line
if the regular expression (RE) in the pattern matches the input line
without its trailing newline.  An empty expression matches every line.
Each input line that matches at least one of the patterns is written to
the standard output.

N.B. grep can support basic regular expression and extended regular expressions. In GNU grep there is no difference between the two, both are extended. For none GNU versions of grep the -E option enables the extended pattern matching which is what we are going to look at in this challenge.

Difficulty - You Choose!

You can tackle this challenge at two different levels of difficulty:

    Easy - use the regular expression library from your programming language.

    Hard - implement your own regex engine.

You can do it either way, or even both! For both, build it the easy way then come back and re-implement the regex with your own engine. If you decided to do that, there’s a pretty good article explaining it at Let’s Build a Regex Engine.

Step Zero

Like most programming languages we’re zero indexed!

For this step, I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that here’s what I’d like you to do to be ready to test your solution.

Download the following text: https://www.gutenberg.org/cache/epub/132/pg132.txt and save it as test.txt. After that please download the additional test data from my dropbox here and unzip them, you should then have the following in your test directory:

% tree
.
├── rockbands.txt
├── symbols.txt
├── test-subdir
│   └── BFS1985.txt
└── test.txt

If you’re on Windows you can use GoW or GitBash to get a bash console, or if you’re a PowerShell user I’m sure you’re capable of translating the commands! Well better than I can! 😇

Step 1

In this step your goal is to implement support for an empty expression. An empty expression matches every line so the command grep "" test.txt will write every line of the file test.txt.

Implement your solution, run the command and check you get every line written out, you can automate this test with the Unix command line tools:

% grep "" test.txt | diff test.txt -
%

Shows that your grep output the same contents as the file test.txt because no diff is output. If your grep is not correct for this step there will be a diff output.

Step 2

In this step your goal is to match a simple one letter pattern and return the correct exit code to the shell. When a pattern is matched grep should return the exit code zero and non-zero when no pattern is matched.

% grep J rockbands.txt
Judas Priest
Bon Jovi
Junkyard

You can check the return code using echo $?.

Step 3

In this step your goal is to recurse a directory tree, that is to support the command line option -r.

So your test case for this step is:

% grep -r Nirvana *
rockbands.txt:Nirvana
test-subdir/BFS1985.txt:Since Bruce Springsteen, Madonna, way before Nirvana
test-subdir/BFS1985.txt:On the radio was Springsteen, Madonna, way before Nirvana
test-subdir/BFS1985.txt:And bring back Springsteen, Madonna, way before Nirvana
test-subdir/BFS1985.txt:Bruce Springsteen, Madonna, way before Nirvana

Step 4

In this step your goal is to implement the -v option. This inverts the search excluding and result that matches. If we’re not a fan of Madonna we might do this:

% grep -r Nirvana * | grep -v Madonna
rockbands.txt:Nirvana

Finding every one of the first results that doesn’t include Madonna.

Step 5

In this step your goal is to support \d and \w in the search pattern. Their meanings are:

    \d - a digit.

    \w - a word character.

Use the following two test cases to check your implementation:

% grep "\d" test-subdir/BFS1985.txt
Her dreams went out the door when she turned 24
There was U2 and Blondie, and music still on MTV
'Cause she's still preoccupied with 19, 19, 1985, 1985
There was U2 and Blondie, and music still on MTV
'Cause she's still preoccupied with 19, 19, 1985
There was U2 and Blondie, and music still on MTV
'Cause she's still preoccupied with 1985
There was U2 and Blondie, and music still on MTV
'Cause she's still preoccupied with 19, 19, 1985

% grep "\w" symbols.txt
pound
dollar

Step 6

In this step your goal is to implement support for matching ^ match to the beginning of a line and $ matches to the end.

You can test with:

% grep ^A rockbands.txt
AC/DC
Aerosmith
Accept
April Wine
Autograph

and:

% grep na$ rockbands.txt
Nirvana

The Final Step

In this step your goal is to support the optional command line argument -i, so you support case insensitive search:

% grep A rockbands.txt | wc -l
8

% grep -i A rockbands.txt | wc -l
58

Once you get the result above, congratulations! You’ve done it, pat yourself on the back, job well done!

Going Beyond This

We’ve covered some of the core functionality of grep, there’s lots more though if you want to go further. Alternatively, if you took the easy path, you could go back and try implementing your own regex engine.

Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server if you want to discuss them.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John