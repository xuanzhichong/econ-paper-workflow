# 实证结果分析报告示例

**项目**: Broadband Rollout and Local Labor Market Adjustment  
**研究类型**: Empirical Economics / Policy Evaluation  
**分析目的**: 为论文 `Main Results`、`Robustness`、`Mechanism` 和附录部分提供结果解读框架  
**分析人员**: Research Team

---

## 执行摘要

本报告基于 municipality-year panel 数据，分析 broadband rollout 对小型 municipalities 劳动力市场调整的影响。基准结果显示，broadband rollout 与本地就业率上升和失业率下降显著相关，且 effect 在 rollout 后第 2–3 年更为明显。事件研究图未显示明显的 pre-trend，支持基准 DID 识别的可接受性。稳健性分析表明，结果对 alternative treatment definitions、sample restrictions 和 controls 设定总体稳健。异质性结果显示，effects 在 baseline labor market thinner、digitally lagging 的 municipalities 中更强。机制分析表明，broadband 可能主要通过 job matching efficiency 和 firm entry 两个渠道发挥作用，但这些机制结果应视为支持性证据，而非额外独立识别。

**当前结论**:  
结果初步支持论文的核心论点，但正文写作时应将重点放在：

1. 识别逻辑与 event-study 证据  
2. 基准结果的经济含义  
3. 稳健性如何回应具体识别威胁  
4. 机制与异质性证据的克制表述

---

## 1. 识别与样本概览

### 1.1 研究问题

本研究关注：broadband rollout 是否改善小型 municipalities 的 labor market adjustment，以及这一影响通过何种 margin 发生。

### 1.2 基准识别设计

基准设计采用 staggered rollout DID / event study 框架，利用不同 municipalities broadband rollout timing 的差异识别 treatment effect。

### 1.3 估计样本

- **单位**: municipality-year
- **时间范围**: 视数据可用性而定的多年面板
- **处理组**: 已发生 broadband rollout 的 municipalities
- **对照组**: 尚未 rollout 的 municipalities
- **核心 outcomes**:
  - employment rate
  - unemployment rate
  - job-finding or labor reallocation indicators
  - firm entry (如可得)

### 1.4 主要识别威胁

- rollout timing 与 municipalities 既有增长趋势相关
- rollout 受地方财政能力或政治优先级影响
- geographic feasibility 既影响 rollout，也影响 labor market outcomes
- 邻近 treated municipalities 可能带来 spillover

---

## 2. 主结果摘要

### 2.1 基准回归结果

**主结果 1**: broadband rollout 与就业率改善显著相关。  
在包含 municipality fixed effects 和 year fixed effects 的基准规格下，treatment coefficient 为正，表明 rollout 后 treated municipalities 的 employment rate 相对对照组上升。

**主结果 2**: broadband rollout 与失业率下降相关。  
对应的 unemployment outcome 显示负向系数，方向与理论预期一致。

### 2.2 结果解读原则

写作时应明确：

- 哪一张表承载主结果
- 系数的单位和经济含义
- 该 effect 是 level change、percentage-point change 还是 log-point change
- controls 和 FE 加入后估计是否稳定
- 是否存在 adjusted sample 变化

### 2.3 建议的正文表达

> Table 2 reports the baseline DID estimates of broadband rollout on local labor market outcomes. Across specifications, broadband rollout is associated with an increase in the local employment rate and a decline in unemployment. The estimated coefficients remain stable after adding municipality and year fixed effects, time-varying municipal controls, and alternative clustering choices, suggesting that the baseline relationship is not driven by a narrow specification choice alone.

---

## 3. 识别有效性与动态结果

### 3.1 Event-study 结果

**主结果 3**: pre-treatment coefficients 整体接近零，未见系统性 pre-trend。  
这为 parallel-trends-type assumption 提供了支持，但应避免过度表述为“完全证明外生性”。

### 3.2 动态效应

- rollout 当年 effect 可能有限
- rollout 后 1–3 年效果逐步增强
- medium-run effects 强于 immediate effects，说明 broadband 影响可能通过 gradual adjustment 实现

### 3.3 建议的正文表达

> Figure 2 presents the event-study estimates around broadband rollout. The pre-treatment coefficients are generally small and statistically imprecise, providing no strong evidence of differential pre-trends before rollout. Post-treatment coefficients become more positive over time, suggesting that the labor market effects of broadband expansion emerge gradually rather than immediately.

---

## 4. 稳健性分析

### 4.1 稳健性检查应回应的识别威胁

稳健性部分不应机械堆砌，而应围绕下列风险展开：

- selective rollout timing
- treatment mismeasurement
- sample composition changes
- omitted time-varying local shocks
- spillover or boundary contamination

### 4.2 建议的稳健性模块

可包括：

- alternative treatment definitions
- excluding early adopters or policy-prioritized municipalities
- adding pre-period municipal trends where defensible
- placebo timing tests
- alternative clustering levels
- sample restrictions excluding potentially contaminated neighboring municipalities

### 4.3 结果解读

若主结果在这些规格下方向一致、数量级相近，应表述为：

- supports the robustness of the main findings
- reduces concern that the main result is driven by a narrow specification choice

而不是表述为：

- definitively proves causality

### 4.4 建议的正文表达

> The robustness checks in Table 3 and Appendix Tables A2–A5 show that the main estimates remain directionally stable across alternative treatment definitions, sample restrictions, and control sets. These exercises reduce the concern that the baseline findings are driven by a specific coding choice or a small set of municipalities, although they cannot eliminate all concerns about selective rollout timing.

---

## 5. 异质性分析

### 5.1 理论动机

异质性分析应服务于主问题，而不是无差别分组。  
本项目较有解释力的分组包括：

- baseline labor market thickness
- baseline digital infrastructure level
- municipality size
- sector composition
- fiscal capacity

### 5.2 预期模式

若 broadband 真正改善 local adjustment，则 effect 可能在：

- baseline digital access 更弱地区
- labor market thinner 地区
- 更依赖信息摩擦缓解的地区

中更明显。

### 5.3 写作提醒

异质性结果应写成：

- consistent with the idea that...
- suggests stronger effects in...

而不要写成：

- proves that the mechanism is...

---

## 6. 机制分析

### 6.1 可行机制

较自然的机制包括：

- improved job search efficiency
- remote work opportunities
- local firm entry
- worker reallocation across sectors or places

### 6.2 写作纪律

机制结果属于支持性证据。  
除非有额外识别，否则不应将其写成独立因果结论。

### 6.3 建议的正文表达

> The mechanism evidence is consistent with the interpretation that broadband rollout improves labor market adjustment partly by facilitating job matching and supporting local firm formation. However, these results should be interpreted as suggestive rather than definitive mechanism proof, because the mechanism outcomes are not separately identified from the main policy shock.

---

## 7. 表格与图形组织建议

### 7.1 主文表格

**Table 1. Summary Statistics**  
- sample definition
- treated vs control descriptive comparison
- key outcomes and controls

**Table 2. Baseline DID Results**  
- one outcome per column or one closely related outcome family per column
- `Controls`, `FE`, `Clustered SE` 用 `Yes/No` 披露

**Table 3. Robustness Checks**  
- alternative treatment definitions
- sample restrictions
- clustering / controls sensitivity

**Table 4. Heterogeneity Analysis**  
- theory-motivated subgroup estimates

**Table 5. Mechanism Results**  
- supporting outcomes only

### 7.2 主文图形

**Figure 1. Rollout Timing Distribution or Treatment Map**  
- 展示 treatment timing variation

**Figure 2. Event-study Plot**  
- 显示 pre-trend 和 post-treatment dynamics

**Figure 3. Heterogeneity Coefficient Plot**  
- 展示 subgroup effects

### 7.3 附录建议

- alternative samples
- placebo timing tests
- extra event-study specifications
- variable construction details
- additional institutional background
- replication or data-access notes

---

## 8. Results 部分写作模板

### 8.1 主结果段落模板

> Table 2 reports the baseline estimates of broadband rollout on local labor market outcomes. Across specifications, the coefficient on rollout is positive for employment and negative for unemployment, indicating that treated municipalities experience more favorable labor market adjustment after rollout. The magnitude remains stable after adding municipality and year fixed effects as well as time-varying controls, suggesting that the baseline pattern is not driven by a narrow set of specification choices.

### 8.2 动态结果段落模板

> Figure 2 presents the event-study estimates. The pre-treatment coefficients are generally small and imprecisely estimated, providing no strong evidence of differential trends before rollout. By contrast, the post-treatment coefficients become progressively larger, consistent with the view that the effects of broadband expansion materialize gradually rather than immediately.

### 8.3 稳健性段落模板

> The robustness checks in Table 3 and the appendix show that the main estimates remain broadly stable across alternative treatment definitions, sample restrictions, and control strategies. These exercises reduce the concern that the baseline findings are driven by treatment coding, a small subset of municipalities, or a particular regression specification.

### 8.4 机制段落模板

> The mechanism results are consistent with the interpretation that broadband rollout affects labor market adjustment through improved matching efficiency and local firm dynamics. At the same time, these estimates should be interpreted cautiously, because the mechanism outcomes are not separately identified from the main treatment effect.

---

## 9. 当前结果写作中的主要风险

### 9.1 需要避免的问题

- 把 event-study 无显著 pre-trend 写成“完全证明外生性”
- 把稳健性检验写成新的 headline finding
- 把机制结果写成确定性 causal channel
- 不说明 adjusted sample 是否变化
- 不说明 clustering level 与 treatment variation 的关系
- 把 appendix 里才有的关键识别细节从正文省掉

### 9.2 如果结果暂时不够强，应如何写

如果估计不够稳健，应使用更克制表述，例如：

- is associated with
- is consistent with
- suggests
- appears to

而不是直接写：

- increases
- reduces
- leads to

---

## 10. 下一步建议

### 10.1 对论文正文

1. 先固定主结果表和 event-study 图  
2. 按识别威胁组织 robustness，而不是罗列所有补充回归  
3. 将 mechanism 和 heterogeneity 明确降级为 supporting evidence  
4. 在主文保留最关键的 identification logic，不要全部挪到 appendix

### 10.2 对附录

1. 补充 variable construction  
2. 补充 sample construction and exclusions  
3. 放入额外 placebo 和 alternative-specification tables  
4. 增加 replication / data-access note

### 10.3 对复现包

需要准备：

- do-file execution order
- table / figure production scripts
- intermediate data description
- restricted-data disclosure if relevant
- README with dependencies and expected outputs

---

## 11. 总结

当前结果分析表明，broadband rollout 对小型 municipalities 的 labor market adjustment 具有正向影响，且动态结果与稳健性分析在总体上支持这一结论。现阶段最重要的不是继续堆砌结果，而是把现有估计按照 empirical economics 的写作纪律组织清楚：主结果围绕识别逻辑展开，稳健性围绕识别威胁展开，机制与异质性保持克制表述，附录承担支持性材料而不替代正文中的核心设计说明。

**建议结论**:  
该项目的 Results 部分应围绕 `baseline DID + event study + targeted robustness + disciplined mechanism/heterogeneity writing` 来组织，而不是采用 benchmark-style experiment reporting.
