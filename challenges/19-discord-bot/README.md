Coding Challenge #19 - Discord Bot
This challenge is to build your own Discord Bot.
John Crickett
Jul 22, 2023

Discord is an instant messaging and VoIP social platform. You can communicate on it using voice calls, video calls and text messages. It’s divided up into a series of communities know as servers.

Discord launched in 2015 and quickly began to replace the use of IRC in some communities - particularly amongst gamers and esport communities. Nowadays it’s widely used for all sorts of communities.

Which makes it an ideal thing to build a bot for. Something that can automate some of the tasks that might be needed on a server, such as welcoming new users.

Share
The Challenge - Building a Discord Bot

In this challenge we’re going to look at building a simple bot that could help users of a server, like the Coding Challenges server find what they’re looking for.

By the way if you love(d) IRC there is a challenge to build your own IRC Client. You could use that as a basis to build this challenge as an IRC bot if you prefer.

Before We Go On; Some News

These Coding Challenges are a great way to become a better coder, but there’s more to software development than just coding. You also need to know how to:

➡️ Break a project down into stages.

➡️ Select a tech stack for the project.

➡️ Document your decisions and explain them (ideally with Architecture Decision Records).

➡️ Write automated tests and have them run in a CI pipeline.

➡️ Review code (and have your code reviewed).

➡️ Understand concurrency - async versus threads.

➡️ Optimise for performance.

➡️ Communicate and collaborate with others in a team.

So to help with that I’ve launched an online cohort based course: Coding Challenges Live: Redis Edition!

In the course we’ll go through all of the above over a three week period as we tackle building a Redis Clone. You can find out more on the Coding Challenges Live: Redis Edition page.

As a reader of the Coding Challenges newsletter I’m offering you a 25% discount, so the course will cost you just $375 instead of the regular price of $500. Use the code: CODINGCHALLENGES to take advantage of this offer on the Coding Challenges Live: Redis Edition page.

Step Zero

In this step you decide which programming language and IDE you’re going to use and you get yourself setup with a nice new project: disdaccbot.

After that you’ll need to visit the Discord Developer Portal and Create an Application:

Next you need to configure a bot user.

Grab your token and save it somewhere safe. Find the “MESSAGE CONTENT INTENT” setting and enable it.

Then set the permissions for your bot:

Then head to the OAuth2 / URL Generator and the scopes and permissions as so:

After that, copy the generated URL that’s just off the screen at the bottom. Pop it in your browser and give your bot permission - ideally to a private test server.

Once all that’s done you should be ready to start coding up your bot! You can dive right in, or you can take some time and go through Discord’s tutorial on building a Discord App.

Step 1 - Hello, World!

In this step your goal is to create you bot and have it connect to the server. Once you’ve done that have it listen for messages and respond to the greeting “Hello” with it’s own greeting that include the person’s name:
Step 2

In this step your goal is to provide a random quote when someone asks for one. We can get some test quotes from the API at dummyJSON.

We’re going to have our bot respond to the message !quote with a random quote. To make it more interesting we’re going to fetch the quote from an external API. We’ll use https://dummyjson.com/ for that.

Check the documentation there for how to use the /quotes endpoint to fetch just one random quote from the 100 that are available.

Once you have it working, it should look something like this:

Your quote may vary - it’s random after all! 😇

Step 3

In this step your goal is to have the bot provide a list of challenges from the Coding Challenges back catalogue. You can download a JSON document of the past challenges from my Dropbox here.

Then extend you bot to respond to the command !challenge with a random challenge as so:

Again, your challenge may vary - it’s random after all!

Step 4

In this step your goal is to allow new challenges to be added to the catalogue of challenges. To do that you’ll add the command !add <challenge> and the command !list to list all the available challenges.

Once complete it should look like this for the first !list:

Then you should be able to add this Discord challenge and see it listed. The command to add a challenge should look like !add <challenge URL> and the bot should check the URL is a valid URL and that it refers to a valid challenge on the codingchallenges.fyi website. If so it should read the title of the challenge from the title tag of the HTML.

That should look like this for an invalid URL:

And like this for a valid URL:

Extra points for making the bot save the newly added challenge to your local copy of the catalogue so new additions are retained when the bot is restarted.

Step 5

In this step your goal is to host your bot somewhere where it can run 24/7/365 as if it were a production system. No this does not count:

I would suggest using the AWS Free Tier, you can setup a tiny EC2 instance for free. If you’re new to AWS I suggest checking out Guille Ojeda’s guide to creating a Self-healing, Single-instance Environment with AWS EC2.

You can then run your bot as a daemon, ensuring it continues to run is the terminal is closed and is automatically started on startup.

Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website.

Thanks and happy coding!

John