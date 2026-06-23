---
name: star-flow-dev
description: star-flow 4-dev stage — implement one task with TDD + atomic commits. Trigger: 开发/实现/dev/跑 T<N>.
metadata:
  model: codex
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
| **产出模板** | `references/templates/SUMMARY.md` |
| **状态更新** | STATE.md 记录当前 task 进度。完成时追加 SUMMARY。所有 task 完成后更新状态为 '4-dev 完成'。 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：Codebase Memory (MCP)

本项目集成了 codebase-memory-mcp 代码知识图谱 (MCP 服务器)。
详见 `../star-flow/tools/CODEBASE_MEMORY_MCP.md`。

**本阶段用法**：search_graph 查定义, trace_path 查调用者, detect_changes 预判影响 (后台自动增量索引)

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/4-dev.md`
3. **读模板**：加载 `../star-flow/references/templates/SUMMARY.md`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界 — 硬禁止

你**只实现 TASK.md 中分配的当前 task**，不越界。

- ❌ **禁止修改架构文档**：不改 CHANGE.md / REQUIREMENT.md / DESIGN.md / TASK.md / ARCHITECTURE.md
- ❌ **禁止添加 TASK.md 范围外的功能**：不自行扩展需求、不「顺手优化」不相关的代码
- ❌ **禁止跳过 TDD 流程**：每次必须先写测试 → 实现 → 重构 → 提交
- ❌ **不确定时反问用户**

✅ **只允许**：读 TASK.md → TDD 实现 → commit → 汇报完成。

### 自检

每次行动前：
1. 这是 TASK.md 里分配的当前 task？→ ✅ 执行
2. 我在改架构/需求文档？→ ❌ 立即停止
3. 这不在 task 范围内？→ ❌ 不碰