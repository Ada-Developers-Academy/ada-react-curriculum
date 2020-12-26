# Advanced Forms

In a previous lesson we talked about the idea of a controlled form, and built one as a React component. In this lesson we'll update the code to be a little DRYer, and to provide a better user experience.

## Learning Goals

By the end of this lesson we will be able to...

- Use our JavaScript knowledge to DRY up our controlled form
- Dynamically provide user feedback as they complete a form with validations

## Refactor of Event Handlers

You may notice the event handlers for the name and input fields are very similar:

```javascript
//  src/components/NewStudentForm.js
// ...
// event handlers
const onNameChange = (event) => {
  console.log(`Name Field updated ${ event.target.value }`);
  setFormFields({
    fullName: event.target.value,
    email: formFields.email,
  });
};

const onEmailChange = (event) => {
  console.log(`Email Field updated ${ event.target.value }`);
  setFormFields({
    fullName: formFields.fullName,
    email: event.target.value,
  });
}
```

We can refactor this into a single function that can update any field, based on a parameter.

```javascript
//  NewStudentForm.js
// ...
// event handlers
const onInputChange = (event) => {
  console.log(`Changing field ${ event.target.name } to ${ event.target.value }`);
  // Duplicate formFields into new object
  const newFormFields = {
    ...formFields,
  }

  newFormFields[event.target.name] = event.target.value;
  setFormFields(newFormFields);
}
```

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: ebeeac6e-9dfa-4730-b3ad-4f6d3b2d382e
* title: event.target.name
* points: 1
* topics: react, react-forms

##### !question

What is stored in `event.target.name`?
##### !end-question

##### !placeholder

What is stored in event.target.name?

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

When an input field is defined in the JSX with `<input name="example_name" value={value} onChange={eventHandler} />` and the callback function is passed an object `event` which describes the circumstates of the event.  

`event.target` is the DOM object which triggered the event.  `event.target.name` returns the `name` attribute of the `input` element, "example_name" in this case.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: 0330ed08-109a-4d18-832d-4bf3aea32af5
* title: Why use the subscript notation?
* points: 1
* topics: react, react-forms

##### !question

Why do we need to use subscript notation (square brackets) to update the state? In the past we used dot notation, which was more concise. What has changed?

##### !end-question

##### !placeholder

Why use []?

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

Because if we use the `.` operator, we cannot use a variable name for the  state attribute to change.  Instead we can use the `[]` and put a variable in the middle.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

### Wait what does `...formFields` do?

The code below is a a bit of JavaScript syntax called the **rest operator** which allow us to duplicate the `formFields` object.  

```javascript
const newFormFields = {
  ...formFields,
}
```

So the code above is the equivalent to:

```javaScript
const newFormFields = {
  fullName: formFields.fullName,
  email: formFields.email,
}
```

### Updating our Input handlers 

Then we can change the `onChange` handlers to use our new consolidated function:

```jsx
<div>
  <label htmlFor="fullName">Name:</label>
  <input name="fullName"
    onChange={onInputChange}
    value={formFields.fullName}
    name="fullName"
  />
</div>
<div>
  <label htmlFor="email">Email:</label>
  <input
    name="email"
    onChange={onInputChange}
    value={formFields.email}
    className={emailValid() ? "valid" : "invalid"}
  />
</div>
```

In this way we can DRY our code a bit and have one function to update any field in the `NewStudentForm`'s state.

## Form Validation

Now that our `NewStudentForm` component track the status of the form fields in its state, we have an opportunity to provide a better user experience. Let's validate form fields on the fly, and let the user know whether what they've typed so far is OK.

We can perform a validation on the email field with a function like this:

```javascript
// src/components/NewStudentForm.js
// ...
const emailValid = () => {
  return formFields.email.match(/\S+@\S+/) || formFields.email === '';
}
```

And give the user feedback on validation with:

```javascript
// NewStudentForm.js
// ...
<input
  name="email"
  onChange={onInputChange}
  value={formFields.email}
  className={emailValid() ? "valid" : "invalid"}
/>
```

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
<!-- Replace everything in square brackets [] and remove brackets  -->

### !challenge

* type: short-answer
* id: ebf8920b-e374-47fe-bab3-4e1dcf6ac7ca
* title: What does `className=` do?
<!-- * points: [1] (optional, the number of points for scoring as a checkpoint) -->
<!-- * topics: [python, pandas] (optional the topics for analyzing points) -->

##### !question

What does this line with `className=` do?

##### !end-question

##### !placeholder

What does this line with `className=` do?

##### !end-placeholder

##### !answer

/.+/

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, hidden, students click to view) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

The ternary in the `className=` allows you to render the form field with a different class, depending on the return value of the `emailValid()` function call.   This way you can give the user visual feedback if the field is valid or not.

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->


The form is re-rendered every time the state of the component changes, and this code will run `this.emailValid()` and if the email field is valid the input will have a class of `valid`, and if not it will have the class of `invalid`.  With a little CSS we can give the user valuable feedback as to the status of a form field.

**Wait!** You just used a ternary!  Remember from [react hello world](https://github.com/Ada-Developers-Academy/textbook-curriculum/blob/master/React/react-hello-world.md#what-is-jsx) we said you can't put an if-statement in a `{}` block?  You can put a 1-line ternary.  However a full multiline `if` statement will not work.

```css
input.valid {
  background: lightgreen;
}

input.invalid {
  background: pink;
}
```

Now the form fields will change color based on whether the input is OK!

You can see this implementation running on [code sandbox](https://codesandbox.io/s/ada-students-forms-advanced-jlqc9)

## Key Takeaway

Controlled forms give us programatic access to what the user's typing, as they type it. That opens up a whole world of opportunities for improving the user experience.

It also allows us to DRY up our code by using the `event.target.name` field to identify and update our state.

## Additional Resources

- [Instant Form Field Validation with React](https://medium.freecodecamp.org/how-to-use-reacts-controlled-inputs-for-instant-form-field-validation-b1c7b033527e)
