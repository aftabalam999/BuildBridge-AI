# 🚀 BuildBridge AI

> **AI-Powered Career Mentor for Students & Freshers**

BuildBridge AI is an intelligent career guidance platform that helps students and early-career professionals identify their career path, generate personalized learning roadmaps, improve their resumes using AI, discover project ideas, and prepare for interviews—all from a single platform.

---

# 📌 Problem Statement

Many students graduate without a clear career direction. They often struggle with questions like:

* Which career should I choose?
* What skills should I learn next?
* Which projects will strengthen my portfolio?
* Is my resume ATS-friendly?
* How should I prepare for interviews?

Most available resources solve only one of these problems. Students must switch between multiple platforms, making career planning fragmented and inefficient.

---

# 💡 Solution

BuildBridge AI centralizes career guidance into a single AI-powered platform.

Using Generative AI, it analyzes a user's profile and provides:

* Personalized career roadmap
* Resume analysis
* Project recommendations
* Learning resources
* Interview preparation

---

# 🎯 Objectives

* Help students discover suitable career paths.
* Generate personalized learning roadmaps.
* Improve resume quality using AI.
* Recommend practical portfolio projects.
* Prepare users for technical interviews.
* Simplify career planning through automation.

---

# ✨ MVP Features

### Authentication

* User Registration
* User Login
* JWT Authentication
* Protected Routes

### Profile

* Personal Information
* Education
* Skills
* Career Goal
* GitHub
* LinkedIn

### AI Career Roadmap

Generate a personalized roadmap based on:

* Skills
* Interests
* Career Goal
* Experience Level

### Resume Review

Upload a resume and receive:

* ATS Score
* Strengths
* Weaknesses
* Improvement Suggestions

### AI Project Recommendations

Generate portfolio projects based on the user's target career.

Each recommendation includes:

* Title
* Difficulty
* Technologies
* Estimated Duration
* Learning Outcomes

### AI Interview Preparation

Generate interview questions categorized by:

* Beginner
* Intermediate
* Advanced

---

# 🛠 Tech Stack

## Frontend

* React.js
* Vite
* Tailwind CSS
* React Router
* Framer Motion
* Axios

## Backend

* Node.js
* Express.js

## Database

* MongoDB
* Mongoose

## Authentication

* JWT
* bcrypt

## AI

* Google Gemini API

## File Storage

* Cloudinary

---

# 📂 Project Structure

```text
BuildBridge-AI/
│
├── docs/
├── client/
├── server/
│
├── README.md
└── package.json
```

Detailed architecture documentation is available inside the **docs/** directory.

---

# 👨‍💻 Team Roles

## Frontend Developer

Responsible for:

* UI Development
* Responsive Design
* React Components
* Dashboard
* API Integration

---

## Backend Developer

Responsible for:

* REST APIs
* MongoDB
* Authentication
* Middleware
* Controllers

---

## AI Developer

Responsible for:

* Gemini Integration
* Prompt Engineering
* Resume Analysis
* Career Roadmap Generation
* Interview Question Generation

---

# 🚀 User Flow

```text
Landing Page

↓

Register / Login

↓

Complete Profile

↓

Dashboard

↓

Generate Career Roadmap

↓

AI Analysis

↓

Roadmap

↓

Resume Review

↓

Project Suggestions

↓

Interview Questions
```

---

# 📄 Documentation

Detailed project documentation is available in the **docs/** folder.

* Project Overview
* Features
* Tech Stack
* Folder Structure
* Frontend Architecture
* Backend Architecture
* Database Schema
* API Documentation
* AI Architecture
* Authentication Flow
* Routing
* Component Tree
* Deployment Guide
* Team Workflow

---

# 🚀 Local Setup

## Clone Repository

```bash
git clone https://github.com/your-username/BuildBridge-AI.git

cd BuildBridge-AI
```

---

## Install Frontend

```bash
cd client

npm install

npm run dev
```

---

## Install Backend

```bash
cd server

npm install

npm run dev
```

---

# 🔐 Environment Variables

Create a `.env` file inside the **server** folder.

```env
PORT=

MONGO_URI=

JWT_SECRET=

GEMINI_API_KEY=

CLOUDINARY_NAME=

CLOUDINARY_API_KEY=

CLOUDINARY_API_SECRET=
```

---

# 📦 Planned Features

* Roadmap History
* Resume Versioning
* Mock Interview Sessions
* AI Chat Career Mentor
* Resume Builder
* Skill Progress Tracking
* Learning Streaks
* Portfolio Generator

---

# 🤝 Contributing

1. Create a feature branch.
2. Implement the feature.
3. Test thoroughly.
4. Submit a Pull Request.

---

# 📜 License

This project is developed for educational purposes and hackathons.

---

# 👥 Authors

BuildBridge AI Team

* Frontend Developer
* Backend Developer
* AI Developer

---

# ⭐ Project Status

**Current Version:** MVP

**Development Status:** Active

---

> **BuildBridge AI — Empowering students with AI-driven career guidance.**
