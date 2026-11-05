| Test Case ID | Module               | Test Scenario                | Test Input                      | Expected Result                        |
| ------------ | -------------------- | ---------------------------- | ------------------------------- | -------------------------------------- |
| TC01         | Login                | Login with valid credentials | Valid username and password     | User should log in successfully        |
| TC02         | Login                | Login with invalid password  | Valid username + wrong password | Error message should be displayed      |
| TC03         | Student Registration | Register a new student       | Valid student details           | Student should be registered           |
| TC04         | Student Registration | Submit empty required fields | Empty fields                    | Validation message should be displayed |
| TC05         | Course Enrollment    | Enroll in an available course| Valid student + available course| Course should be enrolled successfully |
| TC06         | Course Enrollment    | Enroll in a full/closed course| Full/closed course             | System should prevent enrollment       |
| TC07         | Course Creation      | Add a new course module      | Valid course title and syllabus | Course module should be created        |
| TC08         | Assignment Submission| Submit course assignment     | Valid assignment file attachment| Assignment submission should be recorded|
| TC09         | Quiz Assessment      | Submit a course quiz         | Valid quiz answers              | Quiz score should be calculated        |
| TC10         | Logout               | Logout from the system       | Click Logout                    | User should be logged out              |
