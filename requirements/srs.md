# Software Requirements Specification (SRS)

## Online Course Management System (OCMS)

**Course:** Software Engineering Laboratory  
**Project:** Online Course Management System  
**Version:** 1.0  
**Status:** Approved Baseline  

---

### 1. Introduction

#### 1.1 Purpose
The purpose of this document is to define the functional and non-functional requirements for the **Online Course Management System (OCMS)**. It serves as the primary contract between academic laboratory stakeholders, system analysts, designers, and testers.

#### 1.2 Scope
The OCMS is a web-based educational management platform designed to automate and streamline digital learning:
- Course creation, curriculum design, and multimedia lecture delivery.
- Student enrollment, progress tracking, and peer discussion.
- Automated quiz assessment, assignment submission, and verifiable certificate issuance.
- Administrative auditing, instructor onboarding, and analytics reporting.

#### 1.3 Definitions, Acronyms, and Abbreviations
- **OCMS:** Online Course Management System
- **SRS:** Software Requirements Specification
- **ERD:** Entity Relationship Diagram
- **DFD:** Data Flow Diagram
- **CRUD:** Create, Read, Update, Delete
- **LMS:** Learning Management System
- **JWT:** JSON Web Token (Authentication mechanism)

---

### 2. Overall Description

#### 2.1 Product Perspective
OCMS operates as an independent web application backed by a relational database management system. It interacts externally with third-party payment gateways and transactional email services.

#### 2.2 User Classes and Characteristics

```text
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│     STUDENT     │       │   INSTRUCTOR    │       │  ADMINISTRATOR  │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ • Browse & search│       │ • Create courses │       │ • Approve course │
│ • Enroll        │       │ • Upload lessons │       │ • User audits   │
│ • Watch videos  │       │ • Author quizzes │       │ • System stats  │
│ • Take quizzes  │       │ • Grade tasks    │       │ • Role control  │
│ • Get certs     │       │ • View analytics │       │ • Policy enforce│
└─────────────────┘       └─────────────────┘       └─────────────────┘
```

#### 2.3 Operating Environment
- **Client Tier:** Modern web browsers (Google Chrome 110+, Mozilla Firefox 110+, Safari 16+, Microsoft Edge).
- **Application Server:** Node.js runtime environment (v18+).
- **Database Server:** PostgreSQL / SQLite relational database.

---

### 3. Functional Requirements

#### 3.1 Module 1: User Authentication & Role Management
- **FR-1.1:** The system shall allow users to register with name, email, password, and designated role.
- **FR-1.2:** The system shall authenticate users via encrypted password hashing (bcrypt) and issue session tokens.
- **FR-1.3:** The system shall enforce Role-Based Access Control (RBAC) ensuring students cannot access instructor authoring tools.

#### 3.2 Module 2: Course Catalog & Curriculum Authoring
- **FR-2.1:** Instructors shall create courses with title, category, syllabus, price, and thumbnail.
- **FR-2.2:** Instructors shall organize course content hierarchically into Modules, Lessons, and Video/PDF resources.
- **FR-2.3:** Newly created courses shall remain in `Draft` status until submitted to and approved by an Administrator.

#### 3.3 Module 3: Enrollment & Progress Tracking
- **FR-3.1:** Students shall search and filter published courses by keyword, instructor, and category.
- **FR-3.2:** Eligible students shall enroll in courses with a single action, updating seat capacity and creating an enrollment record.
- **FR-3.3:** The system shall calculate student progress dynamically (percentage of lessons viewed and tasks completed).

#### 3.4 Module 4: Assessments & Quizzes
- **FR-4.1:** Instructors shall author multiple-choice quizzes with custom time limits and passing criteria.
- **FR-4.2:** The system shall auto-submit active quiz sessions when the client countdown timer reaches zero.
- **FR-4.3:** The system shall automatically calculate assessment scores and display instant feedback upon submission.

#### 3.5 Module 5: Certification
- **FR-5.1:** Upon achieving 100% course progression and meeting minimum passing scores, the system shall generate a verified Certificate of Completion with a unique verification code.

---

### 4. Non-Functional Requirements

- **NFR-1 (Performance):** Page load times for course lesson pages shall not exceed 2.0 seconds under normal network conditions.
- **NFR-2 (Security):** Passwords shall never be stored in plaintext. Sensitive API routes must require authorization bearer tokens.
- **NFR-3 (Availability):** System architecture shall target 99.5% operational uptime during laboratory demonstration windows.
- **NFR-4 (Usability):** User interfaces shall adhere to WCAG 2.1 Level AA accessibility guidelines, including responsive layout across mobile and desktop viewports.

