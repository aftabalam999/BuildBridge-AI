# 07 - Backend Architecture

# BuildBridge AI

## Express Backend Architecture Documentation

---

# 1. Overview

The backend of BuildBridge AI is built using **Node.js**, **Express.js**, and **MongoDB** following a layered architecture.

The architecture separates responsibilities into:

* Routes
* Controllers
* Services
* Models
* Middleware
* Validators
* Utilities
* AI Prompt Templates
* Configuration

This separation keeps the codebase modular, testable, and easy to extend.

---

# 2. Technology Stack

| Technology        | Purpose               |
| ----------------- | --------------------- |
| Node.js           | Runtime Environment   |
| Express.js        | REST API Framework    |
| MongoDB           | Database              |
| Mongoose          | ODM                   |
| JWT               | Authentication        |
| bcrypt            | Password Hashing      |
| Multer            | File Upload           |
| Cloudinary        | Resume Storage        |
| Google Gemini API | AI Services           |
| dotenv            | Environment Variables |

---

# 3. Backend Directory Structure

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
│   │
│   ├── app.js
│   └── server.js
│
├── package.json
└── .env
```

---

# 4. Request Lifecycle

Every request follows the same processing pipeline.

```text
Client Request

↓

Express Route

↓

Authentication Middleware

↓

Validation Middleware

↓

Controller

↓

Service Layer

↓

Database / Gemini API

↓

Controller

↓

JSON Response

↓

Frontend
```

---

# 5. Layered Architecture

```text
Routes

↓

Controllers

↓

Services

↓

Models

↓

MongoDB
```

External services (Gemini, Cloudinary) are accessed only through the **Service Layer**.

---

# 6. Route Layer

**Responsibility**

* Define API endpoints
* Attach middleware
* Forward requests to controllers

### Example

```text
POST /api/auth/login

↓

authController.login
```

Routes contain **no business logic**.

---

# 7. Controller Layer

**Responsibility**

* Receive requests
* Validate required parameters
* Call the appropriate service
* Return standardized JSON responses

Controllers should remain thin.

### Good Controller

```text
Receive Request

↓

Call Service

↓

Return Response
```

Controllers should **not**:

* Write database queries
* Build AI prompts
* Implement business rules

---

# 8. Service Layer

The **Service Layer** contains all business logic.

Responsibilities include:

* MongoDB operations
* Gemini API communication
* Resume processing
* Prompt generation
* Data transformation
* Cloudinary uploads

Example services:

```text
Auth Service

Profile Service

Roadmap Service

Resume Service

Interview Service

Project Service
```

Every controller communicates with services instead of directly accessing models.

---

# 9. Model Layer

Each MongoDB collection has its own model.

```text
models/

├── User.js
├── Profile.js
└── Resume.js
```

Models define:

* Schema
* Validation
* Relationships
* Indexes
* Default Values

Business logic should not be placed inside models.

---

# 10. Middleware Layer

Middleware handles cross-cutting concerns before a request reaches the controller.

## Authentication Middleware

Responsibilities

* Verify JWT
* Extract user information
* Attach user to request

---

## Upload Middleware

Responsibilities

* Accept PDF files
* Validate file size
* Store temporary files

---

## Error Middleware

Responsibilities

* Catch unhandled exceptions
* Return standardized error responses

---

## Not Found Middleware

Handles unknown API routes.

---

# 11. Validator Layer

All request validation should be centralized.

Examples

```text
validators/

├── authValidator.js
├── profileValidator.js
├── roadmapValidator.js
└── resumeValidator.js
```

Responsibilities

* Required fields
* Email validation
* Password validation
* File validation
* Input sanitization

---

# 12. Utility Layer

Contains reusable helper functions.

Examples

```text
utils/

├── asyncHandler.js
├── response.js
├── logger.js
└── formatter.js
```

Responsibilities

* Async wrappers
* Standard API responses
* Logging
* Formatting

---

# 13. Configuration Layer

All external service configuration is centralized.

```text
config/

├── db.js
├── gemini.js
└── cloudinary.js
```

Responsibilities

* MongoDB connection
* Gemini client initialization
* Cloudinary configuration

---

# 14. AI Prompt Layer

All AI prompts are isolated from business logic.

```text
prompts/

├── roadmapPrompt.js
├── resumePrompt.js
├── interviewPrompt.js
└── projectPrompt.js
```

Benefits

* Easier prompt tuning
* Cleaner controllers
* Reusable prompt templates

---

# 15. Database Flow

```text
Controller

↓

Service

↓

Model

↓

MongoDB

↓

Model

↓

Service

↓

Controller
```

No controller should communicate directly with MongoDB.

---

# 16. Gemini AI Flow

```text
User Request

↓

Controller

↓

Service

↓

Prompt Builder

↓

Gemini API

↓

Structured JSON

↓

Service

↓

Controller

↓

Frontend
```

Gemini should always return structured JSON instead of free-form text to simplify parsing on the frontend.

---

# 17. Resume Upload Flow

```text
Upload Resume

↓

Multer

↓

Temporary Storage

↓

Cloudinary Upload

↓

Extract Resume Text

↓

Gemini Analysis

↓

AI Report

↓

Frontend
```

---

# 18. Authentication Flow

```text
Register

↓

Validate Request

↓

Hash Password

↓

Save User

↓

Login

↓

Verify Password

↓

Generate JWT

↓

Return Token
```

Protected endpoints verify the JWT before executing business logic.

---

# 19. Error Handling

All backend errors return a consistent JSON structure.

### Success Response

```json
{
  "success": true,
  "message": "Operation successful",
  "data": {}
}
```

### Error Response

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": []
}
```

This consistency simplifies frontend integration.

---

# 20. Security Practices

The backend follows these security guidelines:

* Passwords hashed using bcrypt.
* JWT authentication for protected routes.
* Environment variables for secrets.
* Input validation on every request.
* File type and size restrictions.
* Centralized error handling.
* CORS configuration.
* HTTP security headers (Helmet).
* Request rate limiting (optional).

---

# 21. Backend Responsibilities by Module

| Module      | Responsibility                  |
| ----------- | ------------------------------- |
| Routes      | API endpoints                   |
| Controllers | Request handling                |
| Services    | Business logic                  |
| Models      | Database schema                 |
| Middleware  | Authentication, uploads, errors |
| Validators  | Request validation              |
| Config      | External services               |
| Prompts     | AI prompt templates             |
| Utils       | Helper functions                |

---

# 22. Coding Guidelines

* One responsibility per file.
* Controllers must remain thin.
* Services contain business logic.
* Models contain only schema definitions.
* AI prompts must remain inside the `prompts` directory.
* Never duplicate validation logic.
* Keep response structures consistent.
* Avoid direct database access from routes or controllers.

---

# 23. Future Scalability

The architecture is designed to support future expansion without major restructuring.

Potential additions include:

* AI Chat Mentor
* Resume Builder
* Mock Interview Engine
* Admin Dashboard
* Recruiter Portal
* Job Recommendation Engine
* Redis Caching
* Background Jobs
* Microservices
* WebSocket Notifications

---

# 24. Summary

The BuildBridge AI backend follows a layered Express architecture that cleanly separates routing, controllers, services, models, middleware, and AI integrations. This approach improves readability, testability, and maintainability while allowing frontend, backend, and AI developers to work independently. The service-oriented design also makes it straightforward to introduce new features or external integrations without significant architectural changes.
