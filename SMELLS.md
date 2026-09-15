## 1. God Object, src/todo.js

**Where:** src/todo.js, lines 2-121 (class TodoManager).

**Smell:** God Object. The class owns task data, validates descriptions, assigns urgent priority, reads and writes localStorage, builds the list in the DOM, and attaches button handlers.

**Cost:** Storage, validation, task rules, and presentation all give this class reasons to change. Adding a second storage option requires editing the same class that handles input and renders the page, increasing the amount of unrelated behavior that must be checked after a change.

**Not yet fixing:** noted for Week 3.

## 2. Long Parameter List, src/todo.js

**Where:** src/todo.js, line 124 (buildTaskRow signature), with calls on lines 66 and 75.

**Smell:** Long Parameter List. buildTaskRow takes six positional arguments: id, desc, completed, priority, createdAt, and showActions. Each caller unpacks five fields from the same task and adds a boolean flag.

**Cost:** Every caller must remember the argument order. Swapping string values such as priority and createdAt can silently produce incorrect styling or displayed text. Adding another displayed task field means updating the signature and both calls consistently.

**Not yet fixing:** noted for Week 3.

## 3. Duplicated Code, src/todo.js

**Where:** src/todo.js, lines 62-78 (renderPendingRows and renderCompletedRows).

**Smell:** Duplicated Code. Both methods initialize an HTML string, loop over all tasks, filter by completion, call buildTaskRow with the same arguments, and return the accumulated markup. Only the completion condition differs.

**Cost:** Changes to row-building arguments or shared filtering rules must be repeated in both methods. Updating only one would make pending and completed lists behave differently, so moving a task between sections could change how its row is displayed.

**Not yet fixing:** noted for Week 3.
