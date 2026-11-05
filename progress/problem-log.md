# Problem Log

Record real problems faced during each laboratory session. Do not add an entry unless the problem actually occurred.

| Date / Session | Problem Encountered | Cause | Solution / Action Taken | Status |
| :---: | :--- | :--- | :--- | :---: |
| **Session 2** | Ambiguity regarding whether Guest Users should be treated as a primary actor. | Unclear boundaries on whether unregistered visitors should have permissions in the Use Case model. | Established that unregistered visitors can only view public course catalogs. Created an abstract `Guest` role that generalizes into `Student` upon registration. | **Closed** |
| **Session 3** | Scope creep in Course Discussion Forums and live video streaming requirements. | Attempting to specify real-time WebSocket video calls within the initial prototype scope. | Refactored SRS to specify asynchronous pre-recorded video lectures and threaded discussion boards for the MVP phase. | **Closed** |
| **Session 4** | Cardinality confusion in ER diagram between Instructors, Courses, and Cohort Enrollments. | Multiple instructors co-teaching a single course versus single-instructor course ownership. | Introduced an associative entity `Course_Instructor` to support many-to-many relationships with role designations (Primary / Co-Instructor). | **Closed** |
| **Session 5** | Confusion between `<<include>>` and `<<extend>>` stereotypes in Quiz Evaluation. | Unclear whether quiz retakes and certificate issuance are mandatory inclusions or conditional extensions. | Clarified that `Take Quiz` `<<includes>>` `Submit Answers`, while `Issue Certificate` `<<extends>>` `Complete Course` conditioned on `Score >= 70%`. | **Closed** |
| **Session 6** | Process decomposition bottleneck in Data Flow Diagram (DFD Level 1). | Mixing payment verification data flows directly into the course video streaming datastore. | Split Process 3.0 (Course Management) into Process 3.1 (Enrollment & Access Control) and Process 3.2 (Content Streaming) with distinct datastores. | **Closed** |
| **Session 9** | Sequence diagram lifeline mismatch during timed quiz auto-submission. | Difficulty representing asynchronous client-side timer expiration communicating with server session. | Added a client-side Timer object lifeline sending an asynchronous `timeExpired()` event to the QuizController, triggering immediate state lock and auto-evaluation. | **Closed** |
| **Session 11** | Race condition during simultaneous course enrollment when seat limit is reached. | Concurrent database requests reading available seat count before transaction commit. | Applied optimistic database locking with transaction isolation levels to prevent over-enrollment beyond maximum course capacity. | **Closed** |
| **Session 12** | Form validation failure on oversized assignment PDF uploads. | Browser multipart form timeout when handling files larger than standard HTTP payload limits. | Configured client-side pre-upload file size check (max 10MB) and added validation message for unsupported file extensions (.exe, .sh). | **Closed** |

---

## Suggested Categories

- **Requirement ambiguity:** Defining clear boundaries and avoiding scope creep
- **Difficulty identifying actors or stakeholders:** Role modeling and permission boundaries
- **Confusion between UML diagrams:** Correct use of stereotypes, lifelines, and swimlanes
- **ER diagram relationship issues:** Normalization, composite keys, and cardinality
- **Data flow or process definition problems:** DFD leveling, balanced inputs and outputs
- **UI design challenges:** Responsive navigation and accessible media players
- **Implementation errors:** State synchronization, API routing, and concurrency
- **Testing or validation issues:** Edge cases, boundary value limits, and timeout triggers
- **Documentation or version-control issues:** Merge conflicts, branch structuring, and markdown formatting

