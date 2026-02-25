# 🚀 Release Note Automation with Semantic Versioning

## 📖 About This Project

This project implements an automated **Release Note Generation and Version Control System** using:

* `bump2version` for semantic version management
* GitHub Actions for CI/CD automation
* Commit message parsing for intelligent version bumps
* Automated release note generation
* Email notification workflow for releases

The goal is to eliminate manual version updates and ensure consistent, structured, and traceable software releases.

---

# 📝 About Release Notes

Release Notes are automatically generated whenever a version bump occurs.

They include:

* 📌 New Features (`feat:` commits)
* 🐛 Bug Fixes (`fix:` commits)
* ⚠ Breaking Changes (`BREAKING CHANGE:` commits)
* 📦 Updated Version Number
* 🏷 Git Tag Reference

### 🔄 When Are Release Notes Generated?

Release notes are generated only when:

* A valid commit pattern triggers a version bump
* The CI/CD pipeline successfully completes
* A new version tag is created

After generation:

* A structured release summary is prepared
* Email notifications are sent automatically
* Git tags are updated for traceability

This ensures every meaningful update is properly documented and communicated.

---

# 🔄 Automated Version Control using `bump2version`

This project follows **Semantic Versioning (SemVer)** principles:

```
MAJOR.MINOR.PATCH
```

* **MAJOR** → Breaking changes
* **MINOR** → New features (backward compatible)
* **PATCH** → Bug fixes

Whenever changes are pushed to the `main` branch, the GitHub Actions pipeline:

1. Analyzes the latest commit message
2. Determines the appropriate version bump
3. Updates the version file
4. Creates a Git commit for the version update
5. Creates a Git tag
6. Triggers release note generation
7. Sends release notification email

---

# 📌 Version Bump Rules (Commit Convention Based)

| Commit Message Pattern | Version Bump | Example                         | Result          |
| ---------------------- | ------------ | ------------------------------- | --------------- |
| `feat:`                | **Minor**    | `feat: add login endpoint`      | `1.0.0 → 1.1.0` |
| `fix:`                 | **Patch**    | `fix: correct typo in README`   | `1.0.0 → 1.0.1` |
| `BREAKING CHANGE:`     | **Major**    | `BREAKING CHANGE: overhaul API` | `1.0.0 → 2.0.0` |
| `chore:` or others     | ❌ No Bump    | `chore: update docs`            | No change       |

> 🔎 Only commits matching the defined patterns trigger version updates.
> All other commits are ignored by the versioning workflow.

---

# ⚙️ CI/CD Workflow Overview

### 🔹 Step 1: Code Push

Developer pushes changes to the `main` branch.

### 🔹 Step 2: Commit Analysis

The workflow checks the commit message format.

### 🔹 Step 3: Version Bump

`bump2version` updates:

* Version file
* Git commit
* Git tag

### 🔹 Step 4: Release Note Generation

Structured release notes are created based on commit type.

### 🔹 Step 5: Email Notification

An automated email is sent containing:

* Updated version number
* Summary of changes
* Release metadata

---

# 📌 Developer Note

After a version bump occurs via CI:

```bash
git pull origin main
```

Or verify your repository status:

```bash
git status
```

This ensures your local repository remains synchronized with the automated version commit.

---

# 🎯 Key Benefits

* Fully automated semantic versioning
* No manual version management
* Structured and consistent release notes
* CI-integrated release communication
* Clean and scalable DevOps workflow
