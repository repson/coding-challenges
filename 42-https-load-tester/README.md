Coding Challenge #42 - HTTP(S) Load Tester
This challenge is to build your own version of a HTTP(S) Load Tester.
John Crickett
Dec 23, 2023
Happy Holidays!

As we reach the end of 2023 I’d like to wish all the readers of Coding Challenges a happy holiday season and thank you for your continued support and interest in Coding Challenges! 🎉
Now Lets Get Into The Load Tester Coding Challenge!

A HTTP(S) Load Tester is a program that can be used to simulate a load on a website or HTTP(S) based API. It’s a useful tool for tasks such as checking your system handles concurrent load, scales correctly under load and to verify that your rate limiting software works correctly.
The Challenge - Building Your Own HTTP(S) Load Testing Tool

For this coding challenge we’re going build a tool that can make a high volume of concurrent HTTP(S) request against an website/HTTP based API. You could think of it as building your own version of curl, but on steroids, and with some metrics capture and reporting.
Step Zero

In this step you decide which programming language and IDE you’re going to use and you get yourself setup with a nice new project.

Once you’ve done that, have a think about a suitable target for your load testing - if you have a suitable work project you could use that. If not, consider setting up a local web server than you can use. You could even do the build your own web server coding challenge first and use that!

If you haven’t done that challenge feel free to install your favourite web server. If you don’t have one, I’ve documented how to use run a simple web server using Python on the Coding Challenges website.
Step 1

In this step your goal is to read a URL from the command line and make one request to it. That will look something like this:

% ccload http://eu.httpbin.org/get
Response code: 200

I’ve chosen to print out the response code so I can see that it worked.
Step 2

In this step your goal is to allow the user to specify how many requests to make as well as the URL to test. To handle that we are going to want to expand the command line options to accept:

Option Meaning Default -u URL None -n Number of requests to make 10

So the command line then starts to look something like this:

% ccload -u http://eu.httpbin.org/get -n 1
Response code: 200

Be sure to ensure that you make the n requests. Please be careful not to load test a website that you don’t own/have permission to do so - it will look like, and could become, a denial of service attack!
Step 3

So far the requests we’ve sent to the server have all been done in sequence, one after the other - not much of a load test! So in this step your goal is to allow concurrent requests.

To do this let’s add a new option -c for number of concurrent and we’ll stop reporting each result instead producing a brief summary.

% ccload -u http://localhost:8000 -n 100 -c 10
Successes: 100
Failures: 0

Don’t forget to handle the different ranges of HTTP response codes as well as network errors.
Step 4

In this step your goal is to gather some stats for each request. Some useful stats to collect are:

    Total time for each request.

    Time to first byte.

    Time to last byte.

As well as the number of responses for each HTTP response code. Collect the stats in a suitable data structure and we’ll look at reporting them in the next step.
Step 5

In this step your goal is to report the stats gathered in step 5 in a summary format that is useful to the user, for example:

% ccload -u http://localhost:8000 -n 100 -c 10

Results:
 Total Requests (2XX).......................: 100
 Failed Requests (5XX)......................: 0
 Request/second.............................: 79.57

Total Request Time (s) (Min, Max, Mean).....: 0.15, 0.65, 0.35
Time to First Byte (s) (Min, Max, Mean).....: 0.1, 0.5, 0.25
Time to Last Byte (s) (Min, Max, Mean)......: 0.12, 0.6, 0.27

Feel free to add other stats that you think of, or that would be useful to you in your work.
Step 6

In this step your goal is to read the URLs to test from a file. We could do this by adding a -f option which when present if followed by the name of file that contains a list of URLs to use.

% ccload -f urls.txt -n 100 -c 10

Results:
... snipped ...

I would suggest that if the number of URLs is less than the number of requests to be made, then the urls are simply repeated, i.e. if there are 10 URLs and 100 requests, each URL would be requested 10 times.

Once you’ve done this step, congratulations you’ve built a HTTP(S) load tester!
Going Further

You can take this project much further, here are some ideas to consider:

    Allow scripting of requests.

    Support other HTTP methods, and the sending of JSON data for POST and PUT.

    Create the statistics in a format that can be exported to a metric processing tool.

    Allow the testing to be distributed across multiple clients to increase the load beyond that a single client can support.

    Render some graphs with the data.

2 Other Ways I Can Help You:

    I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

    I have some courses available:

        Become a Better Software Developer by Building Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

        Build Your Own Shell (Go Edition) which guides you through solving the Shell Coding Challenge in Go.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.