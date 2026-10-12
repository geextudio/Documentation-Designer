# Documentation Designer Pro

Enterprise Agentic Engineering rules for documentation generation.

## Guides & Documentation

- [面向使用者的实战指南：如何使用 Agentic Engineering 体系构建现代教程 (Markdown)](docs/agentic-tutorial-creation-guide.md)
- [在 VS Code 中使用 GitHub Copilot Chat 与 Agentic Engineering 构建现代教程指南 (独立 HTML)](docs/index.html)
- [现代 SaaS 教程设计系统规范](docs/design-system.md)
- [教程质量评分与验收准则 (0–100 Rubric)](docs/documentation-rubric.md)

## Available Skills

| Skill | Focus & Capabilities | Path |
| :--- | :--- | :--- |
| `tutorial-color-palette` | 配色优化：调色板设计、明暗模式、WCAG对齐、代码高亮视觉协调、语义提示框配色 | [skills/tutorial-color-palette/SKILL.md](skills/tutorial-color-palette/SKILL.md) |
| `tutorial-reading-experience` | 阅读体验优化：排版字阶、行宽阅读限制（Measure）、垂直韵律、分步节奏、吸顶目录、代码一键复制 | [skills/tutorial-reading-experience/SKILL.md](skills/tutorial-reading-experience/SKILL.md) |
| `tutorial-responsive-layout` | 多屏幕适配：移动/平板/桌面断点布局重排、代码块与表格防溢出横滚、Mermaid图表缩放、移动端操作栏与触控人体工学 | [skills/tutorial-responsive-layout/SKILL.md](skills/tutorial-responsive-layout/SKILL.md) |
| `tutorial-ui-optimizer` | 教程整体 UI / UX 优化 | [skills/tutorial-ui-optimizer/SKILL.md](skills/tutorial-ui-optimizer/SKILL.md) |
| `accessibility-reviewer` | 可访问性（a11y）审核与规范支持 | [skills/accessibility-reviewer/SKILL.md](skills/accessibility-reviewer/SKILL.md) |
| `code-snippet-enhancer` | 代码片段增强与高亮格式化 | [skills/code-snippet-enhancer/SKILL.md](skills/code-snippet-enhancer/SKILL.md) |
| `diagram-architect` | 架构图与 Mermaid 流程图生成 | [skills/diagram-architect/SKILL.md](skills/diagram-architect/SKILL.md) |
| `documentation-designer` | 核心文档设计与规范制定 | [skills/documentation-designer/SKILL.md](skills/documentation-designer/SKILL.md) |
| `learning-path-engine` | 学习路径与教程步骤规划 | [skills/learning-path-engine/SKILL.md](skills/learning-path-engine/SKILL.md) |
| `seo-reviewer` | 文档 SEO 优化与结构化数据审核 | [skills/seo-reviewer/SKILL.md](skills/seo-reviewer/SKILL.md) |
| `blazor-docs-generator` | Blazor 文档生成与优化 | [skills/blazor-docs-generator/SKILL.md](skills/blazor-docs-generator/SKILL.md) |
| `nuxt-docs-generator` | Nuxt 文档生成与组件配置 | [skills/nuxt-docs-generator/SKILL.md](skills/nuxt-docs-generator/SKILL.md) |
| `springboot-docs-generator` | Spring Boot 教程与文档生成 | [skills/springboot-docs-generator/SKILL.md](skills/springboot-docs-generator/SKILL.md) |

## HTML 格式教程生成强制规范 (HTML Tutorial Generation Rules)

在生成任何 HTML 格式技术教程（包含单文件独立 `index.html` 或多页面模板）时，必须严格遵守以下规范：

1. **必须包含优雅且不喧宾夺主的页脚 (Footer)**：
   - 页面底部必须包含一个样式精致、现代但**不喧宾夺主**（Understated & Subtle）的全局 `<footer>`。
   - **页脚内容必须包含**：
     - **当前年份**（例如：`2026`，可通过脚本 `<span id="footer-year">2026</span>` 或静态生成对应年份）
     - **作者署名**：`Created by Geextudio`
     - 文本模式：`© 2026 · Created by Geextudio`（可带项目名称或品牌小圆点指示器）
   - **视觉设计与色彩规范**：
     - 顶部微边框：`border-t border-[var(--border-subtle)]`，背景与主画布微融合。
     - 字体阶梯与配色：采用紧凑的 `text-xs`，文字颜色设为静音次级色（`text-slate-400 dark:text-slate-500`），署名部分可略微加深（`text-slate-600 dark:text-slate-300 font-medium`），确保视觉重力适中，不干扰主体技术阅读。
   - **移动端与自适应避让**：
     - 当处于移动端视口且存在底部悬浮/吸底操作栏时，页面或页脚必须保留底部外边距/内边距（`pb-16` 或 `pb-20`），严防悬浮栏遮挡页脚版权信息。
   - **推荐标准 HTML 片段**：
     ```html
     <footer class="mt-auto border-t border-[var(--border-subtle)] bg-[var(--bg-surface)]/50 py-6 text-center text-xs text-slate-400 dark:text-slate-500">
       <div class="max-w-[1440px] mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-2">
         <div class="flex items-center gap-1.5">
           <span class="w-1.5 h-1.5 rounded-full bg-blue-500 inline-block"></span>
           <span>Documentation Designer Pro</span>
         </div>
         <div>
           <span>&copy; <span id="footer-year">2026</span> &middot; Created by <span class="font-medium text-slate-600 dark:text-slate-300">Geextudio</span></span>
         </div>
       </div>
     </footer>
     ```
