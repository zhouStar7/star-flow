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
| **产出模板** | `references/star-flow/无固定模板，按 M-health.md prompt 执行` |
| **状态更新** | STATE.md 记录 last_health_check 时间戳 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 🔧 可用工具：CodeGraph

本项目集成了 codegraph 代码知识图谱。
详见 `../star-flow/tools/CODEGRAPH.md`。

**本阶段用法**：codegraph callers 找0引用导出, codegraph callees 找循环依赖


## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/M-health.md`
3. **读模板**：加载 `../star-flow/references/star-flow/无固定模板，按 M-health.md prompt 执行`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只诊断不治疗。产出报告和建议，不自动修代码。
