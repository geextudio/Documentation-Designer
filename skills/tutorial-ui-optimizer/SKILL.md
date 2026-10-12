---
name: tutorial-ui-optimizer
description: 'Master UI/UX orchestrator for technical web tutorials. Optimizes overall interface polish, visual hierarchy, micro-interactions, dark/light theme switching, and seamless integration between Markdown prose and standalone HTML interactive elements.'
---

# Tutorial UI & UX Master Optimizer

The central orchestrator for engineering polished, high-aesthetic, and developer-friendly tutorial web experiences. Coordinates styling, micro-interactions, component consistency, and visual hierarchy across all tutorial sections.

---

## 1. Aesthetic Standards & Modern Web Design Trends

1. **Subtle Elevation & Clean Layering**:
   - Discard heavy diffuse box-shadows in favor of 1px translucent borders (`border: 1px solid var(--border-subtle)`).
   - Use multi-layer surface elevation (Canvas $\rightarrow$ Surface Card $\rightarrow$ Floating Flyout / Modal).
2. **Glassmorphism in Sticky Elements**:
   - Top navigation bars and floating bottom action bars use backdrop blur (`backdrop-filter: blur(12px); background: rgba(..., 0.85)`).
3. **Smooth Micro-Interactions**:
   - 150ms–200ms cubic-bezier transitions on hover, focus, and active states.
   - Distinct focus-visible outlines (`outline: 2px solid var(--tutorial-accent); outline-offset: 2px`) for keyboard accessibility.
4. **Visual Rhythm & Separation**:
   - Use soft divider lines and generous whitespace (`2.5rem` to `3rem` section spacing) instead of noisy decorative elements.

---

## 2. Interactive Component Specifications

- **Dual-Mode Theme Toggle**: Smooth transition between light and dark themes with persistence in `localStorage` and system theme fallbacks.
- **Scroll Progress & Scrollspy Navigation**:
  - Top 3px gradient reading progress bar.
  - Sticky right-hand Table of Contents dynamically highlighting the active section via `IntersectionObserver`.
- **Actionable Callouts**:
  - Standardized callout boxes with rounded corners (`border-radius: 0.75rem`), left border accent, and semantic icon badges.
- **Progressive Deep-Dives**:
  - Styled `<details>` and `<summary>` elements with smooth chevron rotation animation for optional architecture deep-dives.

---

## 3. Review Checklist

- [ ] Interface adheres to modern SaaS aesthetic (Linear/Vercel/Stripe style).
- [ ] No visual flickering during dark/light mode toggle.
- [ ] Sticky headers and floating toolbars do not occlude headings on anchor navigation (`scroll-margin-top: 5rem`).
- [ ] Full interaction parity between Markdown source annotations and HTML rendering.

