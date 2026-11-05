# System Modelling Diagrams

This directory contains UML and architectural models for the **Online Course Management System (OCMS)** developed during the laboratory modelling sessions.

---

## 1. Use Case Diagram

```mermaid
flowchart LR
  subgraph System["Online Course Management System (OCMS)"]
    UC1([Register & Login])
    UC2([Browse & Search Courses])
    UC3([Enroll in Course])
    UC4([View Lectures & Download Notes])
    UC5([Attempt Timed Quiz])
    UC6([Submit Assignment])
    UC7([Download Certificate])
    UC8([Create Course & Lessons])
    UC9([Grade Submissions])
    UC10([Approve/Reject Course])
    UC11([Manage Users & Roles])
  end

  Student((Student))
  Instructor((Instructor))
  Admin((Administrator))

  Student --> UC1
  Student --> UC2
  Student --> UC3
  Student --> UC4
  Student --> UC5
  Student --> UC6
  Student --> UC7

  Instructor --> UC1
  Instructor --> UC8
  Instructor --> UC9

  Admin --> UC1
  Admin --> UC10
  Admin --> UC11

  UC5 -.->|<<include>>| UC1
  UC7 -.->|<<extend>>| UC3
```

---

## 2. Entity Relationship Diagram (ERD)

```mermaid
erDiagram
  USER ||--o{ ENROLLMENT : places
  USER ||--o{ COURSE : instructs
  USER ||--o{ SUBMISSION : submits
  USER ||--o{ CERTIFICATE : earns

  COURSE ||--|{ MODULE : contains
  MODULE ||--|{ LESSON : includes
  COURSE ||--o{ ENROLLMENT : receives
  COURSE ||--o{ QUIZ : assesses

  QUIZ ||--|{ QUESTION : has
  QUIZ ||--o{ SUBMISSION : generates
  ENROLLMENT ||--o| CERTIFICATE : awards

  USER {
    int user_id PK
    string full_name
    string email UK
    string password_hash
    string role "Student | Instructor | Admin"
    datetime created_at
  }

  COURSE {
    int course_id PK
    string title
    string category
    text description
    string status "Draft | Pending | Published"
    decimal price
  }

  MODULE {
    int module_id PK
    int course_id FK
    string title
    int order_index
  }

  LESSON {
    int lesson_id PK
    int module_id FK
    string title
    string video_url
    string pdf_url
    int duration_minutes
  }

  ENROLLMENT {
    int enrollment_id PK
    int user_id FK
    int course_id FK
    datetime enrolled_at
    float progress_percentage
    string status "Active | Completed"
  }

  QUIZ {
    int quiz_id PK
    int course_id FK
    string title
    int duration_minutes
    int passing_score
  }

  SUBMISSION {
    int submission_id PK
    int user_id FK
    int quiz_id FK
    int score
    datetime submitted_at
    string status "Passed | Failed"
  }

  CERTIFICATE {
    int certificate_id PK
    int enrollment_id FK
    string verification_code UK
    datetime issued_at
  }
```

---

## 3. Sequence Diagram: Course Enrollment & Assessment Flow

```mermaid
sequenceDiagram
  autonumber
  actor Student as Student
  participant UI as Web Client UI
  participant Auth as Auth Controller
  participant CourseService as Course Service
  participant DB as Relational Database
  participant Notify as Notification Service

  Student->>UI: Select course and click "Enroll Now"
  UI->>Auth: Verify active JWT session
  Auth-->>UI: Session valid (Student role)
  UI->>CourseService: POST /api/enroll (course_id, student_id)
  CourseService->>DB: Query existing enrollment
  DB-->>CourseService: No existing record found
  CourseService->>DB: INSERT into ENROLLMENTS
  DB-->>CourseService: Enrollment confirmed
  CourseService->>Notify: Send course welcome email
  CourseService-->>UI: HTTP 201 Created (Enrollment OK)
  UI-->>Student: Display "Enrolled Successfully" & redirect to curriculum
```
