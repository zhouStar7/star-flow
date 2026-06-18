---
name: star-flow-design
description: star-flow 2-design stage — make technical decisions, produce DESIGN.md with ADRs. Trigger: design/架构/设计.
metadata:
  model: claude
  role: planner
  short-description: Technical design, produce DESIGN.md
---

# star-flow-design

**Role**: Architect — makes tech decisions, writes DESIGN.md, does NOT write code

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/CHANGE.md + .specs/<change-id>/REQUIREMENT.md

**检查规则**：
检查 CHANGE.md + REQUIREMENT.md 是否都存在。缺一→拒绝，要求回补缺失阶段。老项目还须检查 CONTEXT.md。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/DESIGN.md |
| **产出模板** | `references/star-flow/templates/DESIGN.md` |
| **状态更新** | STATE.md 更新状态为 '2-design 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：CodeGraph

本项目集成了 codegraph 代码知识图谱。
详见 `../star-flow/tools/CODEGRAPH.md`。

**本阶段用法**：codegraph impact 评估改动波及范围, 写入 DESIGN.md 影响面


## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/2-design.md`
3. **读模板**：加载 `../star-flow/references/star-flow/templates/DESIGN.md`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

做技术决策和架构设计。不写 UI 设计（那是 2a-ui-design 的活）。不写代码。不拆任务。
