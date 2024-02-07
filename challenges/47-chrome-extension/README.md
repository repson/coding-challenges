Coding Challenge #47 - Build Your Own Chrome Extension
This challenge is to build your own Chrome extension to make your new tabs more useful.
John Crickett
Feb 3, 2024

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 42,169 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email📧
Many Thanks To This Week’s Sponsor - Alloy Automation

Stop wasting your time building integrations. Alloy Automation is an integration development platform used by engineering teams at Amazon, Gorgias, Postscript, & others to get rid of the headaches of handling OAuth, API field mappings, and continuously having to add new endpoint support to existing integrations. Founded in 2019, the company is backed by a16z, Bain Capital Ventures, & Y Combinator. Learn more and try out their Unified API today.
Coding Challenge #47

This challenge is to build your own Chrome extension. Chrome extensions are a software programs that extends the functionality of the Google Chrome web browser. They are typically written in HTML, CSS, and JavaScript, and they modify or enhance the browser’s functionality in some way.

Chrome extensions can add new features, customise the appearance of websites, improve productivity, block ads, manage passwords, and much more. You can install and manage Chrome extensions through the Chrome Web Store.

If You Enjoy Coding Challenges Here Are Four Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

    If you work for a company that sells to software engineers, encourage them to sponsor the newsletter. 🙏

The Challenge - Building A Chrome Extension

For this Coding Challenge you’re going to build a Chrome extension that will customise the look and functionality of each new tab you open in Chrome. It’s drawing on inspiration from the popular extension Bonjourr and the more complicated Momentum.

If you’ve never built a Chrome extension before the Chrome for Developer website has a section on getting started building Chrome extensions.

Step Zero

Before we begin, please set up your IDE etc. as you like it. This challenge is one you’ll be tackling in JavaScript or TypeScript along with HTML and CSS.

Step 1

In this step your goal is to create the Coding Challenges equivalent to ‘Hello, World’ for Chrome extensions. That is create an extension that:

    You can install locally

    Sets the background colour of the new tab to Coding Challenges Blue (that’s #04295B)

    Displays the text Coding Challenges>_ in the centre of the new tab. Bonus points for matching the Coding Challenges branding! 😀

When you create a new tab, the tab should then look like this:

Step 2

In this step your goal is to add the current time to the tab, and the date in a human friendly format below. You can draw your inspiration from Bonjourr or my example below:

Don’t forget to include the functionality to update the time!

Step 3 - Version 1

In this step your goal is to add some dynamic information. For example, Bonjourr provides details of the weather.

We’re doing Coding Challenges so we’ll list the latest coding challenges from the Coding Challenges Substack Feed. So, at the time of writing that looks like this:

To do this you’ll have to ensure the extension has permission to fetch from Substack. To further complicate things, at the time of writing the Substack RSS feed does’t include CORS headers so you’ll need to find a way to fetch the feed through some sort of proxy. If you haven’t come across it before, you can learn more about CORS here.

Step 3 - Version 2

In this alternate step your goal is to add some dynamic information without the need for a proxy. As the Coding Challenges Community is doing a great job of sharing solutions I decided to create a version that displays all the open PRs for the Shared Solutions Github Repository. That looks like this:

You can get a list of the PRs by calling Github’s REST API endpoint: https://api.github.com/repos/CodingChallegesFYI/SharedSolutions/pulls you’ll find the full documentation for their REST API here.

Going Further

You can take this Coding Challenge further by extracting further information from either of the dynamic elements and adding some more context. For example, for the Substack feed you could add the images, title and description of each challenge.

After that, you could change the extension to be more generic, perhaps displaying a daily quote and offering a customisable Github feed. Then consider packaging the extension and making it available on the Chrome Web Store.

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