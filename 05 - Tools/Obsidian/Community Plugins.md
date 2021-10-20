
# Obsidian

## Community Plugins

### Aesthetics:

#### Better Word Count

#### Contextual Typography
Reduces spaces between headers in preview mode, for more readable typography. (JS API )

#### Collapse All
Button to collapse all expanded folders.

#### Daily Stats
Shows word count in bottom right of screen, and contains a histogram of word count contributions. 

#### Editor Syntax Highlight
Show code syntax highlighting

#### Typewriter Scroll
Keeps current line centered in the editor.

#### Reading Time
Show's approximate reading time

#### Remember Cursor Position
Saves cursor position for note where it was last worked on. 

#### System Dark Mode
Automatically switches settings via OS settings. 

#### Zoom
Zoom into headings and lists via folding and top level heading navigation. 

| Command                      | Default hotkey (Windows/Linux) | Default hotkey (MacOS) |
| ---------------------------- | ------------------------------ | ---------------------- |
| Zoom in                      | Ctrl.                          | Command.               |
| Zoom out the entire document | CtrlShift.                     | CommandShift.          |



### Navigation

#### Autocomplete

Trigger On/Off: `ctrl+space`

Change suggestion with `Ctrl-n/p` or `up/down arrows` and select with `enter/tab`

#### Checklist

Combines check lists across documents. Anything you tag with #todo will appear.

#### Hotkeys++

| Hotkey           | Action                                      |
| ---------------- | ------------------------------------------- |
| Ctrl + M         | Toggle between checkmarks.                  |
| Ctrl + Shift + M | Toggle between ordered and unordered lists. |
| Ctrl + <         | Toggle blockquotes.                         |
| Ctrl + Shift + 1 | Toggle embeds for internal links.           |
| Blank by default | Duplicate current line or selected lines    |
| Blank by default | Insert line below/above current line        |
| Blank by default | clear current line                          |

#### Jump to Link

- Open command pallete (`Ctrl+P`), find and choose `Jump to link` command
- You can use hotkey (`Ctrl + '` by default)

- Use the command pallete, or press the hotkey (`Ctrl + ;` by default) to instantly jump to any word on the page!
- Custom RegEx can be configured to user preference



#### macOS Keyboard Navigation

Allows navigation by alt+up/down. 

#### Maximize Active Pane

Toggles full screen of current pane via ctrl+shift+x

#### Obsidian Tabs

Opening a document in a new pane (ctrl+click on a document in the file explorer) instead activates tabbed view. One document is visible in the viewer, and the active document can be switched by selecting another tab.

#### Outliner

Allows you to easily move list and sublist items around a list easier. Similar to Roam Research Workflow.

| Command                       | Default hotkey (Windows/Linux) | Default hotkey (MacOS) |
| ----------------------------- | ------------------------------ | ---------------------- |
| Move list and sublists up     | Ctrl Shift ↑                   | Command Shift ↑        |
| Move list and sublists down   | Ctrl Shift ↓                   | Command Shift ↓        |
| Indent the list and sublists  | Tab                            | Tab                    |
| Outdent the list and sublists | ShiftTab                       | ShiftTab               |

#### Sliding Panes

Instead of shrinking the workspace to fit panels, the panels will remain a fixed
width (but resizable) and stack so you can scroll between them. 

- **Toggle Sliding Panes** - Turns sliding panes on or off globally *(also available via command/hotkey)*
- **Leaf Auto Width** - If on, the width of the pane should fill the available space *(also available via command/hotkey)*
- **Leaf Width** - The default width of a single pane
- **Toggle rotated headers** - Rotates headers to use as spines *(also available via command/hotkey)*
- **Swap rotated header direction** - Swaps the direction of rotated headers *(also available via command/hotkey)*
- **Toggle stacking** - Panes will stack up to the left and right *(also available via command/hotkey)*
- **Spine Width** - The width of the rotated header (or gap) for stacking

#### Quick Switcher

#TODO:

#### QuickAdd

Add new pages and templates. 





### Organizational

#### Kanban 

Features:
- Search Cmd/Ctrl F
- You can archive notes 

Dates can be added with \@
Times can be added with \@\@

You can either create a new kanban board or create a note from an empty file. 

You can also create new notes from cards as you work by right clicking, which will then place a new note in the note folder with the note template that is selected. This can be useful for deeper tracking and documentation of issues. 



#### Rollover Daily Todo's 
Pushes any unchecked todo's from previous day into today's note. 

#### Incremental Writing

Incrementally review notes and blocks over time. It tracks the priority, A-factor (spacing), amount refactoring, and last repetition. 

1. Extraction: Add and prioritize extracted writings that contain the most valuable information in a learning queue as independent information. This floats freely for you to later use. Information that is highly applicable should be condensed down into flashcard formats. 
2. Creation.



A-factor, controls the spacing. 



Refactor words as much as possible. Replace words, make more consise, and of course expand upon in your words. , make boats





| Command                                | Default hotkey (Windows/Linux) |                                                              |
| -------------------------------------- | ------------------------------ | ------------------------------------------------------------ |
| Add Block to Queue                     | Ctrl.                          | supports multiple queues that you can switch between using a fuzzy search menu |
| Add links within note to queue         | CtrlShift.                     |                                                              |
| Add note to queue through fuzzy finder |                                |                                                              |
| Add note to queue                      |                                |                                                              |
| Current repitition                     |                                |                                                              |
| Dismiss current repitition             |                                |                                                              |
| Load a queue                           |                                |                                                              |
| Next repitition                        |                                |                                                              |
| Open queue in current pane             |                                |                                                              |
| Open queue in new pane                 |                                |                                                              |

There are currently 10 hotkey / command palette commands and a couple of buttons and context menu commands.

1. Load a queue: The plugin supports multiple queues that you can switch between using a fuzzy search menu. The fuzzy menu searches in the queue folder specified in the settings.
2. Open queue in current pane: Open the currently loaded queue in the current pane. Toggle to preview mode to see it formatted correctly.
3. Open queue in new pane: Open the currently loaded queue in a new pane. Toggle to preview mode to see it formatted correctly.
4. Add note to queue: Adds the current note to the current incremental writing queue.
5. Add block to queue: Adds the current block to the current incremental writing queue.
6. Current repetition: Goes to the current repetition for the loaded queue.
7. Next repetition: Goes to the next repetition for the loaded queue.
8. Dismiss current repetition: Dismiss the current repetition from the queue. This note or block will not show up again for review.
9. Add links within the current note to a queue: Add any links to other notes within the current note to a queue.
10. Add note to queue through a fuzzy finder



#### Journey

Understand path between links

#TODO:

#### Obsidian to Anki

In Anki, navigate to Tools->Addons->AnkiConnect->Config, and change it to look like this:

```
{
    "apiKey": null,
    "apiLogPath": null,
    "webBindAddress": "127.0.0.1",
    "webBindPort": 8765,
    "webCorsOrigin": "http://localhost",
    "webCorsOriginList": [
        "http://localhost",
        "app://obsidian.md"
    ]
}
```

Restart Anki to apply the above changes. With Anki running in the background, load the plugin. This will generate the plugin settings.

## Features

Current features (check out the  [Wiki](https://github.com/Pseudonium/Obsidian_to_Anki/wiki) for more details):

- **Custom note types** - You're not limited to the 6 built-in note types of Anki.

- **Updating notes from file** - Your text files are the canonical source of the notes.

- **Tags**, including **tags for an entire file**.

- **Adding to user-specified deck** on a *per-file* basis.

- **Markdown formatting**.

- **Math formatting**.

- **Embedded images**. GIFs should work too.

- **Audio**.

- **Auto-deleting notes from the file**.

- **Reading from all files in a directory automatically** - recursively too!

- **Inline Notes** - Shorter syntax for typing out notes on a single line.

- **Easy cloze formatting** - A more compact syntax to do Cloze text

- **Frozen Fields**

- **Obsidian integration** - A link to the file that made the flashcard, full link and image embed support.

- **Custom syntax**

  RemNote single-line style.

  ```
  This is how to use::Remnote single-line style
  ```

  Header paragraph style.

  ```
  # Style
  This style is suitable for having the header as the front, and the answer as the back
  ```

  Question answer style.

  ```
  Q: How do you use this style?
  A: Just like this.
  ```

  Neuracache #flashcard style.

  ```
  In Neuracache style, to make a flashcard you do #flashcard
  The next lines then become the back of the flashcard
  ```

  Ruled style

  ```
  How do you use ruled style?
  ---
  You need at least three '-' between the front and back of the card.
  ```

  Markdown table style

  ```
  | Why might this style be useful? |
  | ------ |
  | It looks nice when rendered as HTML in a markdown editor. |
  ```

  Cloze paragraph style

  ```
  The idea of {cloze paragraph style} is to be able to recognise any paragraphs that contain {cloze deletions}.
  ```

  Note that **all custom syntax is off by default**, and must be programmed into the script via the config file - see the Wiki for more details.

#### Periodic Notes

Manage, daily, weekly and monthly notes. Useful for development.

#TODO:

#### Spaced Repetition

- Flashcards
  - [Decks](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Decks) (Using Obsidian's hierarchical tags or folder structure)
  - [Remnote single-line style](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Flashcard-Types#single-line-remnote-style) (`Question::Answer`)
  - [Multi-line style](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Flashcard-Types#multi-line) (Separated by `?`)
  - [Cloze cards](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Flashcard-Types#cloze-cards) (`==highlight==` your cloze deletions!)
  - [Card context - automatic titles based on headings](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Reviewing-flashcards#context) (i.e. `Note title > Heading 1 > Subheading`)
  - Rich text support in flashcards (inherited from Obsidian)
    - Images
    - LaTeX
    - Code syntax highlighting
    - Footnotes
- Notes
  - [Reviewing entire notes](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Notes)
  - Possible use case: [Incremental writing](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Incremental-writing)
- [Statistics](https://github.com/st3v3nmw/obsidian-spaced-repetition/wiki/Statistics)











### Markdown Editing

#### Admonition

Block Styled content for documentation.

~~~markdown
```ad-note
title: Title
collapse: open (optional)
color: 200, 200, 200
icon: triforce // Icon from FontAwesome

This is example text

````ad-warning
This is a nested admonition
````
```
~~~

| Type     | Aliases                     |
| -------- | --------------------------- |
| note     | note, seealso               |
| abstract | abstract, summary, tldr     |
| info     | info, todo                  |
| tip      | tip, hint, important        |
| success  | success, check, done        |
| question | question, help, faq         |
| warning  | warning, caution, attention |
| failure  | failure, fail, missing      |
| danger   | danger, error               |
| bug      | bug                         |
| example  | example                     |
| quote    | quote, cite                 |

See [this](https://squidfunk.github.io/mkdocs-material/reference/admonitions/) for a reference of what these admonitions look like. Custom ones can be made in the documentation.

#### Advanced Tables

- Auto formatting
- Excel-like table navigation (tab/enter between cells and rows)
- [Spreadsheet formulas!](https://github.com/tgrosinger/advanced-tables-obsidian/blob/main/docs/help.md#using-formulas-in-markdown-tables)
- Add, remove, and move columns and rows
- Set column alignment (left, center, right)
- Sort rows by a specified column
- Export to CSV
- Works on Obsidian Mobile (See notes below)
- To include formulas refer to [Help Docs](https://github.com/tgrosinger/advanced-tables-obsidian/blob/main/docs/help.md).

| Hotkey           | Action                      |
| ---------------- | --------------------------- |
| Tab              | Next Cell                   |
| Shift + Tab      | Previous Cell               |
| Enter            | Next Row                    |
| Ctrl + Shift + D | Open table controls sidebar |

#### Extract URL Content

Operates in 2 modes.

1. **Selection** - If you select a URL in the document and execute these commands it will replace the selection with the markdown content.
2. **Document** - If you add front mater with the key of `link` to your document then it is treated as a linked document. Then calling extract will look for the link and replace the content of the document with the extracted content.

It can

- **Extract**: Replace url or document with readable markdown extracted from the sites html content
- **Title Only**: Replace url or document with a markdown anchor with the title extracted from the page content
- **Import from Clipboard**: Extract content from url that is found in your clipboard and dump it at your cursor

#### Find Unlinked Files

Call the command `Find unlinked files` and the file `Find unlinked files plugin output.md` will be created in your vault root and opened in a new pane.

#### Markdown Formatting Assistant

The Side Panel can be opened by the Ribbon Icon on the left side. If you changed the side (left or right) of the panel in the settings, just hit this butten/icon again and it will reload on the right side.

- Markdown Section
- HTML Section
- Latex Section
- Greek Letters Section

##### Command Language

With the command language the speed of the workflow can be specifically improved. By typing the trigger char (by default `\`) the commands will be activated and a suggestion window opens. It shows maximal 5 suggestions, which can be improved by adding more letters. The selected suggestion can be changed with the arrow keys and be activated with the enter key.

##### Color Picker

###### Select a color

The color picker provides an easy and fast workflow to work with colors. If you pick a color with the `Select a Color` button and leave the window (by clicking outside the color picker), the selected color will be inserted at the current courser position. In addition, it will be copied to the clipboard.

###### Color History

Furthermore, the color picker saves the history of the last 10 used colors.

###### Saved Colors

To Save the current color even if obsidian will be closed, just click the `Save Color` button.

###### Sort saved Colors

All saved colors can be sorted via drop a catch.

###### Delete a Color

To delete a saved or last used color just click it with the right mouse button.

###### Additonal Formats

For a even easier handling you can select additional options to what should be added to the color.

###### Options

- Add "color: {your color}"
  - ex. `color: #ffffff`
- Add "background-color: {your color}
  - ex. `background-color: #ffffff`
- Add tag: "style={your color}
  - This option is only helpful, if you also select one of both of the other options like:
  - ex. `style="background-color: #ff0000"`

#### Markdown Prettifier

The default hotkey is `Ctrl+Alt+L`.

- Hashtags janitor

```markdown
A #new and #exciting paragraph!
```

```markdown
---
tags:
    - '#new'
    - '#exciting'
---

A #new and #exciting paragraph!
```

- Autolink literals

- Normalizes ordered lists.

- Normalizes table formatting.

#### Note Refactor

| Hotkey               | Action                                                       |
| -------------------- | ------------------------------------------------------------ |
| Ctrl/Cmd + Shift + N | **Extract selection to new note - first line as filename:** Copy selection into new note with the first line as the file name and replace with a link. |
| Ctrl/Cmd + Shift + C | **Extract selection to new note - content only:** Copy selection into new note, prompt for a file name and replace with a link. |

`Default location for new notes` setting.

3 options available:

1. Vault folder
2. Same folder as current file
3. Specified folder

A folder path set as `Zettels/{{date:YYYY}}/{{date:MMMM}}` will add a new file to the following folder structure:

##### Commands

###### Note Splitting

Splitting the current note from the current line into a new note or append to an existing one.

###### Split note here - current line as note file name

This command splits the current note into a new note from the current line using the current line as the file name for the new note.

###### Split note here - content only

This command splits the current note into a new note, or append to an existing one, from the current line. The user is prompted to enter a file name for the new note.

###### Split note by headings - H1, H2, H3

This command splits the current note into a new note for every heading at the level selected (H1, H2 or H3) using the heading as the file name for each new note.

###### Extract Selection

Extracting the current selection into a new note or append to an existing one.

###### Extract selection to new note or append to existing note - first line as filename

This command copies the selected text into the content of a new note using the first line as the file name for the new note or append to an existing one.

###### Extract selection to new note or append to existing note - content only

This command only copies the selected text into the content of a new note or append to an existing one. The user is prompted to enter a file name for the new note.

###### Extract selection to new note - prefix only as file name

This command only copies the selected text into the content of a new note or append to an existing one. The filename is automatically generated based on the value of **File name prefix** setting. New note is created silently and will not be shown in a new pane.

#### PDF Highlights

Exports Highlights from a pdf.

Optional Settings

- Include page number (Default: off)
- Include highlight color (Default: off)
- Create links (Default: off)

#### PDF to Markdown

Drag your PDF into Obsidian, Open the PDF within Obsidian, Make sure the pane with your PDF is focused, Click the "PDF to Markdown" button in the sidebar.

Weirdly, sometimes, new lines of text had a space infront of them. Such as: - Some text

...which resulted in Obisidian treating it as a sub-block of the preceding line.

To remove the space for those lines, I used a regular expression search-and-replace:

1. In "Find in current buffer" activate "Regex Search" (The `.*` icon)
2. Enter `^([ ]|\t)+` into the search field
3. Use the button "Replace" or "Replace All" to remove the space







### Future

#### Day Planner

Advanced day planner and displays it as a calendar or gant chart. Would be useful in more specific development plans. 

#### Music Notation

music-abc.js plugin

#### PlantUML

Easy UML diagrams

#### Buttons

Create buttons to run commands, open links, templates, etc...

#### Review

REview Notes

#### Templater

Creatue and use templates

#### Timeline: Create Timelines

#### Obsidian Git

May be useful but pushing via git app is simple for now.

#### VimRC Support

