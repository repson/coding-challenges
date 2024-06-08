Coding Challenge #64 - Spotify Playlist Backup Service
Build a service to backup and (optionally) restore Spotify playlists.
John Crickett
Jun 08, 2024

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 57,153 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

The Challenge - Building A Spotify Playlist Backup Tool

This challenge is to build your own Spotify backup tool. It’s inspired by my kids who wanted to ensure they can backup and move their playlists that they’ve spent ages curating. They’re not the only people who had this problem and we’re not the first to solve it.

The challenge is perfect for frontend developers. It focuses on using Spotify’s API to interact with the Spotify service to build a client that can download a user’s playlist.

If you’re not a frontend dev and don’t fancy learning some frontend, you can still use the Spotify’s API from your favourite stack.

So whilst, this challenge is aimed at all those who have been asked for a more frontend focused challenge, you can still build this as a command line application if you prefer.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

Step Zero

Please set up your IDE / editor and programming language of choice.

After that navigate to Spotify’s website and create an account if you don’t already have one. Once you’ve done that head over to the Developer Website.

You can use the API without registering an app, but we’re going to access some personal data (our profile and some public playlists) so we’ll need to register an application.

Click on the Create app button or link to do so:

Enter some sensible values for the app (I’ve reused the app from the build your own Spotify Client Coding Challenge:

Then click on the button to create it!

Step 1

In this step your goal is to authenticate with the Spotify API. To backup public playlists you don’t need to be logged in as the user, so you can use the client id and secret you’ve created in step 0. Don’t forget to ensure they are stored securely.

Spotify offer several options for authentication. You’ll find details of how to do this on in their documentation here.

Be sure to test your authentication code works - perhaps use the supplied credentials to try one of the API calls.

Step 2

In this step your goal is to be able to download a public playlist using the Spotify Web API’s playlist functionality. For this coding challenge I suggest you get the artist, album, track name. Feel free to add anything else you think would be useful.

Step 3

In this step your goal is to create a UI that will get the playlist id from the user and then use that to fetch the playlist from Spotify. Something like this:

Step 4

In this step your goal is to export / download the public playlist as a CSV (or zipped CSV if it’s large).

Step 5

In this step your goal is to allow a Spotify user to log in as themselves and back up all of their playlists.

They should then be able to download / export all their playlists, not just the public ones.

Going Further

You could take this further by:

    Extending it to support exporting playlists from other music services.

    Providing a tool to upload / create the same playlist in Spotify and/or another music service, making it easy to move between them.

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