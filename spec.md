953104 Web User Interface Design and Development — Semester: 1/2025 
LAB 8: Event Handling, Forms & Validation 

 

Objective 

Students will practice: 

 Selecting DOM elements and handling submit/input/change events 

 Using native HTML5 validation (required, type, pattern, minlength) 

 Writing custom JS validation with event.preventDefault() and setCustomValidity() 

 Providing inline feedback (messages, styles) and success states 

Lab Instructions 

The LAB08 instruction and lab resources are posted on MS Teams channel LAB08 – Forms & Validation of the subject 953104. 

Download the zipped file of resources-lab08. 

There are 4 assignments according to this sheet. 

LAB08 is worth 19 points in total. 

Rename your folder as “se104_studentID_lab8” (e.g., se104_4921150xx_lab8). 

During the lab, put your answer files in the folder you created. When you finish all questions, zip the folder. 

Assignment Submission: Upload your solutions to Mango assignments. Submissions later than the due date receive 50% penalty. After the close date, submissions are not accepted. If requested, be prepared to demo your work on your computer. 

Problems 

Q1. Sign‑in — Native HTML5 Validation (5 pts) 

Goal: Use native validation only (no JS error messages). 

Create q1_native.html with a Sign-in form. 

Inputs: email (type="email" required), password (type="password" minlength="8" required). 

Add visible <label> for accessibility; keep markup semantic. 

Valid inputs allow submit to the same page (action="#"). Test empty/invalid/valid. 

Q2. Sign‑up — Custom JS Validation + Inline Feedback (7 pts) 

Goal: Replace browser popups with your own inline feedback. 

Open q2_signup.html from the resource folder. 

Use <input type="text"> for email (avoid native email popups). Use <input type="password"> for password. 

Add <span class="error"> below each field for messages. 

Add .is-valid / .is-invalid classes for green/red borders. 

On input events: validate live. 

Rules — Email: required; must contain '@' and at least one '.' after it. Password: required; ≥ 8 characters and at least one number. 

On submit: set border feedback; use event.preventDefault() to block invalid submissions; do not rely on native popups. 

Q3. Terms Checkbox + Disabled Submit (3 pts) 

Goal: Use DOM + events to control the submit button state. 

Save q2_signup.html as q3_terms.html. 

Add a required “I agree to Terms” checkbox. 

Disable the submit button by default; enable only when: (a) email and password pass Q2 rules, and (b) the checkbox is checked. 

Use input/change events to toggle disabled state. 

Q4. Review Page + Success Messaging (4 pts) 

Goal: Provide a clear success confirmation without exposing sensitive data. 

Open q4_review.html from the resource folder (or create new). 

Reuse validated form logic from Q2/Q3 (or import via <script src="...">). 

On successful submit (no prevents): 

Option A (single-page): Replace the form with a green success banner and show a masked email (e.g., jo***@mail.com). Do not show password. 

Option B (redirect): Navigate to review.html with masked email passed via querystring; show success banner there. Do not pass or display password. 

Expected output: a non-blocking success banner and masked email. 

Points & Rubric (19 pts total) 

Q1: 5 pts 

Q2: 7 pts 

Q3: 3 pts 

Q4: 4 pts 

Deductions (per file): −1 incorrect output; −1 not following constraints; −1 missing labels/accessibility. 