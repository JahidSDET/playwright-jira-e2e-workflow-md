# 🧪 Test Cases: General Forms Functionality
**Application:** Way2Automation Practice Lab — Forms & Common Elements  
**URL:** https://way2automation.com/practicesite/#forms  
**Reference:** `prompts/test-plan.md`  
**Prepared By:** QA Automation Team  
**Date:** 2026-04-23  
**Version:** 1.0  
**Total Test Cases:** 35

---

## Table of Contents

| Section | Range |
|---|---|
| 1. Full Name Field | TC_001 – TC_005 |
| 2. Email Field | TC_006 – TC_010 |
| 3. Password Field | TC_011 – TC_015 |
| 4. Automation Tool Dropdown | TC_016 – TC_020 |
| 5. Experience Level Radio Buttons | TC_021 – TC_024 |
| 6. Practice Topics Checkboxes | TC_025 – TC_029 |
| 7. Confidence Score Slider | TC_030 – TC_034 |
| 8. Notes Textarea | TC_035 – TC_038 |
| 9. Submit Button & Submission Feedback | TC_039 – TC_043 |
| 10. Form-Level & Usability | TC_044 – TC_048 |

---

## 1. Full Name Field

---

### 🧾 Test Case: Valid Full Name Submitted Successfully

- **Test Case ID:** TC_001
- **Priority:** High
- **Objective:** Verify that a standard valid full name is accepted and the form submits successfully.

- **Pre-requisites:**
  - Browser is open and navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in its default state (no prior input)
  - Valid test data prepared: `John Doe`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads fully; the "Forms and Common Elements" section is visible with all form fields rendered.
  2. Click the **Full name** text field.
     - **Expectation:** The field receives focus; a cursor appears inside the input.
  3. Type `John Doe`.
     - **Expectation:** The text `John Doe` appears correctly in the field without truncation or character corruption.
  4. Fill in the **Email** field with `qa@example.com`, **Password** with `Passw0rd`, leave all other fields at defaults.
     - **Expectation:** Email and Password fields show the entered values; remaining defaults are unchanged.
  5. Click **Submit Practice Form**.
     - **Expectation:** The button responds to the click; no browser errors are thrown.
  6. Observe the status indicator below the submit button.
     - **Expectation:** The status element displays a non-empty success confirmation message.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Full Name Field Empty on Submit

- **Test Case ID:** TC_002
- **Priority:** High
- **Objective:** Verify that submitting the form with an empty Full Name field is blocked by validation.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible with all fields empty except pre-selected defaults.
  2. Leave the **Full name** field empty (do not click or type).
     - **Expectation:** Full name field remains blank with placeholder text `Enter full name` visible.
  3. Fill **Email** with `qa@example.com` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values without error.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form does not proceed to submission; focus is returned to the Full name field or a validation message is displayed.
  5. Inspect the Full name field or surrounding area for a validation message.
     - **Expectation:** A visible validation indicator (e.g., red border, tooltip, or inline message) states the field is required.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Full Name with Only Whitespace

- **Test Case ID:** TC_003
- **Priority:** Medium
- **Objective:** Verify that a Full Name containing only whitespace characters is rejected or treated as empty.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads successfully; form elements are visible.
  2. Click the **Full name** field and type five space characters (`     `).
     - **Expectation:** The field appears to contain content (spaces are not visually obvious), but input value consists only of whitespace.
  3. Fill **Email** with `qa@example.com` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form submission is blocked; the whitespace-only input is treated as an invalid or empty value.
  5. Observe the validation response for the Full name field.
     - **Expectation:** A validation message is displayed indicating the field is required or the input is invalid.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Full Name with Special Characters

- **Test Case ID:** TC_004
- **Priority:** Medium
- **Objective:** Verify that full names containing apostrophes, hyphens, and accented characters are accepted.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `O'Brien-García`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Click the **Full name** field and type `O'Brien-García`.
     - **Expectation:** All characters, including the apostrophe (`'`), hyphen (`-`), and accented `á`, are rendered correctly in the field without encoding artifacts.
  3. Fill **Email** with `qa@example.com` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form submits without validation errors triggered by the special characters.
  5. Observe the status indicator.
     - **Expectation:** A success confirmation is displayed; no script errors appear in the browser console.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Full Name at Maximum Length (255 Characters)

- **Test Case ID:** TC_005
- **Priority:** Low
- **Objective:** Verify that a 255-character full name is accepted without truncation errors or application crashes.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: string of 255 `A` characters

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Click the **Full name** field and paste/type 255 repetitions of `A`.
     - **Expectation:** The field accepts the entire string; no character is silently dropped (verify length ≥ 255 or field's `maxlength` attribute caps it gracefully).
  3. Fill **Email** with `qa@example.com` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  4. Click **Submit Practice Form**.
     - **Expectation:** The form either submits successfully or displays a clear max-length validation message; no JavaScript error or crash occurs.
  5. Observe browser console for errors.
     - **Expectation:** No uncaught exceptions related to field length.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 2. Email Field

---

### 🧾 Test Case: Valid Email Accepted

- **Test Case ID:** TC_006
- **Priority:** High
- **Objective:** Verify that a standard valid email address is accepted and allows successful form submission.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `qa@example.com`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form fields are visible.
  2. Fill **Full name** with `John Doe`.
     - **Expectation:** Name is entered correctly.
  3. Click the **Email** field and type `qa@example.com`.
     - **Expectation:** The email is entered without modification; placeholder disappears.
  4. Fill **Password** with `Passw0rd`.
     - **Expectation:** Password field accepts the value.
  5. Click **Submit Practice Form**.
     - **Expectation:** No email validation error appears.
  6. Observe the status indicator.
     - **Expectation:** Success confirmation message is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Invalid Email Format Rejected

- **Test Case ID:** TC_007
- **Priority:** High
- **Objective:** Verify that an email without the `@` symbol and domain is rejected by validation.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `notanemail`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  3. Click the **Email** field and type `notanemail`.
     - **Expectation:** The text is entered as-is; no automatic correction occurs.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form submission is blocked; focus moves to or highlights the Email field.
  5. Inspect the Email field for a validation message.
     - **Expectation:** A message such as "Please include an '@' in the email address" or equivalent is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Email Missing Domain After @ Symbol

- **Test Case ID:** TC_008
- **Priority:** High
- **Objective:** Verify that an email address missing the domain part (e.g., `user@`) is rejected.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `user@`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  3. Click the **Email** field and type `user@`.
     - **Expectation:** The string `user@` is entered verbatim.
  4. Click **Submit Practice Form**.
     - **Expectation:** Submission is blocked; the Email field is highlighted as invalid.
  5. Inspect the Email field for a validation message.
     - **Expectation:** A message indicating an incomplete email address (missing domain) is shown.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Email with Subdomain Accepted

- **Test Case ID:** TC_009
- **Priority:** Low
- **Objective:** Verify that a valid email with a multi-level subdomain is accepted.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `user@mail.qa.example.co.uk`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  3. Click the **Email** field and type `user@mail.qa.example.co.uk`.
     - **Expectation:** The full email string is entered correctly without truncation.
  4. Click **Submit Practice Form**.
     - **Expectation:** No validation error for the email field.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation message is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Empty Email Field on Submit

- **Test Case ID:** TC_010
- **Priority:** High
- **Objective:** Verify that submitting the form with an empty Email field is blocked.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; all form fields are visible.
  2. Fill **Full name** with `John Doe` and **Password** with `Passw0rd`.
     - **Expectation:** Both fields accept the values.
  3. Leave the **Email** field empty.
     - **Expectation:** Email field shows placeholder `qa@example.com`; no value is entered.
  4. Click **Submit Practice Form**.
     - **Expectation:** Submission is blocked; focus returns to the Email field.
  5. Inspect the Email field for a validation message.
     - **Expectation:** A required-field indicator (border highlight, tooltip, or message) is visible.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 3. Password Field

---

### 🧾 Test Case: Valid Password (≥6 Characters) Accepted

- **Test Case ID:** TC_011
- **Priority:** High
- **Objective:** Verify that a password meeting the minimum length requirement allows form submission.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `Secure1` (7 characters)

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Email** with `qa@example.com`.
     - **Expectation:** Both fields accept the values.
  3. Click the **Password** field and type `Secure1`.
     - **Expectation:** 7 masked characters (dots or asterisks) appear in the field.
  4. Click **Submit Practice Form**.
     - **Expectation:** No password length validation error is triggered.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Password Shorter Than 6 Characters Rejected

- **Test Case ID:** TC_012
- **Priority:** High
- **Objective:** Verify that a password with fewer than 6 characters is rejected with a clear validation message.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `abc` (3 characters)

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Email** with `qa@example.com`.
     - **Expectation:** Both fields accept the values.
  3. Click the **Password** field and type `abc`.
     - **Expectation:** 3 masked characters appear in the field.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form submission is blocked; the Password field is highlighted as invalid.
  5. Inspect the Password field for a validation message.
     - **Expectation:** A message such as "Minimum 6 characters" (matching the placeholder hint) or equivalent is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Password Exactly 6 Characters Accepted (Boundary)

- **Test Case ID:** TC_013
- **Priority:** High
- **Objective:** Verify that a password of exactly 6 characters (the boundary minimum) is accepted.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `abcdef` (exactly 6 characters)

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Email** with `qa@example.com`.
     - **Expectation:** Both fields accept the values.
  3. Click the **Password** field and type `abcdef`.
     - **Expectation:** Exactly 6 masked characters appear in the field; no inline error appears while typing.
  4. Click **Submit Practice Form**.
     - **Expectation:** No password length validation error is triggered.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed, confirming the boundary value is accepted.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Password Field Masks Input

- **Test Case ID:** TC_014
- **Priority:** Medium
- **Objective:** Verify that password characters are masked (not displayed in plain text) for security.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `Secret123`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Password field is visible.
  2. Click the **Password** field and type `Secret123`.
     - **Expectation:** Characters are entered but displayed as masked symbols (dots `•` or asterisks `*`); the actual characters `S`, `e`, `c`, etc. are NOT visible.
  3. Verify the HTML `type` attribute of the Password field.
     - **Expectation:** The field has `type="password"` (confirming browser-level masking).
  4. Verify no browser autocomplete or dev tools extension has auto-revealed the password in plaintext.
     - **Expectation:** Password remains masked in the rendered UI.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Empty Password Field on Submit

- **Test Case ID:** TC_015
- **Priority:** High
- **Objective:** Verify that submitting the form with an empty Password field is blocked.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name** with `John Doe` and **Email** with `qa@example.com`.
     - **Expectation:** Both fields accept the values.
  3. Leave the **Password** field empty.
     - **Expectation:** Password field shows placeholder `Minimum 6 characters`; no value entered.
  4. Click **Submit Practice Form**.
     - **Expectation:** Submission is blocked; focus moves to or highlights the Password field.
  5. Inspect the Password field for a validation message.
     - **Expectation:** A required-field or minimum-length validation indicator is visible.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 4. Automation Tool Dropdown

---

### 🧾 Test Case: Default Selection is "Selenium"

- **Test Case ID:** TC_016
- **Priority:** High
- **Objective:** Verify that the Automation Tool dropdown defaults to "Selenium" on fresh page load.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - No prior interaction with the page (fresh load)

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form elements render.
  2. Locate the **Automation tool** dropdown without clicking it.
     - **Expectation:** The dropdown is visible and in a closed state.
  3. Read the currently displayed value of the dropdown.
     - **Expectation:** The displayed value is `Selenium`.
  4. Verify the `selected` attribute in the dropdown's option list.
     - **Expectation:** The `<option value="Selenium">` element has the `selected` attribute.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Select "Playwright" from Dropdown

- **Test Case ID:** TC_017
- **Priority:** High
- **Objective:** Verify that "Playwright" can be selected from the Automation Tool dropdown and the selection persists.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state (Automation tool = Selenium)

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Automation tool dropdown shows `Selenium`.
  2. Click the **Automation tool** dropdown to open it.
     - **Expectation:** Dropdown expands showing all available options.
  3. Click the **Playwright** option.
     - **Expectation:** Dropdown collapses; the selected value updates to `Playwright`.
  4. Verify the displayed value in the closed dropdown.
     - **Expectation:** Dropdown label shows `Playwright`; the `Selenium` option is no longer selected.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Select "Cypress" from Dropdown

- **Test Case ID:** TC_018
- **Priority:** Medium
- **Objective:** Verify that "Cypress" can be selected from the Automation Tool dropdown.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Automation tool dropdown shows `Selenium`.
  2. Click the **Automation tool** dropdown.
     - **Expectation:** Dropdown opens; all options are listed.
  3. Click the **Cypress** option.
     - **Expectation:** Dropdown closes; the selected value updates to `Cypress`.
  4. Verify the displayed value.
     - **Expectation:** Dropdown label shows `Cypress`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Select "Robot Framework" from Dropdown

- **Test Case ID:** TC_019
- **Priority:** Medium
- **Objective:** Verify that "Robot Framework" can be selected from the Automation Tool dropdown.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Automation tool dropdown shows `Selenium`.
  2. Click the **Automation tool** dropdown.
     - **Expectation:** Dropdown opens; all options are listed.
  3. Click the **Robot Framework** option.
     - **Expectation:** Dropdown closes; the selected value updates to `Robot Framework`.
  4. Verify the displayed value.
     - **Expectation:** Dropdown label shows `Robot Framework`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: All Four Options Available in Dropdown

- **Test Case ID:** TC_020
- **Priority:** Medium
- **Objective:** Verify that the Automation Tool dropdown contains exactly four predefined options.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Page is loaded

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form elements are visible.
  2. Click the **Automation tool** dropdown to open it.
     - **Expectation:** Dropdown expands showing its options list.
  3. Count the available options.
     - **Expectation:** Exactly **4** options are present.
  4. Verify each option label:
     - **Expectation:** The four options are, in order: `Selenium`, `Playwright`, `Cypress`, `Robot Framework`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 5. Experience Level Radio Buttons

---

### 🧾 Test Case: Default Selection is "Beginner"

- **Test Case ID:** TC_021
- **Priority:** High
- **Objective:** Verify that the "Beginner" radio button is pre-selected on fresh page load.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - No prior interaction with the page

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Experience level radio group is visible.
  2. Observe the state of each radio button in the **Experience level** group without clicking.
     - **Expectation:** The `Beginner` radio button is in a checked state; `Intermediate` and `Advanced` are unchecked.
  3. Verify the `checked` property of the Beginner radio button programmatically.
     - **Expectation:** `element.checked === true` for Beginner; `false` for others.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Select "Intermediate" Experience Level

- **Test Case ID:** TC_022
- **Priority:** High
- **Objective:** Verify that clicking "Intermediate" selects it and deselects "Beginner".

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Experience level defaults to `Beginner`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; `Beginner` is checked by default.
  2. Click the **Intermediate** radio button.
     - **Expectation:** `Intermediate` radio becomes checked; a visual change (filled circle) is observed.
  3. Verify the state of all radio buttons in the group.
     - **Expectation:** `Intermediate` is checked; `Beginner` and `Advanced` are unchecked.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Select "Advanced" Experience Level

- **Test Case ID:** TC_023
- **Priority:** High
- **Objective:** Verify that clicking "Advanced" selects it and deselects the previously selected option.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Experience level defaults to `Beginner`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; `Beginner` is checked.
  2. Click the **Advanced** radio button.
     - **Expectation:** `Advanced` radio becomes checked.
  3. Verify the state of all radio buttons.
     - **Expectation:** `Advanced` is checked; `Beginner` and `Intermediate` are unchecked.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Only One Radio Button Selected at a Time (Mutual Exclusivity)

- **Test Case ID:** TC_024
- **Priority:** High
- **Objective:** Verify that selecting a new radio button in the Experience Level group always deselects the previously selected one.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Experience level defaults to `Beginner`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** `Beginner` is pre-selected.
  2. Click **Intermediate**.
     - **Expectation:** `Intermediate` is now checked; `Beginner` is unchecked.
  3. Click **Advanced**.
     - **Expectation:** `Advanced` is now checked; `Intermediate` is unchecked; `Beginner` remains unchecked.
  4. Count the number of checked radio buttons in the group.
     - **Expectation:** Exactly **1** radio button is checked at any point during steps 2–3.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 6. Practice Topics Checkboxes

---

### 🧾 Test Case: Default "Forms" Checkbox is Checked

- **Test Case ID:** TC_025
- **Priority:** High
- **Objective:** Verify that "Forms" is pre-checked and all other topics are unchecked on page load.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - No prior interaction

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Practice topics checkbox group is visible.
  2. Observe the state of each checkbox: Forms, Alerts, Frames, Windows.
     - **Expectation:** `Forms` checkbox is checked; `Alerts`, `Frames`, and `Windows` are unchecked.
  3. Verify the `checked` property programmatically.
     - **Expectation:** `Forms.checked === true`; all others `=== false`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Check All Four Topics

- **Test Case ID:** TC_026
- **Priority:** High
- **Objective:** Verify that all four practice topic checkboxes can be checked simultaneously.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Default state: only `Forms` is checked

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; only `Forms` is checked.
  2. Click the **Alerts** checkbox.
     - **Expectation:** `Alerts` becomes checked; `Forms` remains checked; others unchanged.
  3. Click the **Frames** checkbox.
     - **Expectation:** `Frames` becomes checked; `Forms` and `Alerts` remain checked.
  4. Click the **Windows** checkbox.
     - **Expectation:** `Windows` becomes checked; all four checkboxes are now checked simultaneously.
  5. Verify all four checkboxes are checked.
     - **Expectation:** `Forms`, `Alerts`, `Frames`, `Windows` all have `checked === true`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Uncheck All Topics

- **Test Case ID:** TC_027
- **Priority:** Medium
- **Objective:** Verify that all checkboxes can be unchecked and the form handles a zero-selection state gracefully.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Default state: `Forms` is checked

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; `Forms` is checked.
  2. Click the **Forms** checkbox to uncheck it.
     - **Expectation:** `Forms` becomes unchecked; all four checkboxes are now unchecked.
  3. Fill **Full name**, **Email**, and **Password** with valid data.
     - **Expectation:** Fields accept the values.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form either submits successfully (checkboxes are optional) or displays a clear validation message if at least one topic is required.
  5. No JavaScript error or crash occurs.
     - **Expectation:** Browser console shows no uncaught exceptions.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Check Then Uncheck a Topic

- **Test Case ID:** TC_028
- **Priority:** Medium
- **Objective:** Verify that individual checkbox toggle behavior works correctly without affecting other checkboxes.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Default state: only `Forms` is checked

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; only `Forms` is checked.
  2. Click the **Alerts** checkbox to check it.
     - **Expectation:** `Alerts` becomes checked; `Forms` remains checked; `Frames` and `Windows` remain unchecked.
  3. Click the **Alerts** checkbox again to uncheck it.
     - **Expectation:** `Alerts` returns to unchecked state.
  4. Verify the state of all checkboxes.
     - **Expectation:** Only `Forms` is checked — identical to the initial default state.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Submit with Multiple Topics Selected

- **Test Case ID:** TC_029
- **Priority:** Medium
- **Objective:** Verify that submitting the form with multiple practice topics checked works successfully.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Default state: `Forms` is checked

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; `Forms` is checked.
  2. Check **Frames** and **Windows**.
     - **Expectation:** `Forms`, `Frames`, and `Windows` are all checked simultaneously.
  3. Fill **Full name** with `John Doe`, **Email** with `qa@example.com`, **Password** with `Passw0rd`.
     - **Expectation:** All three fields accept the values.
  4. Click **Submit Practice Form**.
     - **Expectation:** No validation error related to checkbox selection is triggered.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 7. Confidence Score Slider

---

### 🧾 Test Case: Default Slider Value is 5

- **Test Case ID:** TC_030
- **Priority:** High
- **Objective:** Verify that the Confidence Score slider defaults to 5 on fresh page load.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - No prior interaction

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Confidence score section is visible.
  2. Read the **Confidence score** status label without interacting with the slider.
     - **Expectation:** The status label displays the value `5`.
  3. Verify the slider element's `value` attribute.
     - **Expectation:** `slider.value === "5"`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Drag Slider to Minimum Value (1)

- **Test Case ID:** TC_031
- **Priority:** High
- **Objective:** Verify that moving the slider to its leftmost position sets the value to the defined minimum (1).

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Slider is at default value of 5

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Confidence score shows `5`.
  2. Move the slider to its leftmost (minimum) position.
     - **Expectation:** The slider handle moves to the far left end of the track.
  3. Read the **Confidence score** status label.
     - **Expectation:** The status label updates to `1` (or the defined minimum boundary value).
  4. Verify the slider element's `value` attribute equals `1`.
     - **Expectation:** `slider.value === "1"`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Drag Slider to Maximum Value (10)

- **Test Case ID:** TC_032
- **Priority:** High
- **Objective:** Verify that moving the slider to its rightmost position sets the value to the defined maximum (10).

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Slider is at default value of 5

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Confidence score shows `5`.
  2. Move the slider to its rightmost (maximum) position.
     - **Expectation:** The slider handle moves to the far right end of the track.
  3. Read the **Confidence score** status label.
     - **Expectation:** The status label updates to `10` (or the defined maximum boundary value).
  4. Verify the slider element's `value` attribute equals `10`.
     - **Expectation:** `slider.value === "10"`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Slider Status Label Updates Dynamically

- **Test Case ID:** TC_033
- **Priority:** Medium
- **Objective:** Verify that the Confidence Score status label updates in real-time as the slider is moved, without requiring a page action.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Slider is at default value of 5

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; status label shows `5`.
  2. Move the slider to value `7` (roughly 60% of the range).
     - **Expectation:** The slider handle moves to the `7` position on the track.
  3. Read the **Confidence score** status label immediately after moving.
     - **Expectation:** The label shows `7` without any page reload or additional button click.
  4. Move the slider back to value `3`.
     - **Expectation:** The label immediately updates to `3`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Submit with Non-Default Slider Value

- **Test Case ID:** TC_034
- **Priority:** Medium
- **Objective:** Verify that the form submits successfully when the Confidence Score slider is set to a non-default value.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Slider is at default value of 5

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Confidence score = 5.
  2. Move the slider to value `9`.
     - **Expectation:** Status label updates to `9`.
  3. Fill **Full name** with `John Doe`, **Email** with `qa@example.com`, **Password** with `Passw0rd`.
     - **Expectation:** All three fields accept the values.
  4. Click **Submit Practice Form**.
     - **Expectation:** No validation error related to the slider is triggered.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed with slider value of `9` included.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 8. Notes Textarea

---

### 🧾 Test Case: Valid Notes Accepted

- **Test Case ID:** TC_035
- **Priority:** High
- **Objective:** Verify that a standard text note is accepted and the form submits successfully.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `Testing the form with Playwright.`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Notes textarea is visible with placeholder `Write test notes`.
  2. Fill **Full name**, **Email**, **Password** with valid data.
     - **Expectation:** All three fields accept the values.
  3. Click the **Notes** textarea and type `Testing the form with Playwright.`
     - **Expectation:** The text appears in the textarea; placeholder disappears.
  4. Click **Submit Practice Form**.
     - **Expectation:** No validation error for the Notes field.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Notes Field Accepts Multi-Line Input

- **Test Case ID:** TC_036
- **Priority:** Medium
- **Objective:** Verify that the Notes textarea correctly handles and preserves multi-line text (newlines).

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Notes textarea is visible.
  2. Click the **Notes** textarea.
     - **Expectation:** Textarea receives focus.
  3. Type `Line 1`, then press `Shift+Enter` or `Enter` to create a new line, then type `Line 2`, press `Enter`, then type `Line 3`.
     - **Expectation:** Each line appears on a separate row within the textarea; the textarea expands or scrolls to accommodate the content.
  4. Verify that line breaks are preserved visually in the textarea.
     - **Expectation:** Three distinct lines are visible: `Line 1`, `Line 2`, `Line 3`.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Submit with Empty Notes

- **Test Case ID:** TC_037
- **Priority:** Medium
- **Objective:** Verify that the Notes field is optional and the form submits successfully when Notes is left empty.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; Notes textarea shows placeholder `Write test notes`.
  2. Fill **Full name** with `John Doe`, **Email** with `qa@example.com`, **Password** with `Passw0rd`.
     - **Expectation:** All three fields accept the values.
  3. Leave the **Notes** textarea empty.
     - **Expectation:** Notes field remains blank with placeholder visible.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form submits without any validation error for the Notes field (it is optional).
  5. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Notes with Special Characters and Unicode

- **Test Case ID:** TC_038
- **Priority:** Low
- **Objective:** Verify that Notes containing HTML special characters, quotes, and Unicode (Japanese) are treated as plain text and do not trigger script execution.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state
  - Test data: `<script>alert('xss')</script> & "quotes" 日本語`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads normally.
  2. Fill **Full name**, **Email**, **Password** with valid data.
     - **Expectation:** All three fields accept the values.
  3. Click the **Notes** textarea and type `<script>alert('xss')</script> & "quotes" 日本語`.
     - **Expectation:** The full string is entered verbatim as visible text in the textarea; no alert dialog appears.
  4. Click **Submit Practice Form**.
     - **Expectation:** Form submits; no browser alert popup (`alert()`) is triggered by the `<script>` tag.
  5. Observe the status indicator and browser console.
     - **Expectation:** Success confirmation is shown; browser console has no script injection errors; Unicode characters `日本語` are preserved without corruption.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 9. Submit Button & Submission Feedback

---

### 🧾 Test Case: Full Valid Form Submission

- **Test Case ID:** TC_039
- **Priority:** High
- **Objective:** Verify that completing all form fields with valid data and clicking Submit produces a successful submission confirmation.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; all form elements are visible in their default state.
  2. Fill **Full name** with `Jane Smith`.
     - **Expectation:** Field shows `Jane Smith`.
  3. Fill **Email** with `jane@example.com`.
     - **Expectation:** Field shows `jane@example.com`.
  4. Fill **Password** with `Passw0rd`.
     - **Expectation:** Field shows 8 masked characters.
  5. Select **Playwright** from the Automation tool dropdown.
     - **Expectation:** Dropdown displays `Playwright`.
  6. Click the **Intermediate** Experience level radio button.
     - **Expectation:** `Intermediate` is selected; `Beginner` is deselected.
  7. Check the **Alerts** checkbox (Forms is already checked by default).
     - **Expectation:** Both `Forms` and `Alerts` are checked.
  8. Move the **Confidence score** slider to `8`.
     - **Expectation:** Status label shows `8`.
  9. Fill **Notes** with `Full form submission test.`
     - **Expectation:** Notes textarea shows the entered text.
  10. Click **Submit Practice Form**.
      - **Expectation:** The button click is registered; no validation errors appear for any field.
  11. Observe the status indicator below the button.
      - **Expectation:** A non-empty success confirmation message is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Submit with Only Required Fields Filled

- **Test Case ID:** TC_040
- **Priority:** High
- **Objective:** Verify that the form submits successfully when only the minimum required fields (Full name, Email, Password) are filled and all optional fields remain at their defaults.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; all defaults are set.
  2. Fill **Full name** with `Min User`.
     - **Expectation:** Field shows `Min User`.
  3. Fill **Email** with `min@example.com`.
     - **Expectation:** Field shows `min@example.com`.
  4. Fill **Password** with `Pass01`.
     - **Expectation:** Field shows 6 masked characters.
  5. Leave Automation tool (`Selenium`), Experience level (`Beginner`), Practice topics (`Forms`), Confidence score (`5`), and Notes (empty) at their defaults.
     - **Expectation:** Default values remain unchanged.
  6. Click **Submit Practice Form**.
     - **Expectation:** No validation errors appear.
  7. Observe the status indicator.
     - **Expectation:** Success confirmation is displayed.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Submit Button is Visible and Clickable

- **Test Case ID:** TC_041
- **Priority:** High
- **Objective:** Verify that the Submit Practice Form button is rendered on the page, is visible in the viewport, and is interactive.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form section is visible.
  2. Scroll down to the **Submit Practice Form** button if not immediately visible.
     - **Expectation:** The button is found within the page DOM and becomes visible in the viewport after scrolling.
  3. Verify the button's enabled state.
     - **Expectation:** Button does not have a `disabled` attribute; it is not grayed out.
  4. Click the **Submit Practice Form** button (with empty fields).
     - **Expectation:** Button responds to the click event (validation messages appear or form processes); button does not cause a page crash.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Status Indicator Updates After Submission

- **Test Case ID:** TC_042
- **Priority:** High
- **Objective:** Verify that the status element below the Submit button transitions from an empty/default state to a visible confirmation state after successful submission.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Form is in default state

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; status element below the submit button is empty or hidden.
  2. Verify the pre-submission state of the status element.
     - **Expectation:** Status element text content is empty or the element is not visible.
  3. Fill **Full name**, **Email**, **Password** with valid data.
     - **Expectation:** All three required fields have valid values.
  4. Click **Submit Practice Form**.
     - **Expectation:** Submit button registers the click.
  5. Observe the status element after submission.
     - **Expectation:** Status element text content is non-empty; a success or confirmation message is displayed (the element transitions to a visible, informative state).

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Rapid Double-Click on Submit Button

- **Test Case ID:** TC_043
- **Priority:** Low
- **Objective:** Verify that rapidly double-clicking the Submit button does not cause duplicate submissions or application errors.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - All fields filled with valid data

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads normally.
  2. Fill all fields with valid data (Full name: `Test User`, Email: `test@example.com`, Password: `Test123`).
     - **Expectation:** All fields show valid values.
  3. Double-click **Submit Practice Form** in rapid succession (two clicks within ~200ms).
     - **Expectation:** Both click events are dispatched.
  4. Observe the status indicator and page behavior.
     - **Expectation:** The form submits once (not twice); the status indicator shows a single confirmation message; no JavaScript errors appear in the console.
  5. Verify no duplicate confirmation messages or error dialogs appear.
     - **Expectation:** Exactly one success indication is visible.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 10. Form-Level & Usability

---

### 🧾 Test Case: Page Loads with Correct Default State

- **Test Case ID:** TC_044
- **Priority:** High
- **Objective:** Verify that all form elements render with the expected default values on a fresh page load.

- **Pre-requisites:**
  - Fresh browser session (no cached form state)
  - No prior interaction with the page

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms` in a fresh browser context.
     - **Expectation:** Page loads; "Forms and Common Elements" heading is visible.
  2. Verify **Full name** field is empty.
     - **Expectation:** Field value is `""` (empty string); placeholder `Enter full name` is visible.
  3. Verify **Email** field is empty.
     - **Expectation:** Field value is `""`; placeholder `qa@example.com` is visible.
  4. Verify **Password** field is empty.
     - **Expectation:** Field value is `""`; placeholder `Minimum 6 characters` is visible.
  5. Verify **Automation tool** dropdown shows `Selenium`.
     - **Expectation:** Dropdown selected option is `Selenium`.
  6. Verify **Experience level** has `Beginner` pre-selected.
     - **Expectation:** `Beginner` radio is checked; `Intermediate` and `Advanced` are unchecked.
  7. Verify **Practice topics** has `Forms` pre-checked.
     - **Expectation:** `Forms` checkbox is checked; `Alerts`, `Frames`, `Windows` are unchecked.
  8. Verify **Confidence score** label shows `5`.
     - **Expectation:** Status label value is `5`; slider is positioned at midpoint.
  9. Verify **Notes** textarea is empty.
     - **Expectation:** Field value is `""`; placeholder `Write test notes` is visible.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Tab Navigation Traverses All Fields in Logical Order

- **Test Case ID:** TC_045
- **Priority:** Medium
- **Objective:** Verify that keyboard Tab navigation moves focus through all form elements in a logical, predictable order.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Mouse is used only to set the initial focus point

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Click the **Full name** field to set initial focus.
     - **Expectation:** Focus is on the Full name input; a visible focus indicator (outline) is present.
  3. Press `Tab` once.
     - **Expectation:** Focus moves to the **Email** field; focus indicator is visible on Email.
  4. Press `Tab` once.
     - **Expectation:** Focus moves to the **Password** field.
  5. Press `Tab` once.
     - **Expectation:** Focus moves to the **Automation tool** dropdown.
  6. Press `Tab` repeatedly through the radio buttons.
     - **Expectation:** Focus traverses the Experience level radio options (Beginner → Intermediate → Advanced).
  7. Press `Tab` repeatedly through the checkboxes.
     - **Expectation:** Focus traverses the Practice topics checkboxes (Forms → Alerts → Frames → Windows).
  8. Press `Tab` once.
     - **Expectation:** Focus moves to the **Confidence score** slider.
  9. Press `Tab` once.
     - **Expectation:** Focus moves to the **Notes** textarea.
  10. Press `Tab` once.
      - **Expectation:** Focus moves to the **Submit Practice Form** button.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: All Fields Have Visible Labels

- **Test Case ID:** TC_046
- **Priority:** Medium
- **Objective:** Verify that every form control is associated with a visible, descriptive label rendered on the page.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - Page is fully loaded

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form section is visible.
  2. Locate the label for the **Full name** field.
     - **Expectation:** A visible text label reading `Full name` is rendered adjacent to the input.
  3. Locate the label for the **Email** field.
     - **Expectation:** A visible text label reading `Email` is rendered.
  4. Locate the label for the **Password** field.
     - **Expectation:** A visible text label reading `Password` is rendered.
  5. Locate the label for the **Automation tool** dropdown.
     - **Expectation:** A visible text label reading `Automation tool` is rendered.
  6. Locate the group label for **Experience level** radio buttons.
     - **Expectation:** A visible group label reading `Experience level` is rendered above or beside the radio options.
  7. Locate the group label for **Practice topics** checkboxes.
     - **Expectation:** A visible group label reading `Practice topics` is rendered.
  8. Locate the label for the **Confidence score** slider.
     - **Expectation:** A visible label reading `Confidence score:` followed by the current value is rendered.
  9. Locate the label for the **Notes** textarea.
     - **Expectation:** A visible text label reading `Notes` is rendered.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Placeholder Text Present in Text Inputs

- **Test Case ID:** TC_047
- **Priority:** Low
- **Objective:** Verify that all text input fields display the correct placeholder text when empty.

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - All fields are empty (fresh page load or cleared)

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; all text fields are empty.
  2. Observe the **Full name** field placeholder.
     - **Expectation:** Placeholder text reads exactly `Enter full name`.
  3. Observe the **Email** field placeholder.
     - **Expectation:** Placeholder text reads exactly `qa@example.com`.
  4. Observe the **Password** field placeholder.
     - **Expectation:** Placeholder text reads exactly `Minimum 6 characters`.
  5. Observe the **Notes** textarea placeholder.
     - **Expectation:** Placeholder text reads exactly `Write test notes`.
  6. Click the **Full name** field and start typing.
     - **Expectation:** The placeholder text disappears as soon as a character is entered.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

### 🧾 Test Case: Form is Keyboard-Accessible via Enter Key

- **Test Case ID:** TC_048
- **Priority:** Medium
- **Objective:** Verify that the form can be fully submitted using only the keyboard (Tab to navigate, Enter to submit).

- **Pre-requisites:**
  - Browser navigated to `https://way2automation.com/practicesite/#forms`
  - All required fields filled with valid data before starting keyboard-only interaction

- **Test Steps & Expectations:**
  1. Navigate to `https://way2automation.com/practicesite/#forms`.
     - **Expectation:** Page loads; form is visible.
  2. Fill **Full name**, **Email**, and **Password** using mouse/keyboard type.
     - **Expectation:** All three required fields contain valid values.
  3. Click the **Full name** field then navigate entirely via `Tab` key until focus reaches the **Submit Practice Form** button.
     - **Expectation:** Focus moves through each field in order and arrives at the Submit button; a visible focus ring is present on the button.
  4. Press `Enter` while the Submit button has focus.
     - **Expectation:** The button's click action is triggered via keyboard; the form submission is initiated.
  5. Observe the status indicator.
     - **Expectation:** Success confirmation message is displayed — identical outcome to a mouse click on the submit button.

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

*End of Test Cases Document*
