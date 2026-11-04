# Week 1 – Code Smells in the Todo App

## 1. God Object – TodoManager

**Where:** `src/todo.js`, lines 2–121 (class `TodoManager`).

**Smell:** God Object. The `TodoManager` class handles multiple responsibilities, including task management, input validation, localStorage persistence, HTML rendering, and DOM event handling. Instead of focusing on one main responsibility, it manages almost the entire application.

**Cost:** This creates tight coupling and makes the class difficult to maintain. For example, changing the way tasks are stored could require modifying the same class responsible for rendering and validating tasks. This increases the risk of introducing bugs when making changes.

**Not yet fixing:** noted for Week 3.

## 2. Duplicated Code – renderPendingRows() and renderCompletedRows()

**Where:** `src/todo.js`, lines 62–79 (methods `renderPendingRows()` and `renderCompletedRows()`).

**Smell:** Duplicated Code. Both methods loop through the task collection, filter tasks based on their completion status, generate HTML using `buildTaskRow()`, and return the resulting HTML. The main difference is the condition used to determine whether a task should be included.

**Cost:** If the task-row generation logic needs to change, both methods must be updated. Forgetting to update one could cause inconsistent behavior between the pending and completed task sections.

**Not yet fixing:** noted for Week 3.

## 3. Long Parameter List – buildTaskRow()

**Where:** `src/todo.js`, line 124 (function `buildTaskRow()`).

**Smell:** Long Parameter List. The function accepts six parameters: `id`, `desc`, `completed`, `priority`, `createdAt`, and `showActions`. This exceeds the four-parameter threshold identified in the lab instructions and makes the function harder to call and understand.

**Cost:** Developers must remember the correct order and meaning of six arguments every time they call the function. Passing arguments in the wrong order could produce incorrect output. Adding more task information could make the function even harder to maintain.

**Not yet fixing:** noted for Week 3.