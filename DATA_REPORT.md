# ML Engineering Sample

This report details three tasks from our ML Engineering collection. The tasks require diagnosing training pathologies from raw checkpoint data, tracing documents through data pipelines, and repairing production framework bugs from symptoms alone.

# Tasks


| Task                             | What it tests                                                                                                                                                                           | Criteria                   | Rollouts |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- | -------- |
| Checkpoint Progression Forensics | Diagnosing PEFT overfitting hidden by falling training loss; connecting training dynamics to downstream benchmark degradation                                                           | 7 (5 positive, 2 penalty)  | 111      |
| Cross-Config Doc Journey         | Tracing documents through 7 datatrove pipeline configs at the filter-threshold level; quantifying config overlap; diagnosing defective dedup variants                                   | 10 (9 positive, 1 penalty) | 127      |
| Packed-Sequence Pipeline Repair  | Repairing three defects in a production NeMo-style SFT pipeline (EOS indexing, loss-boundary off-by-one, mask/label shift) from symptoms alone, with no training reproduction available | 3 functional checks        | 48       |


# Environment

All three tasks share the same harness configuration:

- **Starting state:** pre-populated workspace with real ML artifacts (training checkpoints, parquet files, pipeline source code). No instructions beyond a natural-language problem description.
- **Tooling:** bash shell and file editor via MCP. No IDE, no visualization tools, no Jupyter.
- **Network:** disabled. All required data is local.
- **Grading:** hidden verifiers run after submission. The agent never sees the rubric or test logic during the rollout.

**Checkpoint Progression Forensics** provides 130+ training checkpoints across 33 adapter runs (LoRA, DoRA, IA3, AdaLoRA, full fine-tune), plus downstream benchmark results. The agent must reconstruct step-keyed eval-loss trajectories and connect overfitting patterns to benchmark degradation.

**Cross-Config Doc Journey** provides 7 datatrove pipeline configurations, a multilingual corpus, quality-score parquets, retention matrices, and the GopherQualityFilter source. The agent must trace specific documents through all configs and explain retention decisions at the sub-threshold level.

**Packed-Sequence Pipeline Repair** provides a production sequence-packing SFT codebase with three interacting bugs. The agent must diagnose and fix all three from described symptoms alone, with no ability to run training.

# Calibration

We evaluated 12 frontier models with 5-14 rollouts each, yielding 286 scored rollouts across the three tasks. Pass requires a perfect score (all criteria met). Aggregate panel pass@1: 2.8% (8 of 286 rollouts). Only 4 models have achieved a perfect score on any task in this collection.


| Task                             | Models | Rollouts | Panel mean | Panel pass@1 | Panel pass@10 | Ceiling |
| -------------------------------- | ------ | -------- | ---------- | ------------ | ------------- | ------- |
| Checkpoint Progression Forensics | 12     | 111      | 0.48       | 0%           | 0%            | 0.802   |
| Cross-Config Doc Journey         | 12     | 127      | 0.60       | 5.5%         | 44.5%         | 1.00    |
| Packed-Sequence Pipeline Repair  | 11     | 48       | 0.32       | 2.1%         | 21%           | 1.00    |


## Per-Task Leaderboards

### Checkpoint Progression Forensics

No model achieves a perfect score. The panel ceiling is 0.802 (4 of 5 positive criteria met). The hardest criterion (C5: connecting overfitting to per-benchmark degradation evidence) passes in only 34% of rollouts panel-wide.


| Model                  | Mean | Pass@1 | Pass@10 |
| ---------------------- | ---- | ------ | ------- |
| claude-sonnet-4-6      | 74%  | 0%     | 0%      |
| claude-opus-4-7        | 61%  | 0%     | 0%      |
| gpt-5.5                | 56%  | 0%     | 0%      |
| claude-haiku-4-5       | 52%  | 0%     | 0%      |
| qwen3.6-plus           | 52%  | 0%     | 0%      |
| claude-opus-4-6        | 50%  | 0%     | 0%      |
| grok-4.3               | 50%  | 0%     | 0%      |
| gpt-5.4                | 44%  | 0%     | 0%      |
| glm-5.1                | 42%  | 0%     | 0%      |
| kimi-k2.5              | 42%  | 0%     | 0%      |
| gemini-3.1-pro-preview | 38%  | 0%     | 0%      |
| gemini-2.5-pro         | 16%  | 0%     | 0%      |


### Cross-Config Doc Journey

Three models achieve perfect scores. The task is the most solvable in the collection but still demanding: 10 criteria must all be met simultaneously.


| Model                  | Mean | Pass@1 | Pass@10 |
| ---------------------- | ---- | ------ | ------- |
| gpt-5.5                | 86%  | 9%     | 91%     |
| gpt-5.4                | 84%  | 0%     | 0%      |
| claude-opus-4-6        | 82%  | 0%     | 0%      |
| claude-opus-4-7        | 77%  | 20%    | 100%    |
| glm-5.1                | 74%  | 0%     | 0%      |
| qwen3.6-plus           | 68%  | 0%     | 0%      |
| kimi-k2.5              | 57%  | 0%     | 0%      |
| claude-sonnet-4-6      | 56%  | 40%    | 100%    |
| claude-haiku-4-5       | 55%  | 0%     | 0%      |
| grok-4.3               | 53%  | 0%     | 0%      |
| gemini-3.1-pro-preview | 21%  | 0%     | 0%      |
| gemini-2.5-pro         | 15%  | 0%     | 0%      |


### Packed-Sequence Pipeline Repair

Only gpt-5.4 achieves a perfect score (1 of 3 rollouts). The task requires simultaneously fixing three interacting bugs where each fix constrains the others.


| Model                  | Mean | Pass@1 | Pass@10 |
| ---------------------- | ---- | ------ | ------- |
| gpt-5.4                | 68%  | 33%    | 100%    |
| kimi-k2.5              | 65%  | 0%     | 0%      |
| claude-opus-4-7        | 46%  | 0%     | 0%      |
| grok-4.3               | 45%  | 0%     | 0%      |
| gemini-3.1-pro-preview | 41%  | 0%     | 0%      |
| glm-5.1                | 35%  | 0%     | 0%      |
| claude-sonnet-4-6      | 28%  | 0%     | 0%      |
| claude-opus-4-6        | 28%  | 0%     | 0%      |
| qwen3.6-plus           | 23%  | 0%     | 0%      |
| claude-haiku-4-5       | 0%   | 0%     | 0%      |
| gemini-2.5-pro         | 0%   | 0%     | 0%      |


# Trace Walkthrough

## grok-4.3 on Checkpoint Progression Forensics (score: 0.593)

grok-4.3 scores 0.593 in 31 tool calls over 5.4 minutes. Passes C1 (r32 eval_loss trajectory), C2 (multi-run comparison), and C3 (identifies second overfitting case). Fails C4 (downstream benchmark correlation) and C5 (concrete failure-mode evidence). No penalties applied.

### Phase 1: Environment Discovery (steps 1-6)

The agent explores the workspace structure: `runs/` directory with 33 adapter configurations, `evaluations/` with benchmark results, and top-level parquet files (`training_curves_comparison.parquet`, `eval_results_comparison.parquet`, `qwen3_cross_run_comparison.parquet`). This initial scan correctly identifies all data sources.

### Phase 2: Training Dynamics Analysis (steps 7-17)

The agent loads `training_curves_comparison.parquet` and reconstructs step-keyed eval_loss trajectories for all runs. It identifies:

- `lora_r32_all_alpaca`: eval_loss rising from 1.27 to 1.44 after step 250 (correct)
- `lora_r16_mlp_alpaca`: catastrophic overfitting, eval_loss reaching 1.97 (correct)
- `full_ft_code`: gradual overfitting after step 600, eval_loss rising from 0.89 to 1.10 (correct, satisfies C3)
- Stable runs (`ia3`, `adalora`, `lora_r4`) showing monotonic improvement

This analysis correctly reconstructs the full sweep. The agent reads individual `trainer_state.json` files to cross-validate the parquet data, confirming step-keyed values match.

### Phase 3: The Critical Gap (step 10 and step 18)

At step 10, the agent reads `eval_results_comparison.parquet` and discovers it contains downstream benchmark scores (arc_easy, hellaswag, piqa) for every adapter run. At step 18, it pivots the data into a per-run benchmark comparison table, revealing that overfitting adapters (`lora_r32_all`, `lora_r16_mlp`) score lower on downstream benchmarks than stable ones.

**The agent has the data. It sees the connection. It does not use it.**

### Phase 4: Report Generation (steps 26-27)

The agent's reasoning at step 26: "Now I have a comprehensive understanding of the training data. Let me compile my findings into the REPORT.md file."

The resulting report is technically detailed: 9,000+ characters covering eval_loss trajectories, overfitting mechanisms, adapter susceptibility rankings, and early-warning metrics. It correctly identifies which adapter types overfit and why. But it contains zero benchmark scores, zero per-sample predictions, and zero correlation between overfitting and downstream task performance.

### Root Cause: Analytical Prioritization Failure

The agent treats training dynamics as the complete answer. It conflates "identifying overfitting via eval_loss divergence" with "demonstrating that overfitting actually degrades downstream performance." In ML research, these are distinct claims requiring distinct evidence. A model's eval_loss can rise without proportional benchmark degradation (if the overfitting is on low-frequency patterns irrelevant to the benchmarks), or benchmark scores can drop without eval_loss divergence (distribution shift). The rubric requires showing the actual correlation; the agent assumes it.

This is a genuine analytical gap, not a data-access issue. The agent examined the benchmark data (step 10, step 18), produced a pivot table showing per-adapter benchmark performance, then excluded this from the final report. The report's reasoning treats eval_loss trajectories as sufficient evidence for downstream impact without verifying the claim against the available benchmark data.

**Training signal:** This failure pattern is trainable. The model executes the "hard" part (reconstructing trajectories from raw checkpoints, identifying overfitting patterns across 33 runs) but stops one analytical step short of the complete picture. A reward signal penalizing incomplete causal chains (identifying a pattern without connecting it to its downstream consequence) targets the right capability gap.

# Trace Links


| Task                             | Model           | Score | Steps | Duration | Link                                                                       |
| -------------------------------- | --------------- | ----- | ----- | -------- | -------------------------------------------------------------------------- |
| Cross-Config Doc Journey         | claude-opus-4-7 | 1.00  | 96    | 80.5 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/claude-opus-4-7__score-1.00.md)    |
| Cross-Config Doc Journey         | gpt-5.5         | 0.94  | 69    | 76.9 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/gpt-5.5__score-0.94.md)            |
| Cross-Config Doc Journey         | grok-4.3        | 0.66  | 48    | 7.1 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/grok-4.3__score-0.66.md)           |
| Checkpoint Progression Forensics | kimi-k2.5       | 0.802 | 23    | 7.8 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/checkpoint-progression-forensics/kimi-k2.5__score-0.802.md) |
| Checkpoint Progression Forensics | grok-4.3        | 0.593 | 31    | 5.4 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/checkpoint-progression-forensics/grok-4.3__score-0.593.md)  |
| Packed-Sequence Pipeline Repair  | gpt-5.5         | 1.00  | --    | 16.3 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/gpt-5.5__score-1.00.md)                      |
| Packed-Sequence Pipeline Repair  | grok-4.3        | 0.65  | 61    | 8.4 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/grok-4.3__score-0.65.md)                     |


# Scorecards

Full interactive scorecards with failure-mode breakdowns, per-criterion pass rates, and behavioral patterns:

- [Checkpoint Progression Forensics](https://data.jigsaw.build/ml-engineering/checkpoint-progression-forensics/)
- [Cross-Config Doc Journey](https://data.jigsaw.build/ml-engineering/cross-config-doc-journey/)
- [Packed-Sequence Pipeline Repair](https://data.jigsaw.build/ml-engineering/nm-pack-triple/)

