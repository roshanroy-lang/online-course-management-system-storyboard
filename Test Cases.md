# Software Testing Documentation: Online Course Management System

## Test Suite Overview

This document defines the functional test cases for the **Online Course Management System (OCMS)**, designed to validate user interactions across Student, Instructor, and Administrator roles in accordance with the Software Requirements Specification (SRS).

---

## Functional Test Cases

| Test Case ID | Module | Test Scenario | Test Input | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC01** | User Authentication | Login with valid student credentials | Valid email (`student@univ.edu`) + correct password | User successfully authenticated; redirected to Student Dashboard | As expected | Pass |
| **TC02** | User Authentication | Login with invalid password | Valid email + wrong password | System displays error: *"Invalid email or password"* | As expected | Pass |
| **TC03** | User Registration | Register a new student account | Unique email, valid password, full name | Account created; confirmation email sent; redirect to login | As expected | Pass |
| **TC04** | User Registration | Register with an already registered email | Existing email address | System rejects registration: *"Email already registered"* | As expected | Pass |
| **TC05** | Course Catalog | Search course by keyword and category | Keyword: `"Python"`, Category: `"Computer Science"` | Filtered list displaying all matching published Python courses | As expected | Pass |
| **TC06** | Course Management | Instructor creates a new course draft | Title: `"Data Structures"`, syllabus, description | Course created with status `"Draft"`; assigned unique Course ID | As expected | Pass |
| **TC07** | Course Management | Create course with missing mandatory fields | Empty Course Title or empty category | Form submission prevented; inline validation errors displayed | As expected | Pass |
| **TC08** | Course Enrollment | Student enrolls in an active, published course | Click *"Enroll Now"* on active Course ID `CS201` | Student added to course roster; course appears in *"My Courses"* | As expected | Pass |
| **TC09** | Course Enrollment | Prevent duplicate enrollment in the same course | Attempt to enroll in already enrolled course | Button displays *"Already Enrolled"*; duplicate enrollment blocked | As expected | Pass |
| **TC10** | Content Delivery | Access video lecture and download PDF notes | Click lecture module 1.2; click download PDF | Video streams without error; lesson PDF downloads successfully | As expected | Pass |
| **TC11** | Assignment Module | Student submits assignment before deadline | Attach file `lab1.pdf` (2.4 MB) before due date | Submission timestamp recorded; status updated to *"Submitted"* | As expected | Pass |
| **TC12** | Assignment Module | Attempt to upload unsupported file format | Upload file `lab1.exe` or `lab1.sh` | System rejects upload: *"Unsupported file format. Allowed: .pdf, .zip"* | As expected | Pass |
| **TC13** | Quiz Assessment | Student takes timed multiple-choice quiz | Select answers for 10 questions within 15 mins | Answers recorded; auto-grading calculates score immediately | As expected | Pass |
| **TC14** | Quiz Assessment | Quiz auto-submission on timer expiration | Timer reaches `00:00` while questions unanswered | Quiz automatically submitted; unanswered questions marked 0 | As expected | Pass |
| **TC15** | Discussion Forum | Student posts a question in course thread | Valid topic title + question body | Thread published in course forum; notification sent to instructor | As expected | Pass |
| **TC16** | Gradebook | Instructor enters marks and feedback | Student ID `S102`, Score: `88/100`, Feedback text | Grade saved; student notification triggered; GPA updated | As expected | Pass |
| **TC17** | Certificate Module | Generate course completion certificate | Course completion = 100% and Quiz score ≥ 70% | Unique verified certificate PDF generated with QR validation code | As expected | Pass |
| **TC18** | Admin Management | Admin approves new instructor course submission | Review Course `AI301` draft; click *"Approve"* | Course status changes from `"Pending Approval"` to `"Published"` | As expected | Pass |
| **TC19** | User Logout | User logs out of active session | Click *"Logout"* from profile dropdown | Session destroyed; auth tokens cleared; redirect to home page | As expected | Pass |

---

## Test Execution Summary

- **Total Test Cases Executed:** 19
- **Passed:** 19
- **Failed:** 0
- **Blocked:** 0
- **Execution Date:** Laboratory Session 12
- **Testing Approach:** Black-Box Functional Testing, Equivalence Partitioning, and Boundary Value Analysis

