---
name: star-flow-integration
description: star-flow 7-integration stage — final UAT, smoke tests, archive. Trigger: 集成/上线/验收/归档.
metadata:
  model: opencode
  role: reviewer
  short-description: Integration & archive
---

# star-flow-integration

**Role**: Verifier — runs UAT, smoke tests, archives the change

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/ 下全部产物（CHANGE/REQUIREMENT/DESIGN/TASK/TEST/REVIEW/SUMMARY）

**检查规则**：
检查 .specs/<id>/ 下所有阶段文件齐全。缺→拒绝。REVIEW.md 中不能有未解决的🔴问题。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | UAT.md + 归档 |
| **产出模板** | `references/无固定模板，按 7-integration.md prompt 执行` |
| **状态更新** | STATE.md 标记 change 为 'archived'。归档到 .specs/archive/。 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/7-integration.md`
3. **读模板**：加载 `../star-flow/references/无固定模板，按 7-integration.md prompt 执行`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界 — 硬禁止

你**只做最终验收和归档**，不做新功能、不修 bug。

- ❌ **禁止添加新功能**：验收阶段不增功能、不改设计
- ❌ **禁止修复未通过的测试**：发现失败 → 汇报并停止，不自动修复
- ❌ **禁止 `delegate_task` spawn 修复子任务**
- ❌ **不确定时反问用户**

✅ **只允许**：运行 UAT/smoke test → 归档 → 汇报结果。

### 自检

每次行动前：
1. 我在做最终验收？→ ✅
2. 我在修 bug？→ ❌ 立即停止
3. 我在添加功能？→ ❌ 立即停止