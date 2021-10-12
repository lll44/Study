# Data Structures: Objects and Arrays

> [](https://eloquentjavascript.net/04_data.html#p_3DGxnMhaad)On two occasions I have been asked, ‘Pray, Mr. Babbage, if you put into the machine wrong figures, will the right answers come out?’ [...] I am not able rightly to apprehend the kind of confusion of ideas that could provoke such a question.
> 
> Charles Babbage, Passages from the Life of a Philosopher (1864)

![Picture of a weresquirrel](https://eloquentjavascript.net/img/chapter_picture_4.jpg)

[](https://eloquentjavascript.net/04_data.html#p_j/UjCN3npi)Numbers, Booleans, and strings are the atoms that data structures are built from. Many types of information require more than one atom, though. _Objects_ allow us to group values—including other objects—to build more complex structures.

[](https://eloquentjavascript.net/04_data.html#p_F4YgzUjHcT)The programs we have built so far have been limited by the fact that they were operating only on simple data types. This chapter will introduce basic data structures. By the end of it, you’ll know enough to start writing useful programs.

[](https://eloquentjavascript.net/04_data.html#p_vL8agXHSiL)The chapter will work through a more or less realistic programming example, introducing concepts as they apply to the problem at hand. The example code will often build on functions and bindings that were introduced earlier in the text.

## [](https://eloquentjavascript.net/04_data.html#h_NvjtahQLlw)The weresquirrel

[](https://eloquentjavascript.net/04_data.html#p_0aih0sjFrb)Every now and then, usually between 8 p.m. and 10 p.m., Jacques finds himself transforming into a small furry rodent with a bushy tail.

[](https://eloquentjavascript.net/04_data.html#p_EIDMzKWaqr)On one hand, Jacques is quite glad that he doesn’t have classic lycanthropy. Turning into a squirrel does cause fewer problems than turning into a wolf. Instead of having to worry about accidentally eating the neighbor (_that_ would be awkward), he worries about being eaten by the neighbor’s cat. After two occasions where he woke up on a precariously thin branch in the crown of an oak, naked and disoriented, he has taken to locking the doors and windows of his room at night and putting a few walnuts on the floor to keep himself busy.

[](https://eloquentjavascript.net/04_data.html#p_ciZTylV1yl)That takes care of the cat and tree problems. But Jacques would prefer to get rid of his condition entirely. The irregular occurrences of the transformation make him suspect that they might be triggered by something. For a while, he believed that it happened only on days when he had been near oak trees. But avoiding oak trees did not stop the problem.

[](https://eloquentjavascript.net/04_data.html#p_Xj6eprhXkS)Switching to a more scientific approach, Jacques has started keeping a daily log of everything he does on a given day and whether he changed form. With this data he hopes to narrow down the conditions that trigger the transformations.

[](https://eloquentjavascript.net/04_data.html#p_mcDf0Dxvcm)The first thing he needs is a data structure to store this information.

## [](https://eloquentjavascript.net/04_data.html#h_HjL/otjEJn)Data sets

[](https://eloquentjavascript.net/04_data.html#p_HFLfyQFSDp)To work with a chunk of digital data, we’ll first have to find a way to represent it in our machine’s memory. Say, for example, that we want to represent a collection of the numbers 2, 3, 5, 7, and 11.

[](https://eloquentjavascript.net/04_data.html#p_cnzv4pg+Wz)We could get creative with strings—after all, strings can have any length, so we can put a lot of data into them—and use `"2 3 5 7 11"` as our representation. But this is awkward. You’d have to somehow extract the digits and convert them back to numbers to access them.

[](https://eloquentjavascript.net/04_data.html#p_/aFILq7bDn)Fortunately, JavaScript provides a data type specifically for storing sequences of values. It is called an _array_ and is written as a list of values between square brackets, separated by commas.
    
    edit & run code by clicking it
    
    [](https://eloquentjavascript.net/04_data.html#c_05cIH1hy/D)let listOfNumbers = [2, 3, 5, 7, 11]; console.log(listOfNumbers[2]); // → 5 console.log(listOfNumbers[0]); // → 2 console.log(listOfNumbers[2 - 1]); // → 3

[](https://eloquentjavascript.net/04_data.html#p_xu5bhsrvS2)The notation for getting at the elements inside an array also uses square brackets. A pair of square brackets immediately after an expression, with another expression inside of them, will look up the element in the left-hand expression that corresponds to the _index_ given by the expression in the brackets.

[](https://eloquentjavascript.net/04_data.html#p_1+NmIJreij)The first index of an array is zero, not one. So the first element is retrieved with `listOfNumbers[0]`. Zero-based counting has a long tradition in technology and in certain ways makes a lot of sense, but it takes some getting used to. Think of the index as the amount of items to skip, counting from the start of the array.

## [](https://eloquentjavascript.net/04_data.html#h_vGyI2y8HA6)Properties

[](https://eloquentjavascript.net/04_data.html#p_GC4++VF2pM)We’ve seen a few suspicious-looking expressions like `myString.length` (to get the length of a string) and `Math.max` (the maximum function) in past chapters. These are expressions that access a _property_ of some value. In the first case, we access the `length` property of the value in `myString`. In the second, we access the property named `max` in the `Math` object (which is a collection of mathematics-related constants and functions).

[](https://eloquentjavascript.net/04_data.html#p_dTOk+Nu/lR)Almost all JavaScript values have properties. The exceptions are `null` and `undefined`. If you try to access a property on one of these nonvalues, you get an error.
    
    [](https://eloquentjavascript.net/04_data.html#c_FNR95AymUx)null.length; // → TypeError: null has no properties

[](https://eloquentjavascript.net/04_data.html#p_wm1lZqKJ49)The two main ways to access properties in JavaScript are with a dot and with square brackets. Both `value.x` and `value[x]` access a property on `value`—but not necessarily the same property. The difference is in how `x` is interpreted. When using a dot, the word after the dot is the literal name of the property. When using square brackets, the expression between the brackets is _evaluated_ to get the property name. Whereas `value.x` fetches the property of `value` named “x”, `value[x]` tries to evaluate the expression `x` and uses the result, converted to a string, as the property name.

[](https://eloquentjavascript.net/04_data.html#p_PeocsmCJ3P)So if you know that the property you are interested in is called _color_, you say `value.color`. If you want to extract the property named by the value held in the binding `i`, you say `value[i]`. Property names are strings. They can be any string, but the dot notation works only with names that look like valid binding names. So if you want to access a property named _2_ or _John Doe_, you must use square brackets: `value[2]` or `value["John Doe"]`.

[](https://eloquentjavascript.net/04_data.html#p_v2+DwDjnmO)The elements in an array are stored as the array’s properties, using numbers as property names. Because you can’t use the dot notation with numbers and usually want to use a binding that holds the index anyway, you have to use the bracket notation to get at them.

[](https://eloquentjavascript.net/04_data.html#p_Bcq+Q3kiI4)The `length` property of an array tells us how many elements it has. This property name is a valid binding name, and we know its name in advance, so to find the length of an array, you typically write `array.length` because that’s easier to write than `array["length"]`.

## [](https://eloquentjavascript.net/04_data.html#h_fkrGgDyRWc)Methods

[](https://eloquentjavascript.net/04_data.html#p_t1dHhJEzat)Both string and array values contain, in addition to the `length` property, a number of properties that hold function values.
    
    [](https://eloquentjavascript.net/04_data.html#c_prRDc5amqh)let doh = "Doh"; console.log(typeof doh.toUpperCase); // → function console.log(doh.toUpperCase()); // → DOH

[](https://eloquentjavascript.net/04_data.html#p_TWVl3O+8/l)Every string has a `toUpperCase` property. When called, it will return a copy of the string in which all letters have been converted to uppercase. There is also `toLowerCase`, going the other way.

[](https://eloquentjavascript.net/04_data.html#p_ZYWrM09QFe)Interestingly, even though the call to `toUpperCase` does not pass any arguments, the function somehow has access to the string `"Doh"`, the value whose property we called. How this works is described in [Chapter 6](https://eloquentjavascript.net/06_object.html#obj_methods).

[](https://eloquentjavascript.net/04_data.html#p_96KudJIN5i)Properties that contain functions are generally called _methods_ of the value they belong to, as in “`toUpperCase` is a method of a string”.

[](https://eloquentjavascript.net/04_data.html#p_aAS6mUhzmc)This example demonstrates two methods you can use to manipulate arrays:
    
    [](https://eloquentjavascript.net/04_data.html#c_RiFZUNk6gr)let sequence = [1, 2, 3]; sequence.push(4); sequence.push(5); console.log(sequence); // → [1, 2, 3, 4, 5] console.log(sequence.pop()); // → 5 console.log(sequence); // → [1, 2, 3, 4]

[](https://eloquentjavascript.net/04_data.html#p_6iATZ6SSgb)The `push` method adds values to the end of an array, and the `pop` method does the opposite, removing the last value in the array and returning it.

[](https://eloquentjavascript.net/04_data.html#p_0p3gvnUXoK)These somewhat silly names are the traditional terms for operations on a _stack_. A stack, in programming, is a data structure that allows you to push values into it and pop them out again in the opposite order so that the thing that was added last is removed first. These are common in programming—you might remember the function call stack from [the previous chapter](https://eloquentjavascript.net/03_functions.html#stack), which is an instance of the same idea.

## [](https://eloquentjavascript.net/04_data.html#h_cqg63Sxe3o)Objects

[](https://eloquentjavascript.net/04_data.html#p_D8cm1kz0P8)Back to the weresquirrel. A set of daily log entries can be represented as an array. But the entries do not consist of just a number or a string—each entry needs to store a list of activities and a Boolean value that indicates whether Jacques turned into a squirrel or not. Ideally, we would like to group these together into a single value and then put those grouped values into an array of log entries.

[](https://eloquentjavascript.net/04_data.html#p_amO+YCpNIz)Values of the type _object_ are arbitrary collections of properties. One way to create an object is by using braces as an expression.
    
    [](https://eloquentjavascript.net/04_data.html#c_Y37a9WsXpl)let day1 = { squirrel: false, events: ["work", "touched tree", "pizza", "running"] }; console.log(day1.squirrel); // → false console.log(day1.wolf); // → undefined day1.wolf = false; console.log(day1.wolf); // → false

[](https://eloquentjavascript.net/04_data.html#p_hPPBEWYY/i)Inside the braces, there is a list of properties separated by commas. Each property has a name followed by a colon and a value. When an object is written over multiple lines, indenting it like in the example helps with readability. Properties whose names aren’t valid binding names or valid numbers have to be quoted.
    
    [](https://eloquentjavascript.net/04_data.html#c_n8ErtKNPW/)let descriptions = { work: "Went to work", "touched tree": "Touched a tree" };

[](https://eloquentjavascript.net/04_data.html#p_nZ3mgfn27O)This means that braces have _two_ meanings in JavaScript. At the start of a statement, they start a block of statements. In any other position, they describe an object. Fortunately, it is rarely useful to start a statement with an object in braces, so the ambiguity between these two is not much of a problem.

[](https://eloquentjavascript.net/04_data.html#p_lBjH6GtvXt)Reading a property that doesn’t exist will give you the value `undefined`.

[](https://eloquentjavascript.net/04_data.html#p_m1hLPDyHXE)It is possible to assign a value to a property expression with the `=` operator. This will replace the property’s value if it already existed or create a new property on the object if it didn’t.

[](https://eloquentjavascript.net/04_data.html#p_2b9eQWe4l/)To briefly return to our tentacle model of bindings—property bindings are similar. They _grasp_ values, but other bindings and properties might be holding onto those same values. You may think of objects as octopuses with any number of tentacles, each of which has a name tattooed on it.

[](https://eloquentjavascript.net/04_data.html#p_nQBjCOh9nC)The `delete` operator cuts off a tentacle from such an octopus. It is a unary operator that, when applied to an object property, will remove the named property from the object. This is not a common thing to do, but it is possible.
    
    [](https://eloquentjavascript.net/04_data.html#c_66M3B1wG98)let anObject = {left: 1, right: 2}; console.log(anObject.left); // → 1 delete anObject.left; console.log(anObject.left); // → undefined console.log("left" in anObject); // → false console.log("right" in anObject); // → true

[](https://eloquentjavascript.net/04_data.html#p_vVEymXRSvR)The binary `in` operator, when applied to a string and an object, tells you whether that object has a property with that name. The difference between setting a property to `undefined` and actually deleting it is that, in the first case, the object still _has_ the property (it just doesn’t have a very interesting value), whereas in the second case the property is no longer present and `in` will return `false`.

[](https://eloquentjavascript.net/04_data.html#p_SvMW6lxfp+)To find out what properties an object has, you can use the `Object.keys` function. You give it an object, and it returns an array of strings—the object’s property names.
    
    [](https://eloquentjavascript.net/04_data.html#c_0oaalmpqn6)console.log(Object.keys({x: 0, y: 0, z: 2})); // → ["x", "y", "z"]

[](https://eloquentjavascript.net/04_data.html#p_z4/OPZzTTK)There’s an `Object.assign` function that copies all properties from one object into another.
    
    [](https://eloquentjavascript.net/04_data.html#c_ngXKayzwiT)let objectA = {a: 1, b: 2}; Object.assign(objectA, {b: 3, c: 4}); console.log(objectA); // → {a: 1, b: 3, c: 4}

[](https://eloquentjavascript.net/04_data.html#p_Rl8msr9DUz)Arrays, then, are just a kind of object specialized for storing sequences of things. If you evaluate `typeof []`, it produces `"object"`. You can see them as long, flat octopuses with all their tentacles in a neat row, labeled with numbers.

[](https://eloquentjavascript.net/04_data.html#p_d1H6/6O79A)We will represent the journal that Jacques keeps as an array of objects.
    
    [](https://eloquentjavascript.net/04_data.html#c_H7Np/tieSQ)let journal = [ {events: ["work", "touched tree", "pizza", "running", "television"], squirrel: false}, {events: ["work", "ice cream", "cauliflower", "lasagna", "touched tree", "brushed teeth"], squirrel: false}, {events: ["weekend", "cycling", "break", "peanuts", "beer"], squirrel: true}, /* and so on... */ ];

## [](https://eloquentjavascript.net/04_data.html#h_C3n45IkMhg)Mutability

[](https://eloquentjavascript.net/04_data.html#p_HZ50qDRWmj)We will get to actual programming _real_ soon now. First there’s one more piece of theory to understand.

[](https://eloquentjavascript.net/04_data.html#p_ZAtU8veKBN)We saw that object values can be modified. The types of values discussed in earlier chapters, such as numbers, strings, and Booleans, are all _immutable_—it is impossible to change values of those types. You can combine them and derive new values from them, but when you take a specific string value, that value will always remain the same. The text inside it cannot be changed. If you have a string that contains `"cat"`, it is not possible for other code to change a character in your string to make it spell `"rat"`.

[](https://eloquentjavascript.net/04_data.html#p_0geJong3Bv)Objects work differently. You _can_ change their properties, causing a single object value to have different content at different times.

[](https://eloquentjavascript.net/04_data.html#p_fVZ1xXAqW5)When we have two numbers, 120 and 120, we can consider them precisely the same number, whether or not they refer to the same physical bits. With objects, there is a difference between having two references to the same object and having two different objects that contain the same properties. Consider the following code:
    
    [](https://eloquentjavascript.net/04_data.html#c_I1Dv6D46/p)let object1 = {value: 10}; let object2 = object1; let object3 = {value: 10}; console.log(object1 == object2); // → true console.log(object1 == object3); // → false object1.value = 15; console.log(object2.value); // → 15 console.log(object3.value); // → 10

[](https://eloquentjavascript.net/04_data.html#p_LKrvBk0ldY)The `object1` and `object2` bindings grasp the _same_ object, which is why changing `object1` also changes the value of `object2`. They are said to have the same _identity_. The binding `object3` points to a different object, which initially contains the same properties as `object1` but lives a separate life.

[](https://eloquentjavascript.net/04_data.html#p_eic4GJbroA)Bindings can also be changeable or constant, but this is separate from the way their values behave. Even though number values don’t change, you can use a `let` binding to keep track of a changing number by changing the value the binding points at. Similarly, though a `const` binding to an object can itself not be changed and will continue to point at the same object, the _contents_ of that object might change.
    
    [](https://eloquentjavascript.net/04_data.html#c_eOXMRndYxO)const score = {visitors: 0, home: 0}; // This is okay score.visitors = 1; // This isn't allowed score = {visitors: 1, home: 1};

[](https://eloquentjavascript.net/04_data.html#p_wD7jhXt+Tr)When you compare objects with JavaScript’s `==` operator, it compares by identity: it will produce `true` only if both objects are precisely the same value. Comparing different objects will return `false`, even if they have identical properties. There is no “deep” comparison operation built into JavaScript, which compares objects by contents, but it is possible to write it yourself (which is one of the [exercises](https://eloquentjavascript.net/04_data.html#exercise_deep_compare) at the end of this chapter).

## [](https://eloquentjavascript.net/04_data.html#h_qHGOoBxOeE)The lycanthrope’s log

[](https://eloquentjavascript.net/04_data.html#p_z1vPsL0dwv)So, Jacques starts up his JavaScript interpreter and sets up the environment he needs to keep his journal.
    
    [](https://eloquentjavascript.net/04_data.html#c_CI+dtzXW/x)let journal = []; function addEntry(events, squirrel) { journal.push({events, squirrel}); }

[](https://eloquentjavascript.net/04_data.html#p_ljMiZolRIM)Note that the object added to the journal looks a little odd. Instead of declaring properties like `events: events`, it just gives a property name. This is shorthand that means the same thing—if a property name in brace notation isn’t followed by a value, its value is taken from the binding with the same name.

[](https://eloquentjavascript.net/04_data.html#p_cm0psWaVgC)So then, every evening at 10 p.m.—or sometimes the next morning, after climbing down from the top shelf of his bookcase—Jacques records the day.
    
    [](https://eloquentjavascript.net/04_data.html#c_S+F+R2oIfR)addEntry(["work", "touched tree", "pizza", "running", "television"], false); addEntry(["work", "ice cream", "cauliflower", "lasagna", "touched tree", "brushed teeth"], false); addEntry(["weekend", "cycling", "break", "peanuts", "beer"], true);

[](https://eloquentjavascript.net/04_data.html#p_7VcOxe4CEu)Once he has enough data points, he intends to use statistics to find out which of these events may be related to the squirrelifications.

[](https://eloquentjavascript.net/04_data.html#p_EedDVNQ30H)_Correlation_ is a measure of dependence between statistical variables. A statistical variable is not quite the same as a programming variable. In statistics you typically have a set of _measurements_, and each variable is measured for every measurement. Correlation between variables is usually expressed as a value that ranges from -1 to 1. Zero correlation means the variables are not related. A correlation of one indicates that the two are perfectly related—if you know one, you also know the other. Negative one also means that the variables are perfectly related but that they are opposites—when one is true, the other is false.

[](https://eloquentjavascript.net/04_data.html#p_mq//xARuKm)To compute the measure of correlation between two Boolean variables, we can use the _phi coefficient_ (_ϕ_). This is a formula whose input is a frequency table containing the number of times the different combinations of the variables were observed. The output of the formula is a number between -1 and 1 that describes the correlation.

[](https://eloquentjavascript.net/04_data.html#p_enPDgop6ZQ)We could take the event of eating pizza and put that in a frequency table like this, where each number indicates the amount of times that combination occurred in our measurements:

![Eating pizza versus turning into a squirrel](https://eloquentjavascript.net/img/pizza-squirrel.svg)

[](https://eloquentjavascript.net/04_data.html#p_34XzN30BBH)If we call that table _n_, we can compute _ϕ_ using the following formula:

_ϕ_ =

_n_11_n_00 − _n_10_n_01

√ _n_1•_n_0•_n_•1_n_•0

[](https://eloquentjavascript.net/04_data.html#p_BlqmmOB0tg)(If at this point you’re putting the book down to focus on a terrible flashback to 10th grade math class—hold on! I do not intend to torture you with endless pages of cryptic notation—it’s just this one formula for now. And even with this one, all we do is turn it into JavaScript.)

[](https://eloquentjavascript.net/04_data.html#p_6U87ck4G90)The notation _n_01 indicates the number of measurements where the first variable (squirrelness) is false (0) and the second variable (pizza) is true (1). In the pizza table, _n_01 is 9.

[](https://eloquentjavascript.net/04_data.html#p_pweIXp0GRF)The value _n_1• refers to the sum of all measurements where the first variable is true, which is 5 in the example table. Likewise, _n_•0 refers to the sum of the measurements where the second variable is false.

[](https://eloquentjavascript.net/04_data.html#p_ACMn7uvFzz)So for the pizza table, the part above the division line (the dividend) would be 1×76−4×9 = 40, and the part below it (the divisor) would be the square root of 5×85×10×80, or √340000. This comes out to _ϕ_ ≈ 0.069, which is tiny. Eating pizza does not appear to have influence on the transformations.

## [](https://eloquentjavascript.net/04_data.html#h_YwedOm6SqZ)Computing correlation

[](https://eloquentjavascript.net/04_data.html#p_jn2nhCXEpR)We can represent a two-by-two table in JavaScript with a four-element array (`[76, 9, 4, 1]`). We could also use other representations, such as an array containing two two-element arrays (`[[76, 9], [4, 1]]`) or an object with property names like `"11"` and `"01"`, but the flat array is simple and makes the expressions that access the table pleasantly short. We’ll interpret the indices to the array as two-bit binary numbers, where the leftmost (most significant) digit refers to the squirrel variable and the rightmost (least significant) digit refers to the event variable. For example, the binary number `10` refers to the case where Jacques did turn into a squirrel, but the event (say, “pizza”) didn’t occur. This happened four times. And since binary `10` is 2 in decimal notation, we will store this number at index 2 of the array.

[](https://eloquentjavascript.net/04_data.html#p_h+u9TgFTTH)This is the function that computes the _ϕ_ coefficient from such an array:
    
    [](https://eloquentjavascript.net/04_data.html#c_AnoNjFldkv)function phi(table) { return (table[3] * table[0] - table[2] * table[1]) / Math.sqrt((table[2] + table[3]) * (table[0] + table[1]) * (table[1] + table[3]) * (table[0] + table[2])); } console.log(phi([76, 9, 4, 1])); // → 0.068599434

[](https://eloquentjavascript.net/04_data.html#p_DPLO2QZk5F)This is a direct translation of the _ϕ_ formula into JavaScript. `Math.sqrt` is the square root function, as provided by the `Math` object in a standard JavaScript environment. We have to add two fields from the table to get fields like n1• because the sums of rows or columns are not stored directly in our data structure.

[](https://eloquentjavascript.net/04_data.html#p_GhEP5hEDnb)Jacques kept his journal for three months. The resulting data set is available in the [coding sandbox](https://eloquentjavascript.net/code#4) for this chapter, where it is stored in the `JOURNAL` binding and in a downloadable [file](https://eloquentjavascript.net/code/journal.js).

[](https://eloquentjavascript.net/04_data.html#p_sM+4QT8FKs)To extract a two-by-two table for a specific event from the journal, we must loop over all the entries and tally how many times the event occurs in relation to squirrel transformations.
    
    [](https://eloquentjavascript.net/04_data.html#c_rfea+FwMb5)function tableFor(event, journal) { let table = [0, 0, 0, 0]; for (let i = 0; i < journal.length; i++) { let entry = journal[i], index = 0; if (entry.events.includes(event)) index += 1; if (entry.squirrel) index += 2; table[index] += 1; } return table; } console.log(tableFor("pizza", JOURNAL)); // → [76, 9, 4, 1]

[](https://eloquentjavascript.net/04_data.html#p_1/7IsMpwdF)Arrays have an `includes` method that checks whether a given value exists in the array. The function uses that to determine whether the event name it is interested in is part of the event list for a given day.

[](https://eloquentjavascript.net/04_data.html#p_2jmDtun7lQ)The body of the loop in `tableFor` figures out which box in the table each journal entry falls into by checking whether the entry contains the specific event it’s interested in and whether the event happens alongside a squirrel incident. The loop then adds one to the correct box in the table.

[](https://eloquentjavascript.net/04_data.html#p_f0iI+VuF1R)We now have the tools we need to compute individual correlations. The only step remaining is to find a correlation for every type of event that was recorded and see whether anything stands out.

## [](https://eloquentjavascript.net/04_data.html#h_4WwZLib71C)Array loops

[](https://eloquentjavascript.net/04_data.html#p_NcUX4h3Azc)In the `tableFor` function, there’s a loop like this:
    
    [](https://eloquentjavascript.net/04_data.html#c_pE7VRrRQir)for (let i = 0; i < JOURNAL.length; i++) { let entry = JOURNAL[i]; // Do something with entry }

[](https://eloquentjavascript.net/04_data.html#p_bofXG4HkzH)This kind of loop is common in classical JavaScript—going over arrays one element at a time is something that comes up a lot, and to do that you’d run a counter over the length of the array and pick out each element in turn.

[](https://eloquentjavascript.net/04_data.html#p_Xl/M0+NR/e)There is a simpler way to write such loops in modern JavaScript.
    
    [](https://eloquentjavascript.net/04_data.html#c_OXsCQPvDE1)for (let entry of JOURNAL) { console.log(`${entry.events.length} events.`); }

[](https://eloquentjavascript.net/04_data.html#p_LDkHv2luaA)When a `for` loop looks like this, with the word `of` after a variable definition, it will loop over the elements of the value given after `of`. This works not only for arrays but also for strings and some other data structures. We’ll discuss _how_ it works in [Chapter 6](https://eloquentjavascript.net/06_object.html).

## [](https://eloquentjavascript.net/04_data.html#h_Lg5n7mjqw/)The final analysis

[](https://eloquentjavascript.net/04_data.html#p_LI+01yIQON)We need to compute a correlation for every type of event that occurs in the data set. To do that, we first need to _find_ every type of event.
    
    [](https://eloquentjavascript.net/04_data.html#c_P6cqJZBL1M)function journalEvents(journal) { let events = []; for (let entry of journal) { for (let event of entry.events) { if (!events.includes(event)) { events.push(event); } } } return events; } console.log(journalEvents(JOURNAL)); // → ["carrot", "exercise", "weekend", "bread", …]

[](https://eloquentjavascript.net/04_data.html#p_vBsW+TJrFo)By going over all the events and adding those that aren’t already in there to the `events` array, the function collects every type of event.

[](https://eloquentjavascript.net/04_data.html#p_HohHy+JZoP)Using that, we can see all the correlations.
    
    [](https://eloquentjavascript.net/04_data.html#c_7ws9oWaneM)for (let event of journalEvents(JOURNAL)) { console.log(event + ":", phi(tableFor(event, JOURNAL))); } // → carrot: 0.0140970969 // → exercise: 0.0685994341 // → weekend: 0.1371988681 // → bread: -0.0757554019 // → pudding: -0.0648203724 // and so on...

[](https://eloquentjavascript.net/04_data.html#p_TiI6dIjE18)Most correlations seem to lie close to zero. Eating carrots, bread, or pudding apparently does not trigger squirrel-lycanthropy. It _does_ seem to occur somewhat more often on weekends. Let’s filter the results to show only correlations greater than 0.1 or less than -0.1.
    
    [](https://eloquentjavascript.net/04_data.html#c_hBXzmb7hPU)for (let event of journalEvents(JOURNAL)) { let correlation = phi(tableFor(event, JOURNAL)); if (correlation > 0.1 || correlation < -0.1) { console.log(event + ":", correlation); } } // → weekend: 0.1371988681 // → brushed teeth: -0.3805211953 // → candy: 0.1296407447 // → work: -0.1371988681 // → spaghetti: 0.2425356250 // → reading: 0.1106828054 // → peanuts: 0.5902679812

[](https://eloquentjavascript.net/04_data.html#p_SmM3fqump2)Aha! There are two factors with a correlation that’s clearly stronger than the others. Eating peanuts has a strong positive effect on the chance of turning into a squirrel, whereas brushing his teeth has a significant negative effect.

[](https://eloquentjavascript.net/04_data.html#p_CGdrhu89cM)Interesting. Let’s try something.
    
    [](https://eloquentjavascript.net/04_data.html#c_x7WUJStSIp)for (let entry of JOURNAL) { if (entry.events.includes("peanuts") && !entry.events.includes("brushed teeth")) { entry.events.push("peanut teeth"); } } console.log(phi(tableFor("peanut teeth", JOURNAL))); // → 1

[](https://eloquentjavascript.net/04_data.html#p_Ji3VLlNJjI)That’s a strong result. The phenomenon occurs precisely when Jacques eats peanuts and fails to brush his teeth. If only he weren’t such a slob about dental hygiene, he’d have never even noticed his affliction.

[](https://eloquentjavascript.net/04_data.html#p_CLBAQ41EVq)Knowing this, Jacques stops eating peanuts altogether and finds that his transformations don’t come back.

[](https://eloquentjavascript.net/04_data.html#p_IMX7LE4P7A)For a few years, things go great for Jacques. But at some point he loses his job. Because he lives in a nasty country where having no job means having no medical services, he is forced to take employment with a circus where he performs as _The Incredible Squirrelman_, stuffing his mouth with peanut butter before every show.

[](https://eloquentjavascript.net/04_data.html#p_SK7dEwTJMB)One day, fed up with this pitiful existence, Jacques fails to change back into his human form, hops through a crack in the circus tent, and vanishes into the forest. He is never seen again.

## [](https://eloquentjavascript.net/04_data.html#h_GFaxee4PuU)Further arrayology

[](https://eloquentjavascript.net/04_data.html#p_Wik6gRMuIP)Before finishing the chapter, I want to introduce you to a few more object-related concepts. I’ll start by introducing some generally useful array methods.

[](https://eloquentjavascript.net/04_data.html#p_Px7nduaW01)We saw `push` and `pop`, which add and remove elements at the end of an array, [earlier](https://eloquentjavascript.net/04_data.html#array_methods) in this chapter. The corresponding methods for adding and removing things at the start of an array are called `unshift` and `shift`.
    
    [](https://eloquentjavascript.net/04_data.html#c_Vq1IBpy+hP)let todoList = []; function remember(task) { todoList.push(task); } function getTask() { return todoList.shift(); } function rememberUrgently(task) { todoList.unshift(task); }

[](https://eloquentjavascript.net/04_data.html#p_Z35J/zKDAQ)That program manages a queue of tasks. You add tasks to the end of the queue by calling `remember("groceries")`, and when you’re ready to do something, you call `getTask()` to get (and remove) the front item from the queue. The `rememberUrgently` function also adds a task but adds it to the front instead of the back of the queue.

[](https://eloquentjavascript.net/04_data.html#p_7VffwcInkI)To search for a specific value, arrays provide an `indexOf` method. The method searches through the array from the start to the end and returns the index at which the requested value was found—or -1 if it wasn’t found. To search from the end instead of the start, there’s a similar method called `lastIndexOf`.
    
    [](https://eloquentjavascript.net/04_data.html#c_N+G0EtTfto)console.log([1, 2, 3, 2, 1].indexOf(2)); // → 1 console.log([1, 2, 3, 2, 1].lastIndexOf(2)); // → 3

[](https://eloquentjavascript.net/04_data.html#p_zErdHcwkcD)Both `indexOf` and `lastIndexOf` take an optional second argument that indicates where to start searching.

[](https://eloquentjavascript.net/04_data.html#p_xl0kBHXnu2)Another fundamental array method is `slice`, which takes start and end indices and returns an array that has only the elements between them. The start index is inclusive, the end index exclusive.
    
    [](https://eloquentjavascript.net/04_data.html#c_zCBzPnMpIk)console.log([0, 1, 2, 3, 4].slice(2, 4)); // → [2, 3] console.log([0, 1, 2, 3, 4].slice(2)); // → [2, 3, 4]

[](https://eloquentjavascript.net/04_data.html#p_Y6nY8puZtN)When the end index is not given, `slice` will take all of the elements after the start index. You can also omit the start index to copy the entire array.

[](https://eloquentjavascript.net/04_data.html#p_QNFIcCtVLd)The `concat` method can be used to glue arrays together to create a new array, similar to what the `+` operator does for strings.

[](https://eloquentjavascript.net/04_data.html#p_x8OwNmbLzo)The following example shows both `concat` and `slice` in action. It takes an array and an index, and it returns a new array that is a copy of the original array with the element at the given index removed.
    
    [](https://eloquentjavascript.net/04_data.html#c_q+NBMNgFFy)function remove(array, index) { return array.slice(0, index) .concat(array.slice(index + 1)); } console.log(remove(["a", "b", "c", "d", "e"], 2)); // → ["a", "b", "d", "e"]

[](https://eloquentjavascript.net/04_data.html#p_RxH5uQN5Uq)If you pass `concat` an argument that is not an array, that value will be added to the new array as if it were a one-element array.

## [](https://eloquentjavascript.net/04_data.html#h_mT4YQfwHp6)Strings and their properties

[](https://eloquentjavascript.net/04_data.html#p_sp+O+Km+2n)We can read properties like `length` and `toUpperCase` from string values. But if you try to add a new property, it doesn’t stick.
    
    [](https://eloquentjavascript.net/04_data.html#c_xvzL9wErq7)let kim = "Kim"; kim.age = 88; console.log(kim.age); // → undefined

[](https://eloquentjavascript.net/04_data.html#p_B+oSPYAIbV)Values of type string, number, and Boolean are not objects, and though the language doesn’t complain if you try to set new properties on them, it doesn’t actually store those properties. As mentioned earlier, such values are immutable and cannot be changed.

[](https://eloquentjavascript.net/04_data.html#p_8L2ib2beYN)But these types do have built-in properties. Every string value has a number of methods. Some very useful ones are `slice` and `indexOf`, which resemble the array methods of the same name.
    
    [](https://eloquentjavascript.net/04_data.html#c_/Tmq1doYeG)console.log("coconuts".slice(4, 7)); // → nut console.log("coconut".indexOf("u")); // → 5

[](https://eloquentjavascript.net/04_data.html#p_RUd6q+Q4dc)One difference is that a string’s `indexOf` can search for a string containing more than one character, whereas the corresponding array method looks only for a single element.
    
    [](https://eloquentjavascript.net/04_data.html#c_xM5/GBnZVG)console.log("one two three".indexOf("ee")); // → 11

[](https://eloquentjavascript.net/04_data.html#p_USclxilOGS)The `trim` method removes whitespace (spaces, newlines, tabs, and similar characters) from the start and end of a string.
    
    [](https://eloquentjavascript.net/04_data.html#c_0AfLRWyjq0)console.log(" okay 
     ".trim()); // → okay

[](https://eloquentjavascript.net/04_data.html#p_pSkK9k9R0g)The `zeroPad` function from the [previous chapter](https://eloquentjavascript.net/03_functions.html) also exists as a method. It is called `padStart` and takes the desired length and padding character as arguments.
    
    [](https://eloquentjavascript.net/04_data.html#c_SJbD9MiYu+)console.log(String(6).padStart(3, "0")); // → 006

[](https://eloquentjavascript.net/04_data.html#p_/nMvmESoIj)You can split a string on every occurrence of another string with `split` and join it again with `join`.
    
    [](https://eloquentjavascript.net/04_data.html#c_/rV2Ed5e8V)let sentence = "Secretarybirds specialize in stomping"; let words = sentence.split(" "); console.log(words); // → ["Secretarybirds", "specialize", "in", "stomping"] console.log(words.join(". ")); // → Secretarybirds. specialize. in. stomping

[](https://eloquentjavascript.net/04_data.html#p_EKC26dOCjK)A string can be repeated with the `repeat` method, which creates a new string containing multiple copies of the original string, glued together.
    
    [](https://eloquentjavascript.net/04_data.html#c_70WotkNADb)console.log("LA".repeat(3)); // → LALALA

[](https://eloquentjavascript.net/04_data.html#p_JoGJxr+Ofe)We have already seen the string type’s `length` property. Accessing the individual characters in a string looks like accessing array elements (with a caveat that we’ll discuss in [Chapter 5](https://eloquentjavascript.net/05_higher_order.html#code_units)).
    
    [](https://eloquentjavascript.net/04_data.html#c_Aeop9AuKAb)let string = "abc"; console.log(string.length); // → 3 console.log(string[1]); // → b

## [](https://eloquentjavascript.net/04_data.html#h_hX9DkIBp9y)Rest parameters

[](https://eloquentjavascript.net/04_data.html#p_4Vr2QMYcHp)It can be useful for a function to accept any number of arguments. For example, `Math.max` computes the maximum of _all_ the arguments it is given.

[](https://eloquentjavascript.net/04_data.html#p_eWuSc6aG2b)To write such a function, you put three dots before the function’s last parameter, like this:
    
    [](https://eloquentjavascript.net/04_data.html#c_UXPbyGFVIB)function max(...numbers) { let result = -Infinity; for (let number of numbers) { if (number > result) result = number; } return result; } console.log(max(4, 1, 9, -2)); // → 9

[](https://eloquentjavascript.net/04_data.html#p_rGoFNpUuEy)When such a function is called, the _rest parameter_ is bound to an array containing all further arguments. If there are other parameters before it, their values aren’t part of that array. When, as in `max`, it is the only parameter, it will hold all arguments.

[](https://eloquentjavascript.net/04_data.html#p_ZVL6nOj2oy)You can use a similar three-dot notation to _call_ a function with an array of arguments.
    
    [](https://eloquentjavascript.net/04_data.html#c_h9hmTe3vix)let numbers = [5, 1, 7]; console.log(max(...numbers)); // → 7

[](https://eloquentjavascript.net/04_data.html#p_Q6Tzyy9eaj)This “spreads” out the array into the function call, passing its elements as separate arguments. It is possible to include an array like that along with other arguments, as in `max(9, ...numbers, 2)`.

[](https://eloquentjavascript.net/04_data.html#p_/SfVO/tjcB)Square bracket array notation similarly allows the triple-dot operator to spread another array into the new array.
    
    [](https://eloquentjavascript.net/04_data.html#c_4t+LJt3Kyo)let words = ["never", "fully"]; console.log(["will", ...words, "understand"]); // → ["will", "never", "fully", "understand"]

## [](https://eloquentjavascript.net/04_data.html#h_C51DnYk8WZ)The Math object

[](https://eloquentjavascript.net/04_data.html#p_h3aa0itA5J)As we’ve seen, `Math` is a grab bag of number-related utility functions, such as `Math.max` (maximum), `Math.min` (minimum), and `Math.sqrt` (square root).

[](https://eloquentjavascript.net/04_data.html#p_Sae3fXYP2/)The `Math` object is used as a container to group a bunch of related functionality. There is only one `Math` object, and it is almost never useful as a value. Rather, it provides a _namespace_ so that all these functions and values do not have to be global bindings.

[](https://eloquentjavascript.net/04_data.html#p_fGEMziAXhp)Having too many global bindings “pollutes” the namespace. The more names have been taken, the more likely you are to accidentally overwrite the value of some existing binding. For example, it’s not unlikely to want to name something `max` in one of your programs. Since JavaScript’s built-in `max` function is tucked safely inside the `Math` object, we don’t have to worry about overwriting it.

[](https://eloquentjavascript.net/04_data.html#p_6OHrUF+WEc)Many languages will stop you, or at least warn you, when you are defining a binding with a name that is already taken. JavaScript does this for bindings you declared with `let` or `const` but—perversely—not for standard bindings nor for bindings declared with `var` or `function`.

[](https://eloquentjavascript.net/04_data.html#p_zWXQRNgLI/)Back to the `Math` object. If you need to do trigonometry, `Math` can help. It contains `cos` (cosine), `sin` (sine), and `tan` (tangent), as well as their inverse functions, `acos`, `asin`, and `atan`, respectively. The number π (pi)—or at least the closest approximation that fits in a JavaScript number—is available as `Math.PI`. There is an old programming tradition of writing the names of constant values in all caps.
    
    [](https://eloquentjavascript.net/04_data.html#c_54zxf+2nsU)function randomPointOnCircle(radius) { let angle = Math.random() * 2 * Math.PI; return {x: radius * Math.cos(angle), y: radius * Math.sin(angle)}; } console.log(randomPointOnCircle(2)); // → {x: 0.3667, y: 1.966}

[](https://eloquentjavascript.net/04_data.html#p_KN16iaNdwJ)If sines and cosines are not something you are familiar with, don’t worry. When they are used in this book, in [Chapter 14](https://eloquentjavascript.net/14_dom.html#sin_cos), I’ll explain them.

[](https://eloquentjavascript.net/04_data.html#p_a6xMq73yCc)The previous example used `Math.random`. This is a function that returns a new pseudorandom number between zero (inclusive) and one (exclusive) every time you call it.
    
    [](https://eloquentjavascript.net/04_data.html#c_+gqW4B1qk1)console.log(Math.random()); // → 0.36993729369714856 console.log(Math.random()); // → 0.727367032552138 console.log(Math.random()); // → 0.40180766698904335

[](https://eloquentjavascript.net/04_data.html#p_wukRTlH+QE)Though computers are deterministic machines—they always react the same way if given the same input—it is possible to have them produce numbers that appear random. To do that, the machine keeps some hidden value, and whenever you ask for a new random number, it performs complicated computations on this hidden value to create a new value. It stores a new value and returns some number derived from it. That way, it can produce ever new, hard-to-predict numbers in a way that _seems_ random.

[](https://eloquentjavascript.net/04_data.html#p_2guGKjrtTY)If we want a whole random number instead of a fractional one, we can use `Math.floor` (which rounds down to the nearest whole number) on the result of `Math.random`.
    
    [](https://eloquentjavascript.net/04_data.html#c_LlfOX4tbSH)console.log(Math.floor(Math.random() * 10)); // → 2

[](https://eloquentjavascript.net/04_data.html#p_qcgl/8YUFj)Multiplying the random number by 10 gives us a number greater than or equal to 0 and below 10. Since `Math.floor` rounds down, this expression will produce, with equal chance, any number from 0 through 9.

[](https://eloquentjavascript.net/04_data.html#p_4Vo+PhEiYY)There are also the functions `Math.ceil` (for “ceiling”, which rounds up to a whole number), `Math.round` (to the nearest whole number), and `Math.abs`, which takes the absolute value of a number, meaning it negates negative values but leaves positive ones as they are.

## [](https://eloquentjavascript.net/04_data.html#h_B372u36cp6)Destructuring

[](https://eloquentjavascript.net/04_data.html#p_YaENzwA635)Let’s go back to the `phi` function for a moment.
    
    [](https://eloquentjavascript.net/04_data.html#c_8p90ivE8ZI)function phi(table) { return (table[3] * table[0] - table[2] * table[1]) / Math.sqrt((table[2] + table[3]) * (table[0] + table[1]) * (table[1] + table[3]) * (table[0] + table[2])); }

[](https://eloquentjavascript.net/04_data.html#p_KYh2WplVnQ)One of the reasons this function is awkward to read is that we have a binding pointing at our array, but we’d much prefer to have bindings for the _elements_ of the array, that is, `let n00 = table[0]` and so on. Fortunately, there is a succinct way to do this in JavaScript.
    
    [](https://eloquentjavascript.net/04_data.html#c_z2cboTL/zX)function phi([n00, n01, n10, n11]) { return (n11 * n00 - n10 * n01) / Math.sqrt((n10 + n11) * (n00 + n01) * (n01 + n11) * (n00 + n10)); }

[](https://eloquentjavascript.net/04_data.html#p_kBO/cFWeM1)This also works for bindings created with `let`, `var`, or `const`. If you know the value you are binding is an array, you can use square brackets to “look inside” of the value, binding its contents.

[](https://eloquentjavascript.net/04_data.html#p_Zr6hFslmUP)A similar trick works for objects, using braces instead of square brackets.
    
    [](https://eloquentjavascript.net/04_data.html#c_ZXEdn9Xbfc)let {name} = {name: "Faraji", age: 23}; console.log(name); // → Faraji

[](https://eloquentjavascript.net/04_data.html#p_1RhWeB9//B)Note that if you try to destructure `null` or `undefined`, you get an error, much as you would if you directly try to access a property of those values.

## [](https://eloquentjavascript.net/04_data.html#h_AxpOdvCznQ)JSON

[](https://eloquentjavascript.net/04_data.html#p_7o8VSa4Rvc)Because properties only grasp their value, rather than contain it, objects and arrays are stored in the computer’s memory as sequences of bits holding the _addresses_—the place in memory—of their contents. So an array with another array inside of it consists of (at least) one memory region for the inner array, and another for the outer array, containing (among other things) a binary number that represents the position of the inner array.

[](https://eloquentjavascript.net/04_data.html#p_aF+08iJEQw)If you want to save data in a file for later or send it to another computer over the network, you have to somehow convert these tangles of memory addresses to a description that can be stored or sent. You _could_ send over your entire computer memory along with the address of the value you’re interested in, I suppose, but that doesn’t seem like the best approach.

[](https://eloquentjavascript.net/04_data.html#p_ZM103Qyv6l)What we can do is _serialize_ the data. That means it is converted into a flat description. A popular serialization format is called _JSON_ (pronounced “Jason”), which stands for JavaScript Object Notation. It is widely used as a data storage and communication format on the Web, even in languages other than JavaScript.

[](https://eloquentjavascript.net/04_data.html#p_IMEKAvSfAI)JSON looks similar to JavaScript’s way of writing arrays and objects, with a few restrictions. All property names have to be surrounded by double quotes, and only simple data expressions are allowed—no function calls, bindings, or anything that involves actual computation. Comments are not allowed in JSON.

[](https://eloquentjavascript.net/04_data.html#p_9DCLKzKNiz)A journal entry might look like this when represented as JSON data:
    
    [](https://eloquentjavascript.net/04_data.html#c_A3jdCqz1Q6){ "squirrel": false, "events": ["work", "touched tree", "pizza", "running"] }

[](https://eloquentjavascript.net/04_data.html#p_1IU60Zh2Af)JavaScript gives us the functions `JSON.stringify` and `JSON.parse` to convert data to and from this format. The first takes a JavaScript value and returns a JSON-encoded string. The second takes such a string and converts it to the value it encodes.
    
    [](https://eloquentjavascript.net/04_data.html#c_HYCgCsK7z1)let string = JSON.stringify({squirrel: false, events: ["weekend"]}); console.log(string); // → {"squirrel":false,"events":["weekend"]} console.log(JSON.parse(string).events); // → ["weekend"]

## [](https://eloquentjavascript.net/04_data.html#h_ErccPg/l98)Summary

[](https://eloquentjavascript.net/04_data.html#p_78ZfHX5x1B)Objects and arrays (which are a specific kind of object) provide ways to group several values into a single value. Conceptually, this allows us to put a bunch of related things in a bag and run around with the bag, instead of wrapping our arms around all of the individual things and trying to hold on to them separately.

[](https://eloquentjavascript.net/04_data.html#p_ayhyxvWlMH)Most values in JavaScript have properties, the exceptions being `null` and `undefined`. Properties are accessed using `value.prop` or `value["prop"]`. Objects tend to use names for their properties and store more or less a fixed set of them. Arrays, on the other hand, usually contain varying amounts of conceptually identical values and use numbers (starting from 0) as the names of their properties.

[](https://eloquentjavascript.net/04_data.html#p_1lcitbawCQ)There _are_ some named properties in arrays, such as `length` and a number of methods. Methods are functions that live in properties and (usually) act on the value they are a property of.

[](https://eloquentjavascript.net/04_data.html#p_KWzs1al6OP)You can iterate over arrays using a special kind of `for` loop—`for (let element of array)`.

## [](https://eloquentjavascript.net/04_data.html#h_TcUD2vzyMe)Exercises

### [](https://eloquentjavascript.net/04_data.html#i_8ZspxiCEC/)The sum of a range

[](https://eloquentjavascript.net/04_data.html#p_fpyyiv/hm1)The [introduction](https://eloquentjavascript.net/00_intro.html) of this book alluded to the following as a nice way to compute the sum of a range of numbers:
    
    [](https://eloquentjavascript.net/04_data.html#c_KTbQMmMCli)console.log(sum(range(1, 10)));

[](https://eloquentjavascript.net/04_data.html#p_uTMnVb6I1m)Write a `range` function that takes two arguments, `start` and `end`, and returns an array containing all the numbers from `start` up to (and including) `end`.

[](https://eloquentjavascript.net/04_data.html#p_0GiJNcBSop)Next, write a `sum` function that takes an array of numbers and returns the sum of these numbers. Run the example program and see whether it does indeed return 55.

[](https://eloquentjavascript.net/04_data.html#p_1Uvf7bfQT8)As a bonus assignment, modify your `range` function to take an optional third argument that indicates the “step” value used when building the array. If no step is given, the elements go up by increments of one, corresponding to the old behavior. The function call `range(1, 10, 2)` should return `[1, 3, 5, 7, 9]`. Make sure it also works with negative step values so that `range(5, 2, -1)` produces `[5, 4, 3, 2]`.
    
    [](https://eloquentjavascript.net/04_data.html#c_gV3XCKJAqj)// Your code here. console.log(range(1, 10)); // → [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] console.log(range(5, 2, -1)); // → [5, 4, 3, 2] console.log(sum(range(1, 10))); // → 55

### [](https://eloquentjavascript.net/04_data.html#i_6xTmjj4Rf5)Reversing an array

[](https://eloquentjavascript.net/04_data.html#p_+SVCOC/qcN)Arrays have a `reverse` method that changes the array by inverting the order in which its elements appear. For this exercise, write two functions, `reverseArray` and `reverseArrayInPlace`. The first, `reverseArray`, takes an array as argument and produces a _new_ array that has the same elements in the inverse order. The second, `reverseArrayInPlace`, does what the `reverse` method does: it _modifies_ the array given as argument by reversing its elements. Neither may use the standard `reverse` method.

[](https://eloquentjavascript.net/04_data.html#p_SpaDJmGkSI)Thinking back to the notes about side effects and pure functions in the [previous chapter](https://eloquentjavascript.net/03_functions.html#pure), which variant do you expect to be useful in more situations? Which one runs faster?
    
    [](https://eloquentjavascript.net/04_data.html#c_sghv5avX0H)// Your code here. console.log(reverseArray(["A", "B", "C"])); // → ["C", "B", "A"]; let arrayValue = [1, 2, 3, 4, 5]; reverseArrayInPlace(arrayValue); console.log(arrayValue); // → [5, 4, 3, 2, 1]

### [](https://eloquentjavascript.net/04_data.html#i_nSTX34CM1M)A list

[](https://eloquentjavascript.net/04_data.html#p_7AnSuS26HF)Objects, as generic blobs of values, can be used to build all sorts of data structures. A common data structure is the _list_ (not to be confused with array). A list is a nested set of objects, with the first object holding a reference to the second, the second to the third, and so on.
    
    [](https://eloquentjavascript.net/04_data.html#c_kYAco70aHD)let list = { value: 1, rest: { value: 2, rest: { value: 3, rest: null } } };

[](https://eloquentjavascript.net/04_data.html#p_2un5u6U14Q)The resulting objects form a chain, like this:

![A linked list](https://eloquentjavascript.net/img/linked-list.svg)

[](https://eloquentjavascript.net/04_data.html#p_NaI0fhp38z)A nice thing about lists is that they can share parts of their structure. For example, if I create two new values `{value: 0, rest: list}` and `{value: -1, rest: list}` (with `list` referring to the binding defined earlier), they are both independent lists, but they share the structure that makes up their last three elements. The original list is also still a valid three-element list.

[](https://eloquentjavascript.net/04_data.html#p_iPlgVCeZGh)Write a function `arrayToList` that builds up a list structure like the one shown when given `[1, 2, 3]` as argument. Also write a `listToArray` function that produces an array from a list. Then add a helper function `prepend`, which takes an element and a list and creates a new list that adds the element to the front of the input list, and `nth`, which takes a list and a number and returns the element at the given position in the list (with zero referring to the first element) or `undefined` when there is no such element.

[](https://eloquentjavascript.net/04_data.html#p_8YcepSmcdv)If you haven’t already, also write a recursive version of `nth`.
    
    [](https://eloquentjavascript.net/04_data.html#c_rufmukl+AQ)// Your code here. console.log(arrayToList([10, 20])); // → {value: 10, rest: {value: 20, rest: null}} console.log(listToArray(arrayToList([10, 20, 30]))); // → [10, 20, 30] console.log(prepend(10, prepend(20, null))); // → {value: 10, rest: {value: 20, rest: null}} console.log(nth(arrayToList([10, 20, 30]), 1)); // → 20

### [](https://eloquentjavascript.net/04_data.html#i_IJBU+aXOIC)Deep comparison

[](https://eloquentjavascript.net/04_data.html#p_xTwbRlqHNJ)The `==` operator compares objects by identity. But sometimes you’d prefer to compare the values of their actual properties.

[](https://eloquentjavascript.net/04_data.html#p_DwdnLiD0pC)Write a function `deepEqual` that takes two values and returns true only if they are the same value or are objects with the same properties, where the values of the properties are equal when compared with a recursive call to `deepEqual`.

[](https://eloquentjavascript.net/04_data.html#p_Znb46HKrMg)To find out whether values should be compared directly (use the `===` operator for that) or have their properties compared, you can use the `typeof` operator. If it produces `"object"` for both values, you should do a deep comparison. But you have to take one silly exception into account: because of a historical accident, `typeof null` also produces `"object"`.

[](https://eloquentjavascript.net/04_data.html#p_n9AoXEbeFg)The `Object.keys` function will be useful when you need to go over the properties of objects to compare them.
    
    [](https://eloquentjavascript.net/04_data.html#c_kWPN5i/Y3x)// Your code here. let obj = {here: {is: "an"}, object: 2}; console.log(deepEqual(obj, obj)); // → true console.log(deepEqual(obj, {here: 1, object: 2})); // → false console.log(deepEqual(obj, {here: {is: "an"}, object: 2})); // → true
