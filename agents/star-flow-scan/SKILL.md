---
name: star-flow-scan
description: star-flow I-intel-scan stage — brownfield onboarding. Scans an existing project to generate .specs/CONTEXT.md. Trigger: scan/intel/入场扫描/老项目.
metadata:
  short-description: Scan project, produce CONTEXT.md
---

# star-flow-scan

**Role**: Scanner — read-only, scans project structure, produces CONTEXT.md

---

## 📥 前置工件检查

进入本阶段前，**必须先检查以下文件是否存在**：

**需要检查的文件**：
无（这是 star-flow 的起点）

**检查规则**：
无需检查上游工件

> ⚠️ 前置工件缺失时：**拒绝执行，汇报缺失项，要求先跑上游阶段**。不要跳过、不要猜测、不要自己编造。

---

## 📤 输出工件

| 项目 | 详情 |
|------|------|
| **产出文件** | .specs/CONTEXT.md |
| **产出模板** | `references/star-flow/templates/CONTEXT.md` |
| **状态更新** | STATE.md 中记录 last_intel_scan 时间戳 |

> 📐 产出前先加载对应的模板文件，按模板格式写入。不要自行发明格式。

---

## 📋 执行指令

1. **读前置**：检查并读取上方列出的前置文件
2. **读 Prompt**：加载 `~/.hermes/skills/star-flow/references/star-flow/prompts/I-intel-scan.md`
3. **读模板**：加载 `~/.hermes/skills/star-flow/references/star-flow/templates/CONTEXT.md`
4. **读规则**：遵循 `~/.hermes/skills/star-flow/references/star-flow/RULES.md`
5. **执行**：按 prompt 指令推进
6. **产出**：按模板写入输出文件
7. **更新状态**：更新 STATE.md
8. **汇报**：完成后汇报产出物 + 下一步建议

---

## 🚫 边界

只读扫描，不写任何业务代码。不修改任何源文件。
