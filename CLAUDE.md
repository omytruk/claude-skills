# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository is evolving into a comprehensive ADHD-friendly AI organization and productivity system. It contains custom Claude skills for task management and thought organization, integrated with Notion databases. The system is designed for conversational, zero-friction interactions that work with ADHD brains rather than against them.

## Architecture

### Skill Structure
Each skill is self-contained in its own directory with a `SKILL.md` file that defines:
- Purpose and use cases
- Notion database IDs and URLs
- Workflow steps and logic
- Natural language parsing rules
- Response patterns and confirmations

### Five Core Skills

1. **action-keeper** (action-keeper-skill/): Intelligent reminder and task creation
   - Automatically routes to Reminders (simple, standalone) or Tasks (project-related, complex)
   - Parses natural language for both reminders and tasks
   - Extracts title vs description for tasks
   - Handles Plan Date vs Due Date logic
   - Links tasks to projects automatically
   - Supports relative time ("in 30 minutes", "tomorrow at 9am")
   - Zero decision fatigue - just say what you need

2. **brain-dumper** (brain-dump-skill/): Frictionless thought capture
   - Zero-structure note capture
   - Minimal confirmation responses
   - Deferred processing approach
   - Optional context tagging

3. **note-processor** (note-processing-skill/): Review and organize brain dumps
   - Batch or selective note processing
   - Converts notes to tasks or projects
   - Marks processed items
   - Supports filtered views
   - Integrates with other skills for complex processing

4. **problem-externalizer** (problem-externalizer-skill/): Structured problem externalization
   - Helps separate person from problem through interview process
   - Reduces rumination and overwhelm via 5-phase structure
   - Defines boundaries and actionable components
   - Creates clear next steps from complex situations
   - Integrates seamlessly with work-structurer and action-keeper

5. **work-structurer** (work-structurer-skill/): Notion hierarchy setup and project structuring
   - Creates proper Areas → Projects → Tasks hierarchy
   - Helps discover project goals through guided questions
   - Sets up full project structure efficiently
   - Supports both quick setup and discovery mode
   - Integrates with other skills for complete workflow

### Notion Integration

All skills interact with specific Notion databases:
- **Reminders**: `2a808620-e1b0-8050-9725-cd9c8a75c924` (simple, standalone actions)
- **Tasks**: `2a708620-e1b0-80f9-9306-f1d6d0984dbb` (project-related work with descriptions)
- **Projects**: `2a708620-e1b0-8038-9898-d5ad146c9cbd`
- **Areas of Interest**: `2a708620-e1b0-80db-99b4-ec4706808135`
- **Brain Dump**: `2a708620-e1b0-80be-9b2b-e0540ca13548`

Default fallbacks:
- General Area: https://www.notion.so/2a708620e1b0811bab8ed2364625ad9e
- General Project: https://www.notion.so/2a708620e1b0817dbb37f46a6852a85b

## Key Design Principles

1. **Conversational UI**: All interactions should feel natural, like talking to an assistant
2. **Minimal friction**: Confirmations should be brief ("Got it", "Noted", "✅")
3. **Intelligent defaults**: Use General project/area when unsure rather than asking for clarification
4. **Smart parsing**: Handle various date/time formats and project references contextually
5. **Process later, not now**: Brain dump first, organize during dedicated review sessions

### ADHD-Friendly Design

The system is specifically designed to work with ADHD thought patterns:
- **Capture in the moment**: No structure required when ideas strike
- **Zero decision fatigue**: Intelligent defaults eliminate choice paralysis
- **Flexible processing**: Review and organize when ready, not forced
- **Natural language**: No need to remember syntax or formats
- **Quick confirmations**: Minimal interruption to flow state

## Working with Skills

### Intelligent Routing: Reminders vs Tasks

The action-keeper skill automatically decides whether to create a Reminder or Task based on context:

**Route to REMINDERS when:**
- Simple, standalone action (e.g., "get groceries", "call mom")
- Starts with "Remind me to..."
- No project context or detailed information
- Just needs to be checked off a list

**Route to TASKS when:**
- Related to a project or area of work
- Starts with "I need to..." or "I should..."
- Has context, details, or is part of a workflow
- Examples: "call gallery about exhibition", "build new Claude skill"

**Task Structure:**
- **Title**: Concise action (verb + object)
- **Description**: Additional context, details, why/how information
- **Project**: Always linked to a project (or General Project)

**When in doubt:** If there's ANY project context or detail → Task. If standalone → Reminder.

### Date/Time Parsing Logic
- **Plan Date** = when user wants to do the task (specific datetime)
- **Due Date** = deadline for completion (date only or end of period)
- Understand relative time: "in 30 minutes", "tomorrow", "this week", "by Friday"
- Current date context is critical for accurate parsing

### Intelligent Project Matching (for Tasks)

Use semantic understanding, not just keyword search:

**Process:**
1. Query Active Projects first (Status = "Active")
2. Read full context: Name, Goal, and Description fields
3. Make semantic matches based on what the task is *about*
4. Consider domain/topic alignment with project goals
5. Fall back to keyword matching if semantic matching unclear
6. Default to General Project if no clear match

**Examples:**
- "Write about imagination and AI" → matches Substack project (Goal mentions "imagination")
- "Gallery space for eating disorder art" → matches "ED Awareness Art Series"
- "Research synthography" → matches exhibition project (if Goal mentions synthography)

**Principle:** Never ask for clarification - make intelligent guess and keep flow going

### Note Processing Workflow
1. Query unprocessed notes (Processed = "__NO__")
2. Present numbered list for easy reference
3. Support multiple outcomes per note:
   - Convert to task (use action-keeper skill)
   - Convert to project (use work-structurer skill)
   - Saved to external system (Obsidian)
   - Mark as done/no longer relevant
   - Use problem-externalizer for overwhelming notes
4. Update Processed = "__YES__" immediately when handled

### Problem Externalization Workflow
1. **Dump Phase**: Let user express everything without structure
2. **Boundary Phase**: Define what IS and ISN'T the problem, create separation
3. **Breakdown Phase**: Identify distinct components and sub-problems
4. **Action Phase**: Determine next steps (decisions, actions, information gathering)
5. **Wrap Up**: Present structured summary with clear next actions
6. **Integration**: Offer to create tasks (action-keeper) or projects (work-structurer)

### Work Structuring Workflow
1. **Understand Scope**: Determine if creating Areas, Projects, or Tasks
2. **Create Areas**: Define broad, ongoing areas of interest with descriptions
3. **Create Projects**: Specific outcomes within Areas, with clear goals
4. **Discovery Mode**: Help clarify goals through guided questions when unclear
5. **Task Breakdown**: Optionally break projects into actionable tasks
6. **Present Structure**: Show complete hierarchy with visual formatting
7. **Integration**: Link to action-keeper for task dates, problem-externalizer for overwhelm

### Skill Integration Patterns

The skills are designed to work together seamlessly:

**Brain Dump → Note Processing → Other Skills**
- Capture thoughts with brain-dumper
- Review with note-processor
- Convert to reminders/tasks (action-keeper - automatically routed), projects (work-structurer), or externalize complex issues (problem-externalizer)

**Problem Externalization → Action**
- Use problem-externalizer to clarify overwhelming situations
- Create project structure with work-structurer
- Set up specific reminders or tasks with action-keeper (automatically routed)
- Save additional insights to brain-dumper

**Work Structuring → Task Creation**
- Build Areas/Projects with work-structurer
- Populate with tasks using action-keeper (will create Tasks since they have project context)
- Use problem-externalizer when scope feels overwhelming

**Action-Keeper Intelligence**
- Automatically routes to Reminders or Tasks - no decision needed
- Extracts title vs description for richer task context
- Links tasks to projects while keeping reminders standalone
- Handles all date/time parsing for both types

**Key Principle**: Always offer integration points naturally - "Want me to create a reminder for that?" or "Should we set this up as a project?" or "This sounds overwhelming - want to externalize it together?"

## Response Style
- Keep confirmations brief and natural
- Don't explain mechanics or behind-the-scenes actions
- Use simple acknowledgments: "Got it", "Noted", "Captured"
- Format lists with numbers for easy reference
- Use checkmarks (✅) sparingly for completed actions
