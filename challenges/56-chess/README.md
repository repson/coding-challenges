Coding Challenge #56 - Chess
Build your own chess game and level up your DSA skills!

JOHN CRICKETT
APR 06, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 51,003 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #56 - Chess

This challenge is to build your own chess program. The game chess has held a fascination for many people for hundreds of years, so much so that the first automated chess playing machine, “The Mechanical Turk” was built in 1770!

However, The Turk was a fraud. There was in fact a human player hidden inside the machine who was operating it. This artificial artificial intelligence inspired the name for Amazon’s crowdsourcing market place; Amazon Mechanical Turk.

The idea was copied a few times, then in 1941 real algorithmic attempts to play chess began and soon afterwards chess became considered a big challenge for AI. This lead to a focus on developing ‘AI’ to play chess and ultimately to IBM developing Deep Blue.

Deep Blue was the first computer based chess player to win a game against a world champion in 1996 and subsequently the first to win a match in 1997. It’s estimated that Deep Blue cost around 10 million USD to develop! It wasn’t exactly portable either, being a supercomputer that took up two full server cabinets!

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building A Chess Game
In this coding challenge we’ll build a chess game. It’s a challenge you could do with a web-based UI, a desktop or mobile UI or even a terminal based UI. The choice is yours.

What makes this an interesting challenge is the complexity of a game of chess. It’s widely agreed that to play well you need to be thinking at least five moves ahead. Doesn’t sound much, but with 30 legal moves per piece, there are a quadrillion possibilities to consider. If you could evaluate 10 million possibilities a second, it would take three years to evaluate them all!

Chess is a great testing ground for your data structure and algorithm skills. Here’s why it’s so key.

Picking the right data structure to represent the board is crucial to the performance of the move generation and evaluation. Often bitboards are used to represent the board and Huffman encoding is used to compact data for long-term storage (you can learn move about Huffman encoding in the build you own compression tool challenge).

Chess programs usually consider the possible chess moves as a game tree, the root being the initial state of the game and every node representing a game state. The next move to make is normally determined by examining the tree. In theory if you generate the entire tree you can ‘solve’ the game. But these tree’s get big fast, for example the simple games tic tac toe ends up with 255,168 leaf nodes!

So selecting the right algorithm(s) to explore the tree with a key to making a move in a reasonable amount if time - we don’t want to wait weeks or months between moves!

Some algorithms to explore are minmax, alpha-beta pruning, and Monte Carlo tree search.

Step Zero

In this step you decide which programming language and development environment you’re going to use. You’ll need to be able to represent the chess board and pieces, but the heart of this challenge is building the chess engine.

Step 1

In this step your goal is to display a chess board and render the pieces in the starting positions.

Check out Chess.com’s Learn Chess section if you need inspiration or you aren’t familiar with chess.

Step 2

In this step your goal is to validate possible moves for each pieces on the board. This will be a key part of the move generation that you’ll need to develop a computer player.

My personal approach to this would be to use test driven development (TDD) to develop code to generate and validate all the possible moves for a piece based on it’s type, location on the board, and the other pieces around it.

Step 3
In this step your goal is to allow the player and the computer make moves in turn. Each move should be valid - reject an invalid move by the human player.

For the computer player, keep it simple for now, create a list of all the possible moves the computer can validly do and pick one at random.

Step 4

In this step your goal is to check for a win. Extend the game you have developed so far. After each move check the if the winning condition has been met and if so end the game.

Step 5

In this step your goal is to build you chess engine. Now it’s time to combine the move generation and validation you have to generate the game tree and then use one of the algorithms to prune it so you can look ahead several moves to create a computer player that can win games.

Going Further

There are a lot of optimisations that have been done to further improve the performance of chess engines. I’d suggest reading around them and implementing those that interest you or that offer some useful learning.

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