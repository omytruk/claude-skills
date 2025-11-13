---
name: action-keeper
description: Intelligently create reminders or tasks in Notion using natural language. Use when the user says things like "remind me to...", "I need to...", or mentions doing something at a specific time or by a deadline. Automatically routes to Reminders (simple, standalone) or Tasks (project-related, complex) based on context. Handles date/time parsing, project linking, and description capture.
---

# Action Keeper Skill

## Purpose
Enable Olena to capture reminders and tasks using natural, conversational language. Intelligently routes to the appropriate database (Reminders vs Tasks) based on context, without requiring her to decide which to use.

## Database IDs
- **Reminders**: collection://2a808620-e1b0-8050-9725-cd9c8a75c924
- **Tasks**: collection://2a708620-e1b0-80f9-9306-f1d6d0984dbb
- **Projects**: collection://2a708620-e1b0-8038-9898-d5ad146c9cbd
- **Areas of Interest**: collection://2a708620-e1b0-80db-99b4-ec4706808135

## Default Values
- **General Area URL**: https://www.notion.so/2a708620e1b0811bab8ed2364625ad9e
- **General Project URL**: https://www.notion.so/2a708620e1b0817dbb37f46a6852a85b

## How It Works

When Olena says something like:
- "Remind me to call my mom tomorrow at 9am"
- "Remind me to get groceries tomorrow"
- "I need to call the exhibition place this week for the ED awareness project"
- "I need to build a content repurposing skill for my Imagination Substack"

### Step 1: Parse the Request
Extract:
1. **Action/title** - the main thing to do (e.g., "call my mom", "get groceries")
2. **Details/context** - any additional information that provides context
3. **Timing** - when to do it (e.g., "tomorrow at 9am", "this week")
4. **Project reference** (optional) - which project it relates to (e.g., "ED awareness project", "Imagination Substack")

### Step 2: Decide: Reminder or Task?

**Route to REMINDERS if:**
- Starts with "Remind me to..."
- Simple, standalone action with no project context
- No detailed information beyond the basic action
- Examples: "get groceries", "call mom", "water plants"

**Route to TASKS if:**
- Starts with "I need to..." or "I should..."
- Mentions a specific project or area of work
- Has context, details, or is part of a larger workflow
- Related to ongoing projects/goals
- Examples: "call gallery about exhibition", "build new Claude skill", "write Substack post"

**When in doubt:** If there's ANY project context or detail → Task. If it's simple and standalone → Reminder.

### Step 3: Extract Title vs Description (for Tasks only)
For Tasks, separate:
- **Title**: The action verb + object (concise, scannable)
  - "Call gallery about exhibition"
  - "Build content repurposing skill"
  - "Email editor with draft"

- **Description**: Additional context, details, notes
  - "Ask about February availability, mention ED awareness theme, inquire about community exhibition program"
  - "For Imagination Substack - needs to convert posts into Twitter threads and LinkedIn posts"
  - "Include the three key points we discussed and the deadline change"

If there's no extra detail, Description can be empty.

### Step 4: Determine Plan Date vs Due Date
- **Plan Date** = specific time Olena wants to do the task
  - "tomorrow at 9am" → Plan Date: 2025-11-11T09:00:00
  - "tomorrow" (no time) → Plan Date: 2025-11-11 (date only)
  - "in 30 minutes" → Plan Date: current time + 30 minutes (datetime)
  - "in 2 hours" → Plan Date: current time + 2 hours (datetime)
  - "in 3 days" → Plan Date: current date + 3 days (date only, unless time specified)
  - If no specific day mentioned, leave Plan Date empty
  
- **Due Date** = deadline for completion
  - "by Friday" → Due Date: 2025-11-15
  - "this week" → Due Date: 2025-11-15 (end of current week)
  - "by end of month" → Due Date: last day of current month
  - If no deadline mentioned, leave Due Date empty

### Step 5: Intelligent Project Matching (for Tasks only)

Instead of simple keyword search, use intelligent semantic matching:

**1. Query Active Projects First**
- Filter Projects database by Status = "Active"
- These are Olena's current focus areas - most likely matches

**2. Read Full Project Context**
- Don't just match on project Name
- Read the **Goal** field (what success looks like)
- Read the **Description** field if available
- Understand what the project is *about*

**3. Make Semantic Matches**
Examples of intelligent matching:
- Task: "Write about imagination in the AI age"
  → Matches "Establish Thought Leadership via Substack" (Goal: "Establish voice at intersection of imagination and ADHD")

- Task: "Find gallery space for eating disorder art"
  → Matches "ED Awareness Art Series" even if "ED" isn't in the task text

- Task: "Research synthography techniques"
  → Matches "Houston General Exhibition" (if Goal mentions showcasing synthography work)

**4. Consider Task Context**
- What is the task trying to achieve?
- What domain/topic does it relate to? (Art, Writing, ADHD System, Business)
- Does it align with any project's goal?

**5. Keyword Matching as Backup**
If semantic matching is unclear, look for keywords in project names:
- "exhibition", "Houston", "gallery" → Houston Exhibition project
- "ED awareness", "eating disorder" → ED Awareness project
- "Substack", "writing", "post" → Substack/Writing projects
- "skill", "Claude", "AI system" → ADHD AI System projects

**6. Default to General Project**
- If no clear match after all above steps
- Better than guessing wrong or asking for clarification
- Use: https://www.notion.so/2a708620e1b0817dbb37f46a6852a85b

**7. Never Ask for Clarification**
- Make your best intelligent guess
- Olena can always move tasks later if needed
- Friction of asking > friction of occasionally wrong project

### Step 6: Create the Entry

**If creating a REMINDER:**
Create a new page in the Reminders database with:
- **Reminder** (title): The action to do
- **Plan Date**: If specific time/day mentioned
- **Due Date**: If deadline mentioned
- **Status**: "Not started" (default)

**If creating a TASK:**
Create a new page in the Tasks database with:
- **Task** (title): The action to do (concise)
- **Description**: Additional context and details
- **Project**: URL of the identified or General project
- **Plan Date**: If specific time/day mentioned
- **Due Date**: If deadline mentioned
- **Status**: "Not started" (default)

### Step 7: Confirm
Give Olena a brief, natural confirmation:
- ✅ "Got it - I'll remind you to [task] [timing]"
- Keep it conversational and brief
- Don't explain what you did behind the scenes

## Examples

### REMINDER Examples (simple, standalone)

**Input**: "Remind me to call my mom tomorrow at 9am"
- **Routes to**: Reminders DB
- **Reminder**: "Call my mom"
- **Plan Date**: 2025-11-11T09:00:00 (datetime)
- **Due Date**: (empty)
- **Response**: "Got it - I'll remind you to call your mom tomorrow at 9am"

**Input**: "Remind me to buy cat food"
- **Routes to**: Reminders DB
- **Reminder**: "Buy cat food"
- **Plan Date**: (empty)
- **Due Date**: (empty)
- **Response**: "Got it - I'll remind you to buy cat food"

**Input**: "Remind me to water plants in 30 minutes"
- **Routes to**: Reminders DB
- **Reminder**: "Water plants"
- **Plan Date**: 2025-11-10T[current_time + 30 minutes] (datetime)
- **Due Date**: (empty)
- **Response**: "Got it - I'll remind you to water plants in 30 minutes"

### TASK Examples (project-related, complex)

**Input**: "I need to call the gallery about the ED awareness exhibition by Friday to ask about February availability and their community exhibition program"
- **Routes to**: Tasks DB
- **Task**: "Call gallery about ED awareness exhibition"
- **Description**: "Ask about February availability and their community exhibition program"
- **Plan Date**: (empty)
- **Due Date**: 2025-11-15
- **Project**: (search for "ED awareness" project)
- **Response**: "Got it - I'll remind you to call the gallery by Friday for the ED awareness project"

**Input**: "I need to build a content repurposing skill for my Imagination Substack that converts posts into Twitter threads"
- **Routes to**: Tasks DB
- **Task**: "Build content repurposing skill for Imagination Substack"
- **Description**: "Converts posts into Twitter threads and LinkedIn posts"
- **Plan Date**: (empty)
- **Due Date**: (empty)
- **Project**: (search for "Substack" or "Imagination" project, or General)
- **Response**: "Got it - added task to build the content repurposing skill"

**Input**: "Remind me to email the gallery about the exhibition tomorrow - need to confirm their availability and mention the ED awareness theme"
- **Routes to**: Tasks DB (has project context + details, even though it says "remind me")
- **Task**: "Email gallery about exhibition"
- **Description**: "Confirm their availability and mention the ED awareness theme"
- **Plan Date**: 2025-11-11
- **Due Date**: (empty)
- **Project**: (search for "exhibition" or "ED awareness" project)
- **Response**: "Got it - I'll remind you to email the gallery tomorrow"

## Key Principles

### Routing Intelligence
1. **Decide automatically** - Olena shouldn't have to think "is this a reminder or task?"
2. **Use language cues**: "Remind me" often suggests Reminder, "I need to" suggests Task
3. **Project context wins** - if ANY project is mentioned, it's probably a Task
4. **Details matter** - if there's explanation beyond the action itself, it's a Task
5. **When in doubt, go with Task** - better to have richer structure available

### Title vs Description (for Tasks)
6. **Title = scannable action** - verb + object, concise
7. **Description = context** - the "why", "how", or additional details
8. **Extract smartly** - pull out the essential action for the title, everything else goes to description

### General Best Practices
9. **Use intelligent project matching** - query Active projects, read Goals/Descriptions, make semantic matches based on what the task is *about*, not just keyword matching
10. **Default to General Project** when unsure - better than failing or asking for clarification
11. **Keep confirmations brief and natural** - no need to explain the mechanics or which database was used
12. **Parse dates intelligently** - understand "tomorrow", "next week", "Friday", "in 30 minutes", "in 2 hours", etc. based on current date/time
13. **Handle relative time** - calculate exact datetime for "in X minutes/hours" from current time
14. **Never ask Olena to clarify** - make your best guess and move forward
