---
name: reminder-keeper
description: Create task reminders in Notion using natural language. Use when the user says things like "remind me to...", "I need to...", or mentions doing something at a specific time or by a deadline. Handles date/time parsing, project linking, and creates tasks in Notion.
---

# Reminder Skill

## Purpose
Enable Olena to create task reminders using natural, conversational language without needing to think about Notion structure.

## Database IDs
- **Areas of Interest**: collection://2a708620-e1b0-80bf-b537-000be39d5d7a
- **Projects**: collection://2a708620-e1b0-8017-9b32-000b5045104a
- **Tasks**: collection://2a708620-e1b0-807e-b3eb-000b698751cc

## Default Values
- **General Area URL**: https://www.notion.so/2a708620e1b0811bab8ed2364625ad9e
- **General Project URL**: https://www.notion.so/2a708620e1b0817dbb37f46a6852a85b

## How It Works

When Olena says something like:
- "Remind me to call my mom tomorrow at 9am"
- "Remind me to get groceries tomorrow"
- "Remind me to call the exhibition place this week for the ED awareness project"

### Step 1: Parse the Request
Extract:
1. **Task description** - the thing to do (e.g., "call my mom")
2. **Timing** - when to do it (e.g., "tomorrow at 9am", "this week")
3. **Project reference** (optional) - which project it relates to (e.g., "ED awareness project", "exhibition")

### Step 2: Determine Plan Date vs Due Date
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

### Step 3: Identify the Project
- If Olena mentions a specific project (e.g., "ED awareness", "exhibition", "Houston show"):
  1. Search Projects database for matching project name
  2. Link the task to that project
  
- If no project mentioned or can't find a match:
  - Use the **General Project** (https://www.notion.so/2a708620e1b0817dbb37f46a6852a85b)

### Step 4: Create the Task
Create a new page in the Tasks database with:
- **Task** (title): The task description
- **Project**: URL of the identified or General project
- **Plan Date**: If specific time/day mentioned
- **Due Date**: If deadline mentioned
- **Status**: "Not started" (default)

### Step 5: Confirm
Give Olena a brief, natural confirmation:
- ✅ "Got it - I'll remind you to [task] [timing]"
- Keep it conversational and brief
- Don't explain what you did behind the scenes

## Examples

**Input**: "Remind me to call my mom tomorrow at 9am"
- Task: "Call my mom"
- Plan Date: 2025-11-11T09:00:00 (datetime)
- Due Date: (empty)
- Project: General
- Response: "Got it - I'll remind you to call your mom tomorrow at 9am"

**Input**: "Remind me to email the gallery about the ED awareness exhibition by Friday"
- Task: "Email the gallery about the ED awareness exhibition"
- Plan Date: (empty)
- Due Date: 2025-11-15
- Project: (search for "ED awareness" project)
- Response: "Got it - I'll remind you to email the gallery by Friday for the ED awareness project"

**Input**: "Remind me to buy cat food"
- Task: "Buy cat food"
- Plan Date: (empty)
- Due Date: (empty)
- Project: General
- Response: "Got it - I'll remind you to buy cat food"

**Input**: "Remind me to water plants in 30 minutes"
- Task: "Water plants"
- Plan Date: 2025-11-10T[current_time + 30 minutes] (datetime)
- Due Date: (empty)
- Project: General
- Response: "Got it - I'll remind you to water plants in 30 minutes"

## Key Principles
1. **Be intelligent about project matching** - look for keywords like "exhibition", "ED awareness", "book", "consulting", etc.
2. **Default to General** when unsure - better than failing or asking for clarification
3. **Keep confirmations brief and natural** - no need to explain the mechanics
4. **Parse dates intelligently** - understand "tomorrow", "next week", "Friday", "in 30 minutes", "in 2 hours", etc. based on current date/time
5. **Handle relative time** - calculate exact datetime for "in X minutes/hours" from current time
6. **Never ask Olena to clarify** the project unless absolutely necessary - make your best guess
