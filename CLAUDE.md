# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains custom Claude skills for personal productivity and task management, integrated with Notion databases. These skills are designed for conversational, natural language interactions.

## Architecture

### Skill Structure
Each skill is self-contained in its own directory with a `SKILL.md` file that defines:
- Purpose and use cases
- Notion database IDs and URLs
- Workflow steps and logic
- Natural language parsing rules
- Response patterns and confirmations

### Three Core Skills

1. **reminder-skill**: Task creation with intelligent date/time parsing
   - Parses natural language for task creation ("remind me to...")
   - Handles Plan Date vs Due Date logic
   - Links tasks to projects automatically
   - Supports relative time ("in 30 minutes", "tomorrow at 9am")

2. **brain-dump-skill**: Frictionless thought capture
   - Zero-structure note capture
   - Minimal confirmation responses
   - Deferred processing approach
   - Optional context tagging

3. **note-processing-skill**: Review and organize brain dumps
   - Batch or selective note processing
   - Converts notes to tasks or projects
   - Marks processed items
   - Supports filtered views

### Notion Integration

All skills interact with specific Notion databases:
- **Tasks**: `collection://2a708620-e1b0-807e-b3eb-000b698751cc`
- **Projects**: `collection://2a708620-e1b0-8017-9b32-000b5045104a`
- **Areas of Interest**: `collection://2a708620-e1b0-80bf-b537-000be39d5d7a`
- **Brain Dump**: `collection://2a708620-e1b0-80cc-bbba-000b6e2fdb7b`

Default fallbacks:
- General Area: https://www.notion.so/2a708620e1b0811bab8ed2364625ad9e
- General Project: https://www.notion.so/2a708620e1b0817dbb37f46a6852a85b

## Key Design Principles

1. **Conversational UI**: All interactions should feel natural, like talking to an assistant
2. **Minimal friction**: Confirmations should be brief ("Got it", "Noted", "✅")
3. **Intelligent defaults**: Use General project/area when unsure rather than asking for clarification
4. **Smart parsing**: Handle various date/time formats and project references contextually
5. **Process later, not now**: Brain dump first, organize during dedicated review sessions

## Working with Skills

### Date/Time Parsing Logic
- **Plan Date** = when user wants to do the task (specific datetime)
- **Due Date** = deadline for completion (date only or end of period)
- Understand relative time: "in 30 minutes", "tomorrow", "this week", "by Friday"
- Current date context is critical for accurate parsing

### Project Matching
- Search for keywords in user input ("ED awareness", "exhibition", "book")
- Match against Projects database names
- Default to General Project if no match or ambiguous
- Never ask for clarification unless absolutely necessary

### Note Processing Workflow
1. Query unprocessed notes (Processed = "__NO__")
2. Present numbered list for easy reference
3. Support multiple outcomes per note:
   - Convert to task (use Reminder skill)
   - Convert to project
   - Saved to external system (Obsidian)
   - Mark as done/no longer relevant
4. Update Processed = "__YES__" immediately when handled

## Response Style
- Keep confirmations brief and natural
- Don't explain mechanics or behind-the-scenes actions
- Use simple acknowledgments: "Got it", "Noted", "Captured"
- Format lists with numbers for easy reference
- Use checkmarks (✅) sparingly for completed actions
