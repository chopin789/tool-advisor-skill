# Tool Advisor Skill for Claude Code

**中文** | [English](#english)

---

## 简介

`tool-advisor` 是一个 Claude Code skill，让 Claude 在你工作时**主动提醒**你可以使用哪些工具——包括已安装的 skills、已连接的 MCP 服务器、以及 Claude Code 内置工具。

不再需要记住自己装了哪些工具，Claude 会在合适的时机自动提示你。

## 效果示例

当你发出一个任务请求时，Claude 会在回复前自动插入一条简短提示：

```
💡 **docx skill** is available — it'll give you proper Word formatting with TOC and styles.
```

```
💡 **Tools available for this task:** `pptx` skill (slide creation), `web_search` (for research).
```

```
💡 **GitHub MCP** (not installed) — would let you push this directly to a repo. Install via /mcp.
```

## 安装

将 `tool-advisor` 目录复制到 Claude Code 的 skills 目录：

```bash
mkdir -p ~/.claude/skills/
cp -r tool-advisor/ ~/.claude/skills/tool-advisor/
```

重启 Claude Code 后自动生效。

## 特性

- ✅ 根据当前任务内容**智能匹配**相关工具，不会无差别地列出所有工具
- ✅ 提示简短（1-2 行），不打断你的工作流
- ✅ 新安装 skill 或连接新 MCP 后**自动识别**，无需修改配置
- ✅ 对未安装但有价值的工具也会给出安装建议
- ✅ 纯对话消息（"谢谢"、"好的"）不会触发提示

## 工具覆盖范围

| 任务类型 | 会提醒的工具 |
|---|---|
| 创建/编辑 Word 文档 | `docx` skill |
| 处理 PDF | `pdf` / `pdf-reading` skill |
| 制作演示文稿 | `pptx` skill |
| 表格/数据处理 | `xlsx` skill |
| 网页研究 / 实时信息 | `web_search` 工具、browser MCP |
| 代码执行 / 脚本 | `bash` 工具 |
| GitHub / Git 操作 | GitHub MCP |
| 邮件 / 日历 / 任务 | Gmail、Google Calendar、Asana MCP |
| 前端 UI 开发 | `frontend-design` skill |
| Hugging Face 模型/数据集 | Hugging Face MCP |

---

<a name="english"></a>

## Introduction

`tool-advisor` is a Claude Code skill that **proactively reminds** you of available tools as you work — including installed skills, connected MCP servers, and Claude Code built-in tools.

No more forgetting what you've installed. Claude will surface the right tool at the right moment.

## Example

When you make a request, Claude automatically prepends a brief tip:

```
💡 **docx skill** is available — it'll give you proper Word formatting with TOC and styles.
```

```
💡 **Tools available for this task:** `pptx` skill (slide creation), `web_search` (for research).
```

```
💡 **GitHub MCP** (not installed) — would let you push this directly to a repo. Install via /mcp.
```

## Installation

Copy the `tool-advisor` directory to Claude Code's skills folder:

```bash
mkdir -p ~/.claude/skills/
cp -r tool-advisor/ ~/.claude/skills/tool-advisor/
```

Restart Claude Code and it will be active automatically.

## Features

- ✅ **Context-aware** — only tips when there's a specific match to your current task
- ✅ **Non-intrusive** — 1-2 line inline hints that don't interrupt your flow
- ✅ **Auto-discovers** newly installed skills and MCPs without any config changes
- ✅ Recommends uninstalled tools when the benefit is clearly significant
- ✅ Silent on conversational messages ("thanks", "ok", etc.)

## Tool Coverage

| Task type | Tools surfaced |
|---|---|
| Creating/editing Word docs | `docx` skill |
| Working with PDFs | `pdf` / `pdf-reading` skill |
| Building presentations | `pptx` skill |
| Spreadsheet / data work | `xlsx` skill |
| Web research / current events | `web_search` tool, browser MCP |
| Code execution / scripting | `bash` tool |
| GitHub / git operations | GitHub MCP |
| Email / calendar / tasks | Gmail, Google Calendar, Asana MCPs |
| Frontend UI development | `frontend-design` skill |
| Hugging Face models/datasets | Hugging Face MCP |

## License

MIT