Coding Challenge #69 Notion Clone
This challenge is to build your own version of the note taking app Notion.
John Crickett
Jul 20, 2024

Coding Challenge #69 Build Your Own Notion Clone

This challenge is to build your own version of Notion.

Notion is a note-taking app. It’s the tool I use to write all my LinkedIn post and the Coding Challenges.

The Challenge - Building A Notion Clone

For this Coding Challenge we are going to build a clone of the core, essential bits of Notion. To me those are the bits I use daily. Which includes being able to login, create a page / duplicate a page, edit pages and re-oder pages.
Step Zero

For this step you’re going to set your environment up, ready to begin developing and testing your solution.

You’re going to be building a backend service, which will need some persistent data store. You’ll also want to build a frontend that uses the backend.

I’m suggesting you build it with separate frontend and backend components so you can experiment with building an API - it’s an opportunity to learn RESTful APIs if you’ve never done it. Or if you’ve done plenty of REST perhaps experiment with gRPC or GraphQL. Have fun learning something new is the safe space that is Coding Challenges!

I’ll leave you to setup your IDE / editor of choice and programming language of choice.

Step 1

In this step your goal is to create a home page and the flow that will allow a user to register and login. Notion often uses one time codes for this, you might like to try that versus passwords. As we saw in the build your own password cracker coding challenge, passwords can be vulnerable.

Step 2

In this step your goal is to show a workspace. This is the page a user will see when they login. At first it will be black. After they’ve created some pages it will contain the content. For now provide a single button to ‘Create Page’.

Step 3

In this step your goal is to allow a user to add a page and then edit the contents of the newly opened page. In. Notion that opens up a new page entry screen like this. Your clone should do the same.

The user should then be able to enter page title, replacing ‘Untitled’. You should support formatting for three different levels of headings, bullet points, bold and italic.

At this stage you’ll also want a backend database of some sort as well as an API for your frontend to interact with it.

Step 4

In this step your goal is to add a navigation bar. It could look something like this:

It should list all the pages that the user has created.

Step 5

In this step your goal is to allow pages to be duplicated. This allows a user to create a new blank page or create a new page that is a copy of an existing page (I have a template for coding challenges that I duplicate for each challenge).

Be user to give the duplicate a sensible name, i.e. add “(1)” after the name of “Copy of” to the beginning.

Step 6

In this step your goal is to allow pages to be re-organised. Notion allows me to group pages under other pages and to re-order them on the navigation bar. You should do the same.

Step 7 (Bonus)

Notion has like to many other tools jumped on the AI bandwagon. In this step your goal is to allow generation of text with AI. Add a new formatting option that uses the current sentence as a prompt for an LLM. Ollama is a simple way of plugging AI into your backend, see: https://ollama.com/library/llama3 and https://github.com/ollama/ollama/tree/main/docs

Going Further

You can take this challenge further by adding as much or as little of the remaining functionality of Notion as you like.

Two really interesting options would be building a mobile or desktop app that use the same backend API. Perhaps with Electron for the desktop?

Share Your Solutions!

If you think your solution is an example other developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.

Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John