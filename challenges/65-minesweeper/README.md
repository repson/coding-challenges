Coding Challenge #65 - Minesweeper
Level up as a software engineer by building a classic game.
John Crickett
Jun 22, 2024

Coding Challenge #65

This challenge is to build your own version of the game Minesweeper.

Minesweeper is a logic puzzle game that I first came across when I got my first Windows PC, running Windows 95. The game has been around longer than that, Microsoft shipped a version in the early 1990s and some claim the origins date to 1983.

Recently I’ve been reminded about Minesweeper when my eldest son asked about coding his own version. So this Coding Challenge is for him.

It looks like this:

Made using: minesweeper.online.
If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

Would You Like To Know How To Become A CTO In Under 3 Years?

Then you might like to check out my friend Adelina Chalmers new Udemy course: How to become a CTO in under 3 years – 5 practical ways!

The Challenge - Building Your Own Minesweeper Game

The rules of Minesweeper are relatively simple. The board is divided into a grid, with mines randomly distributed in the grid cells. To win, you need to open all the cells that you can without triggering a mine. You mark off where the mines are.

The number on a cell shows the number of cells adjacent to it that contain mines. Using this information, you can determine if a cell is safe or if it contains a mine. Cells believed to contain a mine can be marked with a flag.

Step Zero

In this step, pick the programming language and development environment you’re going to use. Consider trying something different - this would be a great project to try a frontend stack if you’re a backend developer and vice versa.

If you’re from a data engineering or site-reliability engineering background you could leverage your knowledge of Python with PyGame or Go with Ebitenegine. Rustaceans can check out are we game yet for useful crates.

Minesweeper is relatively simple and as such, it’s a great platform for learning a new technology, or programming language.

You could create your own graphics for the game or there are some on opengameart.org that you can use.

Step 1

In this step your goal is to draw the grid for the initial game state. It should look something like this:

The left hand number - 99 here - shows the number of mines left to find and the right hand number is the time in seconds since starting the game.

Step 2

In this step your goal is to reveal the mine / safe state after a cell is clicked on. That should look something like this:

Step 3

In this step your goal is to detect hitting a mine, reveal the mines not found and offer to play again. For example:

Opting to play again should re-start the game.

Step 4

In this step your goal is to detect a win. A win is when all the mines are found. For example:

Going Further

You can take this further by offering different size playing areas, the bigger the area the harder the game. You could also add a league table so people can record their best scores.

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