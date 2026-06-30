# 09 - API Documentation

# BuildBridge AI

## REST API Documentation

**Base URL**

```text
http://localhost:5000/api
```

---

# API Standards

## Request Format

All requests must use:

```http
Content-Type: application/json
```

For file uploads:

```http
Content-Type: multipart/form-data
```

---

## Authentication

Protected endpoints require a JWT token.

```http
Authorization: Bearer <JWT_TOKEN>
```

---

## Standard Success Response

```json
{
  "success": true,
  "message": "Operation successful",
  "data": {}
}
```

---

## Standard Error Response

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": []
}
```

---

# API Modules

```text
Authentication

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

# 1. Authentication APIs

---

## Register User

### Endpoint

```http
POST /auth/register
```

### Authentication

Not Required

### Request Body

```json
{
  "fullName": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

### Validation

* Full Name required
* Email required
* Email unique
* Password minimum 8 characters

### Success Response

```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "token": "JWT_TOKEN",
    "user": {
      "_id": "...",
      "fullName": "John Doe",
      "email": "john@example.com"
    }
  }
}
```

### Error Codes

| Code | Description          |
| ---- | -------------------- |
| 400  | Validation Error     |
| 409  | Email Already Exists |
| 500  | Server Error         |

---

## Login

### Endpoint

```http
POST /auth/login
```

### Authentication

Not Required

### Request

```json
{
  "email": "john@example.com",
  "password": "password123"
}
```

### Success

```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "token": "JWT_TOKEN",
    "user": {}
  }
}
```

### Error Codes

| Code | Description         |
| ---- | ------------------- |
| 400  | Invalid Request     |
| 401  | Invalid Credentials |

---

## Get Current User

### Endpoint

```http
GET /auth/me
```

### Authentication

Required

### Response

```json
{
  "success": true,
  "data": {
    "_id": "...",
    "fullName": "John Doe",
    "email": "john@example.com"
  }
}
```

---

# 2. Profile APIs

---

## Get Profile

### Endpoint

```http
GET /profile
```

Authentication Required

---

## Update Profile

### Endpoint

```http
PUT /profile
```

### Request

```json
{
  "education": "B.Tech",
  "college": "ABC University",
  "degree": "Computer Science",
  "graduationYear": 2027,
  "experienceLevel": "Beginner",
  "skills": [
    "React",
    "Node.js"
  ],
  "interests": [
    "Web Development"
  ],
  "careerGoal": "Full Stack Developer",
  "github": "https://github.com/user",
  "linkedin": "https://linkedin.com/in/user",
  "portfolio": "https://portfolio.com",
  "bio": "Aspiring Full Stack Developer"
}
```

### Success Response

```json
{
  "success": true,
  "message": "Profile updated successfully"
}
```

---

# 3. Career Roadmap APIs

---

## Generate Roadmap

### Endpoint

```http
POST /roadmap
```

Authentication Required

### Request

```json
{
  "careerGoal": "Full Stack Developer"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "summary": "...",
    "duration": "6 Months",
    "milestones": [
      {
        "title": "Learn HTML & CSS",
        "description": "...",
        "technologies": [
          "HTML",
          "CSS"
        ],
        "resources": [
          "MDN",
          "freeCodeCamp"
        ]
      }
    ],
    "projects": [
      {
        "title": "Portfolio Website",
        "difficulty": "Easy",
        "technologies": [
          "HTML",
          "CSS",
          "JavaScript"
        ]
      }
    ]
  }
}
```

---

## Get Saved Roadmaps

### Endpoint

```http
GET /roadmap
```

Returns all generated roadmaps for the authenticated user.

---

## Get Roadmap by ID

```http
GET /roadmap/:id
```

---

## Delete Roadmap

```http
DELETE /roadmap/:id
```

---

# 4. Resume APIs

---

## Upload Resume

### Endpoint

```http
POST /resume
```

### Authentication

Required

### Content Type

```http
multipart/form-data
```

### Form Data

```text
resume : PDF File
```

### Response

```json
{
  "success": true,
  "message": "Resume uploaded successfully",
  "data": {
    "resumeId": "...",
    "fileUrl": "https://..."
  }
}
```

---

## Analyze Resume

### Endpoint

```http
POST /resume/analyze
```

### Response

```json
{
  "success": true,
  "data": {
    "atsScore": 87,
    "strengths": [],
    "weaknesses": [],
    "missingKeywords": [],
    "suggestions": []
  }
}
```

---

## Get Resume History

```http
GET /resume
```

---

## Delete Resume

```http
DELETE /resume/:id
```

---

# 5. Project Recommendation APIs

---

## Generate Projects

### Endpoint

```http
POST /projects
```

### Request

```json
{
  "careerGoal": "Frontend Developer"
}
```

### Response

```json
{
  "success": true,
  "data": [
    {
      "title": "Weather Dashboard",
      "difficulty": "Intermediate",
      "technologies": [
        "React",
        "Tailwind CSS"
      ],
      "estimatedDuration": "5 Days",
      "learningOutcomes": [
        "API Integration",
        "State Management"
      ]
    }
  ]
}
```

---

# 6. Interview APIs

---

## Generate Interview Questions

### Endpoint

```http
POST /interview
```

### Request

```json
{
  "careerGoal": "Backend Developer",
  "difficulty": "Intermediate"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "questions": [
      {
        "question": "Explain middleware in Express.js.",
        "answer": "...",
        "tips": "..."
      }
    ]
  }
}
```

---

# API Status Codes

| Status | Meaning               |
| ------ | --------------------- |
| 200    | Success               |
| 201    | Resource Created      |
| 400    | Bad Request           |
| 401    | Unauthorized          |
| 403    | Forbidden             |
| 404    | Not Found             |
| 409    | Conflict              |
| 422    | Validation Error      |
| 500    | Internal Server Error |

---

# Validation Rules

## User

* Email must be unique.
* Password minimum 8 characters.
* Name cannot be empty.

---

## Profile

* Career goal is required.
* Skills array must not be empty.
* Graduation year must be valid.

---

## Resume

* Only PDF files.
* Maximum size: 5 MB.

---

## AI Requests

* User profile must exist before generating a roadmap.
* Resume must be uploaded before analysis.
* Career goal is mandatory for project and interview generation.

---

# API Workflow

```text
React Component
        │
        ▼
Axios Service
        │
        ▼
Express Route
        │
        ▼
Controller
        │
        ▼
Service Layer
        │
   ┌────┴────┐
   ▼         ▼
MongoDB   Gemini API
   │         │
   └────┬────┘
        ▼
JSON Response
        │
        ▼
React UI
```

---

# Endpoint Summary

| Method | Endpoint        | Authentication |
| ------ | --------------- | -------------- |
| POST   | /auth/register  | No             |
| POST   | /auth/login     | No             |
| GET    | /auth/me        | Yes            |
| GET    | /profile        | Yes            |
| PUT    | /profile        | Yes            |
| POST   | /roadmap        | Yes            |
| GET    | /roadmap        | Yes            |
| GET    | /roadmap/:id    | Yes            |
| DELETE | /roadmap/:id    | Yes            |
| POST   | /resume         | Yes            |
| POST   | /resume/analyze | Yes            |
| GET    | /resume         | Yes            |
| DELETE | /resume/:id     | Yes            |
| POST   | /projects       | Yes            |
| POST   | /interview      | Yes            |

---

# API Design Principles

* RESTful endpoint naming.
* Stateless authentication using JWT.
* Consistent JSON response format.
* Validation before business logic.
* Controllers remain thin; services contain business logic.
* AI interactions isolated in the service layer.
* Standardized error handling across all endpoints.

---

# Summary

The BuildBridge AI API exposes a clean REST interface for authentication, profile management, AI roadmap generation, resume analysis, project recommendations, and interview preparation. Each endpoint follows a consistent request/response structure, enabling the frontend, backend, and AI modules to evolve independently while maintaining a stable integration contract.
