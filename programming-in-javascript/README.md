# Programming In JavaScript

This is written in article form but could be used as a script for a lesson.

I think this could be useful for the technical workshop 2?

## Learning Outcomes of this lesson

* Exposure to building up a program from simple to more complex while reviewing core programming concepts
* Show that programs are useful! They aren't just a series of functions that we have to complete for an assignment
* Re-emphasizing **input** > **logic** > **output**
* There is no "right" way to write a program (though there may be more efficient ways)

## Why we program... 

Programs help us **automate** tasks that would otherwise be tedious and time consuming. Imagine we wanted to flip a coin 100 times. Rather than doing it ourselves, we can write a program to do it for us.

**How?** Most programs follow the general structure: **input** > **logic** > **output**. When writing a program, we can think about the output we want and how we can get to that result when the program is given inputs.

Here's an example of a program for flipping a coin. ([Run it here!](https://replit.com/@BenSpector/coinFlilp#index.js))

> Note: Not all inputs are provided by a human user. In this case, the random number is the "input" and it is provided by the computer. 

```js
// The random number is the "input". 
// It will be a decimal between 0 and 1
let randomNumber = Math.random();

// Half of the results will be less than .5 so we'll call those heads
let isHeads = randomNumber < .5;

// Use that boolean to choose the string we want to print
let coinFlipResult = isHeads ? "Heads" : "Tails";

// Output the result
console.log(coinFlipResult);
```

**A Note about math in CS**
> These examples use math that may appear daunting (or excite you!). These particular examples of using math to generate a random number and working with that random number is quite common. It will be useful to understand how `Math.random()`, `Math.ceil()`, and `Math.floor()` work. That said, most of the math you will do as a programmer will not be much more complicated than this.

## Programming in the Console

In the early days of programming, programs were used exclusively in a terminal console and were only text-based.

![](https://homepages.uc.edu/~thomam/Intro_OOP_Text/Images/console%20app.png)

These kinds of programs are still valuable for simple tasks like fliping a coin.

## The creativity of programming / a review of core coding concepts
Program logic can be written in many different ways. This is what makes programming a *creative* endeavor. 

In particular, **variables** and **functions** allow us to organize our code in unique ways. **Comments** make our code clear for new readers and illuminate our thought process. **Loops** automate processes many times.

### Consider these different ways to write a program for rolling dice.

Without variables, our code is short and concise… but maybe a bit hard to read…
```js
console.log(Math.ceil(Math.random() * 6) + Math.ceil(Math.random() * 6));
```

Variables let us name our data and break up the logic. Comments clearly show the steps involved.

```js
// First, get two random numbers between 1-6
let roll1 = Math.ceil(Math.random() * 6);
let roll2 = Math.ceil(Math.random() * 6);

// Then, add them to get the total
let finalRoll = roll2 + roll2;

// Output
console.log(finalRoll);
```

Functions let us re-use logic and keep our code D.R.Y. (Don’t Repeat Yourself)

```js
// First, make a reusable function for rolling dice
function rollDie() { 
  return Math.ceil(Math.random() * 6);
}
// Use the function to get the finalRoll amount
let finalRoll = rollDie() + rollDie();
console.log(finalRoll);
```

Parameters in functions open the door to expanded features: Roll *any* kind of dice

```js
// Functions are like mini programs, they have their own input, logic, and output
function rollDie(sides) {  
  return Math.ceil(Math.random() * sides);
}

// Arguments are "passed" to functions that have parameters.
let finalRoll = rollDie(20) + rollDie(20);

// output
console.log(finalRoll);
```

We can use functions to help us write other functions. Loops let us automatically do something MANY times: Roll an s-sided die any number of times

```js
// We can use this function to help us write another function
function rollDie(sides) {  
  return Math.ceil(Math.random() * sides);
}

function rollMultipleDie(times, sides) {
  // Keep a running tally
  let total = 0;

  // Call rollDie(sides) the specified number of times
  for (let i = 0; i < times; i++) {
    total += rollDie(sides);
  } 

  // return the total
  return total;
}

// Roll 5 20-sided die
let result = rollMultipleDie(5, 20);
console.log(result);

// Roll 10 6-sided die
console.log(rollMultipleDie(10, 6));
```

We can add in user input to make it more interactive

```js
function rollDie(sides) {  
  return Math.ceil(Math.random() * sides);
}

function rollMultipleDie(times, sides) {
  // Keep a running tally
  let total = 0;

  // Call rollDie(sides) the specified number of times
  for (let i = 0; i < times; i++) {
    total += rollDie(sides);
  } 

  // Output
  return total;
}

// Get User Input
let times = prompt("how many die would you like to roll?");
let sides = prompt("how many sides are on the die you are rolling?");

// Logic
let result = rollMultipleDie(times, sides);

// Output
console.log(result);
```

## Finally, a few notes...

Always TEST your code!
- If you are using random inputs, run the program many times and record the results to see if it behaving randomly or trending towards certain results.
- Call your functions with multiple inputs. Verify that the outputs are what you expect.


Come up with as many variations of the same function as possible.
- There is not a single "right" way to write a function. 
- Each variation will give you a better sense for when to use your programming tools. 
- Ways to vary your code include:
  - Use alternative function names and/or parameter names
  - Use more/fewer variables within the function
  - Use a `while` loop instead of a `for` loop
  - Use higher order functions

Do we really need to teach semicolons?
- Yes, it's best to use them and [here is why](https://dev.to/adriennemiller/semicolons-in-javascript-to-use-or-not-to-use-2nli)
- Semicolons for expressions, not needed for most control structures 
- Call me out when I don’t use semicolons!