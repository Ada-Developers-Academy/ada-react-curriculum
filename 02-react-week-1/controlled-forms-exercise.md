# Controlled Forms Exercise

Controlled forms are an important part of the React style of web programming. Let's get some practice with them!

**Timebox yourself to 90 minutes**
## Instructions

This is an in-class exercise and will not be submitted.

### Wave 1

Create a new React app with `npx create-react-app`. Something like `npx create-react-app forms-exercise` will create a new project named `forms-exercise` and will do just perfectly.

This app will have one component called `SignupForm`.

The form should have five input elements:
- First name
- Last name
- Email
- Password
- "Create account" button

The form should be controlled by React, that is, use state and `onChange` event handlers to manage the data.

When the form is submitted, it should log the user's information to the console and clear the form fields.

### Wave 2 (Optional)

Style the form to look like this:

![sign-up form](images/signup-form.jpg)

Don't worry about the Facebook / Twitter buttons - either leave them out or make them do nothing.

### Wave 3 (Optional)

Create another component, `UserInfo`, that displays the user's name and email (not password). Once the form is submitted, hide the form and display the `UserInfo` component with the user's information instead. Style it slickly.

## Solution

You can see our [solution to waves 1-2 on CodeSandbox.io](https://codesandbox.io/s/demo-react-form-lxe3h)
## Sources

- Signup form image: https://w3layouts.com/signup-form-flat-template/