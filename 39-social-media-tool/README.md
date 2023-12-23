Coding Challenge #39 - Social Media Tool
This challenge is to build your own version of a social media tool, like Buffer, HyperFury or Tapilo.
John Crickett
Dec 9, 2023

If you’re not aware these tools allow you to draft, edit and schedule posts for one or more social media platforms.

In this challenge we’re going to focus on LinkedIn and X (the social media platform formerly known as Twitter). Other social networks are available.

Aside: Guided Coding Challenges

I have a guided course that walks you through Building Your Own Redis Server in Python and I’m currently porting the course to support building Redis in Go.

After that, which Coding Challenge would you most like to see me build a course around?
POLL
Which Coding Challenge would you most like to see me build a course around?
Web Server
59%
URL Shortener
26%
LISP Interpreter
15%
POLL CLOSED
The Challenge - Building a Social Media Tool

In this challenge we’re going to focus in the infrastructure to create, edit and post on a schedule a post to a single social media platform. That takes you through using a message queue, scheduling and event and calling RESTful APIs.

You can (and should) consider extending it to include authentication of users. If you wanted to take it even further you could extend this challenge to be a full blown business. As you can see from Buffer’s transparency dashboard it’s potentially a profitable business.

Step Zero

As always we’re zero-indexed like every good programming language! In this step please set up your IDE, grab a good cup of coffee (or other beverage of your choice) and create a new project.

After that you will want to sign up either the LinkedIn or X APIs (or even both). You can sign up for the APIs and red their documentation via the following.

LinkedIn’s API is documented here: https://learn.microsoft.com/en-us/linkedin/consumer/integrations/self-serve/share-on-linkedin

X’s API is documented here: https://developer.twitter.com/en/products/twitter-api

Step 1

In this step your goal is to build a backend service to make a post. I’d suggest you build this as a simple service that will listen to a message queue and when it receives a message on the queue will then call the relevant API to post on the related social network.

For example a message might be in JSON and contain fields for: author, post body, and visibility.

This service could then be deployed to a Cloud platform fed via one of their queues or hosted locally and fed via a local message queue such as ZeroMQ or RabbtMQ.

Step 2

In this step your goal is to store a post in a database. You should create a service that can receive a post and store it’s details in a database. Initially the database will need the same fields as we used in Step 1, but expect to add more soon.

Step 3

In this step your goal is to schedule a post. For this you’ll need a post date and time field in the database and the ability to set it when creating the post in the database.

You’ll also what to build or leverage some form of scheduling service. That will either be triggered by a field in the database (i.e. a TTL in something like DynamoDB) or that will periodically check the database for posts that are ready to be posted.

Consider the tradeoffs between the different approaches and how they will scale.

Step 4

In this step your goal is to create a user interface that will allow a user to create a post and either post it immediately or schedule it to be posted at a later date and time.

Step 5

In this step your goal is to create a user interface that allows a user to edit one of their scheduled posts, updating the content and/or changing the time and date that it is scheduled to be posted on the social network.

Going Further

We’ve just scraped the tip of the iceberg with this challenge, so take a look at some of the existing products out there to see how you can take it further. For example add other social media, support posting other media types.

2 Ways I Can Help You:

    I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

    I have a course Become a Better Software Developer by Building Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John