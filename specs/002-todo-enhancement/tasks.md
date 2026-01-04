# Tasks: Todo CLI App Enhancement (Organization & Usability)

**Feature**: 002-todo-enhancement
**Date**: 2026-01-02
**Status**: Draft

## Implementation Strategy

This feature enhances the existing Todo CLI application with organization and usability features including priority levels, tags/categories, due dates, search functionality, filtering, and sorting. The implementation follows an incremental approach with each user story being independently testable.

## Dependencies

- User Story 1 (Enhanced Task Creation) must be completed before User Stories 2, 3, and 4 can be fully tested
- User Story 2 (Search and Filter) and User Story 3 (Sorting) can be developed in parallel after User Story 1
- User Story 4 (Enhanced Display) can be developed in parallel with other stories but requires all other features to be complete

## Parallel Execution Examples

- T006 [P] [US2] Implement search_tasks function in src/todo.py
- T007 [P] [US2] Implement filter_tasks function in src/todo.py
- T008 [P] [US3] Implement sort_tasks function in src/todo.py

## Phase 1: Setup

### Goal
Initialize project structure and dependencies for the enhanced todo application.

### Tasks

- [X] T001 Set up project structure with src/todo.py file
- [X] T002 Install required dependencies (dateutil, optional rich)
- [X] T003 Define Task dataclass with priority, tags, and due_date fields in src/todo.py
- [X] T004 Define TaskList class with enhanced functionality in src/todo.py

## Phase 2: Foundational

### Goal
Implement core data model and basic functionality that will be used by all user stories.

### Tasks

- [X] T005 Implement date parsing utility function for natural language dates in src/todo.py

## Phase 3: User Story 1 - Enhanced Task Creation (Priority: P1)

### Goal
As a user, I want to add tasks with priority levels, tags, and due dates so that I can better organize and prioritize my work.

### Independent Test Criteria
Can be fully tested by adding tasks with different priorities, tags, and due dates and verifying they are stored correctly in the system.

### Tasks

- [X] T006 [P] [US1] Implement add_task function with priority, tags, and due_date support in src/todo.py
- [X] T007 [P] [US1] Implement update_task function to modify priority, tags, and due_date in src/todo.py
- [X] T008 [P] [US1] Add input validation for priority values (high/medium/low) in src/todo.py
- [X] T009 [P] [US1] Add input validation for date format and natural language dates in src/todo.py
- [X] T010 [P] [US1] Add input validation for tags format (space or comma separated) in src/todo.py
- [X] T011 [US1] Test adding tasks with all new attributes in src/todo.py
- [X] T012 [US1] Test adding tasks with default priority when not specified in src/todo.py

## Phase 4: User Story 2 - Task Search and Filter (Priority: P1)

### Goal
As a user, I want to search and filter my tasks by keywords, status, priority, and tags so that I can quickly find and focus on relevant tasks.

### Independent Test Criteria
Can be fully tested by creating multiple tasks with different attributes and then searching/filtering to verify the correct subset of tasks is displayed.

### Tasks

- [X] T013 [P] [US2] Implement search_tasks function that searches title, description, and tags in src/todo.py
- [X] T014 [P] [US2] Implement filter_tasks function with status, priority, and tag filters in src/todo.py
- [X] T015 [P] [US2] Add case-insensitive search functionality in src/todo.py
- [X] T016 [US2] Test search functionality with various keywords in src/todo.py
- [X] T017 [US2] Test filter functionality with different criteria combinations in src/todo.py

## Phase 5: User Story 3 - Task Sorting (Priority: P2)

### Goal
As a user, I want to sort my tasks by priority, due date, or title so that I can view them in an order that makes sense for my workflow.

### Independent Test Criteria
Can be fully tested by creating tasks with different priorities and due dates, then applying different sorting options to verify the correct order.

### Tasks

- [X] T018 [P] [US3] Implement sort_tasks function with priority sorting in src/todo.py
- [X] T019 [P] [US3] Implement sort_tasks function with due date sorting in src/todo.py
- [X] T020 [P] [US3] Implement sort_tasks function with title sorting in src/todo.py
- [X] T021 [US3] Test sorting by priority (high → low) in src/todo.py
- [X] T022 [US3] Test sorting by due date (soonest first) in src/todo.py
- [X] T023 [US3] Test sorting by title (alphabetical) in src/todo.py

## Phase 6: User Story 4 - Enhanced Task Display (Priority: P2)

### Goal
As a user, I want to see priority indicators, tags, and due dates clearly displayed in the task list so that I can quickly assess task importance and deadlines.

### Independent Test Criteria
Can be fully tested by creating tasks with various attributes and verifying they are displayed with appropriate visual indicators in the list.

### Tasks

- [X] T024 [P] [US4] Implement enhanced display function with priority indicators in src/todo.py
- [X] T025 [P] [US4] Implement enhanced display function with tags display in src/todo.py
- [X] T026 [P] [US4] Implement enhanced display function with due date display in src/todo.py
- [X] T027 [P] [US4] Add rich table display support (optional) in src/todo.py
- [X] T028 [US4] Test enhanced display with various task attributes in src/todo.py
- [X] T029 [US4] Ensure display remains readable with 20-40 tasks in src/todo.py

## Phase 7: Menu & UX Enhancement

### Goal
Integrate new features into the existing menu-driven interface while maintaining all existing functionality.

### Tasks

- [X] T030 [P] Add new menu options for search, filter, and sort in src/todo.py
- [X] T031 [P] Update existing menu options to handle new task attributes in src/todo.py
- [X] T032 [P] Implement user input prompts for new features in src/todo.py
- [X] T033 [P] Ensure all Phase I features still work correctly in src/todo.py
- [X] T034 Test complete menu flow with all features in src/todo.py

## Phase 8: Polish & Cross-Cutting Concerns

### Goal
Final testing, documentation, and performance optimization.

### Tasks

- [X] T035 [P] Add error handling for invalid inputs in src/todo.py
- [X] T036 [P] Optimize search/filter/sort performance for up to 40 tasks in src/todo.py
- [X] T037 [P] Update README with new feature examples in README.md
- [X] T038 [P] Test complete user workflow: add with all fields → filter → sort → search in src/todo.py
- [X] T039 [P] Verify all acceptance scenarios from user stories work correctly in src/todo.py
- [X] T040 [P] Run PEP8 and type checking on final code in src/todo.py

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
  - User stories can then proceed in parallel (if staffed)
  - Or sequentially in priority order (P1 → P2 → P3)
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 3 (P2)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 4 (P2)**: Can start after Foundational (Phase 2) - No dependencies on other stories

### Within Each User Story

- Models before services
- Services before endpoints
- Core implementation before integration
- Story complete before moving to next priority

### Parallel Opportunities

- All Setup tasks marked [P] can run in parallel
- All Foundational tasks marked [P] can run in parallel (within Phase 2)
- Once Foundational phase completes, all user stories can start in parallel (if team capacity allows)
- Different user stories can be worked on in parallel by different team members

### Parallel Example: User Story 1

```bash
# Launch all components for User Story 1 together:
Task: "Implement add_task() function in src/todo.py"
Task: "Add input validation for priority values in src/todo.py"
```

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL - blocks all stories)
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Test User Story 1 independently
5. Deploy/demo if ready

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Test independently → Deploy/Demo (MVP!)
3. Add User Story 2 → Test independently → Deploy/Demo
4. Add User Story 3 → Test independently → Deploy/Demo
5. Add User Story 4 → Test independently → Deploy/Demo
6. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
   - Developer D: User Story 4
3. Stories complete and integrate independently

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Verify tests fail before implementing
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence