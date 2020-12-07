# Introduction to React

<iframe src="https://adaacademy.hosted.panopto.com/Panopto/Pages/Embed.aspx?pid=c614976d-173a-4ab7-addb-ac8a0032792b&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

## Learning Goals

By the end of this lesson we will be able to...

- Explain what is React in plain English?
- Explain why we learn React at Ada?
- Identify who is using React?
- Describe at a high level the Virtual DOM
- Describe the concept of a React Components

## What is React?

React is an [open-source](https://github.com/facebook/react) JavaScript library for building user interfaces. It encompasses only the **V** in the MVC Pattern.

React is modular through the use of **components**. A component is a JavaScript function or class which knows how to render pieces of the user interface (HTML and CSS) and assign them behavior (event handling). Each component manages its own state and then components can be composed within one another to create a complete web application.

## Why React?

There are a lot of reasons that technology teams are switching to use React. You can read one of those from the Netflix team written a few years ago on their transition in the [Additional Resources](#additional-resources) below.

Here at Ada, we teach React because it equips you with these skills:

- Designing an application to leverage the constructs and patterns of a library
- Using syntax that you've already seen (with HTML & CSS) in a slightly different way with JSX
- Designing a modular application with individual pieces that fit together
- Understanding and building with a popular, modern front-end JavaScript library

## Who is using React?

React was originally developed by Facebook so they're the first one to mention. Also sites like Airbnb, Dropbox, Instagram and Netflix use React. You can read even more companies in the [Additional Resources](#additional-resources) below.

[This chart](https://bit.ly/3giUg0X) is also a great indicator of how much more popular React has become over the past few years.

## Virtual DOM

One of the most enticing things about using React is the Virtual DOM. React provides a managed copy of our DOM to allow us to make quick changes to our DOM. It allows us to dynamically update our pages by doing a quick comparison between the Virtual DOM that React provides and the real DOM. Then, only the updates that are necessary are made.

## Components

React is made up of **Components** that work together. A very basic component can render some formatted HTML within your application. A more complex series of components can pull data in from a database or API, populate that into formatted HTML and render other components.

## Key Takeaway

React is extremely popular right now and is growing in popularity. React focuses on writing JavaScript functions which render and manage components of the user interface (webpage for React on websites).  The Virtual DOM makes React a desirable solution for web applications where performance and modular are in consideration.

## Additional Resources

- [React Virtual DOM](https://www.codecademy.com/articles/react-virtual-dom)
- [32 Sites Built with React](https://medium.com/@coderacademy/32-sites-built-with-reactjs-172e3a4bed81)
- [Netflix likes React](https://medium.com/netflix-techblog/netflix-likes-react-509675426db)
- [Free Code Camp React Handbook](https://medium.freecodecamp.org/the-react-handbook-b71c27b0a795)
