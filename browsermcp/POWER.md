---
name: "browsermcp"
displayName: "Browser Automation"
description: "Control and automate your browser directly from Kiro. Navigate pages, click elements, fill forms, take screenshots, read console logs, and inspect page structure through the BrowserMCP server."
keywords: ["browser", "browsermcp", "browser-automation", "web-automation", "screenshot", "click", "navigate", "form-fill", "web-testing", "browser-control", "page-snapshot", "console-logs", "web-scraping", "ui-testing"]
author: "custom"
---

# Browser Automation Power

This power provides direct browser control through the BrowserMCP server. It connects to your real browser session via a Chrome extension, enabling navigation, interaction, screenshots, and inspection without headless browsers or bot detection issues.

## Prerequisites

1. **Node.js** (v18 or higher)
   - Check: `node --version`

2. **BrowserMCP Chrome Extension**
   - Install from the Chrome Web Store
   - This extension bridges communication between the MCP server and your browser

3. **Chrome/Chromium browser** must be running with the extension active

## Quick Start

```
"Navigate to https://example.com"
"Take a screenshot of the current page"
"Click the login button"
"Type my email into the input field"
"Show me the console logs"
```

## Available Tools

### Navigation
- **navigate** — Navigate the browser to a specified URL
- **goBack** — Navigate back in browser history
- **goForward** — Navigate forward in browser history

### Page Inspection
- **snapshot** — Capture an aria-level snapshot of the current page structure and metadata
- **screenshot** — Take a PNG screenshot of the current browser view
- **getConsoleLogs** — Retrieve the browser's console logs

### Interaction
- **click** — Click an element on the page by selector or element ID
- **type** — Type text into an input or element
- **hover** — Hover over an element
- **drag** — Drag an element and drop it onto another
- **selectOption** — Select an option in a dropdown/select element
- **pressKey** — Simulate a keyboard key press

### Utility
- **wait** — Pause automation for a given number of seconds

## Workflow: Web Testing

### Step 1: Navigate and Snapshot
Use `navigate` to open the target URL, then `snapshot` to get the page structure. The snapshot provides element identifiers you can use for subsequent interactions.

### Step 2: Interact with Elements
Use the element identifiers from the snapshot to `click` buttons, `type` into inputs, or `selectOption` in dropdowns.

### Step 3: Verify Results
Use `screenshot` to visually verify the page state, `snapshot` to check DOM changes, or `getConsoleLogs` to inspect for errors.

## Workflow: Form Automation

```
1. navigate to the target page
2. snapshot to identify form fields
3. type into each input field
4. selectOption for dropdowns
5. click the submit button
6. snapshot or screenshot to verify submission
```

## Workflow: Debugging

```
1. navigate to the page with issues
2. getConsoleLogs to check for JavaScript errors
3. snapshot to inspect the page structure
4. screenshot for visual reference
```

## Tips

- Always use `snapshot` first to discover element identifiers before interacting
- Use `wait` between actions if the page needs time to load or transition
- `screenshot` returns a base64 PNG image for visual verification
- `getConsoleLogs` is useful for catching JavaScript errors during testing
- Element selectors from `snapshot` are more reliable than CSS selectors for interaction
