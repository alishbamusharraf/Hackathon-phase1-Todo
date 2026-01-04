# API Contracts: Todo In-Memory Python Console App

**Date**: 2026-01-02  
**Feature**: Todo In-Memory Python Console App  
**Branch**: 001-todo-app

## Overview

This document defines the API contracts for the user interactions with the Todo In-Memory Python Console App. These contracts specify how users interact with the application through its menu-driven interface.

## User Actions & Contracts

### 1. Add New Task
- **Action**: User selects option 1 from the main menu
- **Input**: Title (string, 1-255 chars), Description (string, 1-255 chars)
- **Processing**: 
  - Validates input
  - Creates new task with next available ID
  - Adds task to TaskList
- **Output**: Confirmation message with task ID
- **Success Response**: "Task added successfully with ID: {id}"
- **Error Responses**: 
  - "Error: Title and description are required"
  - "Error: Title/description too long (max 255 chars)"

### 2. View All Tasks
- **Action**: User selects option 2 from the main menu
- **Input**: None required
- **Processing**: 
  - Retrieves all tasks from TaskList
  - Formats tasks for display in table format
- **Output**: Formatted table of all tasks with ID, status marker, title, and description
- **Success Response**:
  ```
  ID  Status  Title           Description
  --  ------  -----           -----------
  1   [ ]     Buy groceries   Get milk, bread, and eggs
  2   [X]     Walk the dog    Take the dog for a walk
  ```
- **Error Responses**: "No tasks available"

### 3. Update Existing Task
- **Action**: User selects option 3 from the main menu
- **Input**: Task ID (integer), New title (string, optional), New description (string, optional)
- **Processing**: 
  - Validates task ID exists
  - Updates title and/or description based on user input
- **Output**: Confirmation message
- **Success Response**: "Task {id} updated successfully"
- **Error Responses**: 
  - "Error: Task with ID {id} not found"
  - "Error: No valid updates provided"

### 4. Delete Task
- **Action**: User selects option 4 from the main menu
- **Input**: Task ID (integer)
- **Processing**: 
  - Validates task ID exists
  - Removes task from TaskList
- **Output**: Confirmation message
- **Success Response**: "Task {id} deleted successfully"
- **Error Responses**: "Error: Task with ID {id} not found"

### 5. Toggle Completion Status
- **Action**: User selects option 5 from the main menu
- **Input**: Task ID (integer)
- **Processing**: 
  - Validates task ID exists
  - Flips the completion status of the task
- **Output**: Confirmation message
- **Success Response**: "Task {id} completion status toggled"
- **Error Responses**: "Error: Task with ID {id} not found"

### 6. Quit Application
- **Action**: User selects option 0 from the main menu
- **Input**: None required
- **Processing**: Exits the application gracefully
- **Output**: None
- **Success Response**: Application terminates

## Error Handling Contracts

### General Error Handling
- All invalid inputs must be handled gracefully
- Applications must not crash on any user input
- Error messages must be clear and informative
- Main menu must be restored after any error

### Input Validation Contracts
- All numeric inputs must be validated as integers
- Task IDs must exist in the current TaskList
- Text inputs must be 1-255 characters if provided
- Empty required fields must generate appropriate errors

## User Experience Contracts

### Menu Display
- Main menu must be displayed clearly with numbered options
- Menu must repeat after each operation until user chooses to quit
- All user actions must result in clear feedback

### Feedback Requirements
- All successful operations must provide confirmation
- All failed operations must provide clear error messages
- Task display must use consistent formatting
- Status markers must be [ ] for incomplete and [X] for complete