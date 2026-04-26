# 04 · 提示

可复用的版本化提示资产。提示是系统的一部分 — 不是一次性用品。

---

## 目的

能产出好结果的提示可以反复产出好结果。本章节存储、组织并对团队已验证的提示进行版本控制。

---

## 目录结构

```
04-prompt/
├── code/         # 代码生成、审查、重构的提示
├── design/       # 架构和系统设计任务的提示
├── review/       # PR 审查、安全审查、质量检查的提示
├── workflow/     # 流程自动化和规划的提示
└── templates/    # 用于构建新提示的基础模板
```

---

## 提示文件格式

每个提示文件应包含：

```markdown
# [提示名称]

## 目的
本提示的用途及使用时机。

## 输入
本提示期望的上下文 / 变量。

## 提示
[实际提示文本，用 {{变量}} 标记占位符]

## 预期输出
好的回答应该是什么样的。

## 备注
已知限制、边界情况或优化历史。
```

---

## 新增提示的流程

1. 在对应子目录创建文件，按上方格式填写
2. 本地测试 3 次以上，确认输出稳定
3. 提交时说明：为什么创建、替代了什么
4. 后续修改必须同步更新"备注"中的优化历史

---

## 提示使用流程

各提示之间存在输入输出关系，典型使用链如下：

```
需求结构化 → 架构设计 → 代码生成 / 重构 → PR 审查
```

| 提示 | 输入来源 | 输出去向 |
|------|---------|---------|
| requirement-structuring | 原始需求（文字/会议记录） | 结构化需求文档 → 作为架构设计的输入 |
| architecture-design | 结构化需求 + 系统约束 | 架构选项 → 人工决策后作为代码生成的约束 |
| code-generation | 接口定义 + 架构决策 | 实现代码初稿 → 进入审查流程 |
| refactoring | 已有代码 + 重构目标 | 重构后代码 → 进入审查流程 |
| pr-review | 代码变更 diff | 结构化审查意见 → 人工确认后合并 |

---

## 当前提示清单

| 文件 | 用途 | 版本 |
|------|------|------|
| [templates/prompt-template.md](templates/prompt-template.md) | 创建新提示的起始框架 | v1.0 |
| [code/code-generation.md](code/code-generation.md) | 根据接口定义生成实现代码 | v1.1 |
| [code/refactoring.md](code/refactoring.md) | 在不改变行为的前提下重构代码结构 | v1.0 |
| [code/test-generation.md](code/test-generation.md) | 为已有或新生成的代码编写测试用例 | v1.0 |
| [code/error-diagnosis.md](code/error-diagnosis.md) | 分析错误根本原因并给出修复方向 | v1.0 |
| [design/architecture-design.md](design/architecture-design.md) | 生成架构设计选项供人工决策 | v1.0 |
| [review/pr-review.md](review/pr-review.md) | PR 初轮 AI 审查，生成结构化意见 | v1.2 |
| [workflow/requirement-structuring.md](workflow/requirement-structuring.md) | 将模糊需求转化为结构化输入 | v1.1 |

---

## 规则

- 提示通过 git 进行版本控制 — 每次修改必须附带原因提交
- 不再能产出可靠输出的提示应标记说明，而非悄悄弃用
- 跨团队共享的提示存放在此处；个人或实验性提示在验证前可保留在本地
