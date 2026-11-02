id: pw-mcp-executor-001
mode: agent
description: >
  Execute all test cases for the Playwright project using the Playwright MCP server in headed mode,
  and generate a comprehensive, well-structured HTML test execution report.

tools:
  - playwright

model: GPT-4.1

---

## 🎯 Objective
Execute all test scenarios defined in `prompts/test-cases.md` using the Playwright MCP server, and produce a **detailed HTML test report** capturing execution results, validations, and evidence.

---

## ⚙️ Pre-requisites

- Ensure **Playwright MCP server** is installed and properly configured.
- Verify the MCP server is **running** before execution. Start it if not active.
- If the report file exists:
  - Delete: `automation-testing/test-results.html`
  - Recreate a fresh report with the latest execution results.
- Clean up previous artifacts:
  - Clear all files from `automation-testing/screenshots/`

---

## 🧭 Execution Instructions

### 1. Application Launch
- Launch **Google Chrome (headed mode)** via Playwright MCP
- Navigate to: https://way2automation.com/practicesite/#forms


---

### 2. Test Execution

- Read all scenarios from: `prompts/test-cases.md`
- Execute **all test cases sequentially** (no skipping allowed)
- Do **not pause execution** for clarifications or inputs

#### For Each Test Case:
- Execute steps exactly as defined
- Validate each step against expected outcomes

#### During Execution:
- Capture and log:
- **Actual Results**
- **Expected Results**
- **Pass/Fail Status (Assertions)**

- 📸 Screenshot Policy:
- Capture screenshots **only for failed assertions**
- Save in: `automation-testing/screenshots/`
- Maintain meaningful file names
- Link screenshots in the HTML report

- ⏱ Record:
- Execution time per test case

---

### 3. Report Generation

Append all results to: automation-testing/test-results.html



#### Each Test Case Entry Must Include:
- Test Case Name / Scenario Title
- Description / Objective
- Steps Executed
- Expected vs Actual Results
- Assertion Status (Pass/Fail)
- Execution Time
- Screenshot Links (if applicable)

---

### 4. Final Report Summary

After executing all test cases, update the report with:

#### 📊 Execution Summary Matrix
- Total Test Cases Executed
- Total Passed
- Total Failed
- Execution Date & Time

#### 🚨 Defect Summary
- Highlight all **critical/high-priority failures**
- Provide concise descriptions

#### ✅ Status Banner
- If all tests pass:
  - Display a **Success Message**
- If any test fails:
  - Display a **Failure Summary with details**

#### 📄 Report Quality
- Ensure the report is:
  - Cleanly formatted
  - Easy to navigate
  - Professionally styled (tables, sections, headings)

---

## 🚫 Constraints

- Do NOT generate or execute any automation scripts
- All interactions must occur via **Playwright MCP (interactive execution)**
- Do NOT skip any test scenario
- Do NOT request user input during execution

---

## 🧹 Post Execution

- Close all browser instances and tabs
- Gracefully stop the Playwright MCP server after:
  - All test cases are executed
  - Final report is generated

---

## ✅ Success Criteria

- 100% test case execution coverage
- Accurate and complete HTML report
- Proper failure tracking with screenshots
- Clean environment and graceful shutdown

---

