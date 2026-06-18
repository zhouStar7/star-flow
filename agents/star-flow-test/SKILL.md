---
name: star-flow-test
description: star-flow 5-test stage — run the 5-tier test pyramid. Trigger: 测试/test.
metadata:
  short-description: Test execution, produce TEST.md
---

# star-flow-test

**Role**: Tester — runs functional/perf/security/compat/observability tests

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/REQUIREMENT.md + DESIGN.md + TASK.md + SUMMARY.md

**检查规则**：
检查所有上游文件存在且开发完成（SUMMARY.md 中所有 task 标记✅）。缺任务→拒绝。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/TEST.md |
| **产出模板** | `references/star-flow/templates/TEST.md` |
| **状态更新** | STATE.md 更新状态为 '5-test 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `~/.hermes/skills/star-flow/references/star-flow/prompts/5-test.md`
3. **读模板**：加载 `~/.hermes/skills/star-flow/references/star-flow/templates/TEST.md`
4. **读规则**：遵循 `~/.hermes/skills/star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

测试从 AC 派生，不依赖实现细节。覆盖功能/性能/安全/兼容/可观测性。不修代码（发现问题报告，不自动修复）。
