# JavaScript Data Types and Control Flow

## Expressions, Values, and DataTypes

In JavaScript, we call bits of data values.
The simplest of these values are called primitives.
There are 5 primitive types in JavaScript:

1. Numbers
2. Strings
3. Booleans
4. Undefined
5. Null

### Numbers

Numbers are a good place to start because JavaScript represents numbers and lets us interact with numbers in a way that is familiar to what we are used to in arithmetic.

#### Representation

Numbers are simply represented by their digits. In JS `4`, `13`, `-3`, `2.5` and `10e3` all mean just what youd expect them to mean.
To create a number in JS, just write it.

In your browser console, type `42` and hit **Enter**.

![REPL 42](https://user-images.githubusercontent.com/7882341/27314489-4275c7b4-5542-11e7-8c16-6b6431f9cc42.png)

This is a REPL.
When you hit **Enter**, you tell the computer:

1. **R**ead the JavaScript I just wrote (`42`).
2. **E**valuate it (calculate its value, `42`).
3. **P**rint the value that was evaluated (`42`).
4. **L**oop, returning control to the user and wait to be asked to read the next line.

#### Interaction

The basic mathematical operators work as expected as well.

In your browser console, type `2 + 2` and hit **Enter**.

![REPL 2 + 2](https://user-images.githubusercontent.com/7882341/27314738-933484d2-5543-11e7-9c94-32cc53de7f74.png)

The REPL has just:

1. **R**ead the JavaScript (`2 + 2`).
2. **E**valuated it (calculated its value, `4`).
3. **P**rinted the value that was evaluated (`4`).
4. **L**oop, returning control to the user and wait to be asked to read the next line.

#### Further Consideration on Numbers

- You can find a full list of arithmetic operators [in the expressions and operators MDN documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Arithmetic_operators).
Start with your intuition before checking documentation.
This will be a frustrating process at first but will help to develop your intuition.
- While JavaScript is perfectly happy to accept non-whole numbers (i.e. [floating point numbers](http://floating-point-gui.de/languages/javascript/) or floats) and return them as the result of  an expression, floating point numbers are not exact and when used in series of calculations this lack of percision is exacerbated.
Check out [this site](http://floating-point-gui.de/) devoted to the intricacies of floating point numbers.

### Expressions, Variables and Statements

- The term **Evaluate** is closely related to the idea of an [**Expression**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions) in JavaScript.
- Just about everything we write in JavaScript is an expression.
- An expression is just some code that resolves (evaluates) to a value.
- By writing the operations above, we were telling the browser "evaluate these operations"
- Many expressions simply produce a value (like the examples shown above) others have side-effects, meaning that they cause some change in the program or the world.
  - The quintessential effectful operation is **assignment**, done with the `=` operator (e.g. `answer = 42`).
  Subsequently, the **variable** `answer` evaluates to the value assigned to it (`42`).
- While we can build up arbitrarily long expressions, this quickly becomes limiting.

#### Statements and Variables

- A conceptual line of JavaScript is a statement (conceptual because literally can span multiple lines).
- statement:JavaScript::sentence:English
- Statements are executed one after another top to bottom.
- A statement can be:
  1. An **expression** in which case the expression is executed for side effects.
  2. A statement can be a **delaration** which creates a variable that is now available to be used in any following expression.
    - the keywords for declarations are `var`, `const`, and `let` which all do something very similar with subtle differences.
    - `var` was around long before `const` and `let` which are newer.
    - People tend to use either `var` or `const` and `let`.
    - I'm going to use `const` and `let` but they could all be replaced with `var`.
    - Frequently a variable is declared and assigned a value in the same statement (it is required with `const` and common with `let`). The `=` operater performs assignment in JS.

```js
const myVar = 42
console.log(myVar)

const sum = myVar + 8
console.log(sum)

const doubleSum = 2 * sum
console.log(doubleSum)

let unassigned;
console.log(unassigned)
```

  3. A statement can be **control flow** which we will discuss before the end of this class.
  4. A statement can be a **function declaration** which we will discuss this afternoon.
-

## Strings

- Strings are the way JavaScript represents text.
- Strings are a series of zero or more characters wrapped in single or double quotes (`'Hello World!'`, `"Hello World!"`, `'h'`, and `''` are all examples of strings in JavaScript).
- The only operator for strings is `+` which concatinates.
  - Concatination used to be much more common before ES2015 introduced string templates which allows interpolation of variables using backticks.

```js
let message = `the first number I picked was ${myVar}`
console.log(message)

message = 'the sum of the number I picked and 8 is ' + sum
console.log(message)
```
- **Type coercison** is when one type is converted into another automatical as happened to `42` and `50` here.
- In this case it goes smoothly and sometimes JS can be really helpful

```js
let difference = 20 - '10'
console.log(difference)
```

- But a small mistake can cause problems when we rely on this.

```js
difference = 20 - '$10'
console.log(difference)
```

### Booleans

- Booleans are the simplest data type, there are only two `true` and `false`
- There operators are `!`, `||`, `&&`, and the ternary `condition ? thenExpression : elseExpression`
- Like numbers to strings and vice-versa, JS will convert any value to a boolean.
- There are only five values that evaluate to `false` when converted to boolean; this is called being **falsey**
  - `''` - empty string
  - `0` - number zero
  - `false` - boolean false
  - `undefined` - value given to declared variables that are not given values
  - `null` - value representing nothing
- A common way to get booleans is as the result of a comparison.
  - There are two equality operators `==` and `===` (and two matching inequality operators `!=` and `!==`)
  - We prefer strict equality
  - We can also compare numbers with `<`, `>`,`<=`, `>=`

## Control Flow

We are going to put together the above in a famous coding puzzle FizzBuzz while also discussing control flow.
The puzzle goes like this:
- Count from 1 to 100 printing something for each number
- If the number is divisible by 3 print "Fizz"
- If the number is divisible by 5 print "Buzz"
- If both print "FizzBuzz"

## [`if...else`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

The `if...else` statement has the structure:

```js
if (condition) {
  // this code runs if the condition evaluates to true
} else {
  // this code runs if the condition evaluates to false
  // this code does not run if the condition evaluates to true
}
```

But we are free to omit the else part if we don't have need to run anything if the condition is false.

```js
let num = 9
if (num % 3 === 0) {
  console.log('fizz')
}
if (num % 5 === 0) {
  console.log('buzz')
}
```

## [`while`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)
A `while` loop is like an `if` statement but it will repeat the content of its block repeatedly until the condition becomes false.

```js
num = 0
while (num <= 100) {
  console.log(num)
  num += 1 // short-hand for num = num + 1
}
```

We can update the while loop so that it uses our divisibility logic:

```js
num = 0
while (num <= 100) {
  if (num % 3 === 0) {
    console.log('fizz')
  }
  if (num % 5 === 0) {
    console.log('buzz')
  }
  num++ // short-hand for num += 1
}
```

We're making progress, we can update our logic adding `else` statements so that we know when we have not logged 'fizz' or 'buzz'.

```js
num = 0
while (num <= 100) {
  if (num % 3 === 0) {
    console.log('fizz')
  } else if (num % 5 === 0) {
    console.log('buzz')
  } else {
    console.log(num)
  }
  num++
}
```

Finally we want to add one more conditional to print 'FizzBuzz' if the number is divisible by both 3 and 5.

```js
num = 0
while (num <= 100) {
  if (num % 3 === 0 && num % 5 === 0) {
    console.log('fizzbuzz')
  } else if (num % 3 === 0) {
    console.log('fizz')
  } else if (num % 5 === 0) {
    console.log('buzz')
  } else {
    console.log(num)
  }
  num++
}
```

This duplicate checking of divisibility isn't ideal but a more concise solution is left as an exercies.

## [`for`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)
The pattern we used above to loop down from `100`, (1) initializing a counter: `num = 0`, (2) checking some condition `num <= 100`, and (3) incrementing the counter `num++`, that there is a special syntax to accomidate it.

```js
for (let x = 0; x <= 100; x++) {
  if (x % 3 === 0 && x % 5 === 0) {
    console.log('fizzbuzz')
  } else if (x % 3 === 0) {
    console.log('fizz')
  } else if (x % 5 === 0) {
    console.log('buzz')
  } else {
    console.log(x)
  }
}
```

## Getting User Input

We've learned about basic data types, but it'd be nice if we had a way of getting user input into our browser. We'll learn some ways to use forms and such later in the course, but for now, we'll be getting user input using the `prompt()` function.

At any point in our JS code, if we write prompt(), a pop up box will open in our browser for a user to enter in text.

```js
// prompts user and stores value in the variable
var valueOfPrompt = prompt()
// logs value stored
console.log(valueOfPrompt)
```

You can also pass in a string as an argument to have the pop up box contain that string as a ... prompt.

```js
var age = prompt("How old are you?")
// ES6 String Interpolation
alert(`You are ${age} years old.`)
// ES5 Version
alert("You are " + age + " years old.")
```

Whatever we type into the textbox in the window that prompt() brings up, is returned by prompt to the variable age.

### Adding Conditionals

We could write a check to comment on the user's name.

```js
var name = prompt('What is your name?')
alert(`Hello, ${name}.`)

if (name === 'John') {
  alert("What an excellent name!")
} else {
  alert( "That's a pretty good name!" )
}
```

## Exercise: [Temperature Converter](https://github.com/ga-wdi-exercises/temperature_converter)

### Null & Undefined

The values `null` and `undefined` both mean essentially the same thing, they hold no value.

The difference is that `undefined` impliese nothing because it was never was anything while `null` implies explicitly set to nothing.

## Collections

Frequently (more often than not) in programming, we are dealing with groups of things whether those things are posts on a social media site, pairs of coordinates in a mapping application, transactions in accounting software, or data points in a graphing tool.

In JavaScript we have two kinds of collections.
They differ in how you access their elements.

### Arrays

Arrays are list of things accessed by their position in order, or their index.
Indexes start at 0.
It is totally legal to have arrays with elements of different types but it isn't very common.

```js
const myArr = [4, 5, 6, 7]
console.log(myArr)
console.log(myArr[1])
myArr[1] = 8
console.log(myArr)
myArr.push(9)
console.log(myArr)
console.log(myArr.pop())
console.log(myArr)
```

There are some handy methods that turn strings into arrays and vice-versa

```js
const alphabet = 'abcdefghijklmnopqrstuvwxyz'
console.log(alphabet)
const alphArray = alphabet.split('')
console.log(alphArray)
const namesArray = ['Betsy', 'Ann', 'Bill']
console.log(namesArray)
const namesString = namesArray.join(' and ')
console.log(namesString)
```

### Objects

Objects are similar to Arrays but rather than accessing the elements by index, elements in objects have **keys**.

```js
const lesson  = {
  subject: 'Types and Conditionals',
  students: 24,
  date: 'Friday, 30 June 2017'
}

console.log(lesson['students'])
console.log(lesson['date'])
lesson['subject'] = 'Types and Control Flow'
lesson['time'] = 'AM'
console.log(lesson)
```

Objects are very important in JavaScript and a subject we'll spend a lot more time on.

### Exercise: [Luhn Algorithm](https://github.com/ga-wdi-exercises/luhn_algorithm#challenge-validating-credit-card-numbers)


## Resources

- [Khan Academy Intro to Programming JS](https://www.khanacademy.org/computing/computer-programming/programming#intro-to-programming)
- [You Don't Know JS: Up & Going](https://github.com/getify/You-Dont-Know-JS/blob/master/up%20&%20going/README.md#you-dont-know-js-up--going)
- [Eloquent JavaScript](http://eloquentjavascript.net/)
