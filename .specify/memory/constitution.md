<!--
Sync Impact Report:
- Version change: N/A → 1.0.0
- Added sections: All principles and content from the provided Todo constitution
- Templates requiring updates: N/A (first creation)
- No previously existing principles modified
- No sections removed
- No follow-up items pending
-->
# Todo Constitution
<!-- Example: Spec Constitution, TaskFlow Constitution, etc. -->

## Core Objective
Build a minimal, clean, pleasant-to-use command-line todo application that stores tasks only in memory (no persistence of any kind), implements exactly 5 essential features, and demonstrates excellent code quality and user experience within hackathon constraints.

## Core Principles

### Code Quality
Strict PEP 8 compliance, Type hints mandatory (Python 3.13+), Meaningful names > cleverness, Functions ≤ 25 lines whenever possible, Single responsibility principle, Proper exception handling with helpful user messages, Minimal comments — code must be self-explanatory.

### User Experience
Persistent menu loop until explicit quit, Numbered menu options (1. Add task, 2. View all tasks, 3. Update task, 4. Delete task, 5. Toggle complete/incomplete, 0. Quit), Graceful handling of ALL invalid inputs, Clear feedback after every operation, Compact but readable task list format.

### Technical Constraints
Python 3.13+, Zero external dependencies (rich is allowed but optional), In-memory only: list[dict] or dataclass/Task class, No file/I/O, no database, no json/pickle save/load, No colors unless using rich (and optional).

### Project Structure (Mandatory)
The required project structure including .specify/, src/, pyproject.toml and README.md with specific file locations:
```
.
├── .specify/
│   ├── memory/
│   │   └── constitution.md        ← this file
│   └── history/                   ← all generated specs go here
├── src/
│   └── todo.py                    ← main application (can split later)
├── pyproject.toml
└── README.md
```

### Development Process Rules
Use Spec-Kit Plus workflow, Gemini as primary model for spec/code generation, Every major step must produce a spec document, All specs preserved in .specify/history/, Human must review & approve every generated code block, Commit often with semantic commit messages.

### Success Definition (Phase I Exit Criteria)
All 5 features implemented and working, No crashes on normal & edge-case inputs, Beautiful, readable console output, Follows project structure exactly, Contains constitution + spec history, Clear README with setup & demo commands.

## Explicit Non-Goals for Phase I (Forbidden Features)
Due dates/reminders, Priority levels, Categories/tags/labels, Search/filter/sort, Multiple users, File save/load/export, Unit tests (allowed in structure, not required), Fancy TUI/curses/textual, API/web interface.

## Governance
This constitution is the supreme document for all decisions in Phase I of Todo. Any deviation must be explicitly documented in the spec history, justified with clear reasoning, and approved by the project owner.

**Version**: 1.0.0 | **Ratified**: 2025-12-30 | **Last Amended**: 2026-01-02
