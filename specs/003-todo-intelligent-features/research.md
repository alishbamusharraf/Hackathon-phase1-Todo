# Research: Todo CLI App Enhancement (Intelligent Features)

**Feature**: 003-todo-intelligent-features
**Date**: 2026-01-03

## Overview

This document summarizes research conducted for implementing the Todo CLI app enhancement with intelligent features. The research addresses technical decisions around datetime handling, recurrence patterns, natural language parsing, and reminder systems.

## Decisions Made

### 1. Datetime Handling Strategy

**Decision**: Use Python's datetime module with timezone-naive datetimes for simplicity

**Rationale**: For a CLI application that runs locally, timezone-naive datetimes are sufficient and simpler to implement. The application will store all datetimes in the user's local timezone.

**Implementation**: Use datetime.datetime for due_datetime field with time information.

### 2. Recurrence Pattern Implementation

**Decision**: Implement recurrence using a string pattern format with helper functions

**Rationale**: The spec requires support for various recurrence patterns (daily, weekly, monthly, yearly) and custom intervals. A string-based pattern system provides flexibility while remaining simple to implement.

**Implementation**: Store recurrence as a string (e.g., "daily", "weekly", "every 3 days") and use helper functions to calculate the next occurrence based on the pattern.

### 3. Natural Language Date/Time Parsing

**Decision**: Use python-dateutil library for parsing flexible datetime inputs

**Rationale**: The spec requires accepting various datetime formats including natural language (tomorrow 3pm, next monday 9:00, in 2 hours). The dateutil library provides robust parsing capabilities for these formats.

**Alternatives considered**:
- Custom parser only: More complex to implement and maintain
- dateutil only: This is the best approach for handling natural language expressions

### 4. Recurring Task Logic

**Decision**: When a recurring task is marked complete, create a new task with updated due date

**Rationale**: This approach maintains the original task for history while creating a new instance for the next occurrence. It preserves task metadata while ensuring the recurrence pattern continues.

**Implementation**: When toggling a recurring task to complete, calculate the next due date based on the recurrence pattern and create a new task with the same attributes but updated due date.

### 5. Visual Indicators for Reminders

**Decision**: Use the optional 'rich' library for enhanced visual display of overdue and upcoming tasks

**Rationale**: The 'rich' library provides excellent formatting capabilities that will make overdue and upcoming tasks clearly visible through colors, bold text, and other visual enhancements. It's optional as per the spec and will improve user experience significantly.

**Alternatives considered**:
- Plain text formatting: Less readable for highlighting important status
- Custom formatting: More complex and error-prone
- Other libraries: 'rich' is the most popular and well-maintained option

### 6. Relative Time Display

**Decision**: Implement helper functions to display relative time strings (e.g., "in 2h", "tomorrow 9:00")

**Rationale**: The spec requires displaying due datetimes in both absolute and relative formats. Relative time displays are more user-friendly for understanding when tasks are due.

**Implementation**: Create helper functions that calculate the time difference between current time and due time, then format appropriately (e.g., "in 2 hours", "2 days ago", "tomorrow").

## Technical Unknowns Resolved

### 1. How to handle leap years and month-end dates in recurrence?

**Resolution**: For monthly recurrence, if the original date doesn't exist in the target month (e.g., Jan 31 to Feb), use the last day of the target month. For yearly recurrence, handle leap years by using the same logic.

### 2. How to handle tasks with very long recurrence intervals?

**Resolution**: Calculate the next occurrence based on the recurrence pattern, but add validation to ensure the resulting date is reasonable (e.g., not too far in the future).

### 3. How to handle multiple recurring tasks that become due at the same time?

**Resolution**: The system will handle this naturally as each task is processed independently. The display will show all tasks due at the same time.

## Dependencies

### Required
- Python 3.13+ (as per constitution)
- dateutil (for parsing natural language dates)
- rich (optional, for enhanced display)

### Optional
- The 'rich' library is optional and the application should work without it using plain text display.

## Implementation Approach

The implementation will follow the order specified in the user input:
1. Update Data Model
2. Natural Date/Time Input Parser
3. Recurring Task Logic
4. Enhance View List
5. In-App Awareness / Reminders
6. Menu & Flow Updates
7. Testing & Polish