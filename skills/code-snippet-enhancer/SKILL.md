---
name: code-snippet-enhancer
description: 'Enhance code snippets and terminal commands in technical tutorials. Adds file path headers, 1-click clipboard copy buttons, line-number controls, diff views (+/-), focus line highlights, and syntax contrast optimization.'
---

# Code Snippet & Terminal Output Enhancer

Specialized skill for elevating the utility, readability, and interactivity of code examples and CLI sessions within web tutorials.

---

## 1. High-Friction Tutorial Code Design

1. **File Path & Context Header**:
   - Every substantive code snippet must feature a top header indicating the relative file path (e.g. `src/server.ts`) or command context (e.g. `bash / terminal`).
2. **One-Click Copy Utility**:
   - Integrated clipboard button providing instant tactile feedback (`Copied!` tooltip + checkmark icon).
   - In Markdown: provide clean copyable blocks without line numbers embedded in raw text.
   - In HTML: use `navigator.clipboard.writeText` bound to sanitized code content.
3. **Line Highlighting & Diff Representation**:
   - Highlight newly modified or crucial lines with subtle green or primary tints to guide the reader's eye.
   - For update steps, use unified diff format (`+` / `-`) with distinct colored badges.
4. **Terminal Output Pairing**:
   - Separate input commands from execution outputs.
   - Display realistic terminal outputs with colored status badges (e.g., green checkmarks, duration, status codes) to reassure the reader.

---

## 2. HTML Implementation Pattern

```html
<div class="code-container rounded-xl overflow-hidden border border-slate-700 bg-slate-900 shadow-md my-6">
  <div class="code-header flex items-center justify-between px-4 py-2 bg-slate-800 text-xs text-slate-300">
    <span class="font-mono flex items-center gap-1.5">📁 path/to/file.ext</span>
    <button class="copy-btn hover:text-white" data-code="...">复制</button>
  </div>
  <pre class="p-4 text-sm font-mono overflow-x-auto"><code>...</code></pre>
</div>
```

---

## 3. Review Checklist

- [ ] Every non-trivial code block states its file path or target context.
- [ ] Code is easily copyable without trailing comment noise or prompt characters (`$ `) contaminating the copied string.
- [ ] Horizontal scrollbar is isolated within the pre block and does not cause page-level horizontal overflow.
- [ ] Syntax tokens have sufficient contrast against code container backgrounds ($\ge 4.5:1$).

