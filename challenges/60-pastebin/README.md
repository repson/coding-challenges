Coding Challenge #60 - Pastebin
This challenge is to build your own version of a Pastebin.

JOHN CRICKETT
MAY 04, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 53,549 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #60 - Pastebin

This challenge is to build your own version of a Pastebin. A pastebin is a text storage site that allows users to store plain text in order to share it with other people.

The most well known version is of course the eponymous pastebin.com.

Some News - I’ve Launched a Podcast for Software Engineers!
I’ve launched a podcast for software engineers! 🎙️

It’s called Coding Chats and it focuses on software engineering for the 99% of software engineers who aren't working in big tech companies.

You can find it on YouTube, Spotify, Apple Podcasts and Google Podcasts.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building Your Own Pastebin
A pastebin is a relatively simple concept, you’ve probably used one, for example GitHub Gists are one.

If you haven’t then have a quick play with the Mozilla Community Pastebin as an example of a nice user-friendly version.

Step Zero

Try something different this week! If you usually develop in an IDE, give Vim a go. If you use Vim, perhaps check out an IDE. You probably won’t want to change, but it’ll help if you have to pair with or work with other members of your team who work differently to you.

And of course every software engineer should know the basics of using Vim because it’s the editor that’s most likely to be on a server when you need to edit some config for an emergency prod fix. Just don’t forget to document what you did and apply the change to the source code once the immediate issue is resolved.

Step 1

In this step your goal is to create a site that lets a user paste some content into it and submit the content. When they do that, they should get back a unique URL for the content. So a simple GUI like this:


Then when they press submit, generate a unique id for it. One way to do that is to have some form of atomic counter, another is to generate a hash from the content. Either way return to the user a new unique URL, i.e. https://ccpastebin.fyi/fe45swq.

Step 2

In this step your goal is to save the pasted content to a database and then show it when the user visits the unique URL you presented in Step 1. Ideally extend the submission so that after the snippet is submitted and stored, the user is redirected to the snippet URL.

Think carefully about the different types of database you could use and consider the tradeoffs you’re making between them. I’m using database in the broadest sense here, that is an organised collection of structured data.

Step 3

In this step your goal is to allow the user to delete the pasted snippet. Present a delete button on the page they see via generated URL. If clicked, check they meant to delete it, then if so, delete the snippet.

Ensure you handle someone visiting the URL after it has been deleted and trying to delete the content more than once.

Step 4

In this step your goal is to allow the user to specify an expiry time when pasting into the pastbin. If someone tries to access the URL after the expiry time it should no longer be available.

Give some thought to how you implement expiry, there’s a couple of different approaches you could take and they’ll impact the potential cost of running the solution as a service. This is a good exercise to practice you system design skills on.

If you need some hints, consider Step 5 of the build your own Redis coding challenge.

Step 5

In this step your goal is to deploy your pastebin to a cloud service. You should do this with some form of CI/CD and IaC, depending on the cloud solution you use. Your goal is to make it repeatable and automated so that when you push your change to your GitHub (or equivalent) the code is tested and deployed automatically.

Bonus - Step 6

In this step your goal is to allow the user to specify a formatting option, so they can specify that the pasted snippet is for example Python. Then when the user visits the URL you should format as Python code, providing keyword highlighting etc. For a good example of how this should work check out the Mozilla Community Pastebin.

Going Further

If you want to take this further you could add:

The ability to edit a snippet.

The ability to view the raw snippet.

An easy ay to copy the snippet with a single mouse click.

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