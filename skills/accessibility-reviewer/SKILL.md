---
name: accessibility-reviewer
description: 'Audit and enforce web accessibility (a11y) across technical tutorials and documentation. Validates WCAG 2.1/2.2 AA/AAA compliance, color contrast, keyboard navigation, screen reader semantics, and ARIA attributes in standalone HTML and Markdown.'
---

# Web Accessibility (a11y) Reviewer & Auditor

Specialized auditing skill to guarantee that technical tutorials and documentation are welcoming, legible, and completely operable by learners of all abilities.

---

## 1. Core Compliance Standards (WCAG 2.1/2.2)

1. **Color Contrast**:
   - Normal text ($< 18\text{pt}$ / $24\text{px}$): Minimum $4.5:1$ contrast ratio against background.
   - Large text ($\ge 18\text{pt}$ or bold $\ge 14\text{pt}$): Minimum $3:1$ contrast ratio.
   - UI components & graphical objects (borders, icons, buttons): Minimum $3:1$.
   - Aim for AAA ($7:1$) for long-form tutorial body paragraphs.
2. **Dual-Encoding (No Color-Only Information)**:
   - Callouts must combine distinct background tints with clear icons and text headers (e.g., "⚠️ Warning", "ℹ️ Note").
   - Status indicators (e.g., test pass/fail) must use text labels or checkmarks alongside green/red hues.
3. **Keyboard Operability & Focus Management**:
   - All interactive controls (theme switch, copy button, sidebar drawer, TOC links) must be reachable via `Tab` / `Shift+Tab`.
   - Distinct, high-contrast focus rings (`outline: 2px solid #3B82F6; outline-offset: 2px;`).
4. **Semantic HTML & Screen Reader Support**:
   - Proper heading hierarchy ($H_1 \rightarrow H_2 \rightarrow H_3$) without skipping levels.
   - Meaningful `aria-label` attributes on icon-only buttons (e.g. `aria-label="切换深色模式"`).
   - Alt text on all diagrams and images explaining key structural insights.

---

## 2. Review Checklist

- [ ] All text and UI elements meet or exceed WCAG 2.1 AA contrast requirements in both light and dark themes.
- [ ] No reliance on color alone to convey crucial warnings or success states.
- [ ] Keyboard navigation flows logically from top to bottom; no keyboard traps.
- [ ] Interactive elements possess accessible labels and visible focus indicators.

