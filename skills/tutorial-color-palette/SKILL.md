---
name: tutorial-color-palette
description: 'Optimize color palettes, semantic tokens, dark/light themes, syntax highlighting, and visual contrast for web tutorial experiences. Use when designing tutorial themes, fixing WCAG color contrast, configuring dark mode palettes, harmonizing code block syntax themes with documentation UI, or establishing functional callout color systems.'
---

# Tutorial Color Palette & Visual Theme Optimizer

A specialized skill for engineering cohesive, accessible, and cognitive-friendly color schemes tailored specifically for online web tutorials, interactive guides, and developer documentation.

---

## 1. Core Principles

1. **Content-First Hierarchy**: Colors must guide the eye through structured instructional steps without causing visual fatigue during long learning sessions.
2. **Accessible by Default**: Strictly adhere to WCAG 2.1/2.2 AA standards (minimum 4.5:1 contrast for normal text, 3:1 for large text and UI components; AAA 7:1 preferred for tutorial body prose).
3. **Semantic Coherence**: Functional roles (info, tips, warnings, errors, step success) must have dedicated, universally understood semantic hues paired with non-color cues (icons, badges).
4. **Seamless Dark & Light Adaptation**: Light and dark themes must preserve identical visual hierarchy and contrast levels rather than simple naive color inversions.
5. **Syntax-UI Harmony**: Code blocks and terminal outputs must harmonize with page canvas backgrounds while preserving syntax token readability.

---

## 2. Palette Architecture & Semantic Tokens

### 2.1 Primary & Neutral Scales
- **Canvas Base**:
  - Light mode: Warm off-white (`#FAFAFC` or `#F8FAFC`) to minimize glare compared to pure `#FFFFFF`.
  - Dark mode: Deep slate/charcoal (`#0F172A` or `#0B0F19`) to avoid pure `#000000` OLED haloing on text.
- **Surface Elevation**:
  - Layer 0 (Page Canvas) $\rightarrow$ Layer 1 (Card/Container) $\rightarrow$ Layer 2 (Modal/Flyout/Dropdown).
  - Subtle borders (`rgba(0, 0, 0, 0.08)` in light, `rgba(255, 255, 255, 0.1)` in dark) define boundaries cleanly without aggressive box-shadows.
- **Typography Scale**:
  - `text-primary`: 14:1+ contrast against background for effortless sustained reading.
  - `text-secondary`: For metadata, timestamps, author notes (minimum 5:1 contrast).
  - `text-muted`: Strictly for non-critical placeholders and disabled states.

### 2.2 Functional Callout & Notice Tokens
Tutorials heavily rely on callouts to emphasize prerequisites, best practices, and danger zones:

| Callout Type | Semantic Intent | Light Background | Light Border / Accent | Dark Background | Dark Border / Accent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Note / Info** | Context, extra facts | `#EFF6FF` (Blue 50) | `#3B82F6` (Blue 500) | `#1E293B` (Slate 800) | `#60A5FA` (Blue 400) |
| **Tip / Success** | Best practice, solution | `#F0FDF4` (Green 50) | `#22C55E` (Green 500) | `#064E3B` / 20% tint | `#4ADE80` (Green 400) |
| **Warning** | Caution, deprecation | `#FFFBEB` (Amber 50) | `#F59E0B` (Amber 500) | `#451A03` / 20% tint | `#FBBF24` (Amber 400) |
| **Danger / Error** | Breaking changes, pitfalls | `#FEF2F2` (Red 50) | `#EF4444` (Red 500) | `#450A0A` / 20% tint | `#F87171` (Red 400) |
| **Step Badge** | Progressive milestones | `#F3E8FF` (Purple 50) | `#8B5CF6` (Purple 500) | `#2E1065` / 30% tint | `#A78BFA` (Purple 400) |

---

## 3. Code Block & Syntax Highlighting Harmony

Code snippets are central to technical tutorials. The syntax theme must feel integrated into the surrounding documentation:

1. **Container Background**:
   - In light themes: Use an intentional muted cool-gray container (`#1E293B` for dark code block, or `#F1F5F9` for light-on-light) with crisp contrast against page canvas.
   - In dark themes: Code block container should be slightly darker or elevated with a 1px border (`#334155`).
2. **Line Highlights & Diff Colors**:
   - Added lines: Green tint (`rgba(34, 197, 94, 0.15)`) with a 3px solid green left indicator.
   - Removed lines: Red tint (`rgba(239, 68, 68, 0.15)`) with a 3px solid red left indicator.
   - Focus lines: Soft amber/primary tint (`rgba(59, 130, 246, 0.12)`) to guide reader attention during walkthroughs.
3. **Syntax Contrast**:
   - Comments: Minimum 4.5:1 contrast against code block background (never unreadable dark gray).
   - Keywords, functions, and string literals must pass contrast validation for color-blind readers.

---

## 4. Implementation Specification (CSS Variables & Tailwind)

```css
:root {
  /* Canvas & Neutral */
  --tutorial-bg: #F8FAFC;
  --tutorial-surface: #FFFFFF;
  --tutorial-border: #E2E8F0;
  --tutorial-text-main: #0F172A;
  --tutorial-text-muted: #64748B;

  /* Brand / Action */
  --tutorial-accent: #2563EB;
  --tutorial-accent-hover: #1D4ED8;
  --tutorial-accent-subtle: #DBEAFE;

  /* Callouts */
  --callout-info-bg: #EFF6FF;
  --callout-info-border: #3B82F6;
  --callout-info-text: #1E40AF;

  --callout-tip-bg: #F0FDF4;
  --callout-tip-border: #22C55E;
  --callout-tip-text: #166534;

  --callout-warn-bg: #FFFBEB;
  --callout-warn-border: #F59E0B;
  --callout-warn-text: #92400E;

  /* Code Blocks */
  --code-bg: #0F172A;
  --code-border: #1E293B;
  --code-line-highlight: rgba(59, 130, 246, 0.15);
}

[data-theme='dark'] {
  --tutorial-bg: #0B0F19;
  --tutorial-surface: #111827;
  --tutorial-border: #1F2937;
  --tutorial-text-main: #F3F4F6;
  --tutorial-text-muted: #9CA3AF;

  --tutorial-accent: #3B82F6;
  --tutorial-accent-hover: #60A5FA;
  --tutorial-accent-subtle: #1E3A8A;

  --callout-info-bg: rgba(30, 58, 138, 0.2);
  --callout-info-border: #60A5FA;
  --callout-info-text: #BFDBFE;

  --callout-tip-bg: rgba(6, 78, 59, 0.25);
  --callout-tip-border: #4ADE80;
  --callout-tip-text: #BBF7D0;

  --callout-warn-bg: rgba(120, 53, 15, 0.25);
  --callout-warn-border: #FBBF24;
  --callout-warn-text: #FDE68A;

  --code-bg: #030712;
  --code-border: #1F2937;
  --code-line-highlight: rgba(96, 165, 250, 0.2);
}
```

---

## 5. Review & Audit Checklist

- [ ] **Contrast check**: All body copy achieves $\ge 4.5:1$ contrast in both light and dark modes.
- [ ] **No pure black / pure white**: Glare-reducing off-white canvas used in light mode; soft deep charcoal used in dark mode.
- [ ] **Dual encoding**: Callouts and error states use both color and icons/labels for accessibility.
- [ ] **Syntax highlighting readability**: Low-contrast syntax colors (e.g. dark blue on dark slate) are audited and replaced.
- [ ] **State visibility**: Active links, tabs, hover states, and focus rings (`outline: 2px solid var(--tutorial-accent)`) are distinctly visible.
