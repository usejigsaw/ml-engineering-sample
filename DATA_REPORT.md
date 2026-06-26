# ML Engineering Sample

This report details three tasks from 161 tasks in our [ML Engineering](https://data.jigsaw.build/ml-engineering/) collection. The tasks require diagnosing training pathologies from raw checkpoint data, tracing documents through data pipelines, and repairing production framework bugs from symptoms alone.

# Aggregated Metrics

We detail the task difficulty below on our three sample tasks.


| **Model**         | **Mean** | **Pass@1** | **Pass@5** | **Min** | **Max** | **Std** | **Range** |
| ----------------- | -------- | ---------- | ---------- | ------- | ------- | ------- | --------- |
| GPT 5.5           | 85.7     | 35.0%      | 88.4%      | 59.3    | 100     | 15.6    | 40.7      |
| GLM 5.2           | 70.9     | 13.3%      | 51.1%      | 0.0     | 100     | 25.7    | 100       |
| GPT 5.4           | 70.1     | 8.7%       | 36.5%      | 35.0    | 100     | 18.9    | 65.0      |
| Claude Sonnet 4.6 | 70.0     | 8.0%       | 34.1%      | 0.0     | 100     | 26.7    | 100       |
| Gemini 3.5 Flash  | 62.4     | 5.6%       | 24.9%      | 0.0     | 100     | 25.9    | 100       |
| Claude Opus 4.7   | 61.9     | 12.0%      | 47.2%      | 0.0     | 100     | 33.9    | 100       |
| GLM 5.1           | 58.9     | 20.8%      | 68.9%      | 0.0     | 100     | 34.4    | 100       |
| Qwen3.6 Plus      | 58.7     | 4.8%       | 21.6%      | 0.0     | 100     | 32.8    | 100       |
| Kimi K2.5         | 53.9     | 0.0%       | 0.0%       | 0.0     | 80.2    | 21.7    | 80.2      |
| Kimi K2.6         | 52.8     | 0.0%       | 0.0%       | 0.0     | 94.0    | 35.2    | 94.0      |
| Claude Opus 4.5   | 51.8     | 0.0%       | 0.0%       | 0.0     | 90.0    | 23.4    | 90.0      |
| Claude Haiku 4.5  | 38.6     | 0.0%       | 0.0%       | 0.0     | 80.2    | 29.8    | 80.2      |
| **Grok 4.3**      | 15.7     | 0.0%       | 0.0%       | 0.0     | 65.0    | 20.1    | 65.0      |


# Environment

All three tasks share the same harness configuration:

- **Starting state:** pre-populated workspace with real ML artifacts (training checkpoints, parquet files, pipeline source code). No instructions beyond a natural-language problem description.
- **Tooling:** bash shell and file editor via MCP. No IDE, no visualization tools, no Jupyter.
- **Network:** disabled. All required data is local.
- **Grading:** hidden verifiers run after submission. The agent never sees the rubric or test logic during the rollout.

# Tasks


| Task                             | What it tests                                                                                                                                                                           |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Checkpoint Progression Forensics | Diagnosing PEFT overfitting hidden by falling training loss; connecting training dynamics to downstream benchmark degradation                                                           |
| Cross-Config Doc Journey         | Tracing documents through 7 datatrove pipeline configs at the filter-threshold level; quantifying config overlap; diagnosing defective dedup variants                                   |
| Packed-Sequence Pipeline Repair  | Repairing three defects in a production NeMo-style SFT pipeline (EOS indexing, loss-boundary off-by-one, mask/label shift) from symptoms alone, with no training reproduction available |


# Calibration

### Checkpoint Progression Forensics

We evaluated 13 models at 10 rollouts each on this sample task.



*Fig 1. Leaderboard for checkpoint-progression-forensics. Pass@1 threshold: score = 100%*



*Fig 2. Metadata for checkpoint-progression-forensics.*

### Cross-Config Doc Journey

We evaluated 13 models at 5-10 rollouts each on this sample task.



*Fig 1. Leaderboard for cross-config-doc-journey. Pass@1 threshold: score = 100%*



*Fig 2. Metadata for cross-config-doc-journey.*

### Packed-Sequence Pipeline Repair

We evaluated 11 models at 3-5 rollouts each on this sample task.



*Fig 1. Leaderboard for packed-sequence-pipeline-repair. Pass@1 threshold: score = 100%*



*Fig 2. Metadata for packed-sequence-pipeline-repair.*

# Verification

Three verification mechanisms cover the three grading modalities in this sample.

**Packed-Sequence Pipeline Repair (deterministic).** Graders are Python functional tests that execute the repaired code against fixed inputs and assert on output values. FP rate: 0. FN rate: 0. No judge variance; grading is fully reproducible.

**Cross-Config Doc Journey (LLM-as-judge).** Graded by Claude Sonnet 4.6 against a 10-criterion weighted rubric with ground-truth reference values embedded in each criterion. FN rate: 0/15 sampled low-scoring traces. FP rate: 0/15 sampled high-scoring traces. Measured stochastic variance: +/-0.08 per trace on re-run. A fabrication gate (weight 0, zero_on_met) fires on checkable contradictions of ground truth; an identity-anchored grounding overrule requires citing real document IDs from the staged corpus to lift a gate-zero.

**Checkpoint Progression Forensics (LLM-as-judge).** Graded by Claude Sonnet 4.6 against a 7-criterion rubric with reference eval_loss trajectories and benchmark ceilings embedded in each criterion. FN rate: 0/15. FP rate: 0/15. A fabrication gate fires on impossible claims (eval_loss outside reference envelope, benchmark accuracy above 0.68 ceiling, wrong base-model identity). A contradiction penalty (-20) docks values that drift outside the reference bands, providing defense-in-depth for calibrated fabrications that stay under the gate.

**Reward-hacking resilience.** All three tasks were tested with dedicated adversarial probes (red-team agents instructed to fabricate convincing outputs without doing real analysis). All probes scored 0.00. Detailed per-attempt results: [Appendix A](APPENDIX_A_REWARD_HACKING.md) (nm-pack-triple, 4 attempts), [Appendix B](APPENDIX_B_REWARD_HACKING_DATATROVE.md) (cross-config-doc-journey, 3 attempts), [Appendix C](APPENDIX_C_REWARD_HACKING_PEFT.md) (checkpoint-progression-forensics, 3 attempts).

# Trace Walkthrough

## grok-4.3 on Packed-Sequence Pipeline Repair

### Phase 1: Diagnosis (steps 1-32)

The agent reads the full pipeline: `sequence_packing_utils.py`, `core.py`, `gpt_sft_dataset.py`, and `prepare_packed_ft_dataset.py`. It correctly identifies:

- The collate function slices `input_ids[start:end-1]` and `labels[start+1:end]`, producing a 1-position shift between inputs and labels
- The `_build_loss_mask` function slices `loss_mask[start:end-1]`, aligned with inputs rather than labels
- The EOS indexing uses `eos_idx[0][0] + 1` (first EOS), but a code comment states "The second eos_id index marks the length of the original unpadded sequence"

Grok's reasoning at this point is correct.

### Phase 2: Initial Fix (step 43)

The agent writes a correct EOS fix:

```python
if len(eos_idx[0]) > 1:
    # prepadded: second EOS marks end of real content
    seqlen_unpadded = eos_idx[0][1] + 1
else:
    seqlen_unpadded = eos_idx[0][0] + 1

```

This correctly handles the prepadded case: when CP>1 adds an extra EOS before the content, the first EOS is padding and the second marks the real boundary.

### Phase 3: Reversal (step 44)

One step later, the agent replaces its correct fix with:

```python
# The first eos_id index marks the length of the original unpadded sequence.
# When prepadded for cp_size > 1, extra EOS tokens are appended after the original EOS,
# so we always use the first EOS to determine the real content length.
seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)

```

The reasoning is stated explicitly in the comment: Grok now believes "extra EOS tokens are appended AFTER the original EOS." Under this assumption, the sequence layout would be `[content..., EOS_original, EOS_padded, EOS_padded]`, and the first EOS is indeed the real boundary. But the task prompt says "prepadds" (prepends), and the actual layout is `[EOS_padded, content..., EOS_original]`.

Grok reads the padding utility code:

```python
val = val + [pad_id] * num_pad

```

This line appends pad tokens. Grok concludes: "pad_id is eos_id, and the code appends, so EOS tokens come AFTER the original content." Based on this local observation, it reverts to using the first EOS index.

The error: Grok conflates a local code operation (appending padding for length alignment) with the global sequence layout produced by the full pipeline. The prepadding that matters for CP=2 happens at a different stage. The code comment ("second eos_id index marks the length") reflects the actual runtime layout.

### Consequence

Grok's submitted code leaves all three bugs in place:

1. **EOS reversal undoes its own correct fix.** The collate function still uses `eos_idx[0][0]` (the first EOS) instead of `eos_idx[0][1]` (the second). For a prepadded sequence `[EOS_pad, content..., EOS_natural]`, this computes `seqlen_unpadded = 0 + 1 = 1` regardless of actual content length. The resulting `cu_seqlens_unpadded` is passed as `cu_seqlens_q`/`cu_seqlens_kv` to the attention kernel via `PackedSeqParams`, which then treats all but the first token as padding -- the direct cause of the ~3.8 vs ~2.1 loss spike under CP. Grok also only edits `core.py`, leaving the identical bug in `gpt_sft_dataset.py` unfixed.

2. **The `sequence_packing_utils.py` root causes are never addressed.** The missing loss-mask roll (which should shift the pre-computed mask by 1 to align with next-token labels) and the wrong `answer_start_idx` boundary (which starts loss one position too late and spuriously excludes tokens matching `pad_id`) remain intact. Grok instead edits `_build_loss_mask` in the collate function and adds loss-mask padding in `prepare_packed_ft_dataset.py`, neither of which fixes the upstream misalignment.

Score: 0.00 across all three functional tests.

# Trace Links


| Task                             | Model           | Score | Steps | Duration | Link                                                                                                                                    |
| -------------------------------- | --------------- | ----- | ----- | -------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Cross-Config Doc Journey         | gemini-3.5-flash | 0.84  | 125   | 19.4 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/gemini-3.5-flash__score-0.84.md)   |
| Cross-Config Doc Journey         | **grok-4.3**    | 0.10  | 14    | 3.1 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/cross-config-doc-journey/grok-4.3__score-0.10.md)           |
| Checkpoint Progression Forensics | glm-5.2         | 1.00  | 84    | 20.5 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/checkpoint-progression-forensics/glm-5.2__score-1.00.md)    |
| Checkpoint Progression Forensics | **grok-4.3**    | 0.198 | 14    | 1.9 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/checkpoint-progression-forensics/grok-4.3__score-0.198.md)  |
| Packed-Sequence Pipeline Repair  | gpt-5.5         | 1.00  | 72    | 16.3 min | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/gpt-5.5__score-1.00.md)                      |
| Packed-Sequence Pipeline Repair  | **grok-4.3**    | 0.65  | 61    | 8.4 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/grok-4.3__score-0.65.md)                     |
| Packed-Sequence Pipeline Repair  | **grok-4.3**    | 0.00  | 47    | 8.0 min  | [trace](https://github.com/usejigsaw/ml-engineering-sample/blob/main/traces/nm-pack-triple/grok-4.3__score-0.00.md)                     |


# Scorecards

Full scorecards with failure-mode breakdowns, per-criterion pass rates, and behavioral patterns:

- [Checkpoint Progression Forensics](https://data.jigsaw.build/ml-engineering/checkpoint-progression-forensics/)
- [Cross-Config Doc Journey](https://data.jigsaw.build/ml-engineering/cross-config-doc-journey/)
- [Packed-Sequence Pipeline Repair](https://data.jigsaw.build/ml-engineering/nm-pack-triple/)

# Appendix

[Appendix A.](APPENDIX_A_REWARD_HACKING.md) Reward-hacking resilience (Packed-Sequence Pipeline Repair)

[Appendix B.](APPENDIX_B_REWARD_HACKING_DATATROVE.md) Reward-hacking resilience (Cross-Config Doc Journey)

[Appendix C.](APPENDIX_C_REWARD_HACKING_PEFT.md) Reward-hacking resilience (Checkpoint Progression Forensics)

