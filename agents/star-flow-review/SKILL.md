---
name: star-flow-review
description: star-flow 6-review stage — review code for spec compliance, quality, security. Trigger: review/审查/检查代码.
metadata:
  model: codex
  role: reviewer
  short-description: Code review, produce REVIEW.md
---

# star-flow-review

**Role**: Reviewer — reviews code, produces report, does NOT fix code

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/REQUIREMENT.md + TASK.md + TEST.md + git diff

**检查规则**：
检查 REQUIREMENT/TASK/TEST 全部存在，且 git diff 有内容。缺→拒绝。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/REVIEW.md |
| **产出模板** | `references/star-flow/templates/REVIEW.md` |
| **状态更新** | STATE.md 更新状态为 '6-review 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：CodeGraph

本项目集成了 codegraph 代码知识图谱。
详见 `../star-flow/tools/CODEGRAPH.md`。

**本阶段用法**：codegraph impact 自动影响报告, codegraph callers 发现死代码


## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/6-review.md`
3. **读模板**：加载 `../star-flow/references/star-flow/templates/REVIEW.md`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只审查不修改。按 🔴必须修 / 🟡建议修 / 🟢小问题 分级。每个问题标注文件:行号。不修代码。
