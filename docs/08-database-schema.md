# 08 - Database Schema

# BuildBridge AI

## MongoDB Database Design

---

# 1. Overview

BuildBridge AI uses **MongoDB** as its primary database.

The database stores:

* User Authentication
* User Profile
* Resume Information
* AI Generated Reports
* Career Roadmaps

The MVP uses only **four collections** to keep the architecture simple and maintainable.

---

# 2. Collections

```text
MongoDB

│

├── users

├── profiles

├── resumes

└── roadmaps
```

---

# 3. Database Relationship

```text
                   User
                    │
      ┌─────────────┼─────────────┐
      │             │             │
      ▼             ▼             ▼
   Profile       Resume       Roadmap
```

Relationship Type

```text
User (1)

↓

Profile (1)

↓

Resume (Many)

↓

Roadmap (Many)
```

Each user owns:

* One Profile
* Multiple Resumes
* Multiple Career Roadmaps

---

# 4. Entity Relationship Diagram (ERD)

```text
+----------------------+
|        USERS         |
+----------------------+
| _id                  |
| fullName             |
| email                |
| password             |
| avatar               |
| role                 |
| createdAt            |
| updatedAt            |
+----------+-----------+
           |
           | 1 : 1
           |
           ▼
+----------------------+
|      PROFILES        |
+----------------------+
| _id                  |
| userId               |
| education            |
| college              |
| degree               |
| graduationYear       |
| skills[]             |
| interests[]          |
| careerGoal           |
| github               |
| linkedin             |
| createdAt            |
| updatedAt            |
+----------+-----------+
           |
           |
     +-----+------+
     |            |
     |            |
     ▼            ▼
+-----------+  +----------------+
| RESUMES   |  | ROADMAPS       |
+-----------+  +----------------+
| _id       |  | _id            |
| userId    |  | userId         |
| fileUrl   |  | careerGoal     |
| fileName  |  | roadmapData{}  |
| atsScore  |  | generatedAt    |
| report{}  |  | updatedAt      |
| createdAt |  +----------------+
+-----------+
```

---

# 5. User Schema

Purpose

Stores authentication information.

```javascript
{
    _id: ObjectId,

    fullName: String,

    email: String,

    password: String,

    avatar: String,

    role: {
        type: String,
        default: "student"
    },

    createdAt: Date,

    updatedAt: Date
}
```

---

## Field Description

| Field    | Type   | Required |
| -------- | ------ | -------- |
| fullName | String | Yes      |
| email    | String | Yes      |
| password | String | Yes      |
| avatar   | String | No       |
| role     | String | Yes      |

---

Indexes

```javascript
email
```

Unique.

---

# 6. Profile Schema

Purpose

Stores all career-related information.

```javascript
{
    _id: ObjectId,

    userId: ObjectId,

    education: String,

    college: String,

    degree: String,

    graduationYear: Number,

    experienceLevel: String,

    skills: [String],

    interests: [String],

    careerGoal: String,

    github: String,

    linkedin: String,

    portfolio: String,

    bio: String,

    createdAt: Date,

    updatedAt: Date
}
```

---

## Field Description

| Field          | Type   |
| -------------- | ------ |
| education      | String |
| college        | String |
| degree         | String |
| graduationYear | Number |
| skills         | Array  |
| interests      | Array  |
| careerGoal     | String |
| github         | String |
| linkedin       | String |
| portfolio      | String |

---

Relationship

```text
One User

↓

One Profile
```

---

# 7. Resume Schema

Purpose

Stores uploaded resumes and AI analysis.

```javascript
{
    _id: ObjectId,

    userId: ObjectId,

    fileName: String,

    fileUrl: String,

    extractedText: String,

    atsScore: Number,

    report: {

        strengths: [String],

        weaknesses: [String],

        missingKeywords: [String],

        suggestions: [String]

    },

    createdAt: Date
}
```

---

Each uploaded resume keeps its own AI report.

This allows users to compare different resume versions later.

---

# 8. Roadmap Schema

Purpose

Stores AI-generated career roadmaps.

```javascript
{
    _id: ObjectId,

    userId: ObjectId,

    careerGoal: String,

    roadmapData: {

        summary: String,

        duration: String,

        milestones: [

            {

                title: String,

                description: String,

                technologies: [String],

                resources: [String]

            }

        ],

        projects: [

            {

                title: String,

                difficulty: String,

                technologies: [String]

            }

        ]

    },

    generatedAt: Date,

    updatedAt: Date
}
```

---

Roadmaps are stored as JSON returned by Gemini.

This avoids creating unnecessary collections.

---

# 9. Relationships

## User → Profile

```text
1 : 1
```

One user has one profile.

---

## User → Resume

```text
1 : Many
```

One user can upload multiple resumes.

---

## User → Roadmap

```text
1 : Many
```

One user can generate multiple career roadmaps.

---

# 10. Mongoose Relationships

Example

```javascript
userId: {
    type: mongoose.Schema.Types.ObjectId,
    ref: "User",
    required: true
}
```

Used in

* Profile
* Resume
* Roadmap

---

# 11. Data Flow

```text
User Registers

↓

User Collection

↓

Complete Profile

↓

Profile Collection

↓

Generate Roadmap

↓

Roadmap Collection

↓

Upload Resume

↓

Resume Collection
```

---

# 12. Indexing Strategy

## Users

```text
email
```

Unique index.

---

## Profiles

```text
userId
```

Index.

---

## Resumes

```text
userId
```

Index.

---

## Roadmaps

```text
userId
```

Index.

---

# 13. Validation Rules

## User

* Email required
* Email unique
* Password minimum 8 characters

---

## Profile

* Career Goal required
* Skills cannot be empty
* Graduation Year must be valid

---

## Resume

* PDF only
* Maximum file size (e.g., 5 MB)

---

## Roadmap

* Must contain at least one milestone

---

# 14. Future Collections

These collections are intentionally excluded from the MVP.

Future additions may include:

```text
InterviewHistory

Projects

Notifications

Certificates

LearningProgress

Achievements

Bookmarks

Companies

Jobs

Mentors
```

---

# 15. Database Best Practices

* Use ObjectId references instead of duplicating user data.
* Store passwords only after bcrypt hashing.
* Never store JWT tokens in the database.
* Keep AI responses as structured JSON.
* Index frequently queried fields (`email`, `userId`).
* Enable timestamps on all schemas.
* Validate all incoming data before database operations.

---

# 16. Summary

The BuildBridge AI database is intentionally lightweight, using four primary collections: **Users**, **Profiles**, **Resumes**, and **Roadmaps**. Relationships are centered around the `User` entity, with one-to-one and one-to-many associations where appropriate. AI-generated content is stored as structured JSON, enabling efficient retrieval and future extensibility while keeping the MVP implementation straightforward.
