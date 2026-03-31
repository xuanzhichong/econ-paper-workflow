# Results Section Example

论文 `Results` 部分的完整示例，展示如何在 empirical economics / agricultural economics 论文中呈现主结果、动态结果、稳健性、异质性和机制证据。

---

## Results

### Main Findings Overview

本节分析 broadband rollout 对小型 municipalities labor market adjustment 的影响。基准 DID 结果显示，broadband rollout 与更高的 local employment rate 和更低的 unemployment rate 显著相关。事件研究结果未显示明显的 pre-treatment differential trends，且 post-treatment effects 在 rollout 后第 2–3 年逐步增强。稳健性检验表明，结果对 alternative treatment definitions、sample restrictions 和 controls 设定总体稳健。异质性分析显示，effects 在 baseline digital access 更弱、labor market thinner 的 municipalities 中更为明显。机制结果进一步表明，broadband rollout 可能部分通过 job matching efficiency 和 local firm entry 发挥作用，但这些机制结果应视为支持性证据，而非独立识别的因果机制。

### Baseline Estimates

表 2 报告了 broadband rollout 对 labor market outcomes 的基准估计结果。列 (1)–(3) 以 employment rate 为因变量，列 (4)–(6) 以 unemployment rate 为因变量。最简规格仅包含 municipality fixed effects 和 year fixed effects；后续规格逐步加入 time-varying municipal controls 以及更严格的样本限制。

结果显示，broadband rollout 与就业率上升显著相关，同时与失业率下降相关。更重要的是，随着 controls 和 alternative specifications 的加入，估计系数在符号、数量级和统计精度上保持总体稳定。这表明基准结果并非由单一规格选择驱动。

从经济意义上看，估计量不仅具有统计显著性，也具有实质意义。若按基准规格解释，broadband rollout 带来的 employment improvement 对小型 municipalities 而言并非微不足道，而是足以改变 local labor market adjustment 的速度与方向。

**Table 2. Baseline DID Estimates of Broadband Rollout on Local Labor Market Outcomes**

|  | (1) | (2) | (3) | (4) | (5) | (6) |
|---|---:|---:|---:|---:|---:|---:|
|  | Employment rate | Employment rate | Employment rate | Unemployment rate | Unemployment rate | Unemployment rate |
| Broadband rollout | 0.012*** | 0.011*** | 0.010** | -0.008** | -0.007** | -0.007** |
|  | (0.004) | (0.004) | (0.004) | (0.003) | (0.003) | (0.003) |
| Municipal controls | No | Yes | Yes | No | Yes | Yes |
| Municipality FE | Yes | Yes | Yes | Yes | Yes | Yes |
| Year FE | Yes | Yes | Yes | Yes | Yes | Yes |
| Clustered SE | Yes | Yes | Yes | Yes | Yes | Yes |
| Observations | 4,820 | 4,820 | 4,510 | 4,820 | 4,820 | 4,510 |

**Notes:** Standard errors clustered at the municipality level are reported in parentheses. Municipal controls include time-varying demographic and fiscal covariates. Column (3) and column (6) impose a harmonized estimation sample.

### Dynamic Effects and Identification Support

图 2 展示了围绕 broadband rollout timing 的 event-study estimates。pre-treatment coefficients 整体接近于零，且未表现出系统性的提前变化，这说明在 rollout 之前 treated and not-yet-treated municipalities 之间不存在明显的差异化趋势。虽然这一结果不能完全证明 identification assumption 成立，但它至少没有提供强烈的反证。

相比之下，post-treatment coefficients 在 rollout 后逐步增强，尤其是在第 2–3 年后更为明显。这一动态模式表明，broadband 对 labor market adjustment 的影响并非立即实现，而更可能通过 gradual adjustment process 发生，例如 job search frictions 下降、local labor matching 改善或 firm responses 的逐步累积。

**Figure 2. Event-Study Estimates Around Broadband Rollout**  
*Notes: The omitted category is the year immediately before rollout. Coefficients are plotted with 95% confidence intervals. Standard errors are clustered at the municipality level.*

### Robustness Checks

表 3 与附录表 A2–A5 报告了稳健性检验。我们依次检验了以下可能影响基准结果的因素：treatment definition 的变化、early adopters 的剔除、加入 municipality-specific pre-trends（在可辩护范围内）、alternative clustering choices，以及对潜在 spillover municipalities 的样本限制。

总体来看，主结果在这些规格下方向一致、数量级相近。这表明基准发现并不主要依赖于某一种 treatment coding、少数样本点，或某个特定 controls 组合。与此同时，这些稳健性结果应被理解为“降低识别担忧”，而不是“完全消除所有内生性问题”。

**Table 3. Robustness Checks**

|  | (1) Alternative rollout definition | (2) Exclude early adopters | (3) Add pre-trends | (4) Alternative clustering | (5) Exclude neighboring municipalities |
|---|---:|---:|---:|---:|---:|
| Broadband rollout | 0.011** | 0.010** | 0.009* | 0.010** | 0.009** |
|  | (0.004) | (0.004) | (0.005) | (0.004) | (0.004) |
| Controls | Yes | Yes | Yes | Yes | Yes |
| Municipality FE | Yes | Yes | Yes | Yes | Yes |
| Year FE | Yes | Yes | Yes | Yes | Yes |
| Observations | 4,790 | 4,260 | 4,510 | 4,510 | 4,080 |

**Notes:** Each column modifies the baseline specification in one dimension only. Full details are provided in Appendix Table A2–A5.

### Heterogeneity Analysis

接下来我们考察 broadband rollout 是否在不同 municipalities 之间产生异质影响。表 4 按 baseline digital access 和 local labor market thickness 进行分组。结果显示，effects 在 broadband 基础设施原本较弱、劳动力市场较薄的 municipalities 中更为明显。这一模式与如下解释一致：当信息摩擦更高、job matching 更困难时，数字基础设施的边际作用更大。

需要强调的是，这里的异质性结果用于帮助解释主结果的适用边界，而不是提供新的独立识别结论。因此，正文中应将其表述为 **consistent with** 或 **suggests**, 而不是机械上升为结构性证明。

**Table 4. Heterogeneity by Baseline Digital Access and Labor Market Thickness**

|  | Low baseline digital access | High baseline digital access | Thin labor market | Thick labor market |
|---|---:|---:|---:|---:|
| Broadband rollout | 0.016*** | 0.006 | 0.014*** | 0.005 |
|  | (0.005) | (0.004) | (0.005) | (0.004) |

### Mechanism Evidence

最后，我们考察可能的作用机制。表 5 以 job-finding rate 和 local firm entry 为因变量。结果显示，broadband rollout 与更高的 job-finding rate 以及更强的 local firm entry activity 相关。这一模式与“broadband 改善信息获取、促进匹配效率、并降低创业与扩张的协调成本”的解释一致。

但这些机制结果需要谨慎解释。由于这些中介变量并未在独立识别框架下估计，我们更合适的表述应是：机制证据**支持**主结果的解释，而不是**证明**某一特定渠道。

**Table 5. Mechanism Outcomes**

|  | Job-finding rate | Firm entry |
|---|---:|---:|
| Broadband rollout | 0.009** | 0.013** |
|  | (0.004) | (0.006) |
| Controls | Yes | Yes |
| Municipality FE | Yes | Yes |
| Year FE | Yes | Yes |

### Summary of the Results

总体而言，本节结果表明 broadband rollout 与更有利的 local labor market adjustment 显著相关。基准 DID estimates、event-study dynamics 和 targeted robustness checks 在总体上支持这一结论。异质性结果显示，effects 在数字基础设施更薄弱、劳动力市场更薄的 municipalities 中更为明显；机制结果则表明，job matching efficiency 和 local firm dynamics 可能是重要渠道。

从写作上看，本节最重要的是保持结果组织的层次分明：  
第一，主结果围绕 baseline estimates 与 event-study identification support 展开；  
第二，稳健性检验应明确回应具体识别威胁；  
第三，异质性与机制结果应保持克制，只作为 supporting evidence 呈现；  
第四，所有补充规格、placebo tests 和 variable-construction detail 应清晰指向 appendix，而不是让正文被附属性结果淹没。

---

## 写作要点说明

### 1. 结果组织顺序

推荐顺序：

- `baseline estimates`
- `dynamic / identification support`
- `robustness`
- `heterogeneity`
- `mechanism`
- `appendix signposting`

不要用 benchmark-style 顺序替代 identification-driven 顺序。

### 2. 正文应围绕表图写

- ✅ `Table 2 reports...`
- ✅ `Figure 2 presents...`
- ✅ `Appendix Table A3 shows...`
- ❌ 不要脱离表图做泛泛结果总结

### 3. 结果解释要有经济意义

需要说明：

- 系数单位
- 经济量级
- 规格变化后的稳定性
- 估计是否依赖样本变化

### 4. 识别支持和结果强度要匹配

- event-study 无明显 pre-trend ≠ 完全证明外生性
- robustness 支持主结果 ≠ 完全排除内生性
- mechanism result ≠ 额外独立识别
- heterogeneity result ≠ 结构模型证明

### 5. Appendix 的角色

Appendix 应承担：

- extra tables
- placebo tests
- alternative samples
- variable construction details
- supplementary specifications

但不要把关键 identification logic 或 core sample definitions 藏进 appendix。

---

## 常用句式

### 引入主结果
- `Table X reports the baseline estimates of ...`
- `Across specifications, the coefficient on ... remains ...`
- `The estimates suggest that ...`

### 解读动态结果
- `Figure X presents the event-study estimates around ...`
- `The pre-treatment coefficients provide no strong evidence of ...`
- `The post-treatment pattern suggests that the effect emerges gradually ...`

### 引入稳健性
- `Table X and Appendix Table AX show that the baseline findings remain ...`
- `These checks reduce the concern that ...`
- `The results are not driven solely by ...`

### 引入异质性
- `The heterogeneity estimates suggest stronger effects in ...`
- `This pattern is consistent with the idea that ...`
- `These subgroup results should be interpreted as supporting evidence ...`

### 引入机制
- `The mechanism results are consistent with ...`
- `These findings suggest, but do not definitively establish, that ...`
- `The mechanism evidence should therefore be interpreted cautiously ...`
