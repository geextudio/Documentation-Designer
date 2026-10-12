---
name: tutorial-reading-experience
description: 'Optimize web tutorial reading flow, typography, vertical rhythm, cognitive pacing, and scannability. Use when improving documentation readability, configuring font sizes and line heights, setting optimal reading line length (measure), implementing sticky table of contents (TOC), reading progress indicators, step-by-step cognitive pacing, and interactive reading aids like copy buttons and collapsible deep-dives.'
---

# Tutorial Reading Experience & Readability Optimizer

A specialized skill for engineering superior readability, scannability, and cognitive comprehension in long-form technical tutorials, developer guides, and structured documentation.

---

## 1. Core Principles

1. **Optimal Measure (Line Length)**: Tutorial body text must never span full-screen widths. Maintain an optimal reading length of 60–75 characters (or 40–60 CJK characters) per line (`max-width: 65ch` to `72ch`).
2. **Harmonic Typography Scale**: Clear optical hierarchy between headings and body text so learners can orient themselves instantly during F-pattern scanning.
3. **Cognitive Chunking**: Break dense explanations into bite-sized steps (prerequisite $\rightarrow$ action $\rightarrow$ explanation $\rightarrow$ expected outcome). Never exceed 3–4 sentences per paragraph.
4. **Context Preservation**: Readers must never lose their place. Provide reading progress bars, sticky active Table of Contents (TOC), and clear step counters.
5. **Frictionless Reading Aids**: Interactive code copy buttons, collapsible deep-dives (collapsible `<details>`/accordions for advanced nuances), and highlighted keywords.

---

## 2. Typography & Vertical Rhythm Standards

### 2.1 Font Family & Pairing
- **Prose / Body**: System font stack with excellent x-height and optical legibility:
  `font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif;`
- **Code & Terminal**: High-legibility monospaced font with distinct glyphs for `0`/`O` and `1`/`l`/`I`:
  `font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;`
  `font-feature-settings: "liga" 0;` (optional: disable ambiguous ligatures in tutorials).

### 2.2 Scale, Leading, and Tracking

| Element | Font Size | Line Height (`line-height`) | Letter Spacing (`letter-spacing`) | Margin Bottom |
| :--- | :--- | :--- | :--- | :--- |
| **Tutorial Title (H1)** | `2.25rem` (36px) | `1.2` | `-0.025em` | `1.5rem` |
| **Major Step (H2)** | `1.5rem` (24px) | `1.3` | `-0.02em` | `1rem` |
| **Sub-section (H3)** | `1.25rem` (20px) | `1.4` | `-0.015em` | `0.75rem` |
| **Lead Paragraph** | `1.125rem` (18px)| `1.65` | `normal` | `1.25rem` |
| **Body Prose** | `1rem` (16px) | `1.75` (28px) | `normal` | `1.25rem` |
| **Code Block Text** | `0.875rem` (14px)| `1.6` | `normal` | `1.5rem` |
| **Caption / Metadata** | `0.8125rem` (13px)| `1.5` | `0.01em` | `0.5rem` |

---

## 3. Structural Flow & Tutorial Scannability

### 3.1 4-Part Step Anatomy
Every actionable step in a tutorial should follow a standardized structure:
1. **Actionable Header**: Start with an imperative verb (e.g., `Step 2: Configure the Database Connection`).
2. **Context / Prerequisite**: Single sentence stating what we are about to do and why.
3. **Execution Block**: Clean code snippet or command with file path tag (e.g., `src/config/db.ts`).
4. **Verification / Expected Output**: Clear terminal output or screenshot demonstrating success so the learner knows they succeeded before moving forward.

### 3.2 Reading Navigation & Orientation Components
- **Reading Progress Bar**: Fixed 3px bar at the top of the viewport indicating current scroll depth.
- **Estimated Reading Time**: Displayed under the title alongside difficulty badges (e.g., `⏱️ 8 min read · Beginner`).
- **Sticky Table of Contents (TOC)**: Right-hand sidebar tracking current viewport position (`IntersectionObserver`), highlighting active anchor links.
- **Breadcrumbs & Series Navigation**: Top breadcrumb path and bottom Previous / Next Step pagination cards.

---

## 4. Reading Aids & Interactive Patterns

### 4.1 Frictionless Code Copying
Code snippets must include a dedicated header with:
- Target file path or language badge (`typescript`, `bash`).
- 1-click copy button with instant visual feedback (`Copied!` tooltip or checkmark icon).

### 4.2 Progressive Disclosure (Collapsible Details)
Keep the primary tutorial path clean and streamlined. Secondary edge-cases and deep technical explanations should be packaged into styled `<details>` elements:

```html
<details class="tutorial-deepdive">
  <summary class="font-medium cursor-pointer text-blue-600 hover:text-blue-700">
    🔍 Why does this configuration work? (Deep Dive)
  </summary>
  <div class="mt-2 text-sm text-slate-600 dark:text-slate-300">
    <p>Explanation of internal mechanics, edge cases, and alternatives...</p>
  </div>
</details>
```

---

## 5. Implementation CSS Snippet

```css
/* Optimize reading container measure */
.tutorial-content {
  max-width: 68ch;
  margin-left: auto;
  margin-right: auto;
  font-size: 1rem;
  line-height: 1.75;
  color: var(--tutorial-text-main);
}

/* Vertical rhythm between prose and blocks */
.tutorial-content p {
  margin-bottom: 1.25rem;
}

.tutorial-content h2 {
  margin-top: 2.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
  scroll-margin-top: 5rem; /* Prevents sticky header overlap on anchor jump */
}

.tutorial-content h3 {
  margin-top: 2rem;
  margin-bottom: 0.75rem;
  font-weight: 600;
  scroll-margin-top: 5rem;
}

/* Callout & Code Spacing */
.tutorial-content pre,
.tutorial-content .callout-box {
  margin-top: 1.5rem;
  margin-bottom: 1.5rem;
}
```

---

## 6. Review & Audit Checklist

- [ ] **Line length bounds**: Body text is constrained to `60–75ch` instead of stretching across widescreen displays.
- [ ] **Leading & line height**: Body copy has at least `1.7` to `1.8` line-height for effortless reading.
- [ ] **Anchor scroll offset**: Headings specify `scroll-margin-top` so fixed navbar does not obscure headers when jumping via TOC.
- [ ] **Scannable chunking**: Paragraphs are short ($\le 4$ sentences); steps feature bolded takeaways and imperative headings.
- [ ] **Reading aids active**: Sticky TOC with scrollspy, reading progress indicator, and 1-click code copying with success state are verified.
