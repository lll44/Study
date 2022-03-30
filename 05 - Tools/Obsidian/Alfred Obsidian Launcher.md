

# [Shimmering Obsidian - Alfred](https://github.com/chrisgrieser/shimmering-obsidian)


```toc 
style: bullet 
number min_depth: 1 
max_depth: 6 
```

## Search
Similar to built-in “QuickSwitch” feature, but can be triggered without Obsidian running.
`o`: Searches all notes, aliases, folders, and headings combined.
- `⌘ + ↵`: Open the file in a new pane.
- `⌥ + ↵`: Reveal the file in Finder.
- `fn + ↵`: Append the content to the selected note.
- `⌃ + ↵`: Copy the [Obsidian-URI to the selected file](https://help.obsidian.md/Advanced+topics/Using+obsidian+URI#Action+`hook-get-address`)
- `⇧ + ↵`: Browse a list of all links of the selected note (outgoing links, backlinks, external links.) See at the [section "Browse Links" below](#browse-links-of-a-note) for further information.
- Press `⇧` or `⌘ y` to toggle preview the selected note via macOS' Quick Look feature via Peek. 

```ad-note
title: Workflow Parameters
collapse: closed

- Appended content depends on the `input_append`. Set to `clipboard` will add the clipboard content, `manual` will prompt you for text to append.
- If `open_after_appending` is set to `true`, will open the note afterwards.
- The text set in `append_prefix` will be inserted in front of the input text. 
	- 💡 Using `- [ ]` enables you to add cards to a Kanban Note.
- To ignore files in a specific folder add to `search_ignore_folder`.
```

### Smart Queries
- Add `filename` or `title` to your search query, to display only files. `o obsidian filename`.
- You can filter for starred or recent files by adding `starred` or `recent` to your query.
- You can add `#tag` to your search query to search only for files with a specific tag, e.g., `o file #moc` 
- Add `alias` to your search query, to only display aliases [defined in the YAML-Header](https://help.obsidian.md/How+to/Add+aliases+to+note#Set+aliases). e.g., `o obsidian alias` will only display notes that have the *alias* `obsidian`.

### Search for Folders
When **selecting a folder**, you will **“browse”** the selected folder files, or add `folder` to your search query.
- You can use `⌥` or `new` create a new note *in that folder*. It will use the template note defined in `template_note_path`.
- `..` to browse the *parent* folder of the current folder. 

### Search for Headings
Select or add  `heading` to your search query, to only display headings,`o foobar heading` will 
- Add `h1`, `h2`, … to your search query, to only display headings of a certain level.
- Use `h_Ivl_ignore` to  ignore certain levels.

## Browse Links of a Note
**`ol`: Browse links of the current note**
- OR use `⇧ + ↵` on any search result of the main `o` search to browse the links of that note**
- Selecting an outgoing link or backlink will open the respective note.
	- All the modifiers (`⌘/⌃/⌥/fn/⇧ + ↵`) apply the same way as with the main `o` search.
	- YES, you can repeatedly use `⇧ + ↵` to fully traverse your graph via Alfred. 😎**
- for external links:
	- Selecting an external link with `↵` will open the link in the default browser.
	- Press `⌥ + ↵` on an external link to copy the URL to the clipboard instead.

## Search Notes via their Tags
**`ot`: Search tags and subsequently files with that tag**
- Display and search a full list of all tags in your vault.
	- Press `⌘ + ↵` instead to open Obsidian's search pane and search for the tag there.
- If `merge_nested_tags` is set to `true`, all nested tags are subsumed under their parent tag, e.g., `#inbox/toread` will be displayed under the `#inbox` tag. When set to `false`, all nested tags are displayed separately.

## Search Starred Files
`os`: Search starred Files and Searches
- If you select a starred *search*, Obsidian will open the search pane with the respective query.
- Requires the Starred core plugin enabled.

## Search Recent Files
**`or`: Open recent Files**
- Up to the 10 most recent files are displayed.

## Vault Search as Alfred Fallback
The main search (`o`) can be used as [Fallback Search for Alfred](https://www.alfredapp.com/help/features/default-results/fallback-searches/), showing up when any Alfred search has no result.

![fallback search](images/fallback-search.png)

## Previewing Notes via Quicklook
### Hotkey Setting
- To avoid accidentally triggering the Quick Look feature, I suggest you turn off activating Quick Look via shift and use `⌘ + Y` instead. You can do so with in the Alfred Settings under `Features → Previews`:


### QLMarkdown or Peek
[QLmarkdown](https://github.com/sbarex/QLMarkdown) and [Peek](https://apps.apple.com/app/peek-quick-look-extension/id1554235898) both enable previewing of Markdown documents. Peek is the better choice.


# Note-related Features

## Create a new Note
**`on`: Create a `n`ew note.**
- **File Name:** Anything you type after the keyword `on` (e.g., `on foobar`) will become the filename of the new note (e.g., `foobar.md`).
- **Content:** The `template_note_path` determines the content of the new note.
- **Location:** The new note will be placed in the folder specific `new_note_location`. If empty, it will be in your vault root.
- If you have set `use_quickadd` to `true`, this command will instead trigger the [QuickAdd Plugin](https://github.com/chhoumann/quickadd). Anything you type after the keyword `on` (e.g., `on foobar`) will be passed to search the QuickAdd choices. File Name, Location, and Content will be determined by QuickAdd.

## Scratchpad
`oo` or `triggered via hotkey`: Append to your Scratchpad Note**
-  `scratchpad_note_path` sets
	- When triggered via hotkey, will append the current selection.
	- When you append `#foobar` to `scratchpad_note_path` (e.g. `Inbox/Scratchpad-Note#Thoughts`), the text will be added below the heading "foobar" located in that note.
- The text set in the `scratchpad_append_prefix` will be inserted in front of the input text.
- If `open_after_appending` is set to `true`, will open the scratchpad afterwards.
- Using `- [ ]` as prefix and inserting below a specific heading enables you to add cards to a Kanban Board.

## Daily Notes (deprecated)
**`od`: Open & Append to today's daily note [settings].**
- Either open today's daily note or append to today's daily note, use `cmd + ↵` to open after appending.
- This does *not* require the Daily Notes plugin to be enabled.
- For now, the daily notes must be exactly in the format `YYYY-MM-DD` for this feature to work.
- Using the [workflow configuration](Workflow%20Configuration.md#note-related-features) `daily_note_path`, 
- The text set in  `daily_note_append_prefix` will be inserted in front of the input text.

ℹ️ I encourage you to check out the [Alfred workflow for Obsidian by hauselin](https://github.com/hauselin/obsidian-alfred), which focuses on daily notes.*

## Move Note
`om` : Move the current note to a different folder
- This fully replicates the functionality of the `Move File to another folder` and requires file explorer.




# Screenshot Features

## OCR Screenshots
`Triggered via Hotkey`: Take an OCR Screenshot.

```ad-note
title: Workflow Parameters
collapse: closed

- The *absolute* path set in `ocr_screenshot_file` determines where the the text resulting will be saved to. When empty, will save to `{vault-path}/OCR-Screenshots.md`. If it already exists, it will append to the note.
- You can change the prefix to OCR screenshots by changing `ocr_prefix`.
	- Use a different date format by following [Alfred's Placeholder-Syntax](https://www.alfredapp.com/help/workflows/advanced/placeholders/#date-time).
	- You can leave `ocr_prefix` empty or insert any other fixed value (e.g., a YAML-Header).
	- While not very visible, the workflow configuration variables *do* accept multi-line values.
- For best results, set the proper languages to be recognized with `ocr_languages`.
- When `open_after_screenshot` is set to `true`, then the note will be opened after taking the screenshot. Set to `false` to take OCR screenshots in quick succession.
```



### Requirements
For the OCR Screenshot Feature, you need to install [Tesseract](https://tesseract-ocr.github.io/tessdoc/Installation.html). If you use Homebrew, you can do so with the following two commands:

```bash
brew install tesseract
brew install tesseract-lang # for non-English languages
```

💡 *The first time you use the OCR or image screenshot feature*, you might need to give Alfred permission to record your screen. 

<img src="https://user-images.githubusercontent.com/73286100/131231644-a800c0b0-8dc2-4ae9-bd41-c3937741b94a.png" alt="Permissions for OCR Screenshots" width=35%>

## 🆕 Image Screenshot
**`Triggered via Hotkey`: Take an Image Screenshot.**
- Similar to the default Mac Hotkey `⌘ ⇧ + 4`, the image will be directly saved in your vault with the file name `Screenshot {date} {time}.png` and the image will be embedded (`![[image_file_name.png]]`) in the note `Images.md` in your vault root.
- The images will be saved in `{vault-path}/screenshots/` by default or use `screenshot_path` to specify the *absolute* path of a folder in your vault where to save the images instead.
- If the file “Images.md” already exists in your vault root, any subsequent screenshots will instead append to this note. This is intended for taking screenshots in quick succession.
- When `open_after_screenshot` is set to `true`, then the note will be opened after taking the screenshot. 

## Setting up Hotkeys
At the top left of the workflow, there are some sky-blue fields. You need to double-click them to set the keyboard shortcuts you want to use.

💡 To stay in line with the other macOS keyboard shortcuts for taking screenshots, you can use something like `⌘⇧ + 1` as hotkey.


# Utility Features


## Backup your Vault
**`obackup`: Create a `backup` of your vault.**
- Your whole vault will be compressed into a *zip* file and then moved to `backup_destination`. There will be a notification when the backup has been completed.
- Set the max number via,`max_number_of_bkps`) 
- Hidden folders `.obsidian` and `.trash` are included.


- 💡 Advanced users: you can use the following AppleScript snippet to trigger a backup. This is useful to create automated backups via [launchd](https://launchd.info/), [Cron jobs](https://ostechnix.com/a-beginners-guide-to-cron-jobs/), or [Keyboard Maestro](https://www.keyboardmaestro.com/main/).

```applescript
tell application id "com.runningwithcrayons.Alfred"
	run trigger "backup-obsidian" in workflow "de.chris-grieser.shimmering-obsidian" with argument ""
end tell
# pass 'no sound' as argument to turn off backup confirmation sound
```

⚠️ If you want 100% safety, please use professional backup solutions.


## Open Various Folders
- `o.obsidian`: The hidden `.obsidian` folder located in your vault root will be opened in Finder.
- `o.trash`: Open the hidden `.trash` folder.
- `oapplicationsupport`: Open Obsidian's Application Support folder.
- `oplugin`: The plugin folder in `.obsidian` folder will be opened in Finder.
- `ocss`: Open the `themes` and `snippets` folder. (Along with your installed themes and snippets.)
- Open your vault root with the [Vault Switcher](Vault%20Switcher.md).
- Open local plugin folders with the [Plugin Settings Search](Settings%20and%20Local%20Plugin%20Search.md).

## Carl
**`ocarl`: Search `carl` auto-responses. 🐢**
- Search and paste auto-responses from the beloved Discord Bot of the [Obsidian Discord Server](https://discord.gg/veuWUTm).

## Update Plugins & Metadata
**`oupdate`: Update Plugins and Metadata used by this workflow**
- Update your Community Plugins
- Update your Beta Plugins (installed via [the BRAT Plugin](https://github.com/TfTHacker/obsidian42-brat))
- Re-index the data for the [Documentation Search](Documentation%20and%20Forum%20Search.md).
- Refresh the metadata used for this workflow manually or set an interval to refresh it automatically. See the section on [workflow configuration for more information](Workflow%20Configuration.md#Metadata-Extractor-Configuration)


# Plugin & Theme Search
## Plugins

`op`: Combined Search of community plugins and community themes.
-  `↵` Opens the plugin in Obsidian's Community Plugin Browser.
	- `⌘ + ↵` Opens the GitHub repo instead.
	- `⌥ + ↵` to copy the plugin URI (`obsidian://show-plugin?id=...`) to your clipboard. When Discord is the frontmost app, the copied link will be surrounded with `<` `>` for more convenient pasting in the Discord Desktop app (disables auto-preview).
	- `⇧ + ↵` to display & search the GitHub issues. See [the section below](#-Searching-GitHub-Issues).
	- *Holding* `⌃` will display download numbers, author, and plugin ID.[^2] This is useful, when the plugin description is so long, that you cannot see this anymore.
	- ⚙️ Use `fn + ↵` to clone the GitHub Repository into the folder specified in `download_folder_path` via `git clone` (http).
	- ⚙️ Pressing `⌃ + ↵` will copy the plugin ID to the clipboard.
- Add `plugin` to the search query to only display themes, e.g., use `op focus plugin` as search query to only display *plugins* with the term `focus`.
- The `op` search will also consider the name of the plugin's author, meaning the query `op JaneDoe` will return all plugins (and themes) authored by the user `JaneDoe`.
- The thousand separator used with the download numbers can be set in (`thousand_seperator`).

💡 To open local plugin folders and access settings of beta plugins, use the [Settings & Local Plugin Search](Settings%20and%20Local%20Plugin%20Search.md).

## Themes
`op`: Combined Search of community plugins and community themes.**
- Press `↵` to open the theme browser. (There are no separate theme pages in Obsidian Theme Browser that can be opened.)
	- Use `⇧` or `⌘ + Y` to open a Quick Look Preview of the theme's promo screenshot. Press `⇧` or `⌘ + Y` again to close the preview.
	- *🎨 For Theme Designers:* Use `fn + ↵` to download the main .css file of the theme into the folder specified in the [workflow configuration](Workflow%20Configuration.md#Plugin-and-Theme-Search) (`download_folder_path`).
- Only themes officially included in the community themes are displayed — themes solely available via GitHub or still in review are not shown.
- Add `theme` to the search query to only display themes, e.g., use `op focus theme` as search query to only display *themes* with the term `focus`.
- The `op` search will also consider the name of the theme's author, meaning the query `op JaneDoe` will return all themes (and plugins) authored by the user `JaneDoe`.

<img src="https://user-images.githubusercontent.com/73286100/131027623-5e8b3667-d00d-47dc-ba49-6938686e2aca.gif" alt="plugin search" width=60%>

## Searching GitHub Issues
**Triggered by pressing `⇧ + ↵` on a plugin or theme. Will display a list of its GitHub issues.**
- The list will display the open/closed status, author, and number of comments. The list of issues can be searched like any Alfred Search.
- You can also choose to create a new issue, pre-populated as Feature Request or Bug Report.
- Use `⌥ + ↵` on an issue to copy the issue URL to the clipboard.
- 💡 To avoid unnecessary issues, the creation of new issues is *disabled* when the local version of the plugin is outdated. Instead, you will be provided with a quick shortcut to update the plugin 🙂
- ℹ️ Due to restrictions of the GitHub API, only the most recent 100 issues can be displayed.

<img src="https://user-images.githubusercontent.com/73286100/139559362-747b0c57-c29b-45b5-bc62-4ab53c0718c5.gif" alt="Issue Search" width=60%>
<img src="https://i.imgur.com/AvavR7n.png" alt="update information" width=60%>

[^1]: Unfortunately, there isn't enough versioning information for themes to do the same for them.
[^2]: Accessing the settings of an installed plugin via [the plugin search](Plugin%20and%20Theme%20Search.md) (`op`) via `ctrl + ↵` has been disabled in release 2.4.


# Documentation & Forum Search

## Documentation & Hub
**`oh`: Get `h`elp by searching the official [Obsidian documentation](https://help.obsidian.md/Start+here) and the [Obsidian Hub](https://publish.obsidian.md/hub).**
- This command mimics the search behavior on the official documentation site, meaning that it also searches for headings inside individual documentation pages.
	- Press `↵` to open in your default browser.
	- Use `⌥ + ↵` to copy the link to your clipboard instead. When Discord is the frontmost app, the copied link will be surrounded with `<` `>` for more convenient pasting in the Discord Desktop app (disables auto-preview).
- After major updates of the Obsidian documentation, this Alfred workflow needs to recreate its index of the Obsidian documentation. You can do so by selecting the respective option when typing keyword `oupdate`. (Index recreation can take a few seconds depending on your internet connection. You will be notified when it is done.)

<img src="https://i.imgur.com/RkKGrLw.gif" alt="Searching the Obsidian Documentation" width=60%>

## Forum Search
**`of`: Browse or Search the official [Obsidian `f`orum](https://forum.obsidian.md/).**
- Search in a category: Select a category and press `↵`. Afterwards, you will be prompted to enter a search query. Confirm with `↵` to open that search in your default browser.
- Press `⌘ + ↵` to open the forum category in your default browser.
- Use `⌥ + ↵` to copy the link to the category to your clipboard instead. When Discord is the frontmost app, the copied link will be surrounded with `<` `>` for more convenient pasting in the Discord Desktop app (disables auto-preview).



---
nav_order: 2
---

# Vault Switcher

**`ov`: Open `V`aults in Obsidian, Finder, or the Terminal**
- Select a Vault and press `↵` to open it in Obsidian.
	- `⌘ + ↵` will open the root of the selected vault in your default Terminal. You can [change the default terminal in the Alfred Settings](https://www.alfredapp.com/help/features/terminal/).
	- `⌥ + ↵` open the root in Finder.
	- `⇧ + ↵` to control the selected vault with _Shimmering Obsidian_. (This Alfred workflow can only work on one vault a the same time.) The first time you are controlling another vault, you need to install [the requirements](../README.md#Workflow-Installation) and run `osetup` in that vault once.
	- _⚙️ For developers_: `fn + ↵` run `git pull`on the vault
- Open the Vault Menu to create new vaults or remove vaults.



# Workflow Configuration

<img src="https://i.imgur.com/7YnQJ7K.png" alt="Metadata Extractor Settings" width=70%>

## Alfred Environment Variables
You access the main workflow configuration by clicking the *`[x]`* at the top right of the workflow.  
(Tutorial: [How to set Environment Variables in Alfred](https://www.alfredapp.com/help/workflows/advanced/variables/#environment))


### Alfred-based Quick Switcher
- `h_Ivl_ignore`: Heading levels that should be ignored in the Quick Switcher (`o` command). `h1 h6` will ignore h1 and h6, so only h2, h3, h4, and h5 show up in the Quick Switcher. `h4 h5 h6` will only show h1, h2 and h3 in the Quick Switcher. Enter `h1 h2 h3 h4 h5 h6` to ignore all headings in the Quick Switcher.
- `merge_nested_tags`: When using the `ot` search, merge all [nested tags](https://help.obsidian.md/Plugins/Tag+pane#Nested+tags) to their parent tag, e.g., `#inbox/to-read` and `#inbox/later` would both be subsumed under `#inbox`. Accepts `true` or `false`.
- `open_after_appending`: When appending to a note (`fn + ↵`), the note will automatically be opened afterwards. Accepts `true` or `false`. This setting also applies to the [Scratchpad](Note-related%20Features.md#Scratchpad) feature.
- 🆕 `input_append`: What type of content is used when appending to a note (`fn + ↵`). Accepts `clipboard` or `manual` (= prompting you to enter something).
- 🆕 `search_ignore_folder`: the vault-*relative* path to a folder which should be excluded when using the main search of Quick Switcher (`o` command). (The other sub-searches like `or` or `os` are not affected.) Leave empty to not exclude any folder.

### Note-related Features
- `template_note_path`: Vault-relative path to Template to use when creating new notes with the `on` command or when browsing a folder via [the Alfred-based Quick Switcher](Alfred-based%20Quick%20Switcher.md).
- 🆕 `new_note_location`: Vault-relative path to a folder where new notes created by `on` should be created. Leave empty to create the new note in the vault root.
- `use_quickadd`: Instead of creating a new note based on a template (with the keyword `on`), will trigger the [QuickAdd Plugin](https://github.com/chhoumann/quickadd). Accepted values are `true` and `false`.
- `scratchpad_note_path`: Vault-relative path to your [Scratchpad](Note-related%20Features.md#Scratchpad). 	
	- 🆕 When you append `#foobar` to `scratchpad_note_path` (e.g. `Inbox/Scratchpad-Note#Thoughts`), the text will be added below the heading "foobar" located in that note.
- `append_prefix`: String to insert before content appended to the [Scratchpad](Note-related%20Features.md#Scratchpad). Does accept dynamic content like the current date or time when you use [Alfred's Placeholder Syntax](https://www.alfredapp.com/help/workflows/advanced/placeholders/#date-time).
- `append_prefix`: String to insert before content appended to a note via the Alfred-based Quick-Switcher (`fn + ↵`). Does accept dynamic content like the current date or time when you use [Alfred's Placeholder Syntax](https://www.alfredapp.com/help/workflows/advanced/placeholders/#date-time).
- `daily_note_path`: *absolute* path to the folder where your daily notes are saved. See [Daily Notes](Note-related%20Features.md#Daily%20Notes).
- `daily_note_append_prefix`: String to insert before content appended to the daily note (`od`). Does accept dynamic content like the current date or time when you use [Alfred's Placeholder Syntax](https://www.alfredapp.com/help/workflows/advanced/placeholders/#date-time).

### Screenshots Features
- `ocr_languages`: set language codes of Tesseract, e.g., `eng+deu` for English and German. You can find out the code for your language(s) in [this list](https://tesseract-ocr.github.io/tessdoc/Data-Files-in-different-versions.html).
- `ocr_prefix`: Set the prefix for OCR Screenshots. Does accept dynamic content like the current date or time when you use [Alfred's Placeholder Syntax](https://www.alfredapp.com/help/workflows/advanced/placeholders/#date-time). Note that while not easy to see, `ocr_prefix` can have multi-line values.
- `open_after_screenshot`: When doing an OCR screenshot or an image screenshot, will open the note afterwards. Accepts `true` or `false`.
- `ocr_screenshot_file`: *Absolute* path to the *file* where the text resulting from the OCR should be saved to. When empty, will save/append the text to the file `{vault-path}/OCR-Screenshots.md`.
- `screenshot_path`: *Absolute* path to the *folder* where the image screenshots should be saved to. When empty, will save them the images to `{vault-path}/screenshots/`.

💡 "Absolute path" means you can also store it outside the vault when also turning off `open_after_screenshot`. (Images won't be embedded (`![[]]`) correctly then, though.)

### Plugin & Theme Search
- `thousand_seperator`: The thousand separator to use when download numbers are displayed, e.g., `.` or `,`.
- `download_folder_path`: Path where downloads from the `op` search should be placed. (cloned repositories for plugins or the main CSS-file for themes.)

### Backups
- `backup_destination`: Folder where the backups done by the `obackup` command should be saved.
- `max_number_of_bkps`: Maximum number of backups that should be stored at the backup destination folder. When the number is reached, every new backup cause the oldest backup to be deleted. (Decrease this number, when your backup folder becomes too big.)

### Miscellaneous
- `workspace_to_spellcheck`: Name of the Workspace where spellcheck should be turned on. Leave empty to not toggle any spellcheck setting with workspace changes. See [Workspace Switcher](Workspace%20Switcher.md).
- `auto_update`: Periodically check for updates *of this workflow* and update automatically. Accepts `true` or `false`.

### Internal
These variables are only here for internal and debugging reasons, you do not need to (and normally shouldn't) change them.

- `vault_path`: The *absolute* path to your obsidian vault.
- `vault_name_ENC`: The encoded name of you vault.

## Setting up the Hotkeys
At the top left of the workflow, there are some sky-blue fields. You need to double-click them to set the Keyboard Shortcuts you want to use for the respective commands.

<img src="https://i.imgur.com/wlpht7f.png" alt="Setting up Hotkeys" width=15%>

## For Users familiar with Alfred
You can change any keyword mentioned, like with any other Alfred workflow. All keyword triggers are located to the very left of this workflow.

## Default Terminal
You can change the default terminal used by this workflow [in the Alfred Settings](https://www.alfredapp.com/help/features/terminal/).

## Metadata Extractor Plugin Configuration
- **⚠️ Do not change any of the default values how the metadata extractor names its output files and where they are placed — otherwise this workflow won't be able to find them.**
- The *only* setting you can change is the one regarding the automatic refreshing of the metadata files. The higher the frequency, the more accurate the Quick Switcher of this Alfred workflow will become. You can also use `oupdate → Set Metadata Update Frequency` to change this setting via Alfred.
