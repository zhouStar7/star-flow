# star-flow

轻量级 AI 开发工作流引擎，15 个独立 Agent Skill + 统一协调者。

## 结构

```
SKILL.md                 # 协调者入口
agents/                  # 15 个独立 Agent Skill
  star-flow-scan/        # I-scan 老项目入场扫描
  star-flow-change/      # 0-change 变更澄清
  star-flow-requirement/ # 1-requirement 需求分析
  star-flow-design/      # 2-design 架构设计
  star-flow-ui-design/   # 2a-ui-design UI 设计
  star-flow-task/        # 3-task 任务拆解
  star-flow-dev/         # 4-dev 开发执行
  star-flow-test/        # 5-test 测试
  star-flow-review/      # 6-review 代码审查
  star-flow-integration/ # 7-integration 集成归档
  star-flow-architect/   # A-architect 架构建立
  star-flow-evolve/      # A-evolve 架构演进
  star-flow-restyle/     # L-restyle 换风格
  star-flow-health/      # M-health 代码体检
  star-flow-coordinator/ # 调度队长
references/              # 共享基础设施
  START.md               # 路由规则
  METHODOLOGY.md         # 方法论
  RULES.md               # 规则
  prompts/               # 15 个阶段 prompt
  templates/             # 14 个产出模板
  reference/             # 参考文档
```

## 安装

```bash
cp -r agents/* ~/.hermes/skills/
cp -r references ~/.hermes/skills/star-flow/references/
cp SKILL.md ~/.hermes/skills/star-flow/SKILL.md
```

## 使用

入口：`@star-flow/START.md` + 你的意图

详细文档见 `references/star-flow/README.md`
