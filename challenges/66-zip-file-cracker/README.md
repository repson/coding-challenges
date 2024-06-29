Coding Challenge #66 - Zip File Cracker
This challenge is to build your own zip file cracking tool.
John Crickett
Jun 29, 2024

Coding Challenge #65

This challenge is to build your own zip file cracking tool.

Despite it being well known that encrypted zip file are not particularly secure many people still use them, including several of the companies that my recent employers have used to “encrypt” my payslips.

It’s especially poor when they use a simple to guess / or common combination of words as the password, making the password easily susceptible to a dictionary attack. Making it more security / privacy theatre than reality.

In this coding challenge we’re going to write a zip file cracker so you’ll know how easy it is to crack zip file and you’ll never use password protected (encrypted) zip files to share personal/sensitive data.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building a Zip File Cracker

In this coding challenge we’re going to build a tool to ‘crack’ an encrypted zip file.

Step Zero

In many programming languages we index arrays from zero onwards. Coding Challenges is the same, we start with Step 0. It’s the step where you setup your IDE / editor of choice and programming language of choice.

This is a great challenge to complete in a language like C, C++, Rust or Go so you can build a concurrent cracker. Though it’s perfectly possible to do it in languages like PHP, Python or JavaScript. The choice is yours!

After you’ve setup your development environment create a test zip file like so:

% export LC_CTYPE=C
% cat /dev/urandom | tr -dc '[:alpha:]' | fold -w ${1:-1000} | head -n 1 > cc.txt
challenge-zip-cracker 
% zip -e cctest.zip cc.txt

Enter a password when prompted. For now use the simple password ‘test’.

Step 1

In this step your goal is to verify the file is a zip file. The simplest way to do this is to check the headers match those of a zip file. You can do that by reading the headers and checking they match those detailed here.

If you remember back to the build your own xxd coding challenge we could use xxd to inspect the file and see the headers too:

% xxd -l64 cctest.zip
00000000: 504b 0304 1400 0900 0800 0e81 dc58 09a9  PK...........X..
00000010: b5ad f602 0000 e903 0000 0600 1c00 6363  ..............cc
00000020: 2e74 7874 5554 0900 03ec d17e 66ee d17e  .txtUT.....~f..~
00000030: 6675 780b 0001 04f5 0100 0004 1400 0000  fux.............

Another key thing to notice here is that even though the file is “encrypted” the metadata is not - we can see the filename: cc.txt.

Your program should do something like this:

% cczipcrack cctest.zip
Has zip headers.
% cczipcrack cc.txt
Does not have zip headers.

Step 2

In this step your goal is to conduct a dictionary attack. This type of attach is explained in the build your own password cracker coding challenge. To do this step grab a password list from CrackStation here. Grab the Smaller Wordlist for now.

Then attempt to decrypt the zip file with every word in the dictionary. Print out the correct password when you find it. You could implement the full zip encryption specification or just use a library for your programming language.

% cczipcrack -dict cctest.zip
Password found: test

Step 3

In this step your goal is to try all combinations of valid chars up to a certain length. This is a brute force attack. Usually dictionary attacks are tried before brute force attacks as most passwords are real words and many of them are found in the widely available password dictionaries.

Add support in your zip password cracker for brute forcing the password, allow the user to specify a min and max length of the password then generate all combinations of the allowable password characters.

% cczipcrack -brute -min=1 -max=4 cctest.zip
Password found: test

Step 4

In this step your goal is to check concurrently. Modern CPUs have multiple cores so we should be able to test more passwords by using multiple threads, thereby cracking the password in less time.

For this challenge create one thread per CPU core on the machine on which the cracker is running.

Going Further

You could take this further by checking if the contents of the file are another encrypted zip file and if so cracking that. A zip file within a zip file is a common workaround for the metadata not being encrypted.

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