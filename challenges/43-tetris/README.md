Coding Challenge #43 - Tetris
This challenge is to build your own version of the famous computer game Tetris.
John Crickett
Jan 6, 2024

Tetris hit the news this week with reports that a US teenager Willis Gibson claims to be the first person to beat Tetris by reaching level 157 at which point the game apparently crashed.

With that in mind and amid many request for more Coding Challenges related to computer games, this challenge is to build your own version of the famous computer game Tetris.

The requests make sense; for as long as I have been interested in programming, programmers have been learning by building computer games. Many of us started by building our own Pong and over time progress to either copying other more complex games, building our own game from scratch or customising existing games.

I certainly spent a lot of my childhood cloning Sensible Soccer and the Alien Breed franchise before moving on to writing ‘AI’ based bots for Quake, Quake 2 and Quake 4.

The Challenge - Building Your Own Tetris

Tetris is a computer game that has been around since 1985 and has appeared on many platforms since then. It is one of the best selling computer games of all time.

Fundamentally the game is quite simple the player completes horizontal lines at the bottom of the screen by fitting in shapes that descend from the top of the screen. Completed lines disappear, earning the player points. The game ends when the uncleared lines reach the top of the screen.

Step Zero

In this step you decide which programming language and development environment you’re going to use. This would be a great project to try a frontend stack if you’re a backend developer and if you’re a frontend developer perhaps try building a desktop application.

If you’re from a data engineering or site-reliability engineering background you could leverage your knowledge of Python with PyGame or Go with Ebitenegine. Rustaceans can check out are we game yet for useful crates.

Tetris is a relatively simple game to build and as such, is a great platform for learning a new technology, or programming language.

Step 1

In this step your goal is to create your welcome screen. This screen should give the player the option to start a game or access some basic instructions on how to play the game - i.e. the controls and perhaps an introduction to the gameplay. You can leave starting the game until the next step, but you should render the help screen as part of this one.

You could even include some high scores. Something like the following:

Step 2

In this step your goal is to allow the player to start a game (by clicking on Play) and, when they do so render a playing screen, which might look something like this:

The board is on the left and the score and a Quit button on the right. The initial board in Tetris is 10 blocks wide and 20 blocks high. It’s often rendered with a block based border like the grey blocks in the following image:

Step 3

In this step your goal is to add the pieces, known as ‘tetrominoes’, to the game and have them appear at the top of the screen and ‘fall’ to the bottom. There are seven tetrominoes which look like:

For versions of Tetris that support colour these are the ‘standard’ colours. Alternately you can go fully retro and render the game in black and white/black and green. Once the lowest block of a tetromino reaches the bottom on the board it should stop falling.

The order that the tetrominoes are added to the board is random.

Step 4

In this step your goal is to allow the player to control the tetrominoes as they fall. There are several things a player can do:

    Move the tetromino left or right.

    Rotate the tetromino clockwise or anti-clockwise.

    Accelerate the tetromino downwards.

    Hard drop the tetromino (immediately move it as far down the board as possible).

Step 5

In this step your goal is to remove completed rows from the bottom of the screen and update the scoreboard. Usually removing multiple levels in a single action scores a more that removing a single row or the sum of the single rows, i.e. one row might be worth ten points, two rows might be worth 30 points and three rows 50 points.

The second part of this step is to end the game when the board is ‘full’ - that is, no more pieces can be added at the top of the board. When a games is complete allow the player the option to restart the game.

Congratulations you’e built your own Tetris!

2 Other Ways I Can Help You:

    I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

    I have some courses available:

        Become a Better Software Developer by Building Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

        Build Your Own Shell (Go Edition) which guides you through solving the Shell Coding Challenge in Go.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John