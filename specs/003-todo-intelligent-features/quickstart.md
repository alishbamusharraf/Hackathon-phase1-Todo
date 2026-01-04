# Quickstart Guide: Todo CLI App Enhancement (Intelligent Features)

**Feature**: 003-todo-intelligent-features
**Date**: 2026-01-03

## Overview

This guide provides quick instructions for setting up, running, and using the enhanced Todo CLI application with intelligent features. The application provides a simple command-line interface for managing todo tasks with recurring tasks, full datetime support, and in-app reminder system.

## Prerequisites

- Python 3.13 or higher
- Basic command-line interface knowledge
- Optional: `dateutil` library for natural language date parsing
- Optional: `rich` library for enhanced display

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

3. **Install optional dependencies** (recommended):
   ```bash
   pip install python-dateutil
   pip install rich
   ```

4. **Navigate to project directory**:
   ```bash
   cd path/to/todo-hackathon
   ```

5. **Run the application**:
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
TODO APPLICATION (Enhanced with Intelligent Features)
====================================================
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
6. Search tasks
7. Filter tasks
8. Sort tasks
9. Show overdue tasks
10. Show upcoming tasks
0. Quit
Choose an option:
```

## Basic Usage

### Adding a Task with DateTime and Recurrence
1. Select option `1`
2. Enter the task title when prompted
3. Enter the task description when prompted (optional)
4. Enter the priority level (high/medium/low) (optional, defaults to medium)
5. Enter tags (space or comma separated) (optional)
6. Enter due date and time (e.g., "tomorrow 3pm", "2026-01-15 14:30", "in 2 hours") (optional)
7. Enter recurrence pattern (e.g., "daily", "weekly", "monthly", "every 3 days") (optional)
8. The system will confirm the task was added with its ID

### Viewing Tasks with Enhanced Information
1. Select option `2`
2. All tasks will be displayed in a table format with:
   - ID
   - Status
   - Priority
   - Title
   - Due date/time (relative and absolute)
   - Recurrence pattern (if applicable)

### Updating a Task
1. Select option `3`
2. Enter the task ID you want to update
3. Enter new values for any attributes (or press Enter to keep current values)
4. The system will confirm the update

### Deleting a Task
1. Select option `4`
2. Enter the task ID you want to delete
3. The system will confirm the deletion

### Toggling Task Status (with Recurring Task Handling)
1. Select option `5`
2. Enter the task ID you want to toggle
3. If it's a recurring task, the system will mark the current one as complete and create a new occurrence
4. The system will confirm the status change

### Showing Overdue Tasks
1. Select option `9`
2. Only tasks with past due dates and pending status will be displayed

### Showing Upcoming Tasks
1. Select option `10`
2. Only tasks due in the next 24 hours will be displayed

### Exiting the Application
1. Select option `0`
2. The application will terminate

## Example Workflow

Here's a complete example workflow with intelligent features:

```
TODO APPLICATION (Enhanced with Intelligent Features)
====================================================
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
6. Search tasks
7. Filter tasks
8. Sort tasks
9. Show overdue tasks
10. Show upcoming tasks
0. Quit
Choose an option: 1
Enter task title: Weekly grocery shopping
Enter task description: Buy groceries for the week
Enter priority (high/medium/low, default: medium): medium
Enter tags (comma or space separated, optional): shopping weekly
Enter due date (YYYY-MM-DD HH:MM, natural language, optional): next saturday 10am
Enter recurrence pattern (optional): weekly
Task added successfully with ID: 1

TODO APPLICATION (Enhanced with Intelligent Features)
====================================================
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
6. Search tasks
7. Filter tasks
8. Sort tasks
9. Show overdue tasks
10. Show upcoming tasks
0. Quit
Choose an option: 2
ID  Status  Priority  Title                  Due Date        Recurrence
--  ------  --------  -----                  --------        ----------
1   [ ]     medium    Weekly grocery shop... next Sat 10:00  ↻ weekly

TODO APPLICATION (Enhanced with Intelligent Features)
====================================================
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
6. Search tasks
7. Filter tasks
8. Sort tasks
9. Show overdue tasks
10. Show upcoming tasks
0. Quit
Choose an option: 5
Enter task ID to toggle: 1
Task 1 completion status toggled - next occurrence created with ID: 2

TODO APPLICATION (Enhanced with Intelligent Features)
====================================================
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
6. Search tasks
7. Filter tasks
8. Sort tasks
9. Show overdue tasks
10. Show upcoming tasks
0. Quit
Choose an option: 2
ID  Status  Priority  Title                  Due Date        Recurrence
--  ------  --------  -----                  --------        ----------
1   [X]     medium    Weekly grocery shop... (completed)    ↻ weekly
2   [ ]     medium    Weekly grocery shop... next Sat 10:00  ↻ weekly

TODO APPLICATION (Enhanced with Intelligent Features)
====================================================
1. Add task
2. View all tasks
3. Update task
4. Delete task
5. Toggle complete/incomplete
6. Search tasks
7. Filter tasks
8. Sort tasks
9. Show overdue tasks
10. Show upcoming tasks
0. Quit
Choose an option: 0
```

## Troubleshooting

### Common Issues

1. **Python version error**: Ensure you're using Python 3.13 or higher
2. **Module not found**: Install optional dependencies (`dateutil`, `rich`)
3. **File not found**: Verify that todo.py exists in the src/ directory
4. **Invalid date format**: Use supported formats like "tomorrow 3pm", "2026-01-15 14:30", or "in 2 hours"

### Error Messages
- "Error: Task with ID {id} not found" - Check that the task ID exists
- "Error: Title and description are required" - Task title cannot be empty
- "Error: Invalid date format" - Enter a valid date/time format
- "Error: Invalid recurrence pattern" - Use valid patterns like "daily", "weekly", "monthly", "every X days"

## Next Steps

After completing the setup, try the following:

1. Add a recurring task to familiarize yourself with the recurrence feature
2. Practice setting due dates with time components
3. Use the overdue and upcoming task views to experience the reminder system
4. Test error handling by entering invalid options to ensure graceful error messages