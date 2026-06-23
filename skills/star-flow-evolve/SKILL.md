---
name: star-flow-evolve
description: star-flow A-evolve lateral command — sync architecture docs from recent changes. Trigger: 同步架构/evolve/沉淀架构.
metadata:
  model: codex
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
| **产出模板** | `references/无固定模板，按 A-evolve.md prompt 执行` |
| **状态更新** | STATE.md 更新 last_evolve_at 时间戳 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/A-evolve.md`
3. **读模板**：加载 `../star-flow/references/无固定模板，按 A-evolve.md prompt 执行`
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