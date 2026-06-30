# 02 - Features

# BuildBridge AI

## Feature Documentation

---

# 1. MVP Overview

The Minimum Viable Product (MVP) focuses on solving the core problem of career guidance using Artificial Intelligence. The goal is to deliver a fully functional application with essential features that demonstrate the value of the platform while remaining achievable within the hackathon timeline.

---

# 2. MVP Features

## 2.1 Landing Page

### Description

The landing page introduces BuildBridge AI and explains how it helps students with career planning.

### Functionalities

* Responsive Navigation Bar
* Hero Section
* Features Section
* How It Works
* Career Domains
* Frequently Asked Questions
* Call-to-Action
* Footer

### User Goal

Understand the platform and encourage registration.

---

## 2.2 User Authentication

### Description

Allows users to securely create an account and log in.

### Functionalities

* Register
* Login
* Logout
* JWT Authentication
* Protected Routes
* Password Encryption

### User Goal

Secure access to personalized AI features.

---

## 2.3 User Profile

### Description

Stores information required for AI recommendations.

### Profile Information

* Full Name
* Email
* Education
* Degree
* College
* Graduation Year
* Skills
* Interests
* Career Goal
* GitHub Profile
* LinkedIn Profile

### User Goal

Provide sufficient information for AI analysis.

---

## 2.4 AI Career Roadmap

### Description

Generates a personalized learning roadmap using Gemini AI.

### AI Input

* Education
* Skills
* Interests
* Career Goal
* Experience Level

### AI Output

* Career Summary
* Learning Milestones
* Required Technologies
* Recommended Courses
* Portfolio Projects
* Estimated Timeline

### User Goal

Understand exactly what to learn next.

---

## 2.5 Resume Analysis

### Description

Allows users to upload their resume for AI review.

### Functionalities

* Resume Upload
* Resume Parsing
* ATS Score Estimate
* Resume Feedback

### AI Suggestions

* Strengths
* Weaknesses
* Missing Keywords
* Formatting Issues
* Improvement Suggestions

### User Goal

Improve resume quality before applying for jobs.

---

## 2.6 AI Project Recommendations

### Description

Generate portfolio project ideas based on career goals.

### AI Output

Each recommendation contains:

* Project Title
* Description
* Difficulty
* Technologies
* Estimated Duration
* Learning Outcomes
* Implementation Steps

### User Goal

Build relevant portfolio projects.

---

## 2.7 AI Interview Preparation

### Description

Generate interview questions based on selected career path.

### Categories

* Beginner
* Intermediate
* Advanced

### AI Output

* Question
* Expected Answer
* Explanation
* Tips

### User Goal

Practice interviews efficiently.

---

## 2.8 Dashboard

### Description

Centralized workspace after login.

### Dashboard Widgets

* Welcome Card
* Profile Completion
* AI Roadmap Preview
* Resume Analysis Summary
* Project Recommendations
* Interview Preparation
* Learning Progress (UI Placeholder)

### User Goal

Access all career guidance features from one location.

---

# 3. User Stories

## Authentication

### Story 1

As a new user,

I want to create an account,

so that I can access personalized career guidance.

---

### Story 2

As a registered user,

I want to log in securely,

so that my data remains private.

---

## Profile

### Story 3

As a student,

I want to complete my profile,

so the AI can generate personalized recommendations.

---

## Career Roadmap

### Story 4

As a learner,

I want AI to generate a roadmap,

so I know exactly what to study next.

---

## Resume Review

### Story 5

As a job seeker,

I want AI to analyze my resume,

so I can improve my chances of getting shortlisted.

---

## Project Suggestions

### Story 6

As a beginner developer,

I want project recommendations,

so I can build a stronger portfolio.

---

## Interview Preparation

### Story 7

As a candidate,

I want interview questions,

so I can prepare confidently.

---

## Dashboard

### Story 8

As a user,

I want all my career information in one place,

so I can track my progress easily.

---

# 4. User Flow

```text
Landing Page

↓

Register / Login

↓

Complete Profile

↓

Dashboard

↓

Generate AI Career Roadmap

↓

Resume Upload

↓

AI Resume Analysis

↓

AI Project Suggestions

↓

Interview Preparation
```

---

# 5. Feature Priority

## High Priority (MVP)

* Landing Page
* User Authentication
* User Profile
* AI Career Roadmap
* Resume Upload
* Resume Analysis
* AI Project Recommendations
* AI Interview Questions
* Responsive Dashboard

---

## Medium Priority

* Roadmap History
* Saved Resume Reports
* Download AI Report (PDF)
* Dark/Light Theme
* Profile Completion Progress

---

## Low Priority

* Community Forum
* Leaderboard
* Mentor System
* Company Preparation
* Notifications

---

# 6. Features Excluded from MVP

The following features are intentionally excluded from the hackathon version to maintain focus on the core experience:

* Skill Gap Detection
* Skill Assessment Tests
* Certificate Organizer
* Recruiter Dashboard
* Analytics Dashboard
* Notification System
* Discussion Forum
* Referral System
* Admin Dashboard
* Live Chat
* Learning Progress Tracking
* Resume Version History

---

# 7. Future Scope

After the MVP, the platform can be extended with additional capabilities.

## AI Career Chatbot

A conversational AI mentor that answers career-related questions.

---

## Resume Builder

Generate professional ATS-friendly resumes directly within the platform.

---

## Mock Interviews

Interactive AI-powered interview sessions with feedback.

---

## Progress Tracking

Track completed milestones, projects, and learning progress.

---

## Roadmap History

Allow users to save and revisit multiple career roadmaps.

---

## Learning Dashboard

Visualize learning progress through charts and statistics.

---

## Job Recommendation Engine

Recommend internships and jobs based on the user's profile and roadmap.

---

## Portfolio Generator

Automatically create a personal portfolio website from completed projects.

---

## Mentor Connect

Allow users to connect with experienced professionals for mentorship.

---

## Community

Discussion forums where students can collaborate, ask questions, and share resources.

---

# 8. Success Metrics

The MVP will be considered successful if users can:

* Register and log in successfully.
* Complete their profile.
* Generate an AI career roadmap.
* Upload a resume and receive AI feedback.
* Receive personalized project recommendations.
* Practice interview questions.
* Navigate the application smoothly on desktop and mobile devices.

---

# 9. Summary

The MVP focuses on delivering the highest-value AI features for students and fresh graduates while maintaining a clean, scalable architecture. Non-essential features are intentionally deferred to future releases, allowing the team to build a polished and demonstrable product within the hackathon timeline.
