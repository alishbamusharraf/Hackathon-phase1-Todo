---

description: "Task list for Todo In-Memory Python Console App implementation"
---

# Tasks: Todo In-Memory Python Console App

**Input**: Design documents from `/specs/001-todo-app/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, contracts/

**Tests**: The examples below include test tasks. Tests are OPTIONAL - only include them if explicitly requested in the feature specification.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- **Single project**: `src/`, `tests/` at repository root
- **Web app**: `backend/src/`, `frontend/src/`
- **Mobile**: `api/src/`, `ios/src/` or `android/src/`
- Paths shown below assume single project - adjust based on plan.md structure

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [X] T001 Create project structure per implementation plan in src/, pyproject.toml, README.md
- [X] T002 Initialize Python project with minimal dependencies in pyproject.toml
- [X] T003 [P] Configure linting and formatting tools for Python 3.13+

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [X] T004 Create Task class/data model in src/todo.py with id, title, description, completed attributes
- [X] T005 [P] Implement TaskList collection structure in src/todo.py for in-memory storage
- [X] T006 [P] Setup main application loop with menu display in src/todo.py
- [X] T007 Create basic input validation functions in src/todo.py
- [X] T008 Configure error handling infrastructure with user-friendly messages in src/todo.py

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - Add New Task (Priority: P1) 🎯 MVP

**Goal**: Implement ability for users to add new tasks to their todo list with title and description, auto-generating incremental IDs starting from 1

**Independent Test**: A user can start the application, select the "Add task" option, enter a title and description, and see the task added to the list with a unique ID.

### Implementation for User Story 1

- [X] T009 [US1] Implement add_task() function in src/todo.py to create tasks with auto-incremented IDs
- [X] T010 [US1] Add input validation to ensure title and description meet requirements (1-255 chars)
- [X] T011 [US1] Add user interface for selecting add task option (option 1) in main menu
- [X] T012 [US1] Add confirmation message when task is successfully added
- [X] T013 [US1] Handle edge case when user enters invalid input for title or description

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - View All Tasks (Priority: P1)

**Goal**: Implement ability for users to view all their tasks in a clear, tabular format showing ID, completion status, title, and description

**Independent Test**: A user can start the application and view all tasks in a clear, tabular format showing ID, completion status, title, and description.

### Implementation for User Story 2

- [X] T014 [US2] Implement view_tasks() function in src/todo.py to display all tasks
- [X] T015 [US2] Format output in a clean, table-like structure with ID, status marker, title, description
- [X] T016 [US2] Add user interface for selecting view tasks option (option 2) in main menu
- [X] T017 [US2] Handle case when there are no tasks to display
- [X] T018 [US2] Implement status markers ([ ] for incomplete, [X] for complete)

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - Update Existing Task (Priority: P2)

**Goal**: Implement ability for users to update the title and/or description of existing tasks using the task ID

**Independent Test**: A user can select the "Update task" option, specify a task ID, and modify either the title, description, or both.

### Implementation for User Story 3

- [X] T019 [US3] Implement find_task_by_id() function in src/todo.py to retrieve specific tasks
- [X] T020 [US3] Implement update_task() function in src/todo.py to modify title and/or description
- [X] T021 [US3] Add user interface for selecting update task option (option 3) in main menu
- [X] T022 [US3] Handle case when user tries to update a non-existent task ID
- [X] T023 [US3] Allow partial updates (change only title, only description, or both)

**Checkpoint**: At this point, User Stories 1, 2 AND 3 should all work independently

---

## Phase 6: User Story 4 - Delete Task (Priority: P2)

**Goal**: Implement ability for users to delete tasks by ID, removing them from the list

**Independent Test**: A user can select the "Delete task" option, specify a valid task ID, and have that task removed from the list.

### Implementation for User Story 4

- [X] T024 [US4] Implement delete_task() function in src/todo.py to remove tasks by ID
- [X] T025 [US4] Add user interface for selecting delete task option (option 4) in main menu
- [X] T026 [US4] Handle case when user tries to delete a non-existent task ID
- [X] T027 [US4] Implement confirmation or feedback when task is successfully deleted

**Checkpoint**: At this point, User Stories 1, 2, 3 AND 4 should all work independently

---

## Phase 7: User Story 5 - Toggle Completion Status (Priority: P2)

**Goal**: Implement ability for users to mark tasks as complete or incomplete by flipping the completion status using the task ID

**Independent Test**: A user can select the "Toggle completion status" option, specify a task ID, and have the completion status flipped.

### Implementation for User Story 5

- [X] T028 [US5] Implement toggle_task_status() function in src/todo.py to flip completion status
- [X] T029 [US5] Add user interface for selecting toggle status option (option 5) in main menu
- [X] T030 [US5] Handle case when user tries to toggle status of a non-existent task ID
- [X] T031 [US5] Provide feedback when task status has been successfully toggled

**Checkpoint**: At this point, all 5 user stories should be independently functional

---

## Phase 8: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [X] T032 [P] Complete main menu implementation with all 6 options (1-5 + 0 to quit) in src/todo.py
- [X] T033 [P] Implement persistent menu loop until explicit quit in src/todo.py
- [X] T034 [P] Implement graceful handling of ALL invalid inputs in src/todo.py
- [X] T035 [P] Add clear feedback after every operation in src/todo.py
- [X] T036 [P] Add quit functionality (option 0) in src/todo.py
- [X] T037 [P] Documentation updates in README.md with setup and demo commands
- [X] T038 Code cleanup and refactoring to ensure functions ≤ 25 lines
- [X] T039 Add type hints to all functions in src/todo.py
- [X] T040 Ensure PEP 8 compliance across all code
- [X] T041 Run quickstart validation to ensure complete workflow works

---

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
- **User Story 5 (P2)**: Can start after Foundational (Phase 2) - No dependencies on other stories

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

---

## Parallel Example: User Story 1

```bash
# Launch all components for User Story 1 together:
Task: "Implement add_task() function in src/todo.py"
Task: "Add input validation to ensure title and description meet requirements in src/todo.py"
```

---

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
6. Add User Story 5 → Test independently → Deploy/Demo
7. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
   - Developer D: User Story 4
   - Developer E: User Story 5
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Verify tests fail before implementing
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence