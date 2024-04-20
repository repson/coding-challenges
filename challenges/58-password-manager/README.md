
Coding Challenge #58 - Password Manager
Build your own password manager like Keepass, 1Password or a CLI equivalent.

JOHN CRICKETT
APR 20, 2024
Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 51,148 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧

Ad: Invest in your career and learn modern backend development skills with boot.dev, use the code JOHNCRICKETT you’ll get 25% off your first payment.

Ad: Practice writing complex software with codecrafters.io and get 40% off as a Coding Challenges reader.

Interested in seeing your ad here? Then check out the sponsorship page for details.

Coding Challenge #58 - Password Manager

This challenge is to build your Password Manager (i.e. something like Keepass).

Password managers let you store and manage your passwords in a secure way. All your passwords are stored in a single database that is protected with a master key. Done well this increases your level of security, as you can use hundreds of unique complex passwords without having to try to remember them, storing them all in one place that is protected by the most secure encryption algorithms currently known.

If You Enjoy Coding Challenges Here Are Three Ways You Can Help Support It
Refer a friend or colleague to the newsletter. 🙏

Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

The Challenge - Building a Password Manager

In this Coding Challenge we’re going to build a password manager that will allow you to:

Create a password vault.

Sign in to an existing password vault.

Create a password record within a vault.

Retrieve a password record and the associated password from a vault.

Step Zero

Coding Challenges like the majority of common programming languages arrays is zero based, therefore we start with Step 0!

Step 0 is where you setup your IDE / editor of choice and programming language of choice. For this challenge you could build something web based like 1Password, a desktop application like Keepass or a command line tool. Or go wild and build all three - it’s your project!

Step 1

In this step your goal is to allow a user to create a vault. When a user creates a vault they should be able to provide a name for the vault and set the master password.

You might want to ensure the name is acceptable as a filename, then you can use it as the filename when saving the vault. If you went for a CLI tool, this step might look like this:

% ccpm
Welcome to CC Password Manager
What would you like to do?
1. Create a new password vault
Quit (enter q or quit)
1
Creating a new vault
Please provide a name for the vault: cctest
Please enter a master password:
Please confirm the master password:
New vault created and saved as: cctest.ccv

What would you like to do?
1. Create a new password vault
Quit (enter q or quit)
q
Don’t forget to use a password entry field that masks passwords from prying eyes.

Step 2

In this step your goal is to allow the user to create a password record within a vault. As a minimum the user should be able to specify the following:

A name or identifier for the record.

A username.

A password.

These should then be added to the password vault. Depending upon how you decide to implement the vault the entire vault could be encrypted or the vault could be as simple as a plain text file with the contents of the fields encrypted.

Either way the data needs to be encrypted in order to be secure. So how do we do that?

Well we want to store the password records in an encrypted form. As we learned in the build your own password cracker this is often done with cryptographic hashes. However we use hashes because they’re impossible to reverse. That’s not a useful trait for a password manager! We want to be able to retrieve our passwords.

So instead we want to use a secure symmetric encryption algorithm such as AES-256 or Twofish. These algorithms use a key for encryption and decryption. So to complete our security we use a Key Derivation Function (KDF) to generate the encryption key that we’ll use with the secure symmetric encryption algorithm.

If you haven’t guessed it already, we’ll use the master password and a KDF to generate the encryption key used to encrypt and decrypt the password records.

Step 3

In this step your goal is to allow a user to sign in to a vault. To do that they should be able to identify the vault they wish to sign in to and provide the master password for it.

Once signed in, they should be able to add and retrieve password records without re-entering their password. Something like this:

What would you like to do?
1. Create a new password vault
2. Sign in to a password vault
3. Add a password to a vault
4. Fetch a password from a vault
Quit (enter q or quit)
2
Enter vault name: cctest
Enter password for the cctest vault:
Thank you, you are now signed in.

Step 4

In this step your goal is to allow the user to retrieve a password from the vault. To do this they should have already selected and signed in to a vault.

They should then be prompted to enter the name of the record they wish to retrieve. Something like this:

What would you like to do?

1. Create a new password vault
2. Sign in to a password vault
3. Add a password to a vault
4. Fetch a password from a vault

Quit (enter q or quit)
4
Fetching password
Please enter the record name: cc test record
For cc test record
The username is john
The password is: secretpassword
Congratulations you’ve built a basic password manager!

Going Further

You could extend this by adding the ability to modify and update password records. You could also make it more secure by creating a timeout, such that if they have not used the software for a period of time they will need to re-enter the master password.

2 Other Ways I Can Help You:
I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

I have some courses available:

Build Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

Build Your Own Shell (Go Edition) which guides you through solving the Shell Coding Challenge in Go.

Share Your Solutions!

If you think your solution is an example other developers can learn from, please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John