
*Role 2:* Requirements Classification Specialist  
---

| ID | Description | Category | Type | Priority | Notes |
|----|-------------|----------|------|----------|-------|
| F-01 | Student signup and account creation using university email | Functional | User Requirement | High | Must support common edu emails and invite flow |
| F-02 | Student verification workflow (email confirmation and optional student ID upload) | Functional | System Requirement | High | Verification status affects access level |
| F-03 | Role-based access control: Student, Organization, Admin | Functional | System Requirement | High | Controls permissions and UI access |
| F-04 | Student profile (name, university, major, skills, bio, projects) | Functional | User Requirement | High | Editable by student; viewable by other verified users |
| F-05 | Organization profile with limited information and restricted actions | Functional | User Requirement | High | Org accounts can post opportunities but cannot access student-only areas |
| F-06 | Idea / Project posting (students can create posts describing idea, tags, required skills) | Functional | User Requirement | High | Posts have status (open, closed, in progress) |
| F-07 | Browse and search functionality across categories, skills, and tags | Functional | User Requirement | High | Filtering and sorting options required |
| F-08 | Apply / Join workflow for students to express interest in a project or opportunity | Functional | User Requirement | High | Includes message to project owner and simple proposal form |
| F-09 | Organization posting: internships, one-time jobs, volunteering opportunities (limited to opportunity sections) | Functional | User Requirement | High | Org posts must be flagged as 'organization opportunity' |
| F-10 | Project collaboration tools: basic task list / team assignment (MVP) | Functional | User Requirement | Medium | Integrate lightweight project management features |
| F-11 | Private and group messaging between verified users | Functional | User Requirement | High | Must be accessible only to verified accounts |
| F-12 | Notification system (in-app + optional email notifications) | Functional | User Requirement | High | Users can opt in/out of email notifications |
| F-13 | Reporting and moderation tools (report post/user, admin review queue) | Functional | System Requirement | High | Admin dashboard for moderation actions |
| F-14 | Categories & channels for thematic grouping (e.g., tech, design, social) | Functional | User Requirement | Medium | Students can follow categories |
| F-15 | Profile portfolio: ability to attach project artifacts and links | Functional | User Requirement | Medium | Limit file types/size for attachments |
| F-16 | Application settings & privacy controls (profile visibility, contact preferences) | Functional | User Requirement | Medium | Default privacy set to student-only visibility where appropriate |
| F-17 | Audit logging for security-sensitive actions (login, verification, admin actions) | Functional | System Requirement | High | Logs retained per data retention policy |
| F-18 | Admin user management (suspend, delete, change roles) | Functional | System Requirement | High | Admin actions must be audited |
| F-19 | Onboarding tutorial / help pages for new users | Functional | User Requirement | Low | Short guided tour for first login |
| F-20 | Export / download basic profile or project summary (for CVs) | Functional | User Requirement | Low | CSV or PDF export option (later phase) |
| NF-01 | Authentication security: hashed passwords (bcrypt) and secure session management | Non-Functional | System Requirement | High | Conform to OWASP recommendations |
| NF-02 | Transport security: HTTPS everywhere (TLS) for all requests | Non-Functional | System Requirement | High | Enforce HSTS and secure cookies |
| NF-03 | Data encryption at rest for sensitive fields (verification documents, personal info) | Non-Functional | System Requirement | High | Use AES-256 or equivalent |
| NF-04 | Performance: Page load time < 2s for common pages under expected load | Non-Functional | System Requirement | Medium | Define metrics and testing thresholds |
| NF-05 | Scalability: Support growth from pilot (hundreds) to thousands of users | Non-Functional | System Requirement | Medium | Design DB indexing and horizontal scaling plan |
| NF-06 | Availability: 99.5% uptime target for production | Non-Functional | System Requirement | Medium | Include monitoring and failover strategy |
| NF-07 | Backup & Recovery: Daily backups and tested restore process | Non-Functional | System Requirement | High | Backup retention policy documented |
| NF-08 | Privacy & Compliance: Compliance with local data protection laws and university policies | Non-Functional | System Requirement | High | Include data deletion and user consent flows |
| NF-09 | Usability: Intuitive UI supporting common student workflows | Non-Functional | User Requirement | High | Usability testing with students during sprints |
| NF-10 | Accessibility: Meet WCAG 2.1 AA where feasible | Non-Functional | System Requirement | Medium | Keyboard nav, alt-text, color contrast |
| NF-11 | Maintainability: Clean codebase, modular architecture, and documented APIs | Non-Functional | System Requirement | Medium | Use version control, code reviews, CI pipelines |
| NF-12 | Real-time updates: Real-time notifications and chat (WebSocket or polling) | Non-Functional | System Requirement | Medium | Choose an approach appropriate for MVP |
| NF-13 | Rate limiting & abuse prevention to protect from spam and bots | Non-Functional | System Requirement | High | Apply throttling per IP/account |
| NF-14 | Testing: Automated unit tests & integration tests for core features | Non-Functional | System Requirement | High | Test coverage targets defined by team |
| NF-15 | Logging & Monitoring: Centralized logs, alerts for errors and suspicious activity | Non-Functional | System Requirement | High | Integrate with monitoring services |
| NF-16 | Internationalization / Localization support (future) | Non-Functional | System Requirement | Low | Design text resources for translation |
| NF-17 | Mobile responsiveness and support for major modern browsers | Non-Functional | User Requirement | High | Responsive CSS and mobile-first design |
| NF-18 | Data retention & deletion policy (users can request data deletion) | Non-Functional | System Requirement | High | Comply with privacy regulations and university rules |

---
## Structured Specifications (Role 4)

Three critical functional requirements:

---

### **FR-01 — User Registration and Verification**

**Function:**  
Register new users (students or companies/organizations) and verify their identity or legitimacy.

**Description:**  
Enables students and companies to create accounts with different verification processes.  
Students verify their active student status using a university email or proof of enrollment.  
Companies and organizations verify their authenticity through official domain emails or admin approval.  
Verification ensures a safe and trustworthy environment for genuine users.

**Inputs:**  
User type (student/company), full name, email, password, and optional proof documents (student ID, business registration, etc.).

**Source:**  
Information entered by the user through the registration form.

**Outputs:**  
Verified user account record and confirmation message upon successful verification.

**Destination:**  
User-account database and authentication subsystem.

**Action:**  
When a user submits the registration form, the system validates all inputs.  
If valid, it creates an unverified account and initiates verification.  
- **Students:** receive a verification link or upload proof.  
- **Companies:** receive an email sent to an official domain or await admin approval.  
Upon completion, the account status updates to *verified* and role-based permissions are enabled.

**Requires:**  
Working email service, user database, and admin dashboard for company verification.

**Precondition:**  
The user must not already have an existing account, and the system must be online.

**Postcondition:**  
A verified user account (student or company) exists with the correct access permissions.

**Side effects:**  
Verification emails and admin notifications are generated.

---

### **FR-02 — Opportunity and Project Posting (Students and Companies)**

**Function:**  
Allow verified students and approved companies/organizations to post opportunities or collaboration projects.

**Description:**  
Provides a shared space where students and organizations can post ideas, projects, internships, volunteering, or freelance tasks.  
This function enables interaction between students seeking experience and companies seeking collaboration, while maintaining a student-first environment.

**Inputs:**  
Title, description, category (project/job/volunteering/freelancing), required skills, deadline, duration, optional attachments or images.

**Source:**  
Information entered by verified student or company user.

**Outputs:**  
A new post visible in the opportunity feed.

**Destination:**  
Opportunity database and feed display.

**Action:**  
The user opens the “Create Post / Opportunity” form, fills required fields, and submits.  
The system validates inputs, saves the post, and publishes it in the feed.  
Company posts are limited to specific sections and may be reviewed before publication.

**Requires:**  
Verified user account with proper role-based access.

**Precondition:**  
User (student or company) is logged in and verified.

**Postcondition:**  
New post appears in the opportunities feed for eligible users.

**Side effects:**  
Notifications may be sent to followers or interested students.

---

### **FR-03 — Collaboration Requests and Messaging**

**Function:**  
Enable communication and collaboration between students and organizations through requests and in-app messaging.

**Description:**  
Allows students to send requests to join projects or opportunities and exchange messages with project owners or company representatives.  
Supports direct communication to coordinate teamwork or discuss details securely within the platform.

**Inputs:**  
Project ID, message content, optional file attachments (e.g., CV, portfolio, document).

**Source:**  
Data entered by the logged-in student or company user.

**Outputs:**  
Collaboration request record, confirmation message, and chat thread.

**Destination:**  
Messaging database and notification service.

**Action:**  
When a student clicks “Request to Join” or “Message,” the system validates inputs, stores the request, and notifies the recipient.  
If the recipient accepts, both users gain access to a private chat thread for continued communication.  
All messages are timestamped and stored chronologically.

**Requires:**  
Active verified accounts and a valid project post.

**Precondition:**  
The project or opportunity is active, and both users are authenticated.

**Postcondition:**  
Collaboration request and chat records are stored and visible to both users.

**Side effects:**  
Email or in-app notifications are sent when new messages arrive.








# Role 5: Requirements Prioritization

## Functional Requirements Prioritization

Below is the prioritization of the identified Functional Requirements for the system. Each requirement has been classified as **Mandatory (M)**, **Nice-to-Have (N)**, or **Superfluous (S)**, based on importance for achieving the main goals of the project, feasibility within the initial development timeline, and direct system necessity.

| Requirement ID | Requirement Description                         | Priority |
|----------------|-------------------------------------------------|----------|
| FR-01          | User Registration and Verification (Students + Companies) | M        |
| FR-02          | Opportunity and Project Posting for verified users | M        |
| FR-03          | Collaboration Requests and Messaging between users | M        |

### Justification for Prioritization

- **FR-01** is **Mandatory (M)** because the system cannot function without verified authentic users. This directly supports trust, user legitimacy, and security. Without this requirement, all other system features collapse since no user identity is validated.  

- **FR-02** is **Mandatory (M)** because the core purpose of the platform is to allow students and companies to publish opportunities and projects. This requirement is the central value proposition of the platform and enables the main functionality.  

- **FR-03** is **Mandatory (M)** because collaboration and communication between students and companies is the primary utility of the system after opportunities are posted. Without messaging and collaboration requests, the system becomes a static listing platform and loses its interaction component.  

### Summary

All three functional requirements are classified as **Mandatory (M)** because each one is essential for the system to achieve its main goal — connecting students with organizations through verified collaboration opportunities. Removing any of these requirements would break the core workflow of the platform and therefore none of them can be considered Nice-to-Have (N) or Superfluous (S) in the context of this project scope.

---

**Prepared by: Rozh Zhila**
 Role 5: Requirements Prioritization section
