---
name: star-flow-restyle
description: star-flow L-restyle lateral command — restyle/redesign UI without changing functionality. Trigger: 换风格/换皮/restyle.
metadata:
  model: gemini
  role: maintainer
  short-description: Visual restyle
---

# star-flow-restyle

**Role**: UI Director — changes visual style only, preserves all functionality

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
无强制前置（横向命令，可独立运行）

**检查规则**：
确认是视觉变更而非功能变更。确认用户指定了目标风格或参考。

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | 视觉变更计划 + 代码修改 |
| **产出模板** | `references/无固定模板，按 L-restyle.md prompt 执行` |
| **状态更新** | 不更新 STATE.md（不属于阶段流水线） |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/prompts/L-restyle.md`
3. **读模板**：加载 `../star-flow/references/无固定模板，按 L-restyle.md prompt 执行`
4. **读规则**：遵循 `../star-flow/references/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界 — 硬禁止

你**只改视觉不动功能**。

- ❌ **禁止修改组件逻辑/功能**：不改 script/业务逻辑/数据处理/API 调用
- ❌ **禁止增删组件**：不添加新组件、不删除现有组件
- ❌ **禁止改 DESIGN.md**：视觉改动基于现有 DESIGN.md，不覆盖架构决策
- ❌ **不确定时反问用户**

✅ **只允许**：改 CSS/SCSS、design tokens、颜色、字体、间距、动效。

### 自检

每次行动前：
1. 我在改样式/视觉？→ ✅
2. 我在改组件逻辑/功能？→ ❌ 立即停止
3. 我在添加新组件？→ ❌ 立即停止