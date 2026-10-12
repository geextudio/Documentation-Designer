---
name: tutorial-responsive-layout
description: 'Optimize web tutorial layouts, responsive grids, cross-device breakpoints, mobile touch ergonomics, and code block/diagram reflow across diverse screen sizes (mobile, tablet, laptop, ultrawide). Use when implementing multi-column documentation layouts, handling code snippet horizontal overflow on mobile, optimizing Mermaid and architecture diagrams for small viewports, designing collapsible sidebars, or building thumb-friendly mobile tutorial navigation.'
---

# Tutorial Responsive Layout & Multi-Screen Size Optimizer

A specialized skill for engineering resilient, fluid, and ergonomic responsive layouts for web tutorials across mobile devices, tablets, standard desktops, and ultrawide displays.

---

## 1. Core Principles

1. **Information Density Reflow**: Seamlessly transition from a 3-column layout on desktop (Navigation Sidebar + Reading Column + Table of Contents) to a focused, distraction-free single-column layout on mobile.
2. **Zero Layout Distortion on Code & Tables**: Long code strings, terminal logs, and wide data tables must scroll horizontally within isolated containers and must never break page width or cause horizontal viewport scrolling.
3. **Diagram & Visual Adaptability**: Architecture diagrams (Mermaid, SVGs) must remain legible via responsive vector scaling (`viewBox`), pinch-to-zoom, or full-screen modal expansion on touch screens.
4. **Touch & Thumb Ergonomics**: All interactive elements (copy buttons, next/previous step links, TOC triggers) must maintain a minimum touch target of $44 \times 44\text{px}$ and prioritize lower-screen thumb reach on mobile.
5. **Fluid Typography & Dynamic Spacing**: Use CSS `clamp()` and container queries (`@container`) so font sizes, card paddings, and column gaps scale smoothly without abrupt jumps.

---

## 2. Viewport Breakpoint Architecture

| Breakpoint Tier | Viewport Width | Layout Architecture | Navigation & TOC Strategy |
| :--- | :--- | :--- | :--- |
| **Mobile (`sm`)** | `< 640px` | 1-Column full-width layout, padded with `1rem` (16px) gutters | Drawer menu for chapters; floating bottom sheet / pill for TOC; bottom-docked Step bar |
| **Tablet (`md`)** | `640px – 1023px` | 2-Column or full width with expandable off-canvas navigation | Collapsible left drawer navigation; floating or top-collapsible TOC |
| **Desktop (`lg`)** | `1024px – 1439px` | 3-Column: Left Sidebar (`240px–280px`), Center Content (`max 72ch`), Right TOC (`200px–240px`) | Fixed Left Sidebar + Main Content + Sticky Right TOC |
| **Ultrawide (`xl+`)** | `\ge 1440px` | Centered 3-column with bounded container (`max-width: 1440px`) to prevent content drift | Fixed Left Sidebar + Centered Content + Sticky Right TOC |

---

## 3. High-Friction Responsive Patterns in Tutorials

### 3.1 Code Block Adaptation
Code blocks are prone to breaking mobile layouts:
- **Horizontal Scroll Isolation**: Wrap preformatted code inside an overflow container with `-webkit-overflow-scrolling: touch; overflow-x: auto;`.
- **Sticky Actions**: The header bar with file name and "Copy" button must remain fixed or sticky at the top of the code box while code scrolls underneath.
- **Line Numbers**: Automatically hide line numbers on viewports $< 480\text{px}$ to conserve critical horizontal code width.

```css
.tutorial-code-block {
  position: relative;
  max-width: 100%;
  border-radius: 0.5rem;
  overflow: hidden;
}

.tutorial-code-block pre {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
  padding: 1rem;
  font-size: clamp(0.8125rem, 0.75rem + 0.25vw, 0.9375rem);
}
```

### 3.2 Tables & Comparison Matrices Reflow
Data tables (e.g. CLI flag tables, feature comparisons) fail on mobile if rendered in rigid grid structures:
- **Card-List Transform on Mobile**: Convert table rows into stacked key-value cards under `640px` via CSS data-attributes (`td::before { content: attr(data-label); }`).
- **Scroll Container Fallback**: Alternatively, wrap in an explicitly bounded container with smooth left/right shadow indicators hinting at hidden scrollable columns.

### 3.3 Interactive Diagrams & Mermaid Scaling
- Always configure Mermaid / SVG containers with `width: 100%; height: auto; max-width: 100%;`.
- Add an "Expand / Fullscreen" button (`🔍 Fullscreen`) on mobile screens to let users examine intricate architecture diagrams in a dedicated zoomable modal.

---

## 4. Mobile Ergonomics & Step Navigation

Reading tutorials on mobile requires quick thumb access to navigation:
- **Bottom-Docked Step Controller**: On mobile viewports, pin a compact action bar to the bottom of the viewport with safe-area insets (`env(safe-area-inset-bottom)`):
  - Left: `← Prev Step` button.
  - Center: `Step X of Y` progress badge.
  - Right: `Next Step →` button.
- **Minimum Tap Targets**: Buttons, menu toggles, and checklist checkboxes must be at least $44 \times 44\text{px}$ bounding box.

```css
/* Mobile Bottom Action Bar */
@media (max-width: 640px) {
  .tutorial-mobile-footer {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.75rem 1rem calc(0.75rem + env(safe-area-inset-bottom));
    background: var(--tutorial-surface);
    border-top: 1px solid var(--tutorial-border);
    z-index: 50;
  }

  /* Reserve bottom spacing so footer doesn't obscure content */
  .tutorial-content {
    padding-bottom: 5rem;
  }
}
```

---

## 5. Responsive Grid Layout Architecture (CSS Grid & Container Queries)

```css
/* Modern 3-Column Responsive Documentation Shell */
.doc-layout {
  display: grid;
  grid-template-columns: 1fr;
  min-height: 100vh;
}

/* Tablet & Desktop Layout */
@media (min-width: 1024px) {
  .doc-layout {
    grid-template-columns: 260px minmax(0, 1fr) 240px;
    max-width: 1440px;
    margin: 0 auto;
  }

  .doc-sidebar {
    position: sticky;
    top: 4rem;
    height: calc(100vh - 4rem);
    overflow-y: auto;
  }

  .doc-toc {
    position: sticky;
    top: 4rem;
    height: calc(100vh - 4rem);
    overflow-y: auto;
  }
}

/* Fluid reading typography */
.doc-article {
  padding: clamp(1rem, 0.5rem + 1.5vw, 2.5rem);
  font-size: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
}
```

---

## 6. Review & Audit Checklist

- [ ] **No horizontal window overflow**: The page never triggers horizontal scrolling on any mobile viewport down to $320\text{px}$.
- [ ] **Code block boundary check**: Code snippets, terminal inputs, and commands scroll smoothly within their block containers.
- [ ] **TOC accessible across viewports**: Right-hand TOC gracefully collapses into a quick-access top dropdown or mobile floating sheet.
- [ ] **Diagram responsiveness**: Diagrams resize gracefully with `viewBox` and offer an expand/zoom action on narrow screens.
- [ ] **Touch target compliance**: All actionable buttons and links meet the $44 \times 44\text{px}$ minimum size for touch interaction.
- [ ] **Safe-area padding**: Mobile bottom bars and floating elements respect `env(safe-area-inset-bottom)` on iOS devices.
