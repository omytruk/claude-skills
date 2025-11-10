---
name: work-structurer
description: Structure work into proper Notion hierarchy (Areas → Projects → Tasks). Use when the user says "let's set up my projects", "help me structure this work", "break this project down", or after problem externalization when ready to organize. Creates full hierarchy with goals and helps discover project outcomes through guided questions.
---

# Work Structurer Skill

## Purpose
Help Olena translate ideas, goals, and work into the proper Notion structure (Areas → Projects → Tasks) without her having to explain the system every time. This skill knows the Notion setup and can create the full hierarchy efficiently.

## Database IDs
- **Areas of Interest**: collection://2a708620-e1b0-80bf-b537-000be39d5d7a
- **Projects**: collection://2a708620-e1b0-8017-9b32-000b5045104a
- **Tasks**: collection://2a708620-e1b0-807e-b3eb-000b698751cc

## When to Use This Skill
When Olena says things like:
- "Let's set up my projects in Notion"
- "Help me structure this work"
- "I need to add this to my project system"
- "Let's break this project down into tasks"
- Or after Problem Externalizer when she's ready to organize the work

## The Structure Hierarchy

```
AREA OF INTEREST
├─ Description (what this area encompasses)
└─ PROJECTS
    ├─ Goal (what success looks like for this project)
    ├─ Status (Active, On Hold, Someday, Completed)
    └─ TASKS
        ├─ Plan Date (when to do it)
        ├─ Due Date (deadline)
        └─ Status (Not started, In progress, Done)
```

## How It Works

### Step 1: Understand the Scope
Ask clarifying questions to understand what needs to be structured:
- Is this a new Area of Interest?
- Is this a Project within an existing Area?
- Is this breaking down an existing Project into Tasks?
- Is this all of the above?

### Step 2: Start with Areas (if needed)
If creating or updating Areas:
- **Name**: Clear, concise label (e.g., "Art & Photography", "Writing", "ADHD AI System")
- **Description**: What this area encompasses, why it matters to Olena
- **Examples**: 
  - "Art & Photography: Your creative outlet through synthography and AI-generated art, including exhibitions and artistic expression"
  - "Writing: Books, Substack, and all written work exploring imagination, ADHD, and innovation"

### Step 3: Create Projects
For each project:
- **Name**: Specific, outcome-focused (e.g., "Houston General Exhibition", "ED Awareness Art Series", "Book on Human Imagination")
- **Goal**: What success looks like - a single clear sentence about the outcome
  - If Olena knows the goal, capture it
  - If unclear, enter **Discovery Mode** (see below)
- **Area**: Link to the appropriate Area of Interest
- **Status**: 
  - Active = currently working on it
  - On Hold = paused but will return to
  - Someday = might do eventually
  - Completed = done!

### Discovery Mode: When the Goal Isn't Clear

If Olena doesn't know what success looks like yet, help her discover it through questions:

**Discovery Questions:**
1. "What would make this feel successful to you?"
2. "What changes if this works?"
3. "Who benefits from this project?"
4. "If you completed this perfectly, what would be different?"
5. "What would disappointing look like? (so we can flip it)"

**Offer Examples Based on Project Type:**
- **Exhibition projects**: "X number of attendees" or "meaningful conversations started" or "personal healing through sharing"
- **Writing projects**: "X readers engaged" or "establish thought leadership in Y" or "finish first draft"
- **Building projects**: "working system I use daily" or "tool that reduces X friction" or "foundation for future product"
- **Business projects**: "X clients served" or "Y revenue" or "validated business model"

**Brainstorm Together:**
- "Here are some possible outcomes - which resonates?"
- "Should we start broad and refine it later?"
- "Is this more about process (building a habit) or outcome (specific achievement)?"

**Light Web Research (if helpful):**
- "Want me to look up what successful [type of project] typically achieves?"
- Example: "Let me research what makes a Substack successful"

**When Goal is Still Fuzzy:**
That's okay! Write something like:
- "Explore and establish presence in X space"
- "Build foundation for future clarity"
- "Learn what's possible with Y"

The goal can evolve - it's not locked in forever.

### Step 4: Break Down into Tasks (Optional)
If Olena wants to break a project into tasks:
- Keep tasks actionable and specific
- Use Plan Date for "when I'll do this"
- Use Due Date for "when it must be done by"
- Link all tasks to the Project
- Default Status: "Not started"

### Step 5: Present the Structure
Show Olena what was created in a clear format:
```
✅ Created in Notion:

**Area**: [Area Name]
- [Description]

**Projects**:
1. [Project Name] (Status: Active)
   Goal: [What success looks like]
   - Tasks:
     • [Task 1]
     • [Task 2]
     
2. [Project Name] (Status: Someday)
   Goal: [What success looks like]

Want me to add any tasks to these projects, or shall we leave them at the project level for now?
```

## Key Principles

### 1. Don't Over-Task
Not every project needs tasks immediately. Sometimes just having the project defined is enough. Ask:
- "Do you want to break this down into tasks now, or just have the project set up?"

### 2. Think in Outcomes
Projects should be outcome-focused:
- ✅ "Houston General Exhibition"
- ✅ "Book on Human Imagination"
- ❌ "Work on exhibition stuff"
- ❌ "Writing things"

### 3. Areas are Broad, Projects are Specific
- **Area**: Art & Photography (ongoing, no end date)
- **Project**: Houston General Exhibition (specific, has an outcome)

### 4. Status Reflects Reality
Help Olena be honest about status:
- "On Hold" is not failure - it's strategic pausing
- "Someday" is valid - not everything is "Active"
- Ask: "Is this actually active right now, or is it on hold?"

### 5. Goals Create Clarity
Every project should have a Goal, even if it's fuzzy at first:
- Ask discovery questions when the outcome isn't clear
- It's okay to start with "Explore X" or "Build foundation for Y"
- Goals can evolve - they're not permanent
- A clear goal reduces ADHD rumination ("why am I doing this again?")

### 6. Integrate with Other Skills
After structuring:
- Offer to create reminders for urgent tasks (Reminder Skill)
- Save any additional thoughts to Brain Dump
- Use Problem Externalizer if she's feeling overwhelmed by the scope

## Common Scenarios

### Scenario 1: Brand New Area + Projects
**Olena**: "Let's set up my writing area with all the projects"

**Process**:
1. Create "Writing" Area with description
2. Create each project (Book, Substack - Imagination, Substack - ADHD)
3. Link all projects to Writing area
4. Set appropriate status for each
5. Ask if she wants to break any down into tasks

### Scenario 2: Add Project to Existing Area
**Olena**: "I want to add a new project under Art & Photography for a collaboration"

**Process**:
1. Create the new project
2. Link it to existing "Art & Photography" area
3. Set status
4. Ask about tasks if relevant

### Scenario 3: Break Down Existing Project
**Olena**: "Let's break down the Houston Exhibition project into tasks"

**Process**:
1. Fetch the existing project
2. Ask what the key steps/tasks are
3. Create tasks linked to that project
4. Set Plan/Due dates if mentioned
5. Present the task list

### Scenario 4: Full Setup from Scratch
**Olena**: "Help me set up everything I told you about - all my areas and projects"

**Process**:
1. Confirm the areas to create
2. For each area, confirm the projects
3. Create the full structure
4. Present a complete map
5. Ask about tasks only for active, immediate projects

## Template: Full Structure Creation

When setting up multiple areas and projects, use this approach:

**Step 1**: Confirm understanding
"I heard you mention these areas:
- Art & Photography
- Writing  
- ADHD AI System
- Professional Practice

And within those, these projects:
- [list them]

Does that capture everything?"

**Step 2**: Create systematically
Create Areas first, then Projects linked to them

**Step 3**: Present the map
```
✅ Here's your complete structure in Notion:

🤩 **Art & Photography**
   👩‍💼 Houston General Exhibition (Active)
      Goal: [What success looks like]
   👩‍💼 ED Awareness Art Series (Active)
      Goal: [What success looks like]
   👩‍💼 Mytruk Studio Website (Completed)
      Goal: [What success looks like]

✍️ **Writing**
   👩‍💼 Book on Human Imagination (Active)
      Goal: [What success looks like]
   👩‍💼 Substack Publication (Active)
      Goal: [What success looks like]

🧠 **ADHD AI Operating System**
   👩‍💼 Build Personal AI Infrastructure (Active)
      Goal: [What success looks like]
   👩‍💼 Document & Package for Others (Someday)
      Goal: [What success looks like]

💼 **Professional Practice**
   👩‍💼 LeapMind Collective (On Hold)
      Goal: [What success looks like]
   👩‍💼 Executive Coaching (On Hold)
      Goal: [What success looks like]

Which projects would you like to break down into tasks?
```

## Example: Full Setup Session

**Olena**: "Let's set up everything I told you about earlier in Notion"

**Claude**: "Great! I heard you mention these areas of interest:
- Art & Photography (synthography)
- Writing (book and Substack)
- ADHD AI Operating System (what we're building)
- Professional Practice (consulting/coaching, currently on hold)

And some key projects like:
- Houston General Exhibition
- ED Awareness Art Series
- Book on Human Imagination
- Substack Publication
- Personal AI Infrastructure

Does that capture the main areas and projects?"

**Olena**: "Yes, that's right"

**Claude**: "Perfect. Before I create these, let me ask about a couple of the goals so we can capture what success looks like. For the Substack - what would make that feel successful to you?"

**Olena**: "Hmm, I'm not totally sure yet. I want to build a readership but I don't know how many people or what 'success' really means."

**Claude**: "That's totally fine. Here are some possible goals for a Substack - which direction resonates?
- Build an engaged community of X readers interested in imagination and ADHD
- Establish thought leadership at the intersection of imagination, ADHD, and AI
- Create a consistent writing practice and body of work
- Explore ideas that might become the book"

**Olena**: "I think it's a mix of establishing thought leadership and exploring ideas for the book."

**Claude**: "Got it. So something like: 'Establish voice at the intersection of imagination and ADHD while exploring ideas for the book'?"

**Olena**: "Yes, that works!"

**Claude**: [Creates all areas and projects]

"✅ Done! Here's your complete structure:

🤩 **Art & Photography**
Creative outlet through synthography and AI-generated art, including exhibitions and artistic expression

Projects:
   👩‍💼 Houston General Exhibition (Active)
      Goal: Showcase synthography work to Houston community and gauge interest
   👩‍💼 ED Awareness Art Series (Active)
      Goal: Create meaningful awareness and start conversations about eating disorder recovery
   👩‍💼 Mytruk Studio Website (Completed)
      Goal: Professional online presence for synthography portfolio

✍️ **Writing**
Books, Substack, and all written work exploring imagination, ADHD, and innovation

Projects:
   👩‍💼 Book on Human Imagination (Active)
      Goal: Publish comprehensive work on imagination as foundation for innovation in AI age
   👩‍💼 Establish Thought Leadership via Substack (Active)
      Goal: Establish voice at intersection of imagination and ADHD while exploring ideas for the book

🧠 **ADHD AI Operating System**
Building your personal AI support infrastructure and potentially packaging it for others

Projects:
   👩‍💼 Build Personal AI Infrastructure (Active)
      Goal: Create working ADHD-friendly AI system I use daily that reduces executive function friction
   👩‍💼 Document & Package for Others (Someday)
      Goal: Help other ADHD entrepreneurs by sharing what works

💼 **Professional Practice**
AI transformation consulting, executive coaching, and innovation leadership

Projects:
   👩‍💼 LeapMind Collective (On Hold)
      Goal: Support organizations through systematic AI transformation
   👩‍💼 Executive Coaching (On Hold)
      Goal: Guide newly appointed AI leaders through transformation challenges

Want to break down any of these active projects into specific tasks, or is this structure good for now?"

## Integration Points

**With Problem Externalizer**:
After externalizing a problem, offer: "Want me to set this up as a project in Notion so you can track it?"

**With Reminder Skill**:
When creating tasks during structure setup, use Reminder Skill logic for dates

**With Brain Dump**:
If Olena mentions additional ideas while structuring: "Want me to capture that in Brain Dump for later?"

## Key Reminders for Claude
1. **You know the Notion system** - don't make Olena explain it
2. **Create the full hierarchy** - Areas → Projects → Tasks
3. **Ask about tasks selectively** - not every project needs immediate task breakdown
4. **Present clearly** - use visual hierarchy in responses
5. **Be efficient** - batch create when possible
6. **Status matters** - help Olena be realistic about On Hold vs Active
7. **Link everything properly** - Projects to Areas, Tasks to Projects
