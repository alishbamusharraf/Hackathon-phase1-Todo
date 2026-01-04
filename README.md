# Advanced Python Console Todo App 📝

![Python](https://img.shields.io/badge/Python-3.13+-blue)
![License: MIT](https://img.shields.io/badge/License-MIT-green)

A **powerful console-based todo application** built entirely in memory using Python. Designed for Hackathons, this app demonstrates advanced task management features including recurring tasks, flexible due dates, and visual indicators for overdue or upcoming tasks.

---

## 🚀 Key Features

- **Add tasks** with title, description, due date, and recurrence
- **View tasks** in a clean table with status, due date, and recurrence info
- **Update tasks** — edit title, description, due date, or recurrence
- **Delete tasks** safely by ID
- **Mark tasks complete/incomplete** with toggle functionality
- **Recurring tasks** automatically generate next occurrences
- **Flexible date/time input**:
  - `"tomorrow 3pm"`, `"next monday 9:00"`, `"in 2 hours"`
- **Overdue and upcoming task indicators**:
  - Overdue tasks in **bold red**
  - Upcoming tasks highlighted
- Dedicated views for **overdue** and **upcoming** tasks
- **Graceful error handling** for invalid input

---

## 🛠 Requirements

- Python **3.13+**
- Optional: **UV package manager** for easier dependency handling

---

## ⚡ Installation

1. Make sure Python 3.13+ is installed.
2. Optional: install UV package manager:
   ```bash
   pip install uv
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/todo-console-app.git
cd todo-console-app
Install dependencies:

bash
Copy code
# Using UV
uv sync

# Or standard pip
pip install -e .
🎯 Running the App
Start the console app by running:

bash
Copy code
python src/todo.py
📋 How to Use
After launching, you’ll see the main menu:

markdown
Copy code
Advanced Todo CLI App
1. Add new task
2. View all tasks
3. Update existing task
4. Delete task
5. Mark task as complete/incomplete
6. Show overdue tasks
7. Show upcoming tasks
0. Quit
Enter your choice:
1️⃣ Add a Task
Select option 1

Enter title (required) and description (optional)

Enter due date/time (optional)

Enter recurrence (optional, e.g., daily, weekly, every 3 days)

Task is saved with a unique ID

2️⃣ View Tasks
Option 2 displays all tasks in a table:

ID, Title, Description, Status, Due Date, Recurrence

Overdue tasks highlighted in red

Upcoming tasks highlighted

3️⃣ Update a Task
Option 3

Enter the task ID

Modify title, description, due date, or recurrence

Press Enter to skip any field

4️⃣ Delete a Task
Option 4

Enter the task ID and confirm deletion

5️⃣ Toggle Task Status
Option 5

Enter task ID

Status toggled between complete and incomplete

Recurring tasks automatically generate the next occurrence

6️⃣ View Overdue Tasks
Option 6 lists all overdue tasks with red/bold highlighting

7️⃣ View Upcoming Tasks
Option 7 lists tasks due within the next 24 hours with highlighted display

0️⃣ Quit
Option 0 exits the application

⚠️ Error Handling
Invalid menu choices display an error message and return to the menu

Invalid task IDs are rejected

Empty titles are not allowed

Invalid date/time formats or recurrence patterns are handled gracefully

🏗 Development Notes
Built using Spec-Driven Development methodology with AI assistance

Specifications and task plans are stored in specs/ for reference

Focused on clean, readable code and modular design

