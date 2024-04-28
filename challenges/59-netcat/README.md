Coding Challenge #59 - Netcat
This challenge is to build your own version of netcat.

JOHN CRICKETT
APR 27, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 52,837 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #59 - Build Your Own Netcat

Netcat - which is usually abbreviated to nc is a command line networking utility for reading and writing to network connections with TCP or UDP.

Netcat has many uses, it can be used to probe a network or server looking for vulnerabilities, debugging a network or server, creating a basic server, creating a reverse shell, creating a hex dump of transmitted data, transferring a file and several other things.

Some of it’s functionality overlaps with other Coding Challenges. It can function as a port scanner, a DNS resolver and even be used to create a basic chat client and server. Which makes it a very useful tool to know about and have in your toolbox.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It

Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building Your Own Netcat
In this coding challenge we’ll build a clone of netcat as a way of learning more about building TCP and UDP clients and servers.

Step Zero

As always your first challenges is to set your environment up ready to begin developing and testing your solution.

I’d encourage you to pick a programming language and tech stack that you’re comfortable doing network programming with (we’re building a client and a server after all) and handling command line arguments.

Step 1

In this step your goal is to support listen mode using TCP. By default netcat will use TCP so we for this step we will ignore UDP. Your goal therefore is to support this command line:

% ccnc -l -p 8888

This should start up your netcat clone ccnc listening (-l) for TCP (the default) connections on port 8888 (-p). You can use the real nc to test your clone by doing:

% nc -v localhost 8888

Connection to localhost port 8888 [tcp/ddi-tcp-1] succeeded!
Hi CCNC!

Where Hi CCNC! is what you type in after the connection succeeded message. If your server works it should echo out the data it received, i.e.:

% ccnc -l -p 8888
Hi CCNC!

You should send a CTRL-Z (Windows) or CTRL-D (*nix) from the test netcat client to end the connection.

Step 2
In this step your goal is to extend your netcat to support a UDP server. To select UDP mode accept the command line option -u.

% ccnc -l -p -u 8888

Again you can test this using the real netcat:

% nc -v -u localhost 8888
Connection to localhost port 8888 [udp/ddi-udp-1] succeeded!

Note that this time it’s showing a UDP connection. Try sending some test messages.

N.B. you can send messages from both sides, make sure you support that in your code!

Step 3

In this step your goal is to be able to use your netcat to check if a server is listening on a specified port by attempting to connect to the port, but not sending any data to it (-z). You should support connecting to a single port and scanning a range of ports. To test your code use the real netcat to create a server:

% nc -l -p 8888

Then test your code trying a single port:

% ccnc -z localhost 8888
Connection to localhost port 8888 [tcp] succeeded!

And with a range of ports:

% ccnc -z localhost 8880-8890
Connection to localhost port 8888 [tcp] succeeded!

Notice it only announced the port that was open. You could extend this to support the verbose (-v) option too.

Step 4

In this step your goal is to support the -e option which allows netcat to turn any process into a server. That will mean you run the specified process and pipe the input and output to/from it to/from the connected client. That looks something like this to operate as a reverse shell:

% ccnc -l -p 8888 -e /bin/bash

You can then test that with the real netcat as so:

% nc localhost 8888
ls
file.txt

Where file.txt was a test file I had in the current working directory.

Step 5

In this step your goal is to support hex dumping of the transmitted data. In other words the -x flag. When run with this flag it should look like this (server end):

% ccnc -x -l -p 8888
Hello from the client
Received 22 bytes from the socket
00000000  48 65 6C 6C  6F 20 66 72  6F 6D 20 74  68 65 20 63  Hello from the c
00000010  6C 69 65 6E  74 0A                                  lient.
Response from the server
Sent 25 bytes to the socket
00000000  52 65 73 70  6F 6E 73 65  20 66 72 6F  6D 20 74 68  Response from th
00000010  65 20 73 65  72 76 65 72  0A                        e server.

And the client end (by now you should be able to use either your netcat or the real one):

% nc localhost 8888
Hello from the client
Response from the server

If you’re not familiar with hex dumps you might like to check out the build your own xxd coding challenge.

Going Further

To take this further run the command man nc and implement any other features of netcat that take your fancy.

2 Other Ways I Can Help You:

I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

I have some courses available:

Build Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

Build Your Own Shell (Go Edition) which guides you through solving the Shell Coding Challenge in Go.

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John