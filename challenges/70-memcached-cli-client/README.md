Coding Challenge #70 - Memcached CLI Client
This challenge is to build your own Memcached CLI Tool.
John Crickett
Aug 3

Coding Challenge #70 - Memcached CLI Client

This challenge is to build your own Memcached CLI client. Memcached is a free, open source, high-performance, distributed memory object caching system. It is intended for use in speeding up dynamic web applications by reducing database load.

Memcached is an in-memory key-value store for small chunks of arbitrary data retrieved from back end systems with higher latency. It is simple yet powerful.

Its simple design promotes quick deployment, ease of development, and solves many problems facing large data caches. Its relatively simple API is available for most popular languages.

It’s simple text based network protocol makes it a great platform to use to learn how to build network clients and servers. In this coding challenge we’re going to focus on a client, but if you fancy learning how to build a server, check out the build your own memcached and build your own Redis server coding challenges.

The Challenge - Building A Memcached CLI Client

Memcached is a simple yet powerful server with client libraries in many programming languages. But sometimes it’s useful to be able to interact with a server from the command line. For example it’s useful to be able to use curl to fetch web pages or test/automate calls to RESTful API.

Redis comes with CLI tool, but Memcached doesn’t, so this coding challenge is to build a simple CLI tool for some of the most common Memcached use cases.

Step Zero

Like all good programming languages we’re zero indexed!

For this step, I’ll leave you to setup your IDE / editor of choice and programming language of choice. Keep in mind we’re building a network client so pick a stack you’re comfortable doing that in or would like to learn how to be comfortable doing it in.

If you haven’t built your own Memcached server you should install one that you can connect to for testing.

Step 1

In this step your goal is to build the functionality to serialise and de-serialise the memcached text based protocol. This is the protocol used to communicate with a Memcached Server. Throughout this step you may wish to refer to the Memcached protocol specification.

Storage commands look like this:

<command name> <key> <flags> <exptime> <bytes> [noreply]\r\n

Where <command name> is set, add, replace, append or prepend. The key is a string identifying the key to be used to store the value. Please refer to the protocol specification for the other fields - being able to read a protocol specification and implement it is a useful skill for software engineers.

After the command comes the value in the data block:

<data block>\r\n

The server will then respond with one of :

    STORED\r\n, to indicate success.

    NOT_STORED\r\n to indicate the data was not stored, but not because of an error. This normally means that the condition for an "add" or a "replace" command wasn't met.

    Another response, which you’ll find in the specification but don’t need to implement unless you decide to support Check And Set (CAS) commands.

Retrieval commands look like this:

get <key>*\r\n

In response to this command, the server will send back zero or more items. Each item is sent as a text line followed by a data block. After all the items have been sent, the server sends the string:

END\r\n

to indicate the end of response. Each item sent by the server consists of two lines, the first looks like this:

VALUE <key> <flags> <bytes>\r\n

And the second:

<data block>\r\n

Now that we have the basics of the protocol, your challenge is to write the code required to serialise and de-serialise messages. My personal approach to this would be to use test-driven development (TDD) to build tests for some example messages. Turning the messages into one or more data structures I can use in my code.

Step 2

In this step your goal is to handle command line arguments. The user should be able to set the host server (either hostname or IP address) and the port to use, i.e.:

% ccmc -host memcached.codingchallenges.fyi -p 12121 <command> [<options>]

You should use the defaults of localhost and 11211 if no host or port are specified.

For this step you should also handle the commands set and get. For example:

% ccmc -host memcached.codingchallenges.fyi -p 12121 set testkey testvalue

% ccmc -host memcached.codingchallenges.fyi -p 12121 get testkey

Bonus points for supporting an option for help, i.e. -?, —-?, -h or --help that will display a suitable help message.

Step 3

In this step your goal is to connect to the server and send the set and get messages to the server and the display the result to the user. That would look like this:

% ccmc set test 1234
% ccmc get test
1234

Step 4

In this step your goal is to support for the commands: add and replace. The add command stores the data, but only if the server doesn't already hold data for the key.

The replace command stores the data, but only if the server does not already hold data for the key. As for set and get commands the general format is:

<command name> <key> <flags> <exptime> <byte cound> [noreply]\r\n
<data block>\r\n

When the preconditions of add and replace are not met the server returns  NOT_STORED  otherwise it returns STORED.

Step 5

In this step your goal is to support the append and prepend commands. The append command results in the data being added to an existing key after existing data. Whereas the  prepend  command results in adding the data to an existing key before the existing data.
Going Further

If you want to take this project further you can look at adding support for the cas (Check and Set) operation and the delete, increment and decrement operations.