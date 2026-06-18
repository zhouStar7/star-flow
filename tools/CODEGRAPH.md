# CodeGraph 集成

> codegraph 是代码知识图谱工具。在 star-flow 中替代手动 `find`/`grep`/`tree`。
> 项目需先运行 `codegraph init` 建立索引。

## 可用命令

| 命令 | 用途 | 示例 |
|------|------|------|
| `codegraph init <path>` | 初始化 + 首次索引 | `codegraph init .` |
| `codegraph index` | 全量重建索引 | `codegraph index` |
| `codegraph sync` | 增量同步变更 | `codegraph sync` |
| `codegraph files` | 项目文件结构 | `codegraph files` |
| `codegraph query <symbol>` | 搜索符号 | `codegraph query authMiddleware` |
| `codegraph callers <symbol>` | 查谁调用了它 | `codegraph callers loginHandler` |
| `codegraph callees <symbol>` | 查它调用了谁 | `codegraph callees main` |
| `codegraph impact <symbol>` | 改它会影响什么 | `codegraph impact UserModel` |
| `codegraph affected <files>` | 哪些测试受影响 | `codegraph affected src/api/auth.ts` |

---

## 阶段集成

### I-scan · star-flow-scan

```
替代：手动 tree / ls / find / grep
```

| 原来 | 用 codegraph |
|------|-------------|
| `tree -L 2 src/` | `codegraph files` |
| 手动翻 package.json | `codegraph query` 搜关键 import |
| 手动推断入口文件 | `codegraph callers` 找调用链入口 |

**新增能力**：自动发现模块依赖关系。

---

### 1-design · star-flow-design

```
替代：手动翻代码理解依赖
```

| 原来 | 用 codegraph |
|------|-------------|
| `grep -r "import.*from"` 找依赖 | `codegraph callees <symbol>` |
| 手动判断改动影响面 | `codegraph impact <symbol>` |

**新增能力**：精确评估改动波及范围 → 写 DESIGN.md 的「影响面」段。

---

### 4-dev · star-flow-dev

```
替代：手动 grep 搜索函数定义
```

| 原来 | 用 codegraph |
|------|-------------|
| `grep -r "function name"` | `codegraph query functionName` |
| 翻文件找调用者 | `codegraph callers functionName` |
| 改完后猜测影响 | `codegraph impact functionName` |

**新增能力**：改前检查影响面，改后 `codegraph sync` 更新索引。

---

### 5-test · star-flow-test

```
替代：手动判断哪些测试要跑
```

| 原来 | 用 codegraph |
|------|-------------|
| 跑全部测试 | `codegraph affected src/changed.ts` → 只跑相关测试 |

**新增能力**：精准测试，只跑受影响的测试文件。

---

### 6-review · star-flow-review

```
替代：人工 code review 遗漏
```

| 原来 | 用 codegraph |
|------|-------------|
| 肉眼判断未使用的导出 | `codegraph callers exportedFn` → 无调用者 = 死代码 |
| 手动检查改动影响 | `codegraph impact <changed_symbol>` → 自动生成影响报告 |

**新增能力**：自动发现死代码、未用依赖、断裂的调用链。

---

### M-health · star-flow-health

```
替代：手动巡检
```

| 原来 | 用 codegraph |
|------|-------------|
| eslint 规则 | `codegraph query` + `callers` 找 0 引用导出 |
| 手动翻 import | `codegraph callees` 找循环依赖 |

**新增能力**：死代码检测、循环依赖检测、未用依赖检测。
