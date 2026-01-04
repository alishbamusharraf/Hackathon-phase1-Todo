# Data Model: Todo In-Memory Python Console App

**Date**: 2026-01-02  
**Feature**: Todo In-Memory Python Console App  
**Branch**: 001-todo-app

## Overview

This document defines the data model for the Todo In-Memory Python Console App based on the entities identified in the feature specification. The data model represents the structure and relationships of data used by the application during runtime.

## Entities

### Task

**Definition**: Represents a single todo item in the application

**Attributes**:
- `id` (integer): Unique identifier for the task, auto-incremented starting from 1
- `title` (string): The title of the task (required, 1-255 characters)
- `description` (string): Detailed description of the task (required, 1-255 characters) 
- `completed` (boolean): Completion status of the task (true = complete, false = incomplete)

**Example**:
```python
{
    "id": 1,
    "title": "Buy groceries",
    "description": "Get milk, bread, and eggs from the store",
    "completed": False
}
```

**Validation Rules**:
- `id` must be a positive integer
- `title` must be a non-empty string with 1-255 characters
- `description` must be a non-empty string with 1-255 characters
- `completed` must be a boolean value

### TaskList

**Definition**: Collection of Task objects stored in memory

**Attributes**:
- `tasks` (list[dict]): A list containing Task objects

**Example**:
```python
[
    {
        "id": 1,
        "title": "Buy groceries",
        "description": "Get milk, bread, and eggs from the store",
        "completed": False
    },
    {
        "id": 2,
        "title": "Walk the dog",
        "description": "Take the dog for a 30-minute walk",
        "completed": True
    }
]
```

**Constraints**:
- Each task ID must be unique within the list
- IDs must be sequential starting from 1 (no gaps after deletion)

## State Transitions

### Task Completion State
- **Initial State**: `completed = False`
- **Transition**: User toggles completion status
- **Final State**: `completed = True` (or opposite of initial state)

## Relationships

- TaskList contains multiple Task entities
- Each Task entity is unique within the TaskList (no duplicates)
- Task IDs are unique within the TaskList

## Business Rules

1. **ID Uniqueness**: Each Task must have a unique ID within the TaskList
2. **Auto-incrementing IDs**: New tasks receive the next available ID in sequence
3. **Title and Description Required**: Both fields must be provided when creating a task
4. **Validation**: All input must be validated before creating or updating a Task
5. **Persistence**: All data exists only in memory during application runtime

## Schema Representation (Python)

```python
from typing import List, Dict, Union

Task = Dict[str, Union[int, str, bool]]
# {
#     "id": int,
#     "title": str,
#     "description": str,
#     "completed": bool
# }

TaskList = List[Task]
# [Task, Task, ...]
```

## Data Flow

1. **Task Creation**: User input → Validation → Task object creation → Addition to TaskList
2. **Task Retrieval**: TaskList → Filter by ID → Return specific Task
3. **Task Update**: User input → Validation → Task object modification
4. **Task Deletion**: TaskList → Remove by ID → Update remaining IDs to maintain sequence
5. **Task Toggle**: TaskList → Find by ID → Flip 'completed' boolean value

## Error Conditions

- Attempting to access a non-existent task ID
- Providing invalid data (e.g., empty title/description, invalid ID format)
- Attempting to create a duplicate ID