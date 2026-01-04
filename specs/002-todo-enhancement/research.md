# Research Summary: Todo CLI App Enhancement (Organization & Usability)

**Feature**: 002-todo-enhancement
**Date**: 2026-01-02

## Overview

This document summarizes research conducted for implementing the Todo CLI app enhancement with organization and usability features. The research addresses technical decisions around data modeling, date parsing, search algorithms, and UI enhancements.

## Decisions Made

### 1. Data Model Enhancement

**Decision**: Extend the existing Task dataclass with new fields for priority, tags, and due date

**Rationale**: The existing Task structure needs to be enhanced with:
- priority: str (with values "high", "medium", "low", defaulting to "medium")
- tags: list[str] (to support multiple tags per task)
- due_date: Optional[date] (to store due dates, with None for no due date)

**Implementation**: Using Python dataclass with type hints for better code clarity and IDE support.

### 2. Date Parsing Strategy

**Decision**: Use a combination of dateutil.parse and custom parsing for natural language dates

**Rationale**: The spec requires accepting both standard formats (YYYY-MM-DD) and natural language (tomorrow, next friday, in 3 days). The `dateutil` library provides robust parsing capabilities for various date formats and can handle relative dates.

**Alternatives considered**:
- Only standard formats: Less user-friendly
- Custom parser only: More complex to implement and maintain
- dateutil only: May not handle all natural language expressions

### 3. Search Implementation

**Decision**: Implement a simple substring matching algorithm with case-insensitive search

**Rationale**: For the scope of this application, a simple substring search across title, description, and tags will be sufficient. This approach is efficient for up to 40 tasks and meets the performance requirements.

**Implementation**: Convert all searchable text to lowercase and check for substring matches.

### 4. Filtering Strategy

**Decision**: Implement filtering using Python's built-in filter() function with lambda expressions

**Rationale**: This approach is clean, readable, and efficient for the expected number of tasks (up to 40). It allows for combining multiple filter criteria easily.

**Implementation**: Chain multiple filters or use a single filter with combined conditions.

### 5. Sorting Implementation

**Decision**: Use Python's built-in sorted() function with custom key functions

**Rationale**: Python's sorting algorithm is highly optimized (Timsort) and will handle the expected number of tasks efficiently. Custom key functions can handle the different sorting requirements (priority, due date, title).

**Implementation**: Create different key functions for each sorting option.

### 6. Display Enhancement

**Decision**: Use the optional 'rich' library for better table display, with fallback to plain text

**Rationale**: The 'rich' library provides excellent table formatting capabilities that will make the enhanced task attributes (priority, tags, due date) clearly visible. It's optional as per the spec and will improve user experience significantly.

**Alternatives considered**:
- Plain text formatting: Less readable with multiple attributes
- Custom table implementation: More complex and error-prone
- Other libraries: 'rich' is the most popular and well-maintained option

### 7. Menu Enhancement

**Decision**: Extend the existing menu-driven interface with new options for search, filter, and sort

**Rationale**: The existing menu structure should be preserved to maintain compatibility with existing features while adding new functionality.

**Implementation**: Add new menu options (e.g., 6. Search tasks, 7. Filter tasks, 8. Sort tasks) while keeping the original 5 features intact.

## Technical Unknowns Resolved

### 1. How to handle invalid date inputs?

**Resolution**: Implement input validation with clear error messages. Use try-catch blocks around date parsing and provide helpful feedback to users when they enter invalid dates.

### 2. How to handle tasks with many tags that exceed display width?

**Resolution**: Implement tag abbreviation or truncation in the display function. Show a limited number of tags (e.g., first 3) with an indicator if there are more.

### 3. How to handle empty search queries?

**Resolution**: Treat empty search queries as showing all tasks, with an appropriate message to the user.

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
2. Modify Add & Update Flow
3. Enhance View List
4. Implement Search
5. Implement Filter
6. Implement Sort
7. Menu & UX Polish
8. Final Testing & Docs