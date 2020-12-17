# State in Functional Components

## Interesting Title Here About Why State in Functional Components

In this curriculum, we have focused primarily on functional components when talking about React components.  Compared to class components, they are shorter to write and simpler to read and test.  In early versions of React, however, functional components were 'stateless', meaning they could not use any of the features of state in class components and as a result were not widely used.  State is a powerful tool, and without it, functional components could only be used in limited ways.  To address this issue, the React team added a feature called Hooks that makes it possible to "hook" into state features and use them in functional components.  The Hooks update added several new features to React, including the ability to write custom hooks, but in this lesson we're going to focus on the `useState` hook and adding state features to our functional components.

## Rewriting the [Name - accordian menu?] Example with Functional Components and the useState hook

### Adding the `useState` Hook

The first step is adding the `useState` hook to the functional component.  This is done by replacing the `import React from 'react';` line with:

```javascript

import React, { useState } from 'react';

```

The next step is using `useState` inside the component.  `useState` takes one argument, which is the initial value of our state variable, and is only used the first time the component renders.  `useState` returns an array of two elements, the first element is the current value of the state variable and the second element is the function to update the state variable.  The only way to update the state variable is to use the update function that is given to us by `useState`.  Calling the state update function will trigger a render of the component.  In the example below, we are going use `useState` to build a component with a button that adds exclamation points to a sentence.

```javascript

import React, { useState } from 'react';

function Example() {

    // Declare a new state variable
    // We want to start with 1 exclamation point, so we will set the initial value to 1
    const [exclamationCount, setExclamationCount] = useState(1);

    let exclamationString = "";
    for(let i = 0; i < exclamationCount; i += 1) {
        exclamationString += "!"
    }

    return(
        <div>
            <p>I am very excited{exclamationString}</p>
            <button onClick={() => setExclamationCount(exclamationCount + 1)}>
                Add Excitement
            </button>
        </div>
    );
};

export default Example;

```

*Warning* in the above example, `exclamationCount` is *not* the state variable.  `exclamationCount` is the current value of the state variable.  Let's dig into how this works.  On the first render `useState` will set up the state variable and then give us the current value of that variable and the update function.  When we call the update function and pass it a new value of the state variable, the value is stored and then a render is triggered.  Render calls the Example function.  Every time we call the Example function, `useState` is called.  Every time that `useState` is called after the first render, `useState` will grab the current value of the state variable and store it into `exclamationCount`.  We can then use that value in the code in the rest of the Example component.

This brings us to a few important points to note about calling `useState`.
1.  `useState` must be called at the top of the component.
1.  `useState` can not be called from inside a loop or an if statement

Let's say we want to add a button to add question marks to a question in the Example component above.  We can add new state variables by adding additional calls to `useState`:

```javascript

function Example() {

    const [exclamationCount, setExclamationCount] = useState(1);
    const [questionCount, setQuestionCount] = useState(1);

    // ...

}

```

React requires that calls to `useState` (and all hook calls) always happen in the same order for every single render.  Using `if` statements, loops or any control statements with calls to `useState` will cause errors.  Additionally, do not place calls to hooks inside of helper functions, because this can lead to the situation where you (or someone else using your code) may not realize that the helper function calls the hook and then call the helper function, which can lead to out of order hook calls.  If you always place all calls to `useState` and other hooks at the top of your component, you will avoid these potential problems.

###  Accordian Example

Lets rewrite the Accordian Example from the previous state lesson using functional components.

[TODO]


## Complex Pseudo Code Example with Diagram


## Check for Understanding

Use the following React Class Component to answer the questions

```javascript

// Simple Class Example


```

**Question 1** 