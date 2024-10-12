Coding Challenge #75 - Duplicate File Finder
Build a clone of the command line tool fdupes.
John Crickett
Oct 12, 2024

Coding Challenge #75 - Duplicate File Finder

This challenge is to build your own version of a file deduplication tool. These tools are useful for finding duplicate files that can be deleted to free up storage space.

For many of us this probably isn’t a problem we face often, but it’s enough of a problem that several tools exist, including fdupes written in C. It’s fairly readable code, so even if you don’t fancy writing your own tool, you could learn more about the techniques used by reading the code for fdupes.

There are several uses for deduplication and the techniques used for identifying duplicate files. The first is obviously to find duplicate files and remove them freeing up storage space. Another common use is to exclude duplicate files from backups.

When we extend this to enterprise level backups they also often use these techniques to find duplicates within files to further reduce the storage (and network bandwidth) requirements.

Aside: Performance Quiz - The Answer

Last week I asked readers of Coding Challenges this question: if we re-wrote Docker in Python, what impact would it have on the performance of the containers you run?

The correct answer is that it would have no impact on the performance of the containers that you run. Docker is simply doing some configuration with Linux namespaces and cgroups and then running another process (your container) within those namespaces. The runtime is therefore completely unaffected by the language used to develop Docker.

To really understand Docker, check out the build your own Docker challenge. By building your own Docker, you’ll gain a deeper understanding of Docker and become a better software engineer.

Question: Should I Build A Course On How To Build Your Own Docker?

If you think so, and would be interested, please sign up to the waitlist. If there is enough interest I’ll build a course that explains how to create your own solution to the Docker Coding Challenge in Python, Go and Rust.

Anyone on the waitlist will be offered a 50% discount.

The Challenge - Building A Duplicate File Finder

In this coding challenge we’ll be building a command line tool that can scan a directory to identify and remove duplicate files.

Step Zero

Like all the best programming languages we’re zero indexed!

For this step, I’ll leave you to setup your IDE / editor of choice and programming language of choice. After that here’s what I’d like you to do to be ready to test your solution:

for i in {1..20}; do dd if=/dev/urandom bs=100 count=1 of=file$i; done
cp file1 file21

You can tweak this to create more files (change the 1..20 to use a bigger range), or different sized files (change the value of bs). The cp command then ensures we have a duplicate, again feel free to create more duplicates for testing.

Please make your testing more complete by creating subdirectories and ensuring there are duplicate files in different levels of the directory hierarchy you create.

Step 1

In this step your goal is to accept and directory in the command line and then scan that directory and list all the files in it recursively. That should look something like this:

% ccdupe .
file1
file2
subdir/file11
subdir/anothersubdir/file21

Step 2

In this step your goal is to extend your program from step 1 to record the file and it’s size, then if you find a file with the same size report it as a potential duplicate. Remove the listing of the files now you’ve seen that that works.

That should look something like this:

% ccdupe .
Potential duplicates: file1 file2
# ... snipped duplicates of file1 to file 20.
Potential duplicates: file1 subdir/duplicateoffile1

Note:

    I’ve snipped a lot of messages about the 20 test files I created that are all 100 bytes in size.

    When creating my test data I’ve named my files so it’s easy for me to see if my code is working/not working because I’ve clearly named my files so I know that duplicateoffile1 is a duplicate of file1.

Comparing the file size is a very quick way of filtering out duplicates, but as we can see with the test data we’ve created it’s too simplistic.

Step 3

In this step your goal is to create a more robust way of identifying duplicate files. We can achieve this using a hash function to calculate a hash for each file. If we get two files that produce the same hash they are almost certainly the same.

For this step I suggest you calculate the MD5 of each file and the compare it to all the previously seen MD5 hashes to determine any of the files are duplicates. Then output a list of the duplicates.

You could store the record of the file and it’s MD5 purely in memory, or you could store it in a local database like SQLite, caching the results between runs (do consider how you’d check the cached values are still correct).

That should look something like this:

% ccdupe .
Probable duplicates: file1 subdir/duplicateoffile1

There are other hashes you could use instead of MD5, i.e. SHA1 or SHA256 but as we’re not using the hash for cryptographic purposes it makes sense to use the faster MD5 and if we want to reduce the chance of a false match we can do a more expenses check only on files that have a matching MD5 hash.

If you’re interested, the probability of just two hashes accidentally colliding is approximately: 1.47*10^-29. Pretty unlikely, but there is a known attack on MD5, making it unsuitable for cryptographic purposes but fine as a quick check for us in this use case.

Step 4

In this step your goal is to check that the files identified as duplicates really are duplicates. To do so, do a full compare of the file, comparing every byte on each file with the same byte in the other file.

After you’ve done that, update your output:

% ccdupe .
Duplicates: file1 subdir/duplicateoffile1

Step 5

In this step your goal is to ignore files below a certain size. If we’re focused on quickly freeing up some disk space we might not care about small files. So extend your solution to take an optional command line argument that defines the minimum file size to consider:

% ccdupe --minsize=1000 .
%

Step 6

In this step your goal is to delete the duplicate file that has been found. I suggest you prompt the user to select which file to delete. That might look like this:

% ccdupe .
Duplicates: file1 subdir/duplicateoffile1
Which file should be deleted?
  1) file1
  2) subdir/duplicateoffile1
  Any other value keeps the file and continues

Going Further

Here are some ideas if you want to take this project further:

    Handle symlinks.

    Delete duplicates.

    Write to a log.

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John