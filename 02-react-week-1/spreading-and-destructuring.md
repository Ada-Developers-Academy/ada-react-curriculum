# Rest, Spread & Destructuring



<!-- BEGIN CHALLENGE -->

### !challenge

* type: short-answer
* id: d590caab-d340-45b8-a57c-ee88596c2b50
* title: Combine Two Arrays
<!--Other optional fields (checkpoints only) -->
<!--`points: 1`: the number of points for scoring as a checkpoint-->
<!--`topics: python, pandas`: the topics for analyzing points-->

##### !question

```javascript
const morningTracks = ['Master of Puppets', 'Black Metal', 'Paranoid'];
const eveningTracks = ['Ella Mai', 'American Teen', '17'];

// Merge the above arrays into a single array

```

##### !end-question

##### !answer

/.+/

##### !end-answer

##### !placeholder

you code here...

##### !end-placeholder

<!--optional-->
##### !hint

##### !end-hint

<!--optional, checkpoints only-->
##### !rubric

##### !end-rubric

<!--optional-->
##### !explanation

`const combined = [...morningTracks, ...eveningTracks];`

##### !end-explanation

### !end-challenge

<!--  END CHALLENGE  -->

### Spread operator with strings

You can also break a string into an array of individual characters with the spread operator.

```javascript
const letters = [...'abc']; // ['a', 'b', 'c']
```

### Combining the spread operator with destructuring

You can also use destructuring along with the spread operator to remove individual elements from an array.

```javascript
const list = ['peanut butter', 'chocolate', 'vanilla', 'cookies and cream'];

const [first, second, ...rest] = list;

console.log(first); // peanut butter
console.log(second); // chocolate
console.log(rest); // vanilla,cookies and cream 
```

### Spread operator with object literals

The spread operator can also be used to combine or merge two object literals.  The code below merges two object literals.

```javascript
const ada = {
  name: 'Ada Lovelace',
  age: 103,
};

const language = {
  name: 'C#',
  about: 'A strongly typed language by Microsoft',
};

const merged = { ...ada, ...language };

console.log(merged); // { name: 'C#', age: 103, about: 'A strongly typed language by Microsoft' }
```

Notice that it merges the objects in order, so that `ada`'s name is overwritten by that of `language`.  It also creates an entirely **new** array which shallowly copies elements of the original object.  This means that sub-objects or arrays can be references to the original.

```javascript
const student = {
  name: 'Bob',
  grades: [3, 4, 5],
  address: {
    street: '123 Elm St',
    city: 'Trenton',
    state: 'NJ',
    zip: 11111,
   }
};

const newStudent = { ...student };

newStudent.name = 'Alice';
newStudent.address.street = '4th avenue';

console.log(newStudent);
console.log('---');
console.log(student);
```

The above code outputs: 

```javascript
{
  name: 'Alice',
  grades: [ 12, 4, 5 ],
  address: {
    street: '4th avenue',
    city: 'Trenton',
    state: 'NJ',
    zip: 11111
  }
}
---
{
  name: 'Bob',
  grades: [ 12, 4, 5 ],
  address:
   { 
     street: '4th avenue',
     city: 'Trenton',
     state: 'NJ',
     zip: 11111
  } 
}
```
<br/><br/>

**Question** Look at the code above.  Why do both Alice & Bob have a street address of 4th avenue?

<details>
  <summary>
    Click here to see the answer.
  </summary>

  The `...` operator is making a _shallow_ copy of the original object.  It does not copy all the values of `student`'s properties.  It instead copies the _reference_ to the `address` object and the `grades` array.  To make a _deep copy_ of the original object you would need to do things [differently.](https://medium.com/technofunnel/deep-and-shallow-copy-in-javascript-110f395330c5)
</details>


## Examining Code

The following code simulates merging new permissions into a user account.  With a partner examine the code and answer the questions:

```javascript
const combinePreferences = function combinePreferences(user, ...otherPrefs) {
  otherPrefs.forEach((preference) => {
    user.preferences = { ...user.preferences, ...preference}
  });
  return user;
}

const user = {
  name: 'ada',
  preferences: {
    superuser: true,
    billableUser: false,
  }
};

const billing = {
  billableUser: true,
  getsReports: true,
  canDeployApps: false,
};

const project = {
  canCreateProjects: false,
  canDeployApps: false,
  canDeployToTest: true,
};

console.log(combinePreferences(user, billing, project));
```

**Questions** 

As a pair read the code and predict the result.  Then run the resulting code in the terminal.

1. Identify where the spread operator and rest parameters are.
1. Did it output what you expected?  Why?
1. Is the `forEach` loop necessary?  Could it be done without a loop?  Why or why not?

<details>
  <summary>
    Click here to see some answers.
  </summary>

  1. The rest parameter occurs at `combinePreferences(user, ...preferences)`, and the spread operator is used twice at `user.preferences = { ...user.preferences, ...preference}`.  
  1. The result is the user object with it's preference attribute updated merging them in order of appearance.
  1. The `forEach` loop is needed because using the spread operator on an array will result in merging in the array's keys (index numbers) and values into the preferences.  

</details>

## Review

- Rest parameters can be used to write a method taking an unlimited number of arguments.  
- Using rest parameters arguments are added to an array parameter.
- The spread operator does the inverse, taking an iterable object, like an array or string and converting it to individual items to be used in a function call, or instantiating a method.
- The spread operator can also be used to merge objects.

## Resources

- [MDN on Destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [MDN on Rest Parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)
- [MDN on Spread Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
- [JavaScript.info on Rest & Spread](https://javascript.info/rest-parameters-spread-operator)
