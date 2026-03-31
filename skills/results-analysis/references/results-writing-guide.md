# Results Section Writing Guide for Empirical Economics and Agricultural Economics

论文 `Results` 部分的写作规范与最佳实践。  
本指南适用于 empirical economics 和 agricultural economics 论文，而不是 benchmark-style ML experiment reporting。

---

## Results 部分的目的

**核心目标**: 围绕识别设计呈现主结果，并说明这些结果在统计和经济意义上意味着什么。

**Results 部分不是**:

- 重复 `Data` 或 `Empirical Strategy` 的全部内容
- 罗列与识别无关的补充回归
- 把 mechanism、heterogeneity 或 robustness 写成新的 headline finding
- 用强于设计所支持的语言做因果宣称

**Results 部分是**:

- 展示主估计结果
- 说明结果的方向、数量级和经济意义
- 提供与识别相关的支持性证据
- 用 targeted robustness 回应具体识别威胁
- 将补充材料有纪律地指向 appendix

---

## 标准结构

### 推荐组织方式

```markdown
## Results

### Main findings overview
[1 段简要概述主结果与主要识别支持]

### Baseline estimates
[主回归表，解释系数、规格推进和经济意义]

### Identification support / dynamic evidence
[event study, first stage, design validity evidence]

### Robustness checks
[围绕识别威胁组织，而不是机械堆砌]

### Heterogeneity analysis
[仅在有理论动机时展开]

### Mechanism evidence
[作为 supporting evidence，保持克制]

### Appendix roadmap
[说明哪些补充结果见附录]
```

### 推荐逻辑顺序

1. `baseline estimates`
2. `identification support / dynamic evidence`
3. `robustness`
4. `heterogeneity`
5. `mechanism`
6. `appendix signposting`

不要用 benchmark-style 顺序替代 identification-driven 顺序。

---

## 写作原则

### 1. 每个结果模块都要服务于识别逻辑

错误做法不是结果少，而是结果与识别威胁无关。

❌ **错误**: “表 3 展示了另外一组稳健性检验结果。”

✅ **更好**: “为了检验基准结果是否受 selective rollout timing 驱动，表 3 使用 alternative treatment definitions 和 restricted samples 重新估计基准规格。”

---

### 2. 正文应围绕表图写，而不是围绕抽象结论写

❌ **错误**: “结果表明 broadband rollout 显著改善就业。”

✅ **更好**: “Table 2 reports the baseline DID estimates of broadband rollout on local employment outcomes. Across specifications, the coefficient on rollout remains positive and statistically significant.”

---

### 3. 解释系数时必须说明单位和经济意义

Results 中不能只说显著，还要说：

- 是 level effect、log-point effect、percentage-point effect 还是 elasticity
- 数量级是否具有经济意义
- 加 controls / FE 后是否稳定
- 是否因为 sample 改变而影响 comparability

❌ **错误**: “系数显著为正，说明效果很好。”

✅ **更好**: “The estimate implies a 1.2 percentage-point increase in employment, which is economically meaningful relative to the pre-treatment mean.”

---

### 4. Identification support 要写得克制

特别是 DID / event study / IV / RDD 结果，不要把支持性检验写成“完全证明识别成立”。

❌ **错误**: “pre-trends 不显著证明了识别完全有效。”

✅ **更好**: “The event-study estimates provide no strong evidence of differential pre-trends, which is consistent with the maintained identifying assumption, although it cannot fully rule out all endogeneity concerns.”

---

### 5. Robustness 要回应 threat，不要装饰性堆砌

每个 robustness check 都应该回答一个具体问题：

- 是否是 treatment mismeasurement？
- 是否是 selective timing？
- 是否是 sample composition？
- 是否是 omitted local shocks？
- 是否是 spillover？

❌ **错误**: “我们做了大量稳健性检验，结果都稳健。”

✅ **更好**: “These checks reduce the concern that the baseline estimate is driven by treatment coding, a small subset of municipalities, or one particular control set.”

---

### 6. Mechanism 和 Heterogeneity 要降一级写

Mechanism 和 heterogeneity 通常是 supporting evidence，不应自动升级为主发现。

❌ **错误**: “这证明 broadband 通过 job matching channel 起作用。”

✅ **更好**: “The mechanism results are consistent with the interpretation that broadband improves job matching efficiency, but they should be interpreted as suggestive rather than definitive evidence.”

---

## Baseline Results 的写法

### 应包含的内容

- 哪张表承载主结果
- 因变量是什么
- 关键系数方向和数量级
- controls / FE / clustering 的推进方式
- 结果是否跨规格稳定
- 该 effect 的经济意义

### 推荐句式

- `Table X reports the baseline estimates of ...`
- `Across specifications, the coefficient on ... remains ...`
- `The magnitude is economically meaningful relative to ...`
- `The estimate remains stable after adding ...`
- `The change across columns is modest, suggesting that ...`

---

## Identification Support / Dynamic Evidence 的写法

### DID / Event Study

Results 中应明确：

- omitted period
- treatment timing convention
- pre-treatment coefficients 如何解释
- post-treatment dynamics 如何解释

### IV

Results 中应明确：

- first stage 在哪张表
- reduced form / first stage / second stage 如何区分
- first-stage strength 是否足够
- second-stage interpretation 的范围

### 推荐句式

- `Figure X presents the event-study estimates around ...`
- `The pre-treatment coefficients provide no strong evidence of ...`
- `Post-treatment coefficients become larger over time, suggesting that ...`
- `Panel B reports the first-stage results, which show that ...`

---

## Robustness 的写法

### 应包含的内容

- 该检查回应的 threat 是什么
- 改动了哪一维 specification
- 结果方向、数量级、精度是否保持
- 主结论是否改变

### 推荐句式

- `Table X and Appendix Table AX show that the baseline findings remain ...`
- `These checks reduce the concern that ...`
- `The estimate is somewhat smaller under this specification, but remains ...`
- `The main conclusion is unchanged.`

---

## Heterogeneity 的写法

### 应包含的内容

- 分组是否有理论动机
- subgroup 是如何定义的
- 差异是否有经济解释
- 结果是否只是 supporting evidence

### 推荐句式

- `The heterogeneity estimates suggest stronger effects in ...`
- `This pattern is consistent with the idea that ...`
- `These subgroup results should be interpreted as supportive rather than definitive evidence.`

---

## Mechanism 的写法

### 应包含的内容

- 机制变量是什么
- 为什么这个机制与主问题相关
- 机制结果如何支持主解释
- 为什么不能把它写成额外独立识别

### 推荐句式

- `The mechanism results are consistent with ...`
- `These findings suggest, but do not definitively establish, that ...`
- `The mechanism evidence should therefore be interpreted cautiously ...`

---

## 表格写作规范

### 主结果表

默认遵循 economics-journal table discipline:

- 一列对应一个 `DV` 或一个 specification family
- `Controls`, `FE`, `Clustered SE`, `Weights` 用 `Yes/No` 或清晰方式披露
- 每列都报告 `N`
- 若不同列样本变动，必须说明
- table note 要写清 sample、unit of observation、FE、clustering、权重、特殊样本规则

### Event-study / IV 表

必须额外说明：

- omitted period / omitted category
- timing convention
- first stage / reduced form / second stage 的组织方式
- instrument definition if applicable

### 避免的表格问题

- raw variable names 直接上表
- 系数单位不清楚
- clustering level 不写
- appendix 表静默换样本
- note 把关键设计逻辑藏起来替代正文说明

---

## 图形写作规范

Results 中图形应服务于识别与解释，而不是装饰。

### 推荐图形类型

- `event-study plot`
- `coefficient plot`
- `heterogeneity coefficient plot`
- `descriptive trend plot`
- `mechanism-related descriptive figure`（仅在必要时）

### 图形说明应包含

- 图形展示什么估计对象
- omitted period / baseline group
- confidence interval or standard error display
- 如何与主结果关联

### 推荐句式

- `Figure X plots the event-study coefficients with 95% confidence intervals.`
- `The figure shows that ...`
- `The graphical pattern is consistent with the regression results in Table X.`

---

## 常见错误

### 错误 1: 结果强度超过设计强度

❌ “这证明了政策带来因果影响。”  
✅ “These estimates are consistent with a causal interpretation under the maintained identifying assumptions.”

### 错误 2: 把 mechanism 写成结构性证明

❌ “机制回归证明了该渠道。”  
✅ “The mechanism evidence supports, but does not independently establish, this interpretation.”

### 错误 3: 不说明样本变化

❌ 正文比较列 (2) 和列 (5)，但 `N` 已明显不同。  
✅ 明确说明 harmonized sample 或解释 sample change。

### 错误 4: prose 与 table 不一致

❌ 正文说 effect 显著，但表中已不显著。  
✅ 每句 headline prose 都对照最终 table export 检查。

### 错误 5: robustness 没有目的

❌ 罗列 8 个 check，但不知道各自回应哪个 threat。  
✅ 每个 check 对应一个明确识别担忧。

---

## 检查清单

提交前检查：

- [ ] 主结果围绕识别设计展开
- [ ] 每个 headline sentence 都能对应到最终表图
- [ ] 系数单位和经济意义解释清楚
- [ ] controls / FE / clustering / sample 在表注中披露完整
- [ ] event-study / IV / RDD 结果写得足够克制
- [ ] robustness checks 与具体 threat 一一对应
- [ ] heterogeneity 有理论动机
- [ ] mechanism 结果没有被写得过强
- [ ] appendix 承担支持性材料，而非隐藏关键设计逻辑
- [ ] text、table、appendix 三者表述一致

---

## 示例 Results 部分

参见：

- `examples/example-results-section.md`

---

## 与其他部分的关系

### Results vs Empirical Strategy

**Empirical Strategy**: 解释设计、方程、假设、威胁  
**Results**: 呈现估计结果，并说明这些结果如何与设计和威胁对应

避免在 Results 中重复整段 strategy，但也不要让 reader 看不出结果如何服务于识别。

### Results vs Discussion / Conclusion

**Results**: 报告主估计、识别支持、稳健性、支持性机制证据  
**Discussion / Conclusion**: 提炼 broader meaning、policy implications、limitations

Results 可以解释经济量级和与识别相关的含义，但不要替代 discussion 去做过度延伸。

---

## 总结

Results 部分的核心原则是：

1. **围绕识别逻辑组织，而不是围绕结果堆砌组织**
2. **先主结果，再识别支持，再 targeted robustness**
3. **异质性与机制是 supporting evidence，不是自动升级的 headline**
4. **所有结果解释都要说明单位、数量级和经济意义**
5. **正文、表格、附录和识别表述必须一致**

遵循这些原则，Results 部分才真正符合 empirical economics 和 agricultural economics 的写作范式。
