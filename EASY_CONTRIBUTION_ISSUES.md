# Easy Contribution Issues for Gemini CLI

**Created:** January 21, 2026  
**Purpose:** Document easy, beginner-friendly issues for contribution to the
[google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli)
repository

## Overview

This document lists low-hanging fruit issues that are suitable for contributors,
especially those new to the codebase. These issues are:

- **Open** (not closed or resolved)
- **Priority P1** (high priority issues)
- **Excluded labels:** `status/need-triage`, `🔒 maintainer only`,
  `workstream-rollup`
- Well-defined and actionable
- Relatively simple to implement
- Low-risk (won't break core functionality)

**⚠️ Important:** Always verify that an issue is still **open** before starting
work. Issue statuses can change, and this document may not always be up-to-date.

**📋 Filtering Criteria:**

- ✅ Must have `priority/p1` label
- ❌ Must NOT have `status/need-triage` label
- ❌ Must NOT have `🔒 maintainer only` label
- ❌ Must NOT have `workstream-rollup` label

---

## 🔴 Priority P1 Issues

### Currently Available Issues

**Status:** No open issues currently match all the filtering criteria:

- Has `priority/p1` label
- Does NOT have `status/need-triage` label
- Does NOT have `🔒 maintainer only` label
- Does NOT have `workstream-rollup` label

**Note:** Most P1 issues currently have the `status/need-triage` label, which
means they need maintainer review before being ready for contribution. Check
back regularly as issues are triaged and labels are updated.

**How to find new P1 issues:**

1. Visit:
   https://github.com/google-gemini/gemini-cli/issues?q=is%3Aissue+is%3Aopen+label%3Apriority%2Fp1+-label%3A%22status%2Fneed-triage%22+-label%3A%22%F0%9F%94%92+maintainer+only%22+-label%3Aworkstream-rollup
2. Check the issues page regularly for newly triaged issues
3. Issues may be updated to remove `status/need-triage` after maintainer review

---

## 📋 General Contribution Strategies

### Documentation Improvements (Always Available)

**Type:** Documentation  
**Difficulty:** ⭐ Very Easy  
**Approach:** Review and improve existing documentation

**What to look for:**

- Typos and grammar errors
- Broken links
- Unclear explanations
- Missing examples
- Outdated information

**Files to review:**

- `/docs/` directory (all markdown files)
- `CONTRIBUTING.md`
- `README.md`
- `ROADMAP.md`
- Inline code comments

**Steps:**

1. Read through documentation files
2. Identify improvements
3. Make fixes
4. Run `npm run lint` and `npm run format`
5. Create PR with clear description

### Code Quality Improvements

**Type:** Code Quality  
**Difficulty:** ⭐⭐ Easy to Moderate

**What to look for:**

- Simple TODO items (be careful - many are complex)
- Missing type annotations in TypeScript
- Unclear error messages
- Code comments that need improvement

**Note:** Many TODOs in the codebase are complex architectural changes. Focus on
simple, clear improvements.

---

## 🚀 Getting Started Checklist

Before working on any issue:

- [ ] **Verify issue is open:** Check the GitHub issue page to confirm it's
      still open (not closed)
- [ ] **Sign CLA:** https://cla.developers.google.com/ (if not already signed)
- [ ] **Fork repository:** https://github.com/google-gemini/gemini-cli
- [ ] **Clone fork:**
      `git clone https://github.com/YOUR_USERNAME/gemini-cli.git`
- [ ] **Set up environment:**
  ```bash
  cd gemini-cli
  node -v  # Should be ~20.19.0
  npm install
  export NODE_OPTIONS="--max-old-space-size=4096"  # Important for large repo
  ```
- [ ] **Self-assign issue:** Comment `/assign` on the GitHub issue (max 3 at
      once)
- [ ] **Create branch:** `git checkout -b fix/issue-number-description`
- [ ] **Make changes:** Follow project conventions
- [ ] **Test changes:** `npm run preflight` (or at minimum: `npm run lint`,
      `npm run typecheck`)
- [ ] **Create PR:** Link to the issue (e.g., `Fixes #123`)

---

## 📚 Important Resources

- **Contributing Guide:**
  [CONTRIBUTING.md](https://github.com/google-gemini/gemini-cli/blob/main/CONTRIBUTING.md)
- **Roadmap:**
  [ROADMAP.md](https://github.com/google-gemini/gemini-cli/blob/main/ROADMAP.md)
- **Architecture Docs:** `/docs/architecture.md`
- **Project Structure:** See `AGENT_CONTRIBUTION_LEARNINGS.md` in this directory

---

## ⚠️ Important Notes

1. **Excluded labels (do not contribute to issues with these):**
   - `status/need-triage` - Issues need maintainer review first
   - `🔒 maintainer only` - Reserved for maintainers
   - `workstream-rollup` - Complex, multi-part work
   - `⛔ Do not contribute` - Explicitly not for contributors

2. **Required labels:**
   - `priority/p1` - High priority issues (focus on these)

3. **PR Requirements:**
   - All PRs must link to an existing issue
   - Follow [Conventional Commits](https://www.conventionalcommits.org/)
   - Run `npm run preflight` before submitting
   - Update documentation for user-facing changes

4. **Memory Issues:**
   - This is a large monorepo
   - Always set: `export NODE_OPTIONS="--max-old-space-size=4096"`
   - Some tests may fail in certain environments (check if related to your
     changes)

5. **Test Failures:**
   - Not all tests pass in every environment
   - If a test fails but isn't related to your changes, it's likely a
     pre-existing issue
   - Verify your changes are isolated before assuming responsibility

---

## 🎯 Finding Your First Issue

**Current Status:** No P1 issues are currently available that meet all filtering
criteria.

**What to do:**

1. **Check regularly:** Visit the GitHub issues page and use the search filter:

   ```
   is:issue is:open label:priority/p1 -label:"status/need-triage" -label:"🔒 maintainer only" -label:workstream-rollup
   ```

2. **Alternative approach:** If no P1 issues are available, consider:
   - Reviewing documentation for improvements (see "General Contribution
     Strategies" below)
   - Waiting for issues to be triaged (status/need-triage label removed)
   - Checking for other priority labels (p2, p3) if maintainers approve

3. **Monitor for updates:** Issues are regularly triaged, and labels are
   updated. Check back frequently.

---

## 📝 Issue Tracking

| Issue # | Title                         | Type | Difficulty | Priority | Status | Notes                                                   |
| ------- | ----------------------------- | ---- | ---------- | -------- | ------ | ------------------------------------------------------- |
| -       | No issues currently available | -    | -          | P1       | -      | All P1 issues currently have `status/need-triage` label |

**Last Checked:** January 21, 2026  
**Next Check:** Issues are triaged regularly - check GitHub for updates

---

## 🔍 Finding More Issues

To find P1 issues that meet the criteria:

1. **GitHub Search (Primary Method):**

   ```
   is:issue is:open label:priority/p1 -label:"status/need-triage" -label:"🔒 maintainer only" -label:workstream-rollup
   ```

   Direct link:
   https://github.com/google-gemini/gemini-cli/issues?q=is%3Aissue+is%3Aopen+label%3Apriority%2Fp1+-label%3A%22status%2Fneed-triage%22+-label%3A%22%F0%9F%94%92+maintainer+only%22+-label%3Aworkstream-rollup

2. **Alternative Searches:**
   - Check for `help wanted` label (when available)
   - Check for `good first issue` label (when available)
   - Monitor issues as they're triaged (status/need-triage removed)

3. **Review Issues Page:**
   - https://github.com/google-gemini/gemini-cli/issues
   - Sort by recently updated to see newly triaged issues
   - Filter by `priority/p1` and exclude `status/need-triage`

---

**Last Updated:** January 21, 2026  
**Next Review:** Always verify issue status (open/closed) on GitHub before
starting work. Issue statuses change frequently, and this document may not
always reflect the current state.
