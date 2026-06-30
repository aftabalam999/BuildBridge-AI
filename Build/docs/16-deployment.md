# 16 - Deployment

# BuildBridge AI

## Deployment Documentation

---

# 1. Overview

BuildBridge AI follows a modern cloud deployment architecture.

The application is divided into independent services:

* **Frontend** → Vercel
* **Backend** → Render
* **Database** → MongoDB Atlas
* **Resume Storage** → Cloudinary
* **AI Service** → Google Gemini API

This separation allows each service to scale independently and simplifies deployment.

---

# 2. Deployment Architecture

```text
                    Internet
                        │
                        ▼
                 BuildBridge AI
                        │
        ┌───────────────┼────────────────┐
        │               │                │
        ▼               ▼                ▼
   Vercel          Render API      MongoDB Atlas
 (React App)      (Express API)     (Database)
        │               │
        │               │
        └───────┬───────┘
                │
        ┌───────┴────────┐
        ▼                ▼
 Cloudinary         Gemini API
 Resume Storage      AI Services
```

---

# 3. Deployment Stack

| Service         | Platform          |
| --------------- | ----------------- |
| Frontend        | Vercel            |
| Backend         | Render            |
| Database        | MongoDB Atlas     |
| File Storage    | Cloudinary        |
| AI              | Google Gemini API |
| Version Control | GitHub            |

---

# 4. Deployment Flow

```text
Developer

↓

GitHub Repository

↓

Push Code

↓

Vercel / Render

↓

Automatic Build

↓

Production Deployment
```

---

# 5. Frontend Deployment (Vercel)

## Prerequisites

* GitHub Repository
* Vercel Account

---

### Step 1

Push the frontend code to GitHub.

---

### Step 2

Login to Vercel.

https://vercel.com

---

### Step 3

Import the GitHub repository.

---

### Step 4

Configure:

Framework

```
Vite
```

Root Directory

```
client
```

Build Command

```
npm run build
```

Output Directory

```
dist
```

---

### Step 5

Add Environment Variables

```env
VITE_API_BASE_URL=https://your-backend.onrender.com/api
```

---

### Step 6

Click

```
Deploy
```

Vercel automatically builds and hosts the React application.

---

# 6. Backend Deployment (Render)

## Prerequisites

* GitHub Repository
* Render Account

---

### Step 1

Create

```
New Web Service
```

---

### Step 2

Connect GitHub repository.

---

### Step 3

Select

```
server
```

folder.

---

### Step 4

Configuration

Build Command

```
npm install
```

Start Command

```
npm start
```

Root Directory

```
server
```

---

### Step 5

Environment Variables

```env
PORT=5000

NODE_ENV=production

MONGO_URI=

JWT_SECRET=

JWT_EXPIRES_IN=7d

GEMINI_API_KEY=

CLOUDINARY_CLOUD_NAME=

CLOUDINARY_API_KEY=

CLOUDINARY_API_SECRET=

CLIENT_URL=https://your-frontend.vercel.app
```

---

### Step 6

Deploy.

Render automatically rebuilds the backend after every GitHub push.

---

# 7. MongoDB Atlas

### Step 1

Create a MongoDB Atlas Cluster.

---

### Step 2

Create a database user.

---

### Step 3

Allow network access.

Development

```
0.0.0.0/0
```

Production

Whitelist only trusted IPs if possible.

---

### Step 4

Copy the connection string.

Example

```text
mongodb+srv://username:password@cluster.mongodb.net/buildbridge
```

---

### Step 5

Store inside

```
MONGO_URI
```

---

# 8. Cloudinary Setup

Create an account.

Obtain

* Cloud Name
* API Key
* API Secret

Add them to the backend environment variables.

Cloudinary is used to:

* Store uploaded resumes
* Generate secure file URLs
* Avoid storing files locally

---

# 9. Google Gemini Setup

Create a Google AI Studio account.

Generate an API Key.

Store it securely.

```env
GEMINI_API_KEY=
```

Never expose this key in the frontend.

---

# 10. Production Environment Variables

## Backend

```env
PORT=5000

NODE_ENV=production

MONGO_URI=

JWT_SECRET=

JWT_EXPIRES_IN=7d

CLIENT_URL=https://your-frontend.vercel.app

GEMINI_API_KEY=

CLOUDINARY_CLOUD_NAME=

CLOUDINARY_API_KEY=

CLOUDINARY_API_SECRET=
```

---

## Frontend

```env
VITE_API_BASE_URL=https://your-backend.onrender.com/api
```

---

# 11. Deployment Checklist

## Frontend

* GitHub Connected
* Build Successful
* Environment Variables Added
* API URL Updated
* Responsive UI Verified

---

## Backend

* MongoDB Connected
* Environment Variables Added
* CORS Configured
* JWT Working
* Gemini Connected
* Cloudinary Connected

---

## Database

* Collections Created
* Indexes Applied
* User Authentication Tested

---

# 12. CORS Configuration

Allow only the frontend domain.

Example

```javascript
origin: [
    "http://localhost:5173",
    "https://your-app.vercel.app"
]
```

---

# 13. Production Security

Before deployment ensure:

* HTTPS enabled
* Environment variables secured
* Passwords hashed
* JWT secret is strong
* API keys never committed
* CORS restricted
* File upload validation enabled
* Request validation enabled

---

# 14. CI/CD Workflow

```text
Developer

↓

Git Commit

↓

Git Push

↓

GitHub

↓

Vercel / Render

↓

Automatic Build

↓

Automatic Deployment

↓

Production
```

No manual deployment is required after the initial setup.

---

# 15. Monitoring

Recommended tools:

* Render Logs
* Vercel Analytics
* MongoDB Atlas Monitoring
* Cloudinary Dashboard
* Google AI Usage Dashboard

Monitor:

* API Errors
* Response Times
* Storage Usage
* AI Token Usage
* Database Connections

---

# 16. Troubleshooting

### Backend not starting

* Verify environment variables.
* Check MongoDB connection.
* Review Render logs.

---

### Frontend cannot connect to backend

* Verify `VITE_API_BASE_URL`.
* Confirm CORS configuration.
* Ensure backend is running.

---

### Gemini errors

* Check API key.
* Verify quota limits.
* Review request payload.

---

### Resume upload issues

* Verify Cloudinary credentials.
* Confirm file size limit.
* Ensure PDF format validation.

---

# 17. Future Deployment Improvements

As the application grows, the deployment architecture can be enhanced with:

* Docker containerization
* Nginx reverse proxy
* Redis caching
* CDN for static assets
* GitHub Actions CI/CD
* Kubernetes orchestration
* Monitoring with Prometheus & Grafana
* Centralized logging

---

# 18. Production Architecture

```text
                     Users
                       │
                       ▼
                Vercel Frontend
                       │
                HTTPS REST API
                       │
                       ▼
                 Render Backend
              ┌────────┼────────┐
              │        │        │
              ▼        ▼        ▼
      MongoDB Atlas  Gemini API  Cloudinary
```

---

# 19. Summary

BuildBridge AI is deployed using a cloud-native architecture. The React frontend is hosted on Vercel, the Express backend runs on Render, MongoDB Atlas manages persistent data, Cloudinary stores uploaded resumes, and Google Gemini powers AI functionality. Automatic deployments from GitHub ensure a streamlined CI/CD workflow, while environment variables and secure configuration keep production deployments reliable and maintainable.
