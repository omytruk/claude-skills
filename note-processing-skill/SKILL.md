---
name: note-processor
description: Review and process unprocessed brain dump notes. Use when the user asks to see or process their notes, e.g., "what did I dump on you", "show me my notes", "let's process my brain dump", or "what notes do I need to process". Converts notes to tasks or projects.
---

# Note Processing Skill

## Purpose
Help Olena review and process her unprocessed brain dump notes whenever she's ready - daily, weekly, or whenever she feels like it. Turn raw thoughts into actionable items, project ideas, or organized knowledge.

## Database IDs
- **Brain Dump**: collection://2a708620-e1b0-80cc-bbba-000b6e2fdb7b
- **Projects**: collection://2a708620-e1b0-8017-9b32-000b5045104a
- **Tasks**: collection://2a708620-e1b0-807e-b3eb-000b698751cc
- **Areas of Interest**: collection://2a708620-e1b0-80bf-b537-000be39d5d7a

## How It Works

When Olena says something like:
- "What did I dump on you?"
- "What notes do I need to process?"
- "Show me my unprocessed notes"
- "Let's process my brain dump"
- "What's in my brain dump from this week?"

### Step 1: Query Unprocessed Notes
Search the Brain Dump database for entries where:
- **Processed = "__NO__"**
- Optionally filter by date range if Olena specifies:
  - "from this week"
  - "from today"
  - "from the last few days"
  - "since Monday"

### Step 2: Present the List
Show all unprocessed notes in a clean, scannable format:

```
Here are your [X] unprocessed notes:

1. [Note content] - Nov 10
2. [Note content] - Nov 9
3. [Note content] - Nov 8
...

What would you like to do with these?
```

Keep it simple and numbered for easy reference.

### Step 3: Help Process Each Note
As Olena works through the notes, she might:

**A) Turn it into a task**
- Use the Reminder Skill to create a task
- Mark the note as Processed
- Example: "Let's make #3 a task to do by Friday"

**B) Turn it into a project idea**
- Use Work Structurer Skill to set up the project properly
- Mark the note as Processed
- Example: "That's actually a project idea - add it to my Projects"

**C) Save it to Obsidian**
- Just acknowledge that she's saving it
- Mark the note as Processed
- Example: "I saved #5 to Obsidian, mark it as processed"

**D) Just mark it as done**
- Sometimes she just needs to acknowledge it or it's no longer relevant
- Mark the note as Processed
- Example: "I can mark #2 as done" or "Delete #4"

**E) Keep it unprocessed**
- Leave it as-is for later
- Don't change the Processed status
- Example: "I'll come back to #1 later"

### Step 4: Update Processed Status
When Olena is done with a note (any of A, B, C, or D above):
- Update the note's **Processed** field to "__YES__"

### Step 5: Wrap Up
After processing, give a quick summary:
```
✅ Processed [X] notes, [Y] remain unprocessed
```

## Processing Patterns

**Single Note Processing:**
"Process note #3" → Help with just that one note

**Batch Processing:**
"Let's process all of them" → Go through one by one or let her direct

**Quick Scan:**
"Just show me what's there" → List them, no processing yet

**Selective Processing:**
"Just show me notes about the exhibition" → Filter by "Related To" field

## Examples

### Example 1: Full Processing Session

**Olena**: "What did I dump on you this week?"

**Claude**: "Here are your 5 unprocessed notes from this week:

1. I want to explore partnering with local mental health organizations for the ED awareness exhibition - Nov 10
2. what if the book isn't about imagination in general but specifically about imagination in the age of AI? - Nov 9  
3. feeling overwhelmed by all the projects, need to figure out how to prioritize - Nov 8
4. Found an interesting gallery space on Westheimer, need to check if they do community exhibitions - Nov 7
5. ADHD system idea: color-code tasks by energy level needed - Nov 7

What would you like to do with these?"

**Olena**: "Let's make #4 a task to research that gallery"

**Claude**: ✅ "Got it - I'll remind you to research the Westheimer gallery space" [creates task + marks note as processed]

**Olena**: "I saved #2 to Obsidian, mark it processed"

**Claude**: ✅ "Marked as processed"

**Olena**: "#5 is not relevant anymore, delete it"

**Claude**: ✅ "Marked as processed"

### Example 2: Quick Check

**Olena**: "Any notes I should process?"

**Claude**: "You have 3 unprocessed notes from the past few days. Want to see them?"

**Olena**: "Not right now"

**Claude**: "No problem - they'll be here whenever you're ready"

### Example 3: Filtered View

**Olena**: "Show me brain dump notes about the exhibition"

**Claude**: "Here are 2 unprocessed notes related to the exhibition:

1. I want to explore partnering with local mental health organizations for the ED awareness exhibition - Nov 10
2. Found an interesting gallery space on Westheimer, need to check if they do community exhibitions - Nov 7

Want to process these?"

## Key Principles
1. **Flexible timing** - support daily, weekly, or whenever processing
2. **Easy reference** - number the notes for quick reference
3. **Support various outcomes** - task, project, Obsidian, or just done
4. **Don't force processing** - if she's not ready, that's fine
5. **Track completion** - update Processed status immediately when done
6. **Keep it conversational** - this isn't a chore, it's organizing thoughts
7. **Integrate with other skills** - use Problem Externalizer for overwhelming notes, Work Structurer for complex projects, Reminder Skill for tasks
