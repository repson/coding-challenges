Coding Challenge #53 - Bloom Filter Spell Checker
This challenge is to build your own micro spell checker using a Bloom filter.

JOHN CRICKETT
MAR 16, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 49,215 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #53

This challenge is to build your own micro spell checker. The goal is to create a spell checker that can determine if a word is probably spelt correctly without having to store the full list of words. Thus the spell checker can use less storage (disk or memory). A task that is much less relevant these days, but 20 years ago was incredibly useful on low storage devices.

Whilst we don’t have this problem with spell checking today, we do have similar problems checking if an item is in a data set that would be too big to store efficiently.

So how are these problems solved? With Bloom filters.

A bloom filter is a probabilistic data structure. It is built around a bit array and one or more hash functions. It provides a fast and efficient way of handling set membership queries when the set either does not fit within the memory constraints, or querying the full set would incur a performance penalty.

Bloom filters have been used in:

👉 Spell checkers - like you’re going to build in this Coding Challenge.

👉 Network routers - speeding up packet routing protocols amongst other uses.

👉 Databases - a quick way of determining if if a row is likely to be in the database without performing costly disk lookups. Used in Google’s Bigtable, Apache HBase, Apache Cassandra and Postgres

👉 Web crawlers - don’t re-crawl a URL that’s already been seen.

👉 Cyber security - blacklisting, whitelisting and password / username checkers

👉 Web caches - preventing ‘one hit wonders’ being stored in disk caches for CDNs.

👉 Cryptocurrency - Speeding up wallet synchronisation and finding logs in the blockchain.

👉 Recommendation systems - Medium has used Bloom filters to not recommend articles you’ve already seen.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter - forward this one to them. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building A Simple Spell Checker Using a Bloom Filter
In this challenge you’re going to implement a Bloom filter, and insert thousands of words from a dictionary. You’ll then test other words against the dictionary to see if they’re probably spelt correctly.

Step Zero

In this step you’re going to set your environment up ready to begin developing and testing your solution. I’ll leave you to setup your IDE / editor of choice and programming language of choice for building command line tools.

If you’re not on a Unix like operating system you’ll need to get a dictionary file for testing.

If you are on a Unix-like OS you should be able to generate one by running the command:

% cat /usr/share/dict/words >> dict.txt

Step 1

In this step your goal is to use test driven development (TDD) to develop the Bloom filter data structure. OK you don’t have to use TDD, but I’d suggest writing some tests either before or after writing the Bloom filter, both to test that it works correctly and to help you understand how it works.

To implement a Bloom filter:

Determine the number of items that are likely to be stored and the probability of false positives you system can tolerate then use that to determine the memory requirements and number of has functions needed. There’s a formula, to use for this.

Create a bit array and set all bits to zero.

Insert items by applying the hash functions and setting the corresponding bits to one.

Query for the presence of an item by applying the hash functions. If any of the corresponding bits are zero, the item is definitely not in the set. If all of the bits are one, the item is probably in the set.

To determine the how many hash functions you should use and the interaction between the number of bits, the number of items and the number of hash functions there are a set of formulas which you’ll find documented on the Bloom filter Wikipedia page.

You can use hash functions from your programming languages standard library, implement your own or implement an existing one yourself. For the latter I suggest you check out the Fowler–Noll–Vo hash function and implement a couple of the versions of it. It’s a quick and easy hash function to implement if you’ve never written one before.

Step 2

In this step your goal is to read the dictionary file and insert the words into the Bloom filter.

That might look like this:

% ccspellcheck -build dict.txt
And result in a file being saved that contains the dictionary. I called mine words.bf.

Step 3

In this step your goal is to save the Bloom filter to disk. As the Bloom filter is binary we might like to add a simple header:

The first four bytes will be an identifier, we’ll use CCBF.

The next two bytes will be a version number to describe the version number of the file.

The next two bytes will be the number of hash functions used.

The next four bytes will be the number of bits used for the filter.

All in big endian. After that header, the bit array will be written out.

So when done, running the command from the previous step should result in a file being saved that contains the dictionary. I called mine words.bf.

You can use something like xxd to view a hex dump of the file and check your header, i.e.:

% xxd -l 32 words.bf
00000000: 4343 4246 0001 0004 003d 0900 6002 3104  CCBF.....=..`.1.
00000010: 0d40 2902 3095 0008 88a2 6010 0820 4201  .@).0.....`.. B.
Here we have the identifier, version 1, using 4 hash functions and 0x003d0900 bits.

Do note how small the saved Bloom filter file is compared to the input dictionary. For my implementation the numbers look like this:

% du -h dict.txt words.bf
2.4M    dict.txt
492K    words.bf

Step 4

In this step your goal is to load the Bloom filter from disk. You’ll need to read the header - you should validate the file is of the type and version expected.

Step 5

In this step your goal is to test words provided on the command line to see if they’re probably spelt right.

% ccpsellcheck hi hello word concurrency coding challenges imadethis up
These words are spelt wrong:
 coding
 challenges
 imadethis

It’s disappointing that ‘coding’ and ‘challenges’ aren’t in the dictionary I picked for Coding Challenges, but there we go, life is like that! 🤷‍♂️.

Going Further

You can take this further by creating a filter to stop users picking common passwords when signing up to a website - the filter should be small enough to be downloaded and used client side.

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