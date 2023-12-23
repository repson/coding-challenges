Coding Challenge #33 - Head
This challenge is to build your own version of the Unix command line tool head. It’s a great challenge for beginners and those new to the Unix command line tools.
John Crickett
Oct 28, 2023

The Unix command line tools are a great metaphor for good software engineering and they follow the Unix Philosophies of:

    Writing simple parts connected by clean interfaces - each tool does just one thing and provides a simple CLI that handles text input from either files or file streams.

    Design programs to be connected to other programs - each tool can be easily connected to other tools to create incredibly powerful compositions.

Following these philosophies has made the simple Unix command line tools some of the most widely used software engineering tools - allowing us to create very complex text data processing pipelines from simple tools. There’s even a Coursera course on Data Engineering with Bash!

You can read more about the Unix Philosophy on the Coding Challenges blog.

New Course Coming Nov 17th 2023

After several request for a self-paced, version of my cohort course I’m launching a a new course: Become a Better Software Developer by Building Your Own Redis Server (Python Edition)

The course will guide you through the Redis Coding Challenge using Python. You'll learn network programming, concurrency, test-driven development and how to build high-performance servers. At the end of it you will have built a fully working clone of the original Lua version of Redis in Python.

The course will be live on November 17th 2023. Until then it’s available at the pre-launch price of $100, after which it will be $150.

The Challenge - Building Head

Head is a command line tool that displays the first n lines or bytes of a file, where the user can provide the value for n. If no file or value for n is provided then it displays the first 10 lines from the standard input.
Step Zero

As always the first thing to do is decide on the programming language you’re going to use to tackle this challenge and set up your development environment. Then please download the following text: https://www.gutenberg.org/cache/epub/132/pg132.txt and save it as text.txt.

Once that’s done proceed to Step 1.
Step 1

In this step your goal is to take the filename or no filename and print the contents out. Some sample test cases for this look like:

% cchead test.txt 
The Project Gutenberg eBook of The Art of War
    
This ebook is for the use of anyone anywhere in the United States and
most other parts of the world at no cost and with almost no restrictions
whatsoever. You may copy it, give it away or re-use it under the terms
of the Project Gutenberg License included with this ebook or online
at www.gutenberg.org. If you are not located in the United States,
you will have to check the laws of the country where you are located
before using this eBook.

and:

% cchead
This is some text I typed in
This is some text I typed in
line 2
line 2
line 3
line 3
line 4
line 4
line 5
line 5
line 6
line 6
line 7
line 7
line 8
line 8
line 9
line 9
line 10
line 10

Note in this second example it is reading from the standard input and each line appears twice - the first is the echo of the standard input to the screen that bash (or whatever shell you are using - BTW you can learn more about Shells and build your own shell in another Coding Challenge) does; the second is the line from our cchead. Our implementation should terminate after line 10.
Step 2

In this step your goal is to display only the first n lines, where n is passed to the user as a command line argument. That should look like this:

% cchead -n1 test.txt
The Project Gutenberg eBook of The Art of War

Do test with different values of n and consider what will happen if there aren’t enough lines in the file. You could test that like this:

% echo "Hello, World" >> test2.txt
% cchead -n3 test2.txt 
Hello, World

Make sure your program terminates correctly.
Step 3

In this step your goal is to only display the first c bytes. You can test that like this:

% cchead -c 31 test.txt
The Project Gutenberg eBook

and

% cchead -c 30 test2.txt 
Hello, World

Again ensure you handle reaching the end of the file before printing the required number of characters.
Step 4

In this step your goal is to handle multiple files correctly. When multiple files are provided the output is presented, each file is preceded by a header consisting of the string “==> XXX <==” where “XXX” is the name of the file. That should look like this:

% cchead -n 10 test2.txt test.txt 
==> test2.txt <==
Hello, World

==> test.txt <==
The Project Gutenberg eBook of The Art of War
    
This ebook is for the use of anyone anywhere in the United States and
most other parts of the world at no cost and with almost no restrictions
whatsoever. You may copy it, give it away or re-use it under the terms
of the Project Gutenberg License included with this ebook or online
at www.gutenberg.org. If you are not located in the United States,
you will have to check the laws of the country where you are located
before using this eBook.

Note that up to n lines per file are output.

Once that is done, congratulations you’ve completed this Coding Challenge, why not try another more complex one?

Other Ways I May Be Able To Help You:

    I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

    I am available for 121 coaching and mentoring.

    I occasionally run a cohort based course: Coding Challenges Live: Redis Edition!

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John