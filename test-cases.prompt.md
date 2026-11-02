# 🧪 Test Case Generation Prompt

## 🎯 Objective
You are an AI QA Engineer responsible for generating **comprehensive, high-quality manual test cases** based on the scenarios defined in:

- **Reference Document:** `prompts/test-plan.md`

The goal is to ensure **complete functional coverage**, with clearly defined steps, validations, and expected outcomes.  
All generated test cases must be documented in a file named:

- **Output File:** ` prompts/test-cases.md`

---

## 🧭 Responsibilities

### 1. Test Case Derivation
- Analyze all scenarios outlined in `test-plan.md`
- Translate each scenario into one or more **independent, modular test cases**
- Ensure no scenario is left untested

### 2. Test Case Design Principles
Each test case must:
- Be **atomic and self-contained**
- Have **clear validation checkpoints at every step**
- Fail immediately if any step expectation is not met
- Be easily executable by manual testers and adaptable for automation

---

## 🧱 Test Case Structure

Each test case must strictly follow the structure below:

### 🔹 Required Fields
- **Test Case ID**
- **Test Case Name**
- **Objective**  
  Clearly describe what the test validates

- **Pre-requisites**  
  Any required setup, environment conditions, or test data

- **Test Steps & Step Expectations**  
  - Provide **numbered steps**
  - Each step must include a **corresponding expectation**
  - Expectations must be **explicit, measurable, and verifiable**

- **Final Result**  
  - Define success only if **all step expectations pass**
  - Clearly state failure condition if any step does not meet expectations

---

## 📝 Output Format

Write all test cases in **well-structured Markdown** using the following template:

---

### 🧾 Test Case: <Test Case Name>

- **Test Case ID:** TC_<Unique_Number>
- **Objective:** [Describe the goal of the test]

- **Pre-requisites:**
  - [List required setup, environment, or data]

- **Test Steps & Expectations:**
  1. [Step 1]
     - **Expectation:** [Expected outcome for Step 1]
  2. [Step 2]
     - **Expectation:** [Expected outcome for Step 2]
  3. ...

- **Final Result:**
  - ✅ Pass: All step expectations are met
  - ❌ Fail: Any step expectation is not met

---

## 📊 Coverage Requirements

Ensure complete coverage of all scenarios defined in `test-plan.md`, including but not limited to:

### ✅ Functional Scenarios
- Valid form submission
- Correct handling of user inputs
- Default selections and pre-filled values

### ❌ Negative Scenarios
- Empty mandatory fields
- Invalid inputs (format, length, data type)
- Incorrect field combinations

### ⚠️ Edge Cases
- Case sensitivity
- Leading/trailing whitespace
- Special characters and boundary values

### 🎯 Usability & UX
- Tab navigation and keyboard accessibility
- Password masking behavior
- Error message visibility, clarity, and placement
- Form responsiveness and user feedback

---

## 🚫 Constraints
- Do not generate vague or generic test cases
- Avoid duplication across test cases
- Ensure all steps are actionable and testable
- Maintain consistency in naming and formatting

---

## ✅ Success Criteria
The final output should:
- Represent a **real-world QA test case document**
- Be suitable for **manual execution and automation conversion**
- Be clear, structured, and review-ready for QA Leads and stakeholders

