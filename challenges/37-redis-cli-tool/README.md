Coding Challenge #37 - Redis CLI Tool
This challenge is to build your own version of the Redis CLI Tool.
John Crickett
Nov 25, 2023

When I recently released the course Become a Better Software Developer by Building Your Own Redis Server (Python Edition) I included building a simple version of the Redis CLI tool as one of the lessons and I’ve had some feedback that it would make an interesting challenge on it’s own, so here we are.

BTW, I’m currently porting the course to Go, signup here for the waitlist if you’re interested, everyone on the waitlist will be offered it first at a discount price.

Ad: Reach 60,000+ software engineers every week by sponsoring the Coding Challenges newsletter.

The Challenge - Building A Redis CLI Tool

In this Coding Challenge we’re going to build a CLI tool to send commands to a Redis server, it’s a nice challenge to complement the build your own Redis challenge. If you’re not familiar with Redis you can learn all about it in that challenge.

Step Zero

In this introductory step your task is to set up your environment up ready to begin developing and testing your solution.

Choose your target platform, set up your editor and programming language of choice. I’d encourage you to pick a tech stack that you’re comfortable doing both network programming (we’re building a tool that is a network client) and test driven development (TDD) with.

Once you’ve done that you might like to install Redis itself so you can use it to test your CLI tool implementation against.

Share Coding Challenges

Step 1

In this step your goal is to build the functionality to serialise and de-serialise Redis Serialisation Protocol (RESP) messages. This is the protocol used to communicate with a Redis Server. Throughout this step you may wish to refer to the RESP protocol specification.

Redis uses RESP as a request-response protocol in the following way:

    Clients send commands to a Redis Server as a RESP Array of Bulk Strings.

    The server replies with one of the RESP types according to the command implementation.

In RESP, the first byte determines the data type:

    For Simple Strings, the first byte of the reply is "+"

    For Errors, the first byte of the reply is "``"

    For Integers, the first byte of the reply is ":"

    For Bulk Strings, the first byte of the reply is "$"

    For Arrays, the first byte of the reply is "``"

RESP can represent a Null value using a special variation of Bulk Strings: "$-1\r\n" or Array: "*-1\r\n".

Now that we have the basics of the protocol, your challenge is to write the code required to serialise and de-serialise messages. My personal approach to this would be to use test-driven development (TDD) to build tests for some example messages, i.e.:

    "$-1\r\n"

    "*1\r\n$4\r\nping\r\n”

    "*2\r\n$4\r\necho\r\n$11\r\nhello world\r\n”

    "*2\r\n$3\r\nget\r\n$3\r\nkey\r\n”

    "*3\r\n$3\r\nset\r\n$3\r\nkey\r\n$5\r\nvalue\r\n”

    "+OK\r\n"

    "-Error message\r\n"

    "$0\r\n\r\n"

    "+hello world\r\n”

Don’t forget to include some invalid test cases too.

Step 2

In this step your goal is to build a simple tool that, when run, will open a network connection to a Redis server running on localhost:6379, send the PING command to it, wait for a response, decode and print the response.

In short running it will look something like this:

% ccredis-cli
PONG

Step 3

In this step your goal is to support selecting the host and port from the command line, as well as allow the execution of multiple commands until the user enters the quit command.

Firstly allow the user to specify the host and port of the server to connect to, like this:

% ccredis-cli -h localhost -p 6379

Next instead of sending the PING command, provide a prompt to the user which shows the host and port they are connected to and allows them to enter a command, something like this:

% ccredis-cli
127.0.0.1:6379>ping
PONG
127.0.0.1:6379>ping Hello
Hello
127.0.0.1:6379>echo HI!
HI!
127.0.0.1:6379>set key value
OK
127.0.0.1:6379>get key
value
127.0.0.1:6379>quit

The quit command should not be sent to the server, but should exit the program, closing the network connection to the server.

Step 4

In this step your goal is to support the help command and provide help for each of the commands Redis supports. You’re looking to make this work:

% ccredis-cli
localhost:6379> help
To get help about Redis commands type:
      "help @<group>" to get a list of commands in <group>
      "help <command>" for help on <command>
      "quit" to exit
localhost:6379> help set

  SET key value [NX|XX] [GET] [EX seconds|PX milliseconds|EXAT unix-time-seconds|PXAT unix-time-milliseconds|KEEPTTL]
  summary: Set the string value of a key
  since: 1.0.0
  group: string

localhost:6379>quit
%

You can find the content to use for the help in the Redis GitHub - redis/src/commands as a set of JSON files.

Step 5

In this step your goal is to support hints for the commands. If you look at the actual Redis CLI tool you’ll see (as shown in the screenshot below) that it offers a hint as to the usage of the command as you type it:

Your task for this step is to extract that information from the JSON files and display the correct hint for the command. A real-world use case for algorithms! 😀
Going Further

If you’d like to take this further, consider extending the tool to allow the user to start the CLI with a file that lists a set of commands to run. Then run the commands in turn, stopping if an error occurs.

This Coding Challenge has the same Step 1 as the build your own Redis challenge, so that might be a fun one to look at after this - you can leverage the code you’re already built and use this CLI tool to test your server.