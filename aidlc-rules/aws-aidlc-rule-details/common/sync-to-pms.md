# Sync to Project Management System

## Purpose
Synchronize AI-DLC artifacts to an external project management system (Jira, Azure DevOps, etc.) using MCP tools.

## When to Use
- After User Stories stage completion
- After Units Generation stage completion
- On-demand when user requests PM sync

## Artifacts to Sync

| Artifact | Path | Sync Content |
|----------|------|--------------|
| User Stories | `aidlc-docs/inception/user-stories/stories.md` | Epics, stories, acceptance criteria |
| Requirements | `aidlc-docs/inception/requirements/requirements.md` | Functional/non-functional requirements |
| Units of Work | `aidlc-docs/inception/application-design/unit-of-work.md` | Work breakdown structure |
| Unit-Story Map | `aidlc-docs/inception/application-design/unit-of-work-story-map.md` | Traceability links |

## Execution Steps

### Step 1: Check Previous Sync Status
- [ ] Read `aidlc-docs/inception/plans/pm-sync-status.md` if exists
- [ ] If previous sync found, use same PM system unless user requests change
- [ ] Skip PM system question if already known

### Step 2: Identify PM System (only if not known)
Ask user which PM system to sync to ONLY if:
- No previous sync status exists
- User explicitly wants to change PM system

### Step 2: Create Sync Plan
Create plan at `aidlc-docs/inception/plans/pm-sync-plan.md`:

```markdown
# PM Sync Plan

## Target System
[PM system name]

## Artifacts to Sync
- [ ] User Stories (stories.md)
- [ ] Requirements (requirements.md)
- [ ] Units of Work (unit-of-work.md)
- [ ] Unit-Story Mapping (unit-of-work-story-map.md)

## Sync Actions
[List specific items to create/update]
```

### Step 3: Execute Sync
- [ ] Read each artifact file
- [ ] Use appropriate MCP tool for target PM system
- [ ] For each item: create if new, update if exists

### Step 4: Update Sync Status
Append results to `aidlc-docs/inception/plans/pm-sync-status.md`:

```markdown
## Sync [timestamp]
- **System**: [PM system]
- **Items Created**: [count]
- **Items Updated**: [count]
```

## Completion Message

```markdown
**PM Sync Complete**

Synchronized to [PM System]:
- [X] items created
- [Y] items updated

**What would you like to do next?**
A) Continue with AI-DLC workflow
B) Review sync details

[Answer]:
```

## Error Handling
- If MCP tool unavailable, inform user and skip sync
- If artifact missing, skip and note in status
