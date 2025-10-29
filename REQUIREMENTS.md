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
