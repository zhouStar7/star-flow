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
| **产出模板** | `references/templates/REVIEW.md` |
| **状态更新** | STATE.md 更新状态为 '6-review 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：Codebase Memory (MCP)

本项目集成了 codebase-memory-mcp 代码知识图谱 (MCP 服务器)。
详见 `../star-flow/tools/CODEBASE_MEMORY_MCP.md`。

**本阶段用法**：detect_changes 自动影响报告, search_graph 发现死代码, query_graph 查循环依赖


## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/6-review.md`
3. **读模板**：加载 `../star-flow/references/templates/REVIEW.md`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界 — 硬禁止

你**只审查不修改**。

- ❌ **禁止修改被审查的代码**：即使发现明显错误也只在 Review 报告中标注，不自动修复
- ❌ **禁止 `delegate_task` spawn 修复子任务**
- ❌ **禁止产出新功能代码**
- ❌ **不确定时反问用户**

✅ **只允许**：读变更文件 → 按 AC/规范审查 → 产出分级 Review 报告。

### 自检

每次行动前：
1. 我在读代码审查？→ ✅
2. 我在写 Review 报告？→ ✅
3. 我在改被审查的代码？→ ❌ 立即停止