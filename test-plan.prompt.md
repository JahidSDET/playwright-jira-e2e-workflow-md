# 🧪 Test Plan Generation Prompt

## 🎯 Objective
You are an AI Test Architect responsible for creating a **comprehensive, industry-standard Test Plan** for the **General Forms functionality** of the following web application:

- **Application URL:** https://way2automation.com/practicesite/#forms

The goal is to ensure **functional correctness, input validation, usability, and robustness** of the form components.

---

## 🧭 Scope of Testing
Analyze and validate all UI elements present on the Forms page, including but not limited to:

- Text Input Fields
- Email Field
- Password Field
- Dropdowns
- Radio Buttons
- Checkboxes
- Slider Control
- Notes / Text Area
- Submit Button
- Validation Messages / Status Indicators

---

## 🧩 Responsibilities
You are expected to:

### 1. Functional Analysis
- Examine each form element and its behavior.
- Understand input constraints, default values, and dependencies.

### 2. Test Case Design
Create well-structured test cases covering:

#### ✅ Positive Scenarios
- Valid form submission with all correct inputs
- Proper handling of valid data formats
- Default selections (if applicable)
- Successful UI interactions

#### ❌ Negative Scenarios
- Invalid email formats
- Weak or incorrect password inputs
- Empty mandatory fields
- Invalid or conflicting input combinations
- Boundary violations

#### ⚠️ Edge Cases
- Minimum and maximum input lengths
- Special characters and encoding
- Rapid input changes or multiple submissions
- Browser autofill behavior

#### 🎯 Usability & UX Checks
- Field accessibility and tab navigation
- Error message clarity and placement
- Responsiveness and user feedback
- Form reset or correction flows

---

## 🧱 Test Case Structure
Each test case must include the following:

- **Test Case ID**
- **Test Case Name**
- **Preconditions** (if any)
- **Test Steps** (step-by-step execution)
- **Test Data**
- **Expected Result**
- **Priority** (High / Medium / Low)

---

## 📊 Output Requirements
- Format the entire Test Plan in **clean, well-structured Markdown**
- Use clear section headings and bullet points
- Group test cases logically by component (e.g., Input Fields, Validation, Submission)
- Ensure readability and professional documentation standards

---

## 🚫 Constraints
- Do not make assumptions beyond visible functionality
- Avoid vague or generic test cases
- Ensure all scenarios are actionable and testable

---

## ✅ Success Criteria
The output should resemble a **real-world QA Test Plan document** used in enterprise environments, suitable for:

- Manual Testers
- Automation Engineers
- QA Leads
- Stakeholder Review


once done save this file with the name `test-plan.md` in the prompts directory.
