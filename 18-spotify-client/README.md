Coding Challenge #18 - Spotify Client
This challenge is to build your own Spotify Client using the Spotify API.
John Crickett
Jul 15, 2023

If you’re a software developer I’m sure you’ve heard of Spotify and have an account. If not you can sign up for a free one on their website.
The Challenge - Building a Spotify Client

This challenge is perfect for the frontend developers. It focuses on using Spotify’s API to interact with the Spotify service to build an an online client and uses their Web Playback SDK to support playback.

If you’re not a frontend dev and don’t fancy learning, you can still use the Spotify’s API from your favourite stack to create, edit and play playlists including selecting playback devices.

So whilst, this challenge is aimed at all those who have been asked for a more frontend focused challenge, you can still build this entirely as a command line application if you prefer.

Personally I built my example in JavaScript with React. If I started over I’d use TypeScript (Spotify released the TypeScript SDK, just after I finished writing).
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

So to help with that I’ve just launched an online cohort based course: Coding Challenges Live: Redis Edition!

In the course we’ll go through all of the above over a three week period as we tackle building a Redis Clone. You can find out more on the Coding Challenges Live: Redis Edition page.

As a reader of the Coding Challenges newsletter I’m offering you a 25% discount, so the course will cost you just $375 instead of the regular price of $500. Use the code: CODINGCHALLENGES to take advantage of this offer on the Coding Challenges Live: Redis Edition page.

Step Zero

Please set up your IDE / editor and programming language of choice.

After that navigate to Spotify’s website and create an account if you don’t already have one. Once you’ve done that head over to the Developer Website.

You can use the API without registering an app, but we’re going to access some personal data (our profile and some public playlists) so we’ll need to register and application.

Click on the Create app button or link to do so:

Enter some sensible values for the app:

Then click on the button to create it!
Step 1

In this step your goal is to authenticate the user of your client. Spotify offer several options for this. You’ll find details of how to do this on in their documentation, for a Single Page Web App, they recommend using the authorisation code with PKCE.

Once you’ve authenticated check you can access the user’s profile by calling the /me endpoint. Check the documentation for the User Profile Endpoint to see what data is returned and how to use the authorisation token.

Check you’re getting back the id field you expect to verify that you’ve authenticated correctly.
Step 2

In this step your goal is to fetch the authenticated users playlists and display them to the user.

To do this you’re going to use the Get Playlist API. I then chose to render out the title of the playlist and the provided image, here’s what that looked like for one of mine.

If you’re a fan of the band, they performed great in Manchester on this tour! If you’re not, hopefully you’re seeing a playlist of yours that is more to your taste.
Step 3

In this step your goal is to allow the user to select a playlist then play and pause that playlist. To do this you will need to add the Web Playback SDK (assuming you’re building a frontend application).

You will need to ensure you have the right scopes set for your authentication, once you done that you should be able to view a player that will look something like this:

If you see an error message that “Instance not active. Transfer your playback using your Spotify app” you will need to check the Spotify App and switch device to the Wb Playback SDK.
Step 4

In this step get the device_id of your client and use the Player API to transfer playback automatically to your client.
Taking It Further

You can take this one further by looking at Spotify’s own Web Client and the cloning any other features you fancy.

If you’ve enjoyed reading Coding Challenges, please consider referring a friend, just click the button below:

Refer a friend

Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.
Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John