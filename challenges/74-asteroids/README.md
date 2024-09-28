Coding Challenge #74 - Asteroids
Build a clone of the 1979 arcade game.
John Crickett
Sep 28, 2024

Coding Challenge #74 - Asteroids

This challenge is to build your own version of the classic arcade game Asteroids. Asteroids, which was was first released in 1979, sees the player controlling a spaceship in an asteroid field. The objective of the game is to destroy the asteroids and the occasional flying saucer by shooting them.

The player dies when they collide with either an asteroid or the flying saucer, when all three lives are gone the game is over. The game gets harder over time as the number of asteroids increases. Given how limited computers were in 1979 the graphics are pretty simple, for example:

Or for those of you who want automated test, until I add them you can check out codecrafters.io and you can get 40% off as a Coding Challenges reader plus it helps support Coding Challenges.
The Challenge - Building Your Own Asteroids Game

In this coding challenge we’re going to build a clone of the video arcade game Asteroids. If you haven’t played it before, a quick Google search will provide several online options. Give it a go.
Step Zero

In this step, pick the programming language and development environment you’re going to use. Consider trying something different - this would be a great project to try a frontend stack if you’re a backend developer and vice versa.

If you’re from a data engineering or site-reliability engineering background you could leverage your knowledge of Python with PyGame or Go with Ebitenegine. Rustaceans can check out are we game yet for useful crates.

Asteroids is relatively simple and as such, it’s a great platform for learning a new technology, or programming language.

Step 1

In this step your goal is to create the game screen ready to start the game. Typically this is a simple blank black screen, with a button saying “start new game”. You might like to add the title of the game too.

Step 2

In this step your goal is to enable the player to start a new game. When the game starts their ship should be in the middle of the screen and asteroids should be moving across the screen.

For this step render the ship and the asteroids. The asteroids should move across the screen from one side to the other. When they go off the screen at one edge have them ‘wrap’ around and come back on the opposite edge.

Step 3

In this step your goal is to allow the user to control their ship. The should be able to change the direction it faces and apply some acceleration to the ship in the direction it is facing. Once the ship is moving it should keep moving in that direction. The speed should decrease slowly over time, unless new acceleration is applied.

Like the asteroids, the ship should ‘wrap’ around the screen.

Step 4

In this step your goal is to allow the player to shoot bullets out of the front of their ship and have the bullets travel in a straight line.

Once that works, add collision detection. When an asteroid is hit it should split into two pieces that move faster. Asteroids can usually be split three times before they are fully destroyed.

Step 5

In this step your goal is to add scores. Usually the smaller the target the high the score value. Show the score at the top of the screen.
Going Further

You can take this further by adding:

    A high score table

    some of your own gameplay

    Adding features from the sequel to Asteroids, Asteroids Deluxe.

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John