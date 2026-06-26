# 04 - System Architecture

# BuildBridge AI

## System Architecture Documentation

---

# 1. Overview

BuildBridge AI follows a **three-tier architecture**, separating the presentation layer, business logic layer, and data layer. This modular design improves maintainability, scalability, and team collaboration.

The application consists of:

* **Frontend (React)**
* **Backend API (Node.js + Express)**
* **Database (MongoDB)**
* **AI Service (Google Gemini API)**
* **Cloud Storage (Cloudinary)**

---

# 2. High-Level Architecture

```text
                        +----------------------+
                        |        User          |
                        +----------+-----------+
                                   |
                                   |
                         HTTP / HTTPS Requests
                                   |
                                   v
+----------------------------------------------------------+
|                  React Frontend (Vite)                   |
|----------------------------------------------------------|
| Landing Page                                             |
| Authentication                                           |
| Dashboard                                                 |
| Profile                                                   |
| Resume Upload                                             |
| Career Roadmap                                            |
| Interview Preparation                                     |
| Project Recommendations                                   |
+-------------------------+--------------------------------+
                          |
                     REST API (Axios)
                          |
                          v
+----------------------------------------------------------+
|              Express Backend (Node.js)                   |
|----------------------------------------------------------|
| Authentication                                            |
| Controllers                                               |
| Middleware                                                |
| Services                                                  |
| Gemini Integration                                        |
| Cloudinary Integration                                    |
+-----------+----------------------+------------------------+
            |                      |
            |                      |
            v                      v
+--------------------+      +-----------------------+
|     MongoDB        |      |     Gemini API        |
|--------------------|      |-----------------------|
| Users              |      | Roadmap Generation    |
| Profiles           |      | Resume Analysis       |
| Resumes            |      | Project Suggestions   |
|                    |      | Interview Questions   |
+--------------------+      +-----------------------+
            |
            |
            v
+----------------------------+
|        Cloudinary          |
|----------------------------|
| Resume PDF Storage         |
+----------------------------+
```

---

# 3. Three-Tier Architecture

## Presentation Layer (Frontend)

Responsibilities:

* Display UI
* Form Validation
* Authentication State
* Route Navigation
* API Communication
* Dashboard Rendering

Technology Stack

* React
* Tailwind CSS
* React Router
* Axios
* Framer Motion

---

## Business Logic Layer (Backend)

Responsibilities

* API Endpoints
* Authentication
* Authorization
* Validation
* Database Operations
* AI Communication
* Resume Processing

Technology Stack

* Node.js
* Express
* JWT
* bcrypt
* Multer

---

## Data Layer

Responsibilities

* Store User Data
* Store Profiles
* Store Resume Metadata
* Store AI Reports (optional)
* Data Relationships

Technology

* MongoDB
* Mongoose

---

# 4. Request Flow

```text
User

↓

React UI

↓

Axios Request

↓

Express Route

↓

Controller

↓

Service Layer

↓

MongoDB / Gemini API

↓

Controller

↓

JSON Response

↓

Frontend UI
```

---

# 5. Authentication Flow

```text
Register

↓

Validate Request

↓

Hash Password

↓

Store User

↓

Login

↓

Verify Credentials

↓

Generate JWT

↓

Return Token

↓

Frontend Stores Token

↓

Protected API Access
```

---

# 6. Career Roadmap Flow

```text
User

↓

Complete Profile

↓

Click "Generate Roadmap"

↓

POST /api/roadmap

↓

Roadmap Controller

↓

Roadmap Service

↓

Build AI Prompt

↓

Gemini API

↓

JSON Response

↓

Timeline Parser

↓

Frontend Timeline UI
```

---

# 7. Resume Analysis Flow

```text
Upload Resume

↓

Multer

↓

Cloudinary Upload

↓

Extract Resume Text

↓

Resume Prompt Builder

↓

Gemini API

↓

AI Analysis

↓

Return ATS Score

↓

Frontend Report
```

---

# 8. Project Recommendation Flow

```text
Profile

↓

Career Goal

↓

Gemini Prompt

↓

Gemini API

↓

Projects JSON

↓

Project Cards
```

---

# 9. Interview Preparation Flow

```text
Career Goal

↓

Experience Level

↓

Gemini Prompt

↓

Gemini API

↓

Questions JSON

↓

Frontend Question Cards
```

---

# 10. Backend Internal Architecture

```text
Routes

↓

Controllers

↓

Services

↓

Utilities

↓

MongoDB
```

### Responsibilities

### Routes

Receive HTTP requests.

↓

### Controllers

Validate input and call services.

↓

### Services

Business logic and AI communication.

↓

### Utilities

Helper functions.

↓

### Database

Persistent storage.

---

# 11. Frontend Internal Architecture

```text
Pages

↓

Layouts

↓

Components

↓

Hooks

↓

Services

↓

Axios

↓

Backend
```

---

# 12. AI Architecture

```text
Profile Data

↓

Prompt Builder

↓

Gemini API

↓

Structured JSON

↓

JSON Parser

↓

Reusable React Components
```

---

# 13. Data Flow Diagram

```text
                  USER
                    │
                    ▼
          React Frontend (UI)
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
     Login      Dashboard     Profile
        │           │           │
        └───────────┼───────────┘
                    │
                    ▼
            Express Backend
                    │
      ┌─────────────┼──────────────┐
      │             │              │
      ▼             ▼              ▼
 Authentication   MongoDB      Gemini API
      │             │              │
      └─────────────┼──────────────┘
                    │
                    ▼
              JSON Response
                    │
                    ▼
              React Dashboard
```

---

# 14. Deployment Architecture

```text
                 Internet
                     │
                     ▼
             Vercel Frontend
                     │
             HTTPS API Calls
                     │
                     ▼
             Render Backend
              │          │
              │          │
              ▼          ▼
        MongoDB Atlas   Gemini API
              │
              ▼
          Cloudinary
```

---

# 15. Security Architecture

### Authentication

* JWT Tokens
* Protected Routes
* Password Hashing (bcrypt)

### Validation

* Backend Request Validation
* Input Sanitization
* File Type Validation

### File Upload

* PDF Only
* Maximum File Size Limit
* Cloudinary Storage

### API Protection

* CORS
* Helmet
* Rate Limiting (optional)
* Environment Variables

---

# 16. Error Handling Flow

```text
Client Request

↓

Validation

↓

Controller

↓

Service

↓

Success?

 ├── Yes → Response
 │
 └── No
      ↓
 Error Middleware

↓

Standard JSON Error

↓

Frontend Error Toast
```

---

# 17. Scalability

The architecture is designed to support future expansion.

Possible additions include:

* AI Chat Assistant
* Resume Builder
* Admin Dashboard
* Recruiter Portal
* Learning Analytics
* Mock Interviews
* Job Recommendation Engine
* Notification Service
* Microservices Architecture
* Redis Caching

No major restructuring is required to integrate these features.

---

# 18. Architecture Principles

The project follows these design principles:

* Separation of Concerns
* Reusable Components
* RESTful API Design
* Modular Folder Structure
* Service-Oriented Business Logic
* Stateless Authentication
* Scalable AI Integration
* Maintainable Codebase

---

# 19. Summary

BuildBridge AI is designed using a clean three-tier architecture that separates user interface, business logic, and data storage. The frontend communicates with the backend through REST APIs, while the backend manages authentication, database operations, and AI interactions. Google Gemini provides intelligent career recommendations, resume analysis, project suggestions, and interview preparation, making the system modular, scalable, and suitable for both hackathon development and future production enhancements.
