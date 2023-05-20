# Programming In JavaScript

This is written in article form but could be used as a script for a lesson.

I think this could be useful for the technical workshop 2?

## Learning Outcomes of this lesson

* Review Learn JavaScript concepts
* Exposure to many examples of the same function, written in different ways
* Demonstrate the progression of a program to expand its features
* Show that programs are useful! They aren't just a series of Math-related functions that we have to complete for an assignment
* Understanding that "everything is just **inputs** and **outputs**"
* There is no "right" way to write a program (but there are styles, each with their own tradeoffs)

## Why we program... 

Programming is the act of building a digital tool we call "software". All software serves some purpose for making our lives easier (or more enjoyable).  

Certain tools, like a hammer (increasing our strength) or a car (increasing our speed), enhance our phsycial abilities in the material world. **Software enhances our abilities in a digital world to perform tedius, predictable, and repeated tasks** with no effort at all.

That is, if we can solve the puzzle of how to instruct our computer to do so. 

## Spoiler: The "puzzle" of a program is just inputs and outputs

Imagine we wanted to flip a coin 100 times. A perfect task for a program to solve!

**How?** Most programs are in some way, shape, or form, simply the process of converting **inputs** to **output**. 

### What counts as an "input"?"

The **inputs** to a program typically come from a user. The most basic input that a user can provide, is clicking a button to run the program. 
    * Imagine turning on a toaster. That's user input.
    * Imagine pressing a button to start your dishwasher. That's user input.
    * Imagine turning your car key in the ignition. That's user input. 
    
Inputs can also be more than just flipping a switch. They can include keyboard inputs, gaming controller inputs, mouse clicking and movement inputs, touch inputs, and much more!

### What counts as an "output"?"

The output is often the more amorphous (and fun) side of the equation to think about, and the exact output of your software may be an experience (or collection of experiences) that your user will have. 

**Q: How would you describe the output of our task?**
<details></summary>Ben's Answer</summary>

I want to know the results of flipping a coin 100 times. To be more specific, I want to know how many heads and how many tails came up out of those 100 flips.

</details>

### Writing the program

In order to flip a coin 100 times, I need to figure out how to flip a coin once.

> _This is called "decomposition". I took the bigger problem (flip a coin 100 times) and turned it into a smaller problem (flip a coin once)._

Here's an example of a program for flipping a coin one time. ([Run it here!](https://replit.com/@BenSpector/coinFlilp#index.js))

```js
// We want to know how many heads and tails will be flipped.
let numberOfHeads = 0;
let numberOfTails = 0;

// First generate a random number between 0 and 1 (`Math.random()` is a helpful "function" that handles that tricky task) 
let randomNumber = Math.random();

// If the random number is less than 0.5, we'll say it was a "heads"
if (randomNumber < .5) {
  numberOfHeads += 1; // increase the value of `numberOfHeads` by 1
}

// otherwise, tell the user it was a "tails"
else {
  numberOfTails += 1; // increase the value of `numberOfTails` by 1
}

// Display the result to the user with some formatted text
console.log(`H: ${numberOfHeads}  T: ${numberOfTails}`)
```

Now, for repeating this process 100 times:

```js
// We want to know how many heads and tails will be flipped.
let numberOfHeads = 0;
let numberOfTails = 0;

// We've turned that code into a re-useable "function" called `flipCoinOnce`
// But only the code responsible for flipping the coin and counting the result...
let flipCoinOnce = () => {
  let randomNumber = Math.random();
  if (randomNumber < .5) {
    numberOfHeads += 1;
  } else {
    numberOfTails += 1; 
  }
}

// That way, we can "Invoke" the function called `flipCoinOnce` 100 times...
for (let i = 1; i <= 100; i = i+1) {
  flipCoinOnce();
};

// ...before displaying the result to the user with some formatted text
console.log(`H: ${numberOfHeads}  T: ${numberOfTails}`)
```

#### The order of your operations matters!

**A Note about math in CS**
> These examples use math that may appear daunting (or excite you!). These particular examples of using math to generate a random number and working with that random number is quite common. It will be useful to understand how `Math.random()` work. Don't worry, most of the math that you will have to do has been made loads easier by other programmers before us. Our computers are powerful calculators!
> It is, however, important to understand how the order of your operations matters"

## Programming in the Console

In the early days of programming, programs were used exclusively in a terminal console and were only text-based.

![](https://homepages.uc.edu/~thomam/Intro_OOP_Text/Images/console%20app.png)

To start, we'll write programs that use the console for input and output. These are called Command Line Interfaces (CLIs). These kinds of programs are still valuable for simple tasks like fliping a coin or rolling dice. 

Later on, you'll get the chance to use HTML, CSS, React, and other front-end tools to create Graphical User Interfaces (GUIs) that users can interact with on a website. We'll still have the console, but it will be used more for **testing** and **debugging**.

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

### Adding Features

Adding Features

Now, we can start expanding the features of the program by adding in:
* Parameters which inject flexibility into our functions
* Loops which allow us to easily repeat a task many times
* Arrays offer a new way to organize data that allows for iteration (remember to make use of higher-order functions!)

Parameters in functions make the function more flexible. Instead of sticking with 6 sides on the die, we can make the program roll *any* kind of dice that we specify.

```js
// Functions are like mini programs, they have their own input, logic, and output
function rollDie(sides) {  
  return Math.ceil(Math.random() * sides);
}

// Arguments are "passed" to functions that have parameters.
// Here, we tell the function that we want to roll one die with 20 sides and one with 6
let finalRoll = rollDie(20) + rollDie(6);

// output
console.log(finalRoll);
```

Loops let us automatically do something MANY times: Roll an s-sided die any number of times

```js
// We can use this function to help us write another function
function rollDie(sides) {  
  return Math.ceil(Math.random() * sides);
}

function rollDieXTimes(sides, times) {
  // Keep a running tally
  let total = 0;

  // Call rollDie(sides) the specified number of times
  for (let i = 0; i < times; i++) {
    total += rollDie(sides);
  } 

  // return the total
  return total;
}

// Roll a 20-sided die 5 times
let result = rollDieXTimes(20, 5);
console.log(result);

// Roll a 6-sided die 10 times
console.log(rollDieXTimes(6, 10));
```

We can add in user input to make it more interactive ([Run it here](https://replit.com/@BenSpector/rollDieWithInput#index.js)!)

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

Or use an array to roll a series of die...

```js
function rollDie(sides) {  
  return Math.ceil(Math.random() * sides);
}

// We want to roll two 6-sided die, two 20-sided die, and a 10-sided die
const arrayOfDice = [6, 6, 20, 20, 10];
let total = 0;
arrayOfDice.forEach(die => total += rollDie(die));

console.log(total);
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
