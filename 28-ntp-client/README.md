Coding Challenge #28 - NTP Client
This challenge is to build your own Network Time Protocol client.
John Crickett
Sep 23, 2023

This challenge is to build your own Network Time Protocol client.

Network Time Protocol (NTP for short) is one of those protocols that is fundamental to the Internet and most modern computer systems but very rarely thought about by most of us.

Obviously we want our local computer’s time to be correct, but as we build distributed systems it also becomes important to ensure that all the computers within our systems are synchronised to the same, correct time. Sharing the correct time across servers is key for:

    Root-cause analysis of production issues. If network devices are out of sync by a few milliseconds or—in extreme cases—a few seconds, it can be very difficult to determine the sequence of events.

    Intrusion analysis - correctly timestamped logs can help determine which areas of a network hackers accessed first, uncover the vulnerabilities that were exploited.

    Legal compliance in some industries, for example finance.

Coding Challenges Live Edition.

I'm thinking of running another Cohort based course in November.

I'd love to know what would you like added to the course?

The previous course covered:

➡️ Breaking a project down into stages.
➡️ Selecting a tech stack for your project.
➡️ Documenting your decisions and explaining them using Architecture Decision Records.
➡️ Writing automated tests and running them in a CI pipeline.
➡️ Reviewing code (and having your code reviewed).
➡️ Understanding concurrency - async versus threads.
➡️ Optimising for performance.

Over a three week period as part of the process of building your own Redis Clone.

Full details of the previous course are here: https://maven.com/coding-challenges/challenge-redis

What else would you like to see included in the course to help you become a better software engineer? Hit reply and let me know. Thanks!

The Challenge - Building and NTP Client

NTP is a networking protocol for clock synchronisation between network attached devices. It is one of the oldest Internet protocols in current use.

NTP is intended to synchronise computers to within a few milliseconds of each other. It uses the intersection algorithm, a modified version of Marzullo's algorithm, to select accurate time servers and is designed to mitigate the effects of variable network latency.

Over the public Internet NTP can usually maintain time to within tens of milliseconds and on a local area network can usually do better than one millisecond accuracy.

However, asymmetric routes and network congestion can cause the accuracy to decrease.

The protocol is usually described in terms of a client–server model, but can also be used in peer-to-peer relationships. Clients and servers using NTP send and receive timestamps as UDP packets on port 123.

The full protocol is defined in the NTP RFC which is RFC 5905.

Step Zero

In this step you’re going to set your environment up ready to begin developing and testing your NTP client solution.

I’ll leave you to setup your editor and programming language of choice. I’d encourage you to pick a tech stack that you’re comfortable doing network programming in.

Step 1

In this step your goal is to send a request to an NTP server and receive the response back. You’ll need to contact the NTP server on port 123. The message you’ll need to send is defined in the RFC under section 7 on page 19. Take care to understand which fields you set for the outgoing message.

NTP uses a hierarchical, semi-layered system of time sources. Each level of the hierarchy is termed a stratum and is assigned a number starting with zero for the reference clock at the top.

A server synchronised to a stratum n server is considered to be a stratum n + 1 server. The number represents the distance from the reference clock and is used to prevent cyclical dependencies in the hierarchy. The stratum is not always an indication of the quality or reliability of the server.

For this challenge you can find a list of time servers you can use here or you can use one from the NTP Pool Project.

The packet you get back will have the same structure as packet you sent, check that the first three fields are correct then proceed to Step 2.

Step 2

In this step your goal is to decode the response from the NTP server and print out the four timestamps in the packet.

The obvious test here is to ensure they are all within a few milliseconds of each other (assuming your network latency to the NTP server you picked is reasonable). Test it with ping if you are unsure.

Step 3

In this step your goal is to calculate the offset and the round trip delay. A typical NTP client regularly polls one or more NTP servers. The client must compute its time offset and round-trip delay.

Time offset θ is the positive or negative (client time > server time) difference in absolute time between the two clocks. It is defined as:
\(\theta = \frac{(t_1 - t_0) + (t_2 - t_3 )}{2} \)

Where:

    t0 is the client's timestamp of the request packet transmission

    t1 is the server's timestamp of the request packet reception

    t2 is the server's timestamp of the response packet transmission and

    t3 is the client's timestamp of the response packet reception

The round-trip delay delta is calculated as:
\(delta = {(t_3 - t_0 ) - ( t_2- t_1 )} \)

Step 4

In this step your goal is to set the system clock based on the NTP calculated time. You’ll need to dig in to how to set the system time for your operating system from your programming language.

You can then adjust the local clock time in a loop until the offset is reduced to zero (or below some acceptable threshold, i.e. +/- 0.5ms).

When you’re confident you have it right you can test by:

    Set your system clock to an hour earlier than it is (you might need to disable the operating system’s automatic use of NTP in order to do this.

    Set your system time to an incorrect time.

    Run your code to set the time.

    Check that the time has updated to the correct time.

Don’t forget to re-enable the automatic use of NTP by your OS.

Once that’s done - congratulations you’ve built an NTP Client and seen how it can set your system time and how your OS uses an NTP client to keep the system time and date correct.
Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.
Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John