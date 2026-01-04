# Feature Specification: Todo CLI App Enhancement (Intelligent Features)

**Feature Branch**: `003-todo-intelligent-features`
**Created**: 2026-01-03
**Status**: Draft
**Input**: User description: "Advanced Level Specification - Todo CLI App (Intelligent Features) Project: Todo (In-Memory Python Console Todo App) Level: Advanced (builds on Basic + Intermediate) Target model: Qwen (Qwen2.5-Coder preferred) or any strong coding model Goal: Basic + organized todo app ko intelligent aur future-ready banane ke liye recurring tasks aur proper time-based reminders add karna Must-have new features (Advanced level): 1. Recurring Tasks - Support repeating patterns: daily, weekly, monthly, yearly - Optional: every X days/weeks (e.g. every 3 days, every 2 weeks) - When task is marked complete → auto-create next occurrence with updated due date - Show recurrence pattern in view list (e.g. \"↻ weekly\") 2. Due Dates with Time - Full datetime support (date + time) - Input formats: flexible (YYYY-MM-DD HH:MM, tomorrow 3pm, next monday 9:00, in 2 hours, etc.) - Display format in view: relative (\"in 2h\", \"tomorrow 9:00\") + absolute 3. Reminders / Overdue Awareness - In-app reminder system: - When viewing list → show overdue tasks in red/bold (if rich used) - Show upcoming tasks (e.g. due in next 24h) highlighted - Optional stretch: simple timed console notification (thread/timer based) - Note: No real browser/push notifications (CLI limitation) — only in-app visual + audio beep if possible Data Model Changes: - Task fields to add/update: - due_datetime: datetime.datetime | None - recurrence: str | None # e.g. \"weekly\", \"every 3 days\", \"monthly\" - next_occurrence: datetime.datetime | None (for calculation) CLI / UX Changes: - Add task: extra questions for due date/time + recurrence (optional) - Update task: allow changing due date/time + recurrence - View list: enhanced columns → Due (relative), Recurrence - New menu options / sub-menu: - Show upcoming (next 24h/7d) - Show overdue - Auto-reschedule logic when toggling complete on recurring task Important Constraints: - Still 100% in-memory (no persistence in Advanced level either) - Use datetime module + dateutil (if allowed) for parsing flexible dates - Dependencies: - optional rich (strongly recommended now) - optional python-dateutil (for better natural language date parsing) - Keep console responsive — no blocking long timers - Existing basic + intermediate features must remain fully functional Success Criteria: - Can create weekly grocery task → mark complete → next week instance auto appears - Due dates with time show correctly (past/future, relative time) - Overdue tasks clearly visible every time user opens list - Flexible date input works reasonably well - App remains fast & clean even with 50+ tasks Not in scope for Advanced: - File/database persistence (save/load) - Real system notifications / tray icon - Mobile/web sync - AI smart suggestions - Calendar integration Qwen output expectation: - Updated Task data model with new fields - Suggested natural date parsing strategy - Logic for auto-rescheduling recurring tasks - Proposed menu extensions - Key function signatures / pseudo-code for critical parts"

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Recurring Tasks Management (Priority: P1)

As a user, I want to create recurring tasks with different patterns (daily, weekly, monthly, yearly) so that I don't have to manually create repetitive tasks like weekly grocery shopping or monthly bill payments.

**Why this priority**: This is the core intelligent feature that differentiates the app from basic todo apps. It provides significant time savings for users with repetitive tasks.

**Independent Test**: Can be fully tested by creating a weekly recurring task, marking it complete, and verifying that a new instance with an updated due date is automatically created.

**Acceptance Scenarios**:

1. **Given** I have a weekly recurring task "Buy groceries", **When** I mark it as complete, **Then** a new instance of the task with the same details but a due date 7 days in the future is automatically created.
2. **Given** I want to create a recurring task, **When** I specify the recurrence pattern (daily, weekly, monthly, yearly), **Then** the task is saved with the recurrence information and shows the recurrence indicator in the task list.

---

### User Story 2 - Time-Based Due Dates (Priority: P1)

As a user, I want to set due dates with time information (not just dates) so that I can schedule tasks more precisely throughout the day.

**Why this priority**: This enables proper time management and scheduling, which is essential for the reminder system to work effectively.

**Independent Test**: Can be fully tested by creating tasks with various datetime formats and verifying they are correctly parsed and displayed with both absolute and relative time information.

**Acceptance Scenarios**:

1. **Given** I'm adding a task, **When** I enter a flexible datetime format like "tomorrow 3pm" or "in 2 hours", **Then** the system correctly parses and stores the datetime.
2. **Given** I have tasks with due datetimes, **When** I view the task list, **Then** the due times are displayed in both absolute format and relative format (e.g. "in 2h", "tomorrow 9:00").

---

### User Story 3 - Overdue and Upcoming Task Awareness (Priority: P2)

As a user, I want to be visually aware of overdue and upcoming tasks so that I can prioritize my work effectively and never miss important deadlines.

**Why this priority**: This provides the intelligent reminder functionality that helps users stay on top of their tasks without external notifications.

**Independent Test**: Can be fully tested by creating tasks with past and future due dates, then viewing the task list to verify that overdue tasks are visually distinct and upcoming tasks are highlighted.

**Acceptance Scenarios**:

1. **Given** I have tasks with past due dates, **When** I view the task list, **Then** overdue tasks are visually highlighted (e.g. in red/bold).
2. **Given** I have tasks due in the next 24 hours, **When** I view the task list, **Then** upcoming tasks are visually highlighted.

---

### User Story 4 - Advanced Task Filtering and Navigation (Priority: P2)

As a user, I want to filter tasks by due status (overdue, upcoming) so that I can quickly focus on the most time-sensitive tasks.

**Why this priority**: This enhances the usability of the reminder system by allowing users to quickly navigate to the most critical tasks.

**Independent Test**: Can be fully tested by creating tasks with various due date statuses and using the filter options to view only overdue or upcoming tasks.

**Acceptance Scenarios**:

1. **Given** I have various tasks with different due date statuses, **When** I select "Show overdue tasks", **Then** only tasks with past due dates are displayed.
2. **Given** I have various tasks with different due date statuses, **When** I select "Show upcoming tasks", **Then** only tasks due in the next 24 hours are displayed.

---

### Edge Cases

- What happens when a recurring task is marked complete but the user wants to skip the next occurrence?
- How does the system handle tasks with very long recurrence intervals (e.g., yearly) when the due date falls on a non-existent date (e.g., Feb 29 in non-leap years)?
- What if the user enters an invalid or ambiguous datetime format?
- How does the system handle multiple recurring tasks that become due at the same time?

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: System MUST support recurring task patterns: daily, weekly, monthly, yearly, and custom intervals (e.g. every X days/weeks)
- **FR-002**: System MUST automatically create the next occurrence of a recurring task when the current one is marked complete
- **FR-003**: System MUST store due dates with time information (datetime) rather than just dates
- **FR-004**: System MUST support flexible datetime input formats including natural language (tomorrow 3pm, next monday 9:00, in 2 hours)
- **FR-005**: System MUST display due datetimes in both absolute (e.g. "2026-01-04 15:00") and relative formats (e.g. "in 2h", "tomorrow 3pm")
- **FR-006**: System MUST visually highlight overdue tasks when viewing the task list
- **FR-007**: System MUST visually highlight upcoming tasks (due in next 24 hours) when viewing the task list
- **FR-008**: System MUST provide menu options to filter and view only overdue tasks
- **FR-009**: System MUST provide menu options to filter and view only upcoming tasks
- **FR-010**: System MUST maintain all existing basic and intermediate todo app features while adding new functionality
- **FR-011**: System MUST store all data in memory only, with no file or database persistence
- **FR-012**: System MUST parse natural language datetime expressions using dateutil or similar library

### Key Entities

- **Task**: Represents a user task with attributes including title, description, status (pending/completed), priority (high/medium/low), tags (list of strings), due_datetime (datetime with time information), recurrence (pattern string), and next_occurrence (datetime for calculation)
- **TaskList**: Collection of Task entities with methods for searching, filtering, sorting, and handling recurring tasks

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Users can create a recurring task with a specified pattern in under 60 seconds
- **SC-002**: When a recurring task is marked complete, the next occurrence is automatically created within 1 second
- **SC-003**: 95% of users can successfully create tasks with flexible datetime input on their first attempt
- **SC-004**: Overdue tasks are clearly visible and highlighted 100% of the time when present in the task list
- **SC-005**: The application remains responsive and displays task lists in under 2 seconds even with 50+ tasks
- **SC-006**: 90% of users can identify overdue and upcoming tasks correctly based on visual indicators
- **SC-007**: Natural language datetime parsing correctly interprets at least 90% of common expressions (tomorrow, next monday, in 2 hours, etc.)