# Feature Specification: Todo CLI App Enhancement (Organization & Usability)

**Feature Branch**: `002-todo-enhancement`
**Created**: 2026-01-02
**Status**: Draft
**Input**: User description: "Intermediate Level - Todo CLI App (Organization & Usability) Project: Todo (In-Memory Python Console Todo App) Level: Intermediate (builds directly on Basic/Phase I) Target model: Qwen (Qwen2.5-Coder or similar recommended) Goal: Basic todo app ko zyada practical aur polished banane ke liye organization aur usability features add karna Must-have new features: 1. Priority - Levels: high / medium / low (default = medium) - Add aur Update ke time set karne ka option - View list mein clear dikhaye (jaise !!! / !! / ! ya color agar rich use kar rahe ho) 2. Tags / Categories - Multiple tags per task (space ya comma se separate) - Example: work urgent python shopping - View list mein dikhe (short form mein) 3. Due Date (strongly recommended) - Input: YYYY-MM-DD ya simple words (tomorrow, next friday, in 3 days) - View list mein show ho 4. Search - Keyword search title + description + tags mein - Case insensitive 5. Filter - Status: all / pending / completed - Priority: high / medium / low / all - Tag: koi specific tag 6. Sort - Priority (high → low) - Due date (jaldi waale pehle, bina date waale last) - Title (alphabetical A-Z) - Default: creation order Important Rules: - Sab kuch purely in-memory rahega (koi file/db nahi) - Same menu-driven loop mein hi integrate karna (sub-menu ya extra choices add kar sakte ho) - Code: clean, type hints, PEP 8 - Dependencies: sirf optional 'rich' (better table ke liye recommended) - Phase I ke purane features bilkul safe aur working rahenge Success looks like: - Task add karte waqt priority + tags + date naturally set ho jaaye - 20-40 tasks hone par bhi list readable rahe - Quick search/filter/sort se kaam asaan ho jaaye - User bol sake: "pending high priority work tasks dikha do" Not in this level: - File save / load / export - Recurring tasks - Reminders / notifications - Complex natural language input - Statistics / reports Qwen se chahiye: - Updated data model (Task class mein naye fields) - CLI flow suggestions (menu kaise badhega) - Clear implementation steps / code structure"

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Enhanced Task Creation (Priority: P1)

As a user, I want to add tasks with priority levels, tags, and due dates so that I can better organize and prioritize my work.

**Why this priority**: This is the foundation for all other features. Without the ability to add enhanced tasks, the filtering, searching, and sorting features have no data to work with.

**Independent Test**: Can be fully tested by adding tasks with different priorities, tags, and due dates and verifying they are stored correctly in the system.

**Acceptance Scenarios**:

1. **Given** I am on the task creation screen, **When** I enter a task title and set priority to "high", add tags "work urgent", and set due date to "tomorrow", **Then** the task is created with all specified attributes.
2. **Given** I am on the task creation screen, **When** I enter a task title without specifying priority, tags, or due date, **Then** the task is created with default priority "medium", no tags, and no due date.

---

### User Story 2 - Task Search and Filter (Priority: P1)

As a user, I want to search and filter my tasks by keywords, status, priority, and tags so that I can quickly find and focus on relevant tasks.

**Why this priority**: This is a core usability feature that allows users to manage their tasks efficiently, especially when they have 20-40 tasks in the system.

**Independent Test**: Can be fully tested by creating multiple tasks with different attributes and then searching/filtering to verify the correct subset of tasks is displayed.

**Acceptance Scenarios**:

1. **Given** I have multiple tasks with different priorities and tags, **When** I filter by "high priority" and "work" tag, **Then** only high priority tasks with the "work" tag are displayed.
2. **Given** I have tasks with various titles and descriptions, **When** I search for "python", **Then** all tasks containing "python" in title, description, or tags are displayed (case insensitive).

---

### User Story 3 - Task Sorting (Priority: P2)

As a user, I want to sort my tasks by priority, due date, or title so that I can view them in an order that makes sense for my workflow.

**Why this priority**: This enhances the usability of the task list by allowing users to organize tasks in meaningful ways, particularly important for prioritizing urgent tasks.

**Independent Test**: Can be fully tested by creating tasks with different priorities and due dates, then applying different sorting options to verify the correct order.

**Acceptance Scenarios**:

1. **Given** I have tasks with different priorities, **When** I select "sort by priority", **Then** tasks are displayed with high priority first, then medium, then low.
2. **Given** I have tasks with different due dates, **When** I select "sort by due date", **Then** tasks are displayed with the nearest due date first, followed by tasks without due dates.

---

### User Story 4 - Enhanced Task Display (Priority: P2)

As a user, I want to see priority indicators, tags, and due dates clearly displayed in the task list so that I can quickly assess task importance and deadlines.

**Why this priority**: This is essential for the usability of the enhanced features. Without clear visual indicators, users won't benefit from the added organization features.

**Independent Test**: Can be fully tested by creating tasks with various attributes and verifying they are displayed with appropriate visual indicators in the list.

**Acceptance Scenarios**:

1. **Given** I have tasks with different priorities, **When** I view the task list, **Then** high priority tasks are clearly marked with "!!!" or similar indicator.
2. **Given** I have tasks with different tags and due dates, **When** I view the task list, **Then** tags and due dates are displayed in a readable format next to each task.

### Edge Cases

- What happens when a user enters an invalid date format for due date?
- How does the system handle tasks with very long titles or many tags that exceed display width?
- What if a user tries to search with an empty string or only whitespace?
- How does the system handle tasks with multiple tags that exceed a reasonable display limit?

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: System MUST support three priority levels: high, medium, and low, with medium as the default when creating tasks
- **FR-002**: System MUST allow users to assign multiple tags to tasks, with tags separated by spaces or commas
- **FR-003**: System MUST accept due dates in YYYY-MM-DD format or simple natural language (tomorrow, next friday, in 3 days)
- **FR-004**: System MUST provide keyword search functionality that searches across task titles, descriptions, and tags (case insensitive)
- **FR-005**: System MUST provide filtering options for status (all/pending/completed), priority (high/medium/low/all), and specific tags
- **FR-006**: System MUST provide sorting options by priority (high→low), due date (soonest first), and title (alphabetical)
- **FR-007**: System MUST display priority indicators, tags, and due dates clearly in the task list view
- **FR-008**: System MUST store all data in memory only, with no file or database persistence
- **FR-009**: System MUST maintain all existing Phase I features while adding new functionality
- **FR-010**: System MUST provide a menu-driven interface that integrates new features seamlessly

### Key Entities *(include if feature involves data)*

- **Task**: Represents a user task with attributes including title, description, status (pending/completed), priority (high/medium/low), tags (list of strings), and due date (optional date)
- **TaskList**: Collection of Task entities with methods for searching, filtering, and sorting based on various criteria

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Users can add tasks with priority, tags, and due date in under 30 seconds
- **SC-002**: Users can search/filter/sort tasks and see results displayed in under 2 seconds even with 40 tasks in the system
- **SC-003**: 90% of users can successfully create a task with priority, tags, and due date on their first attempt
- **SC-004**: Users can find specific tasks using search functionality 95% of the time when the task exists
- **SC-005**: Task list remains readable and usable with 20-40 tasks displayed with all enhanced attributes
- **SC-006**: Users can successfully filter tasks by priority, status, and tags 95% of the time
