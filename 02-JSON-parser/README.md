Coding Challenge #2 - Build a JSON Parser
John Crickett
Mar 25, 2023

This weeks challenge is to build your own JSON parser.

Building a JSON parser is an easy way to learn about parsing techniques which are useful for everything from parsing simple data formats through to building a fully featured compiler for a programming language.

Parsing is often broken up into two stages: lexical analysis and syntactic analysis. Lexical analysis is the process of dividing a sequence of characters into meaningful chunks, called tokens. Syntactic analysis (which is also sometimes referred to as parsing) is the process of analysing the list of tokens to match it to a formal grammar.

You can read far more about building lexers, parses and compilers in what is regarded as the definitive book on compilers: Compilers: Principles, Techniques, and Tools - widely known as the “Dragon Book” (because there’s an illustration of a dragon on the cover).
The Challenge - Building a JSON Parser

JSON (which stands for JavaScript Object Notation) is a lightweight data-interchange format, which is widely used for transmitting data over the Internet. It is formally defined by the IETF here: https://tools.ietf.org/html/std90 or there’s a simpler graphical representation here: https://www.json.org/json-en.html

Step Zero

This is software engineering so we’re zero-indexed and for this step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that you can download some simple test data for the JSON parser from my DropBox.

Step 1

In this step your goal is to parse a valid simple JSON object, specifically: ‘{}’ and an invalid JSON file and correctly report which is which. So you should build a very simple lexer and parser for this step.

Your program should report to the standard output stream a suitable message and exit with the code 0 for valid and 1 for invalid. It is conventional for CLI tools to return 0 for success and between 1 and 255 for an error and allows us to combined CLI tools to create more powerful programs. Check out Coding Challenge #1 for more on combing simple cli tools.

You can test your code against the files in the folder tests/step1. Consider automating the tests so you can run them repeatedly as you progress through the challenge.

Step 2

In this step your goal is to extend the parser to parse a simple JSON object containing string keys and string values, i.e.:

{"key": "value"}

You can test against the files in the folder tests/step2.

Step 3

In this step your goal is to extend the parser to parse a JSON object containing string, numeric, boolean and null values, i.e.:

{
  "key1": true,
  "key2": false,
  "key3": null,
  "key4": "value",
  "key5": 101
}

You can test against the files in the folder tests/step3.

Step 4

In this step your goal is to extend the parser to parse a JSON object with object and array values, i.e.:

{
  "key": "value",
  "key-n": 101,
  "key-o": {},
  "key-l": []
}

You can test against the files in the folder tests/step4.

Step 5

In this step your goal is to add some of your own tests to ensure you’re confident that your parse can handle valid JSON and will fail with useful error messages on invalid JSON.

Once you’re confident your parser is done and well tested you can try running it against the test suite here: http://www.json.org/JSON_checker/test.zip

Share Your Solutions!

Even though this is only the first coding challenge I’ve already been asked to share model solutions in as many programming languages as possible - which is an awesome idea, but I just don’t have the time and don’t know even half the programming languages out there so I’d like your help!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message via Twitter or LinkedIn or just post about it there and tag me.

I’ll take a look at every solution and I’ll mention the best solution in the follow week’s newsletter.
Solutions to Coding Challenge #1

There were a number of solutions to the first coding challenge shared with me, the one that stood out to me was Mikhail Golubitsky’s Ruby entry which you’ll find here:

https://github.com/golubitsky/explorations/tree/master/coding_challenges_crickett/01_wc

I loved seeing how this would be handled in a language that I’ve never used and the fact that he added a set of automated tests.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter https://twitter.com/johncrickett, LinkedIn https://www.linkedin.com/in/johncrickett/ or through SubStack