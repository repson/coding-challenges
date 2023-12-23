Coding Challenge #10 - Build Your Own uniq Tool
This weeks challenge is to build your own version of the Unix command line tool uniq.
John Crickett
May 20, 2023

I’m a big fan of the Unix Philosophy and the command line tools it has spawned. By chaining them together you can create complex and powerful software from simple building blocks. That’s a great model to follow for the functions and modules in the software you write and the components you use in the systems you build as a software developer.
The Challenge - Building uniq

Let’s check out the man page on uniq to find out what it does:

The uniq utility reads the specified input_file comparing adjacent lines, and writes a copy of each unique input line to the output_file.  If input_file is a single dash (‘-’) or absent, the standard input is read.  If output_file is absent, standard output is used for output.  The second and succeeding copies of identical adjacent input lines are not written.  Repeated lines in the input will not be detected if they are not adjacent, so it may be necessary to sort the files first.

Step Zero

Like most programming languages we’re zero indexed!

For this step, I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that here’s what I’d like you to do to be ready to test your solution.

Download the test data from my dropbox here and unzip it.
Step 1

In this step your goal is to read an input file and and handle the default behaviour, which is to remove duplicate adjacent lines.

For example the input:

line1
line2
line2
line3
line4

would become:

% uniq test.txt
line1
line2
line3
line4

You can test your program using the above or on the countries list:

% uniq countries.txt | wc -l
246

Step 2

In this step your goal is to read from std input and write out to a file. When the input argument is - then you should read from standard input. When an output file is specified you should write to that rather than standard out.

For example, read from standard input and write to standard out:

% cat test.txt| uniq -
line1
line2
line3
line4

Read from standard input and write to a file:

% cat test.txt| uniq - out.txt
% cat out.txt
line1
line2
line3
line4

Step 3

In this step your goal is to support the count option: -c or --count. This adds a new first column that contains a count of the number of times a line appears in the input file.

% uniq -c test.txt
1 line1
2 line2
1 line3
1 line4

Step 4

In this step your goal is to implement the repeated option: -d or --repeated. When this option is specified your program should output only repeated lines.

% uniq -d test.txt 
line2

Try the command uniq -d countries.txt to find out which countries cuisine my kids love!
Step 5

In this step your goal is to output only uniq lines - that is the -u option. When implemented you should be able to do this:

% uniq -u test.txt
line1
line3
line4

Step 6

In this step your goal is to support a combination of command line options, i.e. uniq -c -d countries.txt Each of the repeated countries should appear twice.

Once you’ve done that - congratulations you’ve built a lite version of the unix command line tool uniq!
Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John