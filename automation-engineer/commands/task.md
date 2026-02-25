---
name: task
description: Manage daily tasks — start a new task, check active task, or close a completed task
---

# Daily Task Management

Manage focused work sessions. Each task is a concrete piece of work from the roadmap.

## Usage

- `/task` — Show the active task or suggest next from roadmap
- `/task start [description]` — Start a new daily task
- `/task done` — Close the active task and record results

---

## `/task` (no arguments)

1. Look for an active task in `project/tasks/` (status: in_progress)
2. If found: show the task's objective, tools, and what's been done so far
3. If not found: read `project/roadmap.md` and suggest the next pending task
4. If roadmap is empty or doesn't exist: suggest running `/setup`

---

## `/task start [description]`

### 1. Load context
- Read `project/roadmap.md` for overall progress
- Read `project/prd.md` for project context
- Check if there's already an active task (if yes, ask to close it first)

### 2. Define the task
If the user provided a description, use it. Otherwise, ask:
- What are we working on today?
- What's the specific goal?
- Which tools/services are involved?

Match the task to a roadmap item if possible.

### 3. Create task file
Create `project/tasks/{YYYY-MM-DD}-{slug}.md` following the template from `project-context`:

- Fill in: objective, tools involved, references to tool files and research
- Set status to `in_progress`
- Link to the roadmap phase

### 4. Load relevant context
Based on the tools involved:
- Read the corresponding `project/tools/{name}.md` files
- Read any relevant `project/research/apis/` documentation
- Read the most recent completed task for continuity

### 5. Start working
Confirm: "Task opened. Here's what we're working on: {summary}. What do we do first?"

---

## `/task done`

### 1. Find active task
Look for the most recent task file in `project/tasks/` with status `in_progress`.

If no active task found, inform the user.

### 2. Record results
Ask the user (or infer from the session):
- What was accomplished?
- What's still pending?
- Any decisions made or things learned?

### 3. Update task file
Update the task file with:
- **Execution**: What was done step by step
- **Result**: What was delivered
- **Pending**: What's left
- **Suggested next task**: Based on roadmap
- Set status to `completed` (or `partial` if not fully done)

### 4. Update roadmap
In `project/roadmap.md`:
- Mark the corresponding task as `[x]` completed
- Add a link to the task file: `(tasks/{filename})`
- Update progress counters
- If this was the last task in a phase, note that the phase is complete

### 5. Summary
Present:
```
## Task completed

**Task**: {title}
**Result**: {1-sentence summary}
**Pending**: {what's left, if anything}

**Roadmap progress**: {X} of {Y} tasks completed
**Next suggested task**: {next pending task from roadmap}
```
