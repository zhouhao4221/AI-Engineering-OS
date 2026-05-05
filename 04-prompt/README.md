# 04 · 提示

记录在反复实践中验证有效的 AI 任务操作模式。

---

## 这些文件是什么

不是填空模板，是**任务操作手册**。每个文件回答三件事：

1. **准备什么** — 做这类任务前需要收集哪些上下文（这是最重要的部分）
2. **怎么触发** — 对 Claude Code 说什么，或怎么写进 CLAUDE.md 让它自动应用
3. **怎么判断** — 好的输出长什么样，常见失败模式是什么

---

## 三种使用方式

**随用随查（最低摩擦）**
开始一个任务之前，扫一眼对应文件，确认需要准备的输入已经齐全。最常见的 AI 输出差的原因，是某个关键上下文没传。

**直接引用（Claude Code）**
不需要复制粘贴，直接告诉 Claude Code 去读：
```
先读 04-prompt/code/code-generation.md，然后实现 [函数名]
```

**写入 CLAUDE.md（自动生效）**
对于高频任务，在 CLAUDE.md 里引用对应文件，之后每次触发该类任务时自动应用：
```markdown
## 代码生成
生成代码前，按 04-prompt/code/code-generation.md 的输入清单确认上下文齐全。
```

---

## 目录结构

```
04-prompt/
├── code/         代码生成、重构、测试、错误诊断
├── design/       架构设计、UI 设计
├── review/       PR 审查
├── workflow/     需求结构化
└── templates/    新增提示文件的格式框架
```

---

## 当前文件清单

| 文件 | 任务 |
|------|------|
| [code/code-generation.md](code/code-generation.md) | 根据接口定义生成实现代码 |
| [code/refactoring.md](code/refactoring.md) | 在不改变行为的前提下重构代码结构 |
| [code/test-generation.md](code/test-generation.md) | 为代码编写测试用例 |
| [code/error-diagnosis.md](code/error-diagnosis.md) | 分析错误根本原因并给出修复方向 |
| [design/architecture-design.md](design/architecture-design.md) | 生成架构方案选项供决策 |
| [design/ai-design-prompt.md](design/ai-design-prompt.md) | UI 生成：新组件、页面布局、设计稿转代码 |
| [review/pr-review.md](review/pr-review.md) | PR 初轮 AI 审查 |
| [workflow/requirement-structuring.md](workflow/requirement-structuring.md) | 将模糊需求转为结构化输入 |

---

## 新增文件的规则

1. 必须是**反复用过、效果稳定**的任务——一次性或实验性任务不收录
2. 文件格式参考 `templates/prompt-template.md`
3. 提交时说明：为什么创建这个文件，验证了几次
4. 修改时在"版本历史"里记录改了什么、为什么改
