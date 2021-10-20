```
Source:
Tags: 
Last-Updated:
```

# Chapter 10Modules

> [](https://eloquentjavascript.net/10_modules.html#p_OwlHMaRbBt)Write code that is easy to delete, not easy to extend.
> 
> Tef, Programming is Terrible

![Picture of a building built from modular pieces](https://eloquentjavascript.net/img/chapter_picture_10.jpg)

[](https://eloquentjavascript.net/10_modules.html#p_lt7t/NZub8)The ideal program has a crystal-clear structure. The way it works is easy to explain, and each part plays a well-defined role.

[](https://eloquentjavascript.net/10_modules.html#p_HLTCewyOYT)A typical real program grows organically. New pieces of functionality are added as new needs come up. Structuring—and preserving structure—is additional work. It’s work that will pay off only in the future, the _next_ time someone works on the program. So it is tempting to neglect it and allow the parts of the program to become deeply entangled.

[](https://eloquentjavascript.net/10_modules.html#p_Ph53LAfIAv)This causes two practical issues. First, understanding such a system is hard. If everything can touch everything else, it is difficult to look at any given piece in isolation. You are forced to build up a holistic understanding of the entire thing. Second, if you want to use any of the functionality from such a program in another situation, rewriting it may be easier than trying to disentangle it from its context.

[](https://eloquentjavascript.net/10_modules.html#p_pzOEW37Kfc)The phrase “big ball of mud” is often used for such large, structureless programs. Everything sticks together, and when you try to pick out a piece, the whole thing comes apart, and your hands get dirty.

## [](https://eloquentjavascript.net/10_modules.html#h_BOlGLA/wK7)Modules

[](https://eloquentjavascript.net/10_modules.html#p_LoWZBZ2Vpv)_Modules_ are an attempt to avoid these problems. A module is a piece of program that specifies which other pieces it relies on and which functionality it provides for other modules to use (its _interface_).

[](https://eloquentjavascript.net/10_modules.html#p_kjhUrZ1SF0)Module interfaces have a lot in common with object interfaces, as we saw them in [Chapter 6](https://eloquentjavascript.net/06_object.html#interface). They make part of the module available to the outside world and keep the rest private. By restricting the ways in which modules interact with each other, the system becomes more like LEGO, where pieces interact through well-defined connectors, and less like mud, where everything mixes with everything.

[](https://eloquentjavascript.net/10_modules.html#p_l+1k6bprY2)The relations between modules are called _dependencies_. When a module needs a piece from another module, it is said to depend on that module. When this fact is clearly specified in the module itself, it can be used to figure out which other modules need to be present to be able to use a given module and to automatically load dependencies.

[](https://eloquentjavascript.net/10_modules.html#p_4WkC7snvFx)To separate modules in that way, each needs its own private scope.

[](https://eloquentjavascript.net/10_modules.html#p_bgQuCetNwq)Just putting your JavaScript code into different files does not satisfy these requirements. The files still share the same global namespace. They can, intentionally or accidentally, interfere with each other’s bindings. And the dependency structure remains unclear. We can do better, as we’ll see later in the chapter.

[](https://eloquentjavascript.net/10_modules.html#p_uf1CU70zfG)Designing a fitting module structure for a program can be difficult. In the phase where you are still exploring the problem, trying different things to see what works, you might want to not worry about it too much since it can be a big distraction. Once you have something that feels solid, that’s a good time to take a step back and organize it.

## [](https://eloquentjavascript.net/10_modules.html#h_CpmQEv+4ez)Packages

[](https://eloquentjavascript.net/10_modules.html#p_g7o14y8ONd)One of the advantages of building a program out of separate pieces, and being actually able to run those pieces on their own, is that you might be able to apply the same piece in different programs.

[](https://eloquentjavascript.net/10_modules.html#p_iBvlR95Pda)But how do you set this up? Say I want to use the `parseINI` function from [Chapter 9](https://eloquentjavascript.net/09_regexp.html#ini) in another program. If it is clear what the function depends on (in this case, nothing), I can just copy all the necessary code into my new project and use it. But then, if I find a mistake in that code, I’ll probably fix it in whichever program I’m working with at the time and forget to also fix it in the other program.

[](https://eloquentjavascript.net/10_modules.html#p_TA/SfLJ50i)Once you start duplicating code, you’ll quickly find yourself wasting time and energy moving copies around and keeping them up-to-date.

[](https://eloquentjavascript.net/10_modules.html#p_CNI2vOkPJp)That’s where _packages_ come in. A package is a chunk of code that can be distributed (copied and installed). It may contain one or more modules and has information about which other packages it depends on. A package also usually comes with documentation explaining what it does so that people who didn’t write it might still be able to use it.

[](https://eloquentjavascript.net/10_modules.html#p_sZgcoPgtEe)When a problem is found in a package or a new feature is added, the package is updated. Now the programs that depend on it (which may also be packages) can upgrade to the new version.

[](https://eloquentjavascript.net/10_modules.html#p_oiLHr3lvbw)Working in this way requires infrastructure. We need a place to store and find packages and a convenient way to install and upgrade them. In the JavaScript world, this infrastructure is provided by NPM ([_https://npmjs.org_](https://npmjs.org)).

[](https://eloquentjavascript.net/10_modules.html#p_WUPNc5b7D2)NPM is two things: an online service where one can download (and upload) packages and a program (bundled with Node.js) that helps you install and manage them.

[](https://eloquentjavascript.net/10_modules.html#p_kcXuOxm8Rl)At the time of writing, there are more than half a million different packages available on NPM. A large portion of those are rubbish, I should mention, but almost every useful, publicly available package can be found on there. For example, an INI file parser, similar to the one we built in [Chapter 9](https://eloquentjavascript.net/09_regexp.html), is available under the package name `ini`.

[](https://eloquentjavascript.net/10_modules.html#p_irXmhzBaaT)[Chapter 20](https://eloquentjavascript.net/20_node.html) will show how to install such packages locally using the `npm` command line program.

[](https://eloquentjavascript.net/10_modules.html#p_D/2FJ7Crwg)Having quality packages available for download is extremely valuable. It means that we can often avoid reinventing a program that 100 people have written before and get a solid, well-tested implementation at the press of a few keys.

[](https://eloquentjavascript.net/10_modules.html#p_4hMCknNFh+)Software is cheap to copy, so once someone has written it, distributing it to other people is an efficient process. But writing it in the first place _is_ work, and responding to people who have found problems in the code, or who want to propose new features, is even more work.

[](https://eloquentjavascript.net/10_modules.html#p_K/LevaOaUV)By default, you own the copyright to the code you write, and other people may use it only with your permission. But because some people are just nice and because publishing good software can help make you a little bit famous among programmers, many packages are published under a license that explicitly allows other people to use it.

[](https://eloquentjavascript.net/10_modules.html#p_sWMlqqRmbd)Most code on NPM is licensed this way. Some licenses require you to also publish code that you build on top of the package under the same license. Others are less demanding, just requiring that you keep the license with the code as you distribute it. The JavaScript community mostly uses the latter type of license. When using other people’s packages, make sure you are aware of their license.

## [](https://eloquentjavascript.net/10_modules.html#h_QQ/m+TRmqd)Improvised modules

[](https://eloquentjavascript.net/10_modules.html#p_VhfSheFY3t)Until 2015, the JavaScript language had no built-in module system. Yet people had been building large systems in JavaScript for more than a decade, and they _needed_ modules.

[](https://eloquentjavascript.net/10_modules.html#p_EThAZWj4TA)So they designed their own module systems on top of the language. You can use JavaScript functions to create local scopes and objects to represent module interfaces.

[](https://eloquentjavascript.net/10_modules.html#p_3jjByT+Dg0)This is a module for going between day names and numbers (as returned by `Date`’s `getDay` method). Its interface consists of `weekDay.name` and `weekDay.number`, and it hides its local binding `names` inside the scope of a function expression that is immediately invoked.
    
    edit & run code by clicking it
    
    [](https://eloquentjavascript.net/10_modules.html#c_m+yRMF5NXw)const weekDay = function() { const names = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]; return { name(number) { return names[number]; }, number(name) { return names.indexOf(name); } }; }(); console.log(weekDay.name(weekDay.number("Sunday"))); // → Sunday

[](https://eloquentjavascript.net/10_modules.html#p_uv8xnuw95L)This style of modules provides isolation, to a certain degree, but it does not declare dependencies. Instead, it just puts its interface into the global scope and expects its dependencies, if any, to do the same. For a long time this was the main approach used in web programming, but it is mostly obsolete now.

[](https://eloquentjavascript.net/10_modules.html#p_i8xxHMuJw+)If we want to make dependency relations part of the code, we’ll have to take control of loading dependencies. Doing that requires being able to execute strings as code. JavaScript can do this.

## [](https://eloquentjavascript.net/10_modules.html#h_oeOkEDaadU)Evaluating data as code

[](https://eloquentjavascript.net/10_modules.html#p_jvij1au4eP)There are several ways to take data (a string of code) and run it as part of the current program.

[](https://eloquentjavascript.net/10_modules.html#p_8T3Py6Zkwc)The most obvious way is the special operator `eval`, which will execute a string in the _current_ scope. This is usually a bad idea because it breaks some of the properties that scopes normally have, such as it being easily predictable which binding a given name refers to.
    
    [](https://eloquentjavascript.net/10_modules.html#c_14x3bOXX9G)const x = 1; function evalAndReturnX(code) { eval(code); return x; } console.log(evalAndReturnX("var x = 2")); // → 2 console.log(x); // → 1

[](https://eloquentjavascript.net/10_modules.html#p_wzjzmC3uLa)A less scary way of interpreting data as code is to use the `Function` constructor. It takes two arguments: a string containing a comma-separated list of argument names and a string containing the function body. It wraps the code in a function value so that it gets its own scope and won’t do odd things with other scopes.
    
    [](https://eloquentjavascript.net/10_modules.html#c_Mc9BAi4AVK)let plusOne = Function("n", "return n + 1;"); console.log(plusOne(4)); // → 5

[](https://eloquentjavascript.net/10_modules.html#p_vgKeYBfC4h)This is precisely what we need for a module system. We can wrap the module’s code in a function and use that function’s scope as module scope.

## [](https://eloquentjavascript.net/10_modules.html#h_N33QHgUxbG)CommonJS

[](https://eloquentjavascript.net/10_modules.html#p_kAtCGxNjIq)The most widely used approach to bolted-on JavaScript modules is called _CommonJS modules_. Node.js uses it and is the system used by most packages on NPM.

[](https://eloquentjavascript.net/10_modules.html#p_NM2zfHqLcE)The main concept in CommonJS modules is a function called `require`. When you call this with the module name of a dependency, it makes sure the module is loaded and returns its interface.

[](https://eloquentjavascript.net/10_modules.html#p_CNeZtts3Cz)Because the loader wraps the module code in a function, modules automatically get their own local scope. All they have to do is call `require` to access their dependencies and put their interface in the object bound to `exports`.

[](https://eloquentjavascript.net/10_modules.html#p_ew2dDAURuM)This example module provides a date-formatting function. It uses two packages from NPM—`ordinal` to convert numbers to strings like `"1st"` and `"2nd"`, and `date-names` to get the English names for weekdays and months. It exports a single function, `formatDate`, which takes a `Date` object and a template string.

[](https://eloquentjavascript.net/10_modules.html#p_fH0b3BN1Fp)The template string may contain codes that direct the format, such as `YYYY` for the full year and `Do` for the ordinal day of the month. You could give it a string like `"MMMM Do YYYY"` to get output like “November 22nd 2017”.
    
    [](https://eloquentjavascript.net/10_modules.html#c_hEFnba6fud)const ordinal = require("ordinal"); const {days, months} = require("date-names"); exports.formatDate = function(date, format) { return format.replace(/YYYY|M(MMM)?|Do?|dddd/g, tag => { if (tag == "YYYY") return date.getFullYear(); if (tag == "M") return date.getMonth(); if (tag == "MMMM") return months[date.getMonth()]; if (tag == "D") return date.getDate(); if (tag == "Do") return ordinal(date.getDate()); if (tag == "dddd") return days[date.getDay()]; }); };

[](https://eloquentjavascript.net/10_modules.html#p_jvrgfRxGB4)The interface of `ordinal` is a single function, whereas `date-names` exports an object containing multiple things—`days` and `months` are arrays of names. Destructuring is very convenient when creating bindings for imported interfaces.

[](https://eloquentjavascript.net/10_modules.html#p_cHv4rZkvfj)The module adds its interface function to `exports` so that modules that depend on it get access to it. We could use the module like this:
    
    [](https://eloquentjavascript.net/10_modules.html#c_pWURcHuHTt)const {formatDate} = require("./format-date"); console.log(formatDate(new Date(2017, 9, 13), "dddd the Do")); // → Friday the 13th

[](https://eloquentjavascript.net/10_modules.html#p_vmJrDleGRH)We can define `require`, in its most minimal form, like this:
    
    [](https://eloquentjavascript.net/10_modules.html#c_CSMfqoYOzp)require.cache = Object.create(null); function require(name) { if (!(name in require.cache)) { let code = readFile(name); let module = {exports: {}}; require.cache[name] = module; let wrapper = Function("require, exports, module", code); wrapper(require, module.exports, module); } return require.cache[name].exports; }

[](https://eloquentjavascript.net/10_modules.html#p_sc1VEkBDCY)In this code, `readFile` is a made-up function that reads a file and returns its contents as a string. Standard JavaScript provides no such functionality—but different JavaScript environments, such as the browser and Node.js, provide their own ways of accessing files. The example just pretends that `readFile` exists.

[](https://eloquentjavascript.net/10_modules.html#p_DxNIETFONd)To avoid loading the same module multiple times, `require` keeps a store (cache) of already loaded modules. When called, it first checks if the requested module has been loaded and, if not, loads it. This involves reading the module’s code, wrapping it in a function, and calling it.

[](https://eloquentjavascript.net/10_modules.html#p_tI7DzFSLjM)The interface of the `ordinal` package we saw before is not an object but a function. A quirk of the CommonJS modules is that, though the module system will create an empty interface object for you (bound to `exports`), you can replace that with any value by overwriting `module.exports`. This is done by many modules to export a single value instead of an interface object.

[](https://eloquentjavascript.net/10_modules.html#p_1en0vUqbeI)By defining `require`, `exports`, and `module` as parameters for the generated wrapper function (and passing the appropriate values when calling it), the loader makes sure that these bindings are available in the module’s scope.

[](https://eloquentjavascript.net/10_modules.html#p_xriS0EN27o)The way the string given to `require` is translated to an actual filename or web address differs in different systems. When it starts with `"./"` or `"../"`, it is generally interpreted as relative to the current module’s filename. So `"./format-date"` would be the file named `format-date.js` in the same directory.

[](https://eloquentjavascript.net/10_modules.html#p_L5+LG67XHa)When the name isn’t relative, Node.js will look for an installed package by that name. In the example code in this chapter, we’ll interpret such names as referring to NPM packages. We’ll go into more detail on how to install and use NPM modules in [Chapter 20](https://eloquentjavascript.net/20_node.html).

[](https://eloquentjavascript.net/10_modules.html#p_B5bzWP/zEC)Now, instead of writing our own INI file parser, we can use one from NPM.
    
    [](https://eloquentjavascript.net/10_modules.html#c_LfcCXOMZGr)const {parse} = require("ini"); console.log(parse("x = 10
    y = 20")); // → {x: "10", y: "20"}

## [](https://eloquentjavascript.net/10_modules.html#h_hF2FmOVxw7)ECMAScript modules

[](https://eloquentjavascript.net/10_modules.html#p_ZB3AF/XP4y)CommonJS modules work quite well and, in combination with NPM, have allowed the JavaScript community to start sharing code on a large scale.

[](https://eloquentjavascript.net/10_modules.html#p_yy6++k1U8b)But they remain a bit of a duct-tape hack. The notation is slightly awkward—the things you add to `exports` are not available in the local scope, for example. And because `require` is a normal function call taking any kind of argument, not just a string literal, it can be hard to determine the dependencies of a module without running its code.

[](https://eloquentjavascript.net/10_modules.html#p_fGE1JkAJHH)This is why the JavaScript standard from 2015 introduces its own, different module system. It is usually called _ES modules_, where _ES_ stands for ECMAScript. The main concepts of dependencies and interfaces remain the same, but the details differ. For one thing, the notation is now integrated into the language. Instead of calling a function to access a dependency, you use a special `import` keyword.
    
    [](https://eloquentjavascript.net/10_modules.html#c_EpiH8qOAcJ)import ordinal from "ordinal"; import {days, months} from "date-names"; export function formatDate(date, format) { /* ... */ }

[](https://eloquentjavascript.net/10_modules.html#p_Md0hUIO/t1)Similarly, the `export` keyword is used to export things. It may appear in front of a function, class, or binding definition (`let`, `const`, or `var`).

[](https://eloquentjavascript.net/10_modules.html#p_2XcNI5i8RP)An ES module’s interface is not a single value but a set of named bindings. The preceding module binds `formatDate` to a function. When you import from another module, you import the _binding_, not the value, which means an exporting module may change the value of the binding at any time, and the modules that import it will see its new value.

[](https://eloquentjavascript.net/10_modules.html#p_H96aQvDt7C)When there is a binding named `default`, it is treated as the module’s main exported value. If you import a module like `ordinal` in the example, without braces around the binding name, you get its `default` binding. Such modules can still export other bindings under different names alongside their `default` export.

[](https://eloquentjavascript.net/10_modules.html#p_C4XHB0ByrT)To create a default export, you write `export default` before an expression, a function declaration, or a class declaration.
    
    [](https://eloquentjavascript.net/10_modules.html#c_Y6Wnu9X+/W)export default ["Winter", "Spring", "Summer", "Autumn"];

[](https://eloquentjavascript.net/10_modules.html#p_XbHIrV+nuJ)It is possible to rename imported bindings using the word `as`.
    
    [](https://eloquentjavascript.net/10_modules.html#c_I7jPaQvsXj)import {days as dayNames} from "date-names"; console.log(dayNames.length); // → 7

[](https://eloquentjavascript.net/10_modules.html#p_oqym70c7ZR)Another important difference is that ES module imports happen before a module’s script starts running. That means `import` declarations may not appear inside functions or blocks, and the names of dependencies must be quoted strings, not arbitrary expressions.

[](https://eloquentjavascript.net/10_modules.html#p_+UaRV7zy4m)At the time of writing, the JavaScript community is in the process of adopting this module style. But it has been a slow process. It took a few years, after the format was specified, for browsers and Node.js to start supporting it. And though they mostly support it now, this support still has issues, and the discussion on how such modules should be distributed through NPM is still ongoing.

[](https://eloquentjavascript.net/10_modules.html#p_UEipP/dEjR)Many projects are written using ES modules and then automatically converted to some other format when published. We are in a transitional period in which two different module systems are used side by side, and it is useful to be able to read and write code in either of them.

## [](https://eloquentjavascript.net/10_modules.html#h_zWTXAU93DC)Building and bundling

[](https://eloquentjavascript.net/10_modules.html#p_Si0Uy8W7Rk)In fact, many JavaScript projects aren’t even, technically, written in JavaScript. There are extensions, such as the type checking dialect mentioned in [Chapter 8](https://eloquentjavascript.net/08_error.html#typing), that are widely used. People also often start using planned extensions to the language long before they have been added to the platforms that actually run JavaScript.

[](https://eloquentjavascript.net/10_modules.html#p_8YI40LC/+x)To make this possible, they _compile_ their code, translating it from their chosen JavaScript dialect to plain old JavaScript—or even to a past version of JavaScript—so that old browsers can run it.

[](https://eloquentjavascript.net/10_modules.html#p_xCwSgQaAdq)Including a modular program that consists of 200 different files in a web page produces its own problems. If fetching a single file over the network takes 50 milliseconds, loading the whole program takes 10 seconds, or maybe half that if you can load several files simultaneously. That’s a lot of wasted time. Because fetching a single big file tends to be faster than fetching a lot of tiny ones, web programmers have started using tools that roll their programs (which they painstakingly split into modules) back into a single big file before they publish it to the Web. Such tools are called _bundlers_.

[](https://eloquentjavascript.net/10_modules.html#p_F5bhvXPahh)And we can go further. Apart from the number of files, the _size_ of the files also determines how fast they can be transferred over the network. Thus, the JavaScript community has invented _minifiers_. These are tools that take a JavaScript program and make it smaller by automatically removing comments and whitespace, renaming bindings, and replacing pieces of code with equivalent code that take up less space.

[](https://eloquentjavascript.net/10_modules.html#p_0kzBnsBjVM)So it is not uncommon for the code that you find in an NPM package or that runs on a web page to have gone through _multiple_ stages of transformation—converted from modern JavaScript to historic JavaScript, from ES module format to CommonJS, bundled, and minified. We won’t go into the details of these tools in this book since they tend to be boring and change rapidly. Just be aware that the JavaScript code you run is often not the code as it was written.

## [](https://eloquentjavascript.net/10_modules.html#h_P8pyzbI9vO)Module design

[](https://eloquentjavascript.net/10_modules.html#p_8K2T8s7itK)Structuring programs is one of the subtler aspects of programming. Any nontrivial piece of functionality can be modeled in various ways.

[](https://eloquentjavascript.net/10_modules.html#p_98c2qP5s8p)Good program design is subjective—there are trade-offs involved and matters of taste. The best way to learn the value of well-structured design is to read or work on a lot of programs and notice what works and what doesn’t. Don’t assume that a painful mess is “just the way it is”. You can improve the structure of almost everything by putting more thought into it.

[](https://eloquentjavascript.net/10_modules.html#p_AF7qUrMoR4)One aspect of module design is ease of use. If you are designing something that is intended to be used by multiple people—or even by yourself, in three months when you no longer remember the specifics of what you did—it is helpful if your interface is simple and predictable.

[](https://eloquentjavascript.net/10_modules.html#p_hHDSnM2Orb)That may mean following existing conventions. A good example is the `ini` package. This module imitates the standard `JSON` object by providing `parse` and `stringify` (to write an INI file) functions, and, like `JSON`, converts between strings and plain objects. So the interface is small and familiar, and after you’ve worked with it once, you’re likely to remember how to use it.

[](https://eloquentjavascript.net/10_modules.html#p_uS+as91Giv)Even if there’s no standard function or widely used package to imitate, you can keep your modules predictable by using simple data structures and doing a single, focused thing. Many of the INI-file parsing modules on NPM provide a function that directly reads such a file from the hard disk and parses it, for example. This makes it impossible to use such modules in the browser, where we don’t have direct file system access, and adds complexity that would have been better addressed by _composing_ the module with some file-reading function.

[](https://eloquentjavascript.net/10_modules.html#p_JYcq/PgjlO)This points to another helpful aspect of module design—the ease with which something can be composed with other code. Focused modules that compute values are applicable in a wider range of programs than bigger modules that perform complicated actions with side effects. An INI file reader that insists on reading the file from disk is useless in a scenario where the file’s content comes from some other source.

[](https://eloquentjavascript.net/10_modules.html#p_6cqySeVoki)Relatedly, stateful objects are sometimes useful or even necessary, but if something can be done with a function, use a function. Several of the INI file readers on NPM provide an interface style that requires you to first create an object, then load the file into your object, and finally use specialized methods to get at the results. This type of thing is common in the object-oriented tradition, and it’s terrible. Instead of making a single function call and moving on, you have to perform the ritual of moving your object through various states. And because the data is now wrapped in a specialized object type, all code that interacts with it has to know about that type, creating unnecessary interdependencies.

[](https://eloquentjavascript.net/10_modules.html#p_uR7iWbgBIy)Often defining new data structures can’t be avoided—only a few basic ones are provided by the language standard, and many types of data have to be more complex than an array or a map. But when an array suffices, use an array.

[](https://eloquentjavascript.net/10_modules.html#p_gE7WoNX7+Z)An example of a slightly more complex data structure is the graph from [Chapter 7](https://eloquentjavascript.net/07_robot.html). There is no single obvious way to represent a graph in JavaScript. In that chapter, we used an object whose properties hold arrays of strings—the other nodes reachable from that node.

[](https://eloquentjavascript.net/10_modules.html#p_17Fkotj+nV)There are several different pathfinding packages on NPM, but none of them uses this graph format. They usually allow the graph’s edges to have a weight, which is the cost or distance associated with it. That isn’t possible in our representation.

[](https://eloquentjavascript.net/10_modules.html#p_d3wpFXYEjN)For example, there’s the `dijkstrajs` package. A well-known approach to pathfinding, quite similar to our `findRoute` function, is called _Dijkstra’s algorithm_, after Edsger Dijkstra, who first wrote it down. The `js` suffix is often added to package names to indicate the fact that they are written in JavaScript. This `dijkstrajs` package uses a graph format similar to ours, but instead of arrays, it uses objects whose property values are numbers—the weights of the edges.

[](https://eloquentjavascript.net/10_modules.html#p_3iug1e4kQG)So if we wanted to use that package, we’d have to make sure that our graph was stored in the format it expects. All edges get the same weight since our simplified model treats each road as having the same cost (one turn).
    
    [](https://eloquentjavascript.net/10_modules.html#c_NyRXVpwPYN)const {find_path} = require("dijkstrajs"); let graph = {}; for (let node of Object.keys(roadGraph)) { let edges = graph[node] = {}; for (let dest of roadGraph[node]) { edges[dest] = 1; } } console.log(find_path(graph, "Post Office", "Cabin")); // → ["Post Office", "Alice's House", "Cabin"]

[](https://eloquentjavascript.net/10_modules.html#p_X8Ulb726ZC)This can be a barrier to composition—when various packages are using different data structures to describe similar things, combining them is difficult. Therefore, if you want to design for composability, find out what data structures other people are using and, when possible, follow their example.

## [](https://eloquentjavascript.net/10_modules.html#h_ErccPg/l98)Summary

[](https://eloquentjavascript.net/10_modules.html#p_OX2jY0nGFw)Modules provide structure to bigger programs by separating the code into pieces with clear interfaces and dependencies. The interface is the part of the module that’s visible from other modules, and the dependencies are the other modules that it makes use of.

[](https://eloquentjavascript.net/10_modules.html#p_sYCJxIhCEI)Because JavaScript historically did not provide a module system, the CommonJS system was built on top of it. Then at some point it _did_ get a built-in system, which now coexists uneasily with the CommonJS system.

[](https://eloquentjavascript.net/10_modules.html#p_wDM2Q8HBcB)A package is a chunk of code that can be distributed on its own. NPM is a repository of JavaScript packages. You can download all kinds of useful (and useless) packages from it.

## [](https://eloquentjavascript.net/10_modules.html#h_TcUD2vzyMe)Exercises

### [](https://eloquentjavascript.net/10_modules.html#i_CJKk6NIC0T)A modular robot

[](https://eloquentjavascript.net/10_modules.html#p_nPAEnO4pep)These are the bindings that the project from [Chapter 7](https://eloquentjavascript.net/07_robot.html) creates:
    
    [](https://eloquentjavascript.net/10_modules.html#c_/nxTd1W0Sy)roads buildGraph roadGraph VillageState runRobot randomPick randomRobot mailRoute routeRobot findRoute goalOrientedRobot

[](https://eloquentjavascript.net/10_modules.html#p_0LdymcLoV8)If you were to write that project as a modular program, what modules would you create? Which module would depend on which other module, and what would their interfaces look like?

[](https://eloquentjavascript.net/10_modules.html#p_hU/u/IPER+)Which pieces are likely to be available prewritten on NPM? Would you prefer to use an NPM package or write them yourself?

### [](https://eloquentjavascript.net/10_modules.html#i_+pU//gQmZ8)Roads module

[](https://eloquentjavascript.net/10_modules.html#p_U88wPDSl2i)Write a CommonJS module, based on the example from [Chapter 7](https://eloquentjavascript.net/07_robot.html), that contains the array of roads and exports the graph data structure representing them as `roadGraph`. It should depend on a module `./graph`, which exports a function `buildGraph` that is used to build the graph. This function expects an array of two-element arrays (the start and end points of the roads).
    
    [](https://eloquentjavascript.net/10_modules.html#c_FPEwj7xDOs)// Add dependencies and exports const roads = [ "Alice's House-Bob's House", "Alice's House-Cabin", "Alice's House-Post Office", "Bob's House-Town Hall", "Daria's House-Ernie's House", "Daria's House-Town Hall", "Ernie's House-Grete's House", "Grete's House-Farm", "Grete's House-Shop", "Marketplace-Farm", "Marketplace-Post Office", "Marketplace-Shop", "Marketplace-Town Hall", "Shop-Town Hall" ];

### [](https://eloquentjavascript.net/10_modules.html#i_E/zWqBFdy8)Circular dependencies

[](https://eloquentjavascript.net/10_modules.html#p_fl2MZMonQV)A circular dependency is a situation where module A depends on B, and B also, directly or indirectly, depends on A. Many module systems simply forbid this because whichever order you choose for loading such modules, you cannot make sure that each module’s dependencies have been loaded before it runs.

[](https://eloquentjavascript.net/10_modules.html#p_b5sTJIUt38)CommonJS modules allow a limited form of cyclic dependencies. As long as the modules do not replace their default `exports` object and don’t access each other’s interface until after they finish loading, cyclic dependencies are okay.

[](https://eloquentjavascript.net/10_modules.html#p_s/oDnu78Ko)The `require` function given [earlier in this chapter](https://eloquentjavascript.net/10_modules.html#require) supports this type of dependency cycle. Can you see how it handles cycles? What would go wrong when a module in a cycle _does_ replace its default `exports` object?
