# React Hello World

## Learning Goals

By the end of this lesson we will be able to...

- Create a new React application
- Read through a basic React component
- Explain how JSX & CSS work in React

### Setup

The React developers have created a nice tool to help you get started with creating a new React application. Since most React applications require the same npm packages and information, this tool that we'll use will install each of these for us by default.


Although it is not the same, we'll use `npx create-react-app` in a similar way to the way we used `rails new`.

```bash
npx create-react-app hello-world
cd hello-world
```

#### What's Included?

Let's go ahead and open this project up in your text editor to examine the files that have been created for us. We'll start in the `src` folder.

Take a look at the `index.js` file that was created. Some questions for you as you check out this code:

<!-- available callout types: info, success, warning, danger, secondary  -->
### !callout-info

## Ask yourself

- What looks familiar?
- What looks new?

### !end-callout

Next, take a look at the `App.js` file that was created. Some questions for you as you check out this code:

<!-- available callout types: info, success, warning, danger, secondary  -->
### !callout-secondary

## Questions to answer:

- What do you think this code is doing?
- How is this code related to the code you looked at in `index.js`?

### !end-callout


#### Functional Components

This code contains a function! However this function looks like it returns HTML!  It also starts with a capital letter.  **In React, component names always start with a capital letter.**

In React, you can build a component as either a class or a function. We will be sticking with functional components, and `create-react-app` will start with a function for the top-level `App` component. For now, we will work with that function.

#### Running the Server

Now that we've examined the code that was generated for us, we can go ahead and run our web server for this application by running `npm start` from our terminal. This command is set up to start our application and then open the browser where the server is running.

**Question**: Where is the HTML that is displayed on the web page coming from?

### Component's function determines how it's rendered

The `App.js` file contains our first (auto-generated) component. How exciting!

Now let's examine the pieces of code within the `App` function and identify the key pieces.

```javascript
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}
```

Here are some important things to note about this function:

- The pieces that look like HTML are **JSX**
- Every component is either a function or a class, and each gets its own file
- Every component is a function that returns a bunch of JSX
  - As we'll see later for a class component, it's the `render` function
  - For a functional component, the whole component is the function!
- The function that is responsible for rendering must return a single object.
  - It must be one of the following:
    - A *single* element.
    - An array of elements.
    - A String.
  - In this case, this rendering function returns the outermost `div`. Every other element in the function is contained within that outermost `div`.

**Try It!** Change something about the `App` function above and see how it immediately affects what the browser displays.

#### What is JSX?

JSX is a pre-processor (similar to ERB in Rails) that adds XML syntax to JavaScript. JSX and React can technically be used independently, but you almost always see them together. JSX looks a lot like HTML though there are a few important differences.

**Adding CSS Classes**

Since JSX is within our JavaScript code, we cannot use the `class` keyword the way we would directly in our HTML. Instead, we must use `className` to avoid the reserved word. You'll notice this in several lines of the rendering function that we were examining above.

**Making it Dynamic**

Take a look at the code above and see if you can identify a location within the `App` function that is rendered dynamically. HINT: You'll be able to identify it because the syntax looks a bit different.

In ERB, we were familiar with using the `<%` and `<%=` elements to dynamically generate content for our views. In JSX, we utilize `{}` to pass in code that we'll use to dynamically generate view data.

**Important Notes**

- JSX cannot contain if-statements. If you need to include logic within your render function, you can do so _before_ the return statement.
- A React Component must return or _render_ a **single element**, an **array of elements** or a **string**. This does not mean that there can't be more complicated JSX in the `return`, but it does mean that if you have multiple elements they need to be wrapped in **one** outermost element or contained within **one** array.

## Learning Comprehension

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: 8b29a78c-313e-42bb-8e8a-d95c46797631
* title: What is JSX?
* points: 1
* topics: react, jsx

##### !question

In your own words explain what JSX is.

##### !end-question

##### !placeholder

Explain JSX

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

JSX is a syntax extension to JavaScript.  Basically it allows us to write HTML-like code that can co-exist with our regular JavaScript in React.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: multiple-choice
* id: a42f5e6d-194f-4fb6-b6fa-c57b37bf15ca
* title: React Components
* points: 1
* topics: react

##### !question

A React component can be...

##### !end-question

##### !options

* A function
* A class
* An Array
* Either a function or a class

##### !end-options

##### !answer

* Either a function or a class

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

You can create a component either with a function or a class.  However with the advent of React Hooks, you really don't **need** to create class components anymore.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: 0c35564e-5953-4927-985a-4855e913830a
* title: Create React App
* points: 1
* topics: react

##### !question

What is `create-react-app`?

##### !end-question

##### !placeholder

What is create react app?

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

`create-react-app` is a tool created by Facebook to generate a starter React application with a bunch of tooling in place to make it easier to build a React application.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->



## Key Takeaway

- We can use `npx create-react-app` to create a new boilerplate React application.
- Once our React application is created, we can run `npm start` in the terminal to start it up.
- JSX is the pre-processor associated with React that we will utilize to generate dynamic HTML.

## Additional Resources

- [`create-react-app`](https://github.com/facebookincubator/create-react-app)
- [JSX Tutorial](http://buildwithreact.com/tutorial/jsx)
