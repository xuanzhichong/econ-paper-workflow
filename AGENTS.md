# Econ Scholar Workflow

## 项目定位

本项目是一个面向 `实证微观 / 政策评估` 的 Codex Scholar 覆写层。

- 默认研究范式：经济学实证研究，不是 ML/AI benchmark research
- 默认工具栈：`Stata + Python`
- 默认语言：中文，保留 `Stata`、`DID`、`IV`、`RDD`、`event study`、`JEL` 等术语
- 默认输出：研究设计、文献综述、Stata workflow、回归规格、论文段落、`R&R response`

## 路由规则

当用户提到以下内容时，优先走经济学实证工作流：

- `Stata`、`do-file`、`reghdfe`、`ivreg2`、`esttab`、`outreg2`
- `DID`、`event study`、`RDD`、`IV`、`matching`
- `回归表`、`稳健性`、`异质性`、`机制分析`、`placebo`、`balance table`
- `识别策略`、`制度背景`、`变量构造`、`附录表`、`复现包`
- `referee report`、`R&R`、`response letter`

当用户说“实验”“结果”“论文”“审稿意见”时，默认理解为经济学实证语境，除非用户明确说明是 ML 训练、benchmark、TensorBoard 或 AI conference。

## 不采用的默认假设

除非用户明确要求，否则不要默认：

- 研究对象是 `NeurIPS`、`ICML`、`ICLR`、`ACL` 这类 AI conference
- 数据分析输入是 `TensorBoard`、训练曲线、benchmark leaderboard
- “实验”指模型训练、ablation、SOTA comparison
- 论文结构必须是 ML conference 风格

如果用户真的提供了 ML 工程上下文，再切回对应 skill；否则保持经济学实证路径。

## 优先使用的 Skills 与 Agents

优先技能：

- `research-ideation`：研究问题、识别策略、数据来源、文献综述
- `results-analysis`：Stata-first 数据处理、主回归、稳健性、表图输出
- `ml-paper-writing`：经济学实证论文写作
- `paper-self-review`：投稿前自审；严格审查或定稿前检查时转入 `qa-paper`
- `review-response`：期刊 `referee response / R&R`；定稿审查时转入 `qa-response`
- `qa-paper`：论文 critic/fixer/verifier 多轮质量闭环
- `qa-response`：response letter critic/fixer/verifier 多轮质量闭环
- `citation-verification`：核验引用，不编造文献

优先代理：

- `literature-reviewer`：经济学文献综述
- `data-analyst`：Stata-first 实证分析
- `paper-miner`：提取经济学论文写作模式
- `rebuttal-writer`：`R&R response`
- `paper-critic`：只读论文批判审查
- `paper-fixer`：按 critic 问题单修稿
- `response-critic`：只读 response letter 审查
- `response-fixer`：按 critic 问题单修 response
- `artifact-verifier`：质量门、轮次状态、剩余风险终审

## 核心工作流

默认工作流：

1. 明确研究问题与政策含义
2. 梳理经典文献、近年工作与识别策略
3. 评估数据可得性、样本构造与变量定义
4. 设计主规格、识别假设与标准误方案
5. 规划稳健性、异质性、机制与附录表
6. 将结果写成经济学论文结构
7. 准备复现包与 `response letter`

严格质量控制场景追加 contractor-style loop：

1. implement
2. verify
3. review
4. fix
5. re-verify
6. score

`critic/fixer` 子循环最多 5 轮。通过条件由 `artifact-verifier` 判断；达到 `APPROVED` 才结束，否则输出 `remaining blockers`。

## 质量门

沿用统一阈值风格：

- `80` = commit-ready
- `90` = internal-share / submission-ready
- `95` = excellence

论文 hard gates：

- 识别逻辑存在明显错误
- 关键表述与表格/附录不一致
- 引用失真或无法核验
- 缺少基本复现说明

Response hard gates：

- 漏回关键意见
- 承诺了未落实的修改
- 回信与正文修改位置对不上
- 语气失衡或回避核心问题

## 输出习惯

优先生成这些文件或内容：

- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`
- `response-letter.md`
- `comment-to-change-map.md`
- `quality_reports/papers/*.md`
- `quality_reports/responses/*.md`
- `quality_reports/verifier/*.md`

## 复现与安全

- 不覆盖原始数据；清洗后的中间数据与最终分析数据要分层管理
- 优先写明确的 `do-file` 执行顺序和日志方案
- 说明样本筛选、merge、变量构造、缺失值处理、winsorization 规则
- 不编造引用、数据来源、期刊要求、统计结果或政策背景
- 不把 API key、账号、私有数据路径写进提交文件

## 写作与审稿

- 论文默认结构：`Introduction` → `Institutional background / context` → `Data` → `Empirical strategy / identification` → `Main results` → `Mechanisms / heterogeneity` → `Robustness` → `Conclusion` → `Appendix`
- 结果表述要克制，避免把相关性包装成识别结论
- `review-response` 默认是期刊审稿回复，不是 conference rebuttal
- 回复审稿意见时，优先给出：回应立场、具体修改、修改位置、未采纳理由、附录补充
