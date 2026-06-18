---
name: star-flow-evolve
description: star-flow A-evolve lateral command — sync architecture docs from recent changes. Trigger: 同步架构/evolve/沉淀架构.
metadata:
  model: claude
  role: maintainer
  short-description: Architecture evolution
---

# star-flow-evolve

**Role**: Architect — reviews recent changes, updates CONTEXT.md and ARCHITECTURE.md

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/CONTEXT.md + 最近归档的 change 产物

**检查规则**：
检查 CONTEXT.md 存在。扫描 .specs/archive/ 中 last_evolve_at 之后归档的 change。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | 更新后的 CONTEXT.md / ARCHITECTURE.md |
| **产出模板** | `references/star-flow/无固定模板，按 A-evolve.md prompt 执行` |
| **状态更新** | STATE.md 更新 last_evolve_at 时间戳 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/A-evolve.md`
3. **读模板**：加载 `../star-flow/references/star-flow/无固定模板，按 A-evolve.md prompt 执行`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只整理沉淀，不写新功能代码。不创建新 change。
