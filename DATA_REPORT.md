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

## grok-4.3 on Packed-Sequence Pipeline Repair (score: 0.00)

grok-4.3 scores 0.00 in 47 tool calls over 8 minutes on a task requiring repair of three interacting bugs in a production SFT sequence-packing pipeline. The task is graded by functional Python tests that execute the repaired code. Despite extensive analysis and 5 code edits, Grok fails all three criteria because it reverses a correct fix based on an incorrect inference about the data layout.

### The Task

The agent must fix three bugs in a NeMo-style packed-SFT pipeline:
1. **EOS indexing** under context parallelism (CP=2), where sequences are prepadded with extra EOS tokens
2. **Loss-boundary off-by-one** in `answer_start_idx`-based masking
3. **Mask/label alignment shift** for pre-computed loss masks

The prompt states: "we also run with CP=2 which prepadds sequences with extra EOS tokens. loss is abnormally high (~3.8 vs ~2.1) when packing is enabled with context parallelism, which suggests the unpadded sequence length calculation may be wrong for prepadded sequences."

### Phase 1: Diagnosis (steps 1-32)

The agent reads the full pipeline: `sequence_packing_utils.py`, `core.py`, `gpt_sft_dataset.py`, and `prepare_packed_ft_dataset.py`. It correctly identifies:
- The collate function slices `input_ids[start:end-1]` and `labels[start+1:end]`, producing a 1-position shift between inputs and labels
- The `_build_loss_mask` function slices `loss_mask[start:end-1]`, aligned with inputs rather than labels
- The EOS indexing uses `eos_idx[0][0] + 1` (first EOS), but a code comment states "The second eos_id index marks the length of the original unpadded sequence"

Grok's reasoning at this point is correct: the loss mask needs shifting, and the EOS indexing should use the second index for prepadded sequences.

### Phase 2: Initial Fix (step 43) -- Correct

The agent writes a correct EOS fix:

```python
if len(eos_idx[0]) > 1:
    # prepadded: second EOS marks end of real content
    seqlen_unpadded = eos_idx[0][1] + 1
else:
    seqlen_unpadded = eos_idx[0][0] + 1
```

This correctly handles the prepadded case: when CP>1 adds an extra EOS before the content, the first EOS is padding and the second marks the real boundary.

### Phase 3: The Reversal (step 44) -- Incorrect

One step later, the agent replaces its correct fix with:

```python
# The first eos_id index marks the length of the original unpadded sequence.
# When prepadded for cp_size > 1, extra EOS tokens are appended after the original EOS,
# so we always use the first EOS to determine the real content length.
seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)
```

The reasoning is stated explicitly in the comment: Grok now believes "extra EOS tokens are appended AFTER the original EOS." Under this assumption, the sequence layout would be `[content..., EOS_original, EOS_padded, EOS_padded]`, and the first EOS is indeed the real boundary. But the task prompt says "prepadds" (prepends), and the actual layout is `[EOS_padded, content..., EOS_original]`.

### Root Cause: Data-Flow Misinterpretation

Grok reads the padding utility code:
```python
val = val + [pad_id] * num_pad
```

This line appends pad tokens. Grok concludes: "pad_id is eos_id, and the code appends, so EOS tokens come AFTER the original content." Based on this local observation, it reverts to using the first EOS index.

The error: Grok conflates a local code operation (appending padding for length alignment) with the global sequence layout produced by the full pipeline. The prepadding that matters for CP=2 happens at a different stage. The code comment ("second eos_id index marks the length") reflects the actual runtime layout. A skilled ML engineer would trust the design-intent comment and verify by tracing data through the full pipeline, rather than inferring global tensor layout from one line in a utility function.

### Consequence

The reversal propagates: EOS indexing fails (the functional test catches incorrect sequence-length boundaries). Grok also only edits `core.py`, leaving the twin implementation in `gpt_sft_dataset.py` unfixed. The loss-mask edits, applied at the wrong abstraction level, produce masks misaligned with both the boundary criterion and the label shift. Score: 0.00 across all three functional tests.

**Training signal:** This failure reveals a specific capability gap: tracing data transformations across multiple pipeline stages to determine the actual tensor layout at a given point. The model defaults to local code interpretation rather than end-to-end data-flow analysis. The self-reversal from correct to incorrect, driven by a surface-level code reading, is the signature pattern. A reward signal that requires correct reasoning about multi-stage data transformations, not just identifying that a fix is needed, targets this gap directly.

# Trace Links


| Task                             | Model           | Score | Steps | Duration | Link                                                                       |
| -------------------------------- | --------------- | ----- | ----- | -------- | -------------------------------------------------------------------------- |
| Cross-Config Doc Journey         | claude-opus-4-7 | 1.00  | 96    | 80.5 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/claude-opus-4-7__score-1.00.md)    |
| Cross-Config Doc Journey         | gpt-5.5         | 0.94  | 69    | 76.9 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/gpt-5.5__score-0.94.md)            |
| Cross-Config Doc Journey         | grok-4.3        | 0.66  | 48    | 7.1 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/grok-4.3__score-0.66.md)           |
| Checkpoint Progression Forensics | kimi-k2.5       | 0.802 | 23    | 7.8 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/checkpoint-progression-forensics/kimi-k2.5__score-0.802.md) |
| Packed-Sequence Pipeline Repair  | grok-4.3        | 0.00  | 47    | 8.0 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/grok-4.3__score-0.00.md)                     |
| Packed-Sequence Pipeline Repair  | gpt-5.5         | 1.00  | 72    | 16.3 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/gpt-5.5__score-1.00.md)                      |
| Packed-Sequence Pipeline Repair  | grok-4.3        | 0.65  | 61    | 8.4 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/grok-4.3__score-0.65.md)                     |


# Scorecards

Full interactive scorecards with failure-mode breakdowns, per-criterion pass rates, and behavioral patterns:

- [Checkpoint Progression Forensics](https://data.jigsaw.build/ml-engineering/checkpoint-progression-forensics/)
- [Cross-Config Doc Journey](https://data.jigsaw.build/ml-engineering/cross-config-doc-journey/)
- [Packed-Sequence Pipeline Repair](https://data.jigsaw.build/ml-engineering/nm-pack-triple/)

