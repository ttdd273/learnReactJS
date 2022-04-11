# Learning ReactJS

I will learn ReactJS through online resources, and this is where I will take notes on the topics.

Credits to [freeCodeAcademy](https://youtu.be/bMknfKXIFA8)

# First React

- We will first pull in ReactDoms through CDN and Babble to start coding.
- Importing the script tags give us global access to ReactDom in `index.js`
  - First is what do I render, second is where do I render it
  - We make a `div` with an id of `"root"`, and call `document.getElementById("root")` to get it
  - Really annoying, you need to run it on your own server to be able to display it, so you need `python -m http.server 8800` to make the server, and then go to `localhost:8800`
  - Think of it under the hood as getting the element, and then writing something similar to append to the element
  - We can also use the `Live Server` extension to host and run a website on locally, rather than typing the python command

# Project 1: Making a Static Webpage

- ## Why React?
  - ### React allows us to write composable code
    - Idea is to build from much smaller pieces than to start with one big piece
    - Put code together to make a larger piece
  - ### React is declarative
    - Opposite is imperative
    - **Declarative** is "what should be done?", just tell me what to do, and I'll do it
    - **Imperative** is "how it should be done?", describe to me every step on how to do something, and I'll do it
- ## JSX - JavaScript XML
  - A flavor of JavaScript that looks a lot like HTML
  - It essentially is syntactic sugar for writing a JavaScript object that includes all of those properties
  - You can only render one single parent element in React
- ## Goodbye CDN
  - We've been using what's called a **CDN**, content delivery network, which is the easier way to start using React.
  - The CDNS we've been using are the script tags that we copied
  - We will now do it the more "formal" way
  - Creating local variables such as `const page` is not very effective, we will use custom components later to replace this.
- ## Pop quiz #1
  1. Why do we need the import statement?
     - We need it because we're not using babel, and react defines JSX.
  2. If I were to console.log(page), what would show up?
     - Nothing, the console will display a javascript object. React elements that describe what React should eventually add to the real DOM for us.
  3. What's wrong with `const page = ( <h1></h1> <p></p> )`
     - It's not wrapped in a single element, you can use fragments, `<></>`.
  4. What's declarative vs imperative?
     - Declarative is you tell them to do something, they will do, while imperative is you have to tell them how to do something.
  5. What does it mean to be "composable"?
     - Composable means you can build a bigger thing from smaller components.

Checkpoint: [YouTubeLink](https://youtu.be/bMknfKXIFA8?t=3596)
