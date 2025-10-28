## Structured Specifications (Role 4)

Three key functional requirements:

---

### **FR-01 — User Registration and Verification**

**Description:**  
The system shall allow new users (students or companies) to register an account, verify their email, and access their profile dashboard.

**Rationale:**  
Registration enables unique, secure access to personalized features and stored data.

**Inputs:**  
User type (student/company), name, email, password, optional organization name.

**Outputs:**  
Confirmation email; new verified account record in the database.

**Preconditions:**  
- User has an unused email address.  
- Internet connection is available.

**Trigger:**  
User clicks "Sign Up" and submits the registration form.

**Normal Flow:**  
1. User selects role (student or company).  
2. Fills registration form and submits.  
3. System validates data (email format, password strength).  
4. System stores user info with “unverified” status.  
5. System sends verification email.  
6. User clicks verification link.  
7. System marks user as verified and redirects to dashboard.

**Alternative Flow:**  
- Email invalid → show error and reject submission.  
- Verification link expired → prompt resend.  

**Postconditions:**  
User has a verified account and can access profile functions.

**Exceptions:**  
Email delivery failure → display resend option.  

**Related Non-Functional Requirements:**  
Security (password hashing), availability (system responds within 3 seconds).

---

### **FR-02 — Job/Task Posting by Companies**

**Description:**  
The system shall allow verified companies to create and publish job or task listings that students can view and apply for.

**Rationale:**  
Posting jobs connects employers to students and forms the core platform purpose.

**Inputs:**  
Job title, description, required skills, location, duration, deadline.

**Outputs:**  
A visible job listing stored in the database.

**Preconditions:**  
Company account must be verified and logged in.

**Trigger:**  
Company user selects “Create Job Post” and submits the form.

**Normal Flow:**  
1. Company opens job creation page.  
2. Enters job details.  
3. System validates all mandatory fields.  
4. System saves job post with status “Published.”  
5. Post appears immediately in student listings.

**Alternative Flow:**  
- Missing required info → system shows error.  
- Save as draft → post not yet visible.

**Postconditions:**  
New job listing exists in the system, visible to eligible users.

**Exceptions:**  
Database error → display “Unable to save post, please retry.”

**Related Non-Functional Requirements:**  
Usability (simple form layout), reliability (data saved correctly).

---

### **FR-03 — Application and Messaging**

**Description:**  
The system shall allow students to apply for a job and send messages to the employer related to that application.

**Rationale:**  
Direct communication between students and employers simplifies hiring and improves response time.

**Inputs:**  
Job ID, cover letter, optional attachments (CV, portfolio).

**Outputs:**  
Application record, confirmation message, and message thread between student and employer.

**Preconditions:**  
Student account verified; job post active.

**Trigger:**  
Student clicks “Apply” and submits an application.

**Normal Flow:**  
1. Student opens job listing.  
2. Clicks “Apply,” fills form, uploads file (optional).  
3. System validates inputs.  
4. System saves application data.  
5. Company receives notification.  
6. Student and company can exchange messages through an in-app chat.

**Alternative Flow:**  
- Invalid file upload → show error.  
- Job expired → prevent application.

**Postconditions:**  
Application stored, visible to both student and company.

**Exceptions:**  
Server downtime → temporary “Try again later” message.

**Related Non-Functional Requirements:**  
Security (file type validation), performance (messaging delay < 2 seconds).

---
