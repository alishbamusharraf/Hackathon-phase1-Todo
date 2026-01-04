# Data Model: Todo CLI App Enhancement (Organization & Usability)

**Feature**: 002-todo-enhancement
**Date**: 2026-01-02

## Overview

This document defines the data model for the enhanced Todo CLI application, which extends the basic todo functionality with priority levels, tags, due dates, and enhanced search/filter/sort capabilities.

## Entity Definitions

### Task

The Task entity represents a single todo item with enhanced attributes.

```python
from dataclasses import dataclass
from datetime import date
from typing import List, Optional

@dataclass
class Task:
    id: int
    title: str
    description: str = ""
    status: str = "pending"  # "pending" or "completed"
    priority: str = "medium"  # "high", "medium", or "low"
    tags: List[str] = None   # List of tags associated with the task
    due_date: Optional[date] = None  # Due date, None if not set
    
    def __post_init__(self):
        if self.tags is None:
            self.tags = []
```

#### Fields

- **id**: Unique identifier for the task (integer)
- **title**: The main task description (string, required)
- **description**: Additional details about the task (string, optional)
- **status**: Current status of the task ("pending" or "completed")
- **priority**: Priority level of the task ("high", "medium", or "low", default "medium")
- **tags**: List of tags associated with the task (list of strings, can be empty)
- **due_date**: Due date for the task (date object, optional)

#### Validation Rules

- `id` must be a positive integer
- `title` must not be empty or only whitespace
- `status` must be either "pending" or "completed"
- `priority` must be one of "high", "medium", or "low"
- `tags` must be a list of non-empty strings with no duplicates
- `due_date` must be a valid date in the future or None

#### State Transitions

- A task can transition from "pending" to "completed" when marked as done
- A task can transition from "completed" to "pending" when unmarked
- All other attributes remain unchanged during status transitions

### TaskList

The TaskList entity represents a collection of Task objects with enhanced functionality.

```python
from typing import List, Optional
from datetime import date

class TaskList:
    def __init__(self):
        self.tasks: List[Task] = []
        self.next_id: int = 1
    
    def add_task(self, title: str, description: str = "", priority: str = "medium", 
                 tags: List[str] = None, due_date: Optional[date] = None) -> Task:
        """Add a new task with the specified attributes"""
        pass
    
    def update_task(self, task_id: int, title: str = None, description: str = None,
                    status: str = None, priority: str = None, 
                    tags: List[str] = None, due_date: Optional[date] = None) -> Optional[Task]:
        """Update an existing task with the specified attributes"""
        pass
    
    def delete_task(self, task_id: int) -> bool:
        """Delete a task by ID"""
        pass
    
    def search_tasks(self, keyword: str) -> List[Task]:
        """Search tasks by keyword in title, description, or tags"""
        pass
    
    def filter_tasks(self, status: str = None, priority: str = None, tag: str = None) -> List[Task]:
        """Filter tasks by status, priority, or tag"""
        pass
    
    def sort_tasks(self, sort_by: str) -> List[Task]:
        """Sort tasks by priority, due date, or title"""
        pass
```

#### Methods

- `add_task`: Creates a new task with the provided attributes
- `update_task`: Updates an existing task's attributes
- `delete_task`: Removes a task from the list
- `search_tasks`: Returns tasks matching a keyword in title, description, or tags
- `filter_tasks`: Returns tasks matching specified filter criteria
- `sort_tasks`: Returns tasks sorted by the specified criteria

## Relationships

- A TaskList contains multiple Task entities
- Each Task belongs to exactly one TaskList

## Data Flow

1. **Task Creation**: User provides title, description, priority, tags, and due date → Task object created with unique ID
2. **Task Storage**: Task objects stored in TaskList's internal list
3. **Task Retrieval**: TaskList provides methods to search, filter, and sort tasks
4. **Task Update**: User modifies task attributes → Task object updated in place
5. **Task Deletion**: User requests deletion → Task object removed from TaskList

## Constraints

- All data remains in memory only (no persistence)
- Task IDs are unique within a TaskList
- TaskList maintains order of creation by default
- Priority values are restricted to "high", "medium", "low"
- Status values are restricted to "pending", "completed"