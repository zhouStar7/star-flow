# 角色分配表

## 协调者 (Coordinator)
> 职责：读 STATE.md，判断进度，委托给对应角色

| Skill | 说明 |
|-------|------|
| `star-flow-coordinator` | 路由调度，不执行阶段 |

---

## 扫描员 (Scanner)
> 职责：老项目入场扫描

| Skill | 说明 |
|-------|------|
| `star-flow-scan` | 生成 .specs/CONTEXT.md |

---

## 规划师 (Planner)
> 职责：变更→需求→设计→UI→任务拆解（全规划链路，不写代码）

| 顺序 | Skill | 产出 |
|------|-------|------|
| 1 | `star-flow-change` | CHANGE.md |
| 2 | `star-flow-requirement` | REQUIREMENT.md |
| 3 | `star-flow-design` | DESIGN.md |
| 4 | `star-flow-ui-design` | UI-DESIGN.md（仅前端） |
| 5 | `star-flow-task` | TASK.md |

---

## 建造师 (Builder)
> 职责：开发 + 测试（写代码，不改 SPEC）

| 顺序 | Skill | 产出 |
|------|-------|------|
| 1 | `star-flow-dev` | 代码 + SUMMARY.md |
| 2 | `star-flow-test` | TEST.md |

---

## 审查员 (Reviewer)
> 职责：审查 + 集成归档（只看不改）

| 顺序 | Skill | 产出 |
|------|-------|------|
| 1 | `star-flow-review` | REVIEW.md |
| 2 | `star-flow-integration` | UAT + 归档 |

---

## 运维师 (Maintainer)
> 职责：架构维护 + 风格 + 健康检查（横向命令，独立运行）

| Skill | 用途 | 触发 |
|-------|------|------|
| `star-flow-architect` | 建立/重构架构文档 | 架构梳理 |
| `star-flow-evolve` | 同步架构演进 | 定期沉淀 |
| `star-flow-restyle` | 换视觉风格 | 换皮/换风格 |
| `star-flow-health` | 代码体检 | 巡检 |
