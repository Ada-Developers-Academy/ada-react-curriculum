# Intro to State

After this lesson, students will be able to:

- Give a high-level explanation of what state means
- Identify state in programs
- Read class-style components in React
- Identify when a class-style component is tracking and updating its state

## State, Generally

State is often a difficult word to define and understand in programming. On the one hand, you might be asked: "how did your program get into this state?" You might reply by showing the stack trace, or walking through code that you know has been run. You could be asked: "What is the state of the variable `x` on the third pass through this `for` loop?" In this case you could answer with the contents of that variable.

### !callout-info

## A Definition of State
State is the word we programmers use to describe the contents of a variable, or set of variables, at a given time. 

### !end-callout

As a definition, the two parts "contents of a variable" and "at a given time" are both important to understanding how we use it.

Here are a couple of quick examples of state:

- The details of a Driver in a ride share app, including whether or not they are available to drive right now.
- The moment to moment position of Pac-Man and the Ghosts during a game of Pac-Man.
- The current time on a stopwatch or clock.
- The restaurant that is currently selected while looking at Google Maps.

Importantly, all of these things can be tracked as data, and they are all things that are likely to change while the program is running. Put another way, 'state' is a way of naming data in our program that we expect to change!

So far, our React apps have had quite a bit of data, but it hasn't really had the opportunity to change much! In order to show a simple example, let's take a look at a brand new kind of component: the class-based, or "classical" component.

## Class-Based Components

There are two main types of components in React.  _Class Components_ and _Functional Components_.  Until now all the components you created in React were functions like this:

```javascript
// components/Student.js

//Our cute functional components that we know and love.
const Student = (props) => {
  return (
    <div>
      <h3>{props.fullName}</h3>
      <ul>
        <li>Class: C14</li>
        <li>Birthday: {props.birthday}</li>
        <li>Email: {props.email}</li>
      </ul>
    </div>
  );
};
```

These components are displaying our data right now, but they aren't able to update or adjust that data! Because there's no way to update the data given to them, they can be called "stateless components". But what if we wanted a straightforward way to track state in a component? What existing tool combines the behavior of functions with the storage ability of variables? That's right! Classes!

Let's take a quick look at what the functional component above would look like if it was class-based instead:

```javascript
// components/Student.js
import React from 'react';

class Student extends React.Component {
  constructor(props) {
    super(props); //props is passed in to the constructor of the component...
    this.state = {
      present: false,
    }
  }
  
  //It's okay to not understand what's going on here yet. 
  //Long story short, I can find out the contents of my <input> 
  //and send them back to the component's state!
  onSetPresent = () => {
    this.setState({present: !this.state.present})
  }

  render() {

    //...and when we want to access that data, we can use `this`
    return (
<div>
      <h3>{this.props.fullName}</h3>
      <ul>
          <li>Class: C14</li>
          <li>Birthday: {this.props.birthday}</li>
          <li>Email: {this.props.email}</li>
      </ul>
      // We will dig into what's going on in this line in the Events lesson.  
      // For now it's enough to know that clicking the button will call the updatePresent function!
      <button onClick={this.updatePresent}>
          Mark {this.state.present ? 'Absent' : 'Present'}
      </button>
</div>
    );
  }
}

export default Student;
```

And if you want to play around with this live, [check out this codepen.](https://codepen.io/dhelmgren/pen/dypRybV) Don't worry about how the pieces we haven't talked about yet work, just try it out and confirm that we can change the name of the student.

Okay, let's take stock of what's different: notice that since we aren't using a function, we can't just hand our `props` off in the usual way. Nope, instead, we need to create a constructor that can accept the `props` we want to pass it. Note that it's important that we call `super(props)` as a part of this statement! Our `props` contain more than just the info we the developers are sending down, so it's important that our parent class, `React.Component`, knows about them as well.

Also, take a look see in that constructor! We are using a special variable that `React.Component` gives us called `state`. Now, I know we just spent a long time saying that _any data_ that can change over time can be considered state. **That's still true!** React, however, is going to use this special object called `state` to know when it has to be reloaded. 

### !callout-info

## So Why Didn't We Learn Class Components Earlier?
React recently introduced a tool to the framework called 'hooks', which we'll be talking about soon. The introduction of hooks, in our opinion, make class components by in large _unnecessary_.  With hooks most applications can be written exclusively with functional components.  There are a few [specialized cases](https://reactjs.org/docs/error-boundaries.html) which require class components, but these scenarios are few and far between and may be replaced hook-based solutions at a later date.

### !end-callout

"Okay okay," I hear you saying, "But how are those fields getting changed!?"

Without getting to into the weeds, there is a function call called `setState` -which we call on line 11 in the codepen- that belongs to `React.Component`. It takes an **object that updates all the fields of your state to their new values** as its parameter, and checks it against the current `state` object. If there are new or updated fields in that object, React updates the DOM to reflect those changes. If not, React just gives the component a high-five and lets them on their merry way.

How do we know what's getting typed in the input box? How do we do that ourselves? Sorry! You'll have to wait it out with us on this one. The short answer is "event handling", which we will go into detail on later.

## But That's The Old Way

Facebook's React team noticed something interesting and somewhat troubling about the way React was being used. Developers around the world were using the React framework, but so many of them weren't using functional components very often! Turns out, tracking state is something that a lot of components need to do, and since developers **loathe** rewriting code, most components were written as classes in order to save the headache of having to update the component later, when someone decided it would need state.

On top of that, this style of component is not as DRY. In fact, some might say it's getting rather sweaty. It has a lot of syntax that we have to remember, and there's a few annoying speedbumps when using `setState` that we won't go into detail about (trust us, it's kind of prickly).

Since React came up with hooks, and since we want to keep things DRY, we are going to focus during this curriculum on how we use hooks to make function-style components stateful.

### !callout-info

## But if we're going to use functional components, why do we care?

React has been around for a while now and a great deal of code and documentation has been written using class components.  React is not eliminating class components and a great number of developers find the abstraction of class components attractive.  It's important to know how they work and how to convert between functional and class components.

### !end-callout
