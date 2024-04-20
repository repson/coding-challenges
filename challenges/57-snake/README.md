
Coding Challenge #57 - Snake
This challenge is to build your own version of the classic game snake.

JOHN CRICKETT
APR 13, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 51,591 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #57 - Snake

This challenge is to build your own version of the classic game snake.

Many of us think of snake as one of the first games that was available on a mobile phone (it appeared on the Nokia 6110 in 1997). But snake goes back much further than that. It’s heritage dates back to 1976, with the first version of what was then called Worm written in 1978.

These days there are thousands of versions and it’s available for just about any device you care to try.

Ad: Do You Need Help Learning To Code or Becoming a Backend Developer?
I’ve had a number of request for tutorials on learning Python, JavaScript or Go. I don’t have anything myself so I’ve partnered with boot.dev who teach you to become a backend developer using Python, JavaScript and Go.

If you use the code JOHNCRICKETT you’ll also get 25% off your first payment. It’s an affiliate link so you’ll also be supporting Coding Challenges if you sign up for boot.dev.

The Challenge - Building Snake

Snake is a simple game. The player controls a snake which move around the playing grid at a fixed speed. The goal is to eat food that appears at random locations on the grid.

For each item of food eaten the snake becomes longer and the player scores points. The game ends when the snake hits the edge of the game grid or it’s own body.

Step Zero

In this step, pick the programming language and development environment you’re going to use. Consider trying something different - this would be a great project to try a frontend stack if you’re a backend developer and vice versa.

If you’re from a data engineering or site-reliability engineering background you could leverage your knowledge of Python with PyGame or Go with Ebitenegine. Rustaceans can check out are we game yet for useful crates.

Snake is relatively simple and as such, it’s a great platform for learning a new technology, or programming language.

Step 1

In this step your goal is to draw the game grid and score display. That’s going to look quite simple, much like this:


Don’t forget to consider the size of the grid in both pixels and cells within the grid. For example the game screen might be 20 cells by 20 cells and each cell be 20 pixels by 20 pixels.

Step 2

In this step your goal is to draw the snake and have it move around the grid. You should decide where the snake will start for your version of the game. It could be in a corner, the centre or in a random cell. Play around and see what you think gives the best gameplay.

To do this you’ll have to create a game loop, in which you detect user input, update the game state and then render the state to the display. Every cell in the snakes body should ‘move’ to the board cell of the preceding body cell every turn. The simple way to do this is to remove the tail cell and add a new head cell.

Give the head of the snake a different colour so the user can recognise it. The snake’s body should be a number of cells long when the game starts. Try four initially but feel free to experiment.


Step 3

In this step your goal is to detect when the snake collides with the wall. At that point end the game and show the score. Offer the user the chance to play a new game.

If they decided to start a new game reset the game state and begin a new game.

Step 4

In this step your goal is to insert food at a random location on the game world. Once inserted the food should be rendered in the world and you will need to detect when it is eaten (a collision occurs between the head of the snake and the food) and then lengthen the snake and increase the score. On top of that you will remove the food from the screen and spawn a new item of food in a new random location.

Step 5

In this step your goal is to detect when the snake collides with itself. When it does so, end the game.

Going Further

There are several options you can explore to take this further:

Make it multiplayer - the original Nokia version was multiplayer to show off the IR port.

Add a high scores table that is saved between games and can record a users name.

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