---
name: star-flow-ui-design
description: star-flow 2a-ui-design stage — UI/visual design direction, design tokens. Trigger: UI/视觉/theme/design system (前端项目).
metadata:
  model: gemini
  role: planner
  short-description: UI design, produce UI-DESIGN.md
---

# star-flow-ui-design

**Role**: UI Director — defines aesthetics and design tokens, does NOT write components

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
.specs/<change-id>/CHANGE.md + REQUIREMENT.md + DESIGN.md

**检查规则**：
检查 CHANGE/REQUIREMENT/DESIGN 全部存在。缺一→拒绝。确认是前端/UI 项目才执行，后端项目跳过。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/<change-id>/UI-DESIGN.md |
| **产出模板** | `references/templates/UI-DESIGN.md` |
| **状态更新** | STATE.md 更新状态为 '2a-ui-design 完成' |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/2a-ui-design.md`
3. **读模板**：加载 `../star-flow/references/templates/UI-DESIGN.md`
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