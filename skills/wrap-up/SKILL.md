---
name: wrap-up
description: Ship the current one-on-one session — branch, commit, push, open a PR against main. Not for loop bundling.
disable-model-invocation: true
---

# wrap-up

**Wrap up** the current working tree into a reviewable PR against the repo default branch (usually `main`). One session, one branch, one PR. Do not merge.

Not for bundling loop deliverables — that is a different skill.

## Process

### 1. Snapshot the work

Run in parallel:

- `git status`
- `git diff` and `git diff --staged`
- `git branch -vv` and `git rev-parse --abbrev-ref HEAD`
- `git remote show origin` (or `gh repo view --json defaultBranchRef`) to learn the **base** branch
- `git log -5 --oneline` for commit-message style

**Done when:** you know whether the tree is dirty, which branch you are on, what **base** is, and whether a remote tracking branch already exists.

### 2. Branch

If HEAD is **base** (or a detached HEAD), create and check out a new branch named for the change (`wrap/<short-slug>` is fine).

If already on a feature branch extract the work that was done during this session to a new branch.

**Done when:** HEAD is a non-**base** branch ready to receive the commit.

### 3. Commit

Stage only the files that belong to this wrap-up. Never stage secrets (`.env`, credentials, etc.).

Draft a concise commit message from the diff (why, not a file list). Commit via HEREDOC:

```bash
git commit -m "$(cat <<'EOF'
<message>

EOF
)"
```

Never update git config. Never `--amend` unless the user asked and the amend safety rules in the session allow it. Never `--no-verify`.

If there is nothing to commit and commits already exist ahead of **base**, skip to push.

**Done when:** the branch has one or more local commits ahead of **base**, and `git status` is clean (or only unrelated untracked files the user did not ask to include).

### 4. Push

```bash
git push -u origin HEAD
```

No force push to **base**. No force push unless the user explicitly asked.

**Done when:** the branch is on `origin` and tracks it.

### 5. Open the PR

Use `gh pr create` against **base**. Title: short, imperative. Body via HEREDOC:

```markdown
## Summary
<1–3 bullets: what changed and why>

```

Analyze **all** commits on this branch vs **base** (`git log <base>...HEAD`, `git diff <base>...HEAD`), not only the latest commit.

**Done when:** you return the PR URL to the user, plus a one- or two-sentence explanation of what the PR contains. Stop. Do not merge.
