# 我的 AI Coding 时间：Harness Engineering 工程实践

## 摘要

AI coding 的关键变化，不只是模型更强、工具更多，而是工程师的工作对象正在变化。

传统工程里，核心链路是：

```text
人类写代码 -> 机器执行代码
```

AI coding 初期，链路变成：

```text
人类写 prompt -> AI 生成代码 -> 人类修代码 -> 机器执行代码
```

而在 Harness Engineering 里，链路进一步变成：

```text
人类设计约束、上下文、工具和反馈回路 -> 智能体写代码 -> 机器执行并验证代码
```

也就是说，工程师不是退出工程，而是把工程判断编码进系统。过去我们直接写代码，现在我们设计一个让 Agent 能稳定写代码、验证代码、修复代码、复用经验的工程环境。

本文想讨论的不是“哪个 AI coding 工具最好用”，而是：当 AI coding 从个人技巧走向工程实践时，我们需要如何设计 harness。

## 1. 开头：从写代码到设计执行环境

传统软件工程的基本假设是：人类理解需求、设计方案、编写代码，机器负责忠实执行。

AI coding 改变了这个假设。模型开始参与理解、规划、编码、测试、重构，甚至 review。但这并不意味着软件工程变简单了。相反，问题从“如何写出代码”变成了“如何让一个不稳定但强大的智能体，在复杂工程环境里持续产出可靠代码”。

如果把 AI coding 只理解成 prompt 技巧，很容易遇到上限：

- 同样的 prompt，今天好用，明天不好用。
- AI 能写局部代码，但容易破坏系统约束。
- 需求、设计、测试、review 没有沉淀，下次还要从头讲。
- Agent 看不到日志、数据库、测试环境和历史决策，只能猜。

这就是 Harness Engineering 出现的背景。真正决定 AI coding 上限的，不只是模型能力，而是模型外部的工程系统。

## 2. AI Coding 的能力阶段

Every 的 Compound Engineering 文章把 AI coding 能力分成多个阶段。按照我的理解，可以简化为 6 个层级：

### L0：Manual Development

不用 AI，开发者自己查文档、读代码、写代码、调试和测试。

这是过去几十年软件工程的默认模式。它稳定、可控，但在人力和速度上有明显上限。

### L1：Chat-Based Assistance

把 AI 当作问答助手或代码片段生成器。

开发者在 ChatGPT、Claude 或编辑器对话窗口里提问，复制有用的代码，再手动粘贴和修改。这个阶段的 AI 主要提升搜索、解释和样板代码生成效率，但控制权仍完全在人类手里。

### L2：Agentic Tools with Line-by-Line Review

Agent 开始进入代码库，可以读文件、改文件、运行命令。

典型工具包括 Cursor、Claude Code、Codex 等。开发者允许 Agent 直接修改代码，但仍然逐步批准每个动作、逐行 review 每个 diff。

很多人会停在这一层：AI 看起来能干活，但人类仍然在旁边盯着每一步，效率提升有限。

### L3：Plan-First, PR-Only Review

关键变化发生在这一层。

开发者和 AI 先共同产出明确的 plan，包括需求、约束、方案、边界条件、测试方式。然后 Agent 按 plan 独立实现，最后人类只 review PR，而不是盯着每一行生成过程。

从这一层开始，AI coding 不再只是“让 AI 写代码”，而是“让 AI 按可审查的计划完成工程任务”。

### L4：Idea to PR

开发者只给出目标或问题，Agent 负责代码库调研、方案设计、实现、测试、自我 review 和 PR 创建。

人类主要参与三个动作：

- 判断什么值得做。
- 审核 Agent 的计划或 PR。
- 决定是否合并。

### L5：Parallel Cloud Execution

多个 Agent 可以在云端或隔离环境中并行工作。

开发者不再受本地机器和单线程注意力限制，可以同时启动多个任务：一个修 bug，一个写测试，一个更新文档，一个做重构。Agent 甚至可以监控用户反馈、CI 失败、日志异常，并主动提出修复 PR。

这一层的瓶颈不再是“我能不能写完”，而是“我能不能设计足够好的任务、约束和验证系统”。

## 3. 工具不是终点，而是 Harness 的入口

现在流行的 AI coding 工具很多，例如 Cursor、Claude Code、Codex、OpenCode、Kiro。它们表面上是不同产品，底层都在争夺同一个位置：成为 Agent 的工作环境。

### Cursor

Cursor 的优势在于编辑器原生体验。它把 chat、composer、inline edit、codebase context 放进 IDE 里，适合从传统编辑器工作流平滑过渡到 Agent 工作流。

### Claude Code

Claude Code 更强调 agentic loop：Agent 可以理解项目、读取文件、调用工具、运行命令，并在 terminal、IDE、web 等入口中工作。它适合把 AI 放进已有的开发流程里。

### Codex

Codex 强调从 ChatGPT、CLI 和云端任务切入工程场景。它可以读取仓库、执行任务、生成 patch、运行验证，并通过 AGENTS.md 等文件读取项目规则。

### OpenCode

OpenCode 的定位是开源 AI coding agent。它支持 terminal、IDE、desktop 等入口，也支持多模型、多 provider、多 session。它代表了一类更开放、可组合的 Agent 工作环境。

### Kiro

Kiro 更偏 spec-driven development。它强调把 prompt 转化成 requirements、design、tasks，然后再进入实现。它的价值在于把“需求澄清”和“执行计划”显式化。

### 小结

这些工具的差异，不只是 UI 差异，而是 harness 设计差异：

- Agent 能看到什么上下文？
- Agent 能调用什么工具？
- Agent 能否运行测试和验证？
- Agent 如何读项目规则？
- Agent 如何保留和复用经验？
- 人类在哪里介入？

工具本身不是终点。工具只是我们搭建 harness 的入口。

## 4. 范式演进：Prompt Engineering -> Context Engineering -> Harness Engineering

AI coding 的热点经历了几个阶段。

### Prompt Engineering

早期重点是“怎么问”。

我们优化 prompt 模板，加入角色、背景、约束、示例，希望模型一次性生成更好的答案。

Prompt Engineering 解决的是：

```text
我要对 AI 说什么？
```

### Context Engineering

后来大家发现，prompt 再好，如果上下文不对，输出也不会稳定。

于是重点变成如何让 AI 看到正确的信息：代码库、文档、接口定义、历史决策、设计稿、报错日志、测试结果。

Context Engineering 解决的是：

```text
AI 应该看到什么？
```

### Harness Engineering

但只给上下文仍然不够。Agent 不只是回答问题，它要执行任务。执行就需要环境、权限、工具、反馈、验证和纠错机制。

Harness Engineering 解决的是：

```text
AI 如何在一个可控环境里可靠地完成任务？
```

一句话总结：

```text
Prompt 解决“说什么”
Context 解决“看什么”
Harness 解决“怎么可靠地做完”
```

## 5. 什么是 Harness

可以把 Agent 拆成两部分：

```text
Agent = Model + Harness
```

Model 是智能能力，Harness 是执行环境。

Harness 包括但不限于：

- 代码仓库
- AGENTS.md、CLAUDE.md 等入口文档
- specs、plans、design docs
- skills、commands、subagents
- lint、typecheck、unit test、e2e test
- CI、preview environment、deployment pipeline
- 日志、数据库、监控、bug 系统
- 权限、沙箱、worktree、分支策略
- review 流程和质量标准

Harness 的目标不是让模型变聪明，而是让模型在工程系统里变得可控、可验证、可复用。

一个好的 harness 会让 Agent 明确知道：

- 当前任务是什么。
- 哪些规则必须遵守。
- 应该从哪里获取上下文。
- 可以调用哪些工具。
- 如何判断任务完成。
- 失败后如何自我修正。
- 经验应该沉淀到哪里。

## 6. 对前端工程师来说：前端工程化 -> AI 工程化

对前端工程师来说，Harness Engineering 并不陌生。

过去十几年，前端从“写页面”演进到“前端工程化”：

- 使用 TypeScript 约束类型。
- 使用 ESLint 和 Prettier 约束风格。
- 使用 Vite、Webpack、Rollup 管理构建。
- 使用组件库和设计系统管理 UI 一致性。
- 使用 Storybook、Playwright、Vitest 管理验证。
- 使用 CI/CD 管理质量门禁和交付。

这些工程化手段的本质，是把个人经验变成系统约束，让团队可以稳定交付。

AI 工程化也是类似逻辑。

过去我们工程化浏览器、构建链和团队协作；现在我们要工程化 Agent 的执行环境。

对应关系大致如下：

| 前端工程化 | AI 工程化 |
| --- | --- |
| README | AGENTS.md |
| 代码规范 | Agent 指令和 review 规则 |
| ESLint | 机械化约束 |
| TypeScript | 可验证的接口契约 |
| CI | Agent 完成任务的质量门禁 |
| Storybook | Agent 可查看的 UI 状态集合 |
| Playwright | Agent 可执行的端到端验证 |
| 组件库 | Agent 可复用的实现模式 |
| 技术文档 | Agent 可检索的项目记忆 |

所以，对前端工程师来说，Harness Engineering 不是一个全新的概念，而是工程化能力的一次迁移。

## 7. Agent 执行流程框架

一个稳定的 Agent 工作流，通常不是“直接让 AI 开写”，而是一个结构化流程。

我更认可下面这个循环：

```text
clarify -> spec -> plan -> work -> verify -> review -> compound
```

### Clarify：澄清问题

先明确要解决什么问题，不要急着实现。

Agent 很擅长执行，但如果目标错了，它会高效地产出错误结果。

### Spec：沉淀意图

把需求、边界、约束、验收标准写成 spec。

Spec 的价值是把模糊想法变成可审查工件。它既服务人，也服务 Agent。

### Plan：拆解执行路径

Plan 不是形式主义。它决定 Agent 如何读代码、改哪些模块、如何验证、遇到风险怎么处理。

在 AI coding 里，plan 正在变成新的“代码”。

### Work：隔离环境中实现

Agent 应该在可控环境里执行，例如 git branch、git worktree、sandbox、cloud task。

这样可以降低对主工作区的干扰，也方便回滚和 review。

### Verify：机械化验证

只靠人类肉眼 review 不够。

Agent 必须能运行：

- lint
- typecheck
- unit test
- e2e test
- build
- visual regression
- domain-specific checks

验证越机械化，Agent 越能自我修正。

### Review：风险审查

Review 不只是看代码风格，而是看行为变化、边界条件、安全风险、测试缺口和系统一致性。

可以让多个 specialized agents 并行 review，但最终质量判断仍由人类负责。

### Compound：沉淀复利

这是最重要但最容易被忽略的一步。

每次任务完成后，都应该问：

- 这次哪里讲得不清楚？
- 哪条规则应该写进 AGENTS.md？
- 哪个重复流程应该变成 skill？
- 哪个人工检查应该变成 lint 或 CI？
- 哪份文档已经腐烂？

如果一次 AI coding 只产出代码，它的收益是一次性的。如果它还改进了 harness，它的收益会复利增长。

## 8. 我的实践：如何搭建 Harness

### 8.1 采用 Superpowers 工作流：先 spec，再 plan，再执行

我不希望 Agent 一上来就写代码。

对复杂任务，我会要求它先理解上下文，再形成 spec，然后写 plan，最后执行。这样做的好处是，错误更早暴露在文本层，而不是代码层。

修正文档比修正代码便宜。修正 plan 比修正 PR 便宜。

### 8.2 先写 Skill 再执行：先外化，再复用

当我发现某类任务会反复出现时，我倾向于先写 skill。

Skill 的价值不是“多一份文档”，而是把一次性的经验变成 Agent 下次可以自动调用的能力。

例如：

- 如何做代码 review。
- 如何排查前端视觉问题。
- 如何生成设计稿。
- 如何处理特定仓库的发布流程。
- 如何查询测试环境日志。

这其实是在把人的隐性经验外化成 Agent 可执行的流程。

### 8.3 渐进式披露：AGENTS.md 做目录页

我不赞成把所有规则都塞进一个巨大的 AGENTS.md。

大文件会带来三个问题：

- 挤占上下文。
- 难以维护。
- 难以验证。

更好的方式是把 AGENTS.md 当成地图，而不是百科全书。

它应该告诉 Agent：

- 当前项目的核心原则是什么。
- 常用命令在哪里。
- 不同任务应该读哪些文档。
- 更深层的规范在哪里。

这样 Agent 可以按需读取上下文，而不是一开始就吞下全部信息。

### 8.4 Lint 和 CI：把偏好变成机械约束

文档会腐烂，口头约定会被忘记。

如果某条规则真的重要，就应该尽量变成机械化检查。

例如：

- import 边界必须由 lint 约束。
- 目录分层必须由结构测试约束。
- 类型错误必须由 CI 阻断。
- UI 关键路径必须有 e2e 测试。
- 文档链接和代码示例应该定期检查。

对 Agent 来说，最好的反馈不是“你写得不对”，而是一个明确、可执行、带修复建议的错误信息。

### 8.5 Doc Garden：治理文档熵

AI 会复现仓库里已有的模式，包括坏模式。

如果文档过时，Agent 会照着过时文档继续生成错误代码。如果坏代码成为仓库里的主流模式，Agent 会把坏模式当成正确模式。

所以文档和代码一样需要治理。

我倾向于把文档当成 garden：

- 定期扫描腐烂文档。
- 检查断链、过期命令、失效截图。
- 对重复、冲突、过时的文档发起重构 PR。
- 把稳定经验升级成 rules、skills 或 lint。

这不是额外负担，而是 AI coding 的基础设施维护。

### 8.6 环境对等：AI 能看到的环境 = 人能看到的环境

如果人类排查问题时可以看日志、查数据库、访问测试环境、看监控、读 bug 系统，那么 Agent 也应该以受控方式具备这些能力。

否则 Agent 只能靠猜。

环境对等包括：

- Agent 能查询测试环境日志。
- Agent 能读取 CI 失败原因。
- Agent 能访问相关 issue、bug、用户反馈。
- Agent 能查看截图或录屏。
- Agent 能运行本地或远程测试。
- Agent 能在隔离环境里复现问题。

目标不是无限授权，而是以最小权限提供足够上下文，让 Agent 可以完成闭环。

### 8.7 出错时，先修 Harness

当 Agent 出错时，第一反应不应该是“这个模型不行”。

更有价值的问题是：

- 它缺了什么上下文？
- 它缺了什么工具？
- 它是否没有明确验收标准？
- 它是否看到了过时文档？
- 它是否没有办法运行验证？
- 它是否缺少可复用 skill？
- 这类错误能不能变成 lint、CI 或 review agent？

这就是 Harness Engineering 的核心心智：不是要求 Agent 每次都更努力，而是让系统每次都更可靠。

## 9. 常见误区与边界

### 误区一：Harness Engineering 等于不写代码

不是。

Harness Engineering 不是放弃代码能力，而是把代码能力上移到系统设计、约束设计、验证设计和质量判断。

不懂代码的人很难设计好 harness。

### 误区二：Harness Engineering 等于写更多 prompt

不是。

Prompt 只是 harness 的一个很小部分。真正重要的是上下文、工具、验证、权限、流程和沉淀机制。

### 误区三：Agent 能跑就等于可用

不一定。

Agent 能生成代码，不代表它能稳定交付。没有测试、CI、review 和环境上下文，AI coding 很容易变成更快地产生技术债。

### 误区四：完全自动化就是目标

也不是。

很多判断仍然需要人类掌舵：

- 什么问题值得解决。
- 哪个方案符合产品方向。
- 哪些风险可以接受。
- 质量标准是否达标。
- 用户体验是否正确。

Agent 可以执行，但方向仍然需要人来定。

## 10. 结尾：工程师的新职责

过去，优秀工程师写出好代码。

现在，优秀工程师要设计出能持续产出好代码的系统。

这不是工程能力的退化，而是工程能力的上移。

我的 AI coding 时间，不是从写代码变成不写代码，而是从写代码，变成设计一个可靠写代码的工程系统。

Harness Engineering 的核心不是让人类消失，而是让人类的判断、经验和 taste 被系统记住、执行和复用。

## 可继续扩写的几个方向

- 加入一次真实任务案例：从需求到 spec、plan、implementation、review、compound。
- 展示一个 AGENTS.md 的目录页示例。
- 展示一个 skill 的结构示例。
- 展示一次“Agent 出错 -> 修 harness”的复盘。
- 补充前端场景：设计稿还原、组件库演进、视觉回归、线上 bug 排查。

## 参考资料

- [Every: Compound Engineering](https://every.to/guides/compound-engineering)
- [Harness Engineering 概念总览](https://github.com/deusyu/harness-engineering/blob/main/concepts/00-overview.md)
- [Cursor](https://cursor.com/)
- [Claude Code](https://claude.com/product/claude-code)
- [OpenAI Codex](https://openai.com/index/introducing-codex/)
- [OpenCode](https://opencode.ai/)
- [Kiro](https://kiro.dev/)
