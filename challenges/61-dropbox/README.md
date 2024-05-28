Coding Challenge #61 - Dropbox
This challenge is to build your own version of Dropbox.
JOHN CRICKETT
MAY 11

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 54,371 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #61 - Dropbox

This challenge is to build your own version of Dropbox.

Dropbox is a cloud file hosting service. It’s been around since 2007 when it heralded a new way of synchronising files between different people and the different devices that we used.

Apparently the founder Drew Houston came up with the idea after repeated forgetting his USB flask drive (remember them?) when he was a student at MIT.

Dropbox is a case study I often use when talking about the value of MVPs and how you can create them without a massive investment. The reason for that is the Dropbox MVP was a mocked up video because there were significant technical hurdles to overcome to actually build Dropbox in those days.

These days, you can build this project in a weekend. Tech has come a long way in the last 17 years!

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building a Dropbox Clone

For this challenge, if you are backend focused (like me) you could just build an API to upload and download files. If you’re feeling more adventurous you could build the frontend too, creating a UI that allows users to sign up, login and upload and download files.

The ultimate however would be to build both, along with some automated testing and then create a CI/CD pipeline to deploy the whole thing as a service to one of the cloud providers. It’s a great opportunity to add some real-world Infrastructure-as-Code experience to your skillset.

If you fancy doing that don’t forget AWS offer a free tier, Azure offers a similar set of services that are free (with limits) for 12 months and Google Cloud offers 20+ free products for all customers (with limits). Other cloud provider are available - wouldn’t it be cool if one sponsors Coding Challenges?

Step Zero

In this step pick your programming language and IDE you’re going to use and you get yourself setup with a nice new ‘ccbox’ project.

Step 1

In this step your goal is to create an API (and frontend if you’re going that way) that will allow a user to sign up and login.

Getting user sign up and authentication right isn’t easy. If you’re going to roll your own do some careful reading around the challenges and look at the lessons you’ll learn from the build your own password cracker coding challenge.

It would be perfectly reasonable to defer the complexity of user authentication and instead integrate social login.

Step 2

In this step your goal is to allow a logged-in (authenticated) user to be able to see the folder structure for their virtual drive.

You should allow them to create one or more folders at the top level. Each folder should be able to contain one of more folders. If you want some inspiration for what this looks like you could sign up to Dropbox or Google Drive and try them out.

Step 3

In this step your goal is to upload one or more files (or folders and their contents) to a folder via the UI (or API).

Step 4

In this step your goal is to allow the user to create sharable links to a file or folder in their drive.

They should be able to create a link that only they can access or a link that is public (accessible without authentication).

Step 5

In this step your goal is to write a tool to sync a local folder on their local machine with their online account.

Initially you might want to make it a CLI program, but eventually you could turn it into a background service that runs on startup. Either option should have some configuration that allows you to specify which local folder is the root.

It should poll the remote ‘drive’ at a set frequency and either upload a new local file (or new changes to an existing one) or download remote files that are newer / have changed more recently than local files.

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