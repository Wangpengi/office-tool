# 📄 智能论文排版系统 (Smart Paper Formatter)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)]()
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat&logo=tailwind-css&logoColor=white)]()

这是一个纯前端实现的**动态规则精准排版系统**。专为解决高校学生在撰写期末论文、毕业论文时面临的排版痛点而设计。

当我们在使用大语言模型（LLM）辅助写作时，AI 往往只能输出 Markdown 纯文本格式，无法保留诸如“黑体三号”、“宋体小四”、“行距固定值22磅”等严格的 Word 排版样式。本项目通过**“AI 提示词约束 + 正则映射渲染”**的巧妙设计，实现了从 AI 生成文本到符合标准规范的 Word 文档的一键转换。

## ✨ 核心特性

- 🎯 **动态提示词引擎**：只需将导师/学校的排版要求（如字体、字号、行距、缩进等）粘贴进来，系统会自动将其转化为带有强约束指令的 AI 提示词 (Prompt)。
- 🧠 **双重渲染机制 (核心黑科技)**：
  - **块级样式控制**：通过要求 AI 输出 `[注：...]` 标签，系统底层自动将其翻译为准确的 CSS 属性（支持各种中文字体、字号转换及精确的磅值行距）。
  - **行内局部补丁**：完美兼容摘要、关键词等“标题加粗但内容不加粗”的复杂需求，精准解析局部 `**加粗**` 语法。
- 📋 **无缝对接 MS Word**：在浏览器中渲染出的排版结果，一键复制后可直接粘贴至空白 Word 文档中，100% 继承所有设定好的样式要求。
- ⚡ **零依赖，开箱即用**：采用单文件 HTML 结构，使用 CDN 引入 Tailwind CSS，无需 Node.js 环境，无需 npm install，双击即可运行。

## 🚀 工作流指南 (Workflow)

本系统采用 **“三步走”** 工作流：

1. **配置排版规则**：
   在左侧输入框填入论文题目及具体的排版要求。点击生成，获取专属的 AI 提示词。
2. **AI 生成内容**：
   将生成的提示词复制并发送给你常用的 AI 对话平台（如 ChatGPT、文心一言、Kimi 等）。AI 将会根据指令，输出带有 `[注：...]` 标签和排版指令的结构化文本。
3. **精准解析与导出**：
   将 AI 生成的完整回复粘贴回本工具的解析框中。点击渲染，系统将在右侧生成完美的预览视图。点击“复制到 Word”，然后在 Word 中使用 `Ctrl + V`（保留源格式）即可大功告成！

## 🛠️ 本地运行与部署

### 本地运行
1. 克隆本项目到本地：
   ```bash
   git clone https://github.com/your-username/smart-paper-formatter.git
   ```
2. 直接在浏览器中双击打开 `formatter.html`（或重命名为 `index.html` 即可使用）。

### 部署到 GitHub Pages
由于本项目是纯静态单页面应用，非常适合部署在 GitHub Pages 上：
1. Fork 或上传本项目到你的 GitHub 仓库。
2. 进入仓库的 `Settings` -> `Pages`。
3. 将 Source 选为 `Deploy from a branch`，Branch 选择 `main`（或 `master`），然后 Save。
4. 等待几分钟，即可通过 `https://your-username.github.io/smart-paper-formatter` 访问你的专属排版工具！

## 💡 开发与重构记录

* **V1 基础版**：尝试通过正则猜测标题与正文，容错率较低。
* **V2 标签版**：引入了提示词约束，要求 AI 给每个段落打上明确的样式标签，大幅提高了解析准确度。
* **V3 完美修复版**：重构解析器，解决了 AI 标签导致“摘要与关键词全段加粗”的 Bug。引入**块级样式 + 行内 Markdown `**` 局部渲染**技术，做到了最终的完美还原。

## 🤝 贡献指南

欢迎提交 Issue 报告 Bug，或者发起 Pull Request 增加新的功能（例如：对多级列表的自适应支持、脚注的自动化处理等）。

## 📄 许可证

本项目基于 [MIT License](https://opensource.org/licenses/MIT) 开源。欢迎自由使用、修改和分发。
