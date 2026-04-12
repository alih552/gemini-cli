---
name: Contribute to Gemini CLI
overview:
  A comprehensive plan to set up the development environment, identify
  contribution opportunities, and make your first contribution to the gemini-cli
  repository.
todos:
  - id: setup-env
    content:
      'Set up development environment: Install Node.js ~20.19.0, fork
      repository, clone fork, install dependencies, and verify build works'
    status: pending
  - id: sign-cla
    content:
      Sign Google Contributor License Agreement at
      https://cla.developers.google.com/
    status: pending
  - id: explore-codebase
    content:
      Review project structure, read CONTRIBUTING.md, ROADMAP.md, and
      architecture docs to understand the codebase
    status: pending
    dependencies:
      - setup-env
  - id: find-opportunity
    content:
      Browse GitHub Issues and Roadmap to find a contribution opportunity (bug
      fix, feature, or documentation improvement)
    status: pending
    dependencies:
      - explore-codebase
  - id: self-assign
    content:
      Self-assign the chosen issue by commenting /assign on the GitHub issue
      (max 3 issues at once)
    status: pending
    dependencies:
      - find-opportunity
  - id: create-branch
    content:
      Create a new git branch for the contribution with a descriptive name
    status: pending
    dependencies:
      - self-assign
  - id: implement-changes
    content:
      Make code or documentation changes following project conventions, update
      docs if user-facing changes
    status: pending
    dependencies:
      - create-branch
  - id: test-changes
    content:
      Run npm run preflight to verify all tests, linting, and formatting pass
      before submitting PR
    status: pending
    dependencies:
      - implement-changes
  - id: create-pr
    content:
      Create pull request linking to the issue, with clear description following
      Conventional Commits format
    status: pending
    dependencies:
      - test-changes
  - id: respond-reviews
    content:
      Respond to PR review comments, make requested changes, and ensure all CI
      checks pass
    status: pending
    dependencies:
      - create-pr
---

# Contributing to Gemini CLI - Complete Setup and Contribution Plan

This plan guides you through setting up your development environment,

understanding the codebase, finding contribution opportunities, and making your

first contribution to the

[gemini-cli repository](https://github.com/google-gemini/gemini-cli).

## Prerequisites and Initial Setup

### 1. Sign Contributor License Agreement (CLA)

- Visit https://cla.developers.google.com/ to sign the Google CLA
- Required before any PRs can be merged
- If you've signed before (even for a different project), you likely don't need

to sign again

- User feedback: This is done.

### 2. Verify Development Environment

- **Node.js**: Install Node.js `~20.19.0` (required for development due to

upstream dependency)

- Use [nvm](https://github.com/nvm-sh/nvm) to manage versions:

`nvm install 20.19.0 && nvm use 20.19.0`

- **Git**: Ensure Git is installed and configured
- **Optional**: Docker/Podman for container-based sandboxing (if you want to

test sandbox features)

### 3. Fork and Clone Repository

- Fork the repository on GitHub: https://github.com/google-gemini/gemini-cli
- Clone your fork:

  ```bash
  git clone https://github.com/YOUR_USERNAME/gemini-cli.git
  cd gemini-cli
  ```

- Add upstream remote:
  ```bash
  git remote add upstream https://github.com/google-gemini/gemini-cli.git
  ```

### 4. Install Dependencies and Build

```bash
npm install
npm run build
```

### 5. Verify Setup

- Run preflight checks: `npm run preflight` (this may take a while on first run)
- Test the CLI: `npm start` (should launch Gemini CLI)
- Run unit tests: `npm run test`

## Understanding the Codebase

### Project Structure

- **`packages/cli/`**: Command-line interface (React-based UI using Ink)
- **`packages/core/`**: Core backend logic and agent functionality
- **`packages/a2a-server/`**: A2A server implementation (Experimental)
- **`packages/vscode-ide-companion/`**: VS Code extension
- **`packages/test-utils/`**: Testing utilities
- **`docs/`**: All project documentation (organized via `sidebar.json`)
- **`scripts/`**: Build, test, and development utility scripts
- **`integration-tests/`**: End-to-end integration tests
- **`evals/`**: Evaluation tests

### Key Files to Review

- [CONTRIBUTING.md](CONTRIBUTING.md): Complete contribution guidelines
- [ROADMAP.md](ROADMAP.md): Project roadmap and priorities
- [GEMINI.md](GEMINI.md): AI-assisted development conventions
- [docs/architecture.md](docs/architecture.md): System architecture
- [package.json](package.json): Project scripts and dependencies

## Finding Contribution Opportunities

### 1. Review Roadmap and Issues

- **Official Roadmap**: https://github.com/orgs/google-gemini/projects/11
- **Roadmap Entry Issue**:

https://github.com/google-gemini/gemini-cli/issues/4191

- **GitHub Issues**: https://github.com/google-gemini/gemini-cli/issues
  - Look for `help wanted` label (when available)
  - Look for `good first issue` label
  - Filter by area labels: `area/model`, `area/tooling`, `area/ux`, `area/docs`,

etc.

- Avoid issues tagged `🔒Maintainers only`

### 2. Contribution Types

- **Bug Fixes**: Fix issues reported in GitHub Issues
- **Features**: Implement roadmap items or approved feature requests
- **Documentation**: Improve docs in `/docs` directory
- **MCP Servers**: Create or improve MCP server integrations
- **Extensions**: Build custom extensions/commands
- **Tests**: Add unit or integration tests

### 3. Self-Assign an Issue

- Find an issue you want to work on
- Comment `/assign` (only that text) to self-assign
- Maximum 3 issues assigned at once

## Making Your Contribution

### 1. Create a Branch

```bash
git checkout -b your-feature-name
# Or for bug fixes: git checkout -b fix/issue-number-description
```

### 2. Make Changes

- **Code changes**: Make edits in `packages/` directory
- **Documentation changes**: Edit files in `docs/` directory
  - Update `docs/sidebar.json` if adding new documentation
- Follow existing code style and conventions
- Review [GEMINI.md](GEMINI.md) for React, comments, and Git conventions

### 3. Test Your Changes

```bash
# Run all checks (recommended before PR)
npm run preflight

# Or run individually:
npm run format      # Format code
npm run lint        # Lint code
npm run build       # Build project
npm run test        # Run unit tests
npm run test:e2e    # Run integration tests (optional, requires API key)
```

### 4. Commit Your Changes

- Follow [Conventional Commits](https://www.conventionalcommits.org/) standard
- Good format: `feat(cli): Add --json flag to 'config get' command`
- Bad format: `Made some changes`
- Link to issue in commit message if applicable: `Fixes #123`

### 5. Create Pull Request

- Push your branch: `git push origin your-feature-name`
- Open PR on GitHub linking to the issue
- **Important**: PRs must be linked to an existing issue
  - For bugs: Link to bug report
  - For features: Link to approved feature request
  - If no issue exists, create one first and wait for maintainer approval

### 6. PR Guidelines

- **Keep it small**: One bug fix or one feature per PR
- **Use draft PRs**: For work-in-progress to get early feedback
- **Update documentation**: If user-facing changes, update `/docs`
- **Clear description**: Explain the "why" and link to issue (e.g.,

`Fixes #123`)

- **Run frontend review**: If touching `packages/cli`, use

`/review-frontend <PR_NUMBER>` in CLI

## Documentation Contributions

### Process

1. Fork and create branch (same as code contributions)
2. Edit files in `/docs` directory
3. Update `docs/sidebar.json` if adding new docs
4. Preview changes locally
5. Run `npm run preflight` to lint/format
6. Open PR

### Style Guide

- Follow

[Google Developer Documentation Style Guide](https://developers.google.com/style)

- Use sentence case for headings
- Write in second person ("you")
- Use present tense
- Include practical examples

## Development Workflow Tips

### Pre-commit Hook (Optional but Recommended)

```bash
echo "
# Run npm build and check for errors
if ! npm run preflight; then
  echo \"npm build failed. Commit aborted.\"
  exit 1
fi
" > .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit
```

### Debugging

- **VS Code**: Press `F5` to debug interactively
- **Command line**: `npm run debug` then attach debugger
- **React DevTools**: `DEV=true npm start` then run `npx react-devtools@4.28.5`

### Sandboxing (Optional)

- Set `GEMINI_SANDBOX=true` in `~/.env` for container-based sandboxing
- Run `npm run build:all` to build sandbox container
- See [CONTRIBUTING.md](CONTRIBUTING.md) for more sandbox options

## Next Steps After First Contribution

1. **Monitor your PR**: Respond to review comments promptly
2. **Help others**: Review other PRs, answer questions in issues
3. **Stay engaged**: Watch the repository, follow roadmap updates
4. **Build expertise**: Focus on specific areas (model support, tooling, UX,

etc.)

## Resources

- **Contributing Guide**: [CONTRIBUTING.md](CONTRIBUTING.md)
- **Roadmap**: [ROADMAP.md](ROADMAP.md) and

https://github.com/orgs/google-gemini/projects/11

- **Documentation**: https://geminicli.com/docs/
- **GitHub Issues**: https://github.com/google-gemini/gemini-cli/issues
- **Community Guidelines**: https://opensource.google/conduct/

## Common Pitfalls to Avoid

1. **Skipping CLA**: PRs will be rejected without signed CLA
2. **No linked issue**: PRs without linked issues are automatically closed
3. **Large PRs**: Break down into smaller, focused PRs
4. **Skipping preflight**: Always run `npm run preflight` before PR
5. **Missing docs**: Update documentation for user-facing changes
6. **Wrong Node version**: Must use Node.js `~20.19.0` for development
