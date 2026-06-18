---
name: star-flow-restyle
description: star-flow L-restyle lateral command — restyle/redesign UI without changing functionality. Trigger: 换风格/换皮/restyle.
metadata:
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
| **产出模板** | `references/star-flow/无固定模板，按 L-restyle.md prompt 执行` |
| **状态更新** | 不更新 STATE.md（不属于阶段流水线） |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `../star-flow/references/star-flow/prompts/L-restyle.md`
3. **读模板**：加载 `../star-flow/references/star-flow/无固定模板，按 L-restyle.md prompt 执行`
4. **读规则**：遵循 `../star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只改视觉（颜色/字体/间距/动效），不动功能逻辑。不增删组件。不改变行为。
