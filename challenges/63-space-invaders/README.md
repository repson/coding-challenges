Coding Challenge #63 - Space Invaders
This challenge is to build your own version of space invaders.
John Crickett
Jun 01, 2024

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 56,451 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

Coding Challenge #65

This challenge is to build your own version of space invaders.

Space Invaders dates back to 1978. It was the first game that fixed the shooter - the player’s character - in one part of the screen and had waves of enemies (aliens) attack the player.

It looks something like this:

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building Space Invaders

Space invaders is a relatively simple game, the gameplay has the player moving their ‘ship’ horizontally across the bottom of the screen and firing at aliens above. There are some bases for the player to take cover underneath.

In the original version the aliens begin in five rows of eleven that move left and right as a group, shifting down the screen each time they reach a screen edge. The player wins by shooting all of the aliens.

As the aliens move across the screen they occasionally drop bombs which fall towards the player and either damage the bases the player has or kill the player, taking one of their lives. The player’s shots also damage the bases.

The player has three lives and the game ends when either they run out of lives or the invaders reach the bottom of the screen.

Step Zero

In this step, pick the programming language and development environment you’re going to use. Consider trying something different - this would be a great project to try a frontend stack if you’re a backend developer and vice versa.

If you’re from a data engineering or site-reliability engineering background you could leverage your knowledge of Python with PyGame or Go with Ebitenegine. Rustaceans can check out are we game yet for useful crates.

Space invaders is relatively simple and as such, it’s a great platform for learning a new technology, or programming language.

You could create your own graphics for the game or there are some on opengameart.org that you can use.

Step 1

In this step your goal is to create the initial game screen, ready for the game to start.

For this step draw the top info bar that contains the score and number of lives remaining at the top of the screen and the player, their bases and the ‘ground’ at the bottom of the screen. It should look something like this:

Step 2

In this step your goal is to display the aliens. The original game had five rows of eleven that were evenly spaced. You could go for that or be creative.

This about how you implement them as you’re going to need to move them all in unison, but also be able to detect collisions individually and remove them individually when the players shots hit them.

Step 3

In this step your goal is to make the aliens and player move. The player should respond to the users keyboard input, moving left or right only, between the left and right edges of the playing screen.

The aliens should move left to right across the screen, stepping down every time they touch the edge of the screen. They should also move a little faster each time they step down the screen.

Step 4

In this step your goal is to have the aliens and player shoot. The aliens should drop a bomb that moves down the screen towards the bottom occasionally. The player should shoot when the player presses the ‘shoot’ button.

You should also now handle collisions between the shots/bombs and the aliens/bases/player updating the score and damage as appropriate. Don’t forget to detect the aliens reaching the bottom of the screen.

Step 5

In this step your goal is to handle the end game conditions, perhaps displaying ‘Game Over’ and providing the user with the option to start a new game.

Going Further

You can take this further by adding in the mystery ship that flies across the top of the screen occasionally.

Another great option is to add some music and have it speed up every time the aliens speed up.

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