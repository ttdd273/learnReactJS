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

# Introduction

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
- ## Components (Composability)
  - The whole point is creating custom components that's reusable
  - Function that creates elements over and over again
  - We use pascal case instead of camelCase for component names
    - Camel case always starts out lowercase with each word delimited by a capital letter (like personOne, textUtil, thingsToDo)
    - Pascal case is similar to camel case, but the first letter is always capitalized (like PersonOne, TextUtil, ThingsToDo)
    - Snake case means that we delimit words with an underscore (like person_one, text_util, things_to_do)
  - And we wrap the function in angle brackets: `<Function />`
- ## Custom Components Quiz
  1. What is a react component?
     - A react component is a function that returns some JSX that can be inserted into HTML.
     - A function that returns React elements.
  2. What's wrong with the code?
     - The function should be PascalCase, and it needs to begin with captial letter.
  3. What's wrong with the code?
     - You need to call with `<Header />` to get the component
- ## Parent and Child Components
  - The parent component is the main component that gets rendered
  - The children components are components that the parent component calls
- ## Styling React Components
  - Use `className=""`, which is very similar to HTML, which uses `class=""`
- ## Organizing Code in React
  - An important way to organize code in React is to separate them out into different folders, etc.
  - General principle:
    - Name the file with PascalCase, similar to the name of the function that its exporting
    - Export the function with `export default function`, depending on the use case
    - Import with `import FunctionName from "./FunctionName"`, you don't neeed the `js` extension since it is the default extension
    - The `./` is a way to indicate you're referring to a file that's in your project, not a dependency
    - Another convention is also to call `Page` the `App` component, or the main component
    - Doesn't exactly work with imports since we don't have the correct dependencies and we're using babel
  - ## Create App
    - In browser babel transformer is not a good long term solution
      - It is necessary because the browser cannot interpret JSX
    - Normally, you need a whole bundler system called `Webpack`
      - You would then configure it so that it compiles your React code into something the browser can understand
    - However, webpack is normally very difficult to pickup, so the React team created a package called `Create-React-App` to hide those abstraction details
      - To use this, you need Node and npm
      - nvm is another module that makes it really easy to change node versions
    - Create-react-app generates a boiler plate, but you can delete everything in it and start from scratch to get it up and running, but you don't need `index.html` file, since it's in the public folder
    - Generally recommended to load css directly in the source folder, and then get it with an import
      - Behind the scenes, React is using something called styleloader that does this
    - For images, put them all in a folder called images and also import them
      - Set `src` to the imported name

# Project 1

- ## Setup
  - Create a components folder, and we will remove most of the boilerplate code from create-react-app
  - Not a whole lot of new materials, definitely keep in mind of the parent child structure
    - Export default for react components
  - Some characteristics unique to this project
    - To make an image into the background, use the `url()` tag in css
    - Specify things in JSX with `classNames`
      - Generally use names with two dashes, e.g. `main--list`

# Project 2

- ## Setup

  - In project 1, everything is hardcoded, and not data driven, and this project will tackle that with props
  - Clone of airbnb experiences page, the list on the page are from the database
  - Remember that CSS elements have a model organized like the following
    - ![CSS Model](/assets/css_model.png "CSS Model")
  - Hero component is a component that contains multiple images, texts, and links.
  - Want to give the font family to the entire body, so that it is spread throughout the website
  - Project card component
    - Need to build out a single instance of the component
    - Problem is that it is not reusable at all, and instead, it should be data driven
    - In React, this is where `props` come into play
  - To type a variable in JSX, use the curly braces `{}`
    - In fact, anything that's inside the curly braces can be run as JavaScript code
  - Duplicating a certain component will always cause it to have the same data
    - To do this, we can add whatever property we want into React
    - In the function parenthesis, just add the word `props` inside it, it can really be named anything, but it passes in a dictionary with the attribute name and the corresponding value that's passed in
  - Pop quiz:

    1. What do props help us accomplish?
       - They allow our components to be data driven, and we can pass in whatever we want into the component.
    2. How do you pass in a prop into a component?
       - Type the name of the prop and its corresponding value, such as `<Component attr=""/>`, and this is a dictionary, so call `props.attr` to access that element
    3. Can I pass in a custom prop into a native DOM element? ex) `<div blahblah={true}/>`
       - WRONG: I think you can since native DOM elements are just JavaScript objects
       - RIGHT: No, you cannot, the JSX will be turned into real DOM elements, and real DOM elements will ony have the properties/attributes specified in the HTML specification.
    4. How do I receive props in a component?

       - The name of the parameter in the function header is the dictionary name, call `props.attr` to get the corresponding attribute.

    5. What data type is `props` when the component receives it?
       - WRONG: A dictionary or a map
       - RIGHT: An object!

  - Object Destructuring:
    - `const {img, name} = person`, will take the corresponding attributes of person and store them into those variables.
    - Rename using colons: `const {img: image...}`
    - You can therefore choose to destructure immediately:
      - `function Header({img, name, ...})`
  - Jokes Page
    - <hr /> tag is the thematic break tag, puts a line in the page
    - It is also an option to conditionally render
    - `{props.setup && <h3>Setup: {props.setup}</h3>} `
    - In React, we can also pass in nonstring props into the components, or any JavaScript types as props
    - To do this, we just surround the types in `{}`
    - You can also pass in additional variables within a string like so:
      - `` {`../images/${props.img}`} ``
    - `Array.map()` method can be used to expand the array elements
    - React JSX can also render the entire array on the page, with `{}` as usual
  - Map array quiz
    1. What does the `.map()` array method do?
    - It loops through the array and applies the function you pass in on each element of the array
    3. What do we usually use the `.map()` method for in React?
       - It is usually used for creating components out of an array of data elements, which are usually objects
    4. Why is using the `.map()` better than just creating the components manually by typing them out?
       - It is better because you are making your website data driven, and reduces code duplicity and makes it flexible for changes, and makes our code more "self-sustaining," not requiring additional changes whenever the data changes.
  - For the project, we will need to move the images folder into the public folder for images to load. In reality, We usually won't have a `data.js` file, and instead, we will load the data in from online resources.
  - You will see a key prop warning anytime you use, and the key is just something unique about the item, `key` propery.
    - You can use certain properties, such as in this case, the rating, etc. However, this is not unique for every item. Therefore, you should use something similar to an ID, which should normally come with a database.
  - Our card component is getting pretty long with all the properties that we're passing in. One way to avoid this is just passing in the entire object
  - Another way to make it simpler is with the object spread syntax
    - `{...item}` will spread all components of item and create a separate prop for each one of them

# Project 3

- This is where we will create interactive web apps using React, until now, we've been making static websites, and reusable components.
- Static web pages
  - Read only, no changes to data
  - Examples: blogs, news sites, recipes
- Dynamic web apps
  - Read-write: ability to change data
  - Highly interactive
  - Displays _your_ data
    - Examples: Bank website, Airbnb
- In this project, we will create a meme generator that takes the top 100 memes from a website and allows the user to generate a random new meme
- Push something to the right in CSS by giving it a margin of auto
- In order for the user to interact with the page, we have to be listening for different events that could occur, and react to them
  - As soon as the page loads, it will immediately make a call to an API called ImageFlip, which will return to us an array of 100 meme images, and clicking the button "Get a new meme image" will simply random pick one out of those 100 meme images
- We will start with event listeners
  - In JavaScript, you can use: `.addEventListener("click", function() {})`
  - In HTML, you can use: `onclick="myFunction()"`
  - In React, we need to use `onClick={function() {}}`, note the capital C, you will have a JavaScript object with that exact property
    - CamelCase is the standard, such as `onMouseEnter`, `onMouseOver`
    - You don't want to include `()` in the property, because that will immediately run the function
    - List of React [eventListeners](https://reactjs.org/docs/events.html#mouse-events)
    - Convention is to add the word handle before the event attribute
- Rendering items
  - The other problem that you run into when using React is that things don't get re-rendered when elements in a component change
  - The rendering only takes place once
  - In order to do this, we need to access something called React state, which allows us to hook into the component and make it so whenever we update the state, React will update the page as well
- ## State vs. Props
  - `Props` refers to the properties being passed into a component in order for it to work correctly, similar to how a function receives parameters: "from above". A component receiving props is not allowed to modify those props, i.e. they are immutable
  - `State` refers to values that are managed by the component, similar to variables declared inside a function. Any time you have changing values that should be saved/displayed, you will likely be using state.
- ## Quiz
  1. How would you describe the concept of "state"?
     - The concept of "state" is something that's managed by the component or the function, it is a mutable part of the function that will change on its own.
     - A way for React to remember some saved values.
  2. When would you want to use props instead of state?
     - You would want to use props instead of state when you are expecting something from the user and want to display that information.
     - Props are like parameters for the function.
  3. When would you want to use state instead of props?
     - You would want to use state instead of props when you want to update something on the page for the user.
  - State is kind of like local variables declared inside a function.
  4.  What does "immutable" mean? Are props immutable? Is state immutable?
      - Immutable means that it can't be changed, and props are immutable while state is mutable.
- React also has a method called `React.useState()`, which is one of the many hooks that React has
  - `React.useState()` actually returns an array `[arg, function()]`
  - This implies we can destructure the result as such:
    - `const [result, function()] = React.useState(arg)`
    - `function(arg)` is generally a function used to set the new React state to what `arg` is
  - One way to use the function that the hook create is to pass in the old state, but you can also do it with a callback function
    - The callback function, which is a function passed as an argument to the hook, will take in the old value of the state, so you can use it in the function body, and you have to include a return statement to have it display
    - This is the best practice in React, and you should always pass in a function to set count
- ## Quiz
  1. You have 2 options for what you can pass in to a state setter function (e.g. 'setCount'). What are they?
  - You can pass in a value to a state setter function or you can pass in a callback function.
  2. When would you want to pass the first option (from answer above) to the state setter function?
  - You want to pass a value when it is more static, or it doesn't depend on the value of the old state.
  3. When would you want to pass the second option (from answer above) to the state setter function?
  - You want to use a callback function when your new state depends on the value of the old state.
- In general, you should not directly modify objects that keep track of the state, and use the state functions to edit them
- Every time a component needs to be rerendered, the component itself will be re-rendered, as well as any child components
  - To pass in event listeners on non-native DOM elements, you normally will call it `handleClick` to indicate that
- Passing data to components
  - You cannot pass data between sibling components, only the parent has those information
  - One workaround is to raise the information necessary to the parent component
  - This can be very tedious, so React offer workarounds called context, and third party state management systems called Redux
- Dynamic styles
  - Just like how you can add styles inside of HTML, you can also add styles inside of the ReactJSX, with `{{}}`, the outer set represents entering JavaScript inside of JSX, and the inner set represents the JavaScript object
  - The attributes must also be camelCase
- If you find yourself initializing state with incoming props, there's probably a better way to do this in the parent component with unified state
  - This is known as **dervied state**, and you probably don't need this, and it leads to multiple sources of truths
- ## Quiz
  1. What is conditional rendering?
     - When we want to only sometimes display something on the page based on a condition of some sort.
  2. When would you use &&?
  - When you want to either display something or NOT display it.
  3. When would you use a ternary?
     - When you need to decide which thing among 2 options to display
  4. What if you need to decide between more than 2 options on what to display?
     - Use an `if...else if...else` condition or `switch` statement
- ## Forms
  - In the old days, you would create a form in the HTML and give it an action, usually a `php` file that processes the form.
    - A method of `POST`
    - The `php` file will process that data
  - In JavaScript, it is a little different
    - You have a selector that picks the form
    - Add a `submit` event listener
    - The function that runs whenever the form is submitted would gather all the values together and submit it to an API
  - The most important thing to know if when you submit the data, it would gather all the data immediately and submit it immediately
- In React, instead of waiting for the form to be submitted
  - Every tiny change changes the state, and React is watching each change that happens
  - When the user is done, you simply submit what you already have
- The `onChange` attribute returns an event, which is called a `SyntheticBaseEvent`, and includes various properties
  - `event.target` will return the DOM element
- Controlled components
  - The state figure in your component should be your single source of truth
  - This means for the forms, we need to add a `value` attribute to the DOM element
- `input` vs `textarea`
  - `input` is a self closing tag in HTMl, whereas `textarea` is not
  - Whatever you put in the two tags is the value of the tag
  - However, in React, they've made the textarea DOM element a self closing tag, and we need to add a `value` attribute to tag
- Checkboxes
  - It is not a DOM element by itself
  - However, in HTML, it is an HTML element `<input type="checkbox"/>`
  - They are fundamentally different because they only hold boolean values
  - In HTML, there is a `checked` property that tells you the value of the checkbox
  - To label a checkbox, you should use `htmlFor`, in plain HTML, it is `for`, but `htmlFor` is the underlying JavaScript attribute, and it points the `id` of the corresponding DOM element
- Radio buttons are a mixture of checkboxes and text input
  - You need to be careful with the `checked` attribute, because it needs to be a boolean value, so you end up needing to use a statement such as `formData.employment === "unemployment"`
- Select boxes
- Submitting the form
  - In HTML, you can use something such as `<input type="submit" value="Send it in" />`
  - In JSX, the default type of the element `<button>` is already a submit button, so you can use that
  - In the old days, you might specify in the form, the method type, and action is some php file
  - However, now you can just use a `onSubmit` event handler
- # Quiz
  1. In vanilla JS app, at what point in form submission do you gather all the data from filled-out form?
     - Right before the form is submitted
  2. When is it submitted in React?
     - As the form is being filled out. The data is all held in local state
  3. Which attributes in the form should match the property name in formData?
     - The `name` property
  4. What's different about saving the data from a checkbox element vs other elements?
     - You use a `checked` property to determine what should be saved
  5. How do you watch for a form submit? How can you trigger a form submit?
     - `onSubmit` handler on the `form` element. Can be triggered with a click.
- # Making API Calls
  - You often need to interact with something outside of your application.
    - You are usually requesting inforamtion from an API
      - When you request information, usually, you want to somehow display that inforamtion
    - Or submitting information to an API
  - Two general steps:
    - Get the data, using (fetch) or another tool like AXIOS
    - Take that data and save it to state
  - When you call `fetch(URL)`, it returns a promise, and you need to resolve it with `.then(anonymous function)`
  - If you just use a normal `fetch` and use the `setState` method to set it to the data you get back, then you will get an infinite loop of rendering, because `fetch` lives on the top level, and it re-renders the component. However, every time the comonent renders, it also calls `fetch` again, which causes the infinite loop
  - This will lead into how we handle side effects
- # Side Effects
  - What are React's primary tasks?
    - Working with the DOM/browser to render UI to the page
    - Manage state for us between render cycles (i.e. state values are "remembered" from one render to another), and we use the `useState` hook to do this
    - Keep the UI updated whenver state changes occur
  - What can't React handle on its own?
    - (Out)side effects
      - localStorage
      - API/database interactions
      - Subscriptions, ex) web sockets
      - Syncing 2 different internal states together
  - `useEffect()` hook is like a tool or a blank canvas that allows us to interact outside of this ecosystem
    - Allows us to sync React state with those outside systems
- `useEffect()`
  - The first parameter is a required callback function
    - Guaranteed to run only after the HTML elements have been rendered on the page
  - The second parameter is optional, but you will almost always use it
    - It is a dependencies array, it will contain values that determine how many times the callback function will run, so it doesn't run an infinite number of times
    - Example: `[]` will only run it once
    - Example: `[count]` will consider that variable as a dependcy, and it replaces it with the value that `count` currently holds. At the end, it makes the comparison `[0] compareTo [1]` to determine whether to run or not, it will not run if it is true
- # Quiz

  1. What is a "side effect" in React? What are some examples?
     - Any code that affects an outside system
     - Local storage, API, websockets, two states to keep in sync
  2. What is NOT a "side effect"?
     - Anything that React is in charge of
     - Maintaining state, keeping the UI in sync with the data, render DOM elements
  3. When does React run your useEffect function? When does it not?
     - As soon as the component loads (first render)
     - On every re-render of the component (assuming no dependencies array)
     - WILL NOT run the effect when the values of the dependencies in the array stay the same between renders
  4. How would you explain what the "dependencies array" is ?
     - Second parameter to the useEffect function
     - A way for React to know whether it should re-reun the effect function

- Always remember that the first parameter to `useEffect` is a callback function
- You could've also changed the functions inside `useEffect` to be `async` and `await` functions. However, you will never want the callback function to be an `async` function. Instead, you can define the `async` function inside the callback function
- Unmounted and mounted are really two terms to describe whether a DOM element is on the page or not
- One important problem is called a **memory leak**, this happens when you're trying to update state on a DOM element that's no longer mounted on the page

  - The solution is this is just called `useEffect cleanup`, which is where you return another function inside the callback function. This usually just undoes what you did before, ex: `removeEventListener`

- Summary: `useEffect` takes a function as its parameter. If that function returns something, it needs to be a cleanup function. Otherwise, it should return nothing. If we make it an async function, it automatically returns a promise instead of a function or nothing. Therefore, it you want to use async operations inside of `useEffect`, you need to define the function separately inside of the callback function
- Lazy state initialization

  - Is when you have an expensive intialization that you only want to be run once, you can provide a function instead of a value into `useState` for that to happen

- Checkpoint: [YouTubeLink](https://youtu.be/bMknfKXIFA8?t=36238)
