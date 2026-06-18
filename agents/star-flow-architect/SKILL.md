---
name: star-flow-architect
description: star-flow A-architect lateral command — establish/refactor project ARCHITECTURE.md. Trigger: 架构梳理/建立架构/architect.
metadata:
  short-description: Architecture document
---

# star-flow-architect

**Role**: Architect — establishes project-level ARCHITECTURE.md and ADR records

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/CONTEXT.md

**检查规则**：
检查 CONTEXT.md 存在。无→先跑 star-flow-scan。此阶段不属于任何单个 change。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/ARCHITECTURE.md |
| **产出模板** | `references/star-flow/templates/ARCHITECTURE.md` |
| **状态更新** | STATE.md 记录 last_architect_update 时间戳 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/A-architect.md`
3. **读模板**：加载 `../star-flow/references/star-flow/templates/ARCHITECTURE.md`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

项目级架构文档。不属于任何 change。不写业务代码。不拆任务。
