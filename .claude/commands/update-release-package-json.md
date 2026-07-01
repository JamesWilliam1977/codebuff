---
name: update-release-package-json
description: Workflow command scaffold for update-release-package-json in codebuff.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-release-package-json

Use this workflow when working on **update-release-package-json** in `codebuff`.

## Goal

Updates the release package.json file for the CLI, often together with dependency lockfile updates.

## Common Files

- `cli/release/package.json`
- `freebuff/cli/release/package.json`
- `bun.lock`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit the CLI release package.json file.
- Update bun.lock to reflect any dependency changes.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.