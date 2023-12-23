Coding Challenge #34 - jq
This challenge is to build your own version of jq.
John Crickett
Nov 4, 2023

The tool jq is a lightweight and flexible command-line JSON processor. It’s incredibly useful for processing JSON responses from REST APIs and other JSON data sources allowing us to quickly and effectively filter out the bits we want.

An example of this was our uses of jq in the build your own cat challenge, where we used it to extract quotes from JSON data to be used in our tests.

The Challenge - Building Your Own jq

The command line tool jq is like sed for JSON data - you can use it to and filter and transform JSON data, much like you would with sed. BTW a past Coding Challenge was to build your own sed.

Step Zero

Like jq itself we’re zero-indexed! In this step you’re going to set your environment up ready to begin developing our jq clone: ccjq.

Step 1

In this step your goal is to open a JSON file and pretty print it.

Turning this unreadable result:

% curl -s 'https://dummyjson.com/quotes?limit=2'
{"quotes":[{"id":1,"quote":"Life isn’t about getting and having, it’s about giving and being.","author":"Kevin Kruse"},{"id":2,"quote":"Whatever the mind of man can conceive and believe, it can achieve.","author":"Napoleon Hill"}],"total":100,"skip":0,"limit":2}
%

Into this nicely formatted JSON:

% curl -s 'https://dummyjson.com/quotes?limit=2' | ccjq
{
  "quotes": [
    {
      "id": 1,
      "quote": "Life isn’t about getting and having, it’s about giving and being.",
      "author": "Kevin Kruse"
    },
    {
      "id": 2,
      "quote": "Whatever the mind of man can conceive and believe, it can achieve.",
      "author": "Napoleon Hill"
    }
  ],
  "total": 100,
  "skip": 0,
  "limit": 2
}

Note the command could also have been: curl 'https://dummyjson.com/quotes?limit=2' | ccjq ‘.’ which uses the simplest filter ‘.’ which is the identity operator - it produces the same output as its input (but ccjq pretty prints it).

Make sure you support both, then move on to Step 2.

Step 2

In this step your goal is to support the array index: .[<number>]. Like most programming languages, arrays in jq are zero indexed.

In use that would look something like this:

% curl -s 'https://api.github.com/repos/CodingChallegesFYI/SharedSolutions/commits?per_page=3' | ccjq '.[0]'
{
  "sha": "74e54f3bcb090790224a2d4ce7000291e3ad2cbf",
  "node_id": "C_kwDOKUpeI9oAKDc0ZTU0ZjNiY2IwOTA3OTAyMjRhMmQ0Y2U3MDAwMjkxZTNhZDJjYmY",
  "commit": { <snip>
  }
  <snip>
}

N.B. I’ve trimmed a lot of JSON out of the result here to make it readable. The ccjq command was: ccjq '.[0]'.

I’ve used GitHub’s API here to get some suitable JSON, but you should consider building your own tests or developing the code using Test-Driven Development.

Step 3

In this step your goal is to handle the object identifier: .codingchallenge and .[<string>], as well as the optional (?) extension to it.

The commands you want to support look like this:

ccjq '.codingchallenge'
ccjq '.["codingchallenge"]'
ccjq '.codingchallenge?'
ccjq '.["codingchallenge"]?'

One approach to testing this might be:

% curl -s 'https://dummyjson.com/quotes?limit=2' | ccjq '.quotes'
[
  {
    "id": 1,
    "quote": "Life isn’t about getting and having, it’s about giving and being.",
    "author": "Kevin Kruse"
  },
  {
    "id": 2,
    "quote": "Whatever the mind of man can conceive and believe, it can achieve.",
    "author": "Napoleon Hill"
  }
]

and:

% curl -s 'https://dummyjson.com/quotes?limit=2' | ccjq '.code'  
null

Don’t forget that they could be nested.

Step 4

In this step your goal is to support the pipe operator ‘|’. The pipe operator combines two filters by feeding the output of the one on the left into the one on the right. It's similar to the Unix shell's pipe. Here’s an example command ccjq '.[0] | .commit.message' being run:

% curl -s 'https://api.github.com/repos/CodingChallegesFYI/SharedSolutions/commits?per_page=3' | ccjq '.[0] | .commit.message'
"some commit message is returned here"

Note the actual commit message you see will vary depending on when you run this command.

Step 5

In this step your goal is to collect the output as an array. You can do this by wrapping the filter in square brackets, that would look like this:

% curl -s 'https://dummyjson.com/quotes?limit=2' | ccjq '[.quotes[].quote]'
[
  "Life isn’t about getting and having, it’s about giving and being.",
  "Whatever the mind of man can conceive and believe, it can achieve."
]

Going Further

There are many other options available in jq itself, if you have the time you can read about in jq’s excellent documentation and implement as many of them as possible.