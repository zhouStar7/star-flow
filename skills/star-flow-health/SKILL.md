---
name: star-flow-health
description: star-flow M-health lateral command — codebase health check. Trigger: 体检/health/技术债/巡检.
metadata:
  model: codex
  role: maintainer
  short-description: Codebase health check
---

# star-flow-health

**Role**: Maintainer — scans for debt, dead code, duplicates, stale dependencies

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/CONTEXT.md

**检查规则**：
检查 CONTEXT.md 存在。扫描 src/ + tests/ 最近活跃的文件。不依赖任何 change。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | 健康报告（输出到对话或 .specs/health/ 目录） |
| **产出模板** | `references/无固定模板，按 M-health.md prompt 执行` |
| **状态更新** | STATE.md 记录 last_health_check 时间戳 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：Codebase Memory (MCP)

本项目集成了 codebase-memory-mcp 代码知识图谱 (MCP 服务器)。
详见 `../star-flow/tools/CODEBASE_MEMORY_MCP.md`。

**本阶段用法**：search_graph 找 0 引用导出, query_graph 查循环依赖, detect_changes 分析未提交变更风险


## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/M-health.md`
3. **读模板**：加载 `../star-flow/references/无固定模板，按 M-health.md prompt 执行`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界 — 硬禁止

你**只产出本阶段的文档工件**，不触碰项目源码。

- ❌ **禁止 `write_file` / `patch` 修改项目源码**（.vue/.ts/.js/.css/.scss 等）
- ❌ **禁止 `terminal` 运行项目命令**（npm/dev/build/git add/commit 等）
- ❌ **禁止 `delegate_task` spawn 子任务做开发**（只产出自己的工件文件）
- ❌ **禁止越界进入其他阶段**（如 scan 不做 design，design 不做 dev）
- ❌ **不确定时反问用户**

✅ **只允许**：读文件分析 → 写自己的工件（.specs/ 下对应文件）→ 汇报产出。

### 自检

每次行动前：
1. 我在读文件/分析？→ ✅
2. 我在写自己的阶段工件？→ ✅
3. 我在改项目源码？→ ❌ 立即停止
4. 我在跑项目命令？→ ❌ 立即停止