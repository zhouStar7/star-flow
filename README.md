# star-flow

一套纯 Markdown 的 AI 编程工作流引擎。把一次软件变更拆成 8 个阶段 + 5 个横向命令，全程无运行时依赖。

---

## 安装

```bash
git clone https://github.com/zhouStar7/star-flow.git
cp -r star-flow/* ~/.hermes/skills/star-flow/
```

只有一个 skill，加载即用：

```
skill_view('star-flow')
```

---

## 使用方式

### 单 Agent（直接对话）

```
@star-flow 给项目加个暗色模式
```

agent 按路由表自动加载对应阶段 prompt。

### Multica 多人编排

用 `--parent` + `--stage` 把各阶段分发给 squad 中不同 agent。所有 agent 统一绑 `star-flow` skill，按需加载不同 `file_path`。

```bash
# 1. 创建主 issue（容器）
MAIN=$(multica issue create --title "暗色模式" --description "star-flow" --output json | jq -r '.id')

# 2. 按 stage 创建子 issue
multica issue create --title "[0-change] 澄清"        --parent $MAIN --stage 1 --assignee "需求师"
multica issue create --title "[1-requirement] 写 AC"   --parent $MAIN --stage 1 --assignee "需求师"
multica issue create --title "[2-design] 技术设计"     --parent $MAIN --stage 2 --assignee "架构师"
multica issue create --title "[3-task] 拆解任务"       --parent $MAIN --stage 3 --assignee "规划师"
multica issue create --title "[4-dev] T01 路由"        --parent $MAIN --stage 4 --assignee "开发者A"
multica issue create --title "[4-dev] T02 主题"        --parent $MAIN --stage 4 --assignee "开发者B"
multica issue create --title "[5-test] 全量测试"       --parent $MAIN --stage 5 --assignee "测试员"
multica issue create --title "[6-review] 代码审查"     --parent $MAIN --stage 6 --assignee "审查员"
multica issue create --title "[7-integration] 集成归档" --parent $MAIN --stage 7 --assignee "审查员"
```

**Stage barrier**：同 stage 所有子 issue done 后，下一 stage 自动唤醒。

---

## Agent 编排

| Agent | 职责 | 加载的 file_path |
|-------|------|-----------------|
| 需求师 | 需求澄清 + 验收标准 | `prompts/0-change.md`, `prompts/1-requirement.md` |
| 架构师 | 技术设计 + 架构决策 | `prompts/2-design.md` + `references/tech-stacks.md` |
| UI 设计师 | 视觉设计 + 换风格 | `prompts/2a-ui-design.md` + `references/ui-aesthetics.md` |
| 规划师 | 任务拆解 | `prompts/3-task.md` |
| 开发者 | 编码 + 项目入场 | `prompts/4-dev.md` + `references/frontend-engineer-rules.md` |
| 测试员 | 全量测试 | `prompts/5-test.md` + `references/test-pyramid.md` |
| 审查员 | 代码审查 + 集成 + 体检 | `prompts/6-review.md`, `prompts/7-integration.md` |

---

## 工作流

```
前端: CHANGE → REQUIREMENT → DESIGN → UI-DESIGN → TASK → DEV → TEST → REVIEW → INTEGRATION
后端: CHANGE → REQUIREMENT → DESIGN → TASK → DEV → TEST → REVIEW → INTEGRATION
```

横向命令（任何时候可单独调用）：
- **I-scan** — 老项目入场扫描 → CONTEXT.md
- **A-architect** — 建立 / 重构架构 → ARCHITECTURE.md
- **A-evolve** — 同步架构文档
- **L-restyle** — 换视觉风格（只改 CSS，不动逻辑）
- **M-health** — 代码库健康检查

---

## 文件结构

```
star-flow/
├── SKILL.md                  # 入口（路由表 + 规则 + 使用说明）
├── README.md                # 本文件
├── prompts/                 # 14 个阶段执行指令
│   ├── 0-change.md
│   ├── 1-requirement.md
│   ├── 2-design.md
│   ├── 2a-ui-design.md
│   ├── 3-task.md
│   ├── 4-dev.md
│   ├── 5-test.md
│   ├── 6-review.md
│   ├── 7-integration.md
│   ├── A-architect.md
│   ├── A-evolve.md
│   ├── I-intel-scan.md
│   ├── L-restyle.md
│   └── M-health.md
├── templates/               # 13 个产出物模板
│   ├── CHANGE.md
│   ├── REQUIREMENT.md
│   ├── DESIGN.md
│   ├── UI-DESIGN.md
│   ├── TASK.md
│   ├── SUMMARY.md
│   ├── PROGRESS.md
│   ├── TEST.md
│   ├── REVIEW.md
│   ├── CONTEXT.md
│   ├── ARCHITECTURE.md
│   ├── STATE.md
│   └── LESSONS.md
└── references/              # 规则 + 查阅型资料
    ├── RULES.md
    ├── SYSTEM.md
    ├── tech-stacks.md
    ├── frontend-engineer-rules.md
    ├── test-pyramid.md
    ├── ui-aesthetics.md
    ├── ui-anti-patterns.md
    └── forge.md
```
