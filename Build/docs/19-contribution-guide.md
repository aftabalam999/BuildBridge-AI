# 19 - Contribution Guide

# BuildBridge AI

## Coding Standards & Contribution Rules

---

# 1. Overview

This document defines the coding standards, Git workflow, contribution process, and best practices for the BuildBridge AI project.

Goals:

* Maintain consistent code quality.
* Reduce merge conflicts.
* Improve readability.
* Simplify code reviews.
* Keep the project scalable.

Every contributor must follow these guidelines before submitting code.

---

# 2. Project Principles

All code should follow these principles:

* Readable over clever.
* Reusable over duplicated.
* Simple over complex.
* Modular over monolithic.
* Consistent over personal preference.

---

# 3. Folder Structure Rules

Do not create new folders unless necessary.

Frontend

```text
client/src/

assets/
components/
pages/
layouts/
routes/
context/
hooks/
services/
utils/
constants/
styles/
```

Backend

```text
server/src/

config/
controllers/
middleware/
models/
prompts/
routes/
services/
validators/
utils/
```

Every file must belong to its appropriate module.

---

# 4. File Naming Convention

Use **PascalCase** for React components.

Examples

```text
Dashboard.jsx
ProfileCard.jsx
ResumeUploader.jsx
RoadmapTimeline.jsx
InterviewCard.jsx
```

Use **camelCase** for utilities and services.

Examples

```text
authService.js
roadmapService.js
profileValidator.js
responseFormatter.js
```

Use **camelCase** for variables and functions.

```javascript
const userProfile = {};

function generateRoadmap() {}
```

Use **UPPER_SNAKE_CASE** for constants.

```javascript
const MAX_FILE_SIZE = 5 * 1024 * 1024;
const API_TIMEOUT = 10000;
```

---

# 5. React Coding Standards

Use only functional components.

✔ Good

```jsx
function Dashboard() {
  return <div>Dashboard</div>;
}
```

Avoid class components.

---

## Component Rules

* One component per file.
* One responsibility per component.
* Keep components under ~200 lines where practical.
* Extract repeated UI into reusable components.

Example

Instead of:

```text
Dashboard.jsx
```

containing every card,

Create:

```text
WelcomeCard.jsx
ResumeCard.jsx
RoadmapCard.jsx
InterviewCard.jsx
```

---

# 6. Backend Coding Standards

Routes

Only define endpoints.

Controllers

Only receive requests and return responses.

Services

Contain all business logic.

Models

Contain only schema definitions.

Middleware

Contain authentication, uploads, and error handling.

Validators

Contain request validation only.

---

# 7. API Standards

Always return the same response format.

Success

```json
{
  "success": true,
  "message": "Operation completed",
  "data": {}
}
```

Failure

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": []
}
```

Do not return inconsistent response structures.

---

# 8. AI Coding Rules

* Store prompts only in the `prompts/` directory.
* Never write prompts inside controllers.
* Return structured JSON from Gemini.
* Validate AI responses before sending them to the frontend.
* Handle malformed AI responses gracefully.

---

# 9. Database Standards

* One schema per file.
* Use Mongoose timestamps.
* Use ObjectId references for relationships.
* Do not duplicate user data across collections.
* Add indexes for frequently queried fields.

Example

```javascript
timestamps: true
```

---

# 10. Git Commit Convention

Format

```text
type(scope): description
```

Examples

```text
feat(auth): add login API

feat(profile): create profile page

fix(resume): validate pdf upload

docs(api): update endpoint documentation

refactor(ai): simplify roadmap service

style(navbar): improve spacing

chore: update dependencies
```

---

# 11. Branch Naming

Features

```text
feature/login

feature/dashboard

feature/profile

feature/roadmap
```

Bug Fixes

```text
bugfix/login-validation

bugfix/navbar-mobile
```

Documentation

```text
docs/api

docs/readme
```

---

# 12. Pull Request Rules

Every Pull Request must:

* Build successfully.
* Pass manual testing.
* Resolve merge conflicts.
* Follow coding standards.
* Include meaningful commit messages.
* Keep changes focused on a single feature.

---

# 13. Code Review Checklist

Before approving a PR, verify:

* Code is readable.
* Naming conventions are followed.
* No duplicated logic.
* Error handling exists.
* API responses are consistent.
* Security concerns are addressed.
* No unnecessary files are included.

---

# 14. Frontend Best Practices

* Use reusable components.
* Keep page components lightweight.
* Move API calls into `services`.
* Use Context only for global state.
* Avoid inline styles.
* Prefer Tailwind utility classes.
* Handle loading and error states.

---

# 15. Backend Best Practices

* Validate all incoming requests.
* Keep controllers thin.
* Use services for business logic.
* Catch asynchronous errors.
* Protect private routes with JWT middleware.
* Never expose secrets in responses.

---

# 16. Security Guidelines

* Never commit `.env` files.
* Never expose API keys.
* Hash passwords using bcrypt.
* Validate file uploads.
* Sanitize user input.
* Restrict CORS in production.
* Keep dependencies updated.

---

# 17. Documentation Rules

Whenever you:

* Add a new API
* Modify the database schema
* Introduce a new environment variable
* Change the folder structure
* Add a new AI module

Update the corresponding document inside the `docs/` directory.

Documentation should remain synchronized with the implementation.

---

# 18. Code Style

### Indentation

* 2 spaces (frontend)
* 2 spaces (backend)

### Quotes

Use single quotes.

```javascript
const name = 'John';
```

### Semicolons

Always use semicolons.

```javascript
const age = 20;
```

### Trailing Commas

Use trailing commas in multiline objects and arrays.

```javascript
const user = {
  name: 'John',
  age: 20,
};
```

---

# 19. Dependency Management

Install only necessary packages.

Before adding a dependency:

* Verify it is actively maintained.
* Confirm it solves a real problem.
* Avoid duplicate functionality.

Remove unused packages regularly.

---

# 20. Testing Before Merge

Every contributor should verify:

* Application starts successfully.
* No console errors.
* APIs respond correctly.
* Responsive layout works.
* AI features return valid JSON.
* Authentication flow is functional.

---

# 21. Definition of Done

A contribution is complete when:

* Feature is implemented.
* Code is committed.
* Pull Request is created.
* Review feedback is addressed.
* Manual testing is completed.
* Documentation is updated if required.
* Changes are merged into `develop`.

---

# 22. Common Mistakes to Avoid

* Large, unrelated commits.
* Direct commits to `main`.
* Hardcoded API URLs.
* Duplicate components.
* Business logic inside React components.
* Database queries inside controllers.
* AI prompts inside controllers.
* Committing `.env` files.
* Ignoring linting or formatting issues.

---

# 23. Contributor Workflow

```text
Create Feature Branch
        │
        ▼
Implement Feature
        │
        ▼
Manual Testing
        │
        ▼
Commit Changes
        │
        ▼
Push Branch
        │
        ▼
Create Pull Request
        │
        ▼
Code Review
        │
        ▼
Merge into develop
        │
        ▼
Release to main
```

---

# 24. Summary

All contributors to BuildBridge AI must follow a consistent workflow, coding style, and architectural pattern. React components should remain modular, Express controllers should stay lightweight, business logic belongs in services, and AI prompts must be isolated from application logic. By adhering to these standards, the team can collaborate efficiently, reduce integration issues, and maintain a clean, scalable codebase throughout the project.
