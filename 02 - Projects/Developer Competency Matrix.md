# Programmer Competency Matrix

- Computer Science 
	- Data Structures 
		- 0 Doesn’t know the difference between Array and LinkedList
		- 1 Able to explain and use Arrays, LinkedLists, Dictionaries etc in practical programming tasks
		- 2 Knows space and time tradeoffs of the basic data structures, Arrays vs LinkedLists, Able to explain how hashtables can be implemented and can handle collisions, Priority queues and ways to implement them etc.
		- 3 Knowledge of advanced data structures like B-trees, binomial and fibonacci heaps, AVL/Red Black trees, Splay Trees, Skip Lists, tries etc.

	- Algorithms 
		- 0 Unable to find the average of numbers in an array (It’s hard to believe but I’ve interviewed such candidates)
		- 1 Basic sorting, searching and data structure traversal and retrieval algorithms
		- 2 Tree, Graph, simple greedy and divide and conquer algorithms, is able to understand the relevance of the levels of this matrix.
		- 3 Able to recognize and code dynamic programming solutions, good knowledge of graph algorithms, good knowledge of numerical computation algorithms, able to identify NP problems etc.

	- Systems Programming 
		- 0 Doesn’t know what a compiler, linker or interpreter is
		- 1 Basic understanding of compilers, linker and interpreters. Understands what assembly code is and how things work at the hardware level. Some knowledge of virtual memory and paging.
		- 2 Understands kernel mode vs. user mode, multi-threading, synchronization primitives and how they’re implemented, able to read assembly code. Understands how networks work, understanding of network protocols and socket level programming.
		- 3 Understands the entire programming stack, hardware (CPU + Memory + Cache + Interrupts + microcode), binary code, assembly, static and dynamic linking, compilation, interpretation, JIT compilation, garbage collection, heap, stack, memory addressing…


- Software Engineering 
	- Version Control 
		- 0 Folder backups by date
		- 1 VSS and beginning CVS/SVN user
		- 2 Proficient in using CVS and SVN features. Knows how to branch and merge, use patches setup repository properties etc.
		- 3 Knowledge of distributed VCS systems. Has tried out Bzr/Mercurial/Darcs/Git

	- Build Automation 
		- 0 Only knows how to build from IDE
		- 1 Knows how to build the system from the command line
		- 2 Can setup a script to build the basic system
		- 3 Can setup a script to build the system and also documentation, installers, generate release notes and tag the code in source control

	- Automated Testing 
		- 0 Thinks that all testing is the job of the tester
		- 1 Has written automated unit tests and comes up with good unit test cases for the code that is being written
		- 2 Has written code in TDD manner
		- 3 Understands and is able to setup automated functional, load/performance and UI tests

- Programming 
	- Problem Decomposition 
		- 0 Only straight line code with copy paste for reuse
		- 1 Able to break up problem into multiple functions
		- 2 Able to come up with reusable functions/objects that solve the overall problem
		- 3 Use of appropriate data structures and algorithms and comes up with generic/object-oriented code that encapsulate aspects of the problem that are subject to change.

	- Systems Decomposition 
		- 0 Not able to think above the level of a single file/class
		- 1 Able to break up problem space and design solution as long as it is within the same platform/technology
		- 2 Able to design systems that span multiple technologies/platforms.
		- 3 Able to visualize and design complex systems with multiple product lines and integrations with external systems. Also should be able to design operations support systems like monitoring, reporting, fail overs etc.

	- Communication 
		- 0 Cannot express thoughts/ideas to peers. Poor spelling and grammar.
		- 1 Peers can understand what is being said. Good spelling and grammar.
		- 2 Is able to effectively communicate with peers
		- 3 Able to understand and communicate thoughts/design/ideas/specs in a unambiguous manner and adjusts communication as per the context

	- Code Organization in File 
		- 0 no evidence of organization within a file
		- 1 Methods are grouped logically or by accessibility
		- 2 Code is grouped into regions and well commented with references to other source files
		- 3 File has license header, summary, well commented, consistent white space usage. The file should look beautiful.

	- Code Organization across Files 
		- 0 No thought given to organizing code across files
		- 1 Related files are grouped into a folder
		- 2 Each physical file has a unique purpose, for e.g. one class definition, one feature implementation etc.
		- 3 Code organization at a physical level closely matches design and looking at file names and folder distribution provides insights into design

	- Source Tree Organization 
		- 0 Everything in one folder
		- 1 Basic separation of code into logical folders.
		- 2 No circular dependencies, binaries, libs, docs, builds, third-party code all organized into appropriate folders
		- 3 Physical layout of source tree matches logical hierarchy and organization. The directory names and organization provide insights into the design of the system.

	- Code Readability 
		- 0 Mono-syllable names
		- 1 Good names for files, variables classes, methods etc.
		- 2 No long functions, comments explaining unusual code, bug fixes, code assumptions
		- 3 Code assumptions are verified using asserts, code flows naturally – no deep nesting of conditionals or methods

	- Defensive Coding 
		- 0 Doesn’t understand the concept
		- 1 Checks all arguments and asserts critical assumptions in code
		- 2 Makes sure to check return values and check for exceptions around code that can fail.
		- 3 Has his own library to help with defensive coding, writes unit tests that simulate faults

	- Error Handling 
		- 0 Only codes the happy case
		- 1 Basic error handling around code that can throw exceptions/generate errors
		- 2 Ensures that error/exceptions leave program in good state, resources, connections and memory is all cleaned up properly
		- 3 Codes to detect possible exception before, maintain consistent exception handling strategy in all layers of code, come up with guidelines on exception handling for entire system.

	- IDE 
		- 0 Mostly uses IDE for text editing
		- 1 Knows their way around the interface, able to effectively use the IDE using menus.
		- 2 Knows keyboard shortcuts for most used operations.
		- 3 Has written custom macros

	- API 
		- 0 Needs to look up the documentation frequentl
		- 1 Has the most frequently used APIs in memory
		- 2 Vast and In-depth knowledge of the API
		- 3 Has written libraries that sit on top of the API to simplify frequently used tasks and to fill in gaps in the API

	- Frameworks 
		- 0 Has not used any framework outside of the core platform
		- 1 Has heard about but not used the popular frameworks available for the platform.
		- 2 Has used more than one framework in a professional capacity and is well-versed with the idioms of the frameworks.
		- 3 Author of framework

	- Requirements 
		- 0 Takes the given requirements and codes to spec
		- 1 Come up with questions regarding missed cases in the spec
		- 2 Understand complete picture and come up with entire areas that need to be speced
		- 3 Able to suggest better alternatives and flows to given requirements based on experience

	- Scripting 
		- 0 No knowledge of scripting tools
		- 1 Batch files/shell scripts
		- 2 Perl/Python/Ruby/VBScript/Powershell
		- 3 Has written and published reusable code

	- Database 
		- 0 Thinks that Excel is a database
		- 1 Knows basic database concepts, normalization, ACID, transactions and can write simple selects
		- 2 Able to design good and normalized database schemas keeping in mind the queries that’ll have to be run, proficient in use of views, stored procedures, triggers and user defined types. Knows difference between clustered and non-clustered indexes. Proficient in use of ORM tools.
		- 3 Can do basic database administration, performance optimization, index optimization, write advanced select queries, able to replace cursor usage with relational sql, understands how data is stored internally, understands how indexes are stored internally, understands how databases can be mirrored, replicated etc. Understands how the two phase commit works.

- Experience 
	- Languages w/ Professional Experinece 
		- 0 Imperative or Object Oriented
		- 1 Imperative, Object-Oriented and declarative (SQL), added bonus if they understand static vs dynamic typing, weak vs strong typing and static inferred types
		- 2 Functional, added bonus if they understand lazy evaluation, currying, continuations
		- 3 Concurrent (Erlang, Oz) and Logic (Prolog)

	- Platforms w/ Professional Experience 
		- 1 
		- 3 
		- 5 
		- 7+ 
		
	- Years of Professional Experience 
		- 1 
		- 2-5 
		- 6-9 
		- 10+ 
		
	- Domain Knowledge 
		- 0 No knowledge of the domain
		- 1 Has worked on at least one product in the domain.
		- 2 Has worked on multiple products in the same domain.
		- 3 Domain expert. Has designed and implemented several products/solutions in the domain. Well versed with standard terms, protocols used in the domain.

- Knowledge 
	- Tool Knowledge 
		- 0 Limited to primary IDE (VS.Net <http://VS.Net>, Eclipse etc.)
		- 1 Knows about some alternatives to popular and standard tools.
		- 2 Good knowledge of editors, debuggers, IDEs, open source alternatives etc. etc. For e.g. someone who knows most of the tools from Scott Hanselman’s power tools list. Has used ORM tools.
		- 3 Has actually written tools and scripts, added bonus if they’ve been published.

	- Languages Exposed to 
		- 0 Imperative or Object Oriented
		- 1 Imperative, Object-Oriented and declarative (SQL), added bonus if they understand static vs dynamic typing, weak vs strong typing and static inferred types
		- 2 Functional, added bonus if they understand lazy evaluation, currying, continuations
		- 3 Concurrent (Erlang, Oz) and Logic (Prolog)

	- Codebase Knowledge 
		- 0 Has never looked at the codebase
		- 1 Basic knowledge of the code layout and how to build the system
		- 2 Good working knowledge of code base, has implemented several bug fixes and maybe some small features.
		- 3 Has implemented multiple big features in the codebase and can easily visualize the changes required for most features or bug fixes.

	- Knowledge of upcoming Tech 
		- 0 Has not heard of the upcoming technologies
		- 1 Has heard of upcoming technologies in the field
		- 2 Has downloaded the alpha preview/CTP/beta and read some articles/manuals
		- 3 Has played with the previews and has actually built something with it and as a bonus shared that with everyone else

	- Platform Internals 
		- 0 Zero knowledge of platform internals
		- 1 Has basic knowledge of how the platform works internally
		- 2 Deep knowledge of platform internals and can visualize how the platform takes the program and converts it into executable code.
		- 3 Has written tools to enhance or provide information on platform internals. For e.g. disassemblers, decompilers, debuggers etc.

	- Books 
		- 0 Unleashed series, 21 days series, 24 hour series, dummies series…
		- 1 Code Complete, Don’t Make me Think, Mastering Regular Expressions
		- 2 Design Patterns, Peopleware, Programming Pearls, Algorithm Design Manual, Pragmatic Programmer, Mythical Man month
		- 3 Structure and Interpretation of Computer Programs, Concepts Techniques, Models of Computer Programming, Art of Computer Programming, Database systems , by C. J Date, Thinking Forth, Little Schemer

	- Blogs 
		- 0 Has heard of them but never got the time.
		- 1 Reads tech/programming/software engineering blogs and listens to podcasts regularly.
		- 2 Maintains a link blog with some collection of useful articles and tools that he/she has collected
		- 3 Maintains a blog in which personal insights and thoughts on programming are shared




