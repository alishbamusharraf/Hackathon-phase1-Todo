# API Contracts: Todo CLI App Enhancement (Intelligent Features)

**Feature**: 003-todo-intelligent-features
**Date**: 2026-01-03

## Overview

This document defines the function interfaces for the enhanced Todo CLI application with intelligent features. Since this is a command-line interface application rather than a web API, the contracts describe the function signatures and expected behavior for the core operations.

## Core Interfaces

### Task Management Functions

#### `add_task(title: str, description: str = "", priority: str = "medium", tags: List[str] = None, due_datetime: str = None, recurrence: str = None) -> int`

**Purpose**: Add a new task to the task list

**Parameters**:
- `title`: The main task description (required, non-empty)
- `description`: Additional details about the task (optional)
- `priority`: Priority level ("high", "medium", "low", default "medium")
- `tags`: Space or comma-separated tags as a string (optional)
- `due_datetime`: Due date and time in various formats (optional)
- `recurrence`: Recurrence pattern (e.g. "daily", "weekly", "every 3 days", optional)

**Returns**: The ID of the newly created task

**Errors**:
- `ValueError`: If title is empty or priority is invalid

---

#### `update_task(task_id: int, title: str = None, description: str = None, status: str = None, priority: str = None, tags: List[str] = None, due_datetime: str = None, recurrence: str = None) -> bool`

**Purpose**: Update an existing task's attributes

**Parameters**:
- `task_id`: The ID of the task to update (required)
- `title`: New title for the task (optional)
- `description`: New description for the task (optional)
- `status`: New status ("pending", "completed", optional)
- `priority`: New priority level (optional)
- `tags`: New list of tags (optional)
- `due_datetime`: New due date and time (optional)
- `recurrence`: New recurrence pattern (optional)

**Returns**: True if the task was updated, False if the task was not found

---

#### `delete_task(task_id: int) -> bool`

**Purpose**: Remove a task from the task list

**Parameters**:
- `task_id`: The ID of the task to delete (required)

**Returns**: True if the task was deleted, False if the task was not found

---

#### `get_task(task_id: int) -> Optional[Task]`

**Purpose**: Retrieve a specific task by ID

**Parameters**:
- `task_id`: The ID of the task to retrieve (required)

**Returns**: The Task object if found, None otherwise

---

#### `get_all_tasks() -> List[Task]`

**Purpose**: Retrieve all tasks in the task list

**Returns**: List of all Task objects in the current order

---

### Date/Time and Recurrence Functions

#### `parse_datetime(datetime_str: str) -> Optional[datetime]`

**Purpose**: Parse a datetime string which can be in various formats including natural language

**Parameters**:
- `datetime_str`: Date and time string in various formats (YYYY-MM-DD HH:MM, natural language, etc.)

**Returns**: Parsed datetime object or None if invalid

---

#### `calculate_next_occurrence(current_datetime: datetime, recurrence_pattern: str) -> Optional[datetime]`

**Purpose**: Calculate the next occurrence datetime based on the recurrence pattern

**Parameters**:
- `current_datetime`: The current due datetime
- `recurrence_pattern`: The recurrence pattern (e.g. "daily", "weekly", "every 3 days")

**Returns**: The next occurrence datetime or None if pattern is invalid

---

### Search and Filter Functions

#### `search_tasks(keyword: str) -> List[Task]`

**Purpose**: Find tasks that match a keyword in title, description, or tags

**Parameters**:
- `keyword`: The search term to look for (case-insensitive)

**Returns**: List of Task objects that match the keyword

---

#### `filter_tasks(status: str = None, priority: str = None, tag: str = None) -> List[Task]`

**Purpose**: Filter tasks based on specified criteria

**Parameters**:
- `status`: Filter by status ("pending", "completed", "all", default None for all)
- `priority`: Filter by priority ("high", "medium", "low", "all", default None for all)
- `tag`: Filter by a specific tag (default None for all)

**Returns**: List of Task objects that match all specified criteria

---

### Specialized Functions for Intelligent Features

#### `get_overdue_tasks() -> List[Task]`

**Purpose**: Get tasks that are overdue (due date is in the past and status is pending)

**Returns**: List of overdue Task objects

---

#### `get_upcoming_tasks(hours: int = 24) -> List[Task]`

**Purpose**: Get tasks that are due within the specified number of hours

**Parameters**:
- `hours`: Number of hours to look ahead (default 24)

**Returns**: List of upcoming Task objects

---

#### `handle_recurring_task_completion(task_id: int) -> bool`

**Purpose**: Handle the completion of a recurring task by creating the next occurrence

**Parameters**:
- `task_id`: The ID of the recurring task being completed

**Returns**: True if the next occurrence was created successfully, False otherwise

---

### Display Functions

#### `display_tasks(tasks: List[Task], format_type: str = "table") -> str`

**Purpose**: Format tasks for display with enhanced information for intelligent features

**Parameters**:
- `tasks`: List of Task objects to display
- `format_type`: Output format ("table", "list", default "table")

**Returns**: Formatted string representation of the tasks with due datetime and recurrence indicators

---

## CLI Command Interface

### Main Menu Options

The application provides a menu-driven interface with the following options:

1. **Add Task**: Prompts for title, description, priority, tags, due date/time, and recurrence
2. **View All Tasks**: Displays all tasks with enhanced attributes (due datetime, recurrence)
3. **Update Task**: Prompts for task ID and new attributes
4. **Delete Task**: Prompts for task ID to delete
5. **Toggle Complete**: Prompts for task ID to toggle status
6. **Search Tasks**: Prompts for keyword to search
7. **Filter Tasks**: Prompts for filter criteria
8. **Sort Tasks**: Prompts for sorting method
9. **Show Overdue**: Displays only overdue tasks
10. **Show Upcoming**: Displays only upcoming tasks (due in next 24 hours)
0. **Quit**: Exits the application

### Input Validation

All functions should validate input according to the following rules:

- Task titles must not be empty or only whitespace
- Priority values must be "high", "medium", or "low"
- Status values must be "pending" or "completed"
- Datetime values must be in valid format (various formats accepted)
- Recurrence patterns must be valid ("daily", "weekly", "monthly", "yearly", "every X days", etc.)
- Task IDs must exist in the current task list