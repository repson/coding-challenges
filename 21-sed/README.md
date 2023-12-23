Coding Challenge #21 - sed
This week’s challenge is to build your own version of the Unix command line tool sed (short for Stream Editor)!
John Crickett
Aug 5, 2023

Sed is a Unix command line tool that parses and transforms text, using a simple, compact programming language. It was one of the first tools to support regular expressions.

The Unix command line tools, like sed, are a great metaphor for good software engineering and they follow the Unix Philosophies of:

    Design for simplicity; add complexity only where you must.

    Design programs to be connected to other programs - each tool can be easily connected to other tools, via files and streams, to create incredibly powerful compositions.

Following these philosophies has made the simple Unix command line tools some of the most widely used software engineering tools which can be chained together to create far more complex and powerful set of tools that you’d expect.

You can read more about the Unix Philosophy on the Coding Challenges blog.
The Challenge - Building You Own Sed

The functional requirements for sed are described by its man page: man sed give it a go in your terminal now.

It sounds like a simple utility, but sed has a wide range of uses including:

    Substitution.

    Filtering.

    In place editing of a file.

Difficulty - You Choose!

You can tackle this challenge at two different levels of difficulty:

    Easy - use the regular expression library from your programming language.

    Hard - implement your own regex engine.

You can do it either way, or even both! For both, build it the easy way then come back and re-implement the regex with your own engine. If you decided to do that, there’s a pretty good article explaining it at Let’s Build a Regex Engine.

Step Zero

Like most programming languages we’re zero indexed!

For this step, I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that here’s what I’d like you to do to be ready to test your solution.

Then let’s grab some quotes to use as test data:

% curl "https://dummyjson.com/quotes?limit=10" | jq '.quotes | .[] | .quote' > test.txt

Step 1

In this step your goal is to implement character replacement, that is reading a file and carrying out a regular expression change to it.

For example of we look at the content of the test file we produced in Step 0, we can see that each line is in quotes:

% cat test.txt
"Life isn’t about getting and having, it’s about giving and being."
"Whatever the mind of man can conceive and believe, it can achieve."
"Strive not to be a success, but rather to be of value."
"Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference."
"I attribute my success to this: I never gave or took any excuse."
"You miss 100% of the shots you don’t take."
"I’ve missed more than 9000 shots in my career. I’ve lost almost 300 games. 26 times I’ve been trusted to take the game winning shot and missed. I’ve failed over and over and over again in my life. And that is why I succeed."
"The most difficult thing is the decision to act, the rest is merely tenacity."
"Every strike brings me closer to the next home run."
"Definiteness of purpose is the starting point of all achievement."

sed takes some options, a command and then a filename, for this step we’ll ignore the options and handle the basic command assuming it is a substitution. This will look like:

ccsed s/this/that/g filename

Which will substitute this for that everywhere this appears in the file filename and will output the result to standard out.

At the end of this step, you should be able to remove the quotes from the file, for example:

% ccsed s/\\"//g test.txt
Life isn’t about getting and having, it’s about giving and being.
Whatever the mind of man can conceive and believe, it can achieve.
Strive not to be a success, but rather to be of value.
Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference.
I attribute my success to this: I never gave or took any excuse.
You miss 100% of the shots you don’t take.
I’ve missed more than 9000 shots in my career. I’ve lost almost 300 games. 26 times I’ve been trusted to take the game winning shot and missed. I’ve failed over and over and over again in my life. And that is why I succeed.
The most difficult thing is the decision to act, the rest is merely tenacity.
Every strike brings me closer to the next home run.
Definiteness of purpose is the starting point of all achievement.

Please use that to remote the quotes and save the output to a new file unquoted.txt.

Step 2

In this step your goal is to only output a range of lines from the file. To do this we use the -n option of sed and then specify a range, i.e. for lines 2 to 4 we would use the command: cat -n ccsed -n '2,4p’ filename

So that we can see that works let’s use cat to number the lines in our unquoted test file:

% cat -n unquoted.txt | ccsed -n '2,4p'
2	Whatever the mind of man can conceive and believe, it can achieve.
3	Strive not to be a success, but rather to be of value.
4	Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference.

If you’ve implemented this correctly you’ll get the output above.

Step 3

In this step your goal is to output only lines containing a specific pattern. The command for this looks like: ccsed -n /pattern/p filename which will only print lines that contain that pattern. Once you’ve implemented that you can test it with:

% ccsed -n /roads/p unquoted.txt
Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference.

Step 4

In this step your goal is to support double spacing a file. That use the option G, which once you’ve implemented it will look like:

% ccsed G unquoted.txt
Life isn’t about getting and having, it’s about giving and being.

Whatever the mind of man can conceive and believe, it can achieve.

Strive not to be a success, but rather to be of value.

Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference.

I attribute my success to this: I never gave or took any excuse.

You miss 100% of the shots you don’t take.

I’ve missed more than 9000 shots in my career. I’ve lost almost 300 games. 26 times I’ve been trusted to take the game winning shot and missed. I’ve failed over and over and over again in my life. And that is why I succeed.

The most difficult thing is the decision to act, the rest is merely tenacity.

Every strike brings me closer to the next home run.

Definiteness of purpose is the starting point of all achievement.

Step 5

In this step your goal is to strip trailing blank lines from a file. First set up your test file by adding a few of blank lines to unquoted.txt. You can do this in your IDE or with the command line: echo "\n\n\n" >> unquoted.txt . You can use cat to check the file now ends with several blank lines, then change your ccsed to support the command:

% ccsed /^$/d unquoted.txt
Life isn’t about getting and having, it’s about giving and being.
Whatever the mind of man can conceive and believe, it can achieve.
Strive not to be a success, but rather to be of value.
Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference.
I attribute my success to this: I never gave or took any excuse.
You miss 100% of the shots you don’t take.
I’ve missed more than 9000 shots in my career. I’ve lost almost 300 games. 26 times I’ve been trusted to take the game winning shot and missed. I’ve failed over and over and over again in my life. And that is why I succeed.
The most difficult thing is the decision to act, the rest is merely tenacity.
Every strike brings me closer to the next home run.
Definiteness of purpose is the starting point of all achievement.

Step 6

In this step your goal is to edit in place. That means supporting the -i option, you can test that with:

% ccsed -i 's/Life/Code/g' unquoted.txt && cat unquoted.txt
Code isn’t about getting and having, it’s about giving and being.
Whatever the mind of man can conceive and believe, it can achieve.
Strive not to be a success, but rather to be of value.
Two roads diverged in a wood, and I—I took the one less traveled by, And that has made all the difference.
I attribute my success to this: I never gave or took any excuse.
You miss 100% of the shots you don’t take.
I’ve missed more than 9000 shots in my career. I’ve lost almost 300 games. 26 times I’ve been trusted to take the game winning shot and missed. I’ve failed over and over and over again in my life. And that is why I succeed.
The most difficult thing is the decision to act, the rest is merely tenacity.
Every strike brings me closer to the next home run.
Definiteness of purpose is the starting point of all achievement.

Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.
Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John