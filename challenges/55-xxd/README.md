
Coding Challenge #55 - xxd
Build you own hexdump tool.

JOHN CRICKETT
MAR 30, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 50,497 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

🙏 I have a favour to ask: Please help me grow Coding Challenges by forwarding this email to one or two of your fellow developers with a brief sentence explaining why you think thy’ll find Coding Challenges useful. Many thanks! ****🙏

Coding Challenge #55 - xxd

This challenge is to build your own version of xxd. Xxd is a Unix command line tool to create hexdumps and to convert a hexdump back into it’s binary form.

It’s a very useful tool if you want to dig into binary files. Typically tools that support hexdumps display the information in both hexadecimal and ASCII format.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

Buy one of my courses that walk you through a Coding Challenge.

The Challenge - Building xxd

In this Coding Challenge we’re going to build a clone of xxd. We’ll use it to create some hexdumps and to convert them back to binary. While we’re at it we’ll learn a little about binary files.

Step Zero

Like most programming languages, Coding Challenges is zero indexed!

For this step, Please ready your IDE / development environment of choice and prepare an new project in your programming language of choice. It’s a program your own adventure!

After that here’s what I’d like you to do to be ready to test your solution. As we did in the build your own tar coding challenge we’re going to use a tarball as an example, you can create it by running the following commands:

echo "File 1 contents" >> file1.txt
echo "File 2 contents" >> file2.txt
echo "File 3 contents" >> file3.txt
tar -cf files.tar file1.txt file2.txt file3.txt

Step 1

In this step your goal is to dump a tarball as hex. To do this you’ll need to open the file in binary mode, read it in and dump the contents to standard out as hex.

By default xxd prints the output in three sections. The first is the offset into the file, the second is the data as hex and the third is the data as text. There are 16 bytes per line. That will look like this:

% ccxxd files.tar | head -n 10
00000000: 6669 6c65 312e 7478 7400 0000 0000 0000  file1.txt.......
00000010: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000030: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000040: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000050: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000060: 0000 0000 3030 3036 3434 2000 3030 3037  ....000644 .0007
00000070: 3635 2000 3030 3030 3234 2000 3030 3030  65 .000024 .0000
00000080: 3030 3030 3032 3020 3134 3630 3133 3233  0000020 14601323
00000090: 3431 3720 3031 3434 3432 0020 3000 0000  417 014442. 0...

I’ve used head to only show the first ten lines for brevity.

Step 2

In this step your goal is to support changing the output to little-endian (-e flag). Using this option treats the byte groups as words in little-endian byte order. The default grouping of four bytes is used unless a different grouping is specified with the -g flag.

This looks like:

% ccxxd -e files.tar | head -n 2
00000000: 656c6966 78742e31 00000074 00000000   file1.txt.......
00000010: 00000000 00000000 00000000 00000000   ................
And:

% ccxxd -e -g 8 files.tar | head -n 2
00000000: 78742e31656c6966 0000000000000074   file1.txt.......
00000010: 0000000000000000 0000000000000000   ................
Don’t forget to handle invalid values for -g.

Step 3

In this step your goal is to support the command line options to set the number of octets to be written out and the number of columns to print per line. These are the -l and -c flags in you want to explore the valid settings in the man entry.

For example:

% ccxxd -l 16 files.tar
00000000: 6669 6c65 312e 7478 7400 0000 0000 0000  file1.txt.......

% ccxxd -l 16 -c 4 files.tar
00000000: 6669 6c65  file
00000004: 312e 7478  1.tx
00000008: 7400 0000  t...
0000000c: 0000 0000  ....

Step 4

In this step your goal is to support the -s flag which allows us to seek to a specific byte offset in the file. For example in the build your own tar challenge we learned that the tarball file has a 512-byte header followed by the file’s contents. We also know that beginning byte 124 there are 12 bytes of the file size in octal:

% ccxxd -s 124 -l 12 files.tar
0000007c: 3030 3030 3030 3030 3032 3020            00000000020
So we know the first file starts at byte 512 and is 16 bytes long. We can therefore see the contents if we seek to offset 512 and check the following 16 bytes of the tarball:

% ccxxd -s 512 -l 16 files.tar
00000200: 4669 6c65 2031 2063 6f6e 7465 6e74 730a  File 1 contents.

Step 5

In this step your goal is to support the ability to revert a hex dump back to a binary file. This is the -r option. In the example below I convert the binary for the build your own shell coding challenge, ccsh to a hex dump saved as ccsh.hex, then convert it back to binary named ccshr and run it.

% ccxxd ccsh > ccsh.hex
% ccxxd -r ccsh.hex >> ccshr
% chmod u+x ccshr
% ./ccshr
ccsh>

Going Further

You can take this challenge further by adding support for the other options for xxd, or by using it to learn more about some of the binary files on your system. For example what files start like this (there is a different answer for each line):

00000000: cafebabe                             ....
00000000: 8950 4e47                            .PNG
00000000: ffd8 ffe0 0010 4a46 4946 0001 0100 0001  ......JFIF......
00000000: 504b 0304                                PK..
00000000: 2550 4446 2d31 2e34 0d25 e2e3 cfd3 0d0a  %PDF-1.4.%......

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

Th