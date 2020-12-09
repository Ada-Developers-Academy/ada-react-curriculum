# Intro to React Exercise

Complete this worksheet with your neighbors. Some items are questions, some items are exercises to extend your hello world React application.

## Test your Knowledge

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: b0959997-50ab-4bc6-873c-9582b30bb4e6
* title: What is CRA?
* points: 1
* topics: react

##### !question

What is the purpose of `create-react-app`?

##### !end-question

##### !placeholder

What is the purpose of Create React App?

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

> Create React App is a tool (built by developers at Facebook) that gives you a massive head start when building React apps. It saves you from time-consuming setup and configuration. You simply run one command and Create React App sets up the tools you need to start your React project.

_Taken from the [Team Treehous Blog](https://blog.teamtreehouse.com/getting-started-create-react-app-tool)_

Essentially `create-react-app` is a too that generates a starter react application with a bunch of tooling and configuration already done for you.  It's a lot better than manually setting it all up yourself.

CRA Provides:

- React, JSX, ES6, TypeScript and Flow syntax support.
- Language extras beyond ES6 like the object spread operator.
- Autoprefixed CSS, so you don’t need -webkit- or other prefixes.
- A fast interactive unit test runner with built-in support for coverage reporting.
- A live development server that warns about common mistakes.
- A build script to bundle JS, CSS, and images for production, with hashes and sourcemaps.
- An offline-first service worker and a web app manifest, meeting all the Progressive Web App criteria. (Note: Using the service worker is opt-in as of react-scripts@2.0.0 and higher)
- Hassle-free updates for the above tools with a single dependency.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->


<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: e2969df0-b0a9-4e2e-8ccb-b14013ca3ab3
* title: How to start the development server
* points: 1
* topics: react

##### !question

How do you start up your development server for your React application?

##### !end-question

##### !placeholder

How do you start the local development server?

##### !end-placeholder

##### !answer

/[(npm\s+start)(yarn\s+start)]/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

You start the development server with:

`npm start` 

or 

`yarn start`
##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: f55c01fe-48a6-4965-a2fa-394950394440
* title: What is invalid?
* points: 1
* topics: react

##### !question

Why is the following react render function invalid?

    ```JavaScript
      function App() {
        return (
          <header>
            <h1>Hello Neat Header</h1>
          </header>
          <p>
            Welcome to my React application!
          </p>
        );
      }
    ```
##### !end-question

##### !placeholder

What is wrong?

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

In a React component you need to return a **single** element.  You can have other JSX inside that element, but you React requires you to return a single JSX element, which can contain other elements.

This could be fixed with:

    ```JavaScript
      function App() {
        return (
          <div>
            <header>
              <h1>Hello Neat Header</h1>
            </header>
            <p>
              Welcome to my React application!
          </p>
          </div>
        );
      }
    ```

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: multiple-choice
* id: 4b66da45-d861-4ec6-b5e9-abea65a203a8
* title: [text, a short question title]
<!-- * points: [1] (optional, the number of points for scoring as a checkpoint) -->
<!-- * topics: [python, pandas] (optional the topics for analyzing points) -->

##### !question

Which of the two JSX code options should you choose? **Why?**

    a.

    ```javascript
    <header class='main-header'>
    </header>
    ```

    b.

    ```javascript
    <header className='main-header'>
    </header>
    ```
##### !end-question

##### !options

* A
* B

##### !end-options

##### !answer

* B

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

`class` is a reserved word in JavaScript, so you need to replace it with `className` in JavaScript.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

The next two questions involve using this [coding sandbox](https://codesandbox.io/s/ada-initial-react-ub6v9?file=/src/App.js), which is kind of like CodePen or Repl.it, but lets you write client-side JavaScript (including React) and see it immediately in the browser.

Open up the Codepen and try the following challenges.

5. Add another `img` tag to your render function to an image of your choice. The image source should be an absolute URL from an image already uploaded on the internet.

6. **Challenge**: Create a local variable in your `App` function equal to your name. Update the function to display the value associated with this local variable.
