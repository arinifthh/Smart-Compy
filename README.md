## **SmartComply System - Detailed Breakdown**

**1. Project Name:** SmartComply

**2. Core Objective:**
To digitalize and streamline compliance processes (e.g., ISO 22000, HALAL, GMP, HACCP, OSH, Food Safety) for organizations, moving away from manual, paper-based audit and documentation workflows.

**3. Current Challenges/Pain Points (Identified):**
* Inefficiencies in workflows.
* High risk of human error.
* Poor traceability of audits and documentation.
* Manual, paper-based processes.

**4. Proposed Solutions/Key Features:**
* **Automated Form Generation:** For various compliance standards.
* **Digital On-site Audits:** Via mobile devices (web-based, not native app).
* **Centralized Document Filing & Reporting:** For all compliance-related data.
* **Customizable Multi-Format Form Support:** (Admin's role).
* **Real-time Filing:** Of audit data.
* **Dashboard-Based Performance Monitoring:** For quality assurance teams, auditors, and managers.
* **Audit-Readiness & Continuous Compliance:** Empowering users to maintain standards.

**5. User Roles and High-Level Responsibilities:**
* **Admin:**
    * Dynamic form builder 
    * User management (creating/managing accounts for Managers, Auditors).
    * System configuration.
      
* **Manager:**
    * Oversees compliance status.
    * Accesses dashboards for performance monitoring.
    * Views audit reports.
      
* **Auditor:**
    * Conducts digital audits on-site using mobile devices (web-based).
    * Fills out dynamic forms.
    * Records audit findings and scores.
    * Documents corrective actions for non-compliant areas.
    * Performs follow-up audits.
    * Obtains shop owner verification/signature.
    * Real-time filing of audit data.

**6.1. Core Audit Process Flow:**
* **Form Assignment:** Auditors receive assigned forms/audits.
* **On-site Audit:** Auditor opens the form on a mobile device (web browser).
* **Form Filling:** Auditor inputs responses to dynamic questions.
* **Scoring:** System calculates marks based on auditor's inputs.
* **Compliance Level Determination:** Based on the calculated score, the system categorizes the compliance level.
* **Corrective Action (if needed):** If the score is low (Concern, Fail, Issuance), the auditor records text-based corrective actions.
* **Shop Owner Verification:** Capture shop owner's signature.
* **Submission:** Finalize and submit the audit.
* **Follow-up Audit Trigger (if needed):** If corrective actions were recorded, a follow-up audit might be scheduled, focusing only on the low-marked sections.

**6.2. Key Functionalities for the Auditor Module:**

* **View Assigned Audits/Forms:** Dashboard/list of pending audits.
* **Dynamic Form Rendering:** Displaying the forms built by the Admin (initially dummy/hardcoded).
* **Question Types:**
    * Score-based questions (e.g., numerical input, dropdowns mapping to scores).
    * Yes/No/N/A (mapping to scores).
    * Text input (for observations, notes).
    * Image/photo upload (for evidence).
* **Scoring Logic Implementation:**
    * Calculation of total/section scores.
    * Mapping scores to compliance levels:
        * **80% and above:** EXCELLENT
        * **70% - 79%:** SATISFACTORY
        * **65% - 69%:** CONCERN
        * **60% - 64%:** FAIL
        * **Below 60%:** ISSUANCE OF TERMINATION LETTER
* **Corrective Action Section:** A dedicated area within the audit form to detail required actions when scores are low.
* **Follow-up Audit Mechanism:**
    * Ability to mark an audit for follow-up.
    * When a follow-up audit is created, it should pre-populate with only the questions/sections that were "Concern," "Fail," or "Issuance" in the previous audit.
* **Shop Owner Signature Capture:**
    * Initial implementation: text field for name and acknowledgment.
    * Future enhancement: basic drawing pad for digital signature (e.g., using JavaScript).
* **Audit History & Reporting (Auditor View):**
    * Ability to view past audits they conducted.
    * Basic summary of audit results.

### **Phase 1: Project Setup and Core Database Structure**

* **Step 1.1: Create New .NET MVC Project:**
    * "How do I create a new .NET 8 MVC project named `SmartComply.Web` from the terminal?"
* **Step 1.2: Identify Core Entities for the Auditor Module & Database Setup:**
    * "Considering the Auditor's needs (audits, forms, questions, responses, corrective actions, signatures), what are the essential database entities/models I should start with? How do I set up Entity Framework Core for these models with SQL Server?"
    * We'll likely need models like:
        * `User` (for Admin, Manager, Auditor roles)
        * `Audit` (to represent an instance of an audit conducted)
        * `FormTemplate` (basic structure of a dynamic form, even if dummy)
        * `FormQuestion` (questions within a form, with types like text, score, etc.)
        * `AuditResponse` (auditor's answer to a specific question in an audit)
        * `CorrectiveAction` (details for follow-up)
        * `Signature` (for shop owner)
* **Step 1.3: Database Migrations:**
    * "How do I create an initial migration for these models and update my SQL Server database?"

### **Phase 2: Authentication & Basic Role Management**

* **Step 2.1: Implement User Registration and Login:**
    * "How do I set up basic user registration and login functionality using ASP.NET Core Identity for our `User` model?"
* **Step 2.2: Implement Basic Role Management:**
    * "How can I introduce simple roles (Admin, Manager, Auditor) and assign them to users, and then use `[Authorize(Roles="Auditor")]` to secure Auditor-specific actions?"

### **Phase 3: Core Auditor Module - Dummy Dynamic Forms**

* **Step 3.1: Create Dummy Dynamic Form Structure:**
    * "Let's start with a hardcoded or seeded dummy dynamic form. How can I represent a simple audit form with a few questions (e.g., a 'Yes/No' question, a 'Score out of 10' question, and a 'Text observation' question) that an auditor can fill out?"
* **Step 3.2: Displaying and Filling Audit Forms:**
    * "How do I create an `AuditorController` and a view that can render this dummy dynamic form, allowing the auditor to input their responses?"
* **Step 3.3: Calculating Scores & Compliance Levels:**
    * "Once the auditor submits the form, how do I process their responses, calculate a total score, and determine the compliance level (EXCELLENT, SATISFACTORY, etc.) based on our defined percentages?"
* **Step 3.4: Capturing Corrective Actions:**
    * "How do I add a section to the audit form where the auditor can input corrective actions, especially if the score is low?"
* **Step 3.5: Implementing Shop Owner Verification (Basic):**
    * "For now, how can I add a simple text field for 'Shop Owner Name' and a checkbox for 'Acknowledged' as a placeholder for the signature?"

