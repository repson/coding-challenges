Coding Challenge #73 - Text Editor
Build your own micro version of vim.
John Crickett
Sep 14, 2024

Coding Challenge #73 - Build Your Own Text Editor

This challenge is to build your own terminal based text editor - think of it as a mini version of Vim, Ed or Nano.

There’s been a resurgence in interest in terminal-based text editors recently as software engineers adopt them over IDEs. This is reflected in the development and interest in new alternatives to existing editors, i.e. Neovim.
If You Enjoy Coding Challenges Here Are Three Ways You 

The Challenge - Building A Text Editor

In this coding challenge we’re going to build a simple terminal-based text editor.
Step Zero

This is software engineering so we’re zero-indexed and for this step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor of choice and programming language of choice. If you’re and IDE user who is feeling brave why not take this coding challenge as a chance to try writing software in a terminal-based editor such as Vim? You can learn Vim with the Vim Adventures.

Step 1

In this step your goal is to create a program that starts up and allows the user to quit when they press q.

The program should:

    Read from stdin unbuffered - so you’re not waiting for the user to press return.

    Disable the default echoing of input to stdout.

    Disable output processing by the terminal.

    Disable all handling of CTRL-C, CTRL-Z, CTRL-M, CTRL-S, CTRL-Q, CTRL-V.

This is commonly known as setting the terminal into raw mode as opposed to cooked mode - you can read more about terminal modes here.

Step 2

In this step your goal is to have your editor clear the screen when started and position the cursor at the top left of the screen.

After that have it also clear the screen and reposition the cursor on exiting the editor.

Finally once that’s sorted, draw a vertical line of of characters down the lefthand side of the screen. Like Vim does. You could use ~ just like Vim or another character.

To complete this step you will need to know about terminal control sequences.

Step 3

In this step your goal is to allow the user to to move the cursor around the screen. You could define your own keys for this or use the Vim ones:

    h - move cursor left

    j - move cursor down

    k - move cursor up

    l - move cursor right

Again refer to the terminal control codes for how to do this. Don’t forget to check the bounds and ensure the cursor doesn’t move off screen.

Step 4

In this step your goal is to allow the user to enter some text. You should do this by having a ‘control’ mode and and ‘editor’ mode and allowing the user to switch with the escape key for ‘control’ mode and escape followed by i for ‘editor’ mode.

Think about how to handle storing the lines of text efficiently so you can render them efficiently.

Step 5

In this step your goal is to support opening and saving files. The user should be able to provide your editor with a filename on startup, i.e.: ccvim text.txt and have it open the file.

You should them allow the user to enter a control sequence, i.e. for Vim we would switch to the ‘control’ mode equivalent and enter the sequence :w to save or :wq to save and quit.

Going Further

You could take this coding challenge further by adding support for:

    Searching within the document and then adding find and replace.

    Handling scrolling when the document becomes longer than the number of lines (or columns) on the screen.

    Handling tabs.

    Supporting the arrow and page up/down keys.

    Adding a status bar that shows some useful information about the file being edited.

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John