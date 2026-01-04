# Quickstart Guide: Todo In-Memory Python Console App

**Date**: 2026-01-02  
**Feature**: Todo In-Memory Python Console App  
**Branch**: 001-todo-app

## Overview

This guide provides quick instructions for setting up, running, and using the Todo In-Memory Python Console App. The application provides a simple command-line interface for managing todo tasks in memory.

## Prerequisites

- Python 3.13 or higher
- Basic command-line interface knowledge

## Setup Instructions

1. **Clone the repository** (if applicable):
   ```bash
   # For this hackathon project, the files are already available
   ```

2. **Verify Python version**:
   ```bash
   python --version
   # or
   python3 --version
   ```
   Ensure you have Python 3.13 or higher.

3. **Navigate to project directory**:
   ```bash
   cd path/to/todo-hackathon
   ```

4. **Run the application**:
   ```bash
   python src/todo.py
   # or
   python3 src/todo.py
   ```

## Running the Application

The application runs in a continuous loop until the user chooses to exit:

```bash
python src/todo.py
```

The main menu will appear with the following options:
```
TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option:
```

## Basic Usage

### Adding a Task
1. Select option `1`
2. Enter the task title when prompted
3. Enter the task description when prompted
4. The system will confirm the task was added with its ID

### Viewing Tasks
1. Select option `2`
2. All tasks will be displayed in a table format with ID, status, title, and description

### Updating a Task
1. Select option `3`
2. Enter the task ID you want to update
3. Enter the new title (or press Enter to keep the current title)
4. Enter the new description (or press Enter to keep the current description)

### Deleting a Task
1. Select option `4`
2. Enter the task ID you want to delete
3. The system will confirm the deletion

### Toggling Task Status
1. Select option `5`
2. Enter the task ID you want to toggle
3. The system will update the completion status

### Exiting the Application
1. Select option `0`
2. The application will terminate

## Example Workflow

Here's a complete example workflow:

```
TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option: 1
Enter task title: Buy groceries
Enter task description: Get milk, bread, and eggs
Task added successfully with ID: 1

TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option: 1
Enter task title: Walk the dog
Enter task description: Take the dog for a 30-minute walk
Task added successfully with ID: 2

TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option: 2
ID  Status  Title           Description
--  ------  -----           -----------
1   [ ]     Buy groceries   Get milk, bread, and eggs
2   [ ]     Walk the dog    Take the dog for a 30-minute walk

TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option: 5
Enter task ID to toggle: 2
Task 2 completion status toggled

TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option: 2
ID  Status  Title           Description
--  ------  -----           -----------
1   [ ]     Buy groceries   Get milk, bread, and eggs
2   [X]     Walk the dog    Take the dog for a 30-minute walk

TODO APPLICATION
===============
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
0. Quit
Choose an option: 0
```

## Troubleshooting

### Common Issues

1. **Python version error**: Ensure you're using Python 3.13 or higher
2. **Module not found**: Make sure you're running the command from the project root
3. **File not found**: Verify that todo.py exists in the src/ directory

### Error Messages
- "Error: Task with ID {id} not found" - Check that the task ID exists
- "Error: Title and description are required" - Task title and description cannot be empty
- "Error: Invalid input" - Enter a valid number from the menu options

## Next Steps

After completing the setup, try the following:

1. Add several tasks to familiarize yourself with the add functionality
2. Practice updating and deleting tasks
3. Use the toggle function to change completion status
4. Test error handling by entering invalid options to ensure graceful error messages