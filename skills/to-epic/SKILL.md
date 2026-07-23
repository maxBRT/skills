---
name: to-epic
description: Turn the current conversation into an epic (full PRD) with tracer-bullet sub-issues on the project issue tracker.
disable-model-invocation: true
---

# to-epic

Synthesize the current conversation into one **epic** — a parent issue whose body is the full PRD — plus **tracer-bullet** sub-issues under it, each declaring its blocking edges. Do not interview the user; synthesize what you already know.

Tracker-agnostic: the epic, its children, and blocking edges are the same everywhere. How they are stored (GitHub sub-issues, Linear parent/sub-issues, local markdown, Jira, ...) comes from the repo's configured tracker docs. If none are configured, ask which tracker and how parent/child + blocking are expressed before publishing.

## Process

### 1. Orient

Explore the repo if you have not already. Use the project's domain glossary throughout, and respect ADRs in the area you are touching.

Sketch the seams at which you will test the feature. Prefer existing seams; prefer the highest seam; fewer seams is better (ideal: one). Confirm the seams with the user.

**Done when:** seams are listed and the user has confirmed them.

### 2. Draft the epic

Write the epic body using the template in [`epic-template.md`](epic-template.md). Keep it in the conversation — do not publish yet.

**Done when:** a complete draft epic exists in chat (every template section filled or explicitly marked N/A).

### 3. Draft tracer-bullet children

Break the work into **tracer bullet** sub-issues:

- Each slice cuts a narrow but complete path through every layer (schema, API, UI, tests) — vertical, not a horizontal layer slice
- A completed slice is demoable or verifiable on its own
- Each slice fits one fresh context window
- Prefactoring comes first ("make the change easy, then make the easy change")

Give each child its **blocking edges** — the other children that must complete before it can start. A child with no blockers can start immediately.

**Wide refactors** are the exception: one mechanical change whose blast radius fans across the codebase so no vertical slice can land green. Sequence as **expand–contract** — expand (new form beside old), migrate in blast-radius batches (each batch its own child, blocked by expand), then contract (delete the old form, blocked by every migrate). If batches cannot stay green alone, share an integration branch and block a final integrate-and-verify child.

**Done when:** every proposed child has a title, blocked-by list, and one-line "what it delivers."

### 4. Quiz the user

Present the breakdown as a numbered list. For each child show:

- **Title**
- **Blocked by**
- **What it delivers** (end-to-end behaviour)

Ask: granularity (too coarse / too fine)? Blocking edges correct? Merge or split any?

Iterate until the user approves.

**Done when:** the user has explicitly approved the epic scope and the child breakdown.

### 5. Publish

Publish in dependency order:

1. Create the **epic** (parent) with the approved PRD body.
2. Create each **child** as a sub-issue of that epic, blockers first so blocking edges can reference real identifiers. Body: [`child-template.md`](child-template.md). Use native parent/child and native blocking where the tracker has them; otherwise encode parent + "Blocked by" in the body. 

Avoid specific file paths or code snippets — they go stale. Exception: a prototype snippet that encodes a decision more precisely than prose (state machine, reducer, schema, type shape) — inline the decision-rich bits and note they came from a prototype.

**Done when:** the epic exists on the tracker, every approved child exists as its sub-issue with parent link and blocking edges set, and you return the epic URL/path plus the child list (titles + identifiers) to the user.
