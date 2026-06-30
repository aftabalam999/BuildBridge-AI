# 12 - Routing

# BuildBridge AI

## Frontend & Backend Routing Documentation

---

# 1. Overview

The application uses:

* **React Router DOM** for client-side routing.
* **Express Router** for backend REST APIs.

Routes are divided into:

* Public Routes
* Protected Routes
* API Routes

---

# 2. Frontend Route Architecture

```text
BrowserRouter
│
├── Public Routes
│
└── Protected Routes
      │
      └── Dashboard Layout
```

---

# 3. Frontend Route Structure

```text
/

├── Login

├── Register

└── Dashboard
      ├── Profile
      ├── Roadmap
      ├── Resume
      ├── Projects
      └── Interview
```

---

# 4. Public Routes

These routes are accessible without authentication.

| Route       | Page         | Layout     |
| ----------- | ------------ | ---------- |
| `/`         | Landing Page | MainLayout |
| `/login`    | Login        | MainLayout |
| `/register` | Register     | MainLayout |
| `*`         | Not Found    | MainLayout |

---

## Landing Page

### Route

```text
/
```

### Purpose

* Product Introduction
* Hero Section
* Features
* CTA
* Navigation

---

## Login

### Route

```text
/login
```

### Purpose

Authenticate existing users.

---

## Register

### Route

```text
/register
```

### Purpose

Create a new user account.

---

## Not Found

### Route

```text
*
```

Displays a custom 404 page.

---

# 5. Protected Routes

Protected routes require authentication.

```text
ProtectedRoute

↓

DashboardLayout

↓

Requested Page
```

---

## Dashboard

```text
/dashboard
```

Purpose

* Welcome Card
* AI Summary
* Quick Navigation

---

## Profile

```text
/profile
```

Purpose

* Edit Personal Information
* Skills
* Career Goal

---

## Roadmap

```text
/roadmap
```

Purpose

* Generate AI Roadmap
* View Timeline

---

## Resume

```text
/resume
```

Purpose

* Upload Resume
* AI Resume Analysis

---

## Projects

```text
/projects
```

Purpose

* AI Project Recommendations

---

## Interview

```text
/interview
```

Purpose

* Interview Preparation

---

# 6. Frontend Route Table

| Route        | Protected | Layout          | Description       |
| ------------ | --------- | --------------- | ----------------- |
| `/`          | No        | MainLayout      | Landing Page      |
| `/login`     | No        | MainLayout      | Login             |
| `/register`  | No        | MainLayout      | Registration      |
| `/dashboard` | Yes       | DashboardLayout | Dashboard         |
| `/profile`   | Yes       | DashboardLayout | User Profile      |
| `/roadmap`   | Yes       | DashboardLayout | AI Career Roadmap |
| `/resume`    | Yes       | DashboardLayout | Resume Analysis   |
| `/projects`  | Yes       | DashboardLayout | AI Projects       |
| `/interview` | Yes       | DashboardLayout | Interview Prep    |
| `*`          | No        | MainLayout      | 404 Page          |

---

# 7. Frontend Navigation Flow

```text
Landing

↓

Register

↓

Login

↓

Dashboard

↓

Profile

↓

Roadmap

↓

Resume

↓

Projects

↓

Interview
```

---

# 8. Route Protection Flow

```text
User

↓

ProtectedRoute

↓

Token Available?

├── Yes
│
│ Dashboard
│
└── No
│
Login
```

---

# 9. Layout Mapping

## MainLayout

Used by:

```text
/

/login

/register

404
```

Contains:

* Navbar
* Footer

---

## DashboardLayout

Used by:

```text
/dashboard

/profile

/roadmap

/resume

/projects

/interview
```

Contains:

* Sidebar
* Topbar
* Main Content

---

# 10. Backend Route Architecture

```text
/api

├── auth

├── profile

├── roadmap

├── resume

├── projects

└── interview
```

Each module has:

* Route File
* Controller
* Service

---

# 11. Backend Route Mapping

## Authentication

Base Route

```text
/api/auth
```

Endpoints

| Method | Endpoint    | Description      |
| ------ | ----------- | ---------------- |
| POST   | `/register` | Register user    |
| POST   | `/login`    | Login user       |
| GET    | `/me`       | Get current user |

---

## Profile

Base Route

```text
/api/profile
```

Endpoints

| Method | Endpoint | Description    |
| ------ | -------- | -------------- |
| GET    | `/`      | Fetch profile  |
| PUT    | `/`      | Update profile |

---

## Career Roadmap

Base Route

```text
/api/roadmap
```

Endpoints

| Method | Endpoint | Description      |
| ------ | -------- | ---------------- |
| POST   | `/`      | Generate roadmap |
| GET    | `/`      | Get all roadmaps |
| GET    | `/:id`   | Get roadmap      |
| DELETE | `/:id`   | Delete roadmap   |

---

## Resume

Base Route

```text
/api/resume
```

Endpoints

| Method | Endpoint   | Description    |
| ------ | ---------- | -------------- |
| POST   | `/`        | Upload resume  |
| POST   | `/analyze` | Analyze resume |
| GET    | `/`        | Resume history |
| DELETE | `/:id`     | Delete resume  |

---

## Projects

Base Route

```text
/api/projects
```

Endpoints

| Method | Endpoint | Description          |
| ------ | -------- | -------------------- |
| POST   | `/`      | Generate AI projects |

---

## Interview

Base Route

```text
/api/interview
```

Endpoints

| Method | Endpoint | Description                  |
| ------ | -------- | ---------------------------- |
| POST   | `/`      | Generate interview questions |

---

# 12. Backend Folder Mapping

```text
routes/

├── authRoutes.js

├── profileRoutes.js

├── roadmapRoutes.js

├── resumeRoutes.js

├── projectRoutes.js

└── interviewRoutes.js
```

Each route file maps to:

```text
Route

↓

Controller

↓

Service

↓

Database / Gemini
```

---

# 13. Complete Request Flow

```text
React Page

↓

React Router

↓

Axios

↓

Express Route

↓

Controller

↓

Service

↓

MongoDB / Gemini

↓

JSON

↓

React UI
```

---

# 14. API Security

The following routes require JWT authentication:

| Route        | Protected |
| ------------ | --------- |
| `/profile`   | Yes       |
| `/roadmap`   | Yes       |
| `/resume`    | Yes       |
| `/projects`  | Yes       |
| `/interview` | Yes       |
| `/auth/me`   | Yes       |

Public routes:

* `/auth/register`
* `/auth/login`

---

# 15. Route Naming Conventions

Frontend

* Use lowercase paths.
* Use nouns instead of verbs.
* Avoid nested routes unless necessary.

Examples

```text
/profile

/roadmap

/projects
```

Backend

* Prefix every endpoint with `/api`.
* Use RESTful conventions.
* Use HTTP methods instead of action names.

Examples

```text
POST /api/roadmap

GET /api/profile

DELETE /api/resume/:id
```

---

# 16. Future Routes

These routes are planned for future versions.

Frontend

```text
/settings

/progress

/chat

/jobs

/notifications

/admin
```

Backend

```text
/api/chat

/api/jobs

/api/notifications

/api/admin

/api/progress
```

---

# 17. Routing Best Practices

* Keep routes RESTful.
* Protect sensitive pages using `ProtectedRoute`.
* Centralize route definitions.
* Avoid hardcoding URLs in components.
* Use route constants where possible.
* Keep page-specific logic inside page components.
* Use nested layouts instead of repeating UI.

---

# 18. Summary

BuildBridge AI uses React Router for client-side navigation and Express Router for REST APIs. Public pages are rendered with `MainLayout`, while authenticated pages use `DashboardLayout` behind a `ProtectedRoute`. Backend routes are organized by feature module and follow RESTful conventions, enabling a clear separation between authentication, profile management, AI services, and data operations. This routing structure supports modular development, straightforward navigation, and future expansion without significant refactoring.
