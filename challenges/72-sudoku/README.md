Coding Challenge #72 - Sudoku
Build your own Sudoku game.
John Crickett
Aug 31, 2024

Coding Challenge #72 - Sudoku

This challenge is to build your own Sudoku game!

Sudoku has been around since the 19th century and has appeared in puzzle books since 1979! Back then it was often called Number Place. It became more popular in 1986 when it was published by a Japanese company under the name Sudoko.
If You Enjoy Coding Challenges Here Are Three Ways You

P.S. I’ve got a new YouTube channel!

I’m creating videos to help you develop a well rounded skillset - when you’re ready for a break from Coding Challenges you can work on your soft and leadership skills. It’s here: https://www.youtube.com/@johncrickett if you’d like to check it out!
The Challenge - Building A Sudoku Game

Sudoku is a logic based number-placement puzzle of Japanese origin. The objective of the puzzle is to fill a 9 × 9 grid with digits so that each column, each row, and each of the nine 3 × 3 boxes that comprise the grid contains all of the digits from 1 to 9.

The creator of the puzzle provides a partially completed grid, which for a well-posed puzzle has a single solution. That looks something like this:

The player ‘wins’ by solving the puzzle so that each square must contain a value that is unique to that row, column, and box.

Step Zero

In this step, pick the programming language and development environment you’re going to use. Consider trying something different - this would be a great project to try a frontend stack if you’re a backend developer and vice versa.

If you’re from a data engineering or site-reliability engineering background you could leverage your knowledge of Python with PyGame or Go with Ebitenegine. Rustaceans can check out are we game yet for useful crates.

Sudoku is relatively simple from the UI point of view and as such, it’s a great platform for learning a new technology, or programming language. Alternately it’s a good project to sharpen your algorithms skills on as you’re going to need to build a solver in order to generate valid, well-posed puzzles.

Step 1

In this step your goal is to draw the empty grid and allow the user to click on a cell and enter a digit from 0 to 9. They should also be able to clear a cell that they have entered.

Step 2

In this step your goal is to write a function to validate a solution is valid. I would tackle this using test-driven development (TDD). If you fancy learning TDD perhaps give it a go, if not, well don’t, it’s your coding challenge!

Step 3

In this step your goal is to implement a sudoku solver. You’re going to build a solver because it is a key part of being able to generate puzzles to solve. There are different ways to solve the Sudoku puzzle two common approaches are search with constraint propagation and search with backtracking.

Again I’d do this with TDD.

Step 4

In this step your goal is to generated a starting puzzle and display it to the player. They should then be able to solve the puzzle, with the following constraints:

    They cannot clear a cell that had a value set in the initial puzzle grid.

    They cannot enter any value except the digits 0 to 9.

They should then be able to enter a value into the cells that empty. They should also be able to clear a cell that they set.

Generating a playable board involves generating a solved board, then removing cells at random ensuring that the removal of the cells leaves you with a board that can still be solved and only has one valid solution. You’ll need the validation code and solver from steps 2 and 3 to do this.
Step 5

In this step your goal is to allow the user to check the validity of their solution, you should tell them if they’ve succeeded or not.
Going Further

There are many options for taking this coding challenge further. You could:

    Support killer sudoku.

    Add a timer so they can easily time themselves.

    Allow printing so they can take puzzles away to solve whilst without a computer/device.

    Create a mobile app.

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John