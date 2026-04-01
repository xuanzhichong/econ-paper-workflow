# Econ Scholar Workflow for Codex

语言：中文 | [English](README.md)

一个面向 Codex 的实证经济学工作流层，适用于：

- 实证微观经济学
- 政策评估
- `Stata + R`
- 论文撰写、投稿前 QA（质量审查）以及 `R&R` 回复工作

这个仓库不是一个可独立运行的应用程序，而是一个围绕以下组件构建的工作流包：

- `AGENTS.md` 中的路由规则
- `agents/` 中的 agent prompts
- `skills/` 中的技能说明
- `config.example.toml` 中的配置示例
- `quality_reports/` 中的报告模板

该工作流构建于以下项目之上：

- `Galaxy-Dawn/claude-scholar`
- `pedrohcgs/claude-code-my-workflow`

本仓库基于 MIT License 发布。若对你有用，你可以 fork 后按自己的研究领域和工作习惯进行调整。

## 目录

- [本工作流的默认假设](#本工作流的默认假设)
- [推荐配置路径](#推荐配置路径)
- [前置条件](#前置条件)
- [快速开始](#快速开始)
- [工作流结构](#工作流结构)
- [第二轮 QA 系统](#第二轮-qa-系统)
- [实用提示词](#实用提示词)
- [仓库结构](#仓库结构)
- [当前覆盖范围](#当前覆盖范围)

## 推荐配置路径

如果你想把这个仓库整合进你自己的 Codex 环境，建议按以下顺序操作：

1. 阅读 `AGENTS.md` 和本 README，确认该工作流与你的研究风格匹配。
2. 将 `config.example.toml` 中相关部分合并到你真实的 `~/.codex/config.toml`。
3. 将 `AGENTS.md`、`agents/` 和 `skills/` 复制或同步到你的 Codex 环境中。
4. 如果你需要文献导入、文献库管理或 PDF 附件支持，配置 Zotero MCP。
5. 在 Codex 中打开你的研究项目，使其加载项目级别的 `AGENTS.md`。
6. 从与你当前任务对应的工作流阶段开始：选题构思、数据审计、论文撰写、质量审查，或 `R&R`。
7. Fork 本仓库，并根据自己的领域与工作流需要修改 prompts、skills 与参考材料。

## 前置条件

在将本工作流合并进 Codex 之前，请确认你已具备：

- [Codex CLI](https://github.com/openai/codex)
- Git
- 可选：Zotero Desktop 与 `zotero-mcp`（用于文献管理）

## 本工作流的默认假设

在这个仓库中，Codex 默认会将你的请求理解为**实证经济学语境**下的任务：

- “results” 指的是回归结果表，而不是 benchmark leaderboard
- “experiment” 指的是经验研究设计，而不是模型训练实验
- “paper” 指的是经济学论文结构，而不是 AI 会议论文结构
- “review response” 指的是期刊 `R&R` 回复，而不是会议 rebuttal

默认技术栈如下：

- 文献：`Google Scholar`、`RePEc`、`IDEAS`、`NBER`、`AEA journals`
- 分析：`Stata` 为主工具
- 作图：`R` 为主工具
- 输出：`literature-review.md`、`analysis-plan.md`、`regression-spec-matrix.md`、`response-letter.md`

## 快速开始

### 1. 将本仓库视为一个经过整理的公共覆写层

这个仓库的设计目的，是合并进你的 Codex 配置中，而不是单独运行。

这个公开包只包含默认的实证经济学工作流层。

首先将以下文件同步到 Codex：

- `AGENTS.md`：项目级别的路由规则与工作流规范
- `config.example.toml`：agent 和 MCP 的注册示例
- `agents/`：专用 agent prompts
- `skills/`：可复用的工作流说明

### 2. 配置 Codex

将 `config.example.toml` 作为参考进行合并，主要包括：

- 启用 `multi_agent`
- 启用 `memories`
- 启用 `skill_approval`
- 注册经济学专用 agents
- 启用 Zotero MCP

重要说明：

- 仓库中的 `config.example.toml` 含有 model/provider 的模板占位符
- 你应将研究工作流相关部分合并到真实的 `~/.codex/config.toml`
- 不要直接复制诸如 `your-api-key` 这样的占位符值
- 请将 `AGENTS.md`、`agents/` 和 `skills/` 复制到你**实际使用**的 Codex 环境中

### 3. 配置 Zotero MCP

如果你需要文献导入、文献库管理和 PDF 附件支持，请配置 Zotero MCP。

至少需要将下面这段 Zotero MCP 配置加入到你真实的 `~/.codex/config.toml` 中：

    [mcp_servers.zotero]
    command = "zotero-mcp"
    args = ["serve"]
    enabled = true

    [mcp_servers.zotero.env]
    ZOTERO_API_KEY = "your-api-key"
    ZOTERO_LIBRARY_ID = "your-library-id"
    ZOTERO_LIBRARY_TYPE = "user"
    UNPAYWALL_EMAIL = "you@example.com"

这是本仓库中文献工作流所需的最低 MCP 配置。

随后，请按照以下文档完成完整的 Zotero MCP 设置，包括安装、凭证配置以及本地 Zotero 连接：

参见：

- [MCP_SETUP.md](MCP_SETUP.md)
- [MCP_SETUP.zh-CN.md](MCP_SETUP.zh-CN.md)

### 4. 在项目根目录启动会话

请从项目根目录打开 Codex，以便其加载 `AGENTS.md`。

建议的第一条 prompt：

    Read AGENTS.md and treat this repository as an empirical economics workflow. I am working on [topic]. Help me set up the workflow and start from the right stage.

## 工作流结构

### Stage 1. 研究选题与构思

使用：

- `research-ideation`
- `literature-reviewer`

输出：

- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `research-design.md`

适用于：

- 打磨研究问题
- 梳理识别策略
- 检查文献是否已经饱和
- 判断数据是否可行

### Stage 2. 数据审计与分析规划

使用：

- `results-analysis`
- `data-analyst`

输入：

- `.dta`
- `.do`
- `.log`
- `.csv`
- `.xlsx`
- 回归结果 `.tex` 表格

输出：

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`

适用于：

- 重建 do-file 执行顺序
- 记录样本构造过程
- 规划基准回归
- 设计稳健性检验与附录表格

### Stage 3. 论文图表

使用：

- `paper-figures`

输入：

- 从 `Stata` 导出的、已处理好的 `.dta` 文件
- 已整理或已聚合、可直接用于绘图的数据集
- 图形草图或截图
- 已有的 `R` 绘图代码

输出：

- 用 `R` 生成的投稿级图表
- `figure-plan.md`
- `figure-spec-sheet.md`
- `figure-caption-sheet.md`

适用于：

- 描述性图表
- 发展趋势图
- 结构或构成图
- 地图类图表
- 多面板论文图
- 将图表修订为 Nature / Nature 子刊风格

### Stage 4. 论文撰写

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

### Stage 5. 投稿前 QA

使用：

- `paper-self-review` 进行静态审查
- `qa-paper` 进行严格的 critic/fixer/verifier 循环

当你需要以下内容时，默认使用 `qa-paper`：

- go / no-go 决策
- 评分
- 多轮 review-fix 循环
- 在给导师或投稿前进行硬门槛检查

### Stage 6. R&R 与回复信

使用：

- `review-response`
- `response-writer`
- 最终 QA 使用 `qa-response`

默认输出：

- `response-letter.md`
- `comment-to-change-map.md`

## 第二轮 QA 系统

本仓库包含一个适配当前 Codex 仓库结构的 `critic/fixer` 工作流。

### Agents

- `paper-critic`
- `paper-fixer`
- `response-critic`
- `response-fixer`
- `artifact-verifier`

### Skills

- `qa-paper`
- `qa-response`

### 循环流程

    pre-flight -> critic -> fixer -> verifier -> repeat if needed -> APPROVED or max 5 rounds

### 分数阈值

- `80` = 可提交到版本库（commit-ready）
- `90` = 可投稿（submission-ready）
- `95` = 卓越水平（excellence）

### 硬门槛

论文：

- 识别策略失败
- 正文与表格不一致
- 引文不可核验
- 缺少 replication note

回复信：

- 缺少关键审稿意见回复
- 承诺修改无法追踪
- 回复信与 change-map 不一致
- 语气存在实质性回避

报告输出目录：

- `quality_reports/papers/`
- `quality_reports/responses/`
- `quality_reports/verifier/`

## 实用提示词

### 开始文献综述

    I want to study [topic]. Use the empirical economics workflow. Start with literature mapping, identification strategies, and feasible data sources.

### 审计一个 Stata 项目

    I have a set of do-files and dta files. Reconstruct the data pipeline, identify the estimation sample, and produce a regression-spec matrix.

### 起草结果部分文字

    Use these regression results to draft the Main Results and Empirical Strategy sections in economics-journal style.

### 用 R 生成论文图表

    I have a Stata-processed dta file. Use the paper-figures workflow to help me build a publication-ready descriptive figure in R.

### 运行严格的论文 QA

    Run qa-paper on this draft. I want hard gates, a score, and a clear submission-readiness verdict.

### 起草并 QA 一封 R&R 回复信

    Use review-response to draft the letter, then run qa-response before finalizing it.

## 仓库结构

- `AGENTS.md`：项目级路由与质量规则
- `config.example.toml`：Codex 配置增补示例
- `LICENSE`：本工作流包的 MIT 许可证
- `agents/`：专用 reviewer 与 worker prompts
- `skills/`：工作流说明与参考材料
- `quality_reports/`：QA 输出与报告模板

## 当前覆盖范围

目前覆盖较好：

- 实证微观经济学
- 政策评估
- `Stata + R`
- 使用 `R` 完成描述性与投稿级图表工作流
- 论文与 `R&R` QA 循环

尚未深度覆盖：

- 完整 replication package 审计
- 面向数据清洗的专门 critic/fixer
- 理论经济学工作流
