# 角色分配表

> 模型映射：🤖 Claude → 推理判断 · 💻 Codex → 编码审查 · 🎨 Gemini → UI 视觉
> 详见 `models/MODELS.md`

## 协调者 (Coordinator) · 🤖 Claude
> 职责：读 STATE.md，判断进度，委托给对应角色

| Skill | 说明 | 模型 |
|-------|------|:----:|
| `star-flow-coordinator` | 路由调度，不执行阶段 | 🤖 |

---

## 扫描员 (Scanner) · 💻 Codex
> 职责：老项目入场扫描

| Skill | 说明 | 模型 |
|-------|------|:----:|
| `star-flow-scan` | 生成 .specs/CONTEXT.md | 💻 |

---

## 规划师 (Planner) · 🤖 Claude
> 职责：变更→需求→设计→任务拆解。**UI 设计除外（交给 Gemini）**

| 顺序 | Skill | 产出 | 模型 |
|------|-------|------|:----:|
| 1 | `star-flow-change` | CHANGE.md | 🤖 |
| 2 | `star-flow-requirement` | REQUIREMENT.md | 🤖 |
| 3 | `star-flow-design` | DESIGN.md | 🤖 |
| 4 | `star-flow-task` | TASK.md | 🤖 |

## UI 设计师 · 🎨 Gemini
> 职责：原型 HTML 设计、design tokens、换风格

| 顺序 | Skill | 产出 | 模型 |
|------|-------|------|:----:|
| — | `star-flow-ui-design` | UI-DESIGN.md | 🎨 |
| — | `star-flow-restyle` | 视觉变更 | 🎨 |

---

## 建造师 (Builder) · 💻 Codex
> 职责：开发 + 测试（写代码，不改 SPEC）

| 顺序 | Skill | 产出 | 模型 |
|------|-------|------|:----:|
| 1 | `star-flow-dev` | 代码 + SUMMARY.md | 💻 |
| 2 | `star-flow-test` | TEST.md | 💻 |

---

## 审查员 (Reviewer) · 💻 Codex
> 职责：审查 + 集成归档（只看不改）

| 顺序 | Skill | 产出 | 模型 |
|------|-------|------|:----:|
| 1 | `star-flow-review` | REVIEW.md | 💻 |
| 2 | `star-flow-integration` | UAT + 归档 | 💻 |

---

## 运维师 (Maintainer) · 🤖 Claude（架构）+ 💻 Codex（巡检）+ 🎨 Gemini（换风格）

| Skill | 用途 | 模型 |
|-------|------|:----:|
| `star-flow-architect` | 建立/重构架构文档 | 🤖 |
| `star-flow-evolve` | 同步架构演进 | 🤖 |
| `star-flow-restyle` | 换视觉风格 | 🎨 |
| `star-flow-health` | 代码体检 | 💻 |
