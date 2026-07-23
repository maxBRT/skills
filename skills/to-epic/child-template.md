# Child issue template

Body for each tracer-bullet sub-issue under the epic.

## What to build

The end-to-end behaviour this ticket makes work, from the user's perspective — not layer-by-layer implementation.

## Acceptance criteria

- [ ] Criterion 1
- [ ] Criterion 2

## Blocked by

- A reference to each blocking child, or "None — can start immediately".

---

# Local `tickets.md` fallback (optional)

Only when the tracker is a single ordered file instead of one file/issue per child:

```markdown
# Tickets: <short name of the work>

A one-line summary of what these tickets build. Reference the epic/PRD.

Work the **frontier**: any ticket whose blockers are all done. For a purely linear chain that means top to bottom.

## <Ticket title>

**What to build:** the end-to-end behaviour this ticket makes work, from the user's perspective — not a layer-by-layer implementation list.

**Blocked by:** the titles of the tickets that gate this one, or "None — can start immediately".

- [ ] Acceptance criterion 1
- [ ] Acceptance criterion 2
```
