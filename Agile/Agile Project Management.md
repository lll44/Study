# Intro

## What is agile project management?

[Agile project management](https://www.atlassian.com/project-management) is an iterative approach to delivering a project, which focuses on continuous releases that incorporate customer feedback. The ability to adjust during each iteration promotes velocity and adaptability. This approach is different from a linear project management approach, which follows a set path with limited deviation. Agile project management is also a cornerstone of [DevOps practices](https://www.atlassian.com/devops/what-is-devops), where development and operations teams work collaboratively.

## Waterfall versus agile

![Waterfall release example | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:75f1a49a-c071-4c59-a820-aa5dfbf8bfbe/waterfall_release_process.svg?cdnVersion=1721)

The waterfall model can exacerbate some of the known challenges of building products:

-   Blockers and dependency management: Traditional project management styles often create "critical paths", where the project can't move forward until a blocking issue is resolved.
-   Difficulty getting user feedback and product validation: the end customer can't interact with the product until it's fully complete. Important issues in the product design and code go undiscovered until release.

Iterative releases unlock multiple opportunities for a team to:

-   adapt to changing circumstances from newly discovered requirements to a blocked piece of work.
-   gather feedback from stakeholders during the process and iterate responsively without the stress of a final delivery deadline.
-   build relationships and connections across roles that make it easier for people to connect and communicate effectively.

Agile allows teams to be more resilient to changes that inevitably occur during a project.

![Agile project management example | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:cbb1fb08-0fd5-4a63-bf4e-76bfe0578512/agile_release_train.svg?cdnVersion=1721)


## Agile principles

-   An agile project is segmented into several incremental steps that include regular feedback intervals.
-   A project requirement is segmented into smaller pieces, which are then prioritized by importance.
-   Promotes collaboration, especially with the customer. 
-   Adjusts at regular intervals to ensure a customer’s needs are met
-   Integrates planning with execution, which allows a team to effectively respond to changing requirements  

### Elements to consider when moving to agile

When adopting agile principles, a team and the stakeholders must embrace two important concepts:

-   The product owner's focus is to optimize the value of the team's output. The team relies on the product owner to prioritize the most important work first.
-   The development team can only accept work that it has the capacity for. The product owner doesn't push work to the team or commit them to arbitrary deadlines. The development team pulls work from the program's backlog as it can accept new work.

Let's explore the mechanisms agile programs use to organize, run, and structure work in an iterative way.

### Roadmaps

A [product roadmap](https://www.atlassian.com/agile/product-management/roadmaps) outlines how a product or solution develops over time. A roadmap in agile development provides important context that empowers teams to reach both incremental and project-wide goals. 
Roadmaps are composed of initiatives, which are large areas of functionality, and include timelines that communicate when a feature will be available. It's accepted that the roadmap will change to reflect that new information - possibly in subtle or broad ways. 
The goal is to keep the roadmap focused on current conditions that impact the project and long-term goals in order to effectively work with stakeholders and respond to the competitive landscape. 

The following is a simple roadmap for a product team, with initiatives in the boxes and timelines indicated by the milestone-markers in red. 

![Agile roadmap | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:e1f6f163-4ea6-40f9-87ef-3e9479623a76/agile_roadmap.svg?cdnVersion=1721)

## Requirements

Each [initiative](https://www.atlassian.com/agile/product-management/requirements) in the roadmap breaks down into a set of requirements. Agile requirements are lightweight descriptions of required functionality, rather than the 100-page documents associated with traditional projects. They evolve over time and capitalize on the team's shared understanding of the customer and the desired product. Agile requirements remain lean while everyone on the team develops a shared understanding via ongoing conversation and collaboration. Only when implementation is about to begin are they fleshed out with full details.

## Backlog

The [backlog](https://www.atlassian.com/agile/scrum/backlogs) sets the priorities for the agile program. The team includes all work items in the backlog: new features, bugs, enhancements, technical or architectural tasks, etc. The product owner prioritizes the work on the backlog for the engineering team. The development team then uses the prioritized backlog as its single source of truth for what work needs to be done.

## Agile metrics

Agile teams thrive on [metrics](https://www.atlassian.com/agile/project-management/metrics). [Work in progress](https://www.atlassian.com/agile/kanban/wip-limits) (WIP) limits keep the team, and the business, focused on delivering the highest priority work. Graphs like [burndown charts](https://www.atlassian.com/agile/tutorials/burndown-charts) and control charts help the team predict their delivery cadence, and continuous flow diagrams help identify bottlenecks. These metrics and artifacts keep everyone focused on the big goals and boost confidence in the team's ability to deliver future work. 

## Agile runs on trust

Agile processes cannot function without a high level of trust amongst team members and therefore create trust. It requires candor to have difficult conversations regarding what's right for the program and the product. Because conversations happen at regular intervals, ideas and concerns are regularly expressed. That means team members need to be confident in each other's ability (and willingness) to execute on the decisions made during those conversations.

# Workflow 
## Start simple, start now

When implementing a workflow for the team, always start simple. Overly complex workflows are hard to understand and adopt–not to mention adapt. 

For software teams, we recommend these basic workflow states:

- **To Do** Work that has not been started

- **In Progress** Work that is actively being looked at by the team

- **Code Review** Work that is completed and awaiting review

- **Done** Work that is completely finished and meets the team's definition of done

In an issue tracker, these statuses flow from one to the next using transitions that structure the workflow. 

![Agile workflow | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:b05f60d5-04a0-4ef1-b2f6-c329bcbdd068/AgileWorkflow.svg?cdnVersion=1721)

### Optional workflow states

Some software teams include additional states in their workflow that help them track the status of work more precisely.

**Awaiting QA** Work that has been implemented, but is still waiting for a tester review (see our article on [agile testing](https://www.atlassian.com/agile/software-development/testing) for more details).

**Ready to merge** Code that has been reviewed and is ready to merge into the main or release branch.

Each state in the workflow doesn't need to be handled by a different person. Developers can do work–from design all the way through to delivery.

[Healthy workflows adapt to the needs of the team. Occasional pain is normal. Chronic pain is not.](https://twitter.com/intent/tweet?text=%20%20Healthy%20workflows%20adapt%20to%20the%20needs%20of%20the%20team.%20Occasional%20pain%20is%20normal.%20Chronic%20pain%20is%20not. &url=https://www.atlassian.com/agile/project-management/workflow&via=Atlassian)

- Discuss each pain point in the team's retrospective.
- Issue trackers should have a flexible workflow configuration.

## Optimize the workflow

Once comfortable with the basic workflow then customize it.
Create statuses for each type of work in a team's process.
Ideation, design, development, code review, and test are functionally different and can be individual statuses. Aim for a lean set of statuses that clearly communicate what phase a piece of work is in.

A well designed workflow answers the following questions:

-   What work has the team completed?
-   Is the backlog of work increasing or keeping pace with the team?
-   How many items are in each status?
-   Are there any bottlenecks that are slowing the team down?
-   How long does it take to complete an average task?
-   How many work items didn't pass our quality standards the first time around?

The next step in optimizing the workflow is a steady stream of work through the workflow. 

*Work in progress (WIP) limits* dictate a minimum and maximum number of issues in a particular state of the workflow, ensuring each state has enough work to keep the team fully utilized, but not so much that it loses focus from juggling priorities. Enforcing WIP limits will quickly show which processes slows overall work through the pipeline. As the team learns to optimize around its WIP limits, throughput will increase. (See the article on [WIP limits](https://www.atlassian.com/agile/kanban/wip-limits) for more details.) 

# Epics, Stories, Themes
### What are stories, epics, initiatives, and themes?

-   **[Stories](https://www.atlassian.com/agile/project-management/user-stories)**, also called “user stories,” are short requirements or requests written from the perspective of an end user.
-   **[Epics](https://www.atlassian.com/agile/project-management/epics)** are large bodies of work that can be broken down into a number of smaller tasks (called stories).
-   **Initiatives** are collections of epics that drive toward a common goal.
-   **Themes** are large focus areas that span the organization.

![Agile epics vs stories vs themes | Atlassian Agile Coach](https://wac-cdn.atlassian.com/dam/jcr:c79bf6d8-3101-48c3-bf2b-506b5bc53ccc/Themes.png?cdnVersion=1724)

## Agile epic vs. story

similar to stories and epics in film or literature. 
A story is one simple narrative; a series of related and interdependent stories makes up an epic. 

Stories are something the team can commit to finish within a one or two-week sprint. 

Typically developers would work on dozens of stories a month. Epics, in contrast, are few in number and take longer to complete. Teams often have two or three epics they work to complete each quarter.

### Examples of an agile story:

-   iPhone users need access to a vertical view of the live feed when using the mobile app.
-   Desktop users need a “view fullscreen” button in the lower right hand corner of the video player.
-   Android users need to be linked to apple store.

[Learn how to configure stories(called issues) in Jira Software](https://www.atlassian.com/agile/tutorials/issues)

The above stories are all related, and could all be considered individual tasks that drive toward the completion of a larger body of work (an epic). In this case, the epic might be **“Improve Streaming Service for Q1 Launch.”**

If you were reporting your team’s progress to the Head of Engineering, you’d be speaking in epics. If you were talking to a colleague on your development team, you’d speak at the story level.

#### For complete definitions, examples and best practices, see:

-   [The Agile Coach: Epics](https://www.atlassian.com/agile/project-management/epics)
-   [The Agile Coach: Stories](https://www.atlassian.com/agile/project-management/user-stories)

## Agile epic vs. initiative

- initiatives are made up of epics. 
- Initiatives offer another level of organization above epics.
- An initiative compiles epics from multiple teams to achieve a much broader, bigger goal than any of the epics themselves. 
- an epic is something you might complete in a month or a quarter, initiatives are often completed in multiple quarters to a year.

![Example user stories | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:a679339b-0098-4c88-acdb-7009b0de6efb/epics-vs-stories-agile-development.png?cdnVersion=1724)

**Example of epics in an initiative:**

Let’s say your rocket ship company wants to decrease the cost per launch by 5% this year. That’s a great fit for an initiative, as no single epic could likely achieve that big of a goal. Within that initiative, there would be epics such as, “Decrease launch-phase fuel consumption by 1%,” “Increase launches per quarter from 3 to 4,” and “Turn all thermostats down from 71 to 69 degrees #Dadmode.”

NEXT: [Learn how to configure Agile Epics](https://www.atlassian.com/agile/tutorials/epics)

## Initiatives vs. themes

-   Initiatives are collections of epics
-   Themes are labels that track high-level organizational goals

Initiatives have a structural design. They house epics, and the completion of those epics will lead to the completion of the initiative. 

Themes allow you to label backlog items, epics, and initiatives to understand what work contributes to what organizational goals. 

Themes should inspire the creation of epics and initiatives but don’t have a ridgid 1-to-1 relationship with them. 

A theme for a rocket ship company would be something like “Safety First.”

This is what themes look like in [Advanced Roadmaps for Jira](https://www.atlassian.com/software/jira/features/roadmaps):

![Example of a sprint | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:08310990-20ef-4930-954a-3345f35f86f7/Sample%20Set.png?cdnVersion=1724)

# Epics
an epic serves to manage tasks. It's a defined body of work that is segmented into user stories based on the needs/requests of customers or end-users.

Epics are a helpful way to organize your work and to create a hierarchy. The idea is to break work down into shippable pieces so that large projects can actually get done and you can continue to ship value to your customers on a regular basis. Epics help teams break their work down, while continuing to work towards a bigger goal.

## What is an agile epic?

An epic is a large body of work that can be broken down into a number of smaller *stories* .

Epics are almost always delivered over a set of sprints. As a team learns more about an epic through development and customer feedback, user stories will be added and removed as necessary. 

That’s the key with agile epics: 
- Scope is flexible, based on customer feedback and team cadence.  

## Agile epic example

Let’s say it’s 2050 and we work for a recreational space-travel organization. We do about a dozen launches a year, so each launch isn’t the single biggest thing we do in a year, but it’s still far from routine and will take many person-hours to complete. That sizing is just right for an epic.

An example epic, “March 2050 Space Tourism Launch” includes stories for routine work items as well as stories aimed to improve key aspects of the shuttle launch, from customers buying space travel tickets to the launch of the rocket itself. As such, multiple teams will contribute to this epic by working on a wide range of stories.

The software team supporting the purchasing of tickets for the March 2050 launch might structure their epic as so:

Epic: March 2050 Launch

Story: Update date range to include March 2050 Launch dates.

Story: Reduce load time for requested flight listings to < 0.45 seconds

Story: Promote Saturn Summer Sale on confirm page for First Class bookings.

Concurrently, the propulsion teams might contribute to the same epic with these stories:

Epic: March 2050 Launch

Story: Keep fuel tanks PSI > 250 PPM on launch

Story: Reduce overall fuel consumption by 1%.

Story: Hire new propulsion engineer to replace Gary.

## Understanding epics within a complete agile program

An epic should give the development team everything they need to be successful. From a practical perspective, it’s the top-tier of their *work hierarchy*. However, understanding how an epic relates to other agile structures provides important context for the daily dev work.

-   A **product roadmap** is a plan of action for how a product or solution will evolve over time. Expressed and visualized as a set of **initiatives** plotted along a timeline.
-   A **theme** is an organization goal that drive the creation of epics and initiatives.
-   Breaking initiatives into **epics** helps keep the team’s daily work — expressed in smaller stories — connected to overall business goals.

A set of completed epics drives a specific initiative.

![Example user stories | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:c79bf6d8-3101-48c3-bf2b-506b5bc53ccc/Themes.png?cdnVersion=1724)

## Creating an agile epic
-   **Reporting** — Create epics for the projects that managers and executives will want to keep an eye on.
-   **Storytelling** — Use epics, and the stories that roll up into them, as a mechanism to tell the story of how you arrived at the current state of a feature or product.
-   **Culture** — Let organizational culture dictate the size and granularity of an epic.
-   **Time** — Most development teams rely on estimation frameworks instead of time, but it’s a worthwhile gut check to make sure your epics will take a couple weeks to complete. Not too long and not too short.

[See how Epics work in Jira](https://www.atlassian.com/agile/tutorials/epics).

## Break down an agile epic

Breaking down an epic into more practical stories helps in understanding a project and maintaining momentum, consider:

-   **User role or persona** — Create a unique story for each user persona. “Quicker login for new visitors,” “quicker login for return customers,” etc.
-   **Ordered steps** — Break down the process and create a story for each step.
-   **Culture** — Let team norms dictate if a story is a quick task or a week-long project.
-   **Time** — Barring another agreed-upon convention, design stories that can be completed in one print or less.

There is no universal definition that draws a line between a big story and an epic. In general, any scope of work that the team estimates at “weeks” (or longer) to complete, rather than “hours” or “days” should be considered an epic and broken down into smaller stories.

## Measuring agile epics

Burndown charts visualize epics.

An Epic Burndown Chart shows the actual and estimated amount of work to be done in a sprint or epic. The horizontal x-axis in a Burndown Chart indicates time, and the vertical y-axis indicates stories or issues.

![Agile burndown chart | Atlassian agile coach](https://wac-cdn.atlassian.com/dam/jcr:ca3f2d90-5217-4886-b6db-b368dd5a1fdd/EpicBurndownChart.svg?cdnVersion=1724)

By monitoring a Burndown Chart, it becomes clear how the team is progressing and where the  blockers are. 

Keeps everyone on the same page 

Facilitates open conversation about the evolution of the product and completion forecasts.

## Optimize your epics with automation
#todo

three of the most common automation rules used for sprints in Jira.

1.  Automatically add 3 stories upon the creation of an epic. [Go to rule](https://www.atlassian.com/software/jira/automation-template-library/rules#/rule/112180).
2.  Auto-close stories when the epic is marked as done. [Go to rule](https://www.atlassian.com/software/jira/automation-template-library/rules#/rule/115382).
3.  Change the status of an epic when the status of one of its linked issues changes. [Go to rule](https://www.atlassian.com/software/jira/automation-template-library/rules#/rule/1357123).

# User stories
_user story is an informal, general explanation of a software feature written from the perspective of the end user. Its purpose is to articulate how a software feature will provide value to the customer._

user stories are not software system requirements. It’s an end goal, not a feature, expressed from the software user’s perspective.

A user story puts end users at the center of the conversation. These stories use non-technical language to provide context for the development team and their efforts. 

After reading a user story, the team knows why they are building, what they're building, and what value it creates. 

A user story is the smallest unit of work in an agile framework. An informal, general explanation of a software feature written from the perspective of the end user or customer. 

user story articulates how a piece of work will deliver a particular value back to the customer. Note that "customers" don't have to be external end users in the traditional sense, they can also be internal customers or colleagues within your organization who depend on your team.

User stories are a few sentences in simple language that outline the desired outcome. They don't go into detail. Requirements are added later, once agreed upon by the team.

User stories are added to sprints and “burned down” over the duration of the sprint. It’s this work on user stories that help scrum teams get better at **estimation** and **sprint planning**, leading to more accurate forecasting and greater agility.

User stories are also the building blocks of larger agile frameworks like epics and initiatives. Epics are large work items broken down into a set of stories, and multiple epics comprise an *initiative*. These larger structures ensure that the day to day work of the development team (on stores) contributes to the organizational goals built into epics and initiatives.

## Why create user stories?

User stories serve a number of key benefits:

-   **Stories keep the focus on the user.** keeps the team focused on tasks that need checked off, the collection of them keeps the team focused on solving problems for real users.  
     
-   **Stories enable collaboration.** With the end goal defined, the team can work together to decide how best to serve the user and meet that goal.  
     
-   **Stories drive creative solutions.** Stories encourage the team to think critically and creatively about how to best solve for an end goal.  
     
-   **Stories create momentum.** With each passing story the development team enjoys a small challenges and a small win, driving momentum.  

## Working with user stories

Once a story has been written, it’s time to integrate it into your workflow. Generally a story is written by the product owner, product manager, or program manager and submitted for review.

During a sprint or iteration planning meeting, the team decides what stories they’ll tackle that sprint. Teams now discuss the requirements and functionality that each user story requires. This is an opportunity to get technical and creative in the team’s implementation of the story. Once agreed upon, these requirements are added to the story.

Another common step in this meeting is to score the stories based on their complexity or time to completion. A story should be sized to complete in one sprint, so as the team specs each story, they make sure to break up stories that will go over that completion horizon.  

## How to write user stories

Consider the following when writing user stories:

-   **Definition of “Done”** — The story is generally “done” when the user can complete the outlined task, but make sure to define what that is.  
     
-   **Outline subtasks or tasks** — Decide which specific steps need to be completed and who is responsible for each of them.  
     
-   **User personas** — For Whom? If there are multiple end users, consider making multiple stories.  
     
-   **Ordered Steps** — Write a story for each step in a larger process.  
     
-   **Listen to feedback** — Talk to your users and capture the problem or need in their words. No need to guess at stories when you can source them from your customers.  
     
-   **Time** — Many development teams avoid discussions of time altogether, relying instead on their estimation frameworks. Stories should be completable in one sprint, stories that might take weeks or months to complete should be broken up into smaller stories or should be considered their own epic.  
     
Once the user stories are clearly defined, make sure they are visible for the entire team.

## User story template and examples

User stories are often expressed in a simple sentence, structured as follows:

**“As a [persona], I [want to], [so that].”**

Breaking this down: 

-   "As a [persona]": Who are we building this for? We’re not just after a job title, we’re after the persona of the person. Max. Our team should have a shared understanding of who Max is. We’ve hopefully interviewed plenty of Max’s. We understand how that person works, how they think and what they feel. We have empathy for Max.
-   “Wants to”: Here we’re describing their intent — not the features they use. What is it they’re actually trying to achieve? This statement should be implementation free — if you’re describing any part of the UI and not what the user goal is you're missing the point.
-   “So that”: how does their immediate desire to do something this fit into their bigger picture? What’s the overall benefit they’re trying to achieve? What is the big problem that needs solving?

For example, user stories might look like:

-   As Max, I want to invite my friends, so we can enjoy this service together.
-   As Sascha, I want to organize my work, so I can feel more in control. 
-   As a manager, I want to be able to understand my colleagues progress, so I can better report our sucess and failures. 

This structure is not required, but it is helpful for defining done. When that persona can capture their desired value, then the story is complete. We encourage teams to define their own structure, and then to stick to it.

## Getting started with agile user stories

User stories describe the why and the what behind the day-to-day work of development team members, often expressed as _persona + need + purpose_.

# Estimation
some ways to make agile estimates as accurate as possible.  

## Collaborating with the product owner
the product owner  is tasked with:
- prioritizing the backlog.
- capture requirements from the business
- breaking down work items into granular pieces and estimates via story points helps them prioritize all (and potentially hidden!) areas of work.

They don’t always understand the details of implementation.

## Agile estimation is a team sport

Involving everyone (developers, designers, testers, deployers... everyone) on the team is key.Each team member brings a different perspective on the product and the work required to deliver a user story.

## Story points vs. hours

Traditional software teams give estimates in a **time format**: days, weeks, months.

Agile teams have transitioned to **Story points** are units of measure for expressing an estimate of the overall effort required to fully implement a product backlog item or any other piece of work. Teams assign story points relative to work complexity, the amount of work, and risk or uncertainty. Values are assigned to more effectively break down work into smaller pieces, so they can address uncertainty.

Here are few reasons to use story points:

-   Dates don’t account for the non-project related work that inevitably creeps into our days: emails, meetings, and interviews that a team member may be involved in.
-   Dates have an emotional attachment to them. Relative estimation removes the emotional attachment.
-   Each team will estimate work on a slightly different scale, which means their velocity (measured in points) will naturally be different. This, in turn, makes it impossible to play politics using velocity as a weapon.
-   Once you agree on the relative effort of each story point value, you can assign points quickly without much debate. 
-   Story points reward team members for solving problems based on difficulty, not time spent. This keeps team members focused on shipping value, not spending time.
-   teams should use story points to understand the size of the work and the prioritization of the work.

## Story points and planning poker
The team will take an item from the backlog, discuss it briefly, and each member will mentally formulate an estimate. 

Everyone holds up a card with the number that reflects their estimate. 

If everyone is in agreement, great! If not, take some time (but not too much time) to understand the rationale behind different estimates. 

Remember though, estimation should be a high level activity.

## Estimate smarter, not harder

**No individual task should be more than 16 hours of work.**

For items deeper in the backlog, give a rough estimate.

Don’t waste time estimating work that is likely to shift.

# Epic
## Know your business
**Business metrics** focus on whether the solution is meeting the market need
**Agile metrics** measure aspects of the development process.

> A program's business metrics should be rooted in its roadmap.

For each initiative on the roadmap, include several key performance indicators (KPIs) that map to the program's goals.

include success criteria for each product requirement such as adoption rate by end-users or percentage of code covered by automated tests.

## How to use agile metrics to optimize your delivery

## Sprint burndown

Scrum teams organize development into **time-boxed sprints**

At the outset of the sprint, the team forecasts how much work they can complete during a sprint. A sprint burndown report then tracks the completion of work throughout the sprint. The x-axis represents time, and the y-axis refers to the amount of work left to complete, measured in either story points or hours. The goal is to have all the forecasted work completed by the end of the sprint.

![Burndown chart](https://wac-cdn.atlassian.com/dam/jcr:13bd4f37-3e5c-49ab-b9ab-e3c6482d7858/AgileBurndownChart.svg?cdnVersion=1752)

Anti-patterns to watch for

-   The team finishes early sprint after sprint because they aren't committing to enough work. 
-   The team misses their forecast sprint after sprint because they're committing to too much work. 
-   The burndown line makes steep drops rather than a more gradual burndown because the work hasn't been broken down into granular pieces.
-   The product owner adds or changes the scope mid-sprint.

## Epic and release burndown
Epic and release (or version) burndown charts track the progress of development over a larger body of work than the sprint burndown, and guide development for both scrum and kanban teams. 

"Scope creep" is the injection of more requirements into a previously-defined project. scope change within epics and versions is a natural consequence of agile development.

## Velocity
Velocity is the average amount of work a scrum team completes during a sprint, measured in either story points or hours, and is very useful for forecasting. The product owner can use velocity to predict how quickly a team can work through the backlog, because the report tracks the forecasted and completed work over several iterations–the more iterations, the more accurate the forecast.

It's important to monitor how velocity evolves over time.

![Velocity chart](https://wac-cdn.atlassian.com/dam/jcr:ce47ba7c-9b61-49ff-a624-e49013a40c7b/AgileVelocityReport.svg?cdnVersion=1752)

Anti-patterns to watch for

When velocity is erratic over a long period of time, always revisit the team's estimation practices. During the team's retrospective, ask the following questions:

-   Are there unforeseen development challenges we didn't account for when estimating this work? How can we better break down work to uncover some of these challenges?
-   Is there outside business pressure pushing the team beyond its limits? Is adherance to development best practices suffering as a result?
-   As a team, are we overzealous in forecasting for the sprint?

## Control chart

Control charts focus on the cycle time of individual issues–the total time from "in progress" to "done".

Measuring cycle time is an efficient and flexible way to improve a team's processes because the results of changes are discernable almost immediately, allowing them to make any further adjustments right away. The end goal is to have a consistent and short cycle time, regardless of the type of work (new feature, [technical debt](https://www.atlassian.com/agile/software-development/technical-debt), etc.).

![Control chart](https://wac-cdn.atlassian.com/dam/jcr:4d4e2f7b-5949-4d05-a1ec-bbbfbcdcf3ce/AgileControlChart.svg?cdnVersion=1752)

Anti-patterns to watch for

Control charts can appear fickle at first. Don't be so concerned with every outlier. Look for trends. Here are two areas to watch out for:

-   Increasing cycle time -Increasing cycle time saps the team of it's hard-earned agility. In the team's retrospective take time to understand an increase. One exception: if the team's definition of done has expanded, cycle time will probably expand too.
-   Erratic cycle time – The goal is to have consistent cycle time for work items which have similar story point values. Filter the control chart for each story point value to check for consistency. If cycle time is erratic on small and large story point values, spend time in the retrospective examining the misses and improving future estimation. 

## Cumulative flow diagram

The cumulative flow diagram should look smooth(ish) from left to right. Bubbles or gaps in any one color indicate shortages and bottlenecks, so when you see one, look for ways to smooth out color bands across the chart.

![Cumulative flow diagram](https://wac-cdn.atlassian.com/dam/jcr:32569175-67da-4d5f-86ad-cbf782b4846d/CumulativeFlowDiagram.svg?cdnVersion=1752)

Anti-patterns to watch for

-   Blocking issues create large backups in some parts of the process and starvation in others.
-   Unchecked backlog growth over time. This results from product owners not closing issues that are obsolete or simply too low in priority to ever be pulled in. 

## Even more metrics

Good metrics aren't limited to the reports discussed above. For example, quality is an important metric for agile teams and there are a number of traditional metrics that can be applied to agile development:

-   How many defects are found...
    -   during development?
    -   after release to customers?
    -   by people outside of the team?
-   How many defects are deferred to a future release?
-   How many customer support requests are coming in?
-   What is the percentage of automated test coverage?

# Gant Chart
It typically includes two sections: the left side outlines a list of tasks, while the right side has a timeline with schedule bars that visualize work. The Gantt chart can also include the start and end dates of tasks, milestones, dependencies between tasks, and assignees.

## What is a Gantt chart used for?

Project managers use Gantt charts for three main reasons:

### Build and manage a comprehensive project

Gantt charts visualize the building blocks of a project and organize it into smaller, more manageable tasks. The resulting small tasks are scheduled on the Gantt chart's timeline, along with dependencies between tasks, assignees, and milestones.

### Determine logistics and task dependencies

Gantt charts can be employed to keep an eye on the logistics of a project. Task dependencies ensure that a new task can only start once another task is completed. If a task is delayed (it happens to the best of us), then dependent issues are automatically rescheduled. This can be especially useful when planning in a multi-team environment.

### Monitor progress of a project

As teams log time towards issues in your plan, you can monitor the health of your projects and make adjustments as necessary. Your Gantt chart can include release dates, milestones, or other important metrics to track your project’s progress.

## The benefits of using a Gantt chart

There are two main reasons why Gantt charts are loved throughout the project management world. They make it easier to create complicated plans, especially those that involve multiple teams and changing deadlines. Gantt charts help teams to plan work around deadlines and properly allocate resources.

Projects planners also use Gantt charts to maintain a bird’s eye view of projects. They depict, among other things, the relationship between the start and end dates of tasks, milestones, and dependent tasks. Modern Gantt chart programs such as Jira Software with Roadmaps and Advanced Roadmaps synthesize information and illustrate how choices impact deadlines.

## Gantt charts in waterfall vs. agile planning

Gantt charts can be a powerful tool for both the [waterfall or agile methodologies.](https://www.atlassian.com/agile/project-management/project-management-intro)

### Waterfall

The waterfall model of project planning follows a linear approach where stakeholder and customer requirements are collected at the beginning of the project. From that, project managers create a sequential project plan, complete with milestones and deadlines. Every piece of the project relies on the completion of preceding tasks. This is favored by teams that focus on process (such as construction or manufacturing) and less on ideation or problem-solving as the steps need to be planned out in advance.

Gantt charts are typically preferred by project managers using waterfall. They determine a project schedule by breaking projects into manageable chunks of work and assigning start and end dates. It’s also helpful in identifying important milestones in your project. Milestones are accomplishments that teams should achieve on or ahead of schedule. They are optional but recommended.

### Agile

Instead of creating a full timeline with set dates, agile teams break projects into smaller iterations (also known as sprints). 

At the beginning of a sprint, a team plans their work against the goals of the project over the course of the next two weeks. Once that sprint is over, the accomplishments and developments from it help to create the plan for the next sprint.

A Gantt chart can show how changing one task has the potential to impact the plan or the product roadmap. For agile teams, this is essential since stakeholder feedback is a large part of the methodology.

### Project-specific charts - Jira Roadmaps

![A screenshot of a project specific Gantt chart in Jira Roadmaps | Atlassian Agile Coach](https://wac-cdn.atlassian.com/dam/jcr:a7906316-e9fa-4af8-93b3-1756936ed9db/Roadmap.png?cdnVersion=1752)

The screenshot above, taken from Roadmaps, shows a project-specific Gantt chart which is commonly used at the team level or within a single department. The chart shows how the team is tracking toward their goals, and the collapsible work breakdown structure allows project managers to get a bird's eye view on the crucial stories of the project.

### High-level organization chart - Advanced Roadmaps

Roadmaps offers quick and easy planning that helps teams better manage their dependencies and track progress on the big picture in real-time, useful for team-level planning of large pieces of work.

For planning, managing, and tracking work across multiple teams or even your entire organization, Advanced Roadmaps empower teams at scale

![Screenshot of cross-team workflow within Jira Advanced Raodmaps](https://wac-cdn.atlassian.com/dam/jcr:80c8ca60-68a6-4318-b46f-113b76d6a9e5/advanced-roadmaps.png?cdnVersion=1752)

Programs designed with cross-team workflows offer more advanced tools like capacity management and automatic scheduling features to help create more complex plans. They also offer a variety of view settings to allow you to customize your Gantt chart to highlight a certain aspect of your plan when presenting.

# DistributedScrum

Distributed scrum team  
: a scrum team that is either fully or partially remote.

Constraints on ad hoc collaboration and informal communication, remote teams need to be more disciplined about their scrum rituals and create new opportunities for bonding and collaboration.

Normally 2 pizza rule for teams in person (7-10 people/ team), but (5-6) for a distributed

## Benefits

-   Wider pool of available talent that can increase skill sets of teams
-   Teams across geographies that allows for 24-hour workday

> “Remote teams that closely follow recommended agile technical practices could easily outperform a colocated team that does not”, according to Gartner

## Challenges

Communication:

-   Without informal hallway chats and impromptu in-person meetings, remote teams need to communicate more and, at times, over communicate.
-   Communicating time should be based in one time zone.
-   Remote workers may have feelings of isolation, less team unity, and miss social interaction with work colleagues, less comraderie.
-   Project knowledge can be scattered since it’s more challenging for remote teams to share information.

## Building a successful Remote Team

A remote scrum team needs clear communication, transparency, mutual trust, collaboration, and a dedication for continuous improvement.

A Distrubuted Scrum Team Communication Plan

-   Remote work agreements
-   A way to contact other team members for informal questions  
-   Establish agreements for how meetings should be structured
-   How team members communicate their availability
-   What collaboration tools should be used

### Collaboration Tools

Agile teams use agile planning tools for collect stories/requirements, report and manage issues, and to track progress and quality.

-   Be accessible to all team members
-   Enable collaboration, sharing, and notifications to team members 
-   A collection of relevant, engaging information

### Impromptu chats

quick water cooler chats disappear with remote work, it’s important to allow for these informal communication channels to exist.  
If you use Slack, you can create specific channels with different intents.  
The scrum master should keep open communication channels to each part of the scrum team, as well as facilitate communication with the team as a whole.

build a united development culture by:

-   Over-communicating decisions across all geographies
-   Minimizing the friction in setting up the development environment
-   Clearly defining the definition of done
-   Creating guidelines for filing effective bug reports

### Daily scrum meetings

These short, daily team meetings provide a quick forum for a distributed team that helps with focus, collaboration, communication, and problem-solving.  
-Schedule regular video conferencing.  
-Hold asynchronous stand-ups where team members use Slack to check-in or comment on their work board to share updates.

structure for our stand-ups:

-   What did I work on yesterday?
-   What am I working on today?
-   What issues are blocking me?

### Product backlog

It’s important that the features of the sprint backlog are clearly documented and “definition of ready” agreed upon.  
If product backlog items are ambiguous, the team may lose momentum and the time to resolution can be delayed.

### Self organization

Team members can **take responsibility** for achieving business goals and how they are contributing to it.  
**Provide visibility** by documenting expectations on a Confluence page and agree how to hold each member accountable.

# Roles

## What are the three scrum roles?

Scrum has three roles:

-   product owner
-   scrum master
-   development team members.

## Scrum roles vs job titles

-   They aren’t job titles.
-   The three roles give a minimum definition of responsibilities and accountability to allow teams to effectively deliver work.
-   Allows teams to take responsibility for how they organize and to keep improving themselves.

## Building a scrum team

Scrum Framework provides the basic structure for regular meetings, artifacts, and who does what.  
Its not a one size fits all solution, the problems are different, the team structures and skills needed are also different.

## The development team: Redefining “developer”

-   The development team can be comprised of all kinds of people including designers, writers, programmers, etc.
-   A team member who has the right skills, as part of the team to do the work.
-   should be able to self-organize so they can make decisions to get work done.
-   empowering the people closest to the work to do what’s needed to solve the problem.  
    ![A diagram showing the development team's responsibilities: Self organization, design, development, UX, testing, deployment.](https://wac-cdn.atlassian.com/dam/jcr:f085fea0-5149-4b9a-9fe1-7e9fd32dc0da/Scrum-Development%20team-revised.png?cdnVersion=1717)

The development team’s responsibilities include:

-   Delivering the work through the sprint.
-   Ensuring Transparency at daily scrum.

**Daily Scrum**  
: provides transparency to the work and provides a dedicated place for team members to seek help, talk about success and highlight issues and blockers, to inspect and adapt the work they are doing and work in a more effective way.

## The product owner: Setting clear direction

Product owners:  
-ensure that they are delivering the most value  
-represents the business  
-tells development what is important to deliver

-   trust is needed between these 2 roles.
-   understand the customer
-   have a vision for the value the scrum team is delivering to the customer.
-   balances the needs of other stakeholders in the organization.
-   must take all these inputs and **prioritize the work**.

Agile teams are designed to inspect and adapt, that means a change in priority may lead to a massive change to the team structure, work products, as well as the end result.

product owners responsibilities as:

**Managing the scrum backlog**

-   does not mean that they are the only one putting in new product backlog Items into the backlog.
-   responsible for the backlog that the development team pulls to deliver from.
-   They should know about everything that is in the backlog.
-   other people that add items to the product backlog should ensure that they communicate with the product owner.

**Release management**

-   The sprint is a planning cycle.
-   Scrum teams can deliver at any time. Ideally, they would deliver frequently throughout the sprint allowing the sprint review to review real customer usage and feedback.
-   Continuous delivery is not always possible, and other release models are required.
-   Product owner must know when things can and should be released.

**Stakeholder management**

-   Any product will have many stakeholders from users, customers, governance and organizational leadership.
-   The product owner will work with all these people to effectively ensure that the development team is delivering value.
-   A large amount of stakeholder management and communication is required.

# Agile Scrum Artifacts

**Agile scrum artifacts**  
: information that a scrum team and stakeholders use to detail the product being developed, actions to produce it, and the actions performed during the project.

The main agile scrum artifacts are  
-product backlog, sprint backlog, and increments.

## Why Agile scrum artifacts

These artifacts provide metadata points that give insight into the performance of a sprint.  
They are essential tools for every scrum team since they enable core scrum attributes of transparency, inspection, and adaption.

Artifacts are created during the main activities of a scrum [sprint](https://www.atlassian.com/agile/scrum/sprints): 

-   Plan work and future goals
-   Create tasks to achieve these goals
-   Organize tasks into sprints based on dependency and priority
-   Execute the tasks
-   Review and analyze results in order to compare to the goals
-   Repeat these steps

## The main artifacts of agile scrum

![Scrum artifacts](https://wac-cdn.atlassian.com/dam/jcr:05c5e42e-3df4-4168-8fe3-ac1656ca76ed/scrum-artifacts.png?cdnVersion=1717)

The main agile scrum artifacts are product backlog, sprint backlog, and increments.

### Product backlog

The [product backlog](https://www.atlassian.com/agile/scrum/backlogs) is:

-   a list of new features, enhancements, bug fixes, tasks, or work requirements needed to build a product.
-   Compiled from input sources like customer support, competitor analysis, market demands, and general business analysis.
-   a “live” artifact in that it is updated on-demand as new information is available.
-   a cross-team backlog that is maintained and curated by the product owner between sprint cycles and as any new ideas arise.
-   Contains tasks that were once in an active sprint but deprioritized and moved to the backlog.

### Sprint backlog

**Sprint backlog** : a set of product backlog tasks that have been promoted to be developed during the next product increment.

-   Created by the development teams to plan deliverables for future increments and detail the work required to create the increment.  
-   Created by selecting a task from the product backlog and breaking that task into smaller, actionable sprint items.
-   The product backlog is home to the primary task while the supporting tasks are housed in the sprint backlog.

-The sprint backlog is updated during the [sprint planning](https://www.atlassian.com/agile/scrum/sprint-planning) phase of scrum.  
-The smaller sprint tasks are assigned to the relevant teams like design and development.  
-If a team does not have the capacity to deliver all the sprint tasks, the remaining sprint tasks will standby in the sprint backlog for a future sprint.

### Product increment

**Product Increment**  
:the customer deliverables that were produced by completing product backlog tasks during a sprint, including the increments of all previous sprints.

-There is always one increment for each sprint and an increment is decided during the scrum planning phase.  
-An increment happens whether the team decides to release to the customer.  
-Product increments are incredibly useful and complementary to CI/CD in version tracking and, if needed, version rollback.

### Extended artifacts

In addition to the previously discussed official scrum artifacts, there exist some extended or meta artifacts. While not official per official scrum guidelines these extended artifacts add additional value and insight to a scrum cycle.

#### Burndown chart

**Sprint Burndown (or burnup) chart**

-   not an official scrum artifact but used to communicate and track progress toward the sprint goal during the sprint.
-   They are graphs that display tasks completed over the duration of a sprint.
-   useful in helping to gauge the active execution velocity of a team so they can reprioritize if the trajectory is off.
-   During sprint planning, teams shouyld look at previous burns.
-   Over time burndown charts help teams better refine their estimates during the planning stages of scrum.

#### The definition of “done”

-   It’s important that teams have a clear definition of **“done”**.
-   This definition can be another type of artifact, which should be documented and shared.
-   An example definition of done for a development team is when code is covered with automated tests that match a specification and is deployed to a production environment.
-   A team without a clear definition of done will find themselves often in sprint review asking “is this done?” when reviewing open scrum tasks.
-   The definition of done helps define the boundaries of an **increment**.
-   **Increments** should be delivered in complete usable packages that are additive to increments that came before.
-   **Done** also defines when tasks are complete and can be closed out for burndown tracking.

## Artifact transparency

**Scrum artifacts** are powerful aids that help teams operate more efficiently.

-   All teams should have access and visibility into the artifacts.
-   Product owners and scrum masters need to make it a regular practice to review and discuss artifacts with development teams.
-   This helps teams stay aware of operational inefficiencies and produce creative ways to improve velocity.

# Scrum metrics

**Scrum metrics** are specific data points that scrum teams track and use to improve efficiency and effectiveness. Scrum teams use metrics to inform decision-making and become more efficient in planning and execution, as well as set target goals and improvement plans.

## What is scrum?

**Scrum** is an agile framework and way of working that helps teams address complex problems, while iteratively developing solutions around a goal.

-The scrum way of working is characterized by the [sprint](https://www.atlassian.com/agile/scrum/sprints), which is a measured amount of time a scrum team works to complete a set amount of work. 

-   scrum metrics are increasingly important to measure team performance and effectiveness.

## What are scrum metrics?

**Scrum metrics** are specific data points that scrum teams track and use to improve efficiency and effectiveness. They can become insights that help guide and improve a team’s agile journey.

Scrum teams use metrics to inform decision-making and become more efficient in planning, execution, establishing a baseline on the status quo, and set target goals and improvement plans.

-   Every team is unique: they can be different in size, technologies used, type of work they do, etc.
-   It’s up to each team to agree on a set of metrics to track and define how to use them.
-   This is not an individual effort and not something the leadership or management can define and enforce on behalf of the teams.

## Why do you need scrum metrics?

-   help teams establish benchmarks and guide the direction of the work.
-   helps bring visibility to various dimensions of a team’s effectiveness, whether it’s a team’s velocity, capacity, predictability in delivery, or quality of the product.
-   Key metrics can cultivate awareness in the team’s performance and instigates action to change and improve.

## Can scrum metrics be used as KPIs?

-Scrum metrics can be used to set up key performance indicators (KPIs), but it depends on the type and scope of the work.

-Scrum metrics alone cannot measure customer value or show if the team even delivered the right thing.  
-For an agile team, KPIs should ultimately show how well the team supports company priorities. 

When measuring a scrum team’s performance, other metrics outside those of the scrum should be considered, including: 

-   **Return on investment (ROI) to a business** — Companies measure this in numerous ways depending on the objectives, including growth in revenue, monthly active revenue (MAU), and more.
-   **Customer satisfaction** — Survey metrics like the Net Promoter Score (NPS) and customer satisfaction score (CSAT) can help track the success of a project. Consistent customer satisfaction metrics for every release are important to showing a scrum team’s value to customers.
-   **Team satisfaction** — Just by asking your team about their level of motivation with the project and engagement with the team, you can catch problems like turnover, attrition, and dissatisfied developers.

## Key scrum events and what metrics to review

While agile scrum defines several recurring events — sprint, sprint planning, daily scrum, sprint review, sprint retrospective — these don’t provide any guarantees of progress or success. However, each one allows team members to inspect and adapt how they work.

![Sprint cycle infographic](https://wac-cdn.atlassian.com/dam/jcr:ae9f40d1-19d8-42e4-8511-751708bb89d5/sprint-cycle.png?cdnVersion=1717)

### Sprint planning

**sprint planning** meeting is held at the beginning of a sprint where a team breaks down story descriptions into detailed tasks.

-   provides an estimate of work to be produced during a sprint.
-   There are a handful of data points that can make your team’s sprint planning more efficient, including sprint goals, current team velocity, team capacity, and type of work.
-   We use a [sprint planning meeting template](https://www.atlassian.com/software/confluence/templates/sprint-planning-meeting) to help guide our sprint planning.

#### Sprint goals

**Sprint goals** help teams decide what to accomplish in a sprint, bring cohesion to the items, and set priorities.

-   often contribute to a bigger outcome than can be achieved through multiple sprints.
-   priority should be based on their impact to this outcome.
-   review goals and priorities regularly to strategize how to sequence and split engineering efforts.

#### Team velocity

**velocity**: how much work it can accomplish during a given time, as well as capacity, or how much availability it has. A velocity chart, [like](https://support.atlassian.com/jira-software-cloud/docs/view-and-understand-the-velocity-chart/), reveals the amount of value delivered during a sprint.

-   helps us predict the volume of work a team can perform for future sprints.
-   A team’s velocity can only be understood after running a few sprints together as a team.

Over time velocity will stabilize as a result of a team working together due to:

-   ramping up on technologies used
-   understanding each other’s expertise
-   learning how to work as a team.

The following is an [example of a velocity chart](https://support.atlassian.com/jira-software-cloud/docs/view-and-understand-the-velocity-chart/) with (1) estimation statistic based on story points, (2) commitment, which is an estimate of all issues in the sprint, (3) completed estimates, and (4) sprints completed.

![Velocity chart infographic](https://wac-cdn.atlassian.com/dam/jcr:742a35f3-070f-42d1-bdc4-abe381dcaf33/chart-1.png?cdnVersion=1717)

#### Team capacity

**Team Capacity**: the amount of work a team can complete in a sprint is based on its capacity and availability.

-   Stable velocity won’t mean anything if half of your team is off on a vacation.
-   gather each team member’s availability a few sprints out and add the sum to get a percentage of total capacity.
-   Since last-minute changes or emergencies can happen to anyone, it’s also a good idea to leave a 10 percent buffer in your sprint commitment to avoid overcommitting and under-delivering.

#### Type of work

-   Be intentional about what work your team is taking on by reviewing the split of different types of work during sprint planning.
-   In this case, even if you find a lot of tech debt and quality work in the backlog, you can solve it strategically by scheduling a tech debt sprint or raising the bar on QA.

### Stand-ups (a.k.a daily scrum)

**[Stand-ups](https://www.atlassian.com/agile/scrum/standups), or Daily Scrum**, are short meetings held each day where team members check in about their work.

-   Should go beyond updates about an individual’s updates on their to-do list.
-   An opportunity to review a team’s sprint progress and realign priorities for making small to big daily decisions that can have a significant impact on a sprint’s outcome.

In doing so, the following data and metrics can come in handy:

#### Progress towards sprint goals

-   a chance to discuss if the team is still on track. If not, why and what can be done about it?
-   If it’s something that can’t be resolved, it’s important to communicate this to key stakeholders, so everyone is on the same page.

#### Sprint burndown

[sprint burndown chart](https://www.atlassian.com/agile/tutorials/burndown-charts). A

**Sprint Burndown Chart** 

-   Tracks the completion of work throughout a sprint.
-   Compares the time and amount of work to complete, measured in story points or hours.
-   Helps predict a team’s ability to complete work in a designated time
-   helps track scope creep.

If a burndown chart has a sharp drop, it could be related to an inaccurate estimate of work. 

![Sprint burndown chart infographic](https://wac-cdn.atlassian.com/dam/jcr:e8f08ad0-a316-4781-a59c-cee0e49ff6a7/sprint-burndown-chart.png?cdnVersion=1717)

#### Workload distribution

-   don’t turn it into a weapon.
-   If you use this to measure an individual’s productivity, you can end up discouraging your team.
-   create a safe environment for everyone to openly talk about how much they’re taking on, and where they need help.

### Sprint retrospective

**[Sprint Retrospectives]**([https://www.atlassian.com/team-playbook/plays/retrospective](https://www.atlassian.com/team-playbook/plays/retrospective))

-   you and your team review what happened in the sprint by celebrating what went well, what needs improvement, and why.
-   the perfect time and place for you to review key sprint metrics, including sprint goal completion and sprint satisfaction.

The following is an example of my team’s retrospective outlined on a Confluence page:

![Sprint retrospective screenshot](https://wac-cdn.atlassian.com/dam/jcr:48bc5981-3e7a-4812-8991-2f18aa0220f6/retrospective-meeting.jpeg?cdnVersion=1717)

### Sprint goal completion

In evaluating your team’s success, scrum metrics we’ve already discussed can come in handy.

Doing so will help your team address the issue and come up with a clearer action plan.

### Sprint satisfaction

-   This is simply asking your team about their satisfaction with the sprint.
    
-   Some teams use a number scale for this, anecdotal feedback, or even emojis/gifs.
    
-   Your team can reflect on team goals and if the type of work was in alignment with team goals.
    
-   encourage team members to speak up and call on them if needed.
    
-   The best retrospectives have multiple perspectives and a variety of opinions.
    
-   By the end of the meeting, the team largely agrees on the top problems, owners, and a plan to follow up on key issues.

# Jira
