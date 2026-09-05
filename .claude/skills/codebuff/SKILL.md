```markdown
# codebuff Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill provides a comprehensive guide to the development patterns used in the `codebuff` TypeScript repository. It covers coding conventions, file organization, commit practices, and detailed step-by-step workflows for synchronizing public snapshots and updating release packages. Whether you're contributing new features, fixing bugs, or managing releases, this guide will help you follow the established practices in the codebase.

## Coding Conventions

### File Naming
- **CamelCase** is used for file names.
  - Example: `myComponent.tsx`, `userProfile.ts`

### Import Style
- **Relative imports** are preferred.
  - Example:
    ```typescript
    import { MyComponent } from './components/myComponent';
    ```

### Export Style
- **Named exports** are used throughout the codebase.
  - Example:
    ```typescript
    // In userProfile.ts
    export function getUserProfile(id: string) { ... }
    ```

### Commit Patterns
- Commit messages are **freeform** (no strict prefixes).
- Average commit message length: **~42 characters**.
  - Example: `fix bug in user authentication flow`

## Workflows

### sync-public-snapshot
**Trigger:** When you want to update the public repository with the latest changes from the private repository.  
**Command:** `/sync-public-snapshot`

1. Export or synchronize changes from the private repository.
2. Update the lockfile (`bun.lock`) to reflect any dependency changes.
3. Optionally update release `package.json` files if CLI or release changes occurred:
    - `cli/release/package.json`
    - `freebuff/cli/release/package.json`
4. Optionally update or add new source files (such as components or types) if relevant features or fixes were made:
    - `cli/src/components/*.tsx`
    - `common/src/types/*.ts`
5. Commit and push your changes to the public repository.

**Example:**
```sh
# Synchronize code and update dependencies
cp ../private-repo/cli/src/components/newFeature.tsx cli/src/components/
bun install
git add bun.lock cli/src/components/newFeature.tsx
git commit -m "sync: update public snapshot with new feature"
git push
```

---

### update-release-package-json
**Trigger:** When you want to release a new CLI version or update release metadata.  
**Command:** `/update-release-package`

1. Edit the CLI release `package.json` file:
    - `cli/release/package.json`
    - `freebuff/cli/release/package.json`
2. Update `bun.lock` to reflect any dependency changes.
3. Commit and push your changes.

**Example:**
```sh
# Update version in package.json
vim cli/release/package.json
# Update dependencies
bun install
git add cli/release/package.json bun.lock
git commit -m "release: bump CLI version and update lockfile"
git push
```

## Testing Patterns

- **Testing framework:** Unknown (not detected).
- **Test file pattern:** Files matching `*.test.*` are used for tests.
  - Example: `userProfile.test.ts`
- **General practice:** Place test files alongside or near the modules they test.

**Example:**
```typescript
// userProfile.test.ts
import { getUserProfile } from './userProfile';

test('returns correct user profile', () => {
  expect(getUserProfile('123')).toEqual({ id: '123', name: 'Alice' });
});
```

## Commands

| Command                  | Purpose                                                      |
|--------------------------|--------------------------------------------------------------|
| /sync-public-snapshot    | Synchronize public repo with latest changes from private repo |
| /update-release-package  | Update CLI release package.json and lockfile                 |
```
