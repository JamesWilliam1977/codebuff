---
name: sync-public-snapshot
description: Workflow command scaffold for sync-public-snapshot in codebuff.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /sync-public-snapshot

Use this workflow when working on **sync-public-snapshot** in `codebuff`.

## Goal

Synchronizes the public repository with updates from the private repository, typically after changes in the private repo.

## Common Files

- `bun.lock`
- `cli/release/package.json`
- `freebuff/cli/release/package.json`
- `cli/src/components/*.tsx`
- `common/src/types/*.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Export or sync changes from the private repository.
- Update lockfile (bun.lock) to reflect dependency changes.
- Optionally update release package.json files if CLI or release changes occurred.
- Optionally update or add new source files (e.g., components, types) if relevant features or fixes were made.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.