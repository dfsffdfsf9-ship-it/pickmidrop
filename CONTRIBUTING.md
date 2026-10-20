# Contributing & Development Guidelines: PickmiDrop

Welcome to the **PickmiDrop** project! To maintain high code quality, stability, and speed across our team, we follow standardized branching, commit, and Pull Request (PR) rules.

---

## 🌿 1. Branch Structure & Strategy

We adopt a modified **GitFlow / Feature Branching** strategy tailored for desktop game development and Steam releases:

```
[ main / production ]  <-- Tagged Steam releases (v1.0.0, v1.1.0)
       ^
       | (release PR)
[ develop ]            <-- Active integration branch (nightly builds)
   ^       ^
   |       |
feature/  feature/     <-- Short-lived feature & bugfix branches
```

### Primary Branches
* **`main`**:
  * Represents production-ready code deployed or packaged for Steam.
  * Direct commits are strictly **forbidden**.
  * Only merged into via release PRs from `develop` or critical `hotfix/*` branches.
  * Each merge into `main` must be tagged with a semantic version (e.g., `v0.1.0`).

* **`develop`**:
  * The primary integration and staging branch.
  * Contains the latest tested features ready for team playtesting.
  * Direct commits are strictly **forbidden**.
  * Changes must be introduced via Pull Requests.

### Working Branches
Create working branches off `develop` using the following prefixes:

| Branch Type | Naming Convention | Description | Example |
| :--- | :--- | :--- | :--- |
| **Feature** | `feature/<jira-or-issue-id>-<short-description>` | New game features, mechanics, or UI screens | `feature/PMD-12-depression-test` |
| **Bugfix** | `bugfix/<jira-or-issue-id>-<short-description>` | Fixes for issues found during development | `bugfix/PMD-44-roulette-audio-desync` |
| **Refactor** | `refactor/<short-description>` | Code restructuring without altering gameplay logic | `refactor/steam-inventory-service` |
| **Release** | `release/v<version>` | Pre-release stabilization, version bump, changelogs | `release/v0.2.0` |
| **Hotfix** | `hotfix/<short-description>` | Critical fixes directly for `main` production builds | `hotfix/steam-auth-session-crash` |

---

## ✍️ 2. Commit Message Rules

We strictly adhere to the [**Conventional Commits Specification**](https://www.conventionalcommits.org/en/v1.0.0/):

### Commit Format
```text
<type>(<optional scope>): <imperative summary>

[optional body explaining context / 'why' rather than 'what']

[optional footer(s), e.g., Closes #123, Refs PMD-45]
```

### Allowed Types
- **`feat`**: A new feature (e.g., egg hatching mechanic, free case unboxing)
- **`fix`**: A bug fix (e.g., odds calculation rounding error, Telegram webhook fix)
- **`docs`**: Documentation changes only (e.g., README, API docs)
- **`style`**: Code style changes (whitespace, formatting, missing semicolons, no logic change)
- **`refactor`**: Code change that neither fixes a bug nor adds a feature
- **`perf`**: Performance improvement (e.g., optimizing wheel animation canvas rendering)
- **`test`**: Adding missing tests or correcting existing tests
- **`chore`**: Maintenance tasks, package upgrades, CI workflow configs
- **`assets`**: Adding or updating sound effects, voice-overs, 3D models, or textures

### Examples
```bash
# Good examples:
git commit -m "feat(roulette): implement voice-over announcer for 1% jackpot drop"
git commit -m "fix(pet): prevent pet expiration timer decrement when app is paused"
git commit -m "chore(deps): update steamworks.js to v0.3.1"

# Bad examples:
git commit -m "fix stuff"
git commit -m "WIP"
git commit -m "added depression test files"
```

---

## 🔀 3. Pull Request (PR) Workflow & Rules

All contributions must go through the Pull Request process before reaching `develop` or `main`.

### Step-by-Step PR Procedure:
1. **Sync**: Ensure your branch is up to date with `develop`:
   ```bash
   git checkout develop
   git pull origin develop
   git checkout feature/PMD-XX-your-feature
   git rebase develop
   ```
2. **Push**: Push your branch to the remote repository:
   ```bash
   git push -u origin feature/PMD-XX-your-feature
   ```
3. **Open PR**: Create a Pull Request against `develop` using the repository's PR template.
4. **Link Issues**: Reference related task/issue (e.g., `Closes #42`).
5. **Self-Review**: Review your own diff before requesting peer reviews.

### PR Requirements for Merge
Before any PR can be merged, it must satisfy:
1. **Minimum 1 Approving Review**: At least one designated team member/maintainer must approve.
2. **Green CI Checks**: Automated checks in [`.github/workflows/ci.yml`](file:///c:/Users/sladk/Downloads/PickmiDrop/.github/workflows/ci.yml) must pass without errors (`npm test` / `npm run validate`). See [**CI Documentation (docs/CI_CD.md)**](file:///c:/Users/sladk/Downloads/PickmiDrop/docs/CI_CD.md).
3. **No Unresolved Conversations**: All comments and questions in the PR review must be addressed.
4. **Merge Method**: **Squash and Merge** (or **Rebase and Merge**) is preferred for feature branches to keep integration history clean.

---

## 🛡️ 4. Branch Protection Rules

The repository administrator enforces the following GitHub/GitLab protection rules on `main` and `develop`:
- Require a pull request before merging.
- Require review approvals (Minimum 1 reviewer).
- Dismiss stale pull request approvals when new commits are pushed.
- Require status checks to pass before merging (`build`, `test`, `lint`).
- Require branches to be up to date before merging.
- Restrict who can push to matching branches (admins / bots only).
- Block force pushes (`--force` is disabled).
