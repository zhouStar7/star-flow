---
name: star-flow-dev
description: star-flow 4-dev stage — implement one task with TDD + atomic commits. Trigger: 开发/实现/dev/跑 T<N>.
metadata:
  role: builder
  short-description: Develop code, TDD + commit
---

# star-flow-dev

**Role**: Developer — writes code with TDD, commits atomically, does NOT modify SPEC files

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/TASK.md

**检查规则**：
检查 TASK.md 存在且当前 task 未标记完成。无 TASK → 拒绝。读取 STATE.md 确定要执行的 task（用户指定的 T<N>，或按顺序下一个待处理）。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | 代码变更 + .specs/<change-id>/SUMMARY.md |
| **产出模板** | `references/star-flow/templates/SUMMARY.md` |
| **状态更新** | STATE.md 记录当前 task 进度。完成时追加 SUMMARY。所有 task 完成后更新状态为 '4-dev 完成'。 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/4-dev.md`
3. **读模板**：加载 `../star-flow/references/star-flow/templates/SUMMARY.md`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

按 TASK.md 逐项执行。TDD 流程：写测试→实现→重构→提交。每次只跑一个 task。不改 CHANGE/DESIGN/TASK。
