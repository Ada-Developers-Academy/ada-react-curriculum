# Rest, Spread & Destructuring

## Learning Goals

By the end of this lesson you should:

- Be able to use the rest parameter syntax to make functions which accept an unlimited number of arguments.
- Be able to explain what the spread operator does and where it is useful.

## Destructuring

Destructuring is a way to peel items from an object or array into individual variables. 

### Destructuring Arrays

With an array you can use square brackets `[]` on the left side of an assignment to pull individual elements from an array in the order they are listed.  

```javascript
const list = [1, 2, 3, 4];

const [first, second, third] = list;
console.log(first);  // 1
console.log(second); // 2
console.log(third);  // 3
```

It can also allow you to swap to variables without an additional temporary variable.

```javascript
let firstName = 'Team';
let lastName = 'Rocket';

[lastName, firstName] = [firstName, lastName];
console.log(lastName); // Team
console.log(firstName); // Rocket
```

### Destructuring Objects

With objects, you can pull items from an object and assign them to variables with the same name as the key.  

```javascript
const pet = {
  name: 'Stinker',
  age: 12,
  human: 'Chris',
  species: 'Cat',
};

const { name, human } = pet;

console.log(name); // Stinker
console.log(human); // Chris
```

This makes it easier to use specific attributes of an object without having to write the full `pet.name` and `pet.human` each time.  

## Rest Parameters

Sometimes it's helpful to write a function that can take any number of arguments.  For example below, `sum` can only take two arguments

```javascript
const sum = function sum(x, y) {
  return x + y;
}

sum(3, 4); // 7
```

If we wanted to add up an unlimited number of arguments we could use a rest parameter by adding the `...` operator before the parameter name.

```javascript
const sum = function sum(...args) {
  // Loop through each item in args adding them together.  
  let sum = 0;
  args.forEach((item) => {
    sum += item;
  });
  return sum;
};

sum(3, 4, 5); // 12
sum(5); // 5
sum(3, 4); // 7

sum(); // 0
```

The parameter to the right of the `...` operator is **always** an array and contains any arguments unclaimed by parameters to the left of the rest parameter.  A rest parameter must be the last parameter in an argument list, but it does not have to be the only argument, for example.

```javascript
const greet = function greet(greeting, ...people) {
  console.log(`${greeting} ${people}`);
}

greet('Hello', 'Ada', 'Grace', 'Katherine'); // Hello Ada,Grace,Katherine
```

In the above example `greeting` takes the value `'hello'` and all the subsequent arguments are stored in the `people` array.  So rest parameters take the _rest_ of the arguments and put them into an array.  

A few things to highlight:

- A rest parameter must be the last item in a functional expression or declaration.
- A function may only have **one** rest parameter.

## The Spread Operator

So rest parameters let us take otherwise normal arguments and put them into an array.  Sometimes however you want to do the reverse.  It can be helpful to peel off elements of an array into arguments to a method.  

```javascript
const calculateBill = (appetizer, mainCourse, desert) => {
  return 1.08 * (appetizer + mainCourse + desert);
}

const prices = [3.75, 15.80, 10.0];

console.log (calculateBill(...prices)); // 31.914
```

In the above example:  `calculateBill(...prices)` is the equivalent to doing:  `calculateBill(prices[0], prices[1], prices[2])`, a much more compact syntax.

The `Math.max` function is a good example of a function you might choose to use the spread operator on, it takes numeric arguments (unlimited size) and returns the largest item.  

```javascript
const list = [3, 7, 25, 1, -50];

const biggest = Math.max(...list);

console.log(biggest); // 25
```

**Wait so these look the same!**  While these both involve the same three periods, examine where the `...` operator is placed.  

- In rest parameters the `...` operator appears in the **function parameters** while in the example above, we used the spread operator to convert an array into individual items in the **function call**.  

- The spread operator can only be applied to [iterable values](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) like arrays and strings while rest parameters take in any kind of arguments and place them into an array.

### Merging Arrays

You can also use the spread operator to expand an array to a list of elements for a new array.

```javascript
const newStudent = 'Ada';

const studentList = ['Charles', 'Grace', 'Katherine', 'Alexandra'];

const newList = [newStudent, ...studentList];

console.log(newList); // Ada,Charles,Grace,Katherine,Alexandra
```



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

