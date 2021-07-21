

## Sprints

![[scrum_process_atlassian.svg]]

 Sprint planning is a collaborative event where the team answers two basic questions: What work can get done in this sprint and how will the chosen work get done?

 The product owner discusses the objective that the sprint should achieve and the product backlog items that, upon completion, would achieve the sprint goal.
 
 Making a plan to build backlog and subtasks to get them done. During the sprint these items go from "in-progress" to "done".
 
 The team implements a daily standup to check progression, blockages, and challenges. Afterwards is a sprint review to showcase with stakeholders. Then a restrospective to identify areas of improvement.
 
 Do;
 - Make sure the team sets and understands the sprint goal and how success will be measured.
 - Do ensure you have a well-groomed backlog with your priorities and dependencies in order.
 -   Ensure you have a good understanding of velocity, and that it reflects things like leave and team meetings.
 -   Leave out work where you won’t be able to get the dependencies done, like work from another team, designs, and legal sign-off.
 
 
 
 

### Sprint Planning
 **The What** –  The product owner describes the objective(or goal) of the sprint and what backlog items contribute to that goal.
 
**The How** – The development team plans the work necessary to deliver the sprint goal. A negotiation between the development team and product owner based on value and effort.

**The Who** – The product owner defines the goal based on the value that they seek. The development team needs to understand how they can or cannot deliver that goal

**The Inputs** – A great starting point for the sprint plan is the product backlog as it provides a list of ‘stuff’ that could potentially be part of the current sprint. 

**The Outputs** – The most important outcome for the sprint planning meeting is that the team can describe the goal of the sprint and how they will start working toward that goal. This is made visible in the sprint backlog.

Set a time limit for sprint planning, ideally no more than two hours. 

Use User stories to define clear outcomes; 
As a \<type of user>, I want \<a goal> so that \<a reason>

Do planning poker to make estimation of different user stories and time limits

 Focus the first part of sprint planning on the objective of the sprint rather than the details of the backlog. By focusing on the goal rather than the work it is possible to find smart alternatives for how that goal is achieved.

### Ceremonies
Use the sprint planning meeting to flesh out intimate details of the work that needs to get done. Encourage team members to sketch out tasks for all stories, bugs, and tasks that come into the sprint. Foster discussions and gather consensus on the plan of action. Effective planning significantly increases the team's chances of success meeting the commitments of the sprint.

**Daily Standup**, once per day no more than 15m and answer;
-   What did I complete yesterday?
-   What will I work on today?
-   Am I blocked by anything?

#TODO: Make sprint question sheet

#NOTES:

There's an implicit accountability in reporting what work you completed yesterday in front of your peers.

Pro TIp:
Some teams use timers to keep everyone on track. Others toss a ball across the team to make sure everyone's paying attention. Many distributed teams use videoconferencing or group chat to close the distance gap. Your team is unique. Your stand up should be, too!

**Iteration Review** At the end of a sprint or milestone for 30-60m to showcase the work of a team ("demo fridays"). Celebrate accomplishments and get immediate feedback from stakeholders.

**Retrospective** for 60m where you *use retrospectives to* find out what's working so the team can continue to focus on those areas. Also, find out what's not working and use the time to find creative solutions and develop an action plan. Continuous improvement is what sustains and drives development within an agile team,

### Backlogs

A product backlog is a prioritized list of work for the development team that is derived from the roadmap and its requirements. The most important items are shown at the top of the product backlog so the team knows what to deliver first. The development team doesn't work through the backlog at the [product owner's](https://www.atlassian.com/agile/product-management) pace and the product owner isn't pushing work to the development team. Instead, the development team pulls work from the product backlog as there is capacity for it, either continually ([kanban](https://www.atlassian.com/agile/kanban)) or by iteration ([scrum](https://www.atlassian.com/agile/scrum)).


Pro Tip:
Keep everything in one issue tracker–don’t use multiple systems to track bugs, requirements, and engineering work items. If it's work for the development team, keep it in a single backlog.

#TODO: Integrate Jira, Slack & Git

#### Roadmaps & Requirements

An example for a space travel company. 

![[Pasted image 20210719130944.png]]

After planning a timeline, you want to break down your product into epics. The product owner with feedback then organizes each user story into a single list for the development team. 

What may influence a product owner's prioritization?

-   Customer priority
-   Urgency of getting feedback
-   Relative implementation difficulty
-   Symbiotic relationships between work items (e.g. B is easier if we do A first)

![[Pasted image 20210719130952.png]]

Also multi epics exist where you may use it to test integration for example booking a discounted flight. 

![[Pasted image 20210719131222.png]]

Product owners should review the backlog before each iteration planning meeting to ensure prioritization is correct and feedback from the last iteration has been incorporated. Regular review of the backlog is often called "backlog grooming" in agile circles.

Once the backlog gets larger, product owners need to group the backlog into near-term and long-term items. Near-term items need to be fully fleshed out before they are labeled as such. This means complete user stories have been drawn up, collaboration with design and development has been sorted out, and estimates from development have been made. Longer term items can remain a bit vague, though it's a good idea to get a rough estimate from the development team to help prioritize them.

Once work is in progress, though, keep changes to a minimum as they disrupt the development team and affect focus, flow, and morale. Once the backlog grows beyond the team's long term capacity, it's okay to close issues the team will never get to. Flag those issues with a specific resolution like “out of scope” in the team's issue tracker to use for research later.

**Anti-patterns to watch for**
-   The product owner prioritizes the backlog at the start of the project, but doesn't adjust it as feedback rolls in from developers and stakeholders.
-   The team limits items on the backlog to those that are customer-facing.
-   The backlog is kept as a document stored locally and shared infrequently, preventing interested parties from getting updates.

All work items should be included in the backlog: user stories, bugs, design changes, technical debt, customer requests, action items from the retrospective, etc. This ensures everyone's work items are included in the overall discussion for each iteration. Team members can then make trade-offs with the product owner before starting an iteration with complete knowledge of everything that needs to be done.

Product owners dictate the priority of work items in the backlog, while the development team dictates the velocity through the backlog. This needs to be balanced. 

### Reviews

Sprint reviews are not retrospectives. A sprint review is about demonstrating the hard work of the entire team: designers, developers, and the product owner.

#### **Step 1: define ‘done’**

Crossing the finish line and completing work requires good planning, a clear definition of ‘done,’ and focused execution. A culture of delivery.

-   Are stories well-defined by the product owner, designer, and the engineering team before implementation?
-   Does everyone understand and live the team’s engineering values and culture?
-   Are there clear definitions and requirements around [code review](https://www.atlassian.com/agile/software-development/code-reviews), automated testing, and [continuous integration](https://www.atlassian.com/agile/software-development/continuous-integration) to encourage sustainable, [agile development](https://www.atlassian.com/agile/software-development/developer)?
-   After the team completes a story, are there many bugs that surface? In other words, does ‘done’ really mean ‘done?’


To define something as done you must have;
-   **Acceptance criteria**: metrics the product owner uses to confirm the story has been implemented to his or her satisfaction.
-   **Testing notes**: short, focused guidance from the quality assistance team that enables the development engineer to write better feature code and automated tests.

#### Step 2: Celebrate the team
We love sprint reviews because they protect the health and morale of the team. Sprint reviews are all about team building. The review isn’t adversarial, it’s not an exam—it’s a collaborative event across the team in which people demo their work, field questions, and get feedback.

If a sprint review doesn’t become a positive activity across the team, it may be indicative of:

-   The team taking on too much work and not completing it during an iteration
-   The team struggling with existing technical debt
-   Features not being developed sustainably to ensure new bugs are not introduced into the codebase
-   The team’s development practices aren’t as tuned as they could be
-   The product owner is changing priorities within an iteration, and the development team is sidelined by scope creep


#TODO: Random; make scripts for easier copying and pasting to obsidian. One window to another. 

#### Step 3: reach across geographies
If working on a remote team it is good for Team members create informal videos and share them on a [Confluence](https://www.atlassian.com/software/confluence) page for the entire team to see.

This helps by;
-   **Product Understanding**: the entire team gets to hear the intention, rationale, and implementation of the feature. It broadens everyone’s understanding of the entire product.
-   **Team Building**: videos create more personal connections across the team. Each of us gets to see who’s behind every aspect of a product. The bridges created by this practice makes us a tighter, more cohesive group despite geographies.


For teams that are new to sprint reviews, there’s a strong temptation to bleed sprint review into the retrospective. A sprint review is an independent ceremony from a sprint retrospective.

### Standups
> Stand-ups are one of the fundamental parts of agile development, and it’s often the most misunderstood. Let’s be real: stand-ups by themselves don’t make your team agile. They aren’t about inflating egos or justifying job descriptions. They aren’t a time to plan; Sprint planning is for planning. They also aren’t the only time to mention blockers. If you’re stuck, ask for help!


To start;
-   What did I work on yesterday?
-   What am I working on today?
-   What issues are blocking me?


At Atlassian, individuals use [Jira](https://www.atlassian.com/software/jira) boards to keep on top of their projects with quick filters. Two great filters that can be used together to help prepare for stand-up are “only my issues” and “recently updated.” When these two filters are used together, they show the issues assigned to you and that have been updated in the last day.

One popular customization of the Only My Issues filter is to add the participants field from the [Jira Toolkit Add-on](https://marketplace.atlassian.com/search?query=jira%20toolkit). This adds any issues you’ve touched rather than just issues assigned to you. The JQL for that filter would be:

`assignee = currentuser() or participants in (currentuser())`


#### Standups
1. Choose a time that works for everyone. 
2. Keep it effecient. Rotate who keeps time to make sure everyone is accountable and invested. Limit the duration of stand-ups to 15 mins–max.
3. Play catch to keep people focused.
4. **Make the stand-up a part of the team’s retrospective** – Stand-ups are part of many agile cultures, but it doesn’t mean that the team can’t discuss the effectiveness of stand-ups in retrospectives


If your team is remote make members visible, reference your scrum board, and be open to asynchrynous standups through slack.

### Scrum Master

As facilitators, scrum masters act as coaches to the rest of the team. “Servant leaders” as the Scrum Guide puts it. 

Responsibilities include; 

1.  **Standups** - Facilitate daily standups ......(or the daily scrum) as needed.
2.  **Iteration/sprint planning meetings** – Protect the team from over-committing and scope creep. Aid in estimation and sub task creation.
3.  **Sprint reviews** – Participate (in the meeting) and capture feedback.
4.  **Retrospectives** – Note areas for improvement and action items for future sprints.
5.  **Board administration** – Work as the administrator of the scrum board. Ensure that cards are up to date.
6.  **1 on 1s** – Meet individually with team members and stakeholders as needed. Iron out team disagreements about process and work styles. Invidual interactions are crucial for team development and getting to know one another.
7.  **Internal Consulting** – Scrum masters should be prepared to consult with team members and internal stakeholders on how best to work with the scrum team.
8.  **Reporting** – Regular analysis of [burndown charts](https://www.atlassian.com/agile/tutorials/burndown-charts) and other portfolio planning tools to understand what gets built and at what cadence.
9.  **Blockers** – The scrum master aids the team by eliminating external blockers and managing internal roadblocks through process or workflow improvements.
10.  **Busy work** – If the scrum team isn’t humming, that’s the scrum master’s problem. Maybe that means fixing broken computers, moving desks around, or even adjusting the thermostat. Scrum masters should be comfortable doing just about anything to help their team and should be not slink away from grabbing coffees or some snacks if that’s what the team really needs.


#### Scrum Master vs Product Manager
That involvement should be along the lines of a product owner who champions customer needs, the "why" of the product. When the involvement blurs into tasking, the "how" for a team, then there is a problem. 

Even with the best of intentions, this kind of utilization mindset tends to hide problems: defects, hand-offs, and unknowns. Interleaving scope and process tends toward locking scope, schedule, and quality. That's a recipe for failure. That's why the scrum master and product owner fill two different needs on a scrum team.

Having a scrum master in place helps balance the cost of changing course with the benefits of efficiency. A good scrum master does this by empowering the team to decide how to best accomplish goals through self-organization

The project manager sets and tracks timeframes and milestones, reports on progress, and coordinates team communication. However, they do so from a place of control, in a more traditional management role.

The scrum master helps the team enhance and streamline the processes by which they achieve their goals. They do so as a team member, or collaborator, ideally not as someone in control. The best scrum teams are self-organizing, and therefore don’t react well to top-down management.


