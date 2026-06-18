# 模型分配表

> 原则：按模型强项分配角色。

## 分配总览

| 模型 | 强项 | 分配角色 | Agent Skills |
|------|------|---------|-------------|
| **Claude** | 推理、判断、PRD | 规划师 | change, requirement, design, task |
| **Codex** | 编码、审查、架构运维 | 扫描 + 建造 + 审查 + 运维 | scan, dev, test, review, architect, evolve, health |
| **Gemini** | 视觉、UI、HTML 原型 | UI 设计师 | ui-design, restyle |
| **Hermes** | 协调调度 | 协调者 | coordinator |
| **OpenCode** | 集成归档 | 集成 | integration |

---

## 详细映射

### 🤖 Claude — 推理型（4 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Claude |
|--------|-------|------|----------------|
| ★★★ | star-flow-change | 0-change | 产品判断、范围切分 |
| ★★★ | star-flow-requirement | 1-requirement | PRD 编写、AC 推导 |
| ★★★ | star-flow-design | 2-design | 架构决策、ADR 撰写 |
| ★★ | star-flow-task | 3-task | 任务拆解、依赖分析 |

### 💻 Codex — 执行型（7 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Codex |
|--------|-------|------|---------------|
| ★★★ | star-flow-dev | 4-dev | TDD 编码、原子提交 |
| ★★★ | star-flow-test | 5-test | 自动化测试执行 |
| ★★★ | star-flow-review | 6-review | 代码审查 |
| ★★ | star-flow-scan | I-scan | 项目扫描、目录测绘 |
| ★★ | star-flow-architect | A-architect | 架构文档、模块梳理 |
| ★ | star-flow-evolve | A-evolve | 架构沉淀 |
| ★ | star-flow-health | M-health | 代码巡检 |

### 🎨 Gemini — 视觉型（2 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Gemini |
|--------|-------|------|---------------|
| ★★★ | star-flow-ui-design | 2a-ui-design | HTML 原型设计、视觉 tokens |
| ★★★ | star-flow-restyle | L-restyle | 换视觉风格 |

### 🔀 Hermes — 协调型（1 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 Hermes |
|--------|-------|------|---------------|
| ★★★ | star-flow-coordinator | 路由 | 协调调度、状态管理 |

### 📦 OpenCode — 集成型（1 个 skill）

| 优先级 | Skill | 阶段 | 为什么是 OpenCode |
|--------|-------|------|-----------------|
| ★★★ | star-flow-integration | 7-integration | 集成验证、归档 |
