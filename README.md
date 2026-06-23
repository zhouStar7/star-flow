# star-flow

一套 AI 编程工作流引擎——15 个独立 Agent Skill，5 种模型按能力分工。

不是工具，是一组文件。clone 即用，无运行时依赖。

---

## 快速开始

```bash
git clone https://github.com/zhouStar7/star-flow.git
cp -r star-flow/skills/* ~/.hermes/skills/
cp -r star-flow/references ~/.hermes/skills/star-flow/references/
cp star-flow/SKILL.md ~/.hermes/skills/star-flow/
```

入口：`@star-flow/START.md` + 你的意图

---

## 架构

```
star-flow/
├── SKILL.md                 # 协调者入口（Hermes）
├── skills/                  # 15 个独立 Agent Skill
│   ├── star-flow-coordinator/    🔀 路由调度
│   ├── star-flow-scan/           💻 老项目入场扫描
│   ├── star-flow-change/         🤖 变更澄清
│   ├── star-flow-requirement/    🤖 需求分析
│   ├── star-flow-design/         🤖 架构设计
│   ├── star-flow-ui-design/      🎨 UI 设计
│   ├── star-flow-task/           🤖 任务拆解
│   ├── star-flow-dev/            💻 开发执行
│   ├── star-flow-test/           💻 测试
│   ├── star-flow-review/         💻 代码审查
│   ├── star-flow-integration/    📦 集成归档
│   ├── star-flow-architect/      💻 架构建立
│   ├── star-flow-evolve/         💻 架构演进
│   ├── star-flow-restyle/        🎨 换视觉风格
│   └── star-flow-health/         💻 代码体检
├── references/              # 共享基础设施
│   ├── START.md             # 路由规则
│   ├── METHODOLOGY.md       # 方法论
│   ├── RULES.md             # 🔴🟡🟢 三级规则
│   ├── MODELS.md            # 模型分配方案
│   ├── ROLES.md             # 角色分配表
│   ├── prompts/             # 15 个阶段执行指令
│   ├── templates/           # 14 个产出物模板
│   └── reference/           # 6 个参考文档
└── tools/
    └── CODEGRAPH.md         # CodeGraph 集成指南
```

---

## 模型分工

| 模型 | Agent | 强项 |
|------|:-----:|------|
| 🔀 **Hermes** | coordinator | 协调路由 |
| 🤖 **Claude** | change, requirement, design, task | 推理判断、PRD、架构 |
| 💻 **Codex** | scan, dev, test, review, architect, evolve, health | 编码、审查、运维 |
| 🎨 **Gemini** | ui-design, restyle | HTML 原型、视觉设计 |
| 📦 **OpenCode** | integration | 集成归档 |

[完整模型分配](references/MODELS.md) · [角色分配表](references/ROLES.md)

---

## 边界规则 — 硬禁止

每个角色有**自检清单**，确保不越界：

| 角色类型 | 角色 | 禁止行为 |
|---------|------|---------|
| 🔀 协调者 | coordinator | ❌ 禁止 spawn 匿名子任务做开发；只做路由调度 |
| 📝 文档产出者 | scan/change/requirement/design/task/ui-design/architect/evolve/health | ❌ 禁止 write_file/patch/terminal 触碰项目源码 |
| 💻 开发 | dev | ❌ 禁止修改架构文档；禁止添加 TASK.md 外的功能 |
| 🧪 测试 | test | ❌ 只测不修：发现问题写入报告，不自动改代码 |
| 🔍 审查 | review | ❌ 只审不改：即使发现错误也只标注，不自动修复 |
| 📦 集成 | integration | ❌ 只验收：不添加新功能、不修 bug |
| 🎨 换皮 | restyle | ❌ 只改 CSS/token：不改组件逻辑、不增删组件 |

> 每次行动前自检：我在做什么？→ 越界则立即停止。不确定时反问用户。

---

## 工作流

```
🔀 Hermes   🤖 Claude              🎨 Gemini   💻 Codex                    📦 OpenCode
    │           │                      │           │                           │
 协调路由 → change → requirement → ui-design → dev → test → review → architect → integration
                └── design ──┘                      └── scan ──┘  └── evolve ──┘
                └── task ───┘                                    └── health ──┘
                                                    └── restyle ─┘
```

---

## 工具集成

- **[CodeGraph](tools/CODEGRAPH.md)** — 代码知识图谱，替代手动 grep/find/tree
- 支持 Windsurf / Claude Code / Cursor / Copilot / Codex / Gemini / Cline 等 AI IDE

---

## 为什么是纯 markdown

不依赖 CLI、不绑版本。clone 就用，想改哪条改哪个 `.md`。不会某天被工具更新坑到。
