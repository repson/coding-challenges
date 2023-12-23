Coding Challenge #24 - Realtime Chat Client and Server
This challenge is to build your own real-time, multi-user chat server and client.
John Crickett
Aug 26, 2023

The server will be able to support multiple client connections. Every time a client sends a message to the server, the server will distribute the message to all the connected clients except the sender.

Before we dig into that, we're going to build what has largely become the 'Hello, World!' of network programming - an Echo server.
But First…
POLL
What would you most like to see in the Coding Challenges newsletter?
More systems programming challenges
29%
More backend challenges
38%
More frontend challenges
12%
Solutions to the past challenges
19%
Something else
2%
POLL CLOSED

If you answer something else or just fancy providing some feedback please feel free to reply to this email (if you get the newsletter by email) or reach out to me - details are in the footer.

Many thanks!

The Challenge - Building a Real-time Chat Server and Client
Step Zero

In this introductory step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to choose your target platform, setup your editor and programming language of choice. I’d encourage you to pick a tech stack that you’re comfortable doing network programming with (we’re building a client and a server after all).
Step 1

In this step your goal is to build an Echo Server

An Echo server listens for connections and the responds to every message sent on a connection with the same message. In other words it echos the message back to the client.

There is an echo server built into most Unix platforms (disabled by default). There is also a formal Echo protocol defined in RFC 862. We're going to implement the TCP version. The specification of which is quite simple:

    TCP Based Echo Service

    One echo service is defined as a connection based application on TCP. A server listens for TCP connections on TCP port 7. Once a connection is established any data received is sent back. This continues until the calling user terminates the connection.

So your challenge for this step is to create simple TCP/IP server that will listen on port 7007 (we’re going to use 7007 instead of 7 as ports below 1024 require elevated privileges on many operating systems).

When the server receives a message it should echo it back to the client. For now you only need to handle one client connection at a time.

You can test your echo server using a telnet client like so:

% telnet localhost 7007
Trying ::1...
telnet: connect to address ::1: Connection refused
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Hello Coding Challenges!
Hello Coding Challenges!
^]
telnet> quit
Connection closed.

I’ve highlighted the echoed text.
Step 2

In this step your goal is to build a simple network client that can send messages to the echo server. When your server starts up it should prompt the user for some input. When the user hits enter the input should be sent to the server and the response received and printed out.

Here’s how that might look if, like me you prefix each line with a hint as to what is happening:

% client
send: test
recv: test
send: quit
%

I suggest you make the client terminate when either quit or exit is entered by the user.
Step 3

In this step your goal is to change your client into a chat client. To do this you’ll want to allow the user to enter their name when they start the chat. Then you’ll want to send messages to the server prefixed with the users name. You can then connect to your echo server to test the client. That might look something like this:

% [chatclient](<http://chatclient.py/>)
name: John
Hi
John: Hi
John: Hi
exit

In the above the chat client echo’s out locally what the user entered and then echo’s out any messages received from the server. That’s why you see John: Hi twice. Don’t forget to ensure that your client can wait for both user input and a network message at the same time. If you don’t know how to do that look up select using either man or your programming language’s documentation.
Step 4

In this step your goal is to build the chat server. Your server should allow multiple users to connect and - you guessed it - chat! To do that your server will need to be either multithreaded or use an async framework to handle multiple concurrent client connections.

When the server receives a message from one client it will need to broadcast the message back to all the clients, except the sending client.

Once you have it working run the server and a couple of clients and talk to yourself - like I did:

% chatclient
name: John
Welcome to the chatroom!
OtherJohn: Hi!
Hey John!
John: Hey John!
How's things? What are you doing?
John: How's things? What are you doing?
OtherJohn: Writing a Coding Challenge!
Same!
John: Same!
exit

Congratulations you’ve now built a simple real-time chat server and client.

If you fancy taking this to the next level check out the Coding Challenge that has you building your own IRC Client!

Thank you for reading Coding Challenges. This post is public so feel free to share it.

Share
Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.
Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John