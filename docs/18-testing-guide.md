# 18 - Testing Guide

# BuildBridge AI

## Manual Testing Checklist

---

# 1. Overview

This document outlines the manual testing process for BuildBridge AI.

Objectives:

* Verify all features work correctly.
* Detect UI and API issues.
* Ensure AI features generate valid responses.
* Validate authentication and authorization.
* Test responsive behavior across devices.

Testing Types

* Functional Testing
* UI Testing
* API Testing
* Authentication Testing
* AI Feature Testing
* Database Testing
* Responsive Testing
* Error Handling Testing

---

# 2. Testing Environment

## Frontend

* React (Vite)
* Chrome
* Firefox
* Microsoft Edge

---

## Backend

* Express.js
* Node.js
* MongoDB Atlas

---

## Third-Party Services

* Google Gemini API
* Cloudinary

---

# 3. Test Accounts

Create at least two users.

### User 1

```text
Email:
student1@test.com

Password:
Password123
```

---

### User 2

```text
Email:
student2@test.com

Password:
Password123
```

---

# 4. Authentication Testing

## User Registration

| Test Case                     | Expected Result           | Status |
| ----------------------------- | ------------------------- | ------ |
| Register with valid data      | User created successfully | ☐      |
| Register with duplicate email | Error displayed           | ☐      |
| Empty name                    | Validation error          | ☐      |
| Invalid email                 | Validation error          | ☐      |
| Short password                | Validation error          | ☐      |

---

## Login

| Test Case         | Expected Result       | Status |
| ----------------- | --------------------- | ------ |
| Valid credentials | Redirect to Dashboard | ☐      |
| Wrong password    | Error message         | ☐      |
| Unknown email     | Error message         | ☐      |
| Empty fields      | Validation error      | ☐      |

---

## Logout

| Test Case                     | Expected Result   | Status |
| ----------------------------- | ----------------- | ------ |
| Click logout                  | Redirect to Login | ☐      |
| Protected routes after logout | Access denied     | ☐      |

---

# 5. Profile Testing

| Test Case               | Expected Result    | Status |
| ----------------------- | ------------------ | ------ |
| Open profile page       | Data loads         | ☐      |
| Update profile          | Saved successfully | ☐      |
| Add skills              | Skills displayed   | ☐      |
| Empty career goal       | Validation error   | ☐      |
| Invalid graduation year | Validation error   | ☐      |

---

# 6. Roadmap Testing

| Test Case                  | Expected Result      | Status |
| -------------------------- | -------------------- | ------ |
| Generate roadmap           | Roadmap displayed    | ☐      |
| Invalid career goal        | Validation error     | ☐      |
| Timeline renders correctly | Pass                 | ☐      |
| Roadmap saved              | Visible in history   | ☐      |
| Delete roadmap             | Removed successfully | ☐      |

---

# 7. Resume Testing

## Upload

| Test Case                     | Expected Result   | Status |
| ----------------------------- | ----------------- | ------ |
| Upload valid PDF              | Upload successful | ☐      |
| Upload non-PDF                | Validation error  | ☐      |
| Upload file larger than limit | Error displayed   | ☐      |

---

## Analysis

| Test Case             | Expected Result     | Status |
| --------------------- | ------------------- | ------ |
| Analyze resume        | AI report generated | ☐      |
| ATS score displayed   | Visible             | ☐      |
| Strengths listed      | Pass                | ☐      |
| Weaknesses listed     | Pass                | ☐      |
| Suggestions displayed | Pass                | ☐      |

---

# 8. Project Recommendation Testing

| Test Case                | Expected Result | Status |
| ------------------------ | --------------- | ------ |
| Generate projects        | Cards displayed | ☐      |
| Difficulty badge visible | Pass            | ☐      |
| Tech stack visible       | Pass            | ☐      |
| Duration shown           | Pass            | ☐      |

---

# 9. Interview Module Testing

| Test Case               | Expected Result     | Status |
| ----------------------- | ------------------- | ------ |
| Generate questions      | Questions displayed | ☐      |
| Beginner difficulty     | Correct questions   | ☐      |
| Intermediate difficulty | Correct questions   | ☐      |
| Advanced difficulty     | Correct questions   | ☐      |
| Answers displayed       | Pass                | ☐      |
| Tips displayed          | Pass                | ☐      |

---

# 10. Dashboard Testing

| Test Case              | Expected Result | Status |
| ---------------------- | --------------- | ------ |
| Dashboard loads        | Success         | ☐      |
| Welcome card           | Visible         | ☐      |
| Navigation works       | Success         | ☐      |
| Dashboard cards render | Success         | ☐      |

---

# 11. Navigation Testing

| Route         | Expected Result | Status |
| ------------- | --------------- | ------ |
| `/`           | Landing page    | ☐      |
| `/login`      | Login page      | ☐      |
| `/register`   | Register page   | ☐      |
| `/dashboard`  | Dashboard       | ☐      |
| `/profile`    | Profile         | ☐      |
| `/roadmap`    | Roadmap         | ☐      |
| `/resume`     | Resume          | ☐      |
| `/projects`   | Projects        | ☐      |
| `/interview`  | Interview       | ☐      |
| Invalid route | 404 page        | ☐      |

---

# 12. Authorization Testing

| Test Case                      | Expected Result   | Status |
| ------------------------------ | ----------------- | ------ |
| Access dashboard without login | Redirect to Login | ☐      |
| Invalid JWT                    | 401 Unauthorized  | ☐      |
| Expired JWT                    | Login required    | ☐      |
| Valid JWT                      | Access granted    | ☐      |

---

# 13. API Testing

Use Postman or Thunder Client.

### Authentication

* Register
* Login
* Get Current User

---

### Profile

* Get Profile
* Update Profile

---

### Roadmap

* Generate Roadmap
* Get Roadmaps
* Delete Roadmap

---

### Resume

* Upload Resume
* Analyze Resume
* Delete Resume

---

### Projects

* Generate Projects

---

### Interview

* Generate Questions

---

# 14. Database Testing

Verify that MongoDB contains:

* User document created
* Profile updated correctly
* Resume stored
* Roadmap stored
* AI responses saved

Check:

* Duplicate users are prevented.
* ObjectId references are valid.
* Timestamps are generated.

---

# 15. AI Testing

## Career Roadmap

* Valid JSON returned
* Summary generated
* Milestones included
* Resources included
* Projects included

---

## Resume Analysis

* ATS score generated
* Strengths identified
* Weaknesses identified
* Suggestions generated

---

## Project Generator

* Multiple projects returned
* Technologies listed
* Difficulty assigned

---

## Interview Generator

* Questions generated
* Answers provided
* Tips included

---

# 16. Responsive Testing

Test on:

| Device  |  Width | Status |
| ------- | -----: | ------ |
| Mobile  |  375px | ☐      |
| Tablet  |  768px | ☐      |
| Laptop  | 1024px | ☐      |
| Desktop | 1440px | ☐      |

Verify:

* Sidebar behavior
* Navigation
* Cards
* Forms
* Tables
* Buttons

---

# 17. Browser Compatibility

| Browser | Status |
| ------- | ------ |
| Chrome  | ☐      |
| Firefox | ☐      |
| Edge    | ☐      |
| Brave   | ☐      |

---

# 18. Performance Testing

Verify:

* Initial page load < 3 seconds
* Dashboard loads smoothly
* API responses within acceptable time
* Resume upload completes successfully
* AI generation completes without timeout
* No noticeable UI lag

---

# 19. Error Handling

| Scenario            | Expected Result        | Status |
| ------------------- | ---------------------- | ------ |
| No internet         | Friendly error message | ☐      |
| Backend offline     | API error displayed    | ☐      |
| Gemini unavailable  | AI error shown         | ☐      |
| Invalid API request | Validation error       | ☐      |
| Cloudinary failure  | Upload error           | ☐      |

---

# 20. Security Checklist

* Passwords are hashed.
* JWT required for protected APIs.
* `.env` is not committed.
* API keys are hidden.
* Invalid file uploads are rejected.
* Input validation is enforced.
* CORS is configured correctly.

---

# 21. Final Acceptance Checklist

| Item                         | Status |
| ---------------------------- | ------ |
| User registration works      | ☐      |
| Login works                  | ☐      |
| Logout works                 | ☐      |
| Profile management works     | ☐      |
| Roadmap generation works     | ☐      |
| Resume upload works          | ☐      |
| Resume analysis works        | ☐      |
| Project recommendations work | ☐      |
| Interview generation works   | ☐      |
| Protected routes work        | ☐      |
| Responsive UI verified       | ☐      |
| Deployment successful        | ☐      |

---

# 22. Bug Reporting Template

```text
Bug Title:

Module:

Steps to Reproduce:

Expected Result:

Actual Result:

Severity:
(Low / Medium / High / Critical)

Screenshot:

Assigned To:

Status:
(Open / In Progress / Fixed / Closed)
```

---

# 23. Testing Best Practices

* Test each feature independently before integration.
* Re-test related functionality after fixing bugs.
* Validate both successful and failure scenarios.
* Test using different user accounts.
* Verify database changes after major operations.
* Confirm AI responses follow the expected JSON structure.
* Perform a complete end-to-end walkthrough before deployment.

---

# 24. Summary

The BuildBridge AI testing process focuses on validating every major feature through structured manual testing. The checklist covers authentication, profile management, AI-powered modules, database operations, API behavior, responsive layouts, security, and error handling. Completing this checklist before deployment helps ensure a stable, reliable MVP for hackathon demonstrations and judging.
