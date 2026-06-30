# 10 - AI Architecture

# BuildBridge AI

## Google Gemini AI Architecture

---

# 1. Overview

BuildBridge AI uses **Google Gemini API** as the intelligence layer of the application.

Instead of generating free-form responses, Gemini is instructed to return **strictly structured JSON**, allowing the frontend to render dynamic UI components without additional parsing.

The AI layer is responsible for:

* Career Roadmap Generation
* Resume Analysis
* Project Recommendations
* Interview Question Generation

The backend acts as a mediator between the frontend and Gemini.

---

# 2. AI Architecture Overview

```text id="x8pnjl"
                  User
                    │
                    ▼
          React Frontend (Dashboard)
                    │
                    ▼
          Express Backend API
                    │
                    ▼
          AI Service Layer
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
 Prompt Builder  Gemini API  Response Validator
        │           │           │
        └───────────┼───────────┘
                    ▼
          Structured JSON Response
                    │
                    ▼
              React Components
```

---

# 3. AI Modules

The AI system is divided into four independent modules.

```text id="fjlwmg"
AI

├── Career Roadmap

├── Resume Analysis

├── Project Recommendation

└── Interview Generator
```

Each module has:

* Prompt Template
* Service
* Response Validator

---

# 4. AI Folder Structure

```text id="g2h3dr"
server/

src/

├── prompts/

│   ├── roadmapPrompt.js

│   ├── resumePrompt.js

│   ├── projectPrompt.js

│   └── interviewPrompt.js

│

├── services/

│   ├── geminiService.js

│   ├── roadmapService.js

│   ├── resumeService.js

│   ├── projectService.js

│   └── interviewService.js
```

---

# 5. AI Request Flow

Every AI request follows the same lifecycle.

```text id="85f0qs"
Frontend

↓

REST API

↓

Controller

↓

Service

↓

Prompt Builder

↓

Gemini API

↓

JSON Validator

↓

Response

↓

Frontend
```

Controllers never communicate directly with Gemini.

---

# 6. Prompt Engineering Strategy

Every prompt follows the same structure.

```text id="qh1gpi"
System Instructions

↓

User Context

↓

Business Rules

↓

Expected JSON Format

↓

Gemini
```

This ensures consistency across all AI features.

---

# 7. Career Roadmap Workflow

```text id="tuxbnn"
User Profile

↓

Roadmap Service

↓

Roadmap Prompt

↓

Gemini API

↓

JSON Validation

↓

Roadmap Timeline
```

### Input

* Education
* Skills
* Interests
* Career Goal
* Experience Level

### Output

* Summary
* Duration
* Milestones
* Technologies
* Learning Resources
* Recommended Projects

---

# 8. Resume Analysis Workflow

```text id="pkjvrb"
Upload Resume

↓

Extract Text

↓

Resume Prompt

↓

Gemini API

↓

AI Analysis

↓

JSON Report
```

### Input

* Resume Text

### Output

* ATS Score
* Strengths
* Weaknesses
* Missing Keywords
* Suggestions

---

# 9. Project Recommendation Workflow

```text id="e93qnt"
Profile

↓

Project Prompt

↓

Gemini API

↓

Projects JSON
```

Each recommendation contains:

* Title
* Description
* Difficulty
* Technologies
* Duration
* Learning Outcomes

---

# 10. Interview Generator Workflow

```text id="zb0hxh"
Career Goal

↓

Interview Prompt

↓

Gemini API

↓

Question List
```

Questions are categorized into:

* Beginner
* Intermediate
* Advanced

Each includes:

* Question
* Expected Answer
* Tips

---

# 11. Prompt Architecture

Each prompt contains four sections.

```text id="v7cfv4"
Role

↓

Context

↓

Instructions

↓

Output Format
```

Example structure:

### Role

"You are an expert career mentor."

### Context

User profile information.

### Instructions

Generate a personalized roadmap.

### Output

Return only valid JSON.

---

# 12. JSON Response Policy

Gemini must **always** return JSON.

Never return:

* Markdown
* Bullet Lists
* HTML
* Natural Language Paragraphs

The backend parses JSON directly.

---

# 13. Career Roadmap JSON

```json id="cixm0h"
{
  "summary": "",
  "duration": "",
  "milestones": [
    {
      "title": "",
      "description": "",
      "technologies": [],
      "resources": []
    }
  ],
  "projects": [
    {
      "title": "",
      "difficulty": "",
      "technologies": []
    }
  ]
}
```

---

# 14. Resume Analysis JSON

```json id="j2z19o"
{
  "atsScore": 90,
  "strengths": [],
  "weaknesses": [],
  "missingKeywords": [],
  "suggestions": []
}
```

---

# 15. Project Recommendation JSON

```json id="ltcdic"
[
  {
    "title": "",
    "description": "",
    "difficulty": "",
    "duration": "",
    "technologies": [],
    "learningOutcomes": []
  }
]
```

---

# 16. Interview JSON

```json id="q8l91b"
{
  "questions": [
    {
      "difficulty": "Beginner",
      "question": "",
      "answer": "",
      "tips": ""
    }
  ]
}
```

---

# 17. Response Validation

Every Gemini response must be validated before sending it to the frontend.

Validation includes:

* Valid JSON
* Required fields exist
* Correct data types
* Non-empty arrays
* Safe fallback values

If validation fails:

* Retry once (optional)
* Return a standardized AI error response

---

# 18. Error Handling

Possible AI failures:

* Invalid JSON
* Empty response
* API timeout
* Quota exceeded
* Network failure

Standard error response:

```json id="5dg6u8"
{
  "success": false,
  "message": "Unable to generate AI response."
}
```

---

# 19. Prompt Best Practices

* Keep prompts in separate files.
* Do not hardcode prompts inside controllers.
* Version prompts if major changes are introduced.
* Keep prompts deterministic where possible.
* Request structured JSON only.
* Avoid ambiguous instructions.
* Limit unnecessary verbosity.

---

# 20. Security Considerations

* Never expose the Gemini API key to the frontend.
* Store API keys in environment variables.
* Sanitize user input before prompt construction.
* Limit prompt size to avoid excessive token usage.
* Never trust AI output without validation.

---

# 21. AI Service Responsibilities

| Service             | Responsibility               |
| ------------------- | ---------------------------- |
| geminiService.js    | Low-level Gemini client      |
| roadmapService.js   | Generate career roadmaps     |
| resumeService.js    | Analyze resumes              |
| projectService.js   | Generate project ideas       |
| interviewService.js | Generate interview questions |

---

# 22. Future AI Enhancements

The architecture supports future AI modules such as:

* AI Career Chatbot
* Mock Interview Simulator
* Resume Builder
* Portfolio Generator
* Job Recommendation Engine
* Learning Path Optimizer
* Personalized Weekly Study Plans
* Company-Specific Interview Preparation
* AI Progress Evaluation

Each new capability can be added by introducing a new prompt and service without modifying the existing architecture.

---

# 23. Summary

The AI layer of BuildBridge AI is built around a service-oriented architecture where Gemini is accessed only through dedicated services and prompt templates. Every AI feature follows the same pipeline—prompt construction, Gemini invocation, JSON validation, and structured response delivery. By enforcing strict JSON output contracts and isolating prompts from controllers, the application remains maintainable, scalable, and reliable while enabling the frontend to render AI-generated content consistently.
