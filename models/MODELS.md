# 模型分配表

> 原则：按模型强项分配角色，不让 Claude 写 UI、不让 Gemini 做架构、不让 Codex 做 PRD。

## 分配总览

| 模型 | 强项 | 分配角色 | Agent Skills |
|------|------|---------|-------------|
| **Claude** (claude-sonnet-4) | 推理、判断、架构、PRD | 协调者 + 规划师 + 运维师 | coordinator, change, requirement, design, task, architect, evolve, health |
| **Codex** (opencode) | 编码、审查、扫描 | 扫描员 + 建造师 + 审查员 | scan, dev, test, review, integration |
| **Gemini** (gemini-3.1-pro) | 视觉、UI、HTML 原型 | UI 设计师 + 换风格 | ui-design, restyle |

---

## 详细映射

### Claude — 推理型（8 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Claude |
|--------|-------|------|----------------|
| ★★★ | star-flow-coordinator | 路由 | 需要理解模糊意图、判断上下文 |
| ★★★ | star-flow-change | 0-change | 产品判断、范围切分 |
| ★★★ | star-flow-requirement | 1-requirement | PRD 编写、AC 推导 |
| ★★★ | star-flow-design | 2-design | 架构决策、ADR 撰写 |
| ★★ | star-flow-task | 3-task | 任务拆解、依赖分析 |
| ★★ | star-flow-architect | A-architect | 架构文档、模块契约 |
| ★ | star-flow-evolve | A-evolve | 架构沉淀（可降级给 Codex） |
| ★ | star-flow-health | M-health | 代码巡检（可降级给 Codex） |

### Codex — 执行型（5 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Codex |
|--------|-------|------|---------------|
| ★★★ | star-flow-dev | 4-dev | TDD 编码、原子提交 |
| ★★★ | star-flow-test | 5-test | 自动化测试执行 |
| ★★★ | star-flow-review | 6-review | 代码审查（对代码变更感知强） |
| ★★ | star-flow-scan | I-scan | 项目扫描、目录测绘 |
| ★★ | star-flow-integration | 7-integration | 集成验证、归档 |

### Gemini — 视觉型（2 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Gemini |
|--------|-------|------|---------------|
| ★★★ | star-flow-ui-design | 2a-ui-design | HTML 原型设计、视觉 tokens、动画 |
| ★★★ | star-flow-restyle | L-restyle | 换视觉风格、design system |

---

## 使用方式

### Multica

```bash
# Claude agent — 规划 + 运维
multica agent create --name "star-flow 规划师" \
  --skill star-flow-coordinator,star-flow-change,star-flow-requirement,star-flow-design,star-flow-task,star-flow-architect,star-flow-evolve,star-flow-health \
  --model claude-sonnet-4

# Codex agent — 扫描 + 建造 + 审查
multica agent create --name "star-flow 建造师" \
  --skill star-flow-scan,star-flow-dev,star-flow-test,star-flow-review,star-flow-integration \
  --model opencode

# Gemini agent — UI 视觉
multica agent create --name "star-flow 视觉师" \
  --skill star-flow-ui-design,star-flow-restyle \
  --model gemini-3.1-pro
```

### Hermes Cron

```bash
hermes cronjob create --name "star-flow 规划" --skills star-flow-change --model claude-sonnet-4 ...
hermes cronjob create --name "star-flow 开发" --skills star-flow-dev --model opencode ...
hermes cronjob create --name "star-flow UI" --skills star-flow-ui-design --model gemini-3.1-pro ...
```
