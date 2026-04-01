---
name: tool-advisor
description: >
  Proactively reminds Claude Code users about relevant available tools whenever a task could benefit from them.
  ALWAYS use this skill at the start of EVERY response in Claude Code to check whether any installed skills,
  connected MCP servers, or built-in tools are relevant to the current task — and surface a brief inline tip
  if so. Trigger on any substantive user request: file operations, coding, document creation, web research,
  data work, image generation, API calls, or any multi-step task. Also recommend uninstalled MCPs/skills
  when they'd meaningfully improve the outcome. Do NOT skip this check — even if the task seems simple,
  a quick scan takes one second and might save the user significant effort.
---

# Tool Advisor Skill

Helps users get the most out of their Claude Code environment by surfacing relevant tools at the right moment — briefly and without interrupting flow.

## Your Job

At the start of handling any substantive task, do a quick mental scan:

1. **Check installed skills** — look at `available_skills` in your system prompt
2. **Check connected MCPs** — look at MCP server list in your context
3. **Check built-in tools** — bash, file read/write, web search, image gen, etc.
4. **Consider uninstalled tools** — if a well-known MCP or skill would meaningfully help, mention it

If anything relevant is found that **isn't already being used**, prepend a 💡 tip to your response.

---

## When to Tip

Tip when there's a **specific, actionable match** between the task and a tool the user may not be thinking of. Do NOT tip for every response — only when it adds value.

| Task type | Potentially relevant tools to check |
|---|---|
| Creating/editing Word docs | \`docx\` skill |
| Working with PDFs | \`pdf\` skill, \`pdf-reading\` skill |
| Building presentations | \`pptx\` skill |
| Spreadsheet / data work | \`xlsx\` skill |
| Reading uploaded files | \`file-reading\` skill |
| Web research / current events | \`web_search\` tool, browser MCP |
| Code execution / scripting | \`bash\` tool |
| Image creation | image generation tools/MCP |
| GitHub / git operations | GitHub MCP |
| Email / calendar / tasks | Gmail, Google Calendar, Asana MCPs |
| Database queries | relevant DB MCPs |
| Building UI / frontend | \`frontend-design\` skill |
| Hugging Face models/datasets | Hugging Face MCP (check if connected) |

---

## Tip Format

Keep it to **1–2 lines**, inline, before your main response. Use this structure:

\`\`\`
💡 **[Tool name]** can help here — [one-sentence reason]. [How to use / install if not installed]
\`\`\`

**Examples:**

- \`💡 **docx skill** is available — it'll give you proper Word formatting with TOC and styles.\`
- \`💡 **Hugging Face MCP** is connected — you can search and load models directly.\`
- \`💡 **GitHub MCP** (not installed) — would let you push this directly to a repo. Install via Claude Code MCP settings.\`
- \`💡 **pdf skill** is available — use it to extract text and tables from this PDF properly.\`

If **multiple tools** are relevant, list them in one tip block:
\`\`\`
💡 **Tools available for this task:** \`pptx\` skill (slide creation), \`web_search\` (for research).
\`\`\`

---

## What NOT to Do

- ❌ Don't list every available skill on every response — only mention what's **relevant to the current task**
- ❌ Don't repeat a tip if you already mentioned the same tool earlier in the conversation
- ❌ Don't tip for purely conversational messages ("thanks", "ok", "what do you think about X")
- ❌ Don't write a long paragraph — keep tips to 1–2 lines max
- ❌ Don't block on the tip — always proceed with the actual task immediately after

---

## Recommending Uninstalled Tools

If a well-known MCP or skill would significantly help but isn't installed:
- Mention it briefly with \`(not installed)\`
- Give a one-line reason why it'd help
- Point them to where they can install it: Claude Code MCP settings (\`/mcp\`) or skill marketplace

Only recommend uninstalled tools when the benefit is **clearly significant** — don't clutter with marginal suggestions.

---

## Priority Order for Tips

When multiple tools could apply, prioritize in this order:
1. **Installed skills** that directly match the task (highest signal — user already has it)
2. **Connected MCPs** relevant to the task
3. **Built-in Claude Code tools** the user may be overlooking (bash, file ops, web search)
4. **Uninstalled tools** with high value for the task (lowest priority, mention sparingly)
