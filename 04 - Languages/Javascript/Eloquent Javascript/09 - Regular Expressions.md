```
Source:
Tags: 
Last-Updated:
```

<<<<<<< Updated upstream
# Chapter 9Regular Expressions

> [](https://eloquentjavascript.net/09_regexp.html#p_MWUwIAb0uO)Some people, when confronted with a problem, think ‘I know, I’ll use regular expressions.’ Now they have two problems.
> 
> Jamie Zawinski

> [](https://eloquentjavascript.net/09_regexp.html#p_icxlw7+18l)Yuan-Ma said, ‘When you cut against the grain of the wood, much strength is needed. When you program against the grain of the problem, much code is needed.’
> 
=======
# 09 Regular Expressions

> Some people, when confronted with a problem, think ‘I know, I’ll use regular expressions.’ Now they have two problems.
> Jamie Zawinski

> Yuan-Ma said, ‘When you cut against the grain of the wood, much strength is needed. When you program against the grain of the problem, much code is needed.’
>>>>>>> Stashed changes
> Master Yuan-Ma, The Book of Programming

![A railroad diagram](https://eloquentjavascript.net/img/chapter_picture_9.jpg)

<<<<<<< Updated upstream
[](https://eloquentjavascript.net/09_regexp.html#p_mYvGNMWwx9)Programming tools and techniques survive and spread in a chaotic, evolutionary way. It’s not always the pretty or brilliant ones that win but rather the ones that function well enough within the right niche or that happen to be integrated with another successful piece of technology.

[](https://eloquentjavascript.net/09_regexp.html#p_iH3Aqi6y2A)In this chapter, I will discuss one such tool, _regular expressions_. Regular expressions are a way to describe patterns in string data. They form a small, separate language that is part of JavaScript and many other languages and systems.

[](https://eloquentjavascript.net/09_regexp.html#p_cxbejyPUGl)Regular expressions are both terribly awkward and extremely useful. Their syntax is cryptic, and the programming interface JavaScript provides for them is clumsy. But they are a powerful tool for inspecting and processing strings. Properly understanding regular expressions will make you a more effective programmer.

## [](https://eloquentjavascript.net/09_regexp.html#h_5w4yGFJRYl)Creating a regular expression

[](https://eloquentjavascript.net/09_regexp.html#p_u/9SKAI2Yi)A regular expression is a type of object. It can be either constructed with the `RegExp` constructor or written as a literal value by enclosing a pattern in forward slash (`/`) characters.
    
    edit & run code by clicking it
    
    [](https://eloquentjavascript.net/09_regexp.html#c_O1I2rl+HTy)let re1 = new RegExp("abc"); let re2 = /abc/;

[](https://eloquentjavascript.net/09_regexp.html#p_dviEva2QQM)Both of those regular expression objects represent the same pattern: an _a_ character followed by a _b_ followed by a _c_.

[](https://eloquentjavascript.net/09_regexp.html#p_qv8UWLVrTv)When using the `RegExp` constructor, the pattern is written as a normal string, so the usual rules apply for backslashes.

[](https://eloquentjavascript.net/09_regexp.html#p_0mNIcPpslS)The second notation, where the pattern appears between slash characters, treats backslashes somewhat differently. First, since a forward slash ends the pattern, we need to put a backslash before any forward slash that we want to be _part_ of the pattern. In addition, backslashes that aren’t part of special character codes (like ` `) will be _preserved_, rather than ignored as they are in strings, and change the meaning of the pattern. Some characters, such as question marks and plus signs, have special meanings in regular expressions and must be preceded by a backslash if they are meant to represent the character itself.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_uRzUiBSrul)let eighteenPlus = /eighteen\+/;

## [](https://eloquentjavascript.net/09_regexp.html#h_vPyyYjMEtz)Testing for matches

[](https://eloquentjavascript.net/09_regexp.html#p_SHaMWlzFzk)Regular expression objects have a number of methods. The simplest one is `test`. If you pass it a string, it will return a Boolean telling you whether the string contains a match of the pattern in the expression.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_Szn1CmrIV5)console.log(/abc/.test("abcde")); // → true console.log(/abc/.test("abxde")); // → false

[](https://eloquentjavascript.net/09_regexp.html#p_YGcbMDV493)A regular expression consisting of only nonspecial characters simply represents that sequence of characters. If _abc_ occurs anywhere in the string we are testing against (not just at the start), `test` will return `true`.

## [](https://eloquentjavascript.net/09_regexp.html#h_8EFR0DU1xd)Sets of characters

[](https://eloquentjavascript.net/09_regexp.html#p_ZyB7HeLr75)Finding out whether a string contains _abc_ could just as well be done with a call to `indexOf`. Regular expressions allow us to express more complicated patterns.

[](https://eloquentjavascript.net/09_regexp.html#p_i/99SEfu9y)Say we want to match any number. In a regular expression, putting a set of characters between square brackets makes that part of the expression match any of the characters between the brackets.

[](https://eloquentjavascript.net/09_regexp.html#p_sC+2E08KnL)Both of the following expressions match all strings that contain a digit:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_Z3UJdL//cY)console.log(/[0123456789]/.test("in 1992")); // → true console.log(/[0-9]/.test("in 1992")); // → true

[](https://eloquentjavascript.net/09_regexp.html#p_i0WYLVUede)Within square brackets, a hyphen (`-`) between two characters can be used to indicate a range of characters, where the ordering is determined by the character’s Unicode number. Characters 0 to 9 sit right next to each other in this ordering (codes 48 to 57), so `[0-9]` covers all of them and matches any digit.

[](https://eloquentjavascript.net/09_regexp.html#p_1qtYlDfA/1)A number of common character groups have their own built-in shortcuts. Digits are one of them: `\d` means the same thing as `[0-9]`.

`\d`
Any digit character

`\w`
An alphanumeric character (“word character”)

`\s`
Any whitespace character (space, tab, newline, and similar)

`\D`
A character that is _not_ a digit

`\W`
A nonalphanumeric character

`\S`
A nonwhitespace character

`.`
Any character except for newline

[](https://eloquentjavascript.net/09_regexp.html#p_yXMUKEYpwG)So you could match a date and time format like 01-30-2003 15:20 with the following expression:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_Y0e7M8nAL0)let dateTime = /\d\d-\d\d-\d\d\d\d \d\d:\d\d/; console.log(dateTime.test("01-30-2003 15:20")); // → true console.log(dateTime.test("30-jan-2003 15:20")); // → false

[](https://eloquentjavascript.net/09_regexp.html#p_gdY0EhLXlE)That looks completely awful, doesn’t it? Half of it is backslashes, producing a background noise that makes it hard to spot the actual pattern expressed. We’ll see a slightly improved version of this expression [later](https://eloquentjavascript.net/09_regexp.html#date_regexp_counted).

[](https://eloquentjavascript.net/09_regexp.html#p_P0qAMYu0C/)These backslash codes can also be used inside square brackets. For example, `[\d.]` means any digit or a period character. But the period itself, between square brackets, loses its special meaning. The same goes for other special characters, such as `+`.

[](https://eloquentjavascript.net/09_regexp.html#p_HqQEZsitdl)To _invert_ a set of characters—that is, to express that you want to match any character _except_ the ones in the set—you can write a caret (`^`) character after the opening bracket.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_XH8deAcckk)let notBinary = /[^01]/; console.log(notBinary.test("1100100010100110")); // → false console.log(notBinary.test("1100100010200110")); // → true

## [](https://eloquentjavascript.net/09_regexp.html#h_iFI1qvUwY9)Repeating parts of a pattern

[](https://eloquentjavascript.net/09_regexp.html#p_crYiu/oAUM)We now know how to match a single digit. What if we want to match a whole number—a sequence of one or more digits?

[](https://eloquentjavascript.net/09_regexp.html#p_B4wupHzbR+)When you put a plus sign (`+`) after something in a regular expression, it indicates that the element may be repeated more than once. Thus, `/\d+/` matches one or more digit characters.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_9/5mFF4Ih4)console.log(/'\d+'/.test("'123'")); // → true console.log(/'\d+'/.test("''")); // → false console.log(/'\d*'/.test("'123'")); // → true console.log(/'\d*'/.test("''")); // → true

[](https://eloquentjavascript.net/09_regexp.html#p_/oNBIVm41F)The star (`*`) has a similar meaning but also allows the pattern to match zero times. Something with a star after it never prevents a pattern from matching—it’ll just match zero instances if it can’t find any suitable text to match.

[](https://eloquentjavascript.net/09_regexp.html#p_77Y5t9C8NV)A question mark makes a part of a pattern _optional_, meaning it may occur zero times or one time. In the following example, the _u_ character is allowed to occur, but the pattern also matches when it is missing.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_EiCIowdq+d)let neighbor = /neighbou?r/; console.log(neighbor.test("neighbour")); // → true console.log(neighbor.test("neighbor")); // → true

[](https://eloquentjavascript.net/09_regexp.html#p_B4ikd8xN8i)To indicate that a pattern should occur a precise number of times, use braces. Putting `{4}` after an element, for example, requires it to occur exactly four times. It is also possible to specify a range this way: `{2,4}` means the element must occur at least twice and at most four times.

[](https://eloquentjavascript.net/09_regexp.html#p_a1yNHuI+49)Here is another version of the date and time pattern that allows both single- and double-digit days, months, and hours. It is also slightly easier to decipher.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_Tw+K6Mxe45)let dateTime = /\d{1,2}-\d{1,2}-\d{4} \d{1,2}:\d{2}/; console.log(dateTime.test("1-30-2003 8:45")); // → true

[](https://eloquentjavascript.net/09_regexp.html#p_RjqN6VMQIa)You can also specify open-ended ranges when using braces by omitting the number after the comma. So, `{5,}` means five or more times.

## [](https://eloquentjavascript.net/09_regexp.html#h_uICSDspz1I)Grouping subexpressions

[](https://eloquentjavascript.net/09_regexp.html#p_pKTOYUDGIr)To use an operator like `*` or `+` on more than one element at a time, you have to use parentheses. A part of a regular expression that is enclosed in parentheses counts as a single element as far as the operators following it are concerned.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_P/f6a65XwI)let cartoonCrying = /boo+(hoo+)+/i; console.log(cartoonCrying.test("Boohoooohoohooo")); // → true

[](https://eloquentjavascript.net/09_regexp.html#p_S5jkv2dMC+)The first and second `+` characters apply only to the second _o_ in _boo_ and _hoo_, respectively. The third `+` applies to the whole group `(hoo+)`, matching one or more sequences like that.

[](https://eloquentjavascript.net/09_regexp.html#p_c4RlIM4/HI)The `i` at the end of the expression in the example makes this regular expression case insensitive, allowing it to match the uppercase _B_ in the input string, even though the pattern is itself all lowercase.

## [](https://eloquentjavascript.net/09_regexp.html#h_CV5XL/TADP)Matches and groups

[](https://eloquentjavascript.net/09_regexp.html#p_K3KRDzatsp)The `test` method is the absolute simplest way to match a regular expression. It tells you only whether it matched and nothing else. Regular expressions also have an `exec` (execute) method that will return `null` if no match was found and return an object with information about the match otherwise.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_JJMWZpk0iD)let match = /\d+/.exec("one two 100"); console.log(match); // → ["100"] console.log(match.index); // → 8

[](https://eloquentjavascript.net/09_regexp.html#p_fJSwbQyG6w)An object returned from `exec` has an `index` property that tells us _where_ in the string the successful match begins. Other than that, the object looks like (and in fact is) an array of strings, whose first element is the string that was matched. In the previous example, this is the sequence of digits that we were looking for.

[](https://eloquentjavascript.net/09_regexp.html#p_VT4fpht7D7)String values have a `match` method that behaves similarly.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_uAkAqNYx+q)console.log("one two 100".match(/\d+/)); // → ["100"]

[](https://eloquentjavascript.net/09_regexp.html#p_/9rdcJO9zZ)When the regular expression contains subexpressions grouped with parentheses, the text that matched those groups will also show up in the array. The whole match is always the first element. The next element is the part matched by the first group (the one whose opening parenthesis comes first in the expression), then the second group, and so on.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_5E2M1BBsUm)let quotedText = /'([^']*)'/; console.log(quotedText.exec("she said 'hello'")); // → ["'hello'", "hello"]

[](https://eloquentjavascript.net/09_regexp.html#p_f4bciMASJ1)When a group does not end up being matched at all (for example, when followed by a question mark), its position in the output array will hold `undefined`. Similarly, when a group is matched multiple times, only the last match ends up in the array.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_j9t+gn+1eT)console.log(/bad(ly)?/.exec("bad")); // → ["bad", undefined] console.log(/(\d)+/.exec("123")); // → ["123", "3"]

[](https://eloquentjavascript.net/09_regexp.html#p_GvLofvnQnz)Groups can be useful for extracting parts of a string. If we don’t just want to verify whether a string contains a date but also extract it and construct an object that represents it, we can wrap parentheses around the digit patterns and directly pick the date out of the result of `exec`.

[](https://eloquentjavascript.net/09_regexp.html#p_DzNUSBaBZb)But first we’ll take a brief detour, in which we discuss the built-in way to represent date and time values in JavaScript.

## [](https://eloquentjavascript.net/09_regexp.html#h_8U7L7LCU27)The Date class

[](https://eloquentjavascript.net/09_regexp.html#p_2NeTRvucQq)JavaScript has a standard class for representing dates—or, rather, points in time. It is called `Date`. If you simply create a date object using `new`, you get the current date and time.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_AjgqFetryg)console.log(new Date()); // → Mon Nov 13 2017 16:19:11 GMT+0100 (CET)

[](https://eloquentjavascript.net/09_regexp.html#p_IcV7kv3B1y)You can also create an object for a specific time.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_2VCU0f4HsQ)console.log(new Date(2009, 11, 9)); // → Wed Dec 09 2009 00:00:00 GMT+0100 (CET) console.log(new Date(2009, 11, 9, 12, 59, 59, 999)); // → Wed Dec 09 2009 12:59:59 GMT+0100 (CET)

[](https://eloquentjavascript.net/09_regexp.html#p_cYaexzwHiw)JavaScript uses a convention where month numbers start at zero (so December is 11), yet day numbers start at one. This is confusing and silly. Be careful.

[](https://eloquentjavascript.net/09_regexp.html#p_gVdQSb0Lv9)The last four arguments (hours, minutes, seconds, and milliseconds) are optional and taken to be zero when not given.

[](https://eloquentjavascript.net/09_regexp.html#p_1mIMU5T5MA)Timestamps are stored as the number of milliseconds since the start of 1970, in the UTC time zone. This follows a convention set by “Unix time”, which was invented around that time. You can use negative numbers for times before 1970. The `getTime` method on a date object returns this number. It is big, as you can imagine.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_lMlCuckMIc)console.log(new Date(2013, 11, 19).getTime()); // → 1387407600000 console.log(new Date(1387407600000)); // → Thu Dec 19 2013 00:00:00 GMT+0100 (CET)

[](https://eloquentjavascript.net/09_regexp.html#p_Cn9WUyCZhq)If you give the `Date` constructor a single argument, that argument is treated as such a millisecond count. You can get the current millisecond count by creating a new `Date` object and calling `getTime` on it or by calling the `Date.now` function.

[](https://eloquentjavascript.net/09_regexp.html#p_iqL2Ehg9D4)Date objects provide methods such as `getFullYear`, `getMonth`, `getDate`, `getHours`, `getMinutes`, and `getSeconds` to extract their components. Besides `getFullYear` there’s also `getYear`, which gives you the year minus 1900 (`98` or `119`) and is mostly useless.

[](https://eloquentjavascript.net/09_regexp.html#p_/RCtQyD3w/)Putting parentheses around the parts of the expression that we are interested in, we can now create a date object from a string.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_xW0xfMnpiZ)function getDate(string) { let [_, month, day, year] = /(\d{1,2})-(\d{1,2})-(\d{4})/.exec(string); return new Date(year, month - 1, day); } console.log(getDate("1-30-2003")); // → Thu Jan 30 2003 00:00:00 GMT+0100 (CET)

[](https://eloquentjavascript.net/09_regexp.html#p_YUOJEGEtSI)The `_` (underscore) binding is ignored and used only to skip the full match element in the array returned by `exec`.

## [](https://eloquentjavascript.net/09_regexp.html#h_26ixny78VY)Word and string boundaries

[](https://eloquentjavascript.net/09_regexp.html#p_xdYJVr9vlf)Unfortunately, `getDate` will also happily extract the nonsensical date 00-1-3000 from the string `"100-1-30000"`. A match may happen anywhere in the string, so in this case, it’ll just start at the second character and end at the second-to-last character.

[](https://eloquentjavascript.net/09_regexp.html#p_kLS7rqRrqG)If we want to enforce that the match must span the whole string, we can add the markers `^` and `$`. The caret matches the start of the input string, whereas the dollar sign matches the end. So, `/^\d+$/` matches a string consisting entirely of one or more digits, `/^!/` matches any string that starts with an exclamation mark, and `/x^/` does not match any string (there cannot be an _x_ before the start of the string).

[](https://eloquentjavascript.net/09_regexp.html#p_fEYS5Ev94W)If, on the other hand, we just want to make sure the date starts and ends on a word boundary, we can use the marker ``. A word boundary can be the start or end of the string or any point in the string that has a word character (as in `\w`) on one side and a nonword character on the other.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_6U0b866tUk)console.log(/cat/.test("concatenate")); // → true console.log(/cat/.test("concatenate")); // → false

[](https://eloquentjavascript.net/09_regexp.html#p_btxd6luedx)Note that a boundary marker doesn’t match an actual character. It just enforces that the regular expression matches only when a certain condition holds at the place where it appears in the pattern.

## [](https://eloquentjavascript.net/09_regexp.html#h_In3b+t6uOO)Choice patterns

[](https://eloquentjavascript.net/09_regexp.html#p_G5RTt0AFku)Say we want to know whether a piece of text contains not only a number but a number followed by one of the words _pig_, _cow_, or _chicken_, or any of their plural forms.

[](https://eloquentjavascript.net/09_regexp.html#p_GcEbQJT+nS)We could write three regular expressions and test them in turn, but there is a nicer way. The pipe character (`|`) denotes a choice between the pattern to its left and the pattern to its right. So I can say this:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_z0soEIN8RB)let animalCount = /\d+ (pig|cow|chicken)s?/; console.log(animalCount.test("15 pigs")); // → true console.log(animalCount.test("15 pigchickens")); // → false

[](https://eloquentjavascript.net/09_regexp.html#p_bPWKulKcxf)Parentheses can be used to limit the part of the pattern that the pipe operator applies to, and you can put multiple such operators next to each other to express a choice between more than two alternatives.

## [](https://eloquentjavascript.net/09_regexp.html#h_AzxCBCKdvY)The mechanics of matching

[](https://eloquentjavascript.net/09_regexp.html#p_SXQOi9ZwwH)Conceptually, when you use `exec` or `test`, the regular expression engine looks for a match in your string by trying to match the expression first from the start of the string, then from the second character, and so on, until it finds a match or reaches the end of the string. It’ll either return the first match that can be found or fail to find any match at all.

[](https://eloquentjavascript.net/09_regexp.html#p_HJjJAo8dQp)To do the actual matching, the engine treats a regular expression something like a flow diagram. This is the diagram for the livestock expression in the previous example:

![Visualization of /\d+ (pig|cow|chicken)s?/](https://eloquentjavascript.net/img/re_pigchickens.svg)

[](https://eloquentjavascript.net/09_regexp.html#p_SNiUdMyezk)Our expression matches if we can find a path from the left side of the diagram to the right side. We keep a current position in the string, and every time we move through a box, we verify that the part of the string after our current position matches that box.

[](https://eloquentjavascript.net/09_regexp.html#p_MB99a8uIlE)So if we try to match `"the 3 pigs"` from position 4, our progress through the flow chart would look like this:
=======


Regular expressions are a way to describe patterns in string data. Properly understanding regular expressions will make you a more effective programmer.

## Creating a regular expression

A regular expression is a type of object. It can be either constructed with the `RegExp` constructor or written as a literal value by enclosing a pattern in forward slash (`/`) characters.
    
```js
let re1 = new RegExp("abc"); 
let re2 = /abc/;
```

Both of those regular expression objects represent the same pattern: an _a_ character followed by a _b_ followed by a _c_.

When using the `RegExp` constructor, the pattern is written as a normal string, so the usual rules apply for backslashes.

A forward slash ends the pattern, we need to put a backslash before any forward slash that we want to be _part_ of the pattern. In addition, backslashes that aren’t part of special character codes (like `\n`) will be _preserved_, rather than ignored as they are in strings, and change the meaning of the pattern. 

Some characters, such as question marks and plus signs, have special meanings in regular expressions and must be preceded by a backslash if they are meant to represent the character itself.

```js    
let eighteenPlus = /eighteen\+/;
```

## Testing for matches

Regular expression objects have a number of methods. 

The simplest one is `test`. If you pass it a string, it will return a Boolean telling you whether the string contains a match of the pattern in the expression.

```js    
console.log(/abc/.test("abcde")); // → true console.log(/abc/.test("abxde")); // → false
```

A regular expression consisting of only nonspecial characters simply represents that sequence of characters. If _abc_ occurs anywhere in the string we are testing against (not just at the start), `test` will return `true`.

## Sets of characters

Fiinding if a string contains _abc_ could just as well be done with a call to `indexOf`, but Regex allows to express more complicated patterns.

To match any number in a set, put a set of characters between square brackets to test the match for them. 

```js    
    []console.log(/[0123456789]/.test("in 1992")); 
	// → true 
	console.log(/[0-9]/.test("in 1992")); 
	// → true
```

Within square brackets, a hyphen (`-`) between two characters can be used to indicate a range of characters, where the ordering is determined by the character’s Unicode number. 

Characters 0 to 9 sit right next to each other in this ordering (codes 48 to 57), so `[0-9]` covers all of them and matches any digit.
A number of common character groups have their own built-in shortcuts.

- `\d` Any digit character (`[0-9]`)
- `\w` An alphanumeric character (“word character”)
- `\s` Any whitespace character (space, tab, newline, and similar)
- `\D` A character that is _not_ a digit
- `\W` A nonalphanumeric character
- `\S` A nonwhitespace character
- `.` Any character except for newline

So you could match a date and time format like 01-30-2003 15:20 with the following expression:
```js    
let dateTime = /\d\d-\d\d-\d\d\d\d \d\d:\d\d/; console.log(dateTime.test("01-30-2003 15:20")); 
// → true 
console.log(dateTime.test("30-jan-2003 15:20")); 
// → false
```

That looks completely awful, doesn’t it? Half of it is backslashes, making it hard to spot the  pattern expressed. We’ll improve this expression [later].


These backslash codes can also be used inside square brackets. For example, `[\d.]` means any digit or a period character. But the period itself, between square brackets, loses its special meaning. The same goes for other special characters, such as `+`.

To _invert_ a set of characters us a caret (`^`) after an opening bracket. to express that you want to match any character _except_ the ones in the set—.

```js
let notBinary = /[^01]/; console.log(notBinary.test("1100100010100110")); 
// → false console.log(notBinary.test("1100100010200110")); 
// → true
```


## Repeating parts of a pattern

We now know how to match a single digit. What if we want to match a whole number—a sequence of one or more digits?

A plus sign (`+`) after something in a regex, indicates the element may be repeated more than once. Thus, `/\d+/` matches one or more digit characters.
    
```js
console.log(/'\d+'/.test("'123'")); // → true console.log(/'\d+'/.test("''")); // → false console.log(/'\d*'/.test("'123'")); // → true console.log(/'\d*'/.test("''")); // → true
```

The star (`*`) has a similar meaning but also allows the pattern to match zero times. Something with a star after it never prevents a pattern from matching—it’ll just match zero instances if it can’t find any suitable text to match.

A question mark (`?`) makes a part of a pattern _optional_, meaning it may occur zero times or one time. In the following example, the _u_ character is allowed to occur, but the pattern also matches when it is missing.

```js   
let neighbor = /neighbou?r/; console.log(neighbor.test("neighbour")); // → true console.log(neighbor.test("neighbor")); // → true
```

To indicate that a pattern should occur a precise number of times, use braces. Putting `{4}` after an element, for example, requires it to occur exactly four times. It can specify a range too: `{2,4}` means the element must occur at least twice and at most four times. You can also specify open-ended ranges when using braces by omitting the number after the comma. So, `{5,}` means five or more times.


Here is another version of the date and time pattern that allows both single- and double-digit days, months, and hours. It is also slightly easier to decipher.
    
```js
let dateTime = /\d{1,2}-\d{1,2}-\d{4} \d{1,2}:\d{2}/; console.log(dateTime.test("1-30-2003 8:45")); 
// → true
```


## Grouping subexpressions

To use an operator like `*` or `+` on more than one element at a time, you have to use parentheses. A part of a regular expression that is enclosed in parentheses counts as a single element as far as the operators following it are concerned.


```js    
let cartoonCrying = /boo+(hoo+)+/i; console.log(cartoonCrying.test("Boohoooohoohooo")); 
// → true
```


The first and second `+` characters apply only to the second _o_ in _boo_ and _hoo_, respectively. The third `+` applies to the whole group `(hoo+)`, matching one or more sequences like that.

The `i` at the end of the expression in the example makes this regular expression case insensitive, allowing it to match the uppercase _B_ in the input string, even though the pattern is itself all lowercase.

## Matches and groups

The `test` method is the absolute simplest way to match a regular expression. It tells you only whether it matched and nothing else. Regular expressions also have an `exec` (execute) method that will return `null` if no match was found and return an object with information about the match otherwise.

```js
let match = /\d+/.exec("one two 100"); console.log(match); // → ["100"] console.log(match.index); // → 8
```

An object returned from `exec` has an `index` property that tells us _where_ in the string the successful match begins. 

Other than that, the object looks like (and in fact is) an array of strings, whose first element is the string that was matched. In the previous example, this is the sequence of digits that we were looking for.

String values have a `match` method that behaves similarly.

```js    
console.log("one two 100".match(/\d+/)); // → ["100"]
```

When the regular expression contains subexpressions grouped with parentheses, the text that matched those groups will also show up in the array. The whole match is always the first element. The next element is the part matched by the first group (the one whose opening parenthesis comes first in the expression), then the second group, and so on.

```js   
let quotedText = /'([^']*)'/; console.log(quotedText.exec("she said 'hello'")); // → ["'hello'", "hello"]
```

When a group does not end up being matched at all (for example, when followed by a question mark), its position in the output array will hold `undefined`. Similarly, when a group is matched multiple times, only the last match ends up in the array.

```js
console.log(/bad(ly)?/.exec("bad")); 
// → ["bad", undefined] console.log(/(\d)+/.exec("123")); 
// → ["123", "3"]
```

Groups can be useful for extracting parts of a string. If we don’t just want to verify whether a string contains a date but also extract it and construct an object that represents it, we can wrap parentheses around the digit patterns and directly pick the date out of the result of `exec`.

But first we’ll take a brief detour, in which we discuss the built-in way to represent date and time values in JavaScript.

## The Date class

JavaScript has a standard class for representing dates—or, rather, points in time called `Date`. If you simply create a date object using `new`, you get the current date and time.
```js
console.log(new Date()); // → Mon Nov 13 2017 16:19:11 GMT+0100 (CET)
```
You can also create an object for a specific time.

```js  
console.log(new Date(2009, 11, 9)); 
// → Wed Dec 09 2009 00:00:00 GMT+0100 (CET)
console.log(new Date(2009, 11, 9, 12, 59, 59, 999));
// → Wed Dec 09 2009 12:59:59 GMT+0100 (CET)
```

> JavaScript uses a convention where month numbers start at zero (so December is 11), yet day numbers start at one. This is confusing and silly. Be careful.

The last four arguments (hours, minutes, seconds, and milliseconds) are optional and taken to be zero when not given.

Timestamps are stored as the number of milliseconds since the start of 1970, in the UTC time zone. This follows a convention set by “Unix time”, which was invented around that time. You can use negative numbers for times before 1970. The `getTime` method on a date object returns this number. It is big, as you can imagine.

```js    
console.log(new Date(2013, 11, 19).getTime()); 
// → 1387407600000 
console.log(new Date(1387407600000)); 
// → Thu Dec 19 2013 00:00:00 GMT+0100 (CET)
```

If you give the `Date` constructor a single argument, that argument is treated as such a millisecond count. You can get the current millisecond count by creating a new `Date` object and calling `getTime` on it or by calling the `Date.now` function.

Date objects provide methods such as `getFullYear`, `getMonth`, `getDate`, `getHours`, `getMinutes`, and `getSeconds` to extract their components. Besides `getFullYear` there’s also `getYear`, which gives you the year minus 1900 (`98` or `119`) and is mostly useless.

Putting parentheses around the parts of the expression that we are interested in, we can now create a date object from a string.

```js  
function getDate(string) { 
	let [_, month, day, year] = 
		/(\d{1,2})-(\d{1,2})-(\d{4})/.exec(string); 
	return new Date(year, month - 1, day); 
} 
console.log(getDate("1-30-2003")); 
// → Thu Jan 30 2003 00:00:00 GMT+0100 (CET)
```

The `_` (underscore) binding is ignored and used only to skip the full match element in the array returned by `exec`.

## Word and string boundaries

Unfortunately, `getDate` will also happily extract the nonsensical date 00-1-3000 from the string `"100-1-30000"`. A match may happen anywhere in the string, so in this case, it’ll just start at the second character and end at the second-to-last character.

If we want to enforce that the match must span the whole string, we can add the markers `^` and `$`. The caret matches the start of the input string, whereas the dollar sign matches the end. So, `/^\d+$/` matches a string consisting entirely of one or more digits, `/^!/` matches any string that starts with an exclamation mark, and `/x^/` does not match any string (there cannot be an _x_ before the start of the string).

The marker `\b` can make sure the date starts and ends on a word boundary . A word boundary can be the start or end of the string or any point in the string that has a word character (as in `\w`) on one side and a nonword character on the other.

#TODO: expand on boundary usages

```js    
console.log(/cat/.test("concatenate")); 
// → true 
console.log(/\bcat\b/.test("concatenate")); 
// → false
```

Note that a boundary marker doesn’t match an actual character. It just enforces that the regular expression matches only when a certain condition holds at the place where it appears in the pattern.

## Choice patterns

#TODO: Continue from here. 

Say we want to know whether a piece of text contains not only a number but a number followed by one of the words _pig_, _cow_, or _chicken_, or any of their plural forms.

We could write three regular expressions and test them in turn, but there is a nicer way. The pipe character (`|`) denotes a choice between the pattern to its left and the pattern to its right. So I can say this:
```js
	let animalCount = /\b\d+ (pig|cow|chicken)s?\b/; 
	console.log(animalCount.test("15 pigs")); 
	// → true 
	console.log(animalCount.test("15 pigchickens")); 
	// → false
```
Parentheses can be used to limit the part of the pattern that the pipe operator applies to, and you can put multiple such operators next to each other to express a choice between more than two alternatives.

## The mechanics of matching

Conceptually, when you use `exec` or `test`, the regular expression engine looks for a match in your string by trying to match the expression first from the start of the string, then from the second character, and so on, until it finds a match or reaches the end of the string. It’ll either return the first match that can be found or fail to find any match at all.

To do the actual matching, the engine treats a regular expression something like a flow diagram. This is the diagram for the livestock expression in the previous example:

![Visualization of /\d+ (pig|cow|chicken)s?/](https://eloquentjavascript.net/img/re_pigchickens.svg)

Our expression matches if we can find a path from the left side of the diagram to the right side. We keep a current position in the string, and every time we move through a box, we verify that the part of the string after our current position matches that box.

So if we try to match `"the 3 pigs"` from position 4, our progress through the flow chart would look like this:
>>>>>>> Stashed changes

  * [](https://eloquentjavascript.net/09_regexp.html#p_bgxoerTVW4)At position 4, there is a word boundary, so we can move past the first box.

  * [](https://eloquentjavascript.net/09_regexp.html#p_YCV1/H+Rbe)Still at position 4, we find a digit, so we can also move past the second box.

  * [](https://eloquentjavascript.net/09_regexp.html#p_fQdWHxKgCF)At position 5, one path loops back to before the second (digit) box, while the other moves forward through the box that holds a single space character. There is a space here, not a digit, so we must take the second path.

  * [](https://eloquentjavascript.net/09_regexp.html#p_KItk5iNp9m)We are now at position 6 (the start of _pigs_) and at the three-way branch in the diagram. We don’t see _cow_ or _chicken_ here, but we do see _pig_, so we take that branch.

  * [](https://eloquentjavascript.net/09_regexp.html#p_SowlGZC6lM)At position 9, after the three-way branch, one path skips the _s_ box and goes straight to the final word boundary, while the other path matches an _s_. There is an _s_ character here, not a word boundary, so we go through the _s_ box.

  * [](https://eloquentjavascript.net/09_regexp.html#p_oJRMcnDoAt)We’re at position 10 (the end of the string) and can match only a word boundary. The end of a string counts as a word boundary, so we go through the last box and have successfully matched this string.

## [](https://eloquentjavascript.net/09_regexp.html#h_NFMtGK0tD3)Backtracking

<<<<<<< Updated upstream
[](https://eloquentjavascript.net/09_regexp.html#p_tCd15MFAty)The regular expression `/([01]+b|[\da-f]+h|\d+)/` matches either a binary number followed by a _b_, a hexadecimal number (that is, base 16, with the letters _a_ to _f_ standing for the digits 10 to 15) followed by an _h_, or a regular decimal number with no suffix character. This is the corresponding diagram:

![Visualization of /([01]+b|\d+|[\da-f]+h)/](https://eloquentjavascript.net/img/re_number.svg)

[](https://eloquentjavascript.net/09_regexp.html#p_MypvfTaiTG)When matching this expression, it will often happen that the top (binary) branch is entered even though the input does not actually contain a binary number. When matching the string `"103"`, for example, it becomes clear only at the 3 that we are in the wrong branch. The string _does_ match the expression, just not the branch we are currently in.

[](https://eloquentjavascript.net/09_regexp.html#p_SjTCKE9hvf)So the matcher _backtracks_. When entering a branch, it remembers its current position (in this case, at the start of the string, just past the first boundary box in the diagram) so that it can go back and try another branch if the current one does not work out. For the string `"103"`, after encountering the 3 character, it will start trying the branch for hexadecimal numbers, which fails again because there is no _h_ after the number. So it tries the decimal number branch. This one fits, and a match is reported after all.

[](https://eloquentjavascript.net/09_regexp.html#p_VymH7raTcU)The matcher stops as soon as it finds a full match. This means that if multiple branches could potentially match a string, only the first one (ordered by where the branches appear in the regular expression) is used.

[](https://eloquentjavascript.net/09_regexp.html#p_zEBIV8lYeb)Backtracking also happens for repetition operators like + and `*`. If you match `/^.*x/` against `"abcxe"`, the `.*` part will first try to consume the whole string. The engine will then realize that it needs an _x_ to match the pattern. Since there is no _x_ past the end of the string, the star operator tries to match one character less. But the matcher doesn’t find an _x_ after `abcx` either, so it backtracks again, matching the star operator to just `abc`. _Now_ it finds an _x_ where it needs it and reports a successful match from positions 0 to 4.

[](https://eloquentjavascript.net/09_regexp.html#p_0MBBMH8aI2)It is possible to write regular expressions that will do a _lot_ of backtracking. This problem occurs when a pattern can match a piece of input in many different ways. For example, if we get confused while writing a binary-number regular expression, we might accidentally write something like `/([01]+)+b/`.

![Visualization of /([01]+)+b/](https://eloquentjavascript.net/img/re_slow.svg)

[](https://eloquentjavascript.net/09_regexp.html#p_5cI0Ma3Wy8)If that tries to match some long series of zeros and ones with no trailing _b_ character, the matcher first goes through the inner loop until it runs out of digits. Then it notices there is no _b_, so it backtracks one position, goes through the outer loop once, and gives up again, trying to backtrack out of the inner loop once more. It will continue to try every possible route through these two loops. This means the amount of work _doubles_ with each additional character. For even just a few dozen characters, the resulting match will take practically forever.

## [](https://eloquentjavascript.net/09_regexp.html#h_k0YuTOu54D)The replace method

[](https://eloquentjavascript.net/09_regexp.html#p_HMQv5qrs78)String values have a `replace` method that can be used to replace part of the string with another string.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_dPdIdK/Wyi)console.log("papa".replace("p", "m")); // → mapa

[](https://eloquentjavascript.net/09_regexp.html#p_jjBKX9l81o)The first argument can also be a regular expression, in which case the first match of the regular expression is replaced. When a `g` option (for _global_) is added to the regular expression, _all_ matches in the string will be replaced, not just the first.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_ztGnSKyKy1)console.log("Borobudur".replace(/[ou]/, "a")); // → Barobudur console.log("Borobudur".replace(/[ou]/g, "a")); // → Barabadar

[](https://eloquentjavascript.net/09_regexp.html#p_BTzyExrWv3)It would have been sensible if the choice between replacing one match or all matches was made through an additional argument to `replace` or by providing a different method, `replaceAll`. But for some unfortunate reason, the choice relies on a property of the regular expression instead.

[](https://eloquentjavascript.net/09_regexp.html#p_/5YU/Qo2Np)The real power of using regular expressions with `replace` comes from the fact that we can refer to matched groups in the replacement string. For example, say we have a big string containing the names of people, one name per line, in the format `Lastname, Firstname`. If we want to swap these names and remove the comma to get a `Firstname Lastname` format, we can use the following code:
=======
The regular expression `/([01]+b|[\da-f]+h|\d+)/` matches either a binary number followed by a _b_, a hexadecimal number (that is, base 16, with the letters _a_ to _f_ standing for the digits 10 to 15) followed by an _h_, or a regular decimal number with no suffix character. This is the corresponding diagram:

![Visualization of /([01]+b|\d+|[\da-f]+h)/](https://eloquentjavascript.net/img/re_number.svg)

When matching this expression, it will often happen that the top (binary) branch is entered even though the input does not actually contain a binary number. When matching the string `"103"`, for example, it becomes clear only at the 3 that we are in the wrong branch. The string _does_ match the expression, just not the branch we are currently in.

So the matcher _backtracks_. When entering a branch, it remembers its current position (in this case, at the start of the string, just past the first boundary box in the diagram) so that it can go back and try another branch if the current one does not work out. For the string `"103"`, after encountering the 3 character, it will start trying the branch for hexadecimal numbers, which fails again because there is no _h_ after the number. So it tries the decimal number branch. This one fits, and a match is reported after all.

The matcher stops as soon as it finds a full match. This means that if multiple branches could potentially match a string, only the first one (ordered by where the branches appear in the regular expression) is used.

[]Backtracking also happens for repetition operators like + and `*`. If you match `/^.*x/` against `"abcxe"`, the `.*` part will first try to consume the whole string. The engine will then realize that it needs an _x_ to match the pattern. Since there is no _x_ past the end of the string, the star operator tries to match one character less. But the matcher doesn’t find an _x_ after `abcx` either, so it backtracks again, matching the star operator to just `abc`. _Now_ it finds an _x_ where it needs it and reports a successful match from positions 0 to 4.

It is possible to write regular expressions that will do a _lot_ of backtracking. This problem occurs when a pattern can match a piece of input in many different ways. For example, if we get confused while writing a binary-number regular expression, we might accidentally write something like `/([01]+)+b/`.

![Visualization of /([01]+)+b/](https://eloquentjavascript.net/img/re_slow.svg)

If that tries to match some long series of zeros and ones with no trailing _b_ character, the matcher first goes through the inner loop until it runs out of digits. Then it notices there is no _b_, so it backtracks one position, goes through the outer loop once, and gives up again, trying to backtrack out of the inner loop once more. It will continue to try every possible route through these two loops. This means the amount of work _doubles_ with each additional character. For even just a few dozen characters, the resulting match will take practically forever.

## [](https://eloquentjavascript.net/09_regexp.html#h_k0YuTOu54D)The replace method

[]String values have a `replace` method that can be used to replace part of the string with another string.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_dPdIdK/Wyi)console.log("papa".replace("p", "m")); // → mapa

The first argument can also be a regular expression, in which case the first match of the regular expression is replaced. When a `g` option (for _global_) is added to the regular expression, _all_ matches in the string will be replaced, not just the first.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_ztGnSKyKy1)console.log("Borobudur".replace(/[ou]/, "a")); // → Barobudur console.log("Borobudur".replace(/[ou]/g, "a")); // → Barabadar

It would have been sensible if the choice between replacing one match or all matches was made through an additional argument to `replace` or by providing a different method, `replaceAll`. But for some unfortunate reason, the choice relies on a property of the regular expression instead.

The real power of using regular expressions with `replace` comes from the fact that we can refer to matched groups in the replacement string. For example, say we have a big string containing the names of people, one name per line, in the format `Lastname, Firstname`. If we want to swap these names and remove the comma to get a `Firstname Lastname` format, we can use the following code:
>>>>>>> Stashed changes
    
    [](https://eloquentjavascript.net/09_regexp.html#c_5P5aZAbVLL)console.log( "Liskov, Barbara
    McCarthy, John
    Wadler, Philip" .replace(/(\w+), (\w+)/g, "$2 $1")); // → Barbara Liskov // John McCarthy // Philip Wadler

<<<<<<< Updated upstream
[](https://eloquentjavascript.net/09_regexp.html#p_sEudLRqyzC)The `$1` and `$2` in the replacement string refer to the parenthesized groups in the pattern. `$1` is replaced by the text that matched against the first group, `$2` by the second, and so on, up to `$9`. The whole match can be referred to with `$&`.

[](https://eloquentjavascript.net/09_regexp.html#p_BpgnqwKFHn)It is possible to pass a function—rather than a string—as the second argument to `replace`. For each replacement, the function will be called with the matched groups (as well as the whole match) as arguments, and its return value will be inserted into the new string.

[](https://eloquentjavascript.net/09_regexp.html#p_GbNoBizUD+)Here’s a small example:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_fwgl3+oeyX)let s = "the cia and fbi"; console.log(s.replace(/(fbi|cia)/g, str => str.toUpperCase())); // → the CIA and FBI

[](https://eloquentjavascript.net/09_regexp.html#p_EXxvdgdiP1)Here’s a more interesting one:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_Zo/y2Vv93l)let stock = "1 lemon, 2 cabbages, and 101 eggs"; function minusOne(match, amount, unit) { amount = Number(amount) - 1; if (amount == 1) { // only one left, remove the 's' unit = unit.slice(0, unit.length - 1); } else if (amount == 0) { amount = "no"; } return amount + " " + unit; } console.log(stock.replace(/(\d+) (\w+)/g, minusOne)); // → no lemon, 1 cabbage, and 100 eggs

[](https://eloquentjavascript.net/09_regexp.html#p_bv4e/DVilz)This takes a string, finds all occurrences of a number followed by an alphanumeric word, and returns a string wherein every such occurrence is decremented by one.

[](https://eloquentjavascript.net/09_regexp.html#p_H94SX/MJX8)The `(\d+)` group ends up as the `amount` argument to the function, and the `(\w+)` group gets bound to `unit`. The function converts `amount` to a number—which always works since it matched `\d+`—and makes some adjustments in case there is only one or zero left.

## [](https://eloquentjavascript.net/09_regexp.html#h_kiECehz+i+)Greed

[](https://eloquentjavascript.net/09_regexp.html#p_VccKwuX/1m)It is possible to use `replace` to write a function that removes all comments from a piece of JavaScript code. Here is a first attempt:
=======
The `$1` and `$2` in the replacement string refer to the parenthesized groups in the pattern. `$1` is replaced by the text that matched against the first group, `$2` by the second, and so on, up to `$9`. The whole match can be referred to with `$&`.

It is possible to pass a function—rather than a string—as the second argument to `replace`. For each replacement, the function will be called with the matched groups (as well as the whole match) as arguments, and its return value will be inserted into the new string.

Here’s a small example:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_fwgl3+oeyX)let s = "the cia and fbi"; console.log(s.replace(/(fbi|cia)/g, str => str.toUpperCase())); // → the CIA and FBI

Here’s a more interesting one:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_Zo/y2Vv93l)let stock = "1 lemon, 2 cabbages, and 101 eggs"; function minusOne(match, amount, unit) { amount = Number(amount) - 1; if (amount == 1) { // only one left, remove the 's' unit = unit.slice(0, unit.length - 1); } else if (amount == 0) { amount = "no"; } return amount + " " + unit; } console.log(stock.replace(/(\d+) (\w+)/g, minusOne)); // → no lemon, 1 cabbage, and 100 eggs

This takes a string, finds all occurrences of a number followed by an alphanumeric word, and returns a string wherein every such occurrence is decremented by one.

The `(\d+)` group ends up as the `amount` argument to the function, and the `(\w+)` group gets bound to `unit`. The function converts `amount` to a number—which always works since it matched `\d+`—and makes some adjustments in case there is only one or zero left.

## [](https://eloquentjavascript.net/09_regexp.html#h_kiECehz+i+)Greed

It is possible to use `replace` to write a function that removes all comments from a piece of JavaScript code. Here is a first attempt:
>>>>>>> Stashed changes
    
    [](https://eloquentjavascript.net/09_regexp.html#c_u0oKSJTOA2)function stripComments(code) { return code.replace(/\/\/.*|\/\*[^]*\*\//g, ""); } console.log(stripComments("1 + /Applications /Library /System /Users /Volumes /bin /cores /dev /etc /home /opt /private /sbin /tmp /usr /var 2 */3")); // → 1 + 3 console.log(stripComments("x = 10;// ten!")); // → x = 10; console.log(stripComments("1 /Applications /Library /System /Users /Volumes /bin /cores /dev /etc /home /opt /private /sbin /tmp /usr /var a */+/* b */ 1")); // → 1 1

[](https://eloquentjavascript.net/09_regexp.html#p_DkzBCJQQdu)The part before the _or_ operator matches two slash characters followed by any number of non-newline characters. The part for multiline comments is more involved. We use `[^]` (any character that is not in the empty set of characters) as a way to match any character. We cannot just use a period here because block comments can continue on a new line, and the period character does not match newline characters.

[](https://eloquentjavascript.net/09_regexp.html#p_s9E9JYjAYp)But the output for the last line appears to have gone wrong. Why?

[](https://eloquentjavascript.net/09_regexp.html#p_atS1ERkauC)The `[^]*` part of the expression, as I described in the section on backtracking, will first match as much as it can. If that causes the next part of the pattern to fail, the matcher moves back one character and tries again from there. In the example, the matcher first tries to match the whole rest of the string and then moves back from there. It will find an occurrence of `*/` after going back four characters and match that. This is not what we wanted—the intention was to match a single comment, not to go all the way to the end of the code and find the end of the last block comment.

[](https://eloquentjavascript.net/09_regexp.html#p_eNtLSVH65f)Because of this behavior, we say the repetition operators (`+`, `*`, `?`, and `{}`) are _greedy_, meaning they match as much as they can and backtrack from there. If you put a question mark after them (`+?`, `*?`, `??`, `{}?`), they become nongreedy and start by matching as little as possible, matching more only when the remaining pattern does not fit the smaller match.

[](https://eloquentjavascript.net/09_regexp.html#p_0L47KZXZKa)And that is exactly what we want in this case. By having the star match the smallest stretch of characters that brings us to a `*/`, we consume one block comment and nothing more.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_MCNF7GxfR1)function stripComments(code) { return code.replace(/\/\/.*|\/\*[^]*?\*\//g, ""); } console.log(stripComments("1 /Applications /Library /System /Users /Volumes /bin /cores /dev /etc /home /opt /private /sbin /tmp /usr /var a */+/* b */ 1")); // → 1 + 1

[](https://eloquentjavascript.net/09_regexp.html#p_o+3JCFC4Dr)A lot of bugs in regular expression programs can be traced to unintentionally using a greedy operator where a nongreedy one would work better. When using a repetition operator, consider the nongreedy variant first.

## [](https://eloquentjavascript.net/09_regexp.html#h_Rhu25fogrG)Dynamically creating RegExp objects

[](https://eloquentjavascript.net/09_regexp.html#p_34PsyHYX4x)There are cases where you might not know the exact pattern you need to match against when you are writing your code. Say you want to look for the user’s name in a piece of text and enclose it in underscore characters to make it stand out. Since you will know the name only once the program is actually running, you can’t use the slash-based notation.

[](https://eloquentjavascript.net/09_regexp.html#p_KAQggWa80Y)But you can build up a string and use the `RegExp` constructor on that. Here’s an example:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_3yQimfD35d)let name = "harry"; let text = "Harry is a suspicious character."; let regexp = new RegExp("\b(" + name + ")\b", "gi"); console.log(text.replace(regexp, "_$1_")); // → _Harry_ is a suspicious character.

[](https://eloquentjavascript.net/09_regexp.html#p_J6H1NBoQy/)When creating the `` boundary markers, we have to use two backslashes because we are writing them in a normal string, not a slash-enclosed regular expression. The second argument to the `RegExp` constructor contains the options for the regular expression—in this case, `"gi"` for global and case insensitive.

[](https://eloquentjavascript.net/09_regexp.html#p_UPAgEiKHfS)But what if the name is `"dea+hl[]rd"` because our user is a nerdy teenager? That would result in a nonsensical regular expression that won’t actually match the user’s name.

[](https://eloquentjavascript.net/09_regexp.html#p_Q+hqmMv8NT)To work around this, we can add backslashes before any character that has a special meaning.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_VVThPW6YGV)let name = "dea+hl[]rd"; let text = "This dea+hl[]rd guy is super annoying."; let escaped = name.replace(/[\[.+*?(){|^$]/g, "\$&"); let regexp = new RegExp("\b" + escaped + "\b", "gi"); console.log(text.replace(regexp, "_$&_")); // → This _dea+hl[]rd_ guy is super annoying.

## [](https://eloquentjavascript.net/09_regexp.html#h_Txg7z4j/ei)The search method

[](https://eloquentjavascript.net/09_regexp.html#p_3QlEdRm5L2)The `indexOf` method on strings cannot be called with a regular expression. But there is another method, `search`, that does expect a regular expression. Like `indexOf`, it returns the first index on which the expression was found, or -1 when it wasn’t found.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_diUfxE6ifs)console.log(" word".search(/\S/)); // → 2 console.log(" ".search(/\S/)); // → -1

[](https://eloquentjavascript.net/09_regexp.html#p_tqlyvUKoi5)Unfortunately, there is no way to indicate that the match should start at a given offset (like we can with the second argument to `indexOf`), which would often be useful.

## [](https://eloquentjavascript.net/09_regexp.html#h_duFTd2hqd0)The lastIndex property

[](https://eloquentjavascript.net/09_regexp.html#p_MvO8+re1D+)The `exec` method similarly does not provide a convenient way to start searching from a given position in the string. But it does provide an _in_convenient way.

[](https://eloquentjavascript.net/09_regexp.html#p_F+JgzwxLtK)Regular expression objects have properties. One such property is `source`, which contains the string that expression was created from. Another property is `lastIndex`, which controls, in some limited circumstances, where the next match will start.

[](https://eloquentjavascript.net/09_regexp.html#p_Ld5Vcdy0jB)Those circumstances are that the regular expression must have the global (`g`) or sticky (`y`) option enabled, and the match must happen through the `exec` method. Again, a less confusing solution would have been to just allow an extra argument to be passed to `exec`, but confusion is an essential feature of JavaScript’s regular expression interface.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_nXsHtqIJdF)let pattern = /y/g; pattern.lastIndex = 3; let match = pattern.exec("xyzzy"); console.log(match.index); // → 4 console.log(pattern.lastIndex); // → 5

[](https://eloquentjavascript.net/09_regexp.html#p_hjLQ+57mDd)If the match was successful, the call to `exec` automatically updates the `lastIndex` property to point after the match. If no match was found, `lastIndex` is set back to zero, which is also the value it has in a newly constructed regular expression object.

[](https://eloquentjavascript.net/09_regexp.html#p_dQPVkpMm7y)The difference between the global and the sticky options is that, when sticky is enabled, the match will succeed only if it starts directly at `lastIndex`, whereas with global, it will search ahead for a position where a match can start.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_98GwGRIMj8)let global = /abc/g; console.log(global.exec("xyz abc")); // → ["abc"] let sticky = /abc/y; console.log(sticky.exec("xyz abc")); // → null

[](https://eloquentjavascript.net/09_regexp.html#p_042bNmzNZK)When using a shared regular expression value for multiple `exec` calls, these automatic updates to the `lastIndex` property can cause problems. Your regular expression might be accidentally starting at an index that was left over from a previous call.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_wrx2wO0P8M)let digit = /\d/g; console.log(digit.exec("here it is: 1")); // → ["1"] console.log(digit.exec("and now: 1")); // → null

[](https://eloquentjavascript.net/09_regexp.html#p_9l7tQ3SsME)Another interesting effect of the global option is that it changes the way the `match` method on strings works. When called with a global expression, instead of returning an array similar to that returned by `exec`, `match` will find _all_ matches of the pattern in the string and return an array containing the matched strings.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_weT/d5+8vE)console.log("Banana".match(/an/g)); // → ["an", "an"]

[](https://eloquentjavascript.net/09_regexp.html#p_zFHO63a2iV)So be cautious with global regular expressions. The cases where they are necessary—calls to `replace` and places where you want to explicitly use `lastIndex`—are typically the only places where you want to use them.

### [](https://eloquentjavascript.net/09_regexp.html#i_m0fs21dHEg)Looping over matches

[](https://eloquentjavascript.net/09_regexp.html#p_Rhy/hnaaT+)A common thing to do is to scan through all occurrences of a pattern in a string, in a way that gives us access to the match object in the loop body. We can do this by using `lastIndex` and `exec`.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_rSzEnbVHja)let input = "A string with 3 numbers in it... 42 and 88."; let number = /\d+/g; let match; while (match = number.exec(input)) { console.log("Found", match[0], "at", match.index); } // → Found 3 at 14 // Found 42 at 33 // Found 88 at 40

[](https://eloquentjavascript.net/09_regexp.html#p_ZdCI2+edqA)This makes use of the fact that the value of an assignment expression (`=`) is the assigned value. So by using `match = number.exec(input)` as the condition in the `while` statement, we perform the match at the start of each iteration, save its result in a binding, and stop looping when no more matches are found.

## [](https://eloquentjavascript.net/09_regexp.html#h_RGsf6ah1EY)Parsing an INI file

[](https://eloquentjavascript.net/09_regexp.html#p_JbrLORqV9r)To conclude the chapter, we’ll look at a problem that calls for regular expressions. Imagine we are writing a program to automatically collect information about our enemies from the Internet. (We will not actually write that program here, just the part that reads the configuration file. Sorry.) The configuration file looks like this:
    
    [](https://eloquentjavascript.net/09_regexp.html#c_RV3f5fiptq)searchengine=https://duckduckgo.com/?q=$1 spitefulness=9.7 ; comments are preceded by a semicolon... ; each section concerns an individual enemy [larry] fullname=Larry Doe type=kindergarten bully website=http://www.geocities.com/CapeCanaveral/11451 [davaeorn] fullname=Davaeorn type=evil wizard outputdir=/home/marijn/enemies/davaeorn

[](https://eloquentjavascript.net/09_regexp.html#p_OgIQS1TJxB)The exact rules for this format (which is a widely used format, usually called an _INI_ file) are as follows:

  * [](https://eloquentjavascript.net/09_regexp.html#p_jIewfc/40B)Blank lines and lines starting with semicolons are ignored.

  * [](https://eloquentjavascript.net/09_regexp.html#p_O/dGCr+aR5)Lines wrapped in `[` and `]` start a new section.

  * [](https://eloquentjavascript.net/09_regexp.html#p_l2Yjl1fUVB)Lines containing an alphanumeric identifier followed by an `=` character add a setting to the current section.

  * [](https://eloquentjavascript.net/09_regexp.html#p_bCaQwCXJCi)Anything else is invalid.

[](https://eloquentjavascript.net/09_regexp.html#p_clbD+OAS4y)Our task is to convert a string like this into an object whose properties hold strings for settings written before the first section header and subobjects for sections, with those subobjects holding the section’s settings.

[](https://eloquentjavascript.net/09_regexp.html#p_8U3vMRn7g4)Since the format has to be processed line by line, splitting up the file into separate lines is a good start. We saw the `split` method in [Chapter 4](https://eloquentjavascript.net/04_data.html#split). Some operating systems, however, use not just a newline character to separate lines but a carriage return character followed by a newline (`" "`). Given that the `split` method also allows a regular expression as its argument, we can use a regular expression like `/ ? /` to split in a way that allows both `" "` and `" "` between lines.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_neI86/XXg2)function parseINI(string) { // Start with an object to hold the top-level fields let result = {}; let section = result; string.split(/
?
    /).forEach(line => { let match; if (match = line.match(/^(\w+)=(.*)$/)) { section[match[1]] = match[2]; } else if (match = line.match(/^\[(.*)\]$/)) { section = result[match[1]] = {}; } else if (!/^\s*(;.*)?$/.test(line)) { throw new Error("Line '" + line + "' is not valid."); } }); return result; } console.log(parseINI(` name=Vasilis [address] city=Tessaloniki`)); // → {name: "Vasilis", address: {city: "Tessaloniki"}}

[](https://eloquentjavascript.net/09_regexp.html#p_86q0K3iF4C)The code goes over the file’s lines and builds up an object. Properties at the top are stored directly into that object, whereas properties found in sections are stored in a separate section object. The `section` binding points at the object for the current section.

[](https://eloquentjavascript.net/09_regexp.html#p_ixTfvSC1VN)There are two kinds of significant lines—section headers or property lines. When a line is a regular property, it is stored in the current section. When it is a section header, a new section object is created, and `section` is set to point at it.

[](https://eloquentjavascript.net/09_regexp.html#p_FPzqsloIkT)Note the recurring use of `^` and `$` to make sure the expression matches the whole line, not just part of it. Leaving these out results in code that mostly works but behaves strangely for some input, which can be a difficult bug to track down.

[](https://eloquentjavascript.net/09_regexp.html#p_ACT8bIScp+)The pattern `if (match = string.match(...))` is similar to the trick of using an assignment as the condition for `while`. You often aren’t sure that your call to `match` will succeed, so you can access the resulting object only inside an `if` statement that tests for this. To not break the pleasant chain of `else if` forms, we assign the result of the match to a binding and immediately use that assignment as the test for the `if` statement.

[](https://eloquentjavascript.net/09_regexp.html#p_mwlBKfUu5D)If a line is not a section header or a property, the function checks whether it is a comment or an empty line using the expression `/^\s*(;.*)?$/`. Do you see how it works? The part between the parentheses will match comments, and the `?` makes sure it also matches lines containing only whitespace. When a line doesn’t match any of the expected forms, the function throws an exception.

## [](https://eloquentjavascript.net/09_regexp.html#h_+y54//b0l+)International characters

[](https://eloquentjavascript.net/09_regexp.html#p_2zJ37rLrbl)Because of JavaScript’s initial simplistic implementation and the fact that this simplistic approach was later set in stone as standard behavior, JavaScript’s regular expressions are rather dumb about characters that do not appear in the English language. For example, as far as JavaScript’s regular expressions are concerned, a “word character” is only one of the 26 characters in the Latin alphabet (uppercase or lowercase), decimal digits, and, for some reason, the underscore character. Things like _é_ or _β_, which most definitely are word characters, will not match `\w` (and _will_ match uppercase `\W`, the nonword category).

[](https://eloquentjavascript.net/09_regexp.html#p_H4r1oRJB6J)By a strange historical accident, `\s` (whitespace) does not have this problem and matches all characters that the Unicode standard considers whitespace, including things like the nonbreaking space and the Mongolian vowel separator.

[](https://eloquentjavascript.net/09_regexp.html#p_Ln5OarYp4l)Another problem is that, by default, regular expressions work on code units, as discussed in [Chapter 5](https://eloquentjavascript.net/05_higher_order.html#code_units), not actual characters. This means characters that are composed of two code units behave strangely.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_CfMTYxun8D)console.log(/🍎{3}/.test("🍎🍎🍎")); // → false console.log(/<.>/.test("<🌹>")); // → false console.log(/<.>/u.test("<🌹>")); // → true

[](https://eloquentjavascript.net/09_regexp.html#p_j4Kcv6J/rF)The problem is that the 🍎 in the first line is treated as two code units, and the `{3}` part is applied only to the second one. Similarly, the dot matches a single code unit, not the two that make up the rose emoji.

[](https://eloquentjavascript.net/09_regexp.html#p_1OZOJ3sk/b)You must add a `u` option (for Unicode) to your regular expression to make it treat such characters properly. The wrong behavior remains the default, unfortunately, because changing that might cause problems for existing code that depends on it.

[](https://eloquentjavascript.net/09_regexp.html#p_MmzTSqcyKg)Though this was only just standardized and is, at the time of writing, not widely supported yet, it is possible to use `\p` in a regular expression (that must have the Unicode option enabled) to match all characters to which the Unicode standard assigns a given property.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_+jV1oln0sr)console.log(/\p{Script=Greek}/u.test("α")); // → true console.log(/\p{Script=Arabic}/u.test("α")); // → false console.log(/\p{Alphabetic}/u.test("α")); // → true console.log(/\p{Alphabetic}/u.test("!")); // → false

[](https://eloquentjavascript.net/09_regexp.html#p_5NxQGhRrMq)Unicode defines a number of useful properties, though finding the one that you need may not always be trivial. You can use the `\p{Property=Value}` notation to match any character that has the given value for that property. If the property name is left off, as in `\p{Name}`, the name is assumed to be either a binary property such as `Alphabetic` or a category such as `Number`.

## [](https://eloquentjavascript.net/09_regexp.html#h_ErccPg/l98)Summary

[](https://eloquentjavascript.net/09_regexp.html#p_/hQX04GtpS)Regular expressions are objects that represent patterns in strings. They use their own language to express these patterns.

`/abc/`
A sequence of characters

`/[abc]/`
Any character from a set of characters

`/[^abc]/`
Any character _not_ in a set of characters

`/[0-9]/`
Any character in a range of characters

`/x+/`
One or more occurrences of the pattern `x`

`/x+?/`
One or more occurrences, nongreedy

`/x*/`
Zero or more occurrences

`/x?/`
Zero or one occurrence

`/x{2,4}/`
Two to four occurrences

`/(abc)/`
A group

`/a|b|c/`
Any one of several patterns

`/\d/`
Any digit character

`/\w/`
An alphanumeric character (“word character”)

`/\s/`
Any whitespace character

`/./`
Any character except newlines

`//`
A word boundary

`/^/`
Start of input

`/$/`
End of input

[](https://eloquentjavascript.net/09_regexp.html#p_AVY5pFcEyH)A regular expression has a method `test` to test whether a given string matches it. It also has a method `exec` that, when a match is found, returns an array containing all matched groups. Such an array has an `index` property that indicates where the match started.

[](https://eloquentjavascript.net/09_regexp.html#p_FoVJlvxp9q)Strings have a `match` method to match them against a regular expression and a `search` method to search for one, returning only the starting position of the match. Their `replace` method can replace matches of a pattern with a replacement string or function.

[](https://eloquentjavascript.net/09_regexp.html#p_APfM9C3A6j)Regular expressions can have options, which are written after the closing slash. The `i` option makes the match case insensitive. The `g` option makes the expression _global_, which, among other things, causes the `replace` method to replace all instances instead of just the first. The `y` option makes it sticky, which means that it will not search ahead and skip part of the string when looking for a match. The `u` option turns on Unicode mode, which fixes a number of problems around the handling of characters that take up two code units.

[](https://eloquentjavascript.net/09_regexp.html#p_mvLGdyUb97)Regular expressions are a sharp tool with an awkward handle. They simplify some tasks tremendously but can quickly become unmanageable when applied to complex problems. Part of knowing how to use them is resisting the urge to try to shoehorn things that they cannot cleanly express into them.

## [](https://eloquentjavascript.net/09_regexp.html#h_TcUD2vzyMe)Exercises

[](https://eloquentjavascript.net/09_regexp.html#p_meNfX2B/+s)It is almost unavoidable that, in the course of working on these exercises, you will get confused and frustrated by some regular expression’s inexplicable behavior. Sometimes it helps to enter your expression into an online tool like [_https://debuggex.com_](https://www.debuggex.com/) to see whether its visualization corresponds to what you intended and to experiment with the way it responds to various input strings.

### [](https://eloquentjavascript.net/09_regexp.html#i_vDM8PzwQWU)Regexp golf

[](https://eloquentjavascript.net/09_regexp.html#p_1t8xXpFN7O)_Code golf_ is a term used for the game of trying to express a particular program in as few characters as possible. Similarly, _regexp golf_ is the practice of writing as tiny a regular expression as possible to match a given pattern, and _only_ that pattern.

[](https://eloquentjavascript.net/09_regexp.html#p_VGCqgCur6C)For each of the following items, write a regular expression to test whether any of the given substrings occur in a string. The regular expression should match only strings containing one of the substrings described. Do not worry about word boundaries unless explicitly mentioned. When your expression works, see whether you can make it any smaller.

  1. [](https://eloquentjavascript.net/09_regexp.html#p_togdFO+/b9)_car_ and _cat_

  2. [](https://eloquentjavascript.net/09_regexp.html#p_2Q37Tsr9DS)_pop_ and _prop_

  3. [](https://eloquentjavascript.net/09_regexp.html#p_2Ah4dFikw1)_ferret_, _ferry_, and _ferrari_

  4. [](https://eloquentjavascript.net/09_regexp.html#p_ttiBCcePDl)Any word ending in _ious_

  5. [](https://eloquentjavascript.net/09_regexp.html#p_XnqTy5SopM)A whitespace character followed by a period, comma, colon, or semicolon

  6. [](https://eloquentjavascript.net/09_regexp.html#p_Ku7hE3qqDn)A word longer than six letters

  7. [](https://eloquentjavascript.net/09_regexp.html#p_mFDWQqRtWe)A word without the letter _e_ (or _E_)

[](https://eloquentjavascript.net/09_regexp.html#p_Tzjl1Axr+h)Refer to the table in the [chapter summary](https://eloquentjavascript.net/09_regexp.html#summary_regexp) for help. Test each solution with a few test strings.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_bnGKrYkiZ9)// Fill in the regular expressions verify(/.../, ["my car", "bad cats"], ["camper", "high art"]); verify(/.../, ["pop culture", "mad props"], ["plop", "prrrop"]); verify(/.../, ["ferret", "ferry", "ferrari"], ["ferrum", "transfer A"]); verify(/.../, ["how delicious", "spacious room"], ["ruinous", "consciousness"]); verify(/.../, ["bad punctuation ."], ["escape the period"]); verify(/.../, ["Siebentausenddreihundertzweiundzwanzig"], ["no", "three small words"]); verify(/.../, ["red platypus", "wobbling nest"], ["earth bed", "learning ape", "BEET"]); function verify(regexp, yes, no) { // Ignore unfinished exercises if (regexp.source == "...") return; for (let str of yes) if (!regexp.test(str)) { console.log(`Failure to match '${str}'`); } for (let str of no) if (regexp.test(str)) { console.log(`Unexpected match for '${str}'`); } }

### [](https://eloquentjavascript.net/09_regexp.html#i_dTiEW14oG0)Quoting style

[](https://eloquentjavascript.net/09_regexp.html#p_x7xoQ6mk60)Imagine you have written a story and used single quotation marks throughout to mark pieces of dialogue. Now you want to replace all the dialogue quotes with double quotes, while keeping the single quotes used in contractions like _aren’t_.

[](https://eloquentjavascript.net/09_regexp.html#p_k3Y0NF9w4b)Think of a pattern that distinguishes these two kinds of quote usage and craft a call to the `replace` method that does the proper replacement.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_sPrcOR+s/4)let text = "'I'm the cook,' he said, 'it's my job.'"; // Change this call. console.log(text.replace(/A/g, "B")); // → "I'm the cook," he said, "it's my job."

### [](https://eloquentjavascript.net/09_regexp.html#i_izldJoT3uv)Numbers again

[](https://eloquentjavascript.net/09_regexp.html#p_0OQXsuIIcQ)Write an expression that matches only JavaScript-style numbers. It must support an optional minus _or_ plus sign in front of the number, the decimal dot, and exponent notation—`5e-3` or `1E10`—again with an optional sign in front of the exponent. Also note that it is not necessary for there to be digits in front of or after the dot, but the number cannot be a dot alone. That is, `.5` and `5.` are valid JavaScript numbers, but a lone dot _isn’t_.
    
    [](https://eloquentjavascript.net/09_regexp.html#c_aHAzeMYYGe)// Fill in this regular expression. let number = /^...$/; // Tests: for (let str of ["1", "-1", "+15", "1.55", ".5", "5.", "1.3e2", "1E-4", "1e+12"]) { if (!number.test(str)) { console.log(`Failed to match '${str}'`); } } for (let str of ["1a", "+-1", "1.2.3", "1+1", "1e4.5", ".5.", "1f5", "."]) { if (number.test(str)) { console.log(`Incorrectly accepted '${str}'`); } }

[◀](https://eloquentjavascript.net/08_error.html) [◆](https://eloquentjavascript.net/index.html) [▶](https://eloquentjavascript.net/10_modules.html)
