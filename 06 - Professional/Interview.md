# Portfolio





# Portfolio Advice

https://old.reddit.com/r/cscareerquestions/comments/1gjws9/how_can_i_build_a_really_good_software_portfolio/


First, for some perspective, check out this entry-level job posting at ArenaNet. In particular, this section:

    Here is what we are looking for in your code samples:
    
        Your best work.
        Demonstrated breadth of programming skills.
        Ability to write readable, maintainable and efficient code.
        Ability to design clear abstractions and clean interfaces.
        Appropriate selection of data structures or algorithms.
    
    What we are not looking for:
    
        Code any of your previous employers have prevented you from sending us.
        Solutions to simple problems (such as counting the number of zero bits in an integer).
        Straightforward implementations of published algorithms (such as A*).
        Wrapper classes for an existing library.
        Math libraries such as matrix and vector implementations.
        That code that you wrote years ago but which you could write better today; we want to see examples of your current skill.
    
    This is your chance to impress our engineering department and show us why we should hire you. So, send us a sample of your very best work, something you're proud of. If you don't have anything on hand that meets the above criteria, write some code that does.

Keep coding and doing cool projects that expand your skill set. That said, you'll want to learn C++ at some point. Even though in many jobs you'll use something else, knowing C++ shows you understand how things work at a lower level. Possibly go even lower level and learn assembly. If you want a fun way to learn assembly, teach yourself to make Gameboy games.

If you really want to impress people, write up some game or tech demo that uses something you had to research rather than something you can just copy an algorithm for. You could write a fluid simulation, implement jump point search, or do something completely different.

Make sure you have a portfolio site. Here's mine for reference, but search around on Google for other examples, look up articles, etc. and create something that fits you.

Remove old projects. Show only your best work.

Make sure to apply for internships. Internships and personal projects are the solution to the Catch-22 of "you need work experience to get a job, but you need a job to get work experience".

Work on a mix of solo projects and team projects. Solo projects are good because it's clear what you personally are capable of, and you can't hide behind teammates. Group projects are good because it gives experience working on teams and on larger projects. Do both.

In 6 months, you can probably crank out two complete, polished projects. If I had to arbitrarily pick two ideas:

    Build a 2D arcade game of your choice. Platformers are an option, but everybody makes them (because they're easy), so something else might stand out more. Make sure the game is complete and has menus, sound, etc. Do this in tech you already know to basically show "this is what I am currently capable of". A shoot-em-up a la Galaga might be fun! Be wary of e.g. RPGs, because you'll spend a ton of time on content to make it decent rather than just on code and mechanics.
    Build a text adventure in C++. I assume you don't know C++ or any other lower-level languages at all, so 3 months is probably enough to learn the language and build a short text-based game that also has some interesting software engineering challenges (how do I store rooms and connections? How do I parse input?) without getting too crazy.








Projects that you expect to use, or projects that have taken weeks or months to plan and complete, not projects taking hours or otherwise not very distinguishable from programming puzzles given at job interviews. Because projects taking weeks/months is closer to the reality of jobs.







I've been a hiring manager for my team before (u/MasterLJ noted the difference elsewhere in this thread) and the thing that impresses me the most (with college students and industry vets alike) is contributions to open source projects. You don't have to be the mastermind behind some new hot technology that all the sexy startups are using. Even small contributions to something you find useful or fun are a great thing to see. One of our recent hires (a new college grad) had contributed a good bunch of code to a minecraft mod, and had all the code up on his github profile. It was a big plus, and wound up being a major reason we hired him.











We're constantly looking for signals that your work might be relevant. The more calibrated we are, the more accurate we'll be; which echoes much of what has been said.

What actually comes into play for a recruiter regarding GitHub are 2 key points of engagement:

First: if we found you because of a non GitHub signal like your LinkedIn, Stackoverflow, a Patent etc and notice you have a GitHub, we'll typically ask about it to find out if there are meaningful projects you'd like to highlight to our client manager.

Second: if we actually found you through your contributions to a relevant project, well, that is all the GitHub we need. For example: maybe we're looking for someone to build a new JS framework and are impressed by your contributions to a popular flavor, we have a good idea you could probably contribute to our project.

So we either found you though other means and might ask you if you're proud of any open projects or we found you directly from them.






[–]csharpcheddar 62 points 2 years ago*

I'm a senior dev who conducts interviews at a fortune 500 company. I look for candidates to be "full stack" developers who understand the big picture. Full stack these days also includes DevOps skills, or at least an understanding of how devops works. I also look for candidates who emphasize user experience and take pride in their work.

If a junior candidate were to pick a technology stack, build a reasonably complex application with that stack, put it on the internet, and demo and talk through the application and technologies used, I would 100% give a hire recommendation.

e.g.

USA state capital lookup application. State capitals are retrieved on demand via AJAX query that hits a server side endpoint.

- Sample stack
	- Front end: Angular, bootstrap.
	- Back end: asp.net WebAPI
	- Database: MySql
	- Hosting: Azure App Service
- Hypothetical Questions
	- Talk me through how this application works. What code executes, where, and when?
	- What development tools did you use?
	- Why did you choose Angular? Why use a JS framework at all?
	- What does Boostrap do? Why is that important?
	- Talk me through the build and deployment process.
	- What challenges did you have?
	- How do you think you could you improve this application?
	- permalinkembedsave

[–]get-your-shinebox 19 points 2 years ago*

To be hipper I'd do:

angular -> react

mysql -> postgres

azure -> aws








# Jobs


# Career / Interview



https://old.reddit.com/r/cscareerquestions/wiki/index


## Code Interview Tips

https://old.reddit.com/r/learnprogramming/comments/b9z8c0/some_advice_to_software_engineering_candidates/

I'm a software engineer at a large company based in the bay and I've recently been interviewing people quite a bit to fill mid career full stack engineering and QA Automation engineer roles. After awhile I've noticed some patterns from applicants that I wanted to share for anyone actively looking for work. These have come up multiple times in round table discussions with other interviewers about candidates and seem like easy gets if people were aware of them:

	1. When doing a technical problem always explain what your game plan is before you begin to solve the challenge and why you think it will work. There is usually a brute force or naive solution that you can reach somewhat easily and many applicants jump into coding that immediately before discussing their thoughts. Depending on the role, this may or may not be acceptable, but if I'm looking for something more complex I'm happy to nudge the candidate toward a better method if that's what I'm looking for. If I just want the naive solution, I'll say its fine and to proceed - going super complex right out of the gate without explaining the naive solution may make it seem like you're over-engineering the problem or aren't practical (especially if your complex solution is wrong). I get the sense that most candidates are anxious to prove that they can code and dive in hastily. This is considered a red flag and usually results in negative marks in the critical thinking column.
	2. Start with test cases. Even if you don't practice test driven development, this shows foresight and gives the interviewer a chance to course correct fundamental misunderstandings about the problem at hand. Even if you don't execute them by the end, write them in comments - show the input and expected output. Try to think up as many edge cases as possible. Once you're most of the way through the problem and you realize you fundamentally misunderstood something its too late for me to help.
	3. If you stop talking for more than a minute people become worried about your ability to communicate your thought process. Even if you're stuck, talk about why you're stuck and if you are unable to make progress just admit it and I'm happy to offer some leading hints. I want to see that you can think critically and program, not that you know the 'trick' to getting the optimal solution.
	4. If you can only do the naive solution and you're not prompted for something harder, try to explain the more complex solution when you're done as best you can. I've passed multiple people through phone screens who would not otherwise have gotten through because I knew they understood that their solution wasn't the best, they just didn't think of the optimal one immediately. If we have time and I want to see something more complex I'll ask you to try to implement it.
	5. In your questions for the interviewer ask about the team. Often the deciding factor for myself and my colleagues concerning a couple of candidates has been whether we got the feeling that the person would be satisfied in the role they're applying for. We don't want to hire someone who is going to leave in a year, engagement is incredibly important. On multiple occasions we have selected someone who was not quite as technically advanced as someone else because they seemed enthusiastic about what the team was working on.

For such a simple problem, I've actually seen a huge variation in the kinds of solutions that are provided, even among people of similar experience and ability. Some people write a concise 20 line function and call it job done while some go the opposite direction and create a fully object oriented solution with multiple classes. Neither is necessarily any more correct than the other. Aside from weeding out the people who just can't program or who write awful code, what it's great for is differentiating between people who just know how to write code, and people who actually know how to engineer software, and there is a big difference.

Aside from the basics - does it actually solve the problem correctly and with reasonably well written code - what I'm really looking for are things like unit tests, documentation, build instructions (or better yet, a nice cross-platform build script), explicitly stated assumptions (e.g. whether or not to do any input validation and if so, how to handle error cases) and the overall approach.

I then spend a good portion of the interview discussing the candidate's solution. I ask them how they decided on the solution that they did, what alternatives they considered, what - if any - problems they ran into, whether they would change anything in retrospect etc. I then ask them to discuss how they would modify their solution to cope with certain changes to the requirements. What if you now had to run this on a microcontroller with a very limited amount of memory? Now what if this operation that they were assuming would be fast was actually connected to a very slow piece of hardware that took a second to respond? That kind of thing.

I've found that this is a much better indicator of ability than getting people to try to write code on a whiteboard under pressure. I can't write code on a whiteboard! Nobody codes by writing line 1, then line 2, then line 3. You end up inserting lines, moving things around, filling in loop bodies after creating the loop structure etc. Not only that, but in practice, we spend a lot of time looking up documentation and, let's be honest, places like stackoverflow. It's just not worth wasting the time to memorize a large standard library or, in some cases, certain aspects of the language or syntax (moreso for things like C++) when I can just spend 10 seconds on Google to find if the function I need exists or what is the correct signature for a move constructor again. So asking somebody to stand up at a whiteboard and do it blind is unfair, I think.








### Resume Tips

https://old.reddit.com/r/cscareerquestions/comments/bgxgu6/im_22_i_havent_applied_to_more_than_20_companies/

I read a lot about people applying to 300 jobs and getting like 2 callbacks, but I had a very different experience. I wanted to share some of my tips that I've learned.

    I never applied a ton, I had connections. In college I joined a professional fraternity and 4 out of the 6 jobs I got were through people I knew who worked there. You get your resume handed right to the manager instead of through HR. I recommend making friends with people in your class, or finding somebody else with a strong network and free-loading off of theirs (and buy them lunch or something). Furthermore, people you know there can give you invaluable advice on what is going to be on the interview/what the hiring manager is like, etc.
    I made friends with the "CS gods" who were role models in my class. Then, I just ask them for their resume, for them to look at mine, for their advice, their compensation and negotiation tactics, etc. It's not like the med field where other people want the competition to fail, I rarely meet any SWE who DOESN'T want to help others get a job.
    Even when I cold apply, NEVER apply on the website, there's too many people that do that. Instead, I find a recruiter on Linkedin, I find their WORK EMAIL with this extension (https://connect.clearbit.com/), and I email them DIRECTLY with my resume, my interest, and a blurb showing that I've researched the company.
    (only applies to US citizens) This sounds shitty, but if you have an asian sounding name and you ARE a citizen, put that you're a citizen on there. Some recruiters will toss resumes JUST because they're asian and the company can't sponsor, even if you are a citizen. I literally put "US Citizen" next to my phone number, linkedin, and github.
    Interviewing is honestly all about confidence. You have to be a salesman. You can't just be good at coding and suck at talking, or vice versa. I don't really study that much the day before an interview (that's for the weeks before), I just go on walks, run, do jumping jacks, get my blood flowing so that I feel the most alive I can be before stepping in to the room.
    credit to u/Chewbahka72, but if you don't have experience just apply to smaller companies, instead of FB/Apple/Google/MSFT. There's a reason those companies pay so well, it's cause everybody has tons of experience, it's ok to start at smaller companies where you can get good tech experience without the cool free food benefits and the company jerking you off while you work.

Let me know if you want me to take a look at your resume or anything!

EDIT: RESUME TIPS:

I got some PMs about resumes, I'll take a look at them but here are my tips for resumes:

    Don't use Arial, Calibri, Times New Roman. I know this might be an unpopular opinion, but if you want to get a job (esp. in Silicon Valley), make it unique. DO put some interest in design. I'm not saying make the whole thing in LaTeX or get Elon Musk to lick it before applying, but try some different fonts and dear God learn to right justify text on the same line. (https://fonts.google.com/) (https://fontawesome.com/?from=io - for LinkedIn, github, email, phone# icons). I use Open Sans and Raleway
    Use PROBLEM, SOLUTION, IMPACT. Indicate the PROBLEM you're trying to solve, then indicate how you SOLVED it (what language, framework, architecture, system, design), and then talk about IMPACT (financial - saved $42069k, operational - less people needed to do this task now, time - saved 20% time on this operation). Here's an example: "Built a batch utility using Java, SQL, Hibernate to automate self-checking of the business's pricing processing system (SOLUTION), allowing the business to catch failed charges due to temporarily failed downstream services (PROBLEM mixed with a little bit of SOLUTION), which in one instance saved the company $2000 in revenue leak"
    Split up your skills into LANGUAGES and FRAMEWORKS/TECHNOLOGIES. Languages: Java, SQL, Python. Frameworks/Technologies: React, Redux, git, AWS, Docker
    Bold text that is important, make text lighter or smaller for text that is not important. IMPORTANT: Company names, Job title, headers. NOT AS IMPORTANT: employment durations, project times, company locations
    Just find a good-looking CS resume online or from a friend and copy the formatting. MS Word is honestly enough for the vast majority of cases.

EDIT 2: Here is my anonymized resume: https://drive.google.com/file/d/15fXupoIsyXC2qBskal6C-Czn9Hutl_8-/view?usp=sharing Not all my experience is on there, I put what I thought were the most valuable ones. I want to highlight that my resume doesn't have the biggest names on there in terms of company names, but I do think it is a strong one due to formatting, design, and wording.

EDIT 3: I had 4 internships in school (1 per summer, 1 in part time) and 2 full-time positions already, sorry for the confusion







    Write code. As much as you can. Until you can do it in your sleep. You might know all the algorithms, but if you haven't really practiced writing code (preferably on a whiteboard), you'll be sluggish in your interviews and the interviewer will pick up on it.
    
    Ask questions. Don't just jump into solving a problem blindly. It's amazing how many times the interviewer will give you an incomplete or ambiguous problem expecting you to ask more questions. Let them know of any assumptions that you may be making about speed, memory, error handling or input.
    
    Know your data structures as well as their complexity/applications. Somebody in this subreddit suggested Interview Cake and I can't stress how beneficial solving their 43 algorithm problems and going through each of the step-by-step solutions was. Some of the questions in my interview were simply variations of the problems I had already solved. I didn't have a lot money so I had bought a 50% off coupon from eBay for Interview Cake.
    
    Review regularly. I made notes of all problems that I had solved and kept reviewing them before interviews. Otherwise, I had trouble recalling the algorithms.
    
    Be honest. If they asked you a question or a technology that you don't know then there is no shame in admitting that you haven't had any experience with it but would be willing to pick it up as and when needed. Moreover, don't list things on your resume that you are only vaguely familiar with. You'd be surprised how frequently people list technologies that they are not comfortable with in their resume.








- Prepare two technical things or projects that you are

- Four stories of teamwork dealing with


- Think of different projects that you have been working on.
  - Anki, spaced repitition software.
  - You can also use a project like a client with backend and communication through API is a good service. How did you define the API, what was the communication mechanism (JSON, XML,00) how did the client did it get that data back, how language is it in. Talk about before technical interview.


Technical interview:
    - Don't get stuck on problem, ask if time and can jump questions.







# Social Engineer Your way into your dream job





- Budget:
  - "How much am I willing to spend to get my dream job?"
- Timeline:
  - "I want my dream job in 2 years or less"
- The keys to an effective sustained marketing campaign
  - Get people to know you exist
  - Give them a reason to care
  - Amaze them once they do
  - Repeat


## Reconnaissance

- "Who are my target companies"
  - How big are the walls?
  - Where are the cracks?
  - Who are the gate keepers?
  - Who is vulnerable to persuasion?
  - "But how do I figure this stuff out?"
    - OSINT Gathering Skills
      - "How much is too much?"

One method is using twitter or instagram, you can target viewers of certain accounts.



- [ ] Finish Video @30.00

https://www.youtube.com/watch?v=__lvS2pjuSg









### During the "So, do you have any questions phase of the interview" why is it recommend to ask "What does success look like in this role?" 

- Clears up any miscommunications about what the job is or what's expected. 
  -  Hours required, tasks required etc. 
- Tells how well suited you are to the job or the management style.
- Lets them know you're a go-getter.



###  A job interview goes both ways. Always keep that in mind.

- What options are there for advancement?
- Where do you see the company in 5 years?
- What do you offer in regards to educating the staff?
- Why is the position open?
- When can i expect to hear from you?
- Whats the average age and education level of the team i'll be working  with? (If its full of teens, it means they  have a large turnover rate)
- How do you like to work with company?



### Often the only thing running through the interviewers head is. "Can  this person fill the gap in my org, right now?"

Actual questions that show me that you are the right kind of person:

- What's the toughest part of the role I'm applying for?
- What was the team's biggest success in the last year? Mistake?
- From what we've discussed, what would I need to learn to get up to speed on this role?
- Can you give me an example where a current employee exceeded your expectations?

# Resume / Job Search






Started contributing to a semi-popular open-source Chrome extension the previous summer. Submitted a ton of resumes online; the only one which called me back was Mozilla, and it was primarily my OSS work that caught their eye. (Yes, they didn't mind that it was for a 'competing' browser.)

Moral: Open-source work = good. Online resume submissions = necessary evil, at best. Contacting recruiters via LinkedIn will get you a bit more attention.






### Resources
https://old.reddit.com/r/cscareerquestions/comments/36kbe3/what_are_the_main_different_type_of_programming/creq1x8/



Advanced job search skills

https://old.reddit.com/r/learnprogramming/comments/7hb7ka/learned_to_code_got_interview_at_google_but_i/
