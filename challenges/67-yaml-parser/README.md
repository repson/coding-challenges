Coding Challenge #67 - YAML Parser
This challenge is to build your own YAML Parser.
John Crickett
Jul 06, 2024

Coding Challenge #67 YAML Parser

This weeks’ challenge is to build your own YAML parser.

Building a YAML parser is an easy way to learn about parsing techniques which are useful for everything from parsing simple data formats through to building a fully featured compiler for a programming language.

Parsing is often broken up into two stages: lexical analysis and syntactic analysis. Lexical analysis is the process of dividing a sequence of characters into meaningful chunks, called tokens. Syntactic analysis (which is also sometimes referred to as parsing) is the process of analysing the list of tokens to match it to a formal grammar.

You can read far more about building lexers, parses and compilers in what is regarded as the definitive book on compilers: Compilers: Principles, Techniques, and Tools - widely known as the “Dragon Book” (because there’s an illustration of a dragon on the cover).
If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building A YAML Parser

YAML (which stands for YAML Ain’t Markup Language) is a lightweight data-interchange format often used for configuration. Probably most notably for AWS CloudFormation and OpenAPI specifications.

It is defined by the public standard here: https://yaml.org/spec/

Step Zero

This is software engineering so we’re zero-indexed and for this step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor of choice and programming language of choice.

Step 1

In this step your goal is to parse the basic YAML building block, a key value pair, specifically: name: Coding Challenges and an invalid YAML file and correctly report which is which. So you should build a very simple lexer and parser for this step.

Your program should report to the standard output stream a suitable message and exit with the code 0 for valid and 1 for invalid. It is conventional for CLI tools to return 0 for success and between 1 and 255 for an error and allows us to combine CLI tools to create more powerful programs. You can learn more about combining CLI tools in the build your own wc Coding Challenge.

You can test your code against the files in the folder tests/step1. Consider automating the tests so you can run them repeatedly as you progress through the challenge.

Step 2

In this step your goal is to extend the parser to handle indentation. In YAML indentation must be made up of spaces, tabs are forbidden.

Here’s a simple test case you can use:

name: Coding Challenges
challenge:
  name: YAML Parser

This should result in a dictionary, equivalent to the JSON:

{
  "name": "Coding Challenges",
  "challenge": {
    "name": "YAML Parser"
  }
}

Step 3

In this step your goal is to extend the parser to parse a YAML file containing string, numeric, boolean and null values, i.e.:

key1: true
key2: off
key3: null
key4: value
key5: 101
key6: ~
key7: 0x12d4
key8: 023332
key9: .inf
key10: .NAN

Be sure to refer to the YAML specification to determine the valid and invalid values for each type.

Step 4

In this step your goal is to extend your parser to support additional string handling. You should handle the difference between quoted strings and non-quoted strings:

quoted: "Coding Challenges\\n"
non: Coding Challenges\\n

The difference is that the quoted string will have the control characters translated, the unquoted string will not. Therefore in the example above the quoted entry will end in a newline, the non-quoted entry will end in the two characters ‘\n’.

You should also support the fold character ‘>’. It allows strings to be spread over more than one line, but the lines will be concatenated without newlines.

message: >
  this is an example from
  the YAML parser Coding Challenge
  that spans more than
  one line

Would therefore be equivalent to:

message: this is an example from the YAML parser Coding Challenge that spans more than one line

Which brings us to the pipe character which allows strings to be interpreted as they are written:

message: |
  this is an example from
  the YAML parser Coding Challenge
  that spans more than
  one line

including the newlines.

Step 5

In this step your goal is to extend the parser to parse a YAML object with object and array values, i.e.:

key: value
array:
 - 1
 - 2
dict:
  innerkey: innervalue

or, using the alternate version of arrays:

key: value
array: [1, 2]
dict:
  innerkey: innervalue

Dictionaries can also be specified using braces as well as indentation, for example:

john: { writes: Coding Challenges, loves: dogs, hates: meetings }

You should ensure your parser handles this too.

Step 5

In this step your goal is to add some of your own tests to ensure you’re confident that your parse can handle valid YAML and will fail with useful error messages on invalid YAML. Dig in to the YAML specification to determine what we have not covered so far.
Going Further

To take your parser further, vist the YAML Test Suite and ensure your parser passes as many of the tests as possible.

Another way to extend this Coding Challenge is to also complete the JSON Parser and then combine both to create a tool that can load either JSON or YAML and then output in the other format.

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John