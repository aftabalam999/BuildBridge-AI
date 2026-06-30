# 11 - Authentication Flow

# BuildBridge AI

## JWT Authentication & Authorization

---

# 1. Overview

BuildBridge AI uses **JWT (JSON Web Token)** based authentication to securely identify users and protect private resources.

Authentication consists of:

* User Registration
* User Login
* Password Hashing
* JWT Generation
* Protected Routes
* Authorization Middleware
* User Logout

The backend remains **stateless**, meaning it does not store active sessions.

---

# 2. Authentication Architecture

```text id="c0j1au"
             User
               │
               ▼
       React Frontend
               │
               ▼
        Authentication API
               │
               ▼
        Express Backend
               │
       ┌───────┴────────┐
       ▼                ▼
 Password Hashing    JWT Generation
       │                │
       └───────┬────────┘
               ▼
          MongoDB User
               │
               ▼
         JWT Returned
               │
               ▼
      Local Storage (Client)
               │
               ▼
      Protected API Requests
```

---

# 3. Authentication Components

## Frontend

* Login Page
* Register Page
* Auth Context
* Protected Route
* Axios Interceptor

---

## Backend

* Auth Routes
* Auth Controller
* Auth Service
* User Model
* JWT Middleware

---

# 4. Registration Flow

```text id="eewmn8"
User

↓

Register Form

↓

POST /api/auth/register

↓

Validate Input

↓

Check Existing Email

↓

Hash Password (bcrypt)

↓

Save User

↓

Generate JWT

↓

Return Token

↓

Frontend Stores Token

↓

Redirect to Dashboard
```

---

# 5. Login Flow

```text id="hy4jlwm"
User

↓

Login Form

↓

POST /api/auth/login

↓

Validate Email

↓

Compare Password

↓

Generate JWT

↓

Return Token

↓

Save Token

↓

Dashboard
```

---

# 6. Logout Flow

```text id="l56shm"
Logout Button

↓

Remove JWT

↓

Clear Auth Context

↓

Redirect to Login
```

Since JWT authentication is stateless, logout is handled entirely on the client by removing the stored token.

---

# 7. JWT Structure

A JWT contains three sections:

```text id="ysl6qa"
Header

↓

Payload

↓

Signature
```

### Payload Example

```json id="8w1zsv"
{
  "userId": "665fa0c3...",
  "email": "john@example.com",
  "role": "student"
}
```

Sensitive information such as passwords must **never** be included in the token.

---

# 8. Password Security

Passwords are hashed before storage.

```text id="mjqe7h"
Password

↓

bcrypt.hash()

↓

Hashed Password

↓

MongoDB
```

During login:

```text id="wdifcb"
Entered Password

↓

bcrypt.compare()

↓

Match?

↓

Login Success / Failure
```

Plain-text passwords are never stored or logged.

---

# 9. Protected Route Flow (Frontend)

```text id="8b88lx"
User

↓

ProtectedRoute

↓

Token Exists?

├── Yes
│
│    ▼
│ Dashboard
│
└── No
     ▼
Login Page
```

Only authenticated users can access:

* Dashboard
* Profile
* Roadmap
* Resume
* Projects
* Interview

---

# 10. Protected API Flow (Backend)

```text id="6y9tfy"
Incoming Request

↓

Authorization Header

↓

Extract Token

↓

Verify JWT

↓

Attach User to Request

↓

Continue

↓

Controller
```

If verification fails:

```text id="1txv3q"
401 Unauthorized
```

---

# 11. Authorization Header

Every protected request includes:

```http id="ad9c0i"
Authorization: Bearer <JWT_TOKEN>
```

Example:

```http id="hprjpj"
GET /api/profile
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

---

# 12. Authentication Middleware

Responsibilities:

* Read Authorization header
* Extract JWT
* Verify signature
* Decode payload
* Attach authenticated user to `req.user`
* Reject invalid tokens

```text id="ddpv53"
Request

↓

JWT Middleware

↓

Token Valid?

├── Yes
│
│    ▼
│ Controller
│
└── No
     ▼
401 Unauthorized
```

---

# 13. Axios Authentication Flow

All API requests use a centralized Axios instance.

```text id="12p5zd"
React Component

↓

Axios Instance

↓

Read Token

↓

Attach Authorization Header

↓

Backend API
```

This avoids manually adding tokens to every request.

---

# 14. Authentication State

Global authentication state is managed using **React Context API**.

Stored information:

```text id="d0p8if"
User

Token

isAuthenticated

Loading State
```

Available methods:

* login()
* logout()
* register()
* fetchCurrentUser()

---

# 15. Authentication Sequence Diagram

```text id="qz7bqz"
User
 │
 │ Register/Login
 ▼
Frontend
 │
 │ POST Request
 ▼
Backend
 │
 │ Validate
 ▼
MongoDB
 │
 │ User Found?
 ▼
JWT
 │
 │ Generate Token
 ▼
Frontend
 │
 │ Store Token
 ▼
Dashboard
```

---

# 16. Error Handling

Common authentication errors:

| Status | Description               |
| ------ | ------------------------- |
| 400    | Invalid request data      |
| 401    | Invalid email or password |
| 401    | Missing token             |
| 401    | Expired token             |
| 403    | Unauthorized access       |
| 409    | Email already exists      |
| 500    | Internal server error     |

Example response:

```json id="l2kqne"
{
  "success": false,
  "message": "Invalid credentials"
}
```

---

# 17. Security Best Practices

* Hash passwords using bcrypt.
* Never store plain-text passwords.
* Keep JWT secret in environment variables.
* Validate all authentication requests.
* Use HTTPS in production.
* Set token expiration (e.g., 7 days).
* Never expose secrets to the frontend.
* Sanitize user input.
* Return generic login errors to avoid user enumeration.

---

# 18. Future Improvements

The current authentication system is suitable for the MVP.

Future enhancements may include:

* Refresh Tokens
* OAuth (Google / GitHub)
* Email Verification
* Password Reset
* Multi-Factor Authentication (MFA)
* Role-Based Access Control (RBAC)
* Session Management
* Device Tracking

---

# 19. Authentication Folder Structure

```text id="n53svw"
server/src/

├── controllers/
│   └── authController.js
│
├── routes/
│   └── authRoutes.js
│
├── services/
│   └── authService.js
│
├── middleware/
│   └── authMiddleware.js
│
├── models/
│   └── User.js
│
└── validators/
    └── authValidator.js
```

Frontend:

```text id="q4t6cw"
client/src/

├── pages/
│   ├── Login.jsx
│   └── Register.jsx
│
├── context/
│   └── AuthContext.jsx
│
├── routes/
│   └── ProtectedRoute.jsx
│
└── services/
    └── authService.js
```

---

# 20. Summary

BuildBridge AI uses a stateless JWT authentication system with bcrypt password hashing and centralized authentication middleware. After successful registration or login, the backend issues a signed JWT that the frontend stores and includes in the `Authorization` header for all protected requests. React Context manages authentication state, while Express middleware validates tokens and authorizes access to secured endpoints. This architecture is lightweight, secure for an MVP, and easily extensible with features such as refresh tokens, OAuth, or role-based authorization in future versions.
