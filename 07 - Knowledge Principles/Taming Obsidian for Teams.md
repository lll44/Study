Links:   
Tags: #security #pkm   
Published: September 7, 2021

# Obsidian, Taming a Collective Consciousness

## The Problem

On August 05, 2021, a member of the Conti ransomware group leaked some of the group’s internal playbooks and technical documentation. The event itself prompted a more widespread examination of how teams’ maintain their operational playbooks and documentation. A [tweet](https://twitter.com/mubix/status/1425461281251905539?s=20) by Mubix came across my radar and seemed to summarize this well.

80%!? Yikes…but probably also fair based on my prior experience. Not only is documenting for our own consumption tedious enough when there are hacks to be had, but layering on sharing of that content between a group, while simultaneously accounting for differing personalities, strategies, formats, search styles and platforms doesn’t exactly simplify its complexity.

Offensive operations are becoming more complex each year and continually require a deeper breadth of knowledge that spans several disciplines like infrastructure creation and configuration, operating system specifics, technique research and tool development etc. The days when operational knowledge was maintained by one person is long gone.

To ensure the highest quality and consistency of testing, we need a knowledge management solution that removes any semblance of siloed knowledge and empowers users to understand and apply aggregate team experience quickly. This does not mean that everyone on a team should then, enabled by each other’s notes, become an expert across all disciplines of operation. The optimal team composition as a compilation of highly specialized individuals. However, when documentation produced by a team member within a unique discipline is readily available across the team, the benefit of each individuals specialization is compounded.

While our methodology isn’t perfect yet, we have the added benefit of being able to say the strategy itself is defined by its continual evolution!

## Why Not the Old Way?

Historically my primary method of maintaining documentation has been an standalone Wiki. While this works well enough for sharing and maintaining information, after a few years of maintaining notes there, making contributions to the Wiki became a non-trivial task.

Most problematically perhaps was that knowledge generation isn’t happening simultaneously with running engagements or with research. Commits to the wiki slowed as people were planning to ‘finalize’ content and move it to the shared resource ‘later.’ And as we all know, ‘later’ only comes once a year…on Tuesday…after your other eight (8) projects and before the twelfth of never.

Why was this happening?

1.  OverHead No matter how often the wiki was kept in view, creating and formatting content into an article became a task all its own. That meant everyone was maintaining personal documentation outside the shared solution and setting aside additional time to reformat and commit the article for the groups benefit.
    
2.  Perfection Perception There can be a propensity to withhold ‘incomplete’ information while waiting for the production of a flawless note. In a technical setting, however, it’s important to acknowledge that your documentation will likely never be “complete” and to develop a strategy where information can be used as readily as its produced.
    
3.  Categorization and Organization In a traditional folder-based note structure, we’re conditioned to categorize content as specifically as possible. This works well enough when you’re the sole resource maintain the information, In our own practice, we found this mentality ultimately lead to the duplication of data and a complex structure. The more complex the structure got and the more time it took to find what you were looking for, the more people disassociate with the the perception of the solution as ‘their own.’ This becomes particularly apparent in that moment when you’ve just established remote command and control over a system and you’re digging through a veritable labyrinth of documents looking for that one piece of information you needed five minutes ago.
    
4.  The Cloud for sharing
    

# The Solution

Here are a list of some of our primary requirements along with how we met them using Obsidian.

1.  Markdown
    
    -   Description: Unanimously preferred format for coders. Markdown is a lightweight HTML-lite-like language designed specifically for formatting text quickly. It is also an application-agnostic format that could persist in other applications if needed.
        
    -   In Obsidian: Obsidian vaults are the folder/subfolder directories on your device and notes are maintained as Markdown (.md) files.
        
2.  Plaintext Backend
    
    -   Description: Maintaining a plaintext backend of notes as markdown files allows it to be application agnostic and . It also enabled the direct addition, manipulation, searching of content across the vault and provides the easiest possible automation for the notes.
        
    -   In Obsidian: Like mentioned above, Obsidian maintains all notes as Markdown (.md) files and in a traditional directory structure.
        
3.  Git Managed
    
    -   Description: [[Git]] is a backup system used by developers that allow you to version control the notes easily, to keep them easily organized and collab around them. It is not an instant system like dropbox but is much more powerful. Requires small overhead to learn.
        
    -   In Obsidian: The plugin [Denolehov’s Obsidian-Git](https://github.com/denolehov/obsidian-git). anyone who has worked in a collaborative Git development environment can tell you, this type of shared commit access to a repository can result in conflicts quickly. For us, this has been manageable through the assignment of few plugin settings which we’ll discuss later in this article.
        
4.  Reduced Overhead
    
    -   Description: We needed to lower the barrier of entry required for committing new content. A [Zettelkasten](https://writingcooperative.com/zettelkasten-how-one-german-scholar-was-so-freakishly-productive-997e4e0ca125) like note-taking and knowledge management ideology, empower users to simply ‘create content’ atomically and have the methodology specifics abstracted from that process.
        
    -   In Obsidian: The plugin, [Templater](https://github.com/SilentVoid13/Templater)we us a single ‘master’ template which was run on the creation of any new note. All content must be generated using this template and, based on a categorization selected during creation, sections of markdown are assembled to produce the corresponding boilerplate note structure.
        
5.  Personal Repository
    
    -   Description: In addition to the group repository, we acknowledged that each consultant should maintain notes which did not need to be visible by the collective team.
        
    -   In Obsidian: To offer this functionality, we simply created a folder within the group repository that was defined with the .gitignore. This allowed personal and group notes to be viewed in a single pane, something that is otherwise not possible using Obsidian.
        

## Our Implementation

### Key Components

Before we get into some more Obsidian-specific content, I’ll briefly define some of the components that we’ll work with throughout this post.

1.  Vault: Your collection of notes. Styles, plugins and application settings are maintained per vault. The number of open vaults correspond directly with the number of application windows open. Use a number system to easily order notes, this also helps for automation later on.
    
2.  Note: The fundamental component of Obsidian, notes are the pages we interact with and where content is maintained. Notes should be a concise distillation of information as it was interpreted by the author. Notes should be written with the sole intent of being readily usable during subsequent research or active operations.
    
3.  Links: How relationships between notes are drawn. Links are denoted by a word or term corresponding to the content of a note which is set between a pair of square brackets “`[[ ]]`”. Behind the content itself, links are the most important component of the your vault. Without folders, links function as the overarching imposed structure of related data as well as the vehicle with which we navigate it.
    
4.  Categories (Primary/Secondary):
    
    -   Categories are our simplification of the more widely adopted term “Map of Content” (MoC). Categories simply serve as a jumping-off point into and around content maintained in your vault.
        
    -   Looking for something related to a DLL Hijacking?
        
        -   Start with the ‘Red Team’ or ‘Pentest’ Primary Category
            
        -   navigate to the Secondary Category corresponding to ‘Persistence’.
            
    -   The division of ‘Primary’ and ‘Secondary’ is entirely arbitrary and established merely to assist in rapid filtering of content scope.
        
    -   Categories are simply lists of links
        
    -   Unlike a folder structure, a single note can belong to one or several categories.
        
    -   It is --not-- important that every note related to a Categories be immediately available across Categories where its content may be relevant. Instead, paths into and between notes should be grown organically as the team uses and searches the vault. This strategy accounts for the creation of several navigational routes which ultimately arrive at the same content, a concept which we’ve found is of paramount importance when operating from a shared solution.
        
5.  Search Tag:
    
    -   Tags are essentially shortcuts for vault-wide searches. These are defined by a short list of emojis which correspond to categorizations of data types committed to the repository.
        
    -   Note: In our study use case we will use regular tags #pkm on different sections [[Note Style Guidelines#Tags | Tags]]
        

## Ready to get started?

[View The Vault Structure](https://github.com/trustedsec/Obsidian-Vault-Structure)

---

### Vault Structure

Below is an example of the vault structure we settled on. The idea behind this structure is to offer a navigational experience similar to a folder structure when there is none. Here you would start with the `000 - Global Index (Start Here!)` note which functions as an index of Primary Categories. From there you would select a relevant Primary and subsequent Secondary Category, each time further narrowing the context of information returned closer to the note you’re looking for.

-   000 – Global Index (Start Here!)
    
-   01 – Primary Categories
    
    1.  01 – Administration
        
    2.  01 – Pentest
        
    3.  01 – Red Team
        
-   02 – Secondary Categories
    
    1.  02 – Lateral Movement
        
    2.  02 – Privilege Escalation
        
    3.  02 – Python
        
    4.  02 – Reporting
        
    5.  02 – Infrastructure
        
-   03 – Content
    
    -   No naming convention or corresponding prefix within `03 - Content`
        
-   04 – Templates
    
-   05 – Personal
    
    -   No naming convention or corresponding prefix within `05 - Personal`
        

And here’s an example of what it looks like to navigate through the structure we’ve defined along one path.

### Synchronization

Using Git for our vaults’ backend synchronization allowed us to maintain and sync notes on a private GitLab repository. We also explicitly defined access to the repository, maintained a history of repository modifications as commits, allowed for rollbacks if necessary, and maintained our information as Markdown (MD) directly.

Our Obsidian Git configuration consists of the following settings:

1. Vault Backup Interval: 60   
2. Auto Pull Interval: 10   
3. Commit Message: FLast {{date}}   
4. Date Placeholder: MM-DD-YYYY HH:mm:ss   
5. Pull Changes Before Push: Enabled (default) 

Additionally we use a .gitignore file to omit files and directories which either caused frequent conflicts or we deliberately did not want synced. Our .gitignore file configuration;

# to exclude Obsidian workspace settings (including plugin and hotkey configurations)   
.obsidian/*   
​  
# OR only to exclude workspace cache   
.obsidian/workspace/*  
​  
# Exclude plugins   
.obsidian/plugins/*   
​  
# Exclude consultant specific files "personal"   
$VAULTNAME/Personal/   
05-Personal/   
​  
# Exclude Day Planner directory placed in vault root   
Day*Planners/*   
​  
# This file is used to keep track of last auto   
backup/pull   
.obsidian-git-data   
​  
# Exclude Untitled Notes   
Untitled*  
​  
# Exclude "bad" names   
null*   
​  
# Add below lines to exclude OS settings and caches   
.trash/   
.DS_Store

Especially while getting started and while everyone is editing documents frequently, its important to remember that conflicts will happen. During this period it may be beneficial to designate a subset of users to migrate notes into the vault or to divide up content creation by category. Additionally, tweaking the push and pull numbers in the Obsidian Git plugin to pull with a higher frequency can help considerably. We found it was beneficial to maintain a short list of conflict scenarios and when in doubt, you can always `git reset` .

## How To:

### Create Content

#### Bitsadmin.exe Example

To demonstrate how this structure works to create, navigate, and associate our data, let’s walk through an example using the LOLbin Bitsadmin.exe and its associated functions as listed in the ever-relevant LOLBAS.

Starting at `000 - Global Index (Start Here!)`, we’ll jump into the vault and select a Primary Category which corresponds to the note we’re creating. Note that the title of the Note is seen here in Edit mode and is itself, a link. Maintaining a page title as a link allows us to seamlessly update the title and all references to the title over the entire vault if its ever necessary.

##### 000 – Global Index

From `000 - Global Index (Start Here!)` I’ll CTRL + Click into the Primary Category `01 - RED TEAM`.

##### Primary Categories

Stepping into the Primary Category `01 - RED TEAM`, you’re presented with a list of Secondary Categories corresponding to the Category. Note how Primary Categories tie directly back to the Global Index. This _back_link facilitates moving backward through the category hierarchy we’ve imposed.

Additionally, note the prefix or each Secondary Category is `02 -` this allows us to quickly identify and Secondary Categories within the context of a note.

##### Secondary Categories

Since we’re dealing with Bitsadmin.exe and the first LOLBAS categorization is for Alternate Data Stream, let’s continue into the Secondary Category, Persistence. Note how Secondary Categories link back to one or more related Primary Categories but not to the `000 - Global Index (Start Here!)` note.

### Link Content

After clicking into the Secondary Category, Persistence, you’re met with our final index of links. The Secondary Category organizes and maintains links to all our Category’s associated content (notes). As the links within the `# Grouping`s on this page grow, a large list of related elements may could indicate it would be beneficial to breakout the grouping into its own Secondary Category. References to notes here could be collapsed and the Secondary Category could be linked.

Another benefit of maintaining `# Grouping`s like this is for their verbatim inclusion into other content. Within Obsidian, it’s possible to embed content from one note and insert it into another. This type of linking is performed referencing the note title and `# Grouping` header.

ResultCommandExample

Link to an entire note `[[name of the note]]`

Link to a notes heading `[[name of the note#heading]]`

Link to a block within a specified heading `[[name of the note^blockname]]`

Alternative Naming `[[name of the note^blockname | Alt Name]]`

For example, editing the note pertaining to `Windows`, I’m able to quickly link or embed the `# Grouping` “LOLBins” from the Secondary Category, “Persistence”. Adding the suffix ‘#’ to the tag will present me with a list of the groupings on the target Category. Selecting a grouping name will create a link to the corresponding content, and prefixing the reference with a “!” will embed the referenced content.

In the above example, im editing the `Windows` note and have the editing and preview panes open side by side. The editing pane allows you to modify the markdown directly where-as the preview window will only render the corresponding content along with any CSS you may have associated with your vault. Simply `CTRL + Click` the preview icon in the lower left hand corner of your note. The panes should open linked, meaning that any notes you now browse to will have edit on the left, and preview on the right.

### Creating Content, Continued

Continuing with our LOLBin example, I’m now ready to create the note that will contain the content I’m looking to document. First, I’ll add a link within the LOLBins grouping as `[[Bitsadmin.exe]]`. By viewing rendered markdown in the preview pane (right-side), you can see that the newly created link to our note is darker than the others. This indicates that the linked content does not exist yet. To create the note, `CTRL + Click` on the newly created link.

#### Templates for Automation

Using [SilentVoid13’s Templater](https://github.com/SilentVoid13/Templater) plugin, I’ve required the association of a Search Tag and a Title on the creation of a note. To require a template to run on the creation of a new note, you need to modify the following settings in the configuration options for the Templater Plugin `Settings > Community Plugins`.

1.  Template Folder Location
    
2.  Set `Empty file template` to `04 - Templates/0400 - Gen_Note`. Differentiated by markdown “struct” we assign, this note will serve for the basis of _ALL_ notes (content or categories).
    

Here we’ll assign the Search Tag associated with TTP, and the title should be automatically populated from the link we clicked to create the note.

We created our note successfully! Since we selected the Search Tag of TTP, templater combined markdown elements to “build” a “TTP” note containing the boilerplate metadata and headings that may help a user get started documenting a particular TTP. Using templates in this way facilitates the abstraction of users from the overhead of committing information. In turn, this allows them to focus less on the categorization and organization of data and empowers us to control it administratively.

#note: The following sections will not be fully integrated into our notes at this time other than stuff regarding application layout.

#### Putting it all together

You can see that some information regarding population of things like the Primary and Secondary Categories was also supplied with the template during the note’s creation. Let’s go ahead and populate these manually and see how they connect our data.

## Navigating Content

### Local Graph View

Now that the links to our associated categories are established, let’s jump into a unique Obsidian feature, the Local graph view, to view its effect on our data. The Local graph view can be opened by using the command palette and selecting Local Graph View.

Within the graph view, here is the note we just created.

From here, you can click on any node of the graph to jump into or create its associated content. For instance, by clicking on the node `02 - Persistence`, I’m taken back to a view of the Secondary Category `02 - Persistence` and its related note links.

In addition to being an effective way to navigate your vault’s content, Obsidian’s graph view has the added benefit transforming notes into a graphical playbook.

-   Need to start an engagement building infrastructure?
    
    -   Jump to the `02 - Infrastructure` Secondary Category and visual review available options for hosting and configuration.
        
-   Just landed on a workstation and need to begin internal reconnaissance?
    
    -   Jump to the Secondary Category of `02 - Reconnaissance`.
        
    -   Click down into the corresponding operating system you’re operating on.
        
    -   Visually review possible reconnaissance methods and select the one which best fits your current scenario.
        

### Searching

No matter how well structured our vault is, it’s likely that you’re not always going to want to start the Global Index and dig down to the note you’re looking for through its associated categories. Obsidian has accounted for this by providing the search pane, and we’ve boosted its effectiveness through our design choice surrounding the use of ‘Search Tags’.

While Obsidian exposes several methods of searching, there are two (2) that I use most often: ‘tag’ and ‘file’.

Since we’ve tagged Categories (Primary and Secondary) with the ‘Map’ emoji, if we’re looking to quickly jump to a specific category such as ‘lateral movement,’ within the search pane we can provide the ‘tag:#’

Our search target of ‘Lateral Movement’

You can see that this has quickly filtered our results to a small number of Categories containing the verbatim string we’re seeking. To take this a step further and get exactly what we want, let’s prefix our search term with the term ‘file:’.

This is the exact Category I wanted to reference. By expanding the tab presented within the search pane, matching keywords can be viewed without opening or redirecting to the matching note.

In replacement of the ‘file:’ prefix, it’s also possible to filter notes further using additional keywords. Here, I’m looking for Windows persistence methods and want to jump directly to a list of them.

Clicking the ‘#Windows’ heading displayed by the search pane takes me to the Persistence Category and appropriately down to the associated ‘#Windows’ grouping of links.

This same concept applies to the graph view as well. Reusing the search filter of ‘tag:#![🗺]’ , we can quickly limit the information displayed to Categories and review their connected relationships.

### Global Graph View

By transitioning to the complete graph view, we’re able to review the same data at additional depths more comfortably. Here’s a breakdown of the same Primary Category on the global graph view. This view ties together any and all notes where we’ve supplied a link back to the Primary Category RED TEAM.

#### Identifying New Content Relationships

With more references to a particular topic, its associated node on the graph view will increase in size.

Looking at our node associated with the keyword LOLBin that we were linking to our content, you can see that it’s fairly large and greyed out. Like links, nodes that do not exist are slightly greyed. Combining our understanding of how size is affected by reference and our knowledge that greyed nodes do not exist, we can look at our data in novel ways to help us extrapolate information and define relationships!

### Application Layout

In my time using Obsidian I’ve found that the layout of the application can drastically affect your use and in turn, the usefulness of the app itself. For this reason I want to share my current layout.

##### Left

-   (top)
    
    -   File Explorer: for when you need a traditional way to get around
        
-   (bottom)
    
    -   Local Graph View: Graph depiction of relationships directly related to the note you’re viewing
        

##### Middle'

Note: These panes are open for interpretation. The markdown editor will eventually support edit and preview as you go, so stacking of different preview panes may be useful.

-   (left)
    
    -   Editing Pane – Displaying the editable markdown associated with the current note
        
-   (right)
    
    -   Preview Pane – Displaying the rendered markdown associated with the current note.
        

##### Right

-   (top)
    
    -   Tag Pane – Displays all possible tags; Allows the near-instant search of notes associated with the tag
        
-   (middle)
    
    -   Outline Pane – Displays an outline of the current note’s content and allows you to jump around to heading within the note
        
    -   (bottom)
        
    -   Starred/Favorites Pane – List of notes you have starred; I typically edit the content of this pane frequently and use it more when I’m looking to jump between a set of notes
        

To move ‘panes’ around the screen, simply left-click on the pane ‘tab’ in the top left of the pane itself and drag. Areas where the pane is placeable/snappable should highlight accordingly.

## Helpful Plugins

A fantastic feature of Obsidian is its support of community plugins. Here are a few honorable mentions that we’ve found particularly helpful:

1.  [Obsidian Git](http://github.com/denolehov/obsidian-git)
    

- This simple plugin allows you to back up your [Obsidian.md](https://obsidian.md) vault to a remote Git repository (e.g., private repo on GitHub). This plugin assumes you have an existing Git repository initialized locally and that credentials are set up.

2.  [Templater](https://github.com/SilentVoid13/Templater)
    

- Description:[Templater](https://github.com/SilentVoid13/Templater) is a template language that lets you insert --variables-- and --functions-- results into your [Obsidian](https://obsidian.md/) notes. It will also let you execute JavaScript code manipulating those variables and functions.

3.  [Mind Map](https://github.com/lynchjames/obsidian-mind-map)
    

- Description: This repository contains a plugin for [Obsidian](https://obsidian.md/) for viewing Markdown notes as Mind Maps using [Markmap](https://markmap.js.org/).

4.  [DataView](https://github.com/blacksmithgu/obsidian-dataview)
    

- Description: Treat your [Obsidian](https://obsidian.md/) as a database which you can query from. Provides a JavaScript API and pipeline-based query language for filtering, sorting, and extracting data from Markdown pages. See the Examples section below for some quick examples, or the full [reference](https://blacksmithgu.github.io/obsidian-dataview/) for all the details.

## Resources

1.  Zettlekasten
    

- [How One German Scholar Was So Freakishly Productive](https://writingcooperative.com/zettelkasten-how-one-german-scholar-was-so-freakishly-productive-997e4e0ca125)  
- [The Zettelkasten Method](https://www.lesswrong.com/posts/NfdHG6oHBJ8Qxc26s/the-zettelkasten-method-1)  
- [How to Take Smart Notes for Knowledge Management](https://improveism.com/zettelkasten-method-smart-notes/)

2.  Obsidian
    

- [Obsidian Community Forums](https://forum.obsidian.md/)  
- [Obsidian Roundup](https://obsidianroundup.org/resources/)  
- [Bryan Jenks Tech](https://www.youtube.com/c/BryanJenksTech)  
- [Linking Your Thinking](https://www.youtube.com/channel/UC85D7ERwhke7wVqskV_DZUA)  
- [How to Take Smart Notes in Obsidian](https://theknowledgeworker.substack.com/p/how-to-take-smart-notes-in-obsidian)