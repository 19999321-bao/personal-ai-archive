---
file: memory/decisions.md
category: memory
permission: READWRITE
last_updated: 2026-11-03
version: 1.0
---

# AI-READWRITE: 重要决策记录

> 记录关键决策的背景、选项、结论，供未来复盘与AI对齐。核心决策原则见 identity/goals.md。
> 本文件记录「在某个具体情境下做了什么决定」，区别于 goals.md 中的「通用原则」。

## 自动写入区（AI-READWRITE，按时间倒序追加到顶部）

### 2026-11-03 16:43 | 采用公开 GitHub 仓库托管个人 AI 档案
- 来源：人工 / Grok Bot
- 背景：需要让 ChatGPT/Claude/Gemini/Grok 等跨平台共享同一份个人上下文
- 选项：各平台分别维护笔记 / 单一公开 GitHub Markdown 仓库 / 私有仓库
- 结论：采用公开仓库 personal-ai-archive（用户 19999321-bao），只写入可公开事实；敏感信息与内部金额不入库
- 影响：便于任意 AI 用 raw URL 读取；写入仍需 PAT；须持续遵守公开口径
- 关联：identity/goals.md「跨 AI 复用」原则
