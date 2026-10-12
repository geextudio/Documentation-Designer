# Documentation Designer Pro - Design System Specification

A unified, accessible, and high-aesthetic design system tailored for engineering documentation, interactive guides, and multi-format tutorials (Markdown and standalone HTML).

---

## 1. Aesthetic Trends & Visual Language

- **Modern SaaS & DevTools Aesthetics**: Inspired by Linear, Vercel, Stripe, and Tailwind UI. Clean geometric typography, subtle 1px translucent borders, purposeful elevation layers, and zero heavy drop-shadows.
- **Low-Glare Dual Palette**:
  - **Light Canvas**: `#F8FAFC` (Slate 50) canvas with pure white `#FFFFFF` surface containers to avoid blinding light glare.
  - **Dark Canvas**: `#0B0F19` deep obsidian with `#111827` elevated cards to prevent OLED haloing.
- **Micro-Interactions**: Smooth 150–200ms cubic transitions, 1-click clipboard animations, scrollspy table-of-contents, and smooth scroll offsets.

---

## 2. Reading Experience & Cognitive Flow

- **Measure (Line Width)**: Strictly enforce `60ch` to `72ch` on body prose (`prose-container`).
- **Typography Scale**:
  - Title ($H_1$): `2.25rem` (36px) / Line height 1.2
  - Milestone Steps ($H_2$): `1.5rem` (24px) / Line height 1.3 / `scroll-margin-top: 5rem`
  - Sub-sections ($H_3$): `1.25rem` (20px) / Line height 1.4
  - Body Prose: `1.03125rem` (16.5px) / Line height 1.8 / Vertical paragraph rhythm `margin-bottom: 1.25rem`
  - Monospace: `0.875rem` (14px) with high-legibility character differentiation (`0`/`O`, `1`/`l`/`I`)
- **4-Step Action Rhythm**:
  1. *Actionable Header*: Imperative verb and clear step number.
  2. *Context / Prerequisite*: 1–2 sentences explaining why this step exists.
  3. *Execution Block*: Code snippet with file path badge or terminal command.
  4. *Verification / Output*: Expected terminal output or test assertion.

---

## 3. Responsive Multi-Screen Layout Architecture

- **Desktop ($\ge 1024\text{px}$)**: 3-column architecture (260px Series Navigation + Central Article + 240px Sticky Table of Contents).
- **Tablet ($640\text{px} - 1023\text{px}$)**: 2-column or centered column with collapsible drawer navigation.
- **Mobile ($< 640\text{px}$)**:
  - 1-column distraction-free reading canvas.
  - Code blocks and tables isolated with smooth horizontal touch-scrolling.
  - Bottom-docked thumb action bar with "Previous Step", "Step Badge", and "Next Step".
  - Tap targets minimum $44 \times 44\text{px}$.

---

## 4. Multi-Format Output Requirements

When generating tutorials, two synchronized formats are produced:
1. **Semantic Markdown (`.md`)**:
   - Clean GitHub-flavored Markdown.
   - Standardized callouts (`> [!NOTE]`, `> [!TIP]`, `> [!WARNING]`, `> [!CAUTION]`).
   - Standard fenced code blocks with file names and language tags.
   - Embedded Mermaid architecture diagrams.
2. **Standalone Complete `index.html`**:
   - Completely self-contained single-file document.
   - Integrated dark/light theme switch with `localStorage` memory.
   - Reading progress bar and sticky scrollspy TOC.
   - 1-click code copy button with visual feedback.
   - Fully responsive on mobile, tablet, desktop, and ultrawide monitors.
   - **Mandatory Subtle Footer**: Includes an understated, elegant `<footer>` with the current year and `Created by Geextudio` (`© [Current Year] · Created by Geextudio`), styled with `text-xs text-slate-400 dark:text-slate-500`, a top subtle border `border-t border-[var(--border-subtle)]`, and mobile bottom bar clearance (`pb-20 lg:pb-6`).

