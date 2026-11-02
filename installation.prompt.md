# ⚙️ Installation Guide: Playwright (TypeScript) + MCP Server

## 🎯 Objective
Set up a complete environment for:
- **Playwright with TypeScript**
- **Chromium-only browser support**
- **Playwright MCP Server**

This guide ensures a clean, minimal, and production-ready setup.

---

## ✅ Prerequisites

- [Node.js](https://nodejs.org/) v18 or later
- npm v9 or later (bundled with Node.js)
- VS Code (recommended) with the [Playwright Test extension](https://marketplace.visualstudio.com/items?itemName=ms-playwright.playwright)

Verify your environment:

```bash
node --version
npm --version
```

---

## 📁 Step 1: Create the Project Directory

```bash
mkdir playwright-tests
cd playwright-tests
```

---

## 📦 Step 2: Initialize a Node.js Project

```bash
npm init -y
```

---

## 🎭 Step 3: Install Playwright with TypeScript

```bash
npm init playwright@latest
```

When prompted by the wizard:

| Prompt | Recommended Answer |
|---|---|
| Language | **TypeScript** |
| Test directory | `tests` (default) |
| GitHub Actions workflow | `false` (unless needed) |
| Install Playwright browsers | **Yes** |

This installs:
- `@playwright/test` — the test runner
- TypeScript support via `tsconfig.json`
- Browser binaries (Chromium, Firefox, WebKit by default)

---

## 🌐 Step 4: Restrict to Chromium Only

Open `playwright.config.ts` and update the `projects` array to keep only Chromium:

```typescript
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './tests',
  fullyParallel: true,
  retries: 0,
  reporter: 'html',
  use: {
    headless: true,
    screenshot: 'only-on-failure',
    video: 'retain-on-failure',
  },
  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] },
    },
  ],
});
```

Remove or comment out the `firefox` and `webkit` project entries if they exist.

---

## 🖥️ Step 5: Install Playwright MCP Server

The [Playwright MCP Server](https://github.com/microsoft/playwright-mcp) exposes browser automation capabilities as MCP (Model Context Protocol) tools, allowing AI agents and copilots to interact with a browser.

```bash
npm install @playwright/mcp@latest
```

---

## ⚙️ Step 6: Configure MCP Server in VS Code

Add the following to your VS Code `settings.json` (open via `Ctrl+Shift+P` → **Preferences: Open User Settings (JSON)**):

```json
{
  "mcp": {
    "servers": {
      "playwright": {
        "command": "npx",
        "args": ["@playwright/mcp@latest"]
      }
    }
  }
}
```

> **Tip:** To enable only Chromium in the MCP server, pass the `--browser chromium` flag:
> ```json
> "args": ["@playwright/mcp@latest", "--browser", "chromium"]
> ```

---

## 🔍 Step 7: Verify Playwright Installation

Run the bundled example test to confirm everything is working:

```bash
npx playwright test
```

View the HTML report after the run:

```bash
npx playwright show-report
```

Expected output: all example tests pass in the **chromium** project.

---

## 📂 Final Project Structure

```
playwright-tests/
├── tests/
│   └── example.spec.ts
├── playwright.config.ts
├── tsconfig.json
├── package.json
└── package-lock.json
```

---

## 🧩 Useful Scripts (add to `package.json`)

```json
"scripts": {
  "test": "playwright test",
  "test:headed": "playwright test --headed",
  "test:debug": "playwright test --debug",
  "report": "playwright show-report"
}
```

---

## 🔗 References

- [Playwright Docs](https://playwright.dev/docs/intro)
- [Playwright TypeScript Guide](https://playwright.dev/docs/test-typescript)
- [Playwright MCP GitHub](https://github.com/microsoft/playwright-mcp)
- [MCP Protocol](https://modelcontextprotocol.io/)
