# PawPal+ Project Reflection

## 1. System Design

**a. Initial design**

- Briefly describe your initial UML design.
The three core actions a user should be able to perform in PawPal+ are adding and managing a pet profile ( name, species, owner info, daily time available), adding and editing care tasks (name, duration, priority), and being able to generate and view today's schedule (constraint-aware plan with reasoning for what was included/skipped). 
- What classes did you include, and what responsibilities did you assign to each?
Pet:
    —animal's name
    -species
    -age
    -simple data container/object
Owner:
    -owner's name
    -how many minutes per day they have available for specific pet 
    -available time is the main constraint passed to the scheduler
Task:
    -single care item
    -the unit of work the scheduler reasons about
    -title
    -duration (in minutes)
    -priority level (high/medium/low)
Scheduler:
    -the core logic class 
    -takes an Owner, a Pet, and a list of Task objects, then selects and orders tasks that fit within the owner's available time, prioritizing high-priority tasks first
Plan:
    -holds the output: the ordered list of scheduled tasks and a plain-language explanation of what was included and what was skipped (and why)

**b. Design changes**

- Did your design change during implementation?
- If yes, describe at least one change and why you made it.
Yes, my design did change from its initial creation. For example, as I thought more about the app, I decided to re-evaluate the relationships between certain classes, specifically between "Owner" and "Plan". At first, it was a one-to-one relationship, but over time, I realized that it's more realistic for the plans to be representative of days of the week rather than a list of task, and of course, no one really does the same thing everyday. 

---

## 2. Scheduling Logic and Tradeoffs

**a. Constraints and priorities**

- What constraints does your scheduler consider (for example: time, priority, preferences)?
The constraints I included were availiable time (of the Owner) and priority (of a given task). 
- How did you decide which constraints mattered most?
For me, the priority constraint takes higher precedence than the time constraint since priority of a task implies urgency and may have negative consequences for the pet if skipped. For example, choosing to skip on the higher priority task, such as giving your dog its medication, in favor of doing a lower priority task, such as giving your dog a midday snack, is not favorable. Also, time is a softer constraint that resets daily and can flex.

**b. Tradeoffs**

- Describe one tradeoff your scheduler makes.
One tradeoff is that the scheduler picks what tasks should be done by greedily choosing tasks based on their priority order, without taking into account other previous tasks that were skipped or re-arranging tasks around to come up with a more optimal schedule for example. 
- Why is that tradeoff reasonable for this scenario?
It's reasonable because pet-care is typically priority driven, and I assume that the average pet owner cares about getting the most important tasks done on their pets over with and not really caring about efficiency or optimization. 

---

## 3. AI Collaboration

**a. How you used AI**

- How did you use AI tools during this project (for example: design brainstorming, debugging, refactoring)?
I mainly used AI for the debugging, refactoring, and implementation of code 
- What kinds of prompts or questions were most helpful?
What I like to do is ask my AI agent clarifying questions (or questions in general) after every suggestion it makes during our chats. This method helps me understand the AI's "thinking" and what is being changed, deleted, or added and for what reason. I also find myself learning a little this way.

**b. Judgment and verification**

- Describe one moment where you did not accept an AI suggestion as-is.
It was during the initial stages of this project (creating the UML diagram). The overall diagram was fine, but I was a bit iffy on how it designed relationships between certain objects. Some relationships didn't make sense to me, so, what I did was edit and revise the original diagram it provided and essentially made it more realistic. 
- How did you evaluate or verify what the AI suggested?
I did what I described above earlier: after looking over its suggestion, I asked the AI agent questions to get an idea on what it meant by designing the diagram the way it did at first. By asking it clarifying questions and discussing my suggestions, I soon understood that it didn't really take into account real-life nuances and that I had to implement those changes on my own. 

---

## 4. Testing and Verification

**a. What you tested**

- What behaviors did you test?
The behaviors that were tested were checking: if a task was successfully marked complete, if a new task could be added onto a pet, if existing tasks were sorted correctly (in terms of priority), if completing a daily task generated a new task dated one day later, and if there were any overlapping tasks. 
- Why were these tests important?
These tests are important because it makes sure that the program isn't unintentionally creating scheduling conflicts or making a pet miss out on a critical task.

**b. Confidence**

- How confident are you that your scheduler works correctly?
I am quite confident that the scheduler works correctly. By "quite", I mean that the logic implemented surely passes for all general, expected cases. 
- What edge cases would you test next if you had more time?
Since the program doesn't really consider unique edge cases, if I had more time the ones that I would test would be testing what should happen if a pet has 0 tasks, if an Owner has 0 available minutes, or what should filter_tasks return when no pets match.

---

## 5. Reflection

**a. What went well**

- What part of this project are you most satisfied with?
I suppose I was most satisfied with the brainstorming/initial design part of the project. It was pretty fun collaborating with the AI, determining what objects should be considered in our PawPet mini-world, and coming up with ideas on how they should be designed. 

**b. What you would improve**

- If you had another iteration, what would you improve or redesign?
I would improve upon the existing program's logical design by incorporating instances that can catch or check for unique edge cases.

**c. Key takeaway**

- What is one important thing you learned about designing systems or working with AI on this project?
I learned to never just roll with the first thing that the AI spits back at you. Even thought the technology is rapidly improving, I think it's safe to always tell the AI to clarify its intentions and ask it questions. That way, you minimize screw-ups in the future. 
