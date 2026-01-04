---
id: 1
title: update-project-constitution
stage: constitution
date: 2026-01-02
surface: agent
model: 
feature: todo-app
branch: 
user: 
command: /sp.constitution 
labels: [constitution, todo-app, setup]
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files:
 - .specify/memory/constitution.md
tests:
 - 
---

## Prompt

```
/sp.constitution 
# Todo - In-Memory Python Console Todo Application
# Phase I - Basic Level (Core Essentials)
# Last updated: December 30, 2025

## 1. Project Identity
Project Name: Todo
Phase: I
Full Title: Todo - In-Memory Python Console Todo App (Basic Level)
Development Paradigm: Spec-Driven Development using Spec-Kit Plus + Gemini

## 2. Core Objective
Build a minimal, clean, pleasant-to-use command-line todo application that:
- Stores tasks only in memory (no persistence of any kind)
- Implements exactly 5 essential features
- Demonstrates excellent code quality and user experience within hackathon constraints

## 3. Mandatory Features (The Only 5 Allowed in Phase I)
1. Add new task
   - Required fields: title (str), description (str)
   - Auto-generate incremental integer ID starting from 1

2. View all tasks
   - Display: ID, status marker, title, description
   - Status markers: [ ] for incomplete, [X] for complete
   - Clean, aligned, table-like console output

3. Update existing task
   - Modify title and/or description
   - Identify task by ID
   - Partial update allowed (change only one field)

4. Delete task
   - Remove by ID
   - Confirm deletion if task exists

5. Toggle completion status
   - Mark as complete / incomplete (flip boolean)
   - Identify by ID

## 4. Core Principles & Non-Negotiable Rules

### Code Quality
- Strict PEP 8 compliance
- Type hints mandatory (Python 3.13+)
- Meaningful names > cleverness
- Functions ≤ 25 lines whenever possible
- Single responsibility principle
- Proper exception handling with helpful user messages
- Minimal comments — code must be self-explanatory

### User Experience
- Persistent menu loop until explicit quit
- Numbered menu options:
  1. Add task
  2. View all tasks
  3. Update task
  4. Delete task
  5. Toggle complete/incomplete
  0. Quit
- Graceful handling of ALL invalid inputs
- Clear feedback after every operation
- Compact but readable task list format

### Technical Constraints
- Python 3.13+
- Zero external dependencies (rich is allowed but optional)
- In-memory only: list[dict] or dataclass/Task class
- No file/I/O, no database, no json/pickle save/load
- No colors unless using rich (and optional)

### Project Structure (Mandatory)
.
├── .specify/
│   ├── memory/
│   │   └── constitution.md        ← this file
│   └── history/                   ← all generated specs go here
├── src/
│   └── todo.py                    ← main application (can split later)
├── pyproject.toml
└── README.md

## 5. Development Process Rules
1. Use Spec-Kit Plus workflow
2. Gemini as primary model for spec/code generation
3. Every major step must produce a spec document
4. All specs preserved in .specify/history/
5. Human must review & approve every generated code block
6. Commit often with semantic commit messages

## 6. Success Definition (Phase I Exit Criteria)
☑ All 5 features implemented and working
☑ No crashes on normal & edge-case inputs
☑ Beautiful, readable console output
☑ Follows project structure exactly
☑ Contains constitution + spec history
☑ Clear README with setup & demo commands

## 7. Explicit Non-Goals for Phase I (Forbidden Features)
× Due dates / reminders
× Priority levels
× Categories / tags / labels
× Search / filter / sort
× Multiple users
× File save / load / export
× Unit tests (allowed in structure, not required)
× Fancy TUI / curses / textual
× API / web interface

## 8. Binding Statement
This constitution is the supreme document for all decisions in Phase I of Toda.
Any deviation must be:
- Explicitly documented in the spec history
- Justified with clear reasoning
- Approved by the project owner
```

## Response snapshot

The constitution file at `.specify/memory/constitution.md` has been successfully updated with the provided content for the Todo application project. The update included:

1. Setting the project name to "Todo"
2. Adding the core objective of building a minimal, clean, command-line todo application
3. Defining 6 core principles:
   - Code Quality
   - User Experience
   - Technical Constraints
   - Project Structure (Mandatory)
   - Development Process Rules
   - Success Definition (Phase I Exit Criteria)
4. Including the non-goals section for Phase I
5. Adding governance information
6. Including version information (Version 1.0.0, Ratified: 2025-12-30, Last Amended: 2026-01-02)

The file now contains all the necessary guidance and constraints for the Todo application development following the Spec-Driven Development approach.

## Outcome

- ✅ Impact: Successfully updated project constitution with specific requirements for the Todo application
- 🧪 Tests: N/A (documentation update)
- 📁 Files: Updated .specify/memory/constitution.md with comprehensive project guidelines
- 🔁 Next prompts: Ready to proceed with spec creation based on this constitution
- 🧠 Reflection: The constitution provides clear boundaries and principles for the Todo app development, which will guide all future implementation decisions.

## Evaluation notes (flywheel)

- Failure modes observed: None
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): Begin feature specification based on this constitution