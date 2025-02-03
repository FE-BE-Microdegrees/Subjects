# Example of Software Requirements Specification (SRS)

## 1. Overview

- **Project Name:** Online Assignment Tracking System
- **Goal:** Create a platform where teachers can assign tasks and track student progress, and where students can submit their responses and receive feedback.

## 2. Functional Requirements

### 2.1. User Authentication and Authorization

- **Requirement 2.1.1:** The system must provide user registration and login functionality using email and password.
- **Requirement 2.1.2:** The system must support different user roles: `teacher` and `student`.
- **Requirement 2.1.3:** Teachers must be able to create and manage student accounts.

### 2.2. Assignment Creation and Management

- **Requirement 2.2.1:** Teachers must be able to add new assignments, including a description, deadline, and required resources.
- **Requirement 2.2.2:** Teachers must be able to assign tasks to specific student groups.
- **Requirement 2.2.3:** Students must be able to submit their responses directly through the system and upload necessary files.

### 2.3. Feedback and Grading

- **Requirement 2.3.1:** Teachers must be able to provide feedback on each assignment and assign a grade.
- **Requirement 2.3.2:** Students must be able to view the feedback and grades provided by the teacher in their user profile.

## 3. Non-functional Requirements

### 3.1. Performance

- **Requirement 3.1.1:** The system must be able to handle up to 500 concurrent users without performance degradation.

### 3.2. Security

- **Requirement 3.2.1:** All user data must be encrypted, and passwords must be hashed.
- **Requirement 3.2.2:** The system must provide role-based access control to ensure data protection and privacy.

## 4. User Restrictions and Prohibitions

### 4.1. User Activity Restrictions

- **Requirement 4.1.1:** Students must not be able to modify or delete assignments created by teachers.
- **Requirement 4.1.2:** Students must not be able to modify other students' responses or view their private data.
- **Requirement 4.1.3:** Teachers must not modify student accounts without their informed consent (except for locking accounts when necessary).
- **Requirement 4.1.4:** Users must not attempt to access hidden areas of the system or manipulate the system code.
- **Requirement 4.1.5:** Users must not submit values containing malicious code or viruses that could harm the system.

## 5. System Interfaces

### 5.1. User Interface (UI)

- **Requirement 5.1.1:** Students and teachers must be able to use a web browser to view and manage assignments.
- **Requirement 5.1.2:** The user interface must be simple and intuitive to ensure usability.

### 5.2. API Interfaces

- **Requirement 5.2.1:** The system must provide a RESTful API to allow third-party applications to interface with it.

## 6. Constraints and Assumptions

- **Assumption 1:** All users will have access to an internet-enabled device.
- **Constraint 1:** The system currently does not support a mobile application and is optimized for use on desktop computers.
