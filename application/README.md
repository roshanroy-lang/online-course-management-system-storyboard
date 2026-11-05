# Application Prototype Planning & Architecture

This directory outlines the technical design, architectural patterns, and prototyping notes for the **Online Course Management System (OCMS)** implemented during laboratory sessions 10 and 11.

---

## 1. System Architecture

The prototype is structured following a decoupled three-tier architectural model:

```text
┌────────────────────────────────────────────────────────┐
│                      Client Tier                       │
│    Responsive Web Interface (HTML5, Tailwind, JS)     │
└───────────────────────────┬────────────────────────────┘
                            │ REST / JSON via HTTPS
┌───────────────────────────▼────────────────────────────┐
│                    Application Tier                    │
│        Node.js / Express.js RESTful API Engine         │
│  [Auth Controller]  [Course Controller]  [Quiz Engine] │
└───────────────────────────┬────────────────────────────┘
                            │ SQL Queries / ORM
┌───────────────────────────▼────────────────────────────┐
│                       Data Tier                        │
│          Relational Database (PostgreSQL / SQLite)     │
└────────────────────────────────────────────────────────┘
```

---

## 2. Technology Stack

- **Frontend:** HTML5, CSS3, JavaScript (ES6+), TailwindCSS
- **Backend API:** Node.js runtime with Express.js framework
- **Authentication:** JSON Web Tokens (JWT) with bcrypt password hashing
- **Database:** SQLite (for local lab development) / PostgreSQL (production target)
- **Modeling & Version Control:** StarUML / Mermaid.js, Git, and GitHub

---

## 3. Core REST API Endpoints

| HTTP Method | Endpoint | Description | Access Role |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/register` | Register new user account | Public |
| `POST` | `/api/auth/login` | Authenticate and return JWT token | Public |
| `GET` | `/api/courses` | Retrieve published course list | Public |
| `GET` | `/api/courses/:id` | Get full curriculum details of a course | Authenticated |
| `POST` | `/api/courses` | Create new course draft | Instructor |
| `POST` | `/api/enroll/:courseId` | Enroll authenticated student in course | Student |
| `GET` | `/api/student/dashboard` | View enrolled courses & progress stats | Student |
| `POST` | `/api/quizzes/:id/submit` | Submit answers for auto-grading | Student |
| `PATCH`| `/api/admin/courses/:id/status`| Approve or reject pending course | Administrator |

---

## 4. Local Prototype Execution

```bash
# 1. Clone repository
git clone https://github.com/<your-username>/online-course-management-system-storyboard.git
cd online-course-management-system-storyboard

# 2. Open client interface
open application/index.html   # or launch live server
```

