---
name: star-flow-requirement
description: star-flow 1-requirement stage — write acceptance criteria and scope from CHANGE.md. Trigger after 0-change is done.
metadata:
  short-description: Analyze requirements, produce REQUIREMENT.md
---

# star-flow-requirement

**Role**: Analyst — writes requirements and AC, does NOT write code

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/CHANGE.md

**检查规则**：
检查 CHANGE.md 是否存在且包含完整的「做什么/为什么/范围/验收标准」段。缺失→拒绝，要求先跑 star-flow-change。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/REQUIREMENT.md |
| **产出模板** | `references/star-flow/templates/REQUIREMENT.md` |
| **状态更新** | STATE.md 更新状态为 '1-requirement 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/1-requirement.md`
3. **读模板**：加载 `../star-flow/references/star-flow/templates/REQUIREMENT.md`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只做需求分析和 AC 编写。不做技术方案。不改 DESIGN.md。不写代码。
