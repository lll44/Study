# How to read and decipher a codebase

In the beginning it's recommended to start with small projects. ie.
- Read code that you rely on

This could be a plugin that you find useful. Public API's have a low barrier of entry. 

- Read code that impresses you, particularly if it's open source.
- Read code written by somebody you respect
- Read code that you can actually grok

Consider diving into a large project like Ruby on Rails, Drupal, or jQuery. I suggest avoiding projects like these for now unless you are an experienced code reader. Large projects have a lot more moving pieces, and you may end up struggling too much with the concepts to learn anything of immediate value

## HOW TO READ
### See the big picture
I suggest your first step is to wrap your head around the project’s structure. This is a variable amount of work depending on the size of the codebase you’ve chosen, but anything larger than one file will require a little bit of time.

First, note the file structure. This step is aided by an editor that has a folder hierarchy. Find out which files include/require/load other files, where the bulk of the code is, the namespaces used if any, and things of this nature. Once you’ve got the big picture you’ll be ready to dig into the details.

### Document your findings
Reading code should not be a passive activity. I encourage you to add comments as you go, documenting your assumptions and your conclusions as you begin to understand the program flow. When you first get started your comments will probably look something like:

// I think this function is called after 'initialize'
// What does this equation even do?
// Pretty sure this variable loses scope after line 17

As your understanding progresses you can remove the little breadcrumb comments you left yourself and perhaps write more meaningful and authoritative comments that could possibly be committed back to the project

### Use the tests, Luke
Tests are a great place to start whenever you read somebody else’s code because they document what the code is supposed to accomplish. Some tests are more informative than others, but no matter how well written, you’ll often find the programmer’s intent in the tests much more easily than you’ll find it in the implementation. While you’re reading, try to get the test suite to run successfully. This will make sure your development environment is configured properly and will make you more confident when making changes.

### Execute, change stuff, execute
You’ll really start to understand things once you’ve broken everything and put it back together again. Remember those tests you got passing? Make them fail, add some more, or try changing the implementation without breaking them. Try adding a small feature that you think is cool, or setup project-wide logging so you can print output at various stages of the code. Is this still reading?

### Rinse and repeat
Once you finish reading one codebase, pick another one and start the process over again. The more code you read, the better you get at reading it and the more you get out of it in less time. I think you’ll find that the ROI increases quite quickly and that it’s actually a very enjoyable way to learn.
  
https://changelog.com/posts/one-sure-fire-way-to-improve-your-coding