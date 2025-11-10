---
name: brain-dumper
description: Capture thoughts, ideas, and notes quickly without structure. Use when the user says "note this", "brain dump", "record this for later", or shares a thought to save. Zero friction capture with minimal confirmation.
---

# Brain Dump Skill

## Purpose
Enable Olena to quickly capture thoughts, ideas, and notes without any structure or processing required. She can dump anything on her mind, and we'll organize it later during weekly reviews.

## Database ID
- **Brain Dump**: collection://2a708620-e1b0-80cc-bbba-000b6e2fdb7b

## How It Works

When Olena says something like:
- "Claude, note this: [thought/idea]"
- "Brain dump: [random idea]"
- "Record this for later: [something]"
- Or just shares a thought and asks you to save it

### Step 1: Capture the Note
Simply take whatever Olena says and capture it as-is. Don't:
- Try to organize it
- Summarize it
- Structure it
- Question it

Just capture it verbatim (or as close as possible).

### Step 2: Identify Related Context (Optional)
If Olena mentions something that clearly relates to a known area/project, capture that in the "Related To" field:
- "ED awareness"
- "Book writing"
- "Exhibition"
- "Consulting"
- etc.

But if it's not clear, leave "Related To" empty. Don't force it.

### Step 3: Create the Brain Dump Entry
Create a new page in the Brain Dump database with:
- **Note** (title): The captured thought/idea
- **Date**: Auto-populated (created time)
- **Processed**: "__NO__" (unchecked - default)
- **Related To**: Optional context if clear

### Step 4: Confirm
Give a brief, minimal acknowledgment:
- ✅ "Noted"
- ✅ "Got it"
- ✅ "Captured"

Keep it super brief - this is meant to be frictionless.

## Examples

**Input**: "Claude, note this: I want to explore partnering with local mental health organizations for the ED awareness exhibition"
- Note: "I want to explore partnering with local mental health organizations for the ED awareness exhibition"
- Related To: "ED awareness"
- Processed: "__NO__"
- Response: "Noted"

**Input**: "Brain dump: what if the book isn't about imagination in general but specifically about imagination in the age of AI?"
- Note: "what if the book isn't about imagination in general but specifically about imagination in the age of AI?"
- Related To: "Book writing"
- Processed: "__NO__"
- Response: "Got it"

**Input**: "Record this: feeling overwhelmed by all the projects, need to figure out how to prioritize"
- Note: "feeling overwhelmed by all the projects, need to figure out how to prioritize"
- Related To: (empty)
- Processed: "__NO__"
- Response: "Captured"

## Key Principles
1. **Zero friction** - make it as easy as possible to dump thoughts
2. **No judgment or filtering** - capture everything as-is
3. **Minimal confirmation** - don't interrupt her flow
4. **Process later, not now** - the point is to get it out of her head
5. **Trust her process** - she'll organize when she's ready (using the Note Processing skill)
