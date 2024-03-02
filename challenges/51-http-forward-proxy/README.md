Coding Challenge #51 - HTTP Forward Proxy Server
This challenge is to build your own HTTP Forward Proxy Server.

JOHN CRICKETT
MAR 2, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 47,218 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #51 - Build Your Own HTTP Forward Proxy Server

This challenge is to build your own HTTP Proxy Server. A proxy is a server that sits between a client that wants to get a resource and a server that provides the resource.

There are two types of proxy servers that you’ll come across: forward proxies and reverse proxies. As software engineers most of us have probably come across reverse proxies, perhaps even configured and operated them in our infrastructure. For those that haven’t here’s a brief overview.

A reverse proxy is typically installed in front of a collection of servers that provide a service to clients. They’re transparent to the clients and typically provide one of more of the following: services:

Load balancing.

Geo forwarding.

DDoS protection.

TLS termination.

Caching.

For example, a CDN service service is in effect a reverse proxy.

Forward proxies are talked about less often, at least by software engineers, as we’re not usually asked to build or run them. If anything I’ve probably spent more of my career focusing on ways around them. 🤫 Not least in the early days of the Internet when many organisations used forward proxies to block large parts of the Internet - one company I worked for blocked all access to MSDN which made being a Windows developer at the time somewhat challenging!

That said some browsing restrictions make sense and forward proxies provide the ability to enforce these restrictions. They can also be used to obfuscate the identify of users where multiple users all connect through the same proxy.

Ironically we can also use use a forward proxy to circumvent browsing restrictions.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

Reminder - Getting Help And Feedback On Your Solutions

If would like some feedback on your solution the best place to get it is on the Discord server - come join the Coding Challenges community, all welcome.

The Challenge - Building Your Own Forward Proxy Server

We’re going to build a simple forward proxy that we can use to proxy some of our HTTP/HTTPS requests through. We’ll then implement some browsing restrictions to see how that works too.

Step Zero

Please set up your IDE / editor and programming language of choice and proceed directly to Step 1 once you’re ready. It would make sense to also have a tool like curl or postman to hand too.

Step 1

In this step your goal is to create a minimal forward proxy. When it’s done you can test it using curl like this:

% curl --proxy "http://localhost:8989" "http://httpbin.org/ip"
In this case we’re telling curl to send the request via our proxy server that is running locally on port 8989.

If you remember from the build your own curl coding challenge, curl will normally send a request that looks like this (I’m only showing the fields we’re interested in):

GET /ip HTTP/1.1
Host: eu.httpbin.org

When we tell it to use the proxy, the request changes and instead looks like this:

GET http://httpbin.org/ip HTTP/1.1
Host: eu.httpbin.org
Proxy-Connection: Keep-Alive

You can configure your proxy server however you like, logging as much or as little as you like, but this is the output I see from mine (running in another terminal):

% ./ccproxy
Starting proxy server on 127.0.0.1:8989
Request made. Target: httpbin.org:443 Client: 127.0.0.1:56157

To make the proxy server work you will need to do the following:

Have your proxy server start up and listen for connections. In my case I decided to listen on port 8989.

When a request is received parse it to extract the target host.

Create a new socket / connection to the target server.

Forward the request, minus the hop by hop headers.

Change the GET request.

Add the ‘X-Forwarded-For’ header.

Read the response from the target server and set the correct response headers before,

Sending the response to the client.

You can find more about the headers in RFC 7230 and on the MDN website.

Step 2

In this step your goal is to refuse to proxy a request to domain on the banned list. In other words like many of the old school corporate proxies used to, you should stop access to some sites that are deemed inappropriate/unsafe/nsfw.

I suggest your proxy reads a list of forbidden hosts from a forbidden-hosts.txt file and refuses to server any requests for them. Here’s how that looked for me, when I added Facebook to the ban list:

% curl --proxy "http://localhost:8989" -v "http://facebook.com/"
*   Trying 127.0.0.1:8989...
* Connected to localhost (127.0.0.1) port 8989 (#0)
> GET <http://facebook.com/> HTTP/1.1
> Host: facebook.com
> User-Agent: curl/8.1.2
> Accept: */*
> Proxy-Connection: Keep-Alive
>
< HTTP/1.1 403 Forbidden
< Content-Type: text/plain; charset=utf-8
< X-Content-Type-Options: nosniff
< Content-Length: 34
<
Website not allowed: facebook.com

Step 3

In this step your goal is to refuse to proxy a web page if certain content appears on the page. Again your proxy could read a list of banned words from a banned-words.txt file and refuse to serve the page if any of those words appear in the response.

For a test I’ve banned the word ‘dummy’ then tried:

% curl --proxy "http://localhost:8989" -v "http://dummyjson.com/"
*   Trying 127.0.0.1:8989...
* Connected to localhost (127.0.0.1) port 8989 (#0)
> GET http://dummyjson.com/ HTTP/1.1
> Host: dummyjson.com
> User-Agent: curl/8.1.2
> Accept: */*
> Proxy-Connection: Keep-Alive
>
< HTTP/1.1 403 Forbidden
< Content-Type: text/plain; charset=utf-8
< X-Content-Type-Options: nosniff
< Content-Length: 43
<
Website content not allowed.

Step 4

In this step your goal is to log all the traffic going through the proxy. For example your proxy server might log like this:

% ./ccproxy
Starting proxy server on 127.0.0.1:8989
Client: 127.0.0.1:62448 Request URL: http://httpbin.org/ip
127.0.0.1:62448   200 OK
Client: 127.0.0.1:62454 Request URL: http://httpbin.org/ip
127.0.0.1:62454   200 OK

Ideally you want to log this to a file and optionally to standard out. You should probably include a date and timestamp - I’ve removed them for clarity here.

Step 5

In this step your goal is to handle TLS so you can also proxy HTTPS requests. So far we’ve only looked at proxying HTTP requests, but most of the Internet is now using HTTPS for very good privacy reasons. We want our proxy server to support that too.

Here’s what happens if we don’t:

% curl --proxy "http://localhost:8989" "https://httpbin.org/ip"
curl: (56) CONNECT tunnel failed, response 400

So we want to extend the proxy server to support HTTPS, which would result in the request succeeding:

% curl --proxy "http://localhost:8989" "https://httpbin.org/ip"
{
  "origin": "82.61.42.63"
}

The error message gives us a hint of what we should do. we need to create a tunnel and support the CONNECT method request. You can see what curl is doing with the -v option:

% curl --proxy "http://localhost:8989" -v "https://httpbin.org/ip"
*   Trying 127.0.0.1:8989...
* Connected to localhost (127.0.0.1) port 8989 (#0)
* CONNECT tunnel: HTTP/1.1 negotiated
* allocate connect buffer
* Establish HTTP proxy tunnel to httpbin.org:443
> CONNECT httpbin.org:443 HTTP/1.1
> Host: httpbin.org:443

The key bit here is the CONNECT line: CONNECT httpbin.org:443 HTTP/1.1 which is asking the proxy to create a connection to the specified host and port. If that connection is established then the proxy will send back a 200 response letting the client know that a tunnel has now been established between the client and the end host.

To implement the tunnel a proxy will need to read data sent to it by the client and forward it to the end server, and in return, read data sent by the end server and forward it to the client. Curl or another client can then send TCP traffic from the client to the end server, including TLS traffic via the tunnel.

Once you have this working you can adjust your computer to route all your web traffic through your proxy - if that works, congratulations you’ve built a forward proxy server.

Going Further

To get even more out of this challenge consider two things:

The connection between your client and your proxy server is not running over TLS - how would you extend the proxy server to provide a secure connection?

If a proxy server provides TLS termination between your client and the end server then so could another proxy server. That proxy server could be malicious or could just be insecure. So be careful when browsing the web through a machine that uses a proxy server even if the connection is over HTTPS it might not be secure.

2 Other Ways I Can Help You:
I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

I have some courses available:

Build Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

Build Your Own Shell (Go Edition) which guides you through solving the Shell Coding Challenge in Go.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John