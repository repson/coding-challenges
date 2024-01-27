Coding Challenge #46 - yq
This challenge is to build your own version of yq
John Crickett
Jan 27, 2024

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 41,012 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #45 - yq

This challenge is to build your own version of yq

The tool yq is a lightweight and flexible command-line YAML processor. It’s useful for processing YAML allowing us to quickly and effectively filter out the bits we want.

If You Enjoy Coding Challenges Here Are Four Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

    If you work for a company that sells to software engineers, encourage them to sponsor the newsletter. 🙏

Coding Challenges News

I’m currently asking for feedback on what challenges to cover next. I’d appreciate your thoughts on LinkedIn, Twitter or by email - just hit reply. Thanks.

Purchasing Price Parity - I’m now offering PPP on my courses making them more accessible for everyone. Many thanks to all those who suggested it.

The Challenge - Building Your Own yq

The command line tool yq is like jq for YAML data - you can use it to and filter and transform YAML data, much like you would JSON dats with jq. By the way, a past Coding Challenge was to build your own jq if you fancy giving that a go.

Step Zero

Like yq itself we’re zero-indexed! In this step you’re going to set your environment up ready to begin developing our yq clone: ccyq.

You can download some test YAML from my dropbox here.

Step 1

In this step your goal is to open the yaml file, read it and print it. You could parse it at this point or just read it and print it line by line.

The outcome should look something like this:

% ccyq quotes.yaml 
quotes:
  - id: 1
    quote: It is bad for a young man to sin; but it is worse for an old man to sin.
    author: Abu Bakr (R.A)
<snip>
  - id: 5
    quote: >-
      These Capitalists Generally Act Harmoniously And In Concert, To Fleece The People.
    author: Abraham Lincoln

N.B. I’ve trimmed the output to just show the first and last quote.

Step 2

In this step your goal is to handle the object identifier: .quotes and .[<string>], as well as the optional (?) extension to it.

The commands you want to support look like this:

% ccyq '.[quotes]' quotes.yaml
% ccyq '.["quotes"]' quotes.yaml
% ccyq '.quotes?' quotes.yaml
% ccyq '.["quotes"]?' quotes.yaml

Don’t forget to add to the YAML file to ensure that only the quotes are extracted.

Step 3

In this step your goal is to support the array index: .[<number>]. Like most programming languages, arrays in yq are zero indexed.

In use that would look something like this:

% ccyq '.quotes[0]' quotes.yaml
id: 1
quote: It is bad for a young man to sin; but it is worse for an old man to sin.
author: Abu Bakr (R.A)

Don’t forget to test other index values, including those that are out of range.

Step 4

In this step your goal is to support the pipe operator ‘|’. The pipe operator combines two filters by feeding the output of the one on the left into the one on the right. It's similar to the Unix shell's pipe. Here’s an example command:

% ccyq '.quotes[1] | .quote' quotes.yaml
If You Are Out To Describe The Truth, Leave Elegance To The Tailor.

Step 5

In this step your goal is to collect the output as an array. You can do this by wrapping the filter in square brackets, that would look like this:

% ccyq '[.quotes[].quote]' quotes.yaml
- It is bad for a young man to sin; but it is worse for an old man to sin.
- If You Are Out To Describe The Truth, Leave Elegance To The Tailor.
- >-
  O man you are busy working for the world, and the world is busy trying to turn you out.
- >-
  While children are struggling to be unique, the world around them is trying all means to make them look like everybody else.
- >-
  These Capitalists Generally Act Harmoniously And In Concert, To Fleece The People.

Going Further

There are many other options available in yq itself, if you have the time you can read about in yq’s documentation and implement as many of them as possible.

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