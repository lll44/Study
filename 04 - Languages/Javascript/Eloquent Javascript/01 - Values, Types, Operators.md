# 1 - Values, Types, and Operators


#TODO: On all of these notes the markdown formatted weird due to some inline paragraph linking in the website that allows you to jump to paragraphs and link them. You will have to delete these as you read. I recommend just clicking the last brack \) and then cntrl-backspace. Don't delete photos or important links. 

#TODO: Also there are practice questions on the website that display a hint  javascript element that pops up but didn't copy when I pasted it here., So you will need to take a look at the website just to assure everything has copied over. 

![Picture of a sea of bits](https://eloquentjavascript.net/img/chapter_picture_1.jpg)

_Bits_ are any kind of two-valued things, zeros and ones.

example, express the number 13 in bits.
    
    0	0	0	0	1	1	0	1
	128	64	32	16	8	4	2	1

So that’s the binary number 00001101. Its non-zero digits  8, 4, and 1, add up to 13.

## Values

_values_ have a type that determines its role.
To create a value, invoke its name. 
Every value has to be stored somewhere.

## Numbers

_number_ type are numeric values. In JavaScript, they are written as follows:
    
`13`

JavaScript uses 64 bit to store a single number value.

_N_ decimal digits, you can represent 10N numbers. Similarly, given 64 binary digits, you can represent 264 different numbers, which is about 18,000,000,000,000,000,000

 _overflow_ to end up with a number that did not fit into the given number of bits.
The actual maximum whole number that can be stored is more in the range of 9 quadrillion (15 zeros)—which is still pleasantly huge.

Fractional numbers are written by using a dot.
    
`9.81`

Also use scientific notation by adding an _e_ (for _exponent_), followed by the exponent of the number.
    
`2.998e8`

2.998 × 10^8 = 299,800,000.

Treat fractional digital numbers as approximations, not as precise values.

whole numbers (also called _integers_)

### Arithmetic

Arithmetic operations take two number values and produce a new number from them. 

Ex:    
`100 + 4 * 11`

The `+` and `*` symbols are called _operators_. Putting an operator between two values will apply it to those values and produce a new value.

 you can change this by wrapping the addition in parentheses.
    
`(100 + 4) * 11`

Subtraction is `-` operator, and division can be done with the `/` operator.

_precedence_ of the operators is the same as mathematics. `/` , `*`, `+`, and `-`

When in doubt, just add parentheses.

`%`  is the _remainder_ operation. `X % Y` is the remainder of dividing `X` by `Y`. 

Ex:
`314 % 100` produces `14`, and `144 % 12` gives `0`. The remainder operator’s precedence is the same as of multiplication and division. You’ll also often see this operator referred to as _modulo_.

### Special numbers

There are three special values in JavaScript that are considered numbers but don’t behave like normal numbers.

`Infinity` and `-Infinity`, represent the positive and negative infinities. 
`Infinity - 1` is still `Infinity`

`NaN` stands for “not a number”, even though it is a value of the number type. You’ll get this result when you, for example, try to calculate `0 / 0` (zero divided by zero), `Infinity - Infinity`, or any number of other numeric operations that don’t yield a meaningful result.

## Strings

The next basic data type is the _string_. Strings are used to represent text. They are written by enclosing their content in quotes.

```
`Down on the sea`
"Lie on the ocean" 
'Float on the ocean'
```

You can use single quotes, double quotes, or backticks to mark strings.

_Newlines_ (the characters you get when you press enter) can be included without escaping only when the string is quoted with backticks 
```
`
```

_escaping_ the character is whenever a backslash ( `\` ) is found inside quoted text, it indicates that the character after it has a special meaning. A quote that is preceded by a backslash will not end the string but be part of it. 

`n` character is a newline.
`t` after a backslash means is a tab character. 

Ex:

`"This is the first line\nAnd this is the second"`

The actual text contained is this:
```    
This is the first line 
And this is the second
```

If two backslashes follow each other, they will collapse together, and only one will be left in the resulting string value. 

`A newline character is written like "\n".`    
will be expressed as:
`"A newline character is written like \"\\n\"."`

Strings are based on the _Unicode_ standard. This standard assigns a number to virtually every character you would ever need, including characters from Greek, Arabic, Japanese, Armenian, and so on. a string can be described by a sequence of characters.

JavaScript’s representation uses 16 bits per string element, which can describe up to 216 different characters.

Unicode defines characters, such as many emoji, take up two “character positions” in JavaScript strings. We’ll come back to this in [Chapter 5]

Strings cannot be divided, multiplied, or subtracted, but the `+` operator _concatenates_—two strings together. 

The following line will produce the string `"concatenate"`:    
`"con" + "cat" + "e" + "nate"`

String values have a number of associated functions (_methods_) that can be used to perform other operations on them. More about these in [Chapter 4]

Strings written with single or double quotes behave very much the same—the only difference is in which type of quote you need to escape inside of them. Backtick-quoted strings, usually called _template literals_, can do a few more tricks. Apart from being able to span lines, they can also embed other values.
```   
`half of 100 is ${100 / 2}`
```
When you write something inside `${}` in a template literal, its result will be computed, converted to a string, and included at that position. The example produces 
```
_half of 100 is 50_
```

## Unary operators

Some operators are written as words. One example is the `typeof` operator, which produces a string value naming the type of the value you give it.
 ```   
console.log(typeof 4.5) 
// → number
console.log(typeof "x") 
// → string
```
We will use `console.log` in example code to indicate that we want to see the result of evaluating something. More in [chapter 2]

The other operators shown all operated on two values, but `typeof` takes only one. 

Operators that uses: 
- two values are  _binary_ operators, while those that take one are called 
- one value operators are  _unary_ operators. 
- The minus operator can be used both as a binary operator and as a unary operator.
```    
console.log(- (10 - 2))
// → -8
```
## Boolean values

JavaScript has a _Boolean_ type true and false.

### Comparison

Here is one way to produce Boolean values:
```    
console.log(3 > 2) 
// → true 
console.log(3 < 2) 
// → false
```
The `>` and `<` signs are “is greater than” and “is less than”, respectively. They are binary operators. 

Strings can be compared in the same way.
```
console.log("Aardvark" < "Zoroaster") 
// → true
```
The way strings are ordered is roughly alphabetic: 
- uppercase letters are always “less” than lowercase ones: `"Z" < "a"`
- nonalphabetic characters (!, -, and so on) are also included in the ordering. 
- When comparing strings, JavaScript goes over the characters from left to right, comparing the Unicode codes one by one.

`>=` (greater than or equal to), `<=` (less than or equal to), `==` (equal to), and `!=` (not equal to), Ex:
```    
console.log("Itchy" != "Scratchy") 
// → true 
console.log("Apple" == "Orange") 
// → false
```

There is only one value in JavaScript that is not equal to itself, and that is `NaN` (“not a number”).
```    
console.log(NaN == NaN) 
// → false
```
`NaN` is supposed to denote the result of a nonsensical computation, and as such, it isn’t equal to the result of any _other_ nonsensical computations.

### Logical operators

Some operations can be applied to Boolean values themselves. 

JavaScript supports three logical operators: _and_, _or_, and _not_

`&&` operator represents logical _and_. It is a binary operator, and its result is true only if both the values given to it are true.
```
console.log(true && false) 
// → false 
console.log(true && true) 
// → true
```

`||` operator denotes logical _or_. It produces true if either of the values given to it is true.
```    
console.log(false || true) 
// → true 
console.log(false || false) 
// → false
```

_Not_ is written as an exclamation mark (`!`). A unary operator that flips the value given to it—`!true` produces `false`, and `!false` gives `true`.

`||` has the lowest precedence, then comes `&&`, then the comparison operators (`>`, `==`, and so on), and then Arithmetic. 

Ex:
```
1 + 1 == 2 && 10 * 10 > 50
```

_ternary_, operating on three values. Is written with a question mark and a colon, like this:
```    
console.log(true ? 1 : 2); 
// → 1 
console.log(false ? 1 : 2); 
// → 2
```

_conditional_ operator (or _ternary_ operator). The value on the left of the question mark “picks” which of the other two values will come out. When it is true, it chooses the middle value, and when it is false, it chooses the value on the right.

## Empty values

There are two special values, written `null` and `undefined`, that are used to denote the absence of a _meaningful_ value. They are themselves values, but they carry no information.

Many operations in the language that don’t produce a meaningful value yield `undefined` simply because they have to yield _some_ value.

The difference between `undefined` and `null` is an accident of JavaScript’s design treat them as mostly interchangeable.

## Automatic type conversion

```    
console.log(8 * null) 
// → 0 
console.log("5" - 1) 
// → 4 
console.log("5" + 1) 
// → 51 
console.log("five" * 2) 
// → NaN 
console.log(false == 0) 
// → true
```

When an operator is applied to the “wrong” type of value, JavaScript will convert that value to the type needed, called _type coercion_. 

`null` in the first expression becomes `0`

`"5"` in the second expression becomes `5` (from string to number)

In the third expression, `+` tries string concatenation before numeric addition, so the `1` is converted to `"1"` (from number to string).

When ( `"five"` or `undefined`) is converted to a number, you get the value `NaN`. Further arithmetic operations on `NaN` keep producing `NaN`, so if you find yourself getting one of those in an unexpected place, look for accidental type conversions.

Comparing values of the same type using `==`, should be true when both values are the same, except  `NaN`. When the types differ in most cases, it just tries to convert one of the values to the other value’s type. 

When `null` or `undefined` occurs on either side of the operator, it produces true only if both sides are one of `null` or `undefined`.
    
```
console.log(null == undefined); 
// → true 
console.log(null == 0); 
// → false
```
That behavior is often useful. When you want to test whether a value has a real value instead of `null` or `undefined`, you can compare it to `null` with the `==` (or `!=`) operator.

Expressions like `0 == false` and `"" == false` are also true because of automatic type conversion. 
When you do _not_ want any type conversions to happen, there are two additional operators: `===` and `!==`. 
The first tests whether a value is _precisely_ equal to the other, and the second tests whether it is not precisely equal. 

Ex: `"" === false` is false as expected.

Use the three-character comparison operators defensively to prevent unexpected type conversions from tripping you up.

### Short-circuiting of logical operators

The logical operators `&&` and `||` handle values of different types in a peculiar way. They convert the value on their left side to Boolean type in order to decide what to do they will return either the _original_ left-hand value or the right-hand value.

The `||` operator will return the value to its left when that can be converted to true and will return the value on its right otherwise. 

This has the expected effect when the values are Boolean and does something analogous for values of other types.
```    
console.log(null || "user") 
// → user 
console.log("Agnes" || "user") 
// → Agnes
```
We can use this functionality as a way to fall back on a default value. If you have a value that might be empty, you can put `||` after it with a replacement value. If the initial value can be converted to false, you’ll get the replacement instead. 

`0`, `NaN`, and the empty string (`""`) count as `false`
all the other values count as `true`. 
Ex: `0 || -1` produces `-1`
`"" || "!?"` yields `"!?"`.

`&&` operator works the other way around. When the value to its left is something that converts to false, it returns that value, and otherwise it returns the value on its right.

The part to their right is evaluated only when necessary. In the case of `true || X`, no matter what `X` is—even if it’s a piece of program that does something _terrible_—the result will be true, and `X` is never evaluated.

`false && X`, is false and will ignore `X`. Called _short-circuit evaluation_.

The conditional operator works in a similar way. Of the second and third values, only the one that is selected is evaluated.