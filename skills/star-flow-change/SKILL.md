---
name: star-flow-change
description: star-flow 0-change stage — clarify a change idea into a concrete proposal. Trigger: new feature/bugfix/refactor, or '做/加/改/优化 + X'.
metadata:
  model: claude
  role: planner
  short-description: Clarify change, produce CHANGE.md
---

# star-flow-change

**Role**: Clarifier — asks clarifying questions, writes CHANGE.md, does NOT write code

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
老项目：.specs/CONTEXT.md

**检查规则**：
老项目检查 CONTEXT.md 是否存在。不存在→拒绝执行，要求先跑 star-flow-scan。新项目跳过此检查。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/CHANGE.md |
| **产出模板** | `references/templates/CHANGE.md` |
| **状态更新** | STATE.md 中创建新 change 条目，状态设为 '0-change 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/0-change.md`
3. **读模板**：加载 `../star-flow/references/templates/CHANGE.md`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只做变更澄清，不写代码。不改 CONTEXT.md。不进入设计阶段。
