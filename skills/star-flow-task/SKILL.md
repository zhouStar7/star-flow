---
name: star-flow-task
description: star-flow 3-task stage — break design into atomic tasks with dependencies. Trigger: 拆任务/task/分解.
metadata:
  model: claude
  role: planner
  short-description: Task breakdown, produce TASK.md
---

# star-flow-task

**Role**: Planner — decomposes work into tasks, does NOT write code

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/DESIGN.md + UI-DESIGN.md（前端项目）

**检查规则**：
检查 DESIGN.md 存在。前端项目还需 UI-DESIGN.md。缺少→拒绝。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/TASK.md |
| **产出模板** | `references/templates/TASK.md` |
| **状态更新** | STATE.md 更新状态为 '3-task 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/3-task.md`
3. **读模板**：加载 `../star-flow/references/templates/TASK.md`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只拆任务和标并行。每个任务 ≤5 文件，有 verify。不写代码。不改 DESIGN。
