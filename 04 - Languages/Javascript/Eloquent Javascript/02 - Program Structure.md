# Program Structure

![Picture of tentacles holding objects](https://eloquentjavascript.net/img/chapter_picture_2.jpg)

## Expressions and statements

_Expression_ : 
- They are a fragment of code that produces a value . 
- They can contain other expressions.
- They correspond to a sentence fragment.
- When between parentheses they are still an expression, 
	- same with a binary operator applied to two expressions.
	- same with a unary operator applied to one expression.

_Statement_: 
- corresponds to a full sentence. 
- A program is a list of statements.

Simplest kind of statement is an expression with a semicolon after it. 

This is a program:
```javascript
1; 
!false;
```
- produces the values `1` and `true` and throw them away. 
- This leaves no impression on the world at all. When you run this program, nothing observable happens.

An expression can be content to just produce a value, which can then be used by the enclosing code. 

A statement stands on its own.

Changing the internal state of the machine in a way that will affect the statements that come after it is called _side effects_. 

Semicolons in JavaScript sometimes can be omited at the end of a statement. 
The rules for when it can be safely omitted are somewhat complex and error-prone. 
In this book, every statement that needs a semicolon will always get one.

## Bindings

We have seen how to produce new values from old values, this does not change the old values, the new value has to be immediately used or it will dissipate again. 

To catch and hold values, there is _binding_, or _variable_:
    
```javascript
let caught = 5 * 5;
```
The previous statement creates a binding called `caught` and uses it to grab hold of the number that is produced by multiplying 5 by 5.

(_keyword_) `let` is defining a binding, the name of the binding,  giving it a value with the `=` operator and an expression.

The binding has been defined and the name can be used as an expression. 
The value of such an expression is the value the binding currently holds.

example:
```javascript
let ten = 10; 
console.log(ten * ten); 
// → 100
```

`=` operator can be used at any time on existing bindings to disconnect them from their current value and have them point to a new one.

```javascript
let mood = "light"; 
console.log(mood); 
// → light mood = "dark"; 
console.log(mood); // → dark
```

Bindings do not _contain_ values; they _grasp_ them.
Two bindings can refer to the same value. 

A program can access only the values that it still has a reference to.

#Example:
	To remember the number of dollars that Luigi still owes you, create a binding. And then when he pays back $35, you assign this binding a new value.

```javascript
let luigisDebt = 140;
luigisDebt = luigisDebt - 35;
console.log(luigisDebt); 
// → 105
```

Defining a binding without giving it a value does not work. 
Asking for the value of an empty binding, will get the value `undefined`.

A single `let` statement may define multiple bindings.  
Separate definitions by commas.

```javascript
let one = 1, two = 2;
console.log(one + two);
// → 3
```

The words `var` and `const` creates bindings, in a way similar to `let`.
    
```javascript
var name = "Ayda";
const greeting = "Hello "; 
console.log(greeting + name);
// → Hello Ayda
```

The first, `var` is the way bindings were declared in pre-2015 JavaScript.
More on the precise way it differs from `let` in the [next chapter]. For now, it mostly does the same thing.
We’ll rarely use it in this book because it has some confusing properties.

The word `const` stands for _constant_, which points at the same value for as long as it lives. Useful for values that you can easily refer to later.

## Binding names

Binding name rules:
	- any word or letter. 
	- Digits can be in binding names, but must not be the first character.
	- dollar signs (`$`) or underscores (`_`) but no other punctuation or special characters
	- `catch_22$` is a valid name 

 `let` is a _keyword_, and  may not be  a binding name. 
 There are also a number of words that are “reserved for use” in future versions of JavaScript, which also can’t be used as binding names. 
 
The full list of keywords and reserved words is rather long:
	
```Javascript
case catch class const continue debugger default delete do else enum export extends false finally for function if implements import interface in instanceof let new package private protected public return static super switch this throw true try typeof var void while with yield
```

Don’t worry about memorizing this list. When creating a binding produces an unexpected syntax error, see whether you’re trying to define a reserved word.

## The environment

_environment_: collection of bindings and their values that exist at a given time.

#Example
	in a browser, there are functions to interact with the currently loaded website and to read mouse and keyboard input.

## Functions

Values provided in the default environment have the type _function_. 
A function is a piece of program wrapped in a value.
Values can be _applied_ in order to run the wrapped program. 

#Example
	in a browser environment, the binding `prompt` holds a function that shows a little dialog box asking for user input. It is used like this:
```javascript    
prompt("Enter passcode");
```
![A prompt dialog](https://eloquentjavascript.net/img/prompt.png)
Executing a function is called _invoking_, _calling_, or _applying_ it.
Call a function by putting parentheses after an expression that produces a function value.
The values are given to the program inside the function. 
Values given to functions are called _arguments_. 

The `prompt` function
	- isn’t used much in modern web programming,
	- mostly because you have no control over the way the resulting dialog looks
	- can be helpful in toy programs and experiments.

## The console.log function

In the examples, `console.log` was used to output values. 

Most JavaScript systems in modern web browsers and Node.js provide a `console.log` function that writes out its arguments to _some_ text output device. 
 
Most browsers interface when you press F12 .

When running the examples (or your own code) on the pages of this book, `console.log` output will be shown after the example, instead of in the browser’s JavaScript console.

```javascript
let x = 30;
console.log("the value of x is", x);
// → the value of x is 30
```

`console.log` does have a period in its name because it isn’t a simple binding it retrieves the `log` property from the value held by the `console` binding. 

Details later in [Chapter 4].

## Return values

Showing a dialog box or writing text to the screen is a _side effect_.
Functions have side effects they produce, and may also produce values, in which case they don’t need to have a side effect. 

#Example 
	the function `Math.max` takes any amount of number arguments and gives back the greatest.

```javascript
console.log(Math.max(2, 4)); 
// → 4
```

Anything that produces a value, such as a value _return_,  is an expression.
function calls can be used within larger expressions. 

#Example 
	Here a call to `Math.min`, which is the opposite of `Math.max`, is used as part of a plus expression:
 
```javascript
console.log(Math.min(2, 4) + 100);
// → 102
```

The [next chapter]lexplains how to write your own functions.

## Control flow

When your program contains more than one statement, the statements are executed from top to bottom. 

#Example 	
	two statements. 
	first one asks the user for a number
	second is executed after the first, shows the square of that number.
 
```javascript
Let theNumber = Number(prompt("Pick a number"));
console.log("Your number is the square root of " + theNumber * theNumber);
```

The function `Number` converts a value to a number. 
The conversionis needed because  `prompt` is a string, a int or . There are similar functions called `String` and `Boolean` that convert to those value types.

Here is the rather trivial schematic representation of straight-line control flow:

![Trivial control flow](https://eloquentjavascript.net/img/controlflow-straight.svg)

## Conditional execution

![Conditional control flow](https://eloquentjavascript.net/img/controlflow-if.svg)

_Conditional execution_ is created with the `if` keyword in JavaScript.
#Example 
show the square of the input only if the input is actually a number.
```javascript   
let theNumber = Number(prompt("Pick a number"));
if (!Number.isNaN(theNumber)) { 
	console.log("Your number is the square root of " + theNumber * theNumber); }
```
enter “parrot”, no output is shown.

`if` keyword executes or skips a statement depending on the value of a Boolean expression. 

The deciding expression is written after the keyword, between parentheses, followed by the statement to execute.

`Number.isNaN` function returns `true` if given `NaN`. 
`Number` function returns `NaN` giving it a string not a valid number.
The condition translates to “unless `theNumber` is not-a-number, do this”.

Wrap statement after  `if` in braces (`{` and `}`)
Braces can be used to group statements into a single statement, a _block_.
also could omit them in this case, since its a single statement
use them in every wrapped statement like this.
Mostly follow that convention , except for some one-liners.
```javascript
if (1 + 1 == 2) console.log("It's true"); 
// → It's true
```
You can use the `else` keyword, together with `if`, to create two separate, alternative execution paths.
```javascript
let theNumber = Number(prompt("Pick a number"));
if (!Number.isNaN(theNumber)) {
	console.log("Your number is the square root of " + theNumber * theNumber); 
} else {
	console.log("Hey. Why didn't you give me a number?"); 
}
```
If you have more than two paths to choose from, “chain” multiple `if`/`else` pairs together. 
#Example :
```javascript 
let num = Number(prompt("Pick a number"));
if (num < 10) {
	console.log("Small"); 
} else if (num < 100) {
	console.log("Medium"); 
} else {
	console.log("Large"); 
}
```
The program first checks whether `num` less than 10.
If it is, it chooses that branch, shows `"Small"`, and done. 
If not, it takes the `else` branch, which itself contains a second `if`. 
If the second condition (`< 100`) holds, that means the number is at least 10 but below 100, and `"Medium"` is shown. 
If not, the second and last `else` branch is chosen.

The schema for this program looks like:

![Nested if control flow](https://eloquentjavascript.net/img/controlflow-nested-if.svg)

## while and do loops

Consider a program that outputs all even numbers from 0 to 12. 

One way to write this is as follows:
```javascript
console.log(0);
console.log(2);
console.log(4);
console.log(6);
console.log(8);
console.log(10);
console.log(12);
```
make something _less_ work, not more. 
If we needed all even numbers less than 1,000, this approach would be unworkable. 
Run a piece of code multiple times. 
This form of control flow is called a _loop_.

![Loop control flow](https://eloquentjavascript.net/img/controlflow-loop.svg)

Looping control flow goes back to a point in the program and repeat it with our current program state. 

Combine this with a binding that counts:    
```javascript
let number = 0; 
while (number <= 12) {
	console.log(number);
number = number + 2; 
} 
// → 0 
// → 2 
// … etcetera
```

`while` : 
- creates a loop. 
- is followed by an expression in parentheses and then a statement, like `if`. 
- keeps entering that statement if the expression produces a value that gives `true`.

`number` binding demonstrates the way a binding can track the progress of a program.
 `number` gets a value that is 2 more than its previous value. 
 At the beginning of every repetition, it is compared with 12 to decide whether finished.

write a program that calculates and shows the value of 2^10 (2 to the 10th power). 

Use two bindings: 
- one to keep track of our result 
- one to count how often we have multiplied this result by 2. 

Loop tests whether second binding reached 10, if not, updates both bindings.
```javascript
let result = 1;
let counter = 0;
while (counter < 10) {
	result = result * 2;
	counter = counter + 1; 
} 
console.log(result); 
// → 1024
```

The counter could start at `1` and checked for `<= 10`
count from 0.

`do` loop always executes its body at least once, and it starts testing whether it should stop only after that first execution.

To reflect this, the test appears after the body of the loop:
```javascript
let yourName; 
do {
	yourName = prompt("Who are you?");
} while (!yourName);
console.log(yourName);
```

This program will force you to enter a name. 
It will ask again and again, until it gets something that is not an empty string. 
`!` operator will convert a value to Boolean type before negating it, and all strings except `""` convert to `true`. 
The loop continues going until provided a non-empty name.

## Indenting Code

In the examples,added paces in front of statements are part of some larger statement. 
These spaces and line breaks are not required
A program could be a single long line.

indentation inside blocks is for structured code.
In code where new blocks are opened inside other blocks, it can be hard to see a block ends and another begins.
proper indentation has visual shape of the program corresponding to the blocks inside it. 
These notes will use two spaces for every open block
	tastes differ—some people use four spaces, and some people use tab characters. 
	
Each new block adds the same amount of space.

```javascript
if (false != true) {
	console.log("That makes sense.");
	if (1 < 2) {
		console.log("No surprise there."); 
	}
}
```

Most code editor programs (including this book) will help by automatically indenting new lines the proper amount.

## for loops

A “counter” binding is created to track the progress of the loop. 
Then a `while` loop, usually with a test expression that checks whether the counter has reached its end value. 
At the end of the loop body, the counter is updated to track progress.

`for` loop #Example :
```javascript
for (let number = 0; number <= 12; number = number + 2) {
	console.log(number); 
} 
// → 0 
// → 2 
// … etcetera
```

This program is exactly equivalent to the [earlier] even-number-printing example, except all the statements that are related to the “state” of the loop are grouped together after `for`.

The parentheses after a `for` keyword must contain two semicolons. 
before the first semicolon _initializes_ the loop, by defining a binding.
Second part is the expression that _checks_ whether the loop must continue. 
Final part _updates_ the state of the loop after every iteration. 
most cases, this is shorter and clearer than a `while` construct.

This is the code that computes 210 using `for` instead of `while`:

```javascript
let result = 1;
for (let counter = 0; counter < 10; counter = counter + 1) {
	result = result * 2; 
}
console.log(result); 
// → 1024
```

## Breaking Out of a Loop

Having the looping condition produce `false` is not the only way a loop can finish. 
a special statement called `break` that has the effect of immediately jumping out of the enclosing loop.

This program illustrates the `break` statement. 
It finds the first number that is both greater than or equal to 20 and divisible by 7.

```javascript
for (let current = 20; ; current = current + 1) {
	if (current % 7 == 0) {
		console.log(current);
		break;
	} 
} 
// → 21
```

Using the remainder (`%`) operator is an easy way to test whether a number is divisible by another number. If it is, the remainder of their division is zero.

The `for` construct in the example does not have a part that checks for the end of the loop. 
The loop will never stop unless the `break` statement inside is executed.

Remove that `break` statement or accidentally write an end condition that always produces `true`, your program would get stuck in an _infinite loop_. 
A program stuck in an infinite loop will never finish running, which is usually a bad thing.

If you create an infinite loop in one of the examples on these pages, you’ll usually be asked whether you want to stop the script after a few seconds. 
If that fails, you will have to close the tab that you’re working in, or on some browsers close your whole browser, to recover.

The `continue` keyword is similar to `break`, in that it influences the progress of a loop. When `continue` is encountered in a loop body, control jumps out of the body and continues with the loop’s next iteration.

## Updating bindings succinctly

Especially when looping, a program often needs to “update” a binding to hold a value based on that binding’s previous value.

```javascript
counter = counter + 1;
```

JavaScript provides a shortcut for this.
```javascript
counter += 1;
```

Similar shortcuts work for many other operators, such as `result *= 2` to double `result` or `counter -= 1` to count downward.

This allows us to shorten our counting example a little more.
```javascript
for (let number = 0; number <= 12; number += 2) {
	console.log(number); 
}
```
For `counter += 1` and `counter -= 1`, there are even shorter equivalents: `counter++` and `counter--`.

## Dispatching on a value with switch

It is not uncommon for code to look like this:
  
 ```javascript
 if (x == "value1") action1();
 else if (x == "value2") action2();
 else if (x == "value3") action3();
 else defaultAction();
```

There is a construct called `switch` that is intended to express such a “dispatch” in a more direct way. 
The syntax JavaScript uses for this (which it inherited from the C/Java line of programming languages) is somewhat awkward—a chain of `if` statements may look better. 

#Example :
```javascript
switch (prompt("What is the weather like?")) {
	case "rainy": 
		console.log("Remember to bring an umbrella.");
		break; 
	case "sunny": 
		console.log("Dress lightly."); 
	case "cloudy": 
		console.log("Go outside."); 
		break; 
	default: 
		console.log("Unknown weather type!");
		break; 
}
```

You may put any number of `case` labels inside the block opened by `switch`. The program will start executing at the label that corresponds to the value that `switch` was given, or at `default` if no matching value is found. It will continue executing, even across other labels, until it reaches a `break` statement. 

In some cases, such as the `"sunny"` case in the example, this can be used to share some code between cases (it recommends going outside for both sunny and cloudy weather). But be careful—it is easy to forget such a `break`, which will cause the program to execute code you do not want executed.

## Capitalization

Binding names may not contain spaces, use multiple words to clearly describe what the binding represents. 
These are pretty much your choices for writing a binding name with several words in it:

```javascript
fuzzylittleturtle 
fuzzy_little_turtle 
FuzzyLittleTurtle 
fuzzyLittleTurtle
```

The first style can be hard to read.
I rather like the look of the underscores, though that style is a little painful to type. 
Standard JavaScript functions, and most JavaScript programmers, follow the bottom style—they capitalize every word except the first, _camelCase_. follow this convention.

In a few cases, such as the `Number` function, the first letter of a binding is also capitalized. This was done to mark this function as a constructor. What a constructor is will become clear in [Chapter 6](https://eloquentjavascript.net/06_object.html#constructors). Dont be bothered by this apparent lack of consistency.

## Comments

 _Comments_ are for:
- Information you want a program to convey to human readers
- Conveying code in such a way that people might understand it. 

Include some related thoughts as part of your program. 

A comment is a piece of text that is part of a program but is completely ignored by the computer. 
Two ways of writing comments:
- write a single-line comment, you can use two slash characters (`//`) and then the comment text after it.

```javascript
let accountBalance = calculateBalance(account); // It's a green hollow where a river sings accountBalance.adjust(); // Madly catching white tatters in the grass. let report = new Report(); // Where the sun on the proud mountain rings: addToReport(accountBalance, report); // It's a little valley, foaming like light in a glass.
```

A `//` comment goes only to the end of the line.

-Section of text between `/*` and `*/` will be ignored in its entirety, regardless of whether it contains line breaks. This is useful for adding blocks of information about a file or a chunk of program.

```javascript
/*  
	I first found this number scrawled on the back of an old  notebook. Since then, it has often dropped by, showing up in  phone numbers and the serial numbers of products that I've  bought. It obviously likes me, so I've decided to keep it. 
*/ 
const myNumber = 11213;
```

## Summary

You now know that a program is built out of statements, which themselves sometimes contain more statements. 
Statements tend to contain expressions, which themselves can be built out of smaller expressions.

Putting statements after one another gives you a program that is executed from top to bottom. You can introduce disturbances in the flow of control by using conditional (`if`, `else`, and `switch`) and looping (`while`, `do`, and `for`) statements.

Bindings can be used to file pieces of data under a name, and they are useful for tracking state in your program. 
The environment is the set of bindings that are defined. 
JavaScript systems always put a number of useful standard bindings into your environment.

Functions are special values that encapsulate a piece of program. 
You can invoke them by writing `functionName(argument1, argument2)`. 
Such a function call is an expression and may produce a value.

## Exercises

If you are unsure how to test your solutions to the exercises, refer to the [Introduction](https://eloquentjavascript.net/00_intro.html).

Each exercise starts with a problem description. Read this description and try to solve the exercise. If you run into problems, consider reading the hints after the exercise. Full solutions to the exercises are not included in this book, but you can find them online at [_https://eloquentjavascript.net/code_](https://eloquentjavascript.net/code#2). If you want to learn something from the exercises, I recommend looking at the solutions only after you’ve solved the exercise, or at least after you’ve attacked it long and hard enough to have a slight headache.

### Looping a triangle

Write a loop that makes seven calls to `console.log` to output the following triangle:
```javascript
# 
##
###
####
##### 
######
#######
```
It may be useful to know that you can find the length of a string by writing `.length` after it.
```javascript
 let abc = "abc";
 console.log(abc.length); 
 // → 3
```
Most exercises contain a piece of code that you can modify to solve the exercise. Remember that you can click code blocks to edit them.
```javascript
// Your code here.
```
### FizzBuzz

Write a program that uses `console.log` to print all the numbers from 1 to 100, with two exceptions. For numbers divisible by 3, print `"Fizz"` instead of the number, and for numbers divisible by 5 (and not 3), print `"Buzz"` instead.

When you have that working, modify your program to print `"FizzBuzz"` for numbers that are divisible by both 3 and 5 (and still print `"Fizz"` or `"Buzz"` for numbers divisible by only one of those).

(This is actually an interview question that has been claimed to weed out a significant percentage of programmer candidates. So if you solved it, your labor market value just went up.)
```javascript    
// Your code here.
```
### Chessboard

Write a program that creates a string that represents an 8×8 grid, using newline characters to separate lines. At each position of the grid there is either a space or a "#" character. The characters should form a chessboard.

Passing this string to `console.log` should show something like this:
    
```javascript
	# # # #
# # # # 
	# # # # 
# # # # 
	# # # #
# # # # 
	# # # # 
# # # #
``` 
When you have a program that generates this pattern, define a binding `size = 8` and change the program so that it works for any `size`, outputting a grid of the given width and height.

    // Your code here.

> hints