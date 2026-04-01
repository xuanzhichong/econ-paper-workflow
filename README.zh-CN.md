# Econ Scholar Workflow for Codex

这是一个面向 `实证微观 / 政策评估` 的 Codex 工作流增强层，主要服务于：

- 实证微观经济学
- 政策评估
- `Stata + R`
- 论文写作、投稿前 QA（质量审查）、`R&R` 回复

这个仓库不是独立程序，而是一套可并入 Codex 的工作流配置包，主要包括：

- `AGENTS.md`：项目级路由和工作流规则
- `agents/`：专门 agent 的提示词
- `skills/`：可复用工作流说明
- `config.example.toml`：Codex 配置示例
- `quality_reports/`：QA 报告模板和输出目录

这套工作流是在下面两个仓库基础上继续改造的：

- `Galaxy-Dawn/claude-scholar`
- `pedrohcgs/claude-code-my-workflow`

本仓库采用 MIT 许可，也欢迎大家 fork 后按自己的研究流程继续调整。

## 目录

- [这套工作流默认怎么理解你的任务](#这套工作流默认怎么理解你的任务)
- [推荐使用步骤](#推荐使用步骤)
- [前置条件](#前置条件)
- [快速开始](#快速开始)
- [可用工作流](#可用工作流)
- [第二轮 QA 系统](#第二轮-qa-系统)
- [实用提示词](#实用提示词)
- [仓库结构](#仓库结构)
- [当前范围](#当前范围)

## 推荐使用步骤

如果你想把这套仓库接到自己的工作流里，建议按下面的顺序使用：

1. 先阅读 `AGENTS.md` 和本 README，确认它和你的研究方式一致。
2. 把 `config.example.toml` 里的相关片段合并到真实的 `~/.codex/config.toml`。
3. 将 `AGENTS.md`、`agents/` 和 `skills/` 同步到你的 Codex 环境。
4. 如果需要文献导入、collection 管理和 PDF 获取，再配置 Zotero MCP。
5. 在你的研究项目根目录启动 Codex，确保它会读取项目级 `AGENTS.md`。
6. 根据你当前任务所在阶段进入对应 workflow：构思、数据审计、论文写作、质量审查或 `R&R`。
7. 如果你的领域或流程不同，直接 fork 本仓库后修改 prompts、skills 和 references。

## 前置条件

把这套工作流并入 Codex 之前，建议先准备好：

- [Codex CLI](https://github.com/openai/codex)
- Git
- 可选：Python 和 `uv`
- 可选：Zotero Desktop 与 `zotero-mcp`，用于文献管理

## 这套工作流默认怎么理解你的任务

在这个仓库里，Codex 默认会按经济学实证语境理解你的请求：

- “结果”默认是回归表，不是 benchmark leaderboard
- “实验”默认是实证设计，不是模型训练
- “论文”默认是经济学论文结构，不是 AI conference 结构
- “审稿回复”默认是期刊 `R&R`，不是 conference rebuttal

默认栈是：

- 文献：`Google Scholar`、`RePEc`、`IDEAS`、`NBER`、`AEA journals`
- 分析：以 `Stata` 为主，`Python` 用于辅助任务
- 产物：`literature-review.md`、`analysis-plan.md`、`regression-spec-matrix.md`、`response-letter.md`

## 快速开始

### 1. 把这个仓库当成精简公开包

这不是一个“直接运行”的仓库，而是用来并入你自己的 Codex 环境。

这个公开包只保留默认启用的经济学层。

优先同步这些内容：

- `AGENTS.md`：项目级路由和行为约束
- `config.example.toml`：agent、feature、MCP 的配置示例
- `agents/`：专门 agent 的系统提示
- `skills/`：本地 workflow 说明

### 2. 配置 Codex

把 `config.example.toml` 当成合并时的参考模板：

- 开启 `multi_agent`
- 开启 `memories`
- 开启 `skill_approval`
- 注册经济学相关 agents
- 启用 Zotero MCP

注意：

- 当前仓库里的 `config.example.toml` 仍然保留了 model/provider 的占位符
- 你应当把研究工作流相关片段合并到真实的 `~/.codex/config.toml`
- 不要把 `your-api-key` 这类占位符原样放进正式配置
- 把 `AGENTS.md`、`agents/` 和 `skills/` 同步到你实际使用的 Codex 环境

### 3. 配置 Zotero MCP

如果你希望使用文献导入、collection 管理和 PDF 获取能力，就需要配置 Zotero MCP。

至少先把下面这段 Zotero MCP 配置合并到真实的 `~/.codex/config.toml`：

```toml
[mcp_servers.zotero]
command = "zotero-mcp"
args = ["serve"]
enabled = true

[mcp_servers.zotero.env]
ZOTERO_API_KEY = "your-api-key"
ZOTERO_LIBRARY_ID = "your-library-id"
ZOTERO_LIBRARY_TYPE = "user"
UNPAYWALL_EMAIL = "you@example.com"
```

这段配置是本仓库文献工作流能够运行起来的最小 MCP 前提。

然后再按下面的文档补完整的 Zotero MCP 安装、凭据和本地 Zotero 连接配置：

参考：

- [MCP_SETUP.md](MCP_SETUP.md)
- [MCP_SETUP.zh-CN.md](MCP_SETUP.zh-CN.md)

### 4. 在项目根目录启动 Codex

这样 Codex 才会自动读取项目级 `AGENTS.md`。

建议第一次会话直接这样说：

```text
读取 AGENTS.md，把这个仓库当成经济学实证工作流。我现在在做 [topic]，请根据当前阶段帮我进入正确 workflow。
```

## 可用工作流

### 阶段 1：研究构思与文献综述

使用：

- `research-ideation`
- `literature-reviewer`

输出：

- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `research-design.md`

适合：

- 收窄研究问题
- 梳理识别策略
- 判断文献是否已经饱和
- 评估数据是否可得

### 阶段 2：数据审计与分析规划

使用：

- `results-analysis`
- `data-analyst`

输入：

- `.dta`
- `.do`
- `.log`
- `.csv`
- `.xlsx`
- 回归表 `.tex`

输出：

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`

适合：

- 还原 do-file 执行顺序
- 记录样本构造
- 规划主回归
- 设计稳健性和附录表

### 阶段 3：论文写作

使用：

- `paper-writing`
- `paper-miner`

默认结构：

1. `Introduction`
2. `Institutional background / context`
3. `Data`
4. `Empirical strategy / identification`
5. `Main results`
6. `Mechanisms / heterogeneity`
7. `Robustness`
8. `Conclusion`
9. `Appendix`

经济学模板入口：

- `skills/paper-writing/templates/econ/README.md`

### 阶段 4：投稿前 QA

使用：

- `paper-self-review`：静态自审
- `qa-paper`：严格 critic/fixer/verifier 闭环

当你需要这些能力时，优先用 `qa-paper`：

- 明确的 go / no-go 判断
- 打分
- 多轮 review-fix
- 提交前 hard gates

### 阶段 5：R&R 与审稿回复

使用：

- `review-response`
- `rebuttal-writer`
- `qa-response`

默认输出：

- `response-letter.md`
- `comment-to-change-map.md`

## 第二轮 QA（质量审查）系统

这个仓库集成了一套按当前 Codex 仓库结构改造的 `critic/fixer` 工作流。

### Agents

- `paper-critic`
- `paper-fixer`
- `response-critic`
- `response-fixer`
- `artifact-verifier`

### Skills

- `qa-paper`
- `qa-response`

### 循环

```text
pre-flight -> critic -> fixer -> verifier -> 必要时继续 -> APPROVED 或最多 5 轮
```

### 阈值

- `80` = commit-ready
- `90` = submission-ready
- `95` = excellence

### Hard Gates

论文：

- 识别逻辑错误
- 关键文字与表格不一致
- 引用不可核验或失真
- 缺少基本复现说明

Response：

- 漏回关键 referee 意见
- 承诺修改但无法追踪
- response 与 change map 不一致
- 语气明显回避或误导

报告会写入以下目录：

- `quality_reports/papers/`
- `quality_reports/responses/`
- `quality_reports/verifier/`

## 实用提示词

### 从文献综述开始

```text
我想研究 [topic]。请使用经济学实证工作流，先帮我做文献地图、识别策略梳理和可用数据评估。
```

### 审计一个 Stata 项目

```text
我有一套 do-file 和 dta。请还原数据流程、识别 estimation sample，并生成 regression-spec matrix。
```

### 写 Main Results

```text
请根据这些回归结果，用 economics journal 风格起草 Main Results 和 Empirical Strategy。
```

### 跑严格论文 QA

```text
对这个 draft 运行 qa-paper。我需要 hard gates、打分和明确的 submission-readiness 结论。
```

### 写并审查 R&R 回复

```text
先用 review-response 起草 response letter，再用 qa-response 做最终 QA。
```

## 仓库结构

- `AGENTS.md`：项目级路由和质量规则
- `config.example.toml`：Codex 配置示例
- `LICENSE`：本工作流包采用的 MIT 许可证
- `agents/`：专门 reviewer / worker 提示词
- `skills/`：工作流说明和参考资料
- `quality_reports/`：QA 报告目录和模板

## 当前范围

当前覆盖得比较好的部分：

- 实证微观
- 政策评估
- `Stata + Python`
- 论文和 `R&R` 的 QA 闭环

当前还没有做深的部分：

- 复现包的深度审计
- 数据清理 QA 的独立 critic/fixer
- 理论经济学工作流
