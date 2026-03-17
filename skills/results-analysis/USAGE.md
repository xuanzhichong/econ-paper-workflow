# Results Analysis Usage

This skill now defaults to empirical economics workflows.

## Typical Prompts

- 帮我根据这套 `Stata do-file` 设计主回归和稳健性
- 我有 `.dta` 和一张回归表，帮我整理成 Results section
- 看看这个 DID 设计还需要哪些 pre-trend 和 placebo 检查
- 帮我做一个 `regression-spec-matrix.md`

## Expected Inputs

- `.dta`
- `.do`
- `.log`
- regression table `.tex`
- data dictionaries or variable notes

## Expected Outputs

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`

The skill should not assume TensorBoard, benchmark comparison, or ablation studies unless the user explicitly asks for an ML workflow.
