```
Source: https://learn.shayhowe.com/html-css/writing-your-best-code/
Tags: 
Last-Updated:
```

###### Lesson 12

# Writing Your Best Code

####  In this Lesson 12

###### HTML

  * [HTML Coding Practices](https://learn.shayhowe.com/html-css/writing-your-best-code/#html-coding-practices)
  * [Additional Resources](https://learn.shayhowe.com/html-css/writing-your-best-code/#additional-resources)

###### CSS

  * [CSS Coding Practices](https://learn.shayhowe.com/html-css/writing-your-best-code/#css-coding-practices)

###### Share

  * [ Share on Twitter ](https://learn.shayhowe.com/html-css/writing-your-best-code/#)
  * [ Share on Facebook ](https://learn.shayhowe.com/html-css/writing-your-best-code/#)
  * [ Share on Google+ ](https://learn.shayhowe.com/html-css/writing-your-best-code/#)

There’s a lot to learn—different elements, attributes, properties, values, and more—in order to write HTML and CSS. Every lesson until this point has had the primary objective of explaining these various components of HTML and CSS, in hopes of helping you to understand the core fundamentals of both languages. This lesson takes a step back and looks at a more abstract picture of HTML and CSS.

More specifically, this lesson focuses on the best coding practices for both HTML and CSS. These coding practices serve as an overarching framework for writing HTML and CSS. They apply to every lesson and should always be kept in mind when programming.

When you’re reviewing these best practices think about how they may be used in other areas or programming languages, too. For example, the use of comments to organize code (as we cover in this lesson) is beneficial in all programming languages. Keep an open mindset and consider how you can fully utilize each practice.

## HTML Coding Practices

A lot of coding best practices emphasize keeping code lean and well organized. The general practices within HTML are no different. The goal is to write well-structured and standards-compliant markup. The guidelines described here provide a brief introduction to HTML coding practices; this is by no means an exhaustive list.

### Write Standards-Compliant Markup

HTML, by nature, is a forgiving language that allows poor code to execute and render to varying levels of accuracy. Successful rendering, however, does not mean that our code is semantically correct or guarantee that it will validate as standards compliant. In addition, poor code is unpredictable, and you can’t be certain what you’re going to get when it renders. We have to pay close attention when writing HTML and be sure to nest and close all elements correctly, to use IDs and classes appropriately, and to always validate our code.

The code that follows has multiple errors, including using the `intro` ID attribute value multiple times when it should be a unique value, closing the `<p>` and `<strong>` elements in the wrong order within the first paragraph, and not closing the `<p>` element at all in the second paragraph.

###### Bad Code
    
    1 2 3
    
    <p id="intro">New items on the menu today include <strong>caramel apple cider and breakfast crepes</p>.</strong> <p id="intro">The caramel apple cider is delicious. 

`

###### Good Code
    
    1 2 3
    
    <p class="intro">New items on the menu today include <strong>caramel apple cider and breakfast crepes</strong>.</p> <p class="intro">The caramel apple cider is delicious.</p> 

`

### Make Use of Semantic Elements

The library of elements in HTML is fairly large, with well over 100 elements available for use. Deciding which elements to use to describe different content may be difficult, but these elements are the backbone of semantics. We need to research and double-check our code to ensure we are using the proper semantic elements. Users will thank us in the long run for building a more accessible website, and your HTML will arguably be easier to style. If you are ever unsure of your code, find a friend to help out and perform routine code reviews.

Here the HTML doesn’t use the proper heading and paragraph elements; instead, it uses meaningless elements to style and group content.

###### Bad Code
    
    1 2 3 4 5
    
    <span class="heading"><strong>Welcome Back</span></strong> <br><br> It has been a while. What have you been up to lately? <br><br> 

`

###### Good Code
    
    1 2 3
    
    <h1>Welcome Back</h1> <p>It has been a while. What have you been up to lately?</p> 

`

### Use the Proper Document Structure

As previously mentioned, HTML is a forgiving language and, therefore, pages will render without the use of the `<!DOCTYPE html>` doctype or `<html>`, `<head>`, and `<body>` elements. Without a doctype and these structural elements, pages will not render properly in every browser.

We must always be sure to the use proper document structure, including the `<!DOCTYPE html>` doctype, and the `<html>`, `<head>`, and `<body>` elements. Doing so keeps our pages standards compliant and fully semantic, and helps guarantee they will be rendered as we wish.

###### Bad Code
    
    1 2 3 4 5
    
    <html> <h1>Hello World</h1> <p>This is a web page.</p> </html> 

`

###### Good Code
    
    1 2 3 4 5 6 7 8 9 10 11
    
    <!DOCTYPE html> <html> <head> <title>Hello World</title> </head> <body> <h1>Hello World</h1> <p>This is a web page.</p> </body> </html> 

`

### Keep the Syntax Organized

As pages grow, managing HTML can become quite a task. Thankfully there are a few quick rules that can help us keep our syntax clean and organized. These include the following:

  * Use lowercase letters within element names, attributes, and values
  * Indent nested elements
  * Strictly use double quotes, not single or completely omitted quotes
  * Remove the forward slash at the end of self-closing elements
  * Omit the values on Boolean attributes

Observing these rules will help keep our code neat and legible. Looking at the two sets of HTML here, the good code is easier to digest and understand.

###### Bad Code
    
    1 2 3 4 5 6 7 8 9 10
    
    <Aside> <h3>Chicago</h3> <H5 HIDDEN='HIDDEN'>City in Illinois</H5> <img src=chicago.jpg alt="Chicago, the third most populous city in the United States" /> <ul> <li>234 square miles</li> <li>2.715 million residents</li> </ul> </ASIDE> 

`

###### Good Code
    
    1 2 3 4 5 6 7 8 9 10
    
    <aside> <h3>Chicago</h3> <h5 hidden>City in Illinois</h5> <img src="chicago.jpg" alt="Chicago, the third most populous city in the United States"> <ul> <li>234 square miles</li> <li>2.715 million residents</li> </ul> </aside> 

`

### Use Practical ID & Class Values

Creating ID and class values can be one of the more difficult parts of writing HTML. These values need to be practical, relating to the content itself, not the style of the content. Using a value of `red` to describe red text isn’t ideal, as it describes the presentation of the content. Should the style of the text ever need to be changed to blue, not only does the CSS have to be changed, but so does the HTML in every instance where the class `red` exists.

The HTML here assumes that the alert message will be red. However, should the style of the alert change to orange the class name of `red` will no longer make sense and will likely cause confusion.

###### Bad Code
    
    1 2
    
    <p class="red">Error! Please try again.</p> 

`

###### Good Code
    
    1 2
    
    <p class="alert">Error! Please try again.</p> 

`

### Use the Alternative Text Attribute on Images

Images should always include the `alt` attribute. Screen readers and other accessibility software rely on the `alt` attribute to provide context for images.

The `alt` attribute value should be very descriptive of what the image contains. If the image doesn’t contain anything of relevance, the `alt` attribute should still be included; however, the value should be left blank so that screen readers will ignore it rather than read the name of the image file.

Additionally, if an image doesn’t have a meaningful value—perhaps it is part of the user interface, for example—it should be included as a CSS background image if at all possible, not as an `<img>` element.

###### Bad Code
    
    1 2
    
    <img src="puppy.jpg"> 

`

###### Good Code
    
    1 2
    
    <img src="puppy.jpg" alt="A beautiful, two-year-old hound mix puppy"> 

`

### Separate Content from Style

Never, ever, use inline styles within HTML. Doing so creates pages that take longer to load, are difficult to maintain, and cause headaches for designers and developers. Instead, use external style sheets, using classes to target elements and apply styles as necessary.

Here, any desired changes to styles within the bad code must be made in the HTML. Consequently, these styles cannot be reused, and the consistency of the styles will likely suffer.

###### Bad Code
    
    1 2
    
    <p style="color: #393; font-size: 24px;">Thank you!</p> 

`

###### Good Code
    
    1 2
    
    <p class="alert-success">Thank you!</p> 

`

### Avoid a Case of “Divitis”

When writing HTML, it is easy to get carried away adding a `<div>` element here and a `<div>` element there to build out any necessary styles. While this works, it can add quite a bit of bloat to a page, and before too long we’re not sure what each `<div>` element does.

We need to do our best to keep our code lean and to reduce markup, tying multiple styles to a single element where possible. Additionally, we should use the HTML5 structural elements where suitable.

###### Bad Code
    
    1 2 3 4 5 6
    
    <div class="container"> <div class="article"> <div class="headline">Headlines Across the World</div> </div> </div> 

`

###### Good Code
    
    1 2 3 4 5 6
    
    <div class="container"> <article> <h1>Headlines Across the World</h1> </article> </div> 

`

### Continually Refactor Code

Over time websites and code bases continue to evolve and grow, leaving behind quite a bit of cruft. Remember to remove old code and styles as necessary when editing a page. Let’s also take the time to evaluate and refactor our code after we write it, looking for ways to condense it and make it more manageable.

## CSS Coding Practices

Similar to those for HTML, the coding practices for CSS focus on keeping code lean and well organized. CSS also has some additional principles regarding how to work with some of the intricacies of the language.

### Organize Code with Comments

CSS files can become quite extensive, spanning hundreds of lines. These large files can make finding and editing our styles nearly impossible. Let’s keep our styles organized in logical groups. Then, before each group, let’s provide a comment noting what the following styles pertain to.

Should we wish, we can also use comments to build a table of contents at the top of our file. Doing so reminds us—and others—exactly what is contained within the file and where the styles are located.

###### Bad Code
    
    1 2 3 4
    
    header { ... } article { ... } .btn { ... } 

`

###### Good Code
    
    1 2 3 4 5 6 7 8 9
    
    /* Primary header */ header { ... } /* Featured article */ article { ... } /* Buttons */ .btn { ... } 

`

### Write CSS Using Multiple Lines & Spaces

When writing CSS, it is important to place each selector and declaration on a new line. Then, within each selector we’ll want to indent our declarations.

After a selector and before the first declaration comes the opening curly bracket, `{`, which should have a space before it. Within a declaration, we need to put a space after the colon, `:`, that follows a property and end each declaration with a semicolon, `;`.

Doing so makes the code easy to read as well as edit. When all of the code is piled into a single line without spaces, it’s hard to scan and to make changes.

###### Bad Code
    
    1 2
    
    a,.btn{background:#aaa;color:#f60;font-size:18px;padding:6px;} 

`

###### GOOD CODE
    
    1 2 3 4 5 6 7 8
    
    a, .btn { background: #aaa; color: #f60; font-size: 18px; padding: 6px; } 

`

#### Comments & Spacing

These two recommendations, organizing code with comments and using multiple lines and spaces, are not only applicable to CSS, but also to HTML or any other language. Overall we need to keep our code organized and well documented. If a specific part of our code is more complex, let’s explain how it works and what it applies to within comments. Doing so helps others working on the same code base, as well as ourselves when we revisit our own code down the road.

### Use Proper Class Names

Class names (or values) should be modular and should pertain to content within an element, not appearance, as much as possible. These values should be written in such a way that they resemble the syntax of the CSS language. Accordingly, class names should be all lowercase and should use hyphen delimiters.

###### Bad Code
    
    1 2
    
    .Red_Box { ... } 

`

###### Good Code
    
    1 2
    
    .alert-message { ... } 

`

### Build Proficient Selectors

CSS selectors can get out of control if they are not carefully maintained. They can easily become too long and too location specific.

The longer a selector is and the more prequalifiers it includes, the higher specificity it will contain. And the higher the specificity the more likely a selector is to break the CSS cascade and cause undesirable issues.

Also in line with keeping the specificity of our selectors as low as possible, let’s not use IDs within our selectors. IDs are overly specific, quickly raise the specificity of a selector, and quite often break the cascade within our CSS files. The cons far outweigh the pros with IDs, and we are wise to avoid them.

Let’s use shorter and primarily direct selectors. Nest them only two to three levels deep, and remove as many location-based qualifying selectors as possible.

###### Bad Code
    
    1 2 3
    
    #aside #featured ul.news li a { ... } #aside #featured ul.news li a em.special { ... } 

`

###### Good Code
    
    1 2 3
    
    .news a { ... } .news .special { ... } 

`

### Use Specific Classes When Necessary

There are times when a CSS selector is so long and specific that it no longer makes sense. It creates a performance lag and is strenuous to manage. In this case, using a class alone is advised. While applying a class to the targeted element may create more code within HTML, it will allow the code to render faster and will remove any managing obstacles.

For example, if an `<em>` element is nested within an `<h1>` element inside of an `<aside>` element, and all of that is nested within a `<section>` element, the selector might look something like aside h1 em. Should the `<em>` element ever be moved out of the `<h1>` element the styles will no longer apply. A better, more flexible selector would use a class, such as text-offset, to target the `<em>` element.

###### Bad Code
    
    1 2
    
    section aside h1 em { ... } 

`

###### Good Code
    
    1 2
    
    .text-offset { ... } 

`

### Use Shorthand Properties & Values

One feature of CSS is the ability to use shorthand properties and values. Most properties and values have acceptable shorthand alternatives. As an example, rather than using four different `margin`-based property and value declarations to set the margins around all four sides of an element, use one single `margin` property and value declaration that sets the values for all four sides at once. Using the shorthand alternative allows us to quickly set and identify styles.

When we’re only setting one value, though, shorthand alternatives should not be used. If a box only needs a bottom `margin`, use the `margin-bottom` property alone. Doing so ensures that other margin values will not be overwritten, and we can easily identify which side the `margin` is being applied to without much cognitive effort.

###### Bad Code
    
    1 2 3 4 5 6 7 8 9 10
    
    img { margin-top: 5px; margin-right: 10px; margin-bottom: 5px; margin-left: 10px; } button { padding: 0 0 0 20px; } 

`

###### Good Code
    
    1 2 3 4 5 6 7
    
    img { margin: 5px 10px; } button { padding-left: 20px; } 

`

### Use Shorthand Hexadecimal Color Values

When available, use the three-character shorthand hexadecimal color value, and always use lowercase characters within any hexadecimal color value. The idea, again, is to remain consistent, prevent confusion, and embrace the syntax of the language the code is being written in.

###### Bad Code
    
    1 2 3 4 5
    
    .module { background: #DDDDDD; color: #FF6600; } 

`

###### Good Code
    
    1 2 3 4 5
    
    .module { background: #ddd; color: #f60; } 

`

### Drop Units from Zero Values

One way to easily cut down on the amount of CSS we write is to remove the unit from any zero value. No matter which length unit is being used—pixels, percentages, em, and so forth—zero is always zero. Adding the unit is unnecessary and provides no additional value.

###### Bad Code
    
    1 2 3 4 5 6
    
    div { margin: 20px 0px; letter-spacing: 0%; padding: 0px 5px; } 

`

###### Good Code
    
    1 2 3 4 5 6
    
    div { margin: 20px 0; letter-spacing: 0; padding: 0 5px; } 

`

### Group & Align Vendor Prefixes

With CSS3, vendor prefixes gained some popularity, adding quite a bit of code to CSS files. The added work of using vendor prefixes is often worth the generated styles; however, they have to be kept organized. In keeping with the goal of writing code that is easy to read and modify, it’s best to group and indent individual vendor prefixes so that the property names stack vertically, as do their values.

Depending on where the vendor prefix is placed, on the property or the value, the alignment may vary. For example, the following good code keeps the `background` property aligned to the left, while the prefixed `linear-gradient()` functions are indented to keep their values vertically stacked. Then, the prefixed `box-sizing` property is indented as necessary to keep the `box-sizing` properties and values vertically stacked.

As always, the objective is to make the styles easier to read and to edit.

###### Bad Code
    
    1 2 3 4 5 6 7 8 9
    
    div { background: -webkit-linear-gradient(#a1d3b0, #f6f1d3); background: -moz-linear-gradient(#a1d3b0, #f6f1d3); background: linear-gradient(#a1d3b0, #f6f1d3); -webkit-box-sizing: border-box; -moz-box-sizing: border-box; box-sizing: border-box; } 

`

###### Good Code
    
    1 2 3 4 5 6 7 8 9
    
    div { background: -webkit-linear-gradient(#a1d3b0, #f6f1d3); background: -moz-linear-gradient(#a1d3b0, #f6f1d3); background: linear-gradient(#a1d3b0, #f6f1d3); -webkit-box-sizing: border-box; -moz-box-sizing: border-box; box-sizing: border-box; } 

`

#### Vendor Prefixes

When using vendor prefixes we need to make sure to place an unprefixed version of our property and value last, after any prefixed versions. Doing so ensures that browsers that support the unprefixed version will render that style according to its placement within the cascade, reading styles from the top of the file to the bottom.

The good news is that browsers are largely moving away from using vendor prefixes. Over time this will become less of a concern; however, for now we’re well advised to double-check which styles require a vendor prefix and to keep those prefixes organized.

### Modularize Styles for Reuse

CSS is built to allow styles to be reused, specifically with the use of classes. For this reason, styles assigned to a class should be modular and available to share across elements as necessary.

If a section of news is presented within a box that includes a border, background color, and other styles, the class of `news` might seem like a good option. However, those same styles may also need to be applied to a section of upcoming events. The class of `news` doesn’t fit in this case. A class of `feat-box` would make more sense and may be widely used across the entire website.

###### Bad Code
    
    1 2 3 4 5 6 7 8 9 10 11
    
    .news { background: #eee; border: 1px solid #ccc; border-radius: 6px; } .events { background: #eee; border: 1px solid #ccc; border-radius: 6px; } 

`

###### Good Code
    
    1 2 3 4 5 6
    
    .feat-box { background: #eee; border: 1px solid #ccc; border-radius: 6px; } 

`

## Additional Resources & Links

Every lesson has come with a few resources for additional learning and discovery. Outlined below is a longer list of resources, as well as beneficial links.

### HTML & CSS

  * [Mozilla Developer Network](https://developer.mozilla.org/en-US/) via Mozilla 
  * [Opera.Dev](https://dev.opera.com/) via Opera 
  * [HTML and CSS Tutorials](http://www.htmldog.com/) via HTML Dog 
  * [DevDocs](https://devdocs.io/) — Instant documentation search 

### Design Inspiration

  * [Dribbble](https://dribbble.com/)
  * [Pattern Tap](http://patterntap.com/)
  * [Premium Pixels](http://www.premiumpixels.com/)

### Frameworks & Style Guides

  * [Web Style Guide](http://webstyleguide.com/wsg3/index.html)
  * [Bootstrap](https://getbootstrap.com/)
  * [Foundation](http://foundation.zurb.com/)
  * [Skeleton Framework](http://getskeleton.com/)
  * [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.xml)
  * [GitHub Styleguide](https://github.com/styleguide/)

### Icons

  * [Helveticons](http://hlvticons.ch/) via Goodbye Horses 
  * [Ion Icons](http://ionicons.com/) via Ben Sperry 
  * [Fugue Icons](http://p.yusukekamiyamane.com/) via Yusuke Kamiyamane 
  * [famfamfam Silk Icons](http://www.famfamfam.com/lab/icons/silk/) via Mark James 
  * [Pictos](http://pictos.cc/) via Drew Wilson 
  * [Picons](http://picons.me/)
  * [The Noun Project](http://thenounproject.com/)

### Miscellaneous

  * [COLOURlovers](http://www.colourlovers.com/) — Color trends and palettes 
  * [ColorHexa](https://www.colorhexa.com/) — Color encyclopedia 
  * [Modernizr](http://modernizr.com/) — JavaScript feature detection library 
  * [jQuery](https://jquery.com/) — Feature-rich JavaScript library 
  * [Google Hosted Libraries](https://developers.google.com/speed/libraries/devguide) — Content distribution network for JavaScript libraries 
  * [Copy Paste Character](http://copypastecharacter.com/) — Copying the “hidden” characters 

## Summary

Hopefully the principles of writing beautiful HTML and CSS are starting to become clear here. While each language does have its own intricacies, the majority of these practices can be shared across the two languages—and many other computer languages.

Individually we need to do our best to uphold these practices, and when working on a team we need to do our best to help educate the team on these practices, too. Likewise, our teams may have valuable suggestions and practices that we should work together to follow.

To highlight some of the overarching themes of this lesson, our HTML and CSS should always

  * Be well organized, so that it is easy to read, edit, and maintain
  * Be modular and flexible, allowing us to reuse code and patterns as necessary
  * Look as if one person wrote it, even if several people contributed

These practices are only the beginning, and as the languages evolve and we write more and more HTML and CSS, we’ll develop new ones. It’s all part of the beauty of knowing HTML and CSS.

You’re now equipped with some very powerful knowledge about how to build websites with HTML and CSS, and I’m excited to see what you do with it. Keep me posted on how it goes, and happy building!
