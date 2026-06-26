# 13 - Component Tree

# BuildBridge AI

## React Component Hierarchy Documentation

---

# 1. Overview

The frontend follows a **component-based architecture** where pages are built from reusable UI components.

Hierarchy:

```text
App
│
├── Layout
│
├── Page
│
├── Feature Components
│
└── Common Components
```

Design Principles

* Single Responsibility
* Reusable Components
* Composition over Inheritance
* Feature-Based Organization
* Minimal Component Nesting

---

# 2. Complete Component Hierarchy

```text
App
│
├── BrowserRouter
│
├── AuthProvider
│
└── AppRoutes
    │
    ├── MainLayout
    │   │
    │   ├── Navbar
    │   ├── Page
    │   └── Footer
    │
    └── DashboardLayout
        │
        ├── Sidebar
        ├── Topbar
        └── Page
```

---

# 3. Root Components

```text
App
│
├── BrowserRouter
├── AuthProvider
├── ToastProvider
└── AppRoutes
```

Responsibilities

### App

Application root.

### BrowserRouter

Handles client-side routing.

### AuthProvider

Stores authentication state.

### ToastProvider

Displays notifications.

---

# 4. Layout Components

## MainLayout

Used for public pages.

```text
MainLayout
│
├── Navbar
├── Outlet
└── Footer
```

Pages using MainLayout

* Landing
* Login
* Register
* NotFound

---

## DashboardLayout

```text
DashboardLayout
│
├── Sidebar
├── Topbar
├── MobileSidebar
└── Outlet
```

Pages using DashboardLayout

* Dashboard
* Profile
* Roadmap
* Resume
* Projects
* Interview

---

# 5. Landing Page Tree

```text
LandingPage
│
├── HeroSection
│
├── FeaturesSection
│
├── HowItWorksSection
│
├── CareerDomainsSection
│
├── TestimonialsSection
│
├── FAQSection
│
├── CTASection
│
└── Footer
```

---

# 6. Authentication Components

## Login

```text
LoginPage
│
├── LoginForm
│
├── Input
│
├── PasswordInput
│
├── SubmitButton
│
└── AuthFooter
```

---

## Register

```text
RegisterPage
│
├── RegisterForm
│
├── Input
│
├── PasswordInput
│
├── ConfirmPassword
│
└── SubmitButton
```

---

# 7. Dashboard Tree

```text
Dashboard
│
├── WelcomeCard
│
├── ProfileCompletionCard
│
├── RoadmapPreviewCard
│
├── ResumeScoreCard
│
├── ProjectsPreviewCard
│
├── InterviewPreviewCard
│
└── RecentActivityCard
```

---

# 8. Profile Page

```text
ProfilePage
│
├── PersonalInfoForm
│
├── EducationForm
│
├── SkillsInput
│
├── InterestsInput
│
├── CareerGoalSelect
│
├── SocialLinksForm
│
└── SaveButton
```

---

# 9. Roadmap Page

```text
RoadmapPage
│
├── RoadmapHeader
│
├── GenerateButton
│
├── Timeline
│   │
│   └── MilestoneCard
│
├── ProjectSuggestions
│
└── ResourcesList
```

---

# 10. Resume Page

```text
ResumePage
│
├── ResumeUploader
│
├── UploadButton
│
├── ResumeCard
│
├── ATSScoreCard
│
├── StrengthsCard
│
├── WeaknessesCard
│
└── SuggestionsCard
```

---

# 11. Projects Page

```text
ProjectsPage
│
├── FilterBar
│
├── ProjectGrid
│
│   └── ProjectCard
│
└── EmptyState
```

Each ProjectCard contains:

```text
ProjectCard
│
├── Title
├── DifficultyBadge
├── TechStack
├── Description
├── Duration
└── LearningOutcomes
```

---

# 12. Interview Page

```text
InterviewPage
│
├── DifficultySelector
│
├── GenerateButton
│
├── QuestionList
│
│   └── QuestionCard
│
└── EmptyState
```

Each QuestionCard

```text
QuestionCard
│
├── DifficultyBadge
├── Question
├── Answer
└── Tips
```

---

# 13. Sidebar Tree

```text
Sidebar
│
├── Logo
│
├── Navigation
│   │
│   ├── Dashboard
│   ├── Profile
│   ├── Roadmap
│   ├── Resume
│   ├── Projects
│   └── Interview
│
└── LogoutButton
```

---

# 14. Topbar Tree

```text
Topbar
│
├── PageTitle
├── SearchBar (Future)
├── NotificationIcon (Future)
└── UserDropdown
```

---

# 15. Common Components

```text
components/common/

├── Button

├── Input

├── Select

├── TextArea

├── Modal

├── Card

├── Badge

├── Avatar

├── Loader

├── Spinner

├── EmptyState

├── Toast

├── Skeleton

├── Divider

├── Tooltip

└── ConfirmDialog
```

These components should never contain business logic.

---

# 16. Form Components

Reusable form controls.

```text
forms/

├── TextInput

├── PasswordInput

├── EmailInput

├── FileUpload

├── MultiSelect

├── TagsInput

└── SubmitButton
```

---

# 17. Component Dependency Flow

```text
Page

↓

Feature Components

↓

Common Components
```

Example

```text
Dashboard

↓

RoadmapPreview

↓

Card

↓

Button
```

---

# 18. State Ownership

## Global State

Stored in Context

```text
User

Token

Authentication
```

---

## Page State

Stored inside pages

Examples

* Form Data
* Loading
* Error
* API Responses

---

## Component State

Only UI state

Examples

* Modal Open
* Dropdown
* Accordion
* Active Tab

---

# 19. Component Naming Convention

Use PascalCase.

Examples

```text
ResumeUploader.jsx

ProjectCard.jsx

RoadmapTimeline.jsx

ProfileForm.jsx

InterviewQuestionCard.jsx
```

Avoid names like:

```text
card.jsx

button2.jsx

component.jsx

page.jsx
```

---

# 20. Folder Mapping

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

Every feature should contain only its own components.

---

# 21. Future Components

Future additions may include:

```text
AIChatWidget

ResumeBuilder

ProgressChart

LearningCalendar

JobCard

CompanyCard

NotificationPanel

SettingsPanel

ThemeSwitcher

Leaderboard
```

---

# 22. Best Practices

* One component, one responsibility.
* Keep components small and composable.
* Extract repeated UI into `common`.
* Avoid deeply nested component trees.
* Pass data through props; avoid unnecessary global state.
* Keep API calls at the page or service layer, not inside presentational components.
* Use descriptive component names.

---

# 23. Summary

The BuildBridge AI frontend is organized around a hierarchical component architecture. Pages compose feature-specific components, which in turn reuse shared UI elements from the `common` directory. Layouts provide consistent navigation and structure, while state is kept as local as possible to reduce complexity. This organization promotes code reuse, maintainability, and parallel development across the frontend team.
