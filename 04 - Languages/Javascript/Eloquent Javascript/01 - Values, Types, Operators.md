# 1 - Values, Types, and Operators


#TODO: On all of these notes the markdown formatted weird due to some inline paragraph linking in the website that allows you to jump to paragraphs and link them. You will have to delete these as you read. I recommend just clicking the last brack \) and then cntrl-backspace. Don't delete photos or important links. 

#TODO: Also there are practice questions on the website that display a hint  javascript element that pops up but didn't copy when I pasted it here., So you will need to take a look at the website just to assure everything has copied over. 

> [](https://eloquentjavascript.net/01_values.html#p_93S4YBaGUf)Below the surface of the machine, the program moves. Without effort, it expands and contracts. In great harmony, electrons scatter and regroup. The forms on the monitor are but ripples on the water. The essence stays invisibly below.
> 
> Master Yuan-Ma, The Book of Programming

![Picture of a sea of bits](https://eloquentjavascript.net/img/chapter_picture_1.jpg)

[](https://eloquentjavascript.net/01_values.html#p_sgNSYKwqbo)Inside the computer’s world, there is only data. You can read data, modify data, create new data—but that which isn’t data cannot be mentioned. All this data is stored as long sequences of bits and is thus fundamentally alike.

_Bits_ are any kind of two-valued things, usually described as zeros and ones. Inside the computer, they take forms such as a high or low electrical charge, a strong or weak signal, or a shiny or dull spot on the surface of a CD. Any piece of discrete information can be reduced to a sequence of zeros and ones and thus represented in bits.

[](https://eloquentjavascript.net/01_values.html#p_PDoqiRoGSa)For example, we can express the number 13 in bits. It works the same way as a decimal number, but instead of 10 different digits, you have only 2, and the weight of each increases by a factor of 2 from right to left. Here are the bits that make up the number 13, with the weights of the digits shown below them:
    
    [](https://eloquentjavascript.net/01_values.html#c_+fMMNc3yUt) 0 0 0 0 1 1 0 1 128 64 32 16 8 4 2 1

[](https://eloquentjavascript.net/01_values.html#p_0u8qQ2tfMI)So that’s the binary number 00001101. Its non-zero digits stand for 8, 4, and 1, and add up to 13.

## [](https://eloquentjavascript.net/01_values.html#h_sVZPaxUSy/)Values

[](https://eloquentjavascript.net/01_values.html#p_ySnc2wG5kf)Imagine a sea of bits—an ocean of them. A typical modern computer has more than 30 billion bits in its volatile data storage (working memory). Nonvolatile storage (the hard disk or equivalent) tends to have yet a few orders of magnitude more.

[](https://eloquentjavascript.net/01_values.html#p_JRdY+sw4TV)To be able to work with such quantities of bits without getting lost, we must separate them into chunks that represent pieces of information. In a JavaScript environment, those chunks are called _values_. Though all values are made of bits, they play different roles. Every value has a type that determines its role. Some values are numbers, some values are pieces of text, some values are functions, and so on.

[](https://eloquentjavascript.net/01_values.html#p_+ayfFmFdze)To create a value, you must merely invoke its name. This is convenient. You don’t have to gather building material for your values or pay for them. You just call for one, and _whoosh_, you have it. They are not really created from thin air, of course. Every value has to be stored somewhere, and if you want to use a gigantic amount of them at the same time, you might run out of memory. Fortunately, this is a problem only if you need them all simultaneously. As soon as you no longer use a value, it will dissipate, leaving behind its bits to be recycled as building material for the next generation of values.

[](https://eloquentjavascript.net/01_values.html#p_lWUuVOz1Pd)This chapter introduces the atomic elements of JavaScript programs, that is, the simple value types and the operators that can act on such values.

## [](https://eloquentjavascript.net/01_values.html#h_flOCH3CuFg)Numbers

[](https://eloquentjavascript.net/01_values.html#p_lB/BspzEbz)Values of the _number_ type are, unsurprisingly, numeric values. In a JavaScript program, they are written as follows:
    
    [](https://eloquentjavascript.net/01_values.html#c_/u5ErTZbax)13

[](https://eloquentjavascript.net/01_values.html#p_nFVjE3kHJh)Use that in a program, and it will cause the bit pattern for the number 13 to come into existence inside the computer’s memory.

[](https://eloquentjavascript.net/01_values.html#p_TBpgYLjzVr)JavaScript uses a fixed number of bits, 64 of them, to store a single number value. There are only so many patterns you can make with 64 bits, which means that the number of different numbers that can be represented is limited. With _N_ decimal digits, you can represent 10N numbers. Similarly, given 64 binary digits, you can represent 264 different numbers, which is about 18 quintillion (an 18 with 18 zeros after it). That’s a lot.

[](https://eloquentjavascript.net/01_values.html#p_WcfWpTcQB6)Computer memory used to be much smaller, and people tended to use groups of 8 or 16 bits to represent their numbers. It was easy to accidentally _overflow_ such small numbers—to end up with a number that did not fit into the given number of bits. Today, even computers that fit in your pocket have plenty of memory, so you are free to use 64-bit chunks, and you need to worry about overflow only when dealing with truly astronomical numbers.

[](https://eloquentjavascript.net/01_values.html#p_qgS+bpqvEk)Not all whole numbers less than 18 quintillion fit in a JavaScript number, though. Those bits also store negative numbers, so one bit indicates the sign of the number. A bigger issue is that nonwhole numbers must also be represented. To do this, some of the bits are used to store the position of the decimal point. The actual maximum whole number that can be stored is more in the range of 9 quadrillion (15 zeros)—which is still pleasantly huge.

[](https://eloquentjavascript.net/01_values.html#p_+wzyK91zcb)Fractional numbers are written by using a dot.
    
    [](https://eloquentjavascript.net/01_values.html#c_tM8nqv41Gp)9.81

[](https://eloquentjavascript.net/01_values.html#p_oofHxZNW9M)For very big or very small numbers, you may also use scientific notation by adding an _e_ (for _exponent_), followed by the exponent of the number.
    
    [](https://eloquentjavascript.net/01_values.html#c_6ew5w+VhSM)2.998e8

[](https://eloquentjavascript.net/01_values.html#p_YbACmHw8Kd)That is 2.998 × 108 = 299,800,000.

[](https://eloquentjavascript.net/01_values.html#p_8KgYC0F1fX)Calculations with whole numbers (also called _integers_) smaller than the aforementioned 9 quadrillion are guaranteed to always be precise. Unfortunately, calculations with fractional numbers are generally not. Just as π (pi) cannot be precisely expressed by a finite number of decimal digits, many numbers lose some precision when only 64 bits are available to store them. This is a shame, but it causes practical problems only in specific situations. The important thing is to be aware of it and treat fractional digital numbers as approximations, not as precise values.

### [](https://eloquentjavascript.net/01_values.html#i_RfBT3HMnYs)Arithmetic

[](https://eloquentjavascript.net/01_values.html#p_PO8MaZIpG1)The main thing to do with numbers is arithmetic. Arithmetic operations such as addition or multiplication take two number values and produce a new number from them. Here is what they look like in JavaScript:
    
    [](https://eloquentjavascript.net/01_values.html#c_bSU4Vtv/mt)100 + 4 * 11

[](https://eloquentjavascript.net/01_values.html#p_Gbkt+ofKYQ)The `+` and `*` symbols are called _operators_. The first stands for addition, and the second stands for multiplication. Putting an operator between two values will apply it to those values and produce a new value.

[](https://eloquentjavascript.net/01_values.html#p_UaADJxNSjA)But does the example mean “add 4 and 100, and multiply the result by 11,” or is the multiplication done before the adding? As you might have guessed, the multiplication happens first. But as in mathematics, you can change this by wrapping the addition in parentheses.
    
    [](https://eloquentjavascript.net/01_values.html#c_ij6V90ZZBQ)(100 + 4) * 11

[](https://eloquentjavascript.net/01_values.html#p_OSF05nVTV6)For subtraction, there is the `-` operator, and division can be done with the `/` operator.

[](https://eloquentjavascript.net/01_values.html#p_sJXEzZnGO0)When operators appear together without parentheses, the order in which they are applied is determined by the _precedence_ of the operators. The example shows that multiplication comes before addition. The `/` operator has the same precedence as `*`. Likewise for `+` and `-`. When multiple operators with the same precedence appear next to each other, as in `1 - 2 + 1`, they are applied left to right: `(1 - 2) + 1`.

[](https://eloquentjavascript.net/01_values.html#p_epF5qxonWY)These rules of precedence are not something you should worry about. When in doubt, just add parentheses.

[](https://eloquentjavascript.net/01_values.html#p_3aZxtaabKD)There is one more arithmetic operator, which you might not immediately recognize. The `%` symbol is used to represent the _remainder_ operation. `X % Y` is the remainder of dividing `X` by `Y`. For example, `314 % 100` produces `14`, and `144 % 12` gives `0`. The remainder operator’s precedence is the same as that of multiplication and division. You’ll also often see this operator referred to as _modulo_.

### [](https://eloquentjavascript.net/01_values.html#i_R4eFf8w7Yz)Special numbers

[](https://eloquentjavascript.net/01_values.html#p_JBBwZano0e)There are three special values in JavaScript that are considered numbers but don’t behave like normal numbers.

[](https://eloquentjavascript.net/01_values.html#p_Vk/nIi3mWM)The first two are `Infinity` and `-Infinity`, which represent the positive and negative infinities. `Infinity - 1` is still `Infinity`, and so on. Don’t put too much trust in infinity-based computation, though. It isn’t mathematically sound, and it will quickly lead to the next special number: `NaN`.

[](https://eloquentjavascript.net/01_values.html#p_kS+V22+tDp)`NaN` stands for “not a number”, even though it _is_ a value of the number type. You’ll get this result when you, for example, try to calculate `0 / 0` (zero divided by zero), `Infinity - Infinity`, or any number of other numeric operations that don’t yield a meaningful result.

## [](https://eloquentjavascript.net/01_values.html#h_OBbEvqxHHH)Strings

[](https://eloquentjavascript.net/01_values.html#p_JUYnmsnZEA)The next basic data type is the _string_. Strings are used to represent text. They are written by enclosing their content in quotes.
    
    [](https://eloquentjavascript.net/01_values.html#c_JcfC82q1V/)`Down on the sea` "Lie on the ocean" 'Float on the ocean'

[](https://eloquentjavascript.net/01_values.html#p_J5Re/uQFh3)You can use single quotes, double quotes, or backticks to mark strings, as long as the quotes at the start and the end of the string match.

[](https://eloquentjavascript.net/01_values.html#p_zqSxAQbLww)Almost anything can be put between quotes, and JavaScript will make a string value out of it. But a few characters are more difficult. You can imagine how putting quotes between quotes might be hard. _Newlines_ (the characters you get when you press enter) can be included without escaping only when the string is quoted with backticks (```).

[](https://eloquentjavascript.net/01_values.html#p_Fhyuks46v3)To make it possible to include such characters in a string, the following notation is used: whenever a backslash (`\`) is found inside quoted text, it indicates that the character after it has a special meaning. This is called _escaping_ the character. A quote that is preceded by a backslash will not end the string but be part of it. When an `n` character occurs after a backslash, it is interpreted as a newline. Similarly, a `t` after a backslash means a tab character. Take the following string:
    
    [](https://eloquentjavascript.net/01_values.html#c_L1XyfWLjvh)"This is the first line
    And this is the second"

[](https://eloquentjavascript.net/01_values.html#p_rtFNX67M4o)The actual text contained is this:
    
    [](https://eloquentjavascript.net/01_values.html#c_dbS7S3Fqly)This is the first line And this is the second

[](https://eloquentjavascript.net/01_values.html#p_RcQxEVsohZ)There are, of course, situations where you want a backslash in a string to be just a backslash, not a special code. If two backslashes follow each other, they will collapse together, and only one will be left in the resulting string value. This is how the string “_A newline character is written like `"` `"`._” can be expressed:
    
    [](https://eloquentjavascript.net/01_values.html#c_AuMrnbfo/X)"A newline character is written like \"\n\"."

[](https://eloquentjavascript.net/01_values.html#p_FkxXOQHt6a)Strings, too, have to be modeled as a series of bits to be able to exist inside the computer. The way JavaScript does this is based on the _Unicode_ standard. This standard assigns a number to virtually every character you would ever need, including characters from Greek, Arabic, Japanese, Armenian, and so on. If we have a number for every character, a string can be described by a sequence of numbers.

[](https://eloquentjavascript.net/01_values.html#p_FZTkxxFJHy)And that’s what JavaScript does. But there’s a complication: JavaScript’s representation uses 16 bits per string element, which can describe up to 216 different characters. But Unicode defines more characters than that—about twice as many, at this point. So some characters, such as many emoji, take up two “character positions” in JavaScript strings. We’ll come back to this in [Chapter 5](https://eloquentjavascript.net/05_higher_order.html#code_units).

[](https://eloquentjavascript.net/01_values.html#p_+y5+JTiKgR)Strings cannot be divided, multiplied, or subtracted, but the `+` operator _can_ be used on them. It does not add, but it _concatenates_—it glues two strings together. The following line will produce the string `"concatenate"`:
    
    [](https://eloquentjavascript.net/01_values.html#c_eCO7oekmP9)"con" + "cat" + "e" + "nate"

[](https://eloquentjavascript.net/01_values.html#p_f802i8aCZi)String values have a number of associated functions (_methods_) that can be used to perform other operations on them. I’ll say more about these in [Chapter 4](https://eloquentjavascript.net/04_data.html#methods).

[](https://eloquentjavascript.net/01_values.html#p_3NJXrCLWRR)Strings written with single or double quotes behave very much the same—the only difference is in which type of quote you need to escape inside of them. Backtick-quoted strings, usually called _template literals_, can do a few more tricks. Apart from being able to span lines, they can also embed other values.
    
    [](https://eloquentjavascript.net/01_values.html#c_1ObyeNEDOw)`half of 100 is ${100 / 2}`

[](https://eloquentjavascript.net/01_values.html#p_ogkFBzzZhi)When you write something inside `${}` in a template literal, its result will be computed, converted to a string, and included at that position. The example produces “_half of 100 is 50_”.

## [](https://eloquentjavascript.net/01_values.html#h_ygn12/ieo+)Unary operators

[](https://eloquentjavascript.net/01_values.html#p_GyQlmgK5IK)Not all operators are symbols. Some are written as words. One example is the `typeof` operator, which produces a string value naming the type of the value you give it.
    
    edit & run code by clicking it
    
    [](https://eloquentjavascript.net/01_values.html#c_iWT//VyY7j)console.log(typeof 4.5) // → number console.log(typeof "x") // → string

[](https://eloquentjavascript.net/01_values.html#p_edv0ySDJvj)We will use `console.log` in example code to indicate that we want to see the result of evaluating something. More about that in the [next chapter](https://eloquentjavascript.net/02_program_structure.html).

[](https://eloquentjavascript.net/01_values.html#p_fvxC7oK7dT)The other operators shown all operated on two values, but `typeof` takes only one. Operators that use two values are called _binary_ operators, while those that take one are called _unary_ operators. The minus operator can be used both as a binary operator and as a unary operator.
    
    [](https://eloquentjavascript.net/01_values.html#c_VpL89RFAPj)console.log(- (10 - 2)) // → -8

## [](https://eloquentjavascript.net/01_values.html#h_cTPxJxlmFR)Boolean values

[](https://eloquentjavascript.net/01_values.html#p_OL3ZufvGRE)It is often useful to have a value that distinguishes between only two possibilities, like “yes” and “no” or “on” and “off”. For this purpose, JavaScript has a _Boolean_ type, which has just two values, true and false, which are written as those words.

### [](https://eloquentjavascript.net/01_values.html#i_Lfz4mKO9Tg)Comparison

[](https://eloquentjavascript.net/01_values.html#p_T4yLn4fXDH)Here is one way to produce Boolean values:
    
    [](https://eloquentjavascript.net/01_values.html#c_GaxnXrIPwC)console.log(3 > 2) // → true console.log(3 < 2) // → false

[](https://eloquentjavascript.net/01_values.html#p_j0tOwzfb6M)The `>` and `<` signs are the traditional symbols for “is greater than” and “is less than”, respectively. They are binary operators. Applying them results in a Boolean value that indicates whether they hold true in this case.

[](https://eloquentjavascript.net/01_values.html#p_NxTGvCsM4s)Strings can be compared in the same way.
    
    [](https://eloquentjavascript.net/01_values.html#c_Qud5plnVuV)console.log("Aardvark" < "Zoroaster") // → true

[](https://eloquentjavascript.net/01_values.html#p_No3uOP/bY2)The way strings are ordered is roughly alphabetic but not really what you’d expect to see in a dictionary: uppercase letters are always “less” than lowercase ones, so `"Z" < "a"`, and nonalphabetic characters (!, -, and so on) are also included in the ordering. When comparing strings, JavaScript goes over the characters from left to right, comparing the Unicode codes one by one.

[](https://eloquentjavascript.net/01_values.html#p_fGKTuK5BBc)Other similar operators are `>=` (greater than or equal to), `<=` (less than or equal to), `==` (equal to), and `!=` (not equal to).
    
    [](https://eloquentjavascript.net/01_values.html#c_9h4L8Mnvdg)console.log("Itchy" != "Scratchy") // → true console.log("Apple" == "Orange") // → false

[](https://eloquentjavascript.net/01_values.html#p_tLooHn2QPj)There is only one value in JavaScript that is not equal to itself, and that is `NaN` (“not a number”).
    
    [](https://eloquentjavascript.net/01_values.html#c_Vhz09Rgw3h)console.log(NaN == NaN) // → false

[](https://eloquentjavascript.net/01_values.html#p_rcMZUIfGYR)`NaN` is supposed to denote the result of a nonsensical computation, and as such, it isn’t equal to the result of any _other_ nonsensical computations.

### [](https://eloquentjavascript.net/01_values.html#i_pdqDW7Pebo)Logical operators

[](https://eloquentjavascript.net/01_values.html#p_nRCLrGwcCn)There are also some operations that can be applied to Boolean values themselves. JavaScript supports three logical operators: _and_, _or_, and _not_. These can be used to “reason” about Booleans.

[](https://eloquentjavascript.net/01_values.html#p_h6pEyNS4IJ)The `&&` operator represents logical _and_. It is a binary operator, and its result is true only if both the values given to it are true.
    
    [](https://eloquentjavascript.net/01_values.html#c_SHi38sNkwM)console.log(true && false) // → false console.log(true && true) // → true

[](https://eloquentjavascript.net/01_values.html#p_T/V30CHY82)The `||` operator denotes logical _or_. It produces true if either of the values given to it is true.
    
    [](https://eloquentjavascript.net/01_values.html#c_diXyv7iPd1)console.log(false || true) // → true console.log(false || false) // → false

[](https://eloquentjavascript.net/01_values.html#p_OxH3G7iBRz)_Not_ is written as an exclamation mark (`!`). It is a unary operator that flips the value given to it—`!true` produces `false`, and `!false` gives `true`.

[](https://eloquentjavascript.net/01_values.html#p_qSXjNNI5/y)When mixing these Boolean operators with arithmetic and other operators, it is not always obvious when parentheses are needed. In practice, you can usually get by with knowing that of the operators we have seen so far, `||` has the lowest precedence, then comes `&&`, then the comparison operators (`>`, `==`, and so on), and then the rest. This order has been chosen such that, in typical expressions like the following one, as few parentheses as possible are necessary:
    
    [](https://eloquentjavascript.net/01_values.html#c_6eZ07bDo11)1 + 1 == 2 && 10 * 10 > 50

[](https://eloquentjavascript.net/01_values.html#p_EWJu4coIAh)The last logical operator I will discuss is not unary, not binary, but _ternary_, operating on three values. It is written with a question mark and a colon, like this:
    
    [](https://eloquentjavascript.net/01_values.html#c_G7eVm8ilWm)console.log(true ? 1 : 2); // → 1 console.log(false ? 1 : 2); // → 2

[](https://eloquentjavascript.net/01_values.html#p_xZmtGs+CeV)This one is called the _conditional_ operator (or sometimes just the _ternary_ operator since it is the only such operator in the language). The value on the left of the question mark “picks” which of the other two values will come out. When it is true, it chooses the middle value, and when it is false, it chooses the value on the right.

## [](https://eloquentjavascript.net/01_values.html#h_FewqJ8K2E+)Empty values

[](https://eloquentjavascript.net/01_values.html#p_Q/OIPtr8xY)There are two special values, written `null` and `undefined`, that are used to denote the absence of a _meaningful_ value. They are themselves values, but they carry no information.

[](https://eloquentjavascript.net/01_values.html#p_3veSnHeYus)Many operations in the language that don’t produce a meaningful value (you’ll see some later) yield `undefined` simply because they have to yield _some_ value.

[](https://eloquentjavascript.net/01_values.html#p_43ZLcQuUDk)The difference in meaning between `undefined` and `null` is an accident of JavaScript’s design, and it doesn’t matter most of the time. In cases where you actually have to concern yourself with these values, I recommend treating them as mostly interchangeable.

## [](https://eloquentjavascript.net/01_values.html#h_AY+YGu6qyM)Automatic type conversion

[](https://eloquentjavascript.net/01_values.html#p_I6CpHrk6+W)In the Introduction, I mentioned that JavaScript goes out of its way to accept almost any program you give it, even programs that do odd things. This is nicely demonstrated by the following expressions:
    
    [](https://eloquentjavascript.net/01_values.html#c_QqYG9KqZ2/)console.log(8 * null) // → 0 console.log("5" - 1) // → 4 console.log("5" + 1) // → 51 console.log("five" * 2) // → NaN console.log(false == 0) // → true

[](https://eloquentjavascript.net/01_values.html#p_3GSZqcE16B)When an operator is applied to the “wrong” type of value, JavaScript will quietly convert that value to the type it needs, using a set of rules that often aren’t what you want or expect. This is called _type coercion_. The `null` in the first expression becomes `0`, and the `"5"` in the second expression becomes `5` (from string to number). Yet in the third expression, `+` tries string concatenation before numeric addition, so the `1` is converted to `"1"` (from number to string).

[](https://eloquentjavascript.net/01_values.html#p_mw5To5JJ6Q)When something that doesn’t map to a number in an obvious way (such as `"five"` or `undefined`) is converted to a number, you get the value `NaN`. Further arithmetic operations on `NaN` keep producing `NaN`, so if you find yourself getting one of those in an unexpected place, look for accidental type conversions.

[](https://eloquentjavascript.net/01_values.html#p_XbK88HE+DJ)When comparing values of the same type using `==`, the outcome is easy to predict: you should get true when both values are the same, except in the case of `NaN`. But when the types differ, JavaScript uses a complicated and confusing set of rules to determine what to do. In most cases, it just tries to convert one of the values to the other value’s type. However, when `null` or `undefined` occurs on either side of the operator, it produces true only if both sides are one of `null` or `undefined`.
    
    [](https://eloquentjavascript.net/01_values.html#c_qmGDPdETlf)console.log(null == undefined); // → true console.log(null == 0); // → false

[](https://eloquentjavascript.net/01_values.html#p_hu+ZqjMro3)That behavior is often useful. When you want to test whether a value has a real value instead of `null` or `undefined`, you can compare it to `null` with the `==` (or `!=`) operator.

[](https://eloquentjavascript.net/01_values.html#p_N4OuWeYOwF)But what if you want to test whether something refers to the precise value `false`? Expressions like `0 == false` and `"" == false` are also true because of automatic type conversion. When you do _not_ want any type conversions to happen, there are two additional operators: `===` and `!==`. The first tests whether a value is _precisely_ equal to the other, and the second tests whether it is not precisely equal. So `"" === false` is false as expected.

[](https://eloquentjavascript.net/01_values.html#p_S/opLpHJcU)I recommend using the three-character comparison operators defensively to prevent unexpected type conversions from tripping you up. But when you’re certain the types on both sides will be the same, there is no problem with using the shorter operators.

### [](https://eloquentjavascript.net/01_values.html#i_3jN0iK4yKW)Short-circuiting of logical operators

[](https://eloquentjavascript.net/01_values.html#p_CFbagJsQYK)The logical operators `&&` and `||` handle values of different types in a peculiar way. They will convert the value on their left side to Boolean type in order to decide what to do, but depending on the operator and the result of that conversion, they will return either the _original_ left-hand value or the right-hand value.

[](https://eloquentjavascript.net/01_values.html#p_BFq+/JeBH9)The `||` operator, for example, will return the value to its left when that can be converted to true and will return the value on its right otherwise. This has the expected effect when the values are Boolean and does something analogous for values of other types.
    
    [](https://eloquentjavascript.net/01_values.html#c_ENjxHGMklb)console.log(null || "user") // → user console.log("Agnes" || "user") // → Agnes

[](https://eloquentjavascript.net/01_values.html#p_+E3wg/b+ti)We can use this functionality as a way to fall back on a default value. If you have a value that might be empty, you can put `||` after it with a replacement value. If the initial value can be converted to false, you’ll get the replacement instead. The rules for converting strings and numbers to Boolean values state that `0`, `NaN`, and the empty string (`""`) count as `false`, while all the other values count as `true`. So `0 || -1` produces `-1`, and `"" || "!?"` yields `"!?"`.

[](https://eloquentjavascript.net/01_values.html#p_LlkwKHpB6u)The `&&` operator works similarly but the other way around. When the value to its left is something that converts to false, it returns that value, and otherwise it returns the value on its right.

[](https://eloquentjavascript.net/01_values.html#p_IW4V8ztNjs)Another important property of these two operators is that the part to their right is evaluated only when necessary. In the case of `true || X`, no matter what `X` is—even if it’s a piece of program that does something _terrible_—the result will be true, and `X` is never evaluated. The same goes for `false && X`, which is false and will ignore `X`. This is called _short-circuit evaluation_.

[](https://eloquentjavascript.net/01_values.html#p_WW6GFa4Qbm)The conditional operator works in a similar way. Of the second and third values, only the one that is selected is evaluated.

## [](https://eloquentjavascript.net/01_values.html#h_ErccPg/l98)Summary

[](https://eloquentjavascript.net/01_values.html#p_K8XmHEfEpW)We looked at four types of JavaScript values in this chapter: numbers, strings, Booleans, and undefined values.

[](https://eloquentjavascript.net/01_values.html#p_3rwX3Mq/e/)Such values are created by typing in their name (`true`, `null`) or value (`13`, `"abc"`). You can combine and transform values with operators. We saw binary operators for arithmetic (`+`, `-`, `*`, `/`, and `%`), string concatenation (`+`), comparison (`==`, `!=`, `===`, `!==`, `<`, `>`, `<=`, `>=`), and logic (`&&`, `||`), as well as several unary operators (`-` to negate a number, `!` to negate logically, and `typeof` to find a value’s type) and a ternary operator (`?:`) to pick one of two values based on a third value.

[](https://eloquentjavascript.net/01_values.html#p_WHkzsJyNsJ)This gives you enough information to use JavaScript as a pocket calculator but not much more. The [next chapter](https://eloquentjavascript.net/02_program_structure.html) will start tying these expressions together into basic programs.
