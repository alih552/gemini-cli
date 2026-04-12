# Agent Contribution Guide: google-gemini/gemini-cli

**Date:** January 21, 2026 **Topic:** Contributing to the Gemini CLI Codebase
**Status:** Success (Documentation Fix)

## Overview

This document summarizes the learnings, workflow, and troubleshooting steps
discovered while creating a contribution for the `gemini-cli` repository. It is
intended to guide future agents or developers in navigating this specific
codebase efficiently.

## Key Learnings

### 1. Resource Intensity

The `gemini-cli` project is a large monorepo. Standard Node.js memory limits are
often insufficient for running full linting or testing suites
(`npm run preflight` or `npm run test:ci`), especially in a CI or agent
environment.

- **Symptom:**
  `FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory`
- **Solution:** Increase the Node.js heap size before running heavy scripts.
  ```bash
  export NODE_OPTIONS="--max-old-space-size=4096"
  ```

### 2. Test Suite Reliability

Not all tests pass in every environment. Specifically,
`src/ui/utils/terminalSetup.test.ts` in `packages/cli` may fail depending on the
simulated terminal environment variables (e.g., detecting "Windsurf" or "Cursor"
instead of "VS Code").

- **Lesson:** Do not assume test failures are caused by your changes.
- **Strategy:** Verify if the files you modified are referenced in the failing
  tests. If not, and if the failures look environment-specific (like terminal
  detection), they are likely unrelated pre-existing issues.

### 3. Finding "Micro" Contributions

Searching for `TODO` in the codebase (`grep -r "TODO" .`) yields hundreds of
results, many of which are complex architectural changes or vague placeholders.

- **Better Strategy:** Read the documentation files (`CONTRIBUTING.md`,
  `ROADMAP.md`, `README.md`) first. Typos and grammar fixes in these files are
  high-value, low-risk contributions that help maintainers without requiring
  deep architectural knowledge.

## Recommended Workflow

1.  **Setup & Verification:**
    - Check Node version: `node -v` (Should be ~20.19.0).
    - Install dependencies: `npm install`.
    - **Crucial:** Export memory options immediately:
      `export NODE_OPTIONS="--max-old-space-size=4096"`.

2.  **Discovery:**
    - List files to understand the monorepo structure (`packages/cli`,
      `packages/core`).
    - Read `CONTRIBUTING.md` not just for rules, but to spot errors (typos,
      broken links).

3.  **Implementation:**
    - Create a descriptive branch: `git checkout -b fix/your-topic`.
    - Use the `replace` tool for precise edits to avoid overwriting unrelated
      file content.

4.  **Verification:**
    - Run `npm run lint` (fastest check for style/typos).
    - Run `npm run typecheck`.
    - Run `npm run test:ci`.
    - _Note:_ If `test:ci` fails, analyze the stack trace. If unrelated to your
      changes, proceed with the commit but note the failures.

## Specific Commands Cheat Sheet

| Task           | Command                                | Notes                                                    |
| :------------- | :------------------------------------- | :------------------------------------------------------- |
| **Install**    | `npm install`                          | -                                                        |
| **Lint**       | `npm run lint`                         | Requires high memory.                                    |
| **Typecheck**  | `npm run typecheck`                    | Checks TypeScript across workspaces.                     |
| **Full Check** | `npm run preflight`                    | Runs format, build, lint, typecheck, and test:ci. Heavy. |
| **Commit**     | `git commit -m "feat(scope): message"` | Follow Conventional Commits.                             |

## Tips for Future Agents

- **Don't Revert on Unrelated Failures:** If you make a doc change and a complex
  integration test fails, do not revert your work. Verify the isolation of your
  change first.
- **Check "help wanted" Labels:** The `CONTRIBUTING.md` explicitly mentions
  using `help wanted` labels. If you have browser access, check the GitHub
  Issues page for these.
- **Monorepo Awareness:** Remember this is a workspace setup. You might need to
  use `npm run <script> -w <workspace>` to target specific packages if you are
  working on code logic.
