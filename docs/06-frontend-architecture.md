# 06 - Frontend Architecture

# BuildBridge AI

## React Frontend Architecture Documentation

---

# 1. Overview

The frontend of BuildBridge AI is built using **React (Vite)** with a **feature-based architecture**. The application is divided into reusable components, layouts, pages, services, and utilities to keep the codebase modular and maintainable.

### Design Principles

* Component Reusability
* Separation of Concerns
* Feature-Based Organization
* Responsive Design
* Scalable Routing
* Centralized API Communication
* Minimal Global State

---

# 2. Technology Stack

| Technology                   | Purpose                  |
| ---------------------------- | ------------------------ |
| React                        | UI Library               |
| Vite                         | Development & Build Tool |
| Tailwind CSS                 | Styling                  |
| React Router DOM             | Client-side Routing      |
| Axios                        | API Requests             |
| Framer Motion                | Animations               |
| React Context API            | Global State             |
| React Hook Form *(Optional)* | Form Management          |

---

# 3. Frontend Architecture

```text
src/
│
├── assets/
├── components/
├── context/
├── hooks/
├── layouts/
├── pages/
├── routes/
├── services/
├── utils/
├── constants/
├── styles/
│
├── App.jsx
└── main.jsx
```

Each folder has a dedicated responsibility to ensure clear separation between UI, logic, routing, and data access.

---

# 4. Application Entry Flow

```text
main.jsx
      │
      ▼
<App />
      │
      ▼
<AuthProvider>
      │
      ▼
BrowserRouter
      │
      ▼
AppRoutes
      │
      ▼
Selected Page
      │
      ▼
Reusable Components
```

---

# 5. Application Routing

The application uses **React Router v6**.

## Public Routes

```text
/
```

Landing Page

```text
/login
```

Login Page

```text
/register
```

Register Page

---

## Protected Routes

```text
/dashboard
/profile
/roadmap
/resume
/projects
/interview
```

Protected routes require a valid JWT token.

---

## Routing Structure

```text
BrowserRouter
│
├── Public Routes
│     ├── Landing
│     ├── Login
│     └── Register
│
└── Protected Routes
      └── DashboardLayout
            ├── Dashboard
            ├── Profile
            ├── Roadmap
            ├── Resume
            ├── Projects
            └── Interview
```

---

# 6. Layout Architecture

The application contains two primary layouts.

## MainLayout

Used for public pages.

Components

* Navbar
* Footer
* Main Content

```text
MainLayout
│
├── Navbar
├── Page
└── Footer
```

---

## DashboardLayout

Used after user authentication.

Components

* Sidebar
* Top Navigation
* Main Content
* Mobile Navigation

```text
DashboardLayout
│
├── Sidebar
├── Topbar
└── Content Area
```

---

# 7. Component Architecture

```text
Page
│
├── Feature Components
│
├── Common Components
│
└── Utility Components
```

Example

```text
Dashboard

│

├── WelcomeCard

├── ProfileCompletion

├── ResumeScoreCard

├── RoadmapCard

├── ProjectCard

└── InterviewCard
```

---

# 8. Common Components

These components are reusable throughout the application.

Examples

* Button
* Input
* TextArea
* Select
* Card
* Badge
* Avatar
* Modal
* Loader
* Spinner
* Toast
* EmptyState

All reusable UI must remain inside:

```text
components/common/
```

---

# 9. State Management

The application intentionally keeps global state minimal.

## Local State

Managed using

```javascript
useState()
```

Used for

* Forms
* Modal Visibility
* Dropdowns
* Loading States

---

## Shared State

Managed using

```javascript
useContext()
```

Context stores

* User
* JWT Token
* Authentication Status
* Logout Function

```text
AuthContext

↓

All Protected Pages
```

---

## Future Upgrade

If the application grows significantly, Context API can be replaced with:

* Redux Toolkit
* Zustand

The current project does not require them.

---

# 10. API Architecture

All HTTP requests are centralized.

```text
React Component

↓

Service Layer

↓

Axios Instance

↓

Backend API
```

Example

```text
Dashboard

↓

roadmapService.js

↓

api.js

↓

Express API
```

Benefits

* Reusable API Calls
* Easier Error Handling
* Cleaner Components

---

# 11. Axios Structure

```text
services/

│

├── api.js

├── authService.js

├── profileService.js

├── roadmapService.js

├── resumeService.js

├── interviewService.js

└── projectService.js
```

Responsibilities

### api.js

* Axios Instance
* Base URL
* Token Injection
* Response Interceptor

### Feature Services

Contain only API functions.

Example

```javascript
login()

register()

generateRoadmap()

uploadResume()

generateProjects()

generateInterview()
```

---

# 12. Authentication Flow

```text
Login

↓

Backend

↓

JWT Token

↓

Local Storage

↓

AuthContext

↓

Protected Route

↓

Dashboard
```

---

# 13. Protected Route Flow

```text
User

↓

ProtectedRoute

↓

Token Exists?

├── Yes
│     ↓
│ Dashboard
│
└── No
      ↓
Login Page
```

---

# 14. Page Architecture

Each page should contain minimal business logic.

```text
Page

↓

Components

↓

Services

↓

API
```

Pages should:

* Fetch Data
* Manage Page State
* Render Components

They should not contain API implementation logic.

---

# 15. Loading States

Every asynchronous operation must display a loading state.

Examples

* Login Button
* Dashboard Loading
* Resume Upload
* AI Generation
* Roadmap Generation

Recommended Components

```text
Loader

Spinner

Skeleton Card
```

---

# 16. Error Handling

Each page must gracefully handle:

* Network Errors
* API Errors
* Validation Errors
* Authentication Errors

Display user-friendly messages using a centralized Toast component.

---

# 17. Responsive Design

The application follows a **mobile-first** approach.

Breakpoints

| Device  |   Width |
| ------- | ------: |
| Mobile  |  <640px |
| Tablet  |  ≥640px |
| Laptop  | ≥1024px |
| Desktop | ≥1280px |

Key considerations

* Collapsible Sidebar
* Mobile Navigation
* Responsive Cards
* Flexible Grid Layouts

---

# 18. Folder Responsibility

| Folder     | Responsibility       |
| ---------- | -------------------- |
| assets     | Images, icons, logos |
| components | Reusable UI          |
| pages      | Complete screens     |
| layouts    | Shared layouts       |
| routes     | Route configuration  |
| context    | Global state         |
| hooks      | Custom hooks         |
| services   | API communication    |
| utils      | Helper functions     |
| constants  | App-wide constants   |
| styles     | Global styling       |

---

# 19. Frontend Best Practices

* Use functional components only.
* Keep components focused on a single responsibility.
* Avoid API calls directly inside reusable components.
* Centralize all HTTP requests in the `services` folder.
* Prefer composition over deeply nested components.
* Use descriptive file names.
* Avoid duplicated UI.
* Separate presentation from business logic.

---

# 20. Frontend Data Flow

```text
User Action
      │
      ▼
React Component
      │
      ▼
Service Layer
      │
      ▼
Axios
      │
      ▼
Backend API
      │
      ▼
JSON Response
      │
      ▼
React State
      │
      ▼
UI Update
```

---

# 21. Summary

The BuildBridge AI frontend follows a modular, feature-based React architecture with centralized routing, reusable layouts, Context API for authentication, and a dedicated service layer for API communication. The design minimizes coupling between UI and business logic, enabling parallel development, easier maintenance, and future scalability without significant restructuring.
