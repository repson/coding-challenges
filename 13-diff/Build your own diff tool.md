Coding Challenge #13 - Build Your Own diff Tool
This challenge is to build your own diff command line tool. You know, like Unix and git have!
John Crickett
Jun 10, 2023

The diff tool has been part of every software developers tool box since it was initially released in June 1974. How’s that for legacy code that’s still providing value today!
Coding Challenges Live - Cohort Training Course

Would you like to tackle one of these coding challenges with a cohort of other software engineers - and me?

I’m building a three-week cohort-based course around a coding challenges On the course you’ll learn:

    How the application is built - the data structures, algorithms, and architecture behind it.

    How to tackle the project in stages - breaking it down into a series of steps and testing as you go.

    How to collaborate with other software engineers - reviewing their code and offering feedback on their solutions.

If that sounds interesting, you can register your interest and provide feedback on which challenge you’d like to cover here: https://maven.com/forms/cfd972

I’ll be offering a 50% discount to everyone who fills out the survey.

Ok let’s get into the challenge of building diff….
The Challenge - Building diff

Fundamentally like all the Unix command line tools diff does a very simple job. If we check the man output for diff (man diff), we get:

The diff utility compares the contents of file1 and file2 and writes 
to the standard output the list of changes necessary to convert one 
file into the other.  No output is produced if the files are identical.

The core algorithm that is commonly used is described in An O(ND) Difference Algorithm and its Variations by. Eugene W. Myers. There is also the Hunt-Szymanski Algorithm for LCS which was originally used in diff.

The Meyers algorithm is the default used in git. You probably didn’t know - I didn’t before writing this - that git also supports three other algorithms. If your curious to learn more check out the paper: How different are different diff algorithms in Git?
Step Zero

Like all great software development, Coding Challenges is zero indexed! In this step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor and programming language of choice. After that please ensure you have your favourite unit testing library ready to go - for this challenge we’re going to write unit tests first.

Once that’s done you can download some test files for the later steps from my Dropbox.
Step 1

In this step your goal is to implement an algorithm to solve the longest common subsequence problem with a single string. The Wikipedia article on the longest common subsequence provides some pseudo code that might help or you can dig into the papers linked earlier in the challenge.

You should implement some unit tests for your algorithm, here are a few test cases:

String 1: "ABCDEF"
String 2: "ABCDEF"
Expected LCS: "ABCDEF"

String 1: "ABC"
String 2: "XYZ"
Expected LCS: ""

String 1: "AABCXY"
String 2: "XYZ"
Expected LCS: "XY"

String 1: ""
String 2: ""
Expected LCS: ""

String 1: "ABCD"
String 2: "AC"
Expected LCS: "AC"

Please think carefully about any others you might need. Hint think carefully about the time and space complexity of the algorithm and consider some tests with that in mind.

Once you’re happy you can find the LCS in a pair of strings move on to step 2.
Step 2

In this step your goal is to build the next layer of a diff tool - now that you can find common subsequences in a pair of strings, you need to be able to apply that to multiple lines - arrays of strings.

Again we can work on this by writing a set of unit tests and then implementing a function that will pass all of them.

Here’s some test cases to get you started:

Lines 1: "This is a test which contains:", "this is the lcs"
Lines 2: "this is the lcs", "we're testing"
Expected LCS: "this is the lcs"

Lines 1: "Coding Challenges helps you become a better software engineer through
          that build real applications.",
         "I share a weekly coding challenge aimed at helping software
          engineers level up their skills through deliberate practice.",
         "I’ve used or am using these coding challenges as exercise 
          to learn a new programming language or technology.",
         "Each challenge will have you writing a full application or
          tool. Most of which will be based on real world tools and
          utilities."
Lines 2: "Helping you become a better software engineer through
          coding challenges that build real applications.",
         "I share a weekly coding challenge aimed at helping software
          engineers level up their skills through deliberate practice.",
         "These are challenges that I’ve used or am using as exercises
          to learn a new programming language or technology.",
         "Each challenge will have you writing a full application or
          tool. Most of which will be based on real world tools and
          utilities."

Expected LCS: 

"I share a weekly coding challenge aimed at helping software engineers level up their skills through deliberate practice.",
"Each challenge will have you writing a full application or tool. Most of which will be based on real world tools and utilities."

I’ve deliberately not covered some of the test cases you’ll need to think about. Your challenge is add your own test cases and ensure you code passes them all.

Once you have that working we can progress to Step 3.
Step 3

In this step your goal is to create a function to generate the differences between two arrays of strings as a third array of strings.

Again I’d encourage you to to approach this by writing unit tests first.

Taking the Coding Challenges text above your should output:

< Coding Challenges helps you become a better software engineer through 
  that build real applications.
> Helping you become a better software engineer through coding 
challenges that build real applications.
< I’ve used or am using these coding challenges as exercises to learn a 
  new programming language or technology.
> These are challenges that I’ve used or am using as exercises to learn 
  a new programming language or technology.

Please note the lines are wrapped to fit on the page, the actual lines being with > and <.
Step 4

In this step your goal is to read take the functions you built so far and use them to build your diff tool. It should two command line arguments, one for the original file and one for the new version of the file.

You should then read the contents of the two files, run them through the functions we wrote in steps 1, 2 and 3 and print out a list of the differences between the two files.

For example:

% ccdiff origcc.txt newcc.txt
< Coding Challenges helps you become a better software engineer through 
  that build real applications.
> Helping you become a better software engineer through coding challenges that build real applications.
< I’ve used or am using these coding challenges as exercises to learn a 
  new programming language or technology.
> These are challenges that I’ve used or am using as exercises to learn 
  a new programming language or technology.

Please note the lines are wrapped to fit on the page, the actual lines being with > and <.

Once you have that working, congratulations you’ve built your own diff command like tool!
Step 5 (Optional)

In this step your goal is to consider scale. How would you solution cope with very large files? Are there optimisations you can make to improve the performance?
Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.
Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John