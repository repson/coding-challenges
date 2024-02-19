Coding Challenge #49 - Password Cracker
This challenge is to build your own version of John the Ripper or CrackStation.
John Crickett
Feb 17, 2024

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 45,491 software developers who have subscribed. I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Coding Challenge #48

This challenge is to build your own version of John the Ripper or CrackStation. These are password cracking tools that can be used to recover passwords, by penetration testers and of course bad guys.

We’re going to take a look at them because they provide an interesting way of learning several different things - you can pick and choose where you focus from the list:

    How to implement cryptographic hash functions - you can build these by hand if learning how to code them interests you, otherwise you can use the ones available for your programming language.

    How and why certain approaches to storing passwords are insecure so you have a better understanding of how to build a secure system and to securely store passwords for the systems that you develop.

    How to build and optimise a computationally expensive piece of software.

If You Enjoy Coding Challenges Here Are Four Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

    If you work for a company that sells to software engineers, encourage them to sponsor the newsletter. 🙏

The Challenge - Building A Password Cracker

Ever since we’ve been building multi-user systems there’s been a need to identify and authenticate users. That started off with usernames and passwords stored in plaintext (unencrypted), which wasn’t very secure and meant that anyone with access to the password data could read everyone’s passwords.

Pretty soon we moved to using hashing functions to obscure the plaintext passwords. When a user provided their password it would be hashed and the hash value stored. When a user logged on, the password they entered would be hashed and the generated hash compared to the stored hash, if they match the user is authenticated. This was an improvement. Most of the hashing functions are secure - impossible to reverse to get the password from the hash - but there is another problem.

As the number of users grew, we started to see a problem created by us, the users. The problem is we tended to pick similar passwords and often many of us used the same password. For example for many years the most common passwords have been: 123456, password, 123456789, qwerty, 111111, 123123 and other similar words and patterns.

Attackers therefore realised they didn’t need to decrypt the hashes, they could instead try common passwords and lists of words from the dictionary, run those through a hash function and when the hashes match they had the password. At the same time computers because faster and cheaper so it also became possible to brute force passwords hashing every permutation of letters and numbers possible - up to a certain length. At least this was possible with early hash functions that were quick and cheap to compute.

As a result more complex hashes were adopted and we began to push for longer passwords that included varying case, numbers and symbols. To combat this attaches started using rainbow tables. Rainbow tables are pre-computed tables of common words, phrases and passwords along with their hash. Now cracking is simply a cases of looking up the hash to see if it’s in the table. To counter this new algorithms are used along with a technique known as salting.

In this challenge we’re going to build a password cracker that uses some of these techniques.

Step Zero

In many programming languages we index arrays from zero onwards. Coding Challenges is the same, we start with Step 0. It’s the step where you setup your IDE / editor of choice and programming language of choice.

Depending on whether you’re going to aim for more of a John the Ripper or a CrackStation you might pick a stack like C, C++, Rust or Go versus a stack like PHP, Python or JavaScript. The choice is yours!

Step 1

In this step your goal is to implement the MD5 hash function. By doing so you will have an awareness of how password hashes are generated. Wikipedia has an explanation of the MD5 algorithm.

You can test your implementation against the implementation in your programming languages standard library. In the event that it doesn’t have support you can compare to this Python that you could run locally or on one of the online IDEs.

from hashlib import md5

print(md5(b'password').hexdigest())

Step 2

In this step your goal is to crack an MD5 password by brute force. To do that you’ll want to generate all the possible permutations of valid password characters up to a predefined length, then hash them and compare to a pre-determined hashed password.

As a test case try some four letter passwords and brute force them. Here’s a couple you could try:

7a95bf926a0333f57705aeac07a362a2
08054846bbc9933fd0395f8be516a9f9

This is the equivalent of incremental mode in John the Ripper.

Step 3

In this step your goal is to use a word list to speed up the attack. Instead of generated every single possible permutation of letters we’ll use a word list of common passwords. You can get one such list from CrackStation here. Grab the Smaller Wordlist for now.

Adapt your program to allow the user to specify whether to brute force or use a word list, allowing them to specify the path to the word list. See how quickly you can crack this hash: 2bdb742fc3d075ec6b73ea414f27819a

Step 4

In this step your goal is to build your own rainbow table. A rainbow table is a set of pre-computed hashes. For this process you can read in the word list and/or generate all the possible permutations of valid password characters up to a set length, then compute the hash for them. Save that hash and the input ‘password’ used to generate the hash to a file.

Step 5

In this step your goal is to crack an password using the rainbow table. Simply put, your code will now read in the pre-computed rainbow table and look up the hash to ‘crack’ in it.
Step 6 (Bonus)

In this step your goal is to add support for other common cryptographic hashing functions. After than read up on and learn about salting and key derivation functions (KDF).
Going Further

You can take this challenge further by optimising your solution to use multiple threads to compute (or look up) the hashes in parallel. You can go even further down that road by looking at how GPUs are used to accelerate password cracking.
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