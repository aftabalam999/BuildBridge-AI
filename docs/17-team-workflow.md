# 17 - Team Workflow

# BuildBridge AI

## Team Collaboration & Git Workflow

---

# 1. Overview

This document defines the collaboration process for the BuildBridge AI project.

The objectives are:

* Maintain a clean Git history.
* Minimize merge conflicts.
* Enable parallel development.
* Clearly define responsibilities.
* Ensure code quality before merging.

The team consists of **three developers**:

* Frontend Developer
* Backend Developer
* AI Integration Developer

---

# 2. Team Structure

```text
Project Lead
      │
      ├──────────────┬──────────────┐
      │              │              │
      ▼              ▼              ▼
Frontend        Backend         AI Integration
Developer       Developer        Developer
```

---

# 3. Responsibilities

## Frontend Developer

Responsible for:

* Landing Page
* Authentication UI
* Dashboard UI
* Profile Page
* Roadmap UI
* Resume UI
* Project Cards
* Interview Page
* Responsive Design
* API Integration
* Tailwind Styling

Folders

```text
client/src/

components/
pages/
layouts/
routes/
styles/
assets/
hooks/
context/
```

---

## Backend Developer

Responsible for:

* Express Server
* REST APIs
* MongoDB
* Authentication
* JWT
* Middleware
* Validation
* Controllers
* Database Models
* Cloudinary Integration

Folders

```text
server/src/

controllers/
models/
routes/
middleware/
validators/
config/
```

---

## AI Developer

Responsible for:

* Gemini Integration
* Prompt Engineering
* AI Services
* JSON Validation
* Resume Analysis
* Roadmap Generation
* Project Recommendation
* Interview Generator

Folders

```text
server/src/

prompts/
services/
utils/
```

---

# 4. Git Branch Strategy

The project follows a simple feature-branch workflow.

```text
main
│
└── develop
      │
      ├── frontend
      ├── backend
      └── ai
```

---

## Branch Purposes

### main

Production-ready code only.

---

### develop

Integration branch for all completed features.

---

### frontend

Frontend development.

---

### backend

Backend development.

---

### ai

Gemini integration and AI logic.

---

# 5. Branch Naming Convention

For feature branches:

```text
feature/<feature-name>
```

Examples

```text
feature/login-page

feature/dashboard

feature/profile-api

feature/roadmap-ai

feature/resume-analysis
```

For bug fixes:

```text
bugfix/<issue-name>
```

Examples

```text
bugfix/login-validation

bugfix/navbar-mobile

bugfix/jwt-error
```

---

# 6. Development Workflow

```text
Create Feature Branch

↓

Develop Feature

↓

Commit Changes

↓

Push Branch

↓

Create Pull Request

↓

Code Review

↓

Merge into develop

↓

Merge develop → main
```

---

# 7. Daily Workflow

Every developer should follow this sequence.

### Step 1

Pull the latest changes.

```bash
git checkout develop

git pull origin develop
```

---

### Step 2

Create a feature branch.

```bash
git checkout -b feature/profile-page
```

---

### Step 3

Develop the feature.

---

### Step 4

Commit changes.

```bash
git add .

git commit -m "feat(profile): add profile update form"
```

---

### Step 5

Push the branch.

```bash
git push origin feature/profile-page
```

---

### Step 6

Create a Pull Request.

---

### Step 7

Merge after review.

---

# 8. Commit Message Convention

Use the following format:

```text
type(scope): description
```

---

## Feature

```text
feat(auth): add login API
```

---

## Fix

```text
fix(profile): resolve validation issue
```

---

## Style

```text
style(navbar): improve spacing
```

---

## Refactor

```text
refactor(roadmap): simplify AI response parser
```

---

## Documentation

```text
docs(api): update endpoint documentation
```

---

## Chore

```text
chore: update dependencies
```

---

# 9. Pull Request Checklist

Before creating a PR:

* Code compiles successfully.
* No console errors.
* No unused imports.
* Responsive layout verified.
* API tested.
* No hardcoded secrets.
* Documentation updated if required.

---

# 10. Merge Rules

Merge only if:

* Feature is complete.
* No merge conflicts.
* Build passes.
* Code reviewed by at least one teammate.

Never push directly to:

```text
main
```

---

# 11. Folder Ownership

| Folder             | Owner    |
| ------------------ | -------- |
| client/components  | Frontend |
| client/pages       | Frontend |
| client/layouts     | Frontend |
| client/routes      | Frontend |
| server/routes      | Backend  |
| server/controllers | Backend  |
| server/models      | Backend  |
| server/middleware  | Backend  |
| server/prompts     | AI       |
| server/services    | AI       |
| server/utils       | Shared   |

---

# 12. Communication Workflow

For every completed feature:

```text
Developer

↓

Push Branch

↓

Notify Team

↓

Review

↓

Merge
```

Use a shared communication channel (Discord, WhatsApp, or Slack) for:

* Feature updates
* Merge requests
* Bug reports
* Deployment announcements

---

# 13. Code Review Guidelines

Review for:

* Readability
* Naming conventions
* Reusability
* Error handling
* Performance
* Security
* Documentation

Do not approve code that:

* Breaks existing functionality.
* Introduces duplicated logic.
* Contains commented-out code.
* Includes sensitive credentials.

---

# 14. Project Timeline

## Day 1

* Project setup
* Repository setup
* Documentation
* UI Design
* Database schema

---

## Day 2

Frontend

* Landing Page
* Dashboard
* Profile UI

Backend

* Authentication
* Database
* REST APIs

AI

* Gemini Integration
* Prompt Development

---

## Day 3

* API Integration
* AI Integration
* Resume Upload
* Roadmap Generation
* Testing
* Bug Fixes
* Deployment

---

# 15. Definition of Done

A task is considered complete when:

* Functionality is implemented.
* Code is committed.
* Code is pushed.
* Pull Request is approved.
* Feature is merged into `develop`.
* Documentation is updated if needed.
* No critical bugs remain.

---

# 16. Repository Structure

```text
BuildBridge-AI/

├── client/

├── server/

├── docs/

├── README.md

├── .gitignore

└── LICENSE
```

---

# 17. Best Practices

* Pull before starting work.
* Work only on your assigned branch.
* Commit frequently with meaningful messages.
* Keep pull requests small and focused.
* Avoid editing files owned by another developer without coordination.
* Never commit `.env` files or API keys.
* Resolve conflicts locally before merging.
* Update documentation when APIs or architecture change.

---

# 18. Final Responsibilities

| Team Member | Primary Responsibility                       |
| ----------- | -------------------------------------------- |
| Developer 1 | Frontend (React, Tailwind, UI/UX)            |
| Developer 2 | Backend (Express, MongoDB, JWT, APIs)        |
| Developer 3 | AI (Gemini, Prompt Engineering, AI Services) |

All team members are responsible for:

* Testing
* Bug Fixes
* Documentation
* Deployment Support
* Final Presentation

---

# 19. Summary

The BuildBridge AI team follows a feature-branch Git workflow with a dedicated `develop` branch for integration and `main` for production-ready code. Responsibilities are clearly divided among frontend, backend, and AI developers to enable parallel development while minimizing merge conflicts. Consistent commit messages, pull request reviews, and documented ownership ensure efficient collaboration and a maintainable codebase throughout the hackathon.
