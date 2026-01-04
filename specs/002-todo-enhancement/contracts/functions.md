# API Contracts: Todo CLI App Enhancement (Organization & Usability)

**Feature**: 002-todo-enhancement
**Date**: 2026-01-02

## Overview

This document defines the function interfaces for the enhanced Todo CLI application. Since this is a command-line interface application rather than a web API, the contracts describe the function signatures and expected behavior for the core operations.

## Core Interfaces

### Task Management Functions

#### `add_task(title: str, description: str = "", priority: str = "medium", tags: List[str] = None, due_date: str = None) -> int`

**Purpose**: Add a new task to the task list

**Parameters**:
- `title`: The main task description (required, non-empty)
- `description`: Additional details about the task (optional)
- `priority`: Priority level ("high", "medium", "low", default "medium")
- `tags`: Space or comma-separated tags as a string (optional)
- `due_date`: Due date in YYYY-MM-DD format or natural language (optional)

**Returns**: The ID of the newly created task

**Errors**:
- `ValueError`: If title is empty or priority is invalid

---

#### `update_task(task_id: int, title: str = None, description: str = None, status: str = None, priority: str = None, tags: List[str] = None, due_date: str = None) -> bool`

**Purpose**: Update an existing task's attributes

**Parameters**:
- `task_id`: The ID of the task to update (required)
- `title`: New title for the task (optional)
- `description`: New description for the task (optional)
- `status`: New status ("pending", "completed", optional)
- `priority`: New priority level (optional)
- `tags`: New list of tags (optional)
- `due_date`: New due date in YYYY-MM-DD format or natural language (optional)

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

### Sort Functions

#### `sort_tasks(sort_by: str) -> List[Task]`

**Purpose**: Sort tasks based on specified criteria

**Parameters**:
- `sort_by`: Sorting method ("priority", "due_date", "title", "creation", default "creation")

**Returns**: List of Task objects sorted according to the specified method

---

### Display Functions

#### `display_tasks(tasks: List[Task], format_type: str = "table") -> str`

**Purpose**: Format tasks for display

**Parameters**:
- `tasks`: List of Task objects to display
- `format_type`: Output format ("table", "list", default "table")

**Returns**: Formatted string representation of the tasks

---

## CLI Command Interface

### Main Menu Options

The application provides a menu-driven interface with the following options:

1. **Add Task**: Prompts for title, description, priority, tags, and due date
2. **View All Tasks**: Displays all tasks with enhanced attributes
3. **Update Task**: Prompts for task ID and new attributes
4. **Delete Task**: Prompts for task ID to delete
5. **Toggle Complete**: Prompts for task ID to toggle status
6. **Search Tasks**: Prompts for keyword to search
7. **Filter Tasks**: Prompts for filter criteria
8. **Sort Tasks**: Prompts for sorting method
0. **Quit**: Exits the application

### Input Validation

All functions should validate input according to the following rules:

- Task titles must not be empty or only whitespace
- Priority values must be "high", "medium", or "low"
- Status values must be "pending" or "completed"
- Dates must be in valid format (YYYY-MM-DD or natural language)
- Task IDs must exist in the current task list