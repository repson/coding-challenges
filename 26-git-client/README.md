Coding Challenge #26 - Build Your Own Git Client
This challenge is to build your own git client.
John Crickett
Sep 9, 2023
If You Enjoy Coding Challenges Please Help Spread the Word!

Coding Challenges is 6 months old today!

If you’re enjoying it, please help spread the word.

You can do that by sharing the website: https://codingchallenges.fyi or sharing your favourite coding challenge on Hacker News, Reddit or your social media platform of choice. Many thanks in advance for your support!

Thank you for reading Coding Challenges. This post is public so feel free to share it.

Share
OK on with the Coding Challenge!

As a software engineer, coder, programmer, or whatever you refer to yourself as, I’m sure you’ve heard of the distributed version control system that is git and the hugely popular git hosting service GitHub.

If you’ve not come across git before, I wrote about it recently on LinkedIn here, where I also explained why it’s called git!

This challenge is going to have you build a git client that can: create a new repository, add some commits and push them to GitHub.

Step Zero

This is software engineering so we’re zero-indexed and for this step you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to setup your IDE / editor of choice and programming language of choice.

Once you’ve done that I suggest taking some time to read through the Internals section of the Git SCM website. It’ll take you through the steps needed to manipulate a git repository. If you want to really dig into git you can check out the git source code on GitHub.

Step 1

In this step your goal is to create a basic git client that can initialise an empty git repository. An empty git repo is simply the .git directory with a few files in it, these are:

    HEAD a reference to the current HEAD.

    config - the repository’s configuration file, there are some defaults set in it.

    description - the repository’s description file - the default value is defined in the git source repo.

    hooks - a directory containing any hooks for the repo.

    info - a directory that contains the excludes file. We’ll ignore it for this challenge.

    objects - a directory, this is the object store.

    refs - a directory.

You can check you implementation by running it and then testing with git itself. For example (I’ve called our git implementation ccgit):

% ccgit init test
initialized empty repository: test
% cd test
% git status
On branch master No commits yet nothing to commit (create/copy files and use "git add" to track)

Don’t forget to check if there is already a git repository initialised in the directory.

Step 2

In this step your goal is to add one or more files to the index.

In effect you will be implementing the equivalent of hash-object command, to get the hash of an object to add it to the index. Be sure to read the section on Object Storage to understand how a hash is generated for an object.

Once you have a hash for the object you wish to add to the index you want to implement the equivalent to the update-index --add command. The format of the Git index file is documented here.

When completed you should be able to do:

% touch hello-coding-challenges.txt
% ccgit add hello-coding-challenges.txt
% git status
On branch master

Changes to be committed:
(use "git restore --staged <file>..." to unstage)
	new file:   hello-coding-challenges.txt

Note that I’ve used git itself to test that the file has successfully been added to the index.

Step 3

In this step your goal is to support the status command. Having used git status to see that we’ve added a file to the index, it would be nice to be able to use our own status command.

To identify the changed or un-tracked files walk the directory tree and compare each file to the entry in the index. If the file is not in the index it’s untracked, if it’s there and the hash has changed it’s changed, if it’s in the index but not in the directory tree it’s been deleted.

Once done this should look like this:

% ccgit status
On branch master

Changes to be committed:
	new file:   hello-coding-challenges.txt

Untracked files:
	another-coding-challenge.txt

You can determine the current branch from the file .git/HEAD

I’d suggest also adding and deleting files to check that your status works completely.

Step 4

In this step your goal is to be able to commit the staged files. To create a commit, read through the Tree Objects section of the Git Internals Git Objects documentation.

You’ll want to add all the staged files to the database. The files are stored in the objects directory. The files are all deflated with zlib.

Git stores the content as a single file per piece of content, named with the SHA-1 checksum of the content and its header. The subdirectory is named with the first 2 characters of the SHA-1, and the filename is the remaining 38 characters. For example of the SHA-1 is fd55a0bc090c8ea131ef6dc2ae0386b64798e87e then the file will be stored in objects/fd/55a0bc090c8ea131ef6dc2ae0386b64798e87e

After that you need to write the tree to disk and update the index. This is documented in the internal documentation linked above.

Once you’ve done a commit, use git to check it has worked, that should look like this:

% ccgit commit "Add Hello CC"
committed to master: 8e0ed1fd59559543c9e8612bdc5bd3558abc73f9
% git log
commit 8e0ed1fd59559543c9e8612bdc5bd3558abc73f9 (HEAD -> master)
Author: John Crickett [3667898+JohnCrickett@users.noreply.github.com](<mailto:3667898+JohnCrickett@users.noreply.github.com>)
Date:   Wed Sep 6 19:36:00 2023 +0000
	Add Hello CC

Step 5

In this step your goal is to support the diff command. You can refer to the Diff Coding Challenge to understand how to write your own diff algorithm (a great way to learn about dynamic programming and longest common subsequence).

If you don’t fancy tackling a full diff algorithm implementation right now, there are libraries that provide diff implementations for most programming languages.

Then iterate over the list of files that have changed and diff each file in turn. You can use the code you wrote for the status command to identify what has changed.

Once you’ve implemented diff you should be able to do the following:

% echo "Hello Diff Step" >> hello-coding-challenges.txt
% ccgit diff
diff --git a/hello-coding-challenges.txt b/hello-coding-challenges.txt
index e69de29..99e7373 100644
--- a/hello-coding-challenges.txt
+++ b/hello-coding-challenges.txt
@@ -0,0 +1 @@
+Hello Diff Step

Step 6

In this step your goal is to push to a remote git repo - I used GitHub. As a first step, create a new repository on GitHub for you to push to.

You can learn how git pushes to a remote repository in the Git SCM book, see the Transfer Protocols section. You’ll want to study the Uploading Data section in particular. I’d suggest implementing it over HTTPS at first using a username and GitHub personal access token for authentication.

Once you’re done you should be able to push a commit to GitHub and then view that commit through the GitHub UI (or clone the repo to a different directory with git itself).
Going Further

The obvious next step for this challenge is to extend your code to support merging.

Thank you for reading Coding Challenges. This post is public so feel free to share it.

Share
Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John