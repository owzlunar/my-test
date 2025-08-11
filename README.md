# Git Branching Strategy 

This repository follows a simplified Git Flow branching model with four main branches:

---

## 🔀 Branch Overview

| Branch      | Purpose                                                         |
|-------------|-----------------------------------------------------------------|
| `main`      | Stable, production-ready code. All releases are deployed from here. |
| `dev`       | Integration branch for features. Active development happens here.   |
| `release`   | Staging area for final testing before merging to `main`.         |
| `hotfix`    | For critical fixes applied directly to production (`main`).      |

---

## 🚧 Feature Development

1. Branch off from `dev`:
    ```bash
    git checkout dev
    git checkout -b feature/your-feature-name
    ```

2. Make changes, commit, and merge back to `dev`:
    ```bash
    git add .
    git commit -m "Add: your feature"
    git checkout dev
    git merge feature/your-feature-name
    ```

3. Delete the feature branch after merge (optional).

---

## 🚀 Release Process

1. When `dev` is stable and ready for release:
    ```bash
    git checkout dev
    git checkout -b release/vX.X.X
    ```

2. Do final testing, fixes, or polishing in `release`.

3. Merge into `main` and tag:
    ```bash
    git checkout main
    git merge release/vX.X.X
    git tag -a vX.X.X -m "Release vX.X.X"
    git push origin main --tags
    ```

4. Merge back to `dev` to keep it up to date:
    ```bash
    git checkout dev
    git merge main
    ```

---

## 🛠 Hotfixes

1. Branch from `main`:
    ```bash
    git checkout main
    git checkout -b hotfix/critical-bug
    ```

2. Make the fix, then merge into `main` and `dev`:
    ```bash
    git commit -am "Fix: critical bug"
    git checkout main
    git merge hotfix/critical-bug
    git checkout dev
    git merge hotfix/critical-bug
    ```

---

## 📌 Naming Conventions

- `feature/feature-name`
- `release/v1.0.0`
- `hotfix/issue-description`

---

## ✅ Best Practices

- Use pull requests (PRs) for all merges.
- Keep `main` deployable at all times.
- Protect `main`, `dev`, and `release` branches in your repo settings.
- Use Git tags for all releases (`v1.0.0`, etc.).
