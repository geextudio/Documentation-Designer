---
name: documentation-designer
description: 'Core architectural documentation design skill. Formats instructional tutorials, defines information architecture, ensures dual-format output (semantic Markdown and standalone index.html), and aligns documentation structure with high pedagogical standards.'
---

# Documentation Designer & Architecture Generator

Core architectural engine for structuring comprehensive, pedagogically sound, and visually engaging technical tutorials and documentation suites.

---

## 1. Dual-Format Delivery Standard

Every tutorial must be designed to export seamlessly into two complementary formats:
1. **Semantic Markdown (`.md`)**:
   - Universal compatibility with GitHub, GitBook, VitePress, Docusaurus, and Obsidian.
   - Standardized admonitions (`> [!NOTE]`, `> [!TIP]`, `> [!WARNING]`, `> [!CAUTION]`).
   - Explicit fenced code blocks with filename tags, diff indicators, and syntax labels.
   - Textual Mermaid diagrams for architectural clarity.
2. **Standalone Complete `index.html`**:
   - Zero-dependency single-file deployment.
   - Built-in Tailwind CSS styling, responsive grid layouts, interactive theme toggling, and client-side Mermaid rendering.
   - Integrated reading aids: progress indicator, sticky TOC, 1-click code copying, and mobile bottom bar.

---

## 2. Pedagogical Information Architecture

Structure every tutorial chapter around a consistent cognitive flow:
1. **Title & Orientation**: Action-oriented H1, estimated reading time, difficulty level, and prerequisite checklist.
2. **Learning Objectives**: A highlighted card outlining 2–3 concrete takeaways.
3. **Architectural Overview**: High-level diagram showing where the learner is and where they are going.
4. **Step-by-Step Execution**: Modular H2 milestones following the 4-step rhythm (Intent $\rightarrow$ Prereq $\rightarrow$ Code/Action $\rightarrow$ Verification).
5. **Expected Outcome & Testing**: Verified terminal output or visual verification checklist.
6. **Next Steps & Navigation**: Previous/Next chapter cards and links to companion repositories.

---

## 3. Quality Verification

- [ ] Clear F-pattern scannability with distinctive headings and bolded key concepts.
- [ ] Both Markdown and standalone HTML artifacts validate without broken links or missing tags.
- [ ] Information density is balanced; cognitive overload is mitigated through progressive disclosure.

