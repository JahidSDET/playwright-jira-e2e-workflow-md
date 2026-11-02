# 🧪 Test Plan: General Forms Functionality
**Application:** Way2Automation Practice Lab — Forms & Common Elements  
**URL:** https://way2automation.com/practicesite/#forms  
**Prepared By:** QA Automation Team  
**Date:** 2026-04-23  
**Version:** 1.0

---

## 1. Introduction

This document describes the test plan for the **Forms and Common Elements** section of the Way2Automation Practice Lab. The page contains a single form with text inputs, a dropdown, radio buttons, checkboxes, a range slider, a textarea, and a submit button, all of which must be validated for functional correctness, input validation, usability, and robustness.

---

## 2. Scope

### In Scope
| Component | Description |
|---|---|
| Full Name field | Free-text input |
| Email field | Email-format input |
| Password field | Masked input with minimum-length constraint |
| Automation Tool dropdown | Single-select: Selenium, Playwright, Cypress, Robot Framework |
| Experience Level radio group | Single-select: Beginner (default), Intermediate, Advanced |
| Practice Topics checkboxes | Multi-select: Forms (default), Alerts, Frames, Windows |
| Confidence Score slider | Range control, default value 5 |
| Notes textarea | Free-text multi-line input |
| Submit Practice Form button | Form submission trigger |
| Submission status indicator | Post-submit feedback element |

### Out of Scope
- Back-end data persistence (page states all data stays in the browser)
- Authentication / session management
- File upload section (`#file-upload`)
- Frames section (`#frames`)
- Windows section (`#windows`)

---

## 3. Test Objectives

- Verify all form fields accept valid inputs and reject invalid inputs correctly.
- Verify default values are pre-populated as expected.
- Verify the submit action produces the correct status feedback.
- Verify edge-case and boundary inputs are handled gracefully.
- Verify usability attributes (tab order, labels, placeholders, accessibility roles).

---

## 4. Test Environment

| Item | Value |
|---|---|
| Browser | Chromium (Desktop Chrome device profile) |
| Framework | Playwright + TypeScript |
| Base URL | https://way2automation.com/practicesite/#forms |
| Execution | Headless (CI) / Headed (debug) |

---

## 5. Test Cases

### 5.1 Full Name Field

---

#### TC-FN-001 — Valid full name submitted successfully
- **Priority:** High
- **Preconditions:** Page is loaded and form is in default state.
- **Test Steps:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
  2. Click the **Full name** field.
  3. Type `John Doe`.
  4. Fill remaining required fields with valid data.
  5. Click **Submit Practice Form**.
- **Test Data:** `John Doe`
- **Expected Result:** Form submits successfully; status indicator confirms submission.

---

#### TC-FN-002 — Full name field is empty on submit
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Leave the **Full name** field empty.
  2. Fill all other fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** *(empty)*
- **Expected Result:** Submission is blocked or a validation message indicates the field is required.

---

#### TC-FN-003 — Full name with only whitespace
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `     ` (spaces only) in the **Full name** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `"     "` (5 spaces)
- **Expected Result:** Submission is blocked or whitespace-only input is rejected with a validation message.

---

#### TC-FN-004 — Full name with special characters
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `O'Brien-García` in the **Full name** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `O'Brien-García`
- **Expected Result:** Name containing apostrophes, hyphens, and accented characters is accepted.

---

#### TC-FN-005 — Full name at maximum reasonable length (255 characters)
- **Priority:** Low
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type a 255-character string in the **Full name** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `A` × 255
- **Expected Result:** Input is accepted without truncation errors or browser crashes.

---

### 5.2 Email Field

---

#### TC-EM-001 — Valid email accepted
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `qa@example.com` in the **Email** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `qa@example.com`
- **Expected Result:** Form submits successfully.

---

#### TC-EM-002 — Invalid email format rejected
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `notanemail` in the **Email** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `notanemail`
- **Expected Result:** Submission is blocked; a validation message indicates an invalid email format.

---

#### TC-EM-003 — Email missing domain
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `user@` in the **Email** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `user@`
- **Expected Result:** Validation error for incomplete email address.

---

#### TC-EM-004 — Email with subdomain accepted
- **Priority:** Low
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `user@mail.qa.example.co.uk` in the **Email** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `user@mail.qa.example.co.uk`
- **Expected Result:** Form accepts complex but valid email addresses.

---

#### TC-EM-005 — Empty email field on submit
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Leave the **Email** field empty.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** *(empty)*
- **Expected Result:** Submission blocked; required-field validation message shown.

---

### 5.3 Password Field

---

#### TC-PW-001 — Valid password (≥6 characters) accepted
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `Secure1` in the **Password** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `Secure1`
- **Expected Result:** Form submits successfully.

---

#### TC-PW-002 — Password shorter than 6 characters rejected
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `abc` in the **Password** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `abc` (3 chars)
- **Expected Result:** Validation error: "Minimum 6 characters" (or equivalent message).

---

#### TC-PW-003 — Password exactly 6 characters accepted (boundary)
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `abcdef` in the **Password** field.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `abcdef` (6 chars)
- **Expected Result:** Form accepts the minimum-length password and submits.

---

#### TC-PW-004 — Password field masks input
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `Secret123` in the **Password** field.
  2. Observe the rendered characters in the field.
- **Test Data:** `Secret123`
- **Expected Result:** Input is masked (displayed as dots or asterisks).

---

#### TC-PW-005 — Empty password field on submit
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Leave the **Password** field empty.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** *(empty)*
- **Expected Result:** Submission blocked; required-field validation message shown.

---

### 5.4 Automation Tool Dropdown

---

#### TC-DD-001 — Default selection is "Selenium"
- **Priority:** High
- **Preconditions:** Page is loaded fresh.
- **Test Steps:**
  1. Observe the **Automation tool** dropdown without interacting with it.
- **Test Data:** N/A
- **Expected Result:** Dropdown displays "Selenium" as the selected option.

---

#### TC-DD-002 — Select "Playwright" from dropdown
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Open the **Automation tool** dropdown.
  2. Select "Playwright".
  3. Verify the selection is reflected.
- **Test Data:** `Playwright`
- **Expected Result:** Dropdown shows "Playwright" as selected.

---

#### TC-DD-003 — Select "Cypress" from dropdown
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Open the **Automation tool** dropdown.
  2. Select "Cypress".
- **Test Data:** `Cypress`
- **Expected Result:** Dropdown shows "Cypress" as selected.

---

#### TC-DD-004 — Select "Robot Framework" from dropdown
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Open the **Automation tool** dropdown.
  2. Select "Robot Framework".
- **Test Data:** `Robot Framework`
- **Expected Result:** Dropdown shows "Robot Framework" as selected.

---

#### TC-DD-005 — All four options are available
- **Priority:** Medium
- **Preconditions:** Page is loaded.
- **Test Steps:**
  1. Open the **Automation tool** dropdown.
  2. List all available options.
- **Expected Result:** Exactly four options: Selenium, Playwright, Cypress, Robot Framework.

---

### 5.5 Experience Level Radio Buttons

---

#### TC-RB-001 — Default selection is "Beginner"
- **Priority:** High
- **Preconditions:** Page is loaded fresh.
- **Test Steps:**
  1. Observe the **Experience level** radio group without interaction.
- **Expected Result:** The "Beginner" radio button is checked by default.

---

#### TC-RB-002 — Select "Intermediate"
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Click the **Intermediate** radio button.
  2. Verify selection.
- **Expected Result:** "Intermediate" is selected; "Beginner" is deselected.

---

#### TC-RB-003 — Select "Advanced"
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Click the **Advanced** radio button.
  2. Verify selection.
- **Expected Result:** "Advanced" is selected; previous selection is deselected.

---

#### TC-RB-004 — Only one radio button can be selected at a time
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Click "Intermediate".
  2. Click "Advanced".
  3. Verify that only "Advanced" is checked.
- **Expected Result:** Mutual exclusivity enforced; only one radio is selected at any time.

---

### 5.6 Practice Topics Checkboxes

---

#### TC-CB-001 — Default "Forms" checkbox is checked
- **Priority:** High
- **Preconditions:** Page is loaded fresh.
- **Test Steps:**
  1. Observe the **Practice topics** checkbox group.
- **Expected Result:** The "Forms" checkbox is checked by default; Alerts, Frames, Windows are unchecked.

---

#### TC-CB-002 — Check all four topics
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Check **Alerts**, **Frames**, and **Windows** (Forms already checked).
  2. Verify all four are checked.
- **Expected Result:** All four checkboxes show a checked state simultaneously.

---

#### TC-CB-003 — Uncheck all topics
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Uncheck the **Forms** checkbox.
  2. Verify all checkboxes are unchecked.
- **Expected Result:** All checkboxes are unchecked; form allows zero selections (or shows a validation message if required).

---

#### TC-CB-004 — Check then uncheck a topic
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Check **Alerts**.
  2. Uncheck **Alerts**.
  3. Verify "Alerts" is unchecked; "Forms" remains checked.
- **Expected Result:** Toggle behavior works correctly; other checkboxes are unaffected.

---

#### TC-CB-005 — Submit with multiple topics selected
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Check **Frames** and **Windows** in addition to the default **Forms**.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Expected Result:** Form submits successfully with multiple checkboxes selected.

---

### 5.7 Confidence Score Slider

---

#### TC-SL-001 — Default slider value is 5
- **Priority:** High
- **Preconditions:** Page is loaded fresh.
- **Test Steps:**
  1. Read the **Confidence score** status label without interacting with the slider.
- **Expected Result:** Status label shows `5`.

---

#### TC-SL-002 — Drag slider to minimum value (1)
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Move the slider to its leftmost position.
  2. Read the status label.
- **Expected Result:** Status label updates to `1` (or the defined minimum).

---

#### TC-SL-003 — Drag slider to maximum value (10)
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Move the slider to its rightmost position.
  2. Read the status label.
- **Expected Result:** Status label updates to `10` (or the defined maximum).

---

#### TC-SL-004 — Slider value updates dynamically
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Move the slider to position `7`.
  2. Observe the **Confidence score** status label.
- **Test Data:** Slider value = `7`
- **Expected Result:** Status label reflects `7` immediately without requiring a page reload.

---

#### TC-SL-005 — Submit with non-default slider value
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Move the slider to `9`.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Expected Result:** Form submits successfully; the slider value of `9` is part of the submission.

---

### 5.8 Notes Textarea

---

#### TC-NT-001 — Valid notes accepted
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Click the **Notes** textarea.
  2. Type `Testing the form with Playwright.`
  3. Fill remaining fields with valid data.
  4. Click **Submit Practice Form**.
- **Test Data:** `Testing the form with Playwright.`
- **Expected Result:** Form submits successfully with the note content.

---

#### TC-NT-002 — Notes field accepts multi-line input
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `Line 1\nLine 2\nLine 3` into the **Notes** textarea.
  2. Verify line breaks are preserved.
- **Test Data:** Multi-line text
- **Expected Result:** Textarea renders line breaks correctly.

---

#### TC-NT-003 — Submit with empty notes
- **Priority:** Medium
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Leave the **Notes** textarea empty.
  2. Fill remaining required fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** *(empty)*
- **Expected Result:** Form submits successfully (Notes is optional) or shows a graceful validation message if required.

---

#### TC-NT-004 — Notes with special characters and symbols
- **Priority:** Low
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Type `<script>alert('xss')</script> & "quotes" 日本語` into the **Notes** textarea.
  2. Fill remaining fields with valid data.
  3. Click **Submit Practice Form**.
- **Test Data:** `<script>alert('xss')</script> & "quotes" 日本語`
- **Expected Result:** Input is accepted as plain text; no script execution occurs (XSS prevention). Unicode characters are preserved.

---

### 5.9 Submit Button & Submission Feedback

---

#### TC-SB-001 — Full valid form submission
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Fill **Full name**: `Jane Smith`
  2. Fill **Email**: `jane@example.com`
  3. Fill **Password**: `Passw0rd`
  4. Select **Automation tool**: `Playwright`
  5. Select **Experience level**: `Intermediate`
  6. Check **Practice topics**: `Forms`, `Alerts`
  7. Move **Confidence score** slider to `8`
  8. Fill **Notes**: `Full form submission test.`
  9. Click **Submit Practice Form**.
- **Test Data:** All fields valid
- **Expected Result:** Status indicator confirms successful submission (e.g., success message or visual feedback).

---

#### TC-SB-002 — Submit with only required fields filled
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Fill only the minimum required fields (Full name, Email, Password) with valid data.
  2. Leave optional fields at their defaults.
  3. Click **Submit Practice Form**.
- **Expected Result:** Form submits successfully.

---

#### TC-SB-003 — Submit button is visible and clickable
- **Priority:** High
- **Preconditions:** Page is loaded.
- **Test Steps:**
  1. Scroll to the **Submit Practice Form** button.
  2. Verify it is visible and enabled.
- **Expected Result:** Button is rendered, visible, and responds to click events.

---

#### TC-SB-004 — Status indicator updates after submission
- **Priority:** High
- **Preconditions:** Page is in default state.
- **Test Steps:**
  1. Fill all fields with valid data.
  2. Click **Submit Practice Form**.
  3. Observe the status element below the button.
- **Expected Result:** Status element transitions to a non-empty state confirming the submission result.

---

#### TC-SB-005 — Rapid double-click on submit
- **Priority:** Low
- **Preconditions:** Page is in default state with all fields valid.
- **Test Steps:**
  1. Fill all fields with valid data.
  2. Double-click **Submit Practice Form** rapidly.
- **Expected Result:** Form submits once; no duplicate submissions or errors.

---

### 5.10 Form-Level & Usability Tests

---

#### TC-UX-001 — Page loads with correct default state
- **Priority:** High
- **Preconditions:** Fresh page load.
- **Test Steps:**
  1. Navigate to the page URL.
  2. Verify all default values:
     - Full name, Email, Password, Notes: empty
     - Automation tool: `Selenium`
     - Experience level: `Beginner` selected
     - Practice topics: `Forms` checked
     - Confidence score: `5`
- **Expected Result:** All defaults match the specification.

---

#### TC-UX-002 — Tab navigation traverses all fields in order
- **Priority:** Medium
- **Preconditions:** Page is loaded.
- **Test Steps:**
  1. Click the **Full name** field.
  2. Press `Tab` repeatedly and record the focus order.
- **Expected Result:** Focus moves logically through Full name → Email → Password → Automation tool → Experience level options → Practice topic options → Confidence score slider → Notes → Submit.

---

#### TC-UX-003 — All fields have visible labels
- **Priority:** Medium
- **Preconditions:** Page is loaded.
- **Test Steps:**
  1. Inspect each form control for an associated visible label.
- **Expected Result:** Every input, select, radio group, checkbox group, slider, and textarea has a descriptive label visible on the page.

---

#### TC-UX-004 — Placeholder text is present in text inputs
- **Priority:** Low
- **Preconditions:** Page is loaded; fields are empty.
- **Test Steps:**
  1. Observe placeholder text in Full name, Email, Password, and Notes fields.
- **Expected Result:**
  - Full name: `Enter full name`
  - Email: `qa@example.com`
  - Password: `Minimum 6 characters`
  - Notes: `Write test notes`

---

#### TC-UX-005 — Form is keyboard-accessible (Enter to submit)
- **Priority:** Medium
- **Preconditions:** All fields filled with valid data; focus on last field or submit button.
- **Test Steps:**
  1. Fill all fields with valid data.
  2. Tab to the **Submit Practice Form** button.
  3. Press `Enter`.
- **Expected Result:** Form is submitted successfully via keyboard.

---

## 6. Entry and Exit Criteria

### Entry Criteria
- Application is accessible at the target URL.
- Playwright + TypeScript environment is installed and verified.
- All test cases have been reviewed and approved.

### Exit Criteria
- All **High** priority test cases pass.
- No open **High** or **Medium** severity defects remain.
- Test execution report is generated and reviewed.

---

## 7. Risk and Assumptions

| Risk | Mitigation |
|---|---|
| External URL availability | Retry logic + test skip on connectivity failure |
| Undocumented validation rules | Derive expected behavior from placeholder text and visible UI |
| Browser rendering differences | Chromium-only scope eliminates cross-browser variance |
| Dynamic content / animations | Use Playwright `waitFor` assertions to handle async UI updates |

---

## 8. Test Deliverables

- This Test Plan document (`test-plan.md`)
- Automated test scripts (`tests/*.spec.ts`)
- HTML Test Execution Report (`playwright-report/index.html`)

---

*End of Test Plan*
