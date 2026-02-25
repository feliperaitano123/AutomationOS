---
description: Organizes requirements into prioritized tasks with dependencies and writes to the roadmap
---

# Task Planning

Planning and task organization skill. Auto-activates when the user describes what needs to be done or asks to organize work.

## When to activate

- User describes a requirement or feature to implement
- Requests like "what needs to be done", "how to organize", "where to start"
- New projects that need structuring
- Progress review or reprioritization

## How it works

### 1. Understand the requirement

Before breaking into tasks, confirm:
- What exactly needs to be delivered?
- Is there a dependency on something external (API, credential, approval)?
- What's the priority relative to other things in progress?
- What tools and research already exist? (check `project/tools/` and `project/research/`)

### 2. Break into tasks

Each task should be:
- **Actionable**: Starts with a verb (Create, Configure, Test, Connect)
- **Small**: Completable in one work session
- **Independent when possible**: Minimize dependencies between tasks
- **Verifiable**: Has a clear "done" criteria

### 3. Order by dependency and impact

Prioritize in this order:
1. Tasks that unblock other tasks
2. Tasks with highest impact on the final result
3. Simpler tasks (quick wins for momentum)
4. Optional or polish tasks

### 4. Write to roadmap

Tasks go directly into `project/roadmap.md`. Follow this format:

```markdown
## Phase 1: {name}
- [ ] Task 1 — short description
- [ ] Task 2 — short description

## Phase 2: {name}
- [ ] Task 3 — short description (depends on: Task 1)
- [ ] Task 4 — short description

## Phase 3: Validation
- [ ] Task 5 — test complete flow
```

When updating an existing roadmap:
- Don't remove completed tasks — they serve as history
- Mark completed tasks with `[x]` and link to the task log file
- Add new phases or tasks as needed
- Update the progress counters at the top

### 5. Connect to daily tasks

Each roadmap task can become a daily `/task start`. When a task is started:
- A file is created in `project/tasks/{YYYY-MM-DD}-{slug}.md`
- The roadmap entry links to this file
- When done, both the task file and roadmap are updated

## Rules

- Never create more than 3 phases — if you need more, the scope is too large
- If a task has more than 5 subtasks, break it into separate tasks
- Always include a validation/testing phase
- Ask about priorities when multiple requirements compete
- Tasks must reference the tools they'll use (linking to `project/tools/`)
