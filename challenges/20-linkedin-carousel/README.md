Coding Challenge #20 - LinkedIn Carousel Generator.
This challenge is to build your own carousel generator for LinkedIn posts (aka a PDF document builder).
John Crickett
Jul 29, 2023

There are a number of different approaches to this problem. Some people have built Powerpoint templates, The online graphic design tool Canva has created templates that you can use and some, have created online software tools (and even launched and sold them as a business).

I’m a software developer, not a graphic designer so I like the idea of a software tool. A tool that allows me to focus on the bit I’m good at - writing - and ignore the bit I’m bad at - graphic design.

How you tackle this challenge is up to you. You could build it as an online app, entirely frontend using JavaScript. You could build it full-stack, you could build it as a desktop application, or you could build it without a GUI - offering the same functionality via an API (which of course you could also access from a frontend).

Share Coding Challenges

The Challenge - Building a Carousel Generator

For LinkedIn, the carousel can in in any of the following formats: Powerpoint (PPT or PPTX), Word Document (DOC or DOCX) or Portable Document Format (PDF). We’re going to focus on PDF.

So this challenge is to build a software tool that allows a user to create a carousel that they can use on a LinkedIn post. Though you don’t have to use it for that - you could use it to generate handouts for your next tech talk - it’s essentially going to build a PDF document.

Step Zero

In this step you decide which programming language and IDE you’re going to use and you get yourself setup with a nice new project.

Step 1

In this step your goal is to allow the user to preview a slide with some text on it. So that means the user should be presented with a GUI that shows a slide preview and a text box. When the test is updated the slide preview is updated.

LinkedIn supports multiple sizes, with a common size being the 1080 x 1080 pixel square. The max supported is 4320 x 4320 pixels. For this challenge we will stick to a 1080 x 1080 square which will make it feasible to offer a full sized preview on most screens.

So your GUI looks something like this:

Step 2

In this step your goal is to be able to add a profile image, which will be shown in the top left hand corner and their name that can be shown beneath it.

To do that you’ll need to add the ability to upload an image as well as to specify their name/handle. Once you’ve don that you should have a GUI something like this (feel free to make it a better UX):

Step 3

In this step your goal is to set the background and foreground colour as well as the font face and size. These will affect all the slides.

Step 4

In this step your goal is to be able to add a slide and navigate through the slides, with the preview and edit options for the text on each slide.

Step 5

In this step your goal is to add an image as the background of an individual slide, a high level of transparency is a good idea (or go one step further and make it configurable).

Step 6

In this step your goal is to export the carousel as a PDF. The PDF should have one page per slide, reflecting the font, color, content and background image added for each slide.
Going Further

You can take this further and add support for PowerPoint and other formats. You could also integrate with the LinkedIn API to post it.

Share Coding Challenges
Past Challenges and Community

Don’t forget you can find all the past challenges on the Coding Challenges website and there is a Discord Server and Coding Challenges Sub Reddit, if you want to discuss them.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know - ping me a message on the Discord Server or in the Coding Challenges Sub Reddit, via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John