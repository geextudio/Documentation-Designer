---
name: diagram-architect
description: 'Generate modern, responsive architecture diagrams, sequence flows, and system topologies using Mermaid.js. Optimizes diagrams for light/dark themes, responsive viewports, and visual clarity in technical tutorials.'
---

# Diagram Architect & Mermaid Visualizer

Specialized skill for creating lucid, professional architecture diagrams, data pipelines, and sequence flows tailored for developer tutorials and documentation.

---

## 1. Diagram Design Principles

1. **Simplicity Over Clutter**: Keep tutorial diagrams focused on the immediate concept (max 6–8 nodes per diagram) rather than overwhelming full-enterprise architecture.
2. **Harmonious Styling**:
   - Align diagram colors with the tutorial theme (cool blues, emerald greens, and muted slates).
   - In HTML: Initialize Mermaid with dynamic theme detection (`dark` vs `default`) matching the active theme toggle.
3. **Responsive Scaling**:
   - Mermaid SVG containers must use `width: 100%; height: auto; max-width: 100%;`.
   - Provide horizontal overflow scrolling or full-screen expansion modal on narrow mobile screens.
4. **Dual Format Compatibility**:
   - In Markdown: render standard ```mermaid ... ``` code blocks.
   - In HTML: render `<div class="mermaid">...</div>` with Mermaid.js runtime rendering.

---

## 2. Standard Diagram Types in Tutorials

- **System Flow / Pipeline**: `graph LR` or `flowchart TD` showing input $\rightarrow$ gateway $\rightarrow$ processing queue $\rightarrow$ datastore.
- **Sequence Diagram**: `sequenceDiagram` showing API handshake, token issuance, and backpressure messaging.
- **State Machine**: `stateDiagram-v2` showing step-by-step state transitions.

---

## 3. Review Checklist

- [ ] Diagrams correctly render in both Markdown previewers and standalone HTML.
- [ ] Diagram text labels are concise and bilingual/multilingual friendly.
- [ ] No SVG truncation or layout distortion on mobile viewports.
- [ ] Mermaid node colors adjust cleanly to light and dark themes.

