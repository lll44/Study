# Obsidian Flashcards

## Table of Contents

```toc

```

## Installation

1. Install this plugin on Obsidian:

- Open Settings > Community plugins
    - Make sure Safe mode is off
    - Click Browse community plugins
    - Search for "**Flashcards**"
    - Click Install
    - Once installed, close the community plugins window and activate the newly installed plugin
	
  2. Install [AnkiConnect](https://ankiweb.net/shared/info/2055492159) on Anki

    Tools > Add-ons -> Get Add-ons...
    Paste the code **2055492159** > Ok
    Select the plugin > Config > Paste the configuration below
  3. Open the settings of the plugin, and while Anki is opened press "**Grant Permission**"

## Requirements

First, Anki and [AnkiConnect](https://ankiweb.net/shared/info/2055492159) should be running and configured properly, as explained [here](https://github.com/reuseman/flashcards-obsidian/#how-to-install).

## Write Cards

Hashtags is the way to define them and can be customized in the settings, but the default one is `#card`. Here there is an example file ([Preview](https://github.com/reuseman/flashcards-obsidian/blob/main/docs/demo.md) | [Markdown](https://raw.githubusercontent.com/reuseman/flashcards-obsidian/main/docs/demo.md)).

### #card Hashtag

To mark a line or a heading as the **front** of a card just write a **#card** tag after it. On a new line write the **back** of the card. And remember to space things out!

    

# This could be a title 
## This is the front #card 

This is the back of the card. This line will not be part of it, because there is an empty line above. 

### This is a normal and reversed card  #card-reverse Which means that two cards will be generated on Anki. ### Also revers #card/reverse But this time it uses Obsidian hierarchical tags. ### This could be another question #card But this time without the heading. ## This is another way to define the front #card This style is usefull to avoid the hashtags when referencing in Obsidian 

### Inline Style with ::

    

    # This could be a title All of these works: My question::My answer My question:: My answer My question ::My Answer My question :: My answer You can even use it in lists: - My question:: My answer

#### Reverse

To create a reversed card with the inline style just use `:::`.

    

    All of these works: My question:::My answer My question::: My answer My question :::My Answer My question ::: My answer

### Cloze

    

    This is a way to define a ==cloze== by using the Obsidian highlight syntax in order to avoid making notes dirty. The alternative is this type of {cloze} that is totally equal to {1:cloze}. With the number you can specify the order {2:later cloze}. 

### Spaced with #card-spaced Hashtag

    

    This could be a beautifull quote that you want to see once in a while #card-spaced

Optionally, you can consider the `#card/spaced` alternative to use obsidian hierarchical tags.

## Generate Cards on Anki

  1. In Obsidian, open the file where you have the flashcards
  2. Then to insert/update/delete just run inside Obsidian the command `Ctrl+p` and execute the command `Flashcards: generate for the current file`

### Insert

Write the cards and just run the command above. The insertion operation will add cards on Anki. While, in Obsidian it will add an ID to keep track of them.

### Update

Just edit the card in Obsidian, and run the command above.  

**NOTE: Make certain that when you want to update the BROWSE window of Anki is closed.** Unfortunately, this is a bug that is not my under control, but it's a problem tied up with the Anki APIs I am using.

### Delete

Delete the content of the card in Obsidian, but without deleting the ID. The plugin will take care of it. So for example

    

    ## This is the front of the card to delete #card This is the back of the card to delete. ^1607361487244

This is what you should leave:

    

    ^1607361487244

## Features

### Context-aware Mode

To make sense of notes, they should talk about a specific topic, so if you have two headings of level 1 (# heading), probably you should have two notes that talks about those topics. Moreover, the note itself is written with a tree-structure and then connected in a graph way. Based on this hypothesis, the context-aware mode creates the context in the **front** of the card. Where the context the outline of the headings in a tree structure. The demo shows is in action. This helps you out:

  * **during review**, because the front will be **unique** and this helps the memory in reaching for the correct answer. If the front is repeated for multiple cards, it's impossible to remember what's in the back, it's pure randomness.
  * **during writing**, because you can write following the same structure for different topics, and cards will always be **unique**. So you do not have to think too much about the writing itself.

**Example:**
    

    # Computer Science ## Languages #card Stuff ### OOP #card Stuff #### C++ #card Stuff #### Java #card Answer ### Functional Stuff

**Generated card for the Java heading**

  * With context-aware mode on 🟢
    
    Front: Computer Science > Languages > OOP > Java Back: Answer

  * With context-aware mode off 🔴
    
    Front: Java Back: Answer

### Deck

To define in which deck in Anki the cards should go, write the name of the deck in the [front matter](https://publish.obsidian.md/help/Advanced+topics/YAML+front+matter). You can even specify sub decks by using two colons, `My Deck Name::Sub deck`. If you want to change the deck after the cards have been generated, just change the deck name.

    

    --- cards-deck: My Deck Name --- ## This is the front #card This is the back of the card.

#### Folder-based Deck Name

This should be enabled in the settings. `Default: On`. It enables to automatically create cards into a deck that follows the hierarchical paths of where the note is. For example, if you have a file in the path `food/italian/cavatelli.md`, then the cards will be generated in a deck named `food::italian`.

### Tags

To define the tags that should be used in Anki, there are two approaches.

  * Global tags: takes all the tags specified after any line that starts with `tags:`. To hide them in the preview, just put them in the [front matter](https://publish.obsidian.md/help/Advanced+topics/YAML+front+matter) of Obsidian.
  * Local tags: takes the tag after the #card tag.
    
    --- tags: global-tag1, global-tag2 --- ## This is the front #card #my-local-tag This is the back of the card.

Global tags can even be defined in this manner:

    

    tags: global-tag1, #global-tag2, [[global-tag3]]

or without the comma:

    

    tags: global-tag1 #global-tag2 [[global-tag3]]

### Images

To add images, just [embed](https://publish.obsidian.md/help/How+to/Embed+files) them normally.

### Code Highlight Support

This should be enabled in the settings. `Default: Off`

### Source Support

This should be enabled in the settings. `Default: Off`  

Note that whenever enabled, the previous cards created without the source support cannot be updated, unless you switch back. My suggestion is to stick with one mode.

### LaTeX Support

Just write your latex code by using the Obsidian syntax:

    

    This is an example $3+4$ $$50+2$$

## Troubleshooting

If you have some problem in the configuration step with Anki, open Anki annd `Tools -> Add-ons -> AnkiConnect -> Config`, paste the following:

    

    { "apiKey": null, "apiLogPath": null, "webBindAddress": "127.0.0.1", "webBindPort": 8765, "webCorsOrigin": "[http://localhost](http://localhost/)", "webCorsOriginList": [ "[http://localhost](http://localhost/)", "app://obsidian.md" ] } 

## Customization

To have coloured tags for the flashcards one, you can use this in `obsidian.css`. It's not added directly in the plugin, to do not mess with your styles 😊.

    

    .tag { color: var(--text-normal); background-color: var(--text-accent); border: none; font-size: 11px; padding: 1px 8px; text-align: center; text-decoration: none; margin: 0px 0px; cursor: pointer; border-radius: 14px; display: inline; vertical-align: middle; } .tag:hover { color: var(--text-normal); background-color: var(--text-accent-hover); } .tag[href="#card"] { background-color: #821515; } .tag[href="#card-reverse"] { background-color: #821515; }

  *

  

