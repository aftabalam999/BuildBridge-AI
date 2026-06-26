# 05 - Folder Structure

# BuildBridge AI

## Folder Structure Documentation

---

# 1. Overview

BuildBridge AI follows a modular architecture that separates the frontend and backend into independent applications. Each folder has a single responsibility to improve maintainability, scalability, and collaboration.

```text
BuildBridge-AI/
│
├── client/          # React Frontend
├── server/          # Express Backend
├── docs/            # Project Documentation
├── README.md
└── package.json
```

---

# 2. Frontend Folder Structure

```text
client/
│
├── public/
│
├── src/
│   │
│   ├── assets/
│   │   ├── images/
│   │   ├── icons/
│   │   ├── logos/
│   │   └── illustrations/
│   │
│   ├── components/
│   │   ├── common/
│   │   ├── landing/
│   │   ├── dashboard/
│   │   ├── profile/
│   │   ├── roadmap/
│   │   ├── resume/
│   │   ├── interview/
│   │   └── project/
│   │
│   ├── pages/
│   │
│   ├── layouts/
│   │
│   ├── routes/
│   │
│   ├── context/
│   │
│   ├── hooks/
│   │
│   ├── services/
│   │
│   ├── utils/
│   │
│   ├── constants/
│   │
│   ├── styles/
│   │
│   ├── App.jsx
│   └── main.jsx
│
├── package.json
└── vite.config.js
```

---

# 3. Frontend Folder Explanation

## public/

Contains static files that are served directly.

Examples:

* favicon.ico
* robots.txt
* manifest.json

---

## src/

Main application source code.

---

## assets/

Stores all static resources.

```text
assets/
│
├── images/
├── icons/
├── logos/
└── illustrations/
```

Examples

* Hero images
* Dashboard illustrations
* SVG icons
* Company logos

---

## components/

Reusable UI components grouped by feature.

```text
components/
│
├── common/
├── landing/
├── dashboard/
├── profile/
├── roadmap/
├── resume/
├── interview/
└── project/
```

### common/

Reusable components shared across the application.

Examples

* Button
* Input
* Modal
* Loader
* Card
* Badge
* Avatar
* Toast
* Spinner

---

### landing/

Landing page components.

Examples

* Navbar
* Hero
* Features
* FAQ
* Footer
* CTA
* Testimonials

---

### dashboard/

Dashboard widgets.

Examples

* Sidebar
* Topbar
* WelcomeCard
* StatsCard
* ProfileCompletion
* DashboardCard

---

### profile/

Profile-related components.

Examples

* PersonalInfoForm
* SkillsInput
* EducationForm
* SocialLinks

---

### roadmap/

Roadmap visualization.

Examples

* Timeline
* MilestoneCard
* ResourceCard
* ProgressBar

---

### resume/

Resume analysis UI.

Examples

* ResumeUploader
* ATSScoreCard
* SuggestionCard
* ResumeReport

---

### interview/

Interview preparation.

Examples

* QuestionCard
* DifficultySelector
* AnswerCard

---

### project/

Project recommendation UI.

Examples

* ProjectCard
* TechBadge
* DifficultyBadge

---

## pages/

Represents complete application pages.

```text
pages/
│
├── Landing.jsx
├── Login.jsx
├── Register.jsx
├── Dashboard.jsx
├── Profile.jsx
├── Roadmap.jsx
├── Resume.jsx
├── Projects.jsx
├── Interview.jsx
└── NotFound.jsx
```

Each page combines multiple reusable components.

---

## layouts/

Reusable layouts.

Examples

```text
layouts/
│
├── MainLayout.jsx
└── DashboardLayout.jsx
```

MainLayout

* Navbar
* Footer

DashboardLayout

* Sidebar
* Topbar
* Main Content

---

## routes/

Application routing.

Examples

```text
routes/
│
├── AppRoutes.jsx
└── ProtectedRoute.jsx
```

Responsibilities

* Route configuration
* Authentication guard
* 404 handling

---

## context/

Global React Context.

Examples

```text
context/
│
└── AuthContext.jsx
```

Stores

* Logged-in User
* Authentication State
* Token
* Logout Function

---

## hooks/

Reusable custom hooks.

Examples

```text
hooks/
│
├── useAuth.js
├── useFetch.js
└── useDebounce.js
```

---

## services/

API communication.

Examples

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

* Axios Instance
* API Calls
* Error Handling

---

## utils/

Helper functions.

Examples

```text
utils/
│
├── formatter.js
├── validator.js
└── storage.js
```

---

## constants/

Application constants.

Examples

```text
constants/
│
├── api.js
├── colors.js
└── routes.js
```

---

## styles/

Global styles.

Examples

```text
styles/
│
├── globals.css
└── variables.css
```

---

# 4. Backend Folder Structure

```text
server/
│
├── src/
│   │
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── prompts/
│   ├── routes/
│   ├── services/
│   ├── validators/
│   ├── utils/
│   ├── uploads/
│   ├── app.js
│   └── server.js
│
├── package.json
└── .env
```

---

# 5. Backend Folder Explanation

## config/

Application configuration.

Examples

```text
config/
│
├── db.js
├── gemini.js
└── cloudinary.js
```

Responsibilities

* MongoDB Connection
* Gemini Configuration
* Cloudinary Configuration

---

## controllers/

Receives requests and returns responses.

Examples

```text
controllers/
│
├── authController.js
├── profileController.js
├── roadmapController.js
├── resumeController.js
├── interviewController.js
└── projectController.js
```

Responsibilities

* Validate request
* Call services
* Return JSON

---

## middleware/

Application middleware.

Examples

```text
middleware/
│
├── authMiddleware.js
├── uploadMiddleware.js
├── errorMiddleware.js
└── notFoundMiddleware.js
```

---

## models/

MongoDB models.

```text
models/
│
├── User.js
├── Profile.js
└── Resume.js
```

Each file contains one Mongoose schema.

---

## prompts/

AI prompts.

```text
prompts/
│
├── roadmapPrompt.js
├── resumePrompt.js
├── interviewPrompt.js
└── projectPrompt.js
```

Keeping prompts separate makes them easier to improve without changing controllers.

---

## routes/

REST API endpoints.

```text
routes/
│
├── authRoutes.js
├── profileRoutes.js
├── roadmapRoutes.js
├── resumeRoutes.js
├── interviewRoutes.js
└── projectRoutes.js
```

Responsibilities

* API endpoints
* Route protection
* Controller mapping

---

## services/

Business logic.

```text
services/
│
├── geminiService.js
├── roadmapService.js
├── resumeService.js
├── interviewService.js
└── projectService.js
```

Responsibilities

* AI Communication
* Business Rules
* Database Logic

---

## validators/

Input validation.

Examples

```text
validators/
│
├── authValidator.js
├── profileValidator.js
└── resumeValidator.js
```

---

## utils/

Helper functions.

Examples

```text
utils/
│
├── response.js
├── asyncHandler.js
└── logger.js
```

---

## uploads/

Temporary file storage before Cloudinary upload.

```text
uploads/
│
└── resumes/
```

---

## app.js

Creates the Express application.

Responsibilities

* Register middleware
* Register routes
* Error handling

---

## server.js

Application entry point.

Responsibilities

* Load environment variables
* Connect to MongoDB
* Start Express server

---

# 6. Folder Responsibility Matrix

| Folder      | Responsibility                 |
| ----------- | ------------------------------ |
| assets      | Static resources               |
| components  | Reusable UI                    |
| pages       | Complete screens               |
| layouts     | Shared page layouts            |
| routes      | Navigation & API routes        |
| context     | Global state                   |
| hooks       | Custom React hooks             |
| services    | API and business logic         |
| utils       | Helper functions               |
| controllers | Handle HTTP requests           |
| models      | MongoDB schemas                |
| middleware  | Request processing             |
| prompts     | AI prompt templates            |
| validators  | Request validation             |
| config      | External service configuration |

---

# 7. Best Practices

* Keep one responsibility per file.
* Avoid placing API logic inside React components.
* Never access MongoDB directly from controllers; use services.
* Store AI prompts only in the `prompts` directory.
* Keep reusable UI inside `components/common`.
* Create feature-specific folders as the application grows.
* Separate validation, business logic, and request handling.
* Use descriptive file and folder names.

---

# 8. Summary

The BuildBridge AI folder structure is organized around modularity and separation of concerns. The frontend isolates reusable UI, pages, services, and state management, while the backend separates routing, controllers, services, models, middleware, and AI prompts. This structure enables parallel development by multiple team members and provides a scalable foundation for future features without requiring major refactoring.
