## Structured Specifications (Role 4)

Three key functional requirements:

---

### **FR-01 — Student Registration and Verification**

**Description:**  
The system should allow new users (students) to register an account and verify their student status before accessing the platform.

**Purpose:**  
To ensure that only genuine, active students can join the platform, keeping it safe and trustworthy.

**Inputs:**  
Full name, university email, password, optional student ID or proof of enrollment.

**Outputs:**  
Verification email or code; new verified student account stored in the database.

**Preconditions:**  
- User has an active student email or valid proof of enrollment.  
- Internet connection is available.

**Trigger:**  
Student clicks **“Sign Up”** and submits registration form.

**Normal Flow:**  
1. Student enters registration details.  
2. System validates all fields.  
3. System sends a verification email or code to the provided address.  
4. Student clicks the link or enters the code to confirm their identity.  
5. System activates the account and redirects to the student dashboard.

**Alternative Flow:**  
- Invalid email or missing information → show error.  
- Verification code expired → allow resending a new one.

**Postconditions:**  
Verified student account is active, granting access to collaboration features.

**Exceptions:**  
Email delivery fails → show “resend verification” option.

**Related Non-Functional Requirements:**  
Security (student data encryption), availability (response within 3 seconds).

---

### **FR-02 — Opportunity and Project Posting (Students and Companies)**

**Description:**  
The system shall allow verified students, companies, and organizations to create and publish posts such as projects, collaboration ideas, volunteering opportunities, or short-term tasks.

**Purpose:**  
To provide a shared space where students can find real opportunities and where companies can post relevant projects while maintaining the student-focused environment.

**Inputs:**  
Post title, description, category (project / job / volunteering / freelancing), required skills, duration, deadline, and optional attachments or links.

**Outputs:**  
A visible post stored in the database and displayed in the opportunity feed.

**Preconditions:**  
- User account (student, company, or organization) is verified and logged in.  
- For companies/organizations, access is limited to their designated posting section.

**Trigger:**  
User clicks **“Create Post / Opportunity”** and submits the form.

**Normal Flow:**  
1. User (student or company) opens the posting form.  
2. Fills in all required fields and uploads optional attachments.  
3. System validates all inputs.  
4. System saves the post with status **“Published.”**  
5. The post becomes visible in the opportunities feed (students see all posts; companies see limited interaction options).  
6. Students can view, apply for, or request to join posted opportunities.

**Alternative Flow:**  
- Missing required fields → show validation errors.  
- User saves as draft → post not visible until published.  
- Company post flagged for review → hidden until approved by admin.

**Postconditions:**  
A new opportunity or project post is saved and visible to authorized users according to their role.

**Exceptions:**  
Database or upload failure → system displays “Unable to save post, please retry.”

**Related Non-Functional Requirements:**  
Usability (clear, role-based posting interface), security (restricted company permissions), reliability (data saved accurately).
--

### **FR-03 — Collaboration Requests and Messaging**

**Description:**  
The system shall allow students to send collaboration requests and communicate through an in-app messaging feature.

**Purpose:**  
To enable direct communication and teamwork among students who wish to collaborate on projects or ideas.

**Inputs:**  
Project ID, message content, optional file attachments or links.

**Outputs:**  
Collaboration request record, notification to project owner, and message thread between participants.

**Preconditions:**  
- Both users (sender and receiver) are verified students.  
- The project post is active.

**Trigger:**  
Student clicks **“Request to Join”** or **“Message”** on a project post.

**Normal Flow:**  
1. Student selects a project and sends a request or message.  
2. System validates inputs and stores the request.  
3. The project owner receives a notification.  
4. If accepted, both users gain access to the shared message thread.  
5. They can continue chatting and sharing files in-app.

**Alternative Flow:**  
- Invalid attachment → show error message.  
- Request rejected → sender receives rejection notice.  

**Postconditions:**  
Collaboration request and chat history are saved and accessible to both users.

**Exceptions:**  
Server downtime → “Message failed, please try again later.”

**Related Non-Functional Requirements:**  
Privacy (messages visible only to participants), performance (message delivery under 2 seconds).

---
