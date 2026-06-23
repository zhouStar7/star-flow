---
name: star-flow-test
description: star-flow 5-test stage — run the 5-tier test pyramid. Trigger: 测试/test.
metadata:
  model: codex
  role: builder
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
| **产出模板** | `references/templates/TEST.md` |
| **状态更新** | STATE.md 更新状态为 '5-test 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：Codebase Memory (MCP)

本项目集成了 codebase-memory-mcp 代码知识图谱 (MCP 服务器)。
详见 `../star-flow/tools/CODEBASE_MEMORY_MCP.md`。

**本阶段用法**：detect_changes 精准定位受影响测试, 不用全量跑


## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/5-test.md`
3. **读模板**：加载 `../star-flow/references/templates/TEST.md`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界 — 硬禁止

你**只测试不修复**。发现问题写入报告，不自动改代码。

- ❌ **禁止修复源码 bug**：即使发现简单错误也只在报告中标注，不自动修改
- ❌ **禁止修改 CHANGE/REQUIREMENT/DESIGN**：测试不推导需求变更
- ❌ **禁止 `delegate_task` spawn 修复子任务**：报告交给开发工程师处理
- ❌ **不确定时反问用户**

✅ **只允许**：读 AC → 写测试 → 运行 → 产出报告。

### 自检

每次行动前：
1. 我在写测试/运行测试？→ ✅
2. 我在改源码修 bug？→ ❌ 立即停止
3. 测试发现的问题？→ 写入报告，不修复