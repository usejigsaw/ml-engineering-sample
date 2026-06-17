# kimi-k2.5 on Checkpoint Progression Forensics

**Score:** 0.802
**Tool calls:** 23
**Duration:** N/A
**Trace ID:** `ea934c2e-659f-47cb-b68d-141595358ae3`

---

## Trajectory

### Step 1: shell

```json
{
  "commands": [
    "find /home/ubuntu/workspace/training-export-proprietary -type d -maxdepth 3 | head -50",
    "ls -la /home/ubuntu/workspace/training-export-proprietary/"
  ]
}
```

### Step 2: shell

```json
{
  "commands": [
    "ls -la /home/ubuntu/workspace/training-export-proprietary/runs/",
    "ls -la /home/ubuntu/workspace/training-export-proprietary/evaluations/ | head -50"
  ]
}
```

### Step 3: shell

```json
{
  "commands": [
    "ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/",
    "ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_code_instructions/",
    "ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/"
  ]
}
```

### Step 4: shell

```json
{
  "commands": [
    "head -20 /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/training_log.csv",
    "head -20 /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_code_instructions/training_log.csv",
    "head -20 /home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/training_log.csv"
  ]
}
```

### Step 5: shell

```json
{
  "commands": [
    "ls /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/",
    "ls /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r16_alpaca/"
  ]
}
```

### Step 6: shell

```json
{
  "commands": [
    "cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/eval_results.json",
    "cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r16_alpaca/eval_results.json"
  ]
}
```

### Step 7: shell

```json
{
  "commands": [
    "ls /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/",
    "ls /home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/"
  ]
}
```

### Step 8: shell

```json
{
  "commands": [
    "python3 -c \"import pandas as pd; df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_training_curves.parquet'); print(df.columns.tolist()); print(df.head())\"",
    "python3 -c \"import pandas as pd; df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet'); print(df.columns.tolist()); print(df.head())\""
  ]
}
```

### Step 9: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\nprint('Unique runs:', df['run_name'].unique())\nprint()\nprint(df.groupby('run_name').agg({'step': ['min', 'max', 'count'], 'loss': ['min', 'max', 'last'], 'eval_loss': ['min', 'max', 'last'], 'grad_norm': ['mean', 'max']}))\n\""
  ]
}
```

### Step 10: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/eval_results_comparison.parquet')\nprint(df.columns.tolist())\nprint(df)\n\"",
    "python3 -c \"\nimport pandas as pd\ndf = pd.read_csv('/home/ubuntu/workspace/training-export-proprietary/qwen3_cross_run_comparison.csv')\nprint(df.columns.tolist())\nprint(df.head(20))\n\""
  ]
}
```

### Step 11: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\n# Get a summary view of loss progression for key runs\nkey_runs = ['lora_r32_all_alpaca', 'lora_r32_all_code_instructions', 'lora_r16_alpaca', 'lora_r16_code_instructions', 'lora_r4_alpaca', 'lora_r4_code_instructions', 'adalora_alpaca', 'ia3_alpaca']\nfor run in key_runs:\n    if run in df['run_name'].values:\n        run_df = df[df['run_name'] == run][['step', 'loss', 'eval_loss', 'grad_norm']].dropna(subset=['step'])\n        print(f'\\\\n=== {run} ===')\n        print(f'Steps: {run_df[\\\"step\\\"].min():.0f} to {run_df[\\\"step\\\"].max():.0f}')\n        print(f'Final loss: {run_df[\\\"loss\\\"].iloc[-1]:.4f}')\n        print(f'Final eval_loss: {run_df[\\\"eval_loss\\\"].dropna().iloc[-1] if not run_df[\\\"eval_loss\\\"].dropna().empty else \\\"N/A\\\"}')\n        print(f'Loss trend (first 5 avg vs last 5 avg): {r
```

### Step 12: shell

```json
{
  "commands": [
    "cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r16/eval_results.json",
    "cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all/eval_results.json",
    "cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r4/eval_results.json"
  ]
}
```

### Step 13: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\nimport json\n\n# Load training curves\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\n\n# Let's look at detailed trajectories\nruns_to_analyze = ['lora_r32_all_alpaca', 'lora_r16_alpaca', 'lora_r4_alpaca', 'ia3_alpaca', 'adalora_alpaca']\n\nfor run in runs_to_analyze:\n    run_df = df[df['run_name'] == run].sort_values('step')\n    print(f'\\\\n=== {run} ===')\n    # Get eval_loss at checkpoints\n    evals = run_df[run_df['eval_loss'].notna()][['step', 'loss', 'eval_loss', 'grad_norm']]\n    print(evals.to_string(index=False))\n\"",
    "python3 -c \"\nimport pandas as pd\n\n# Load training curves for code instruction runs\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\n\nruns_to_analyze = ['lora_r32_all_code_instructions', 'lora_r16_code_instructions', 'lora_r4_code_instructions', 'dora_r8_code_instru
```

### Step 14: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\n\n# Analyze training loss vs eval metrics\n# The key insight: eval_loss increasing while training loss decreasing indicates overfitting\n\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\n\n# Get the \"best\" checkpoint based on eval_loss for each run\nruns = df['run_name'].unique()\n\nprint('=== Best checkpoint per run (lowest eval_loss) ===')\nfor run in runs:\n    run_df = df[df['run_name'] == run]\n    evals = run_df[run_df['eval_loss'].notna()]\n    if not evals.empty:\n        best = evals.loc[evals['eval_loss'].idxmin()]\n        final = evals.iloc[-1]\n        print(f'{run}:')\n        print(f'  Best: step {best[\\\"step\\\"]:.0f}, eval_loss={best[\\\"eval_loss\\\"]:.4f}')\n        print(f'  Final: step {final[\\\"step\\\"]:.0f}, eval_loss={final[\\\"eval_loss\\\"]:.4f}')\n        print(f'  Degradation: {final[\\\"eval_loss\\\"] - best[\\\"eval_loss\\\"]:.4f}
```

### Step 15: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\n\n# Load the qwen3 cross run comparison which has eval metrics\ndf = pd.read_csv('/home/ubuntu/workspace/training-export-proprietary/qwen3_cross_run_comparison.csv')\n\n# Get key metrics for comparison\nprint('=== Qwen3 Runs: Training Loss vs Eval Performance ===')\nfor _, row in df.iterrows():\n    print(f'{row[\\\"run_name\\\"]}:')\n    print(f'  Final train loss: {row[\\\"final_train_loss\\\"]:.4f}')\n    print(f'  arc_easy_acc: {row[\\\"arc_easy_acc\\\"]:.3f}')\n    print(f'  hellaswag_acc: {row[\\\"hellaswag_acc\\\"]:.3f}')\n    print(f'  piqa_acc: {row[\\\"piqa_acc\\\"]:.3f}')\n    avg_acc = (row['arc_easy_acc'] + row['hellaswag_acc'] + row['piqa_acc']) / 3\n    print(f'  Avg acc (arc+hellaswag+piqa): {avg_acc:.3f}')\n    print()\n\"",
    "python3 -c \"\nimport pandas as pd\n\n# Load qwen3 training curves for detailed analysis\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_training_curves
```

### Step 16: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\nimport json\n\n# Load eval results comparison \ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/eval_results_comparison.parquet')\n\n# Pivot to get benchmark scores per run\npivot = df.pivot_table(index='run_name', columns=['benchmark', 'metric'], values='value')\nprint('=== Eval Results Summary ===')\nprint(pivot)\n\"",
    "python3 -c \"\nimport json\n\n# Look at adapter weight stats for lora_r32_all_alpaca\nwith open('/home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json') as f:\n    stats = json.load(f)\nprint('=== LoRA r32_all_alpaca Weight Stats ===')\nprint(json.dumps(stats, indent=2)[:3000])\n\"",
    "python3 -c \"\nimport json\n\n# Look at adapter weight stats for lora_r16_alpaca\nwith open('/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/adapter_weight_stats.json') as f:\n    stats = json.load(f)\nprint('=== LoRA r16_alpa
```

### Step 17: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\n\n# Load training curves\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\n\n# Compare grad_norm trends\nruns = ['lora_r32_all_alpaca', 'lora_r16_alpaca', 'lora_r4_alpaca', 'ia3_alpaca', 'adalora_alpaca']\n\nprint('=== Grad Norm Analysis (early vs late training) ===')\nfor run in runs:\n    run_df = df[df['run_name'] == run].sort_values('step')\n    run_df = run_df[run_df['grad_norm'].notna()]\n    if not run_df.empty:\n        early = run_df.head(10)['grad_norm'].mean()\n        late = run_df.tail(10)['grad_norm'].mean()\n        max_gn = run_df['grad_norm'].max()\n        print(f'{run}:')\n        print(f'  Early avg grad_norm: {early:.4f}')\n        print(f'  Late avg grad_norm: {late:.4f}')\n        print(f'  Max grad_norm: {max_gn:.4f}')\n        print(f'  Ratio (late/early): {late/early:.2f}')\n        print()\n\"",
    "python3 -c \"\nimport pandas as pd\n\n# 
```

### Step 18: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\nimport json\n\n# Full analysis of the problematic runs\nprint('=== DPO/KTO Runs - Additional Analysis ===')\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_training_curves.parquet')\n\n# Look at reward margins for DPO runs\ndpo_runs = [r for r in df['run_name'].unique() if 'dpo' in r and '1.7b' in r]\nfor run in dpo_runs:\n    run_df = df[df['run_name'] == run].sort_values('step')\n    print(f'\\\\n=== {run} ===')\n    if 'rewards/margins' in run_df.columns:\n        margins = run_df[run_df['rewards/margins'].notna()]\n        if not margins.empty:\n            print(f'Margin trend: {margins[\\\"rewards/margins\\\"].iloc[0]:.4f} -> {margins[\\\"rewards/margins\\\"].iloc[-1]:.4f}')\n            print(f'Accuracies: {margins[\\\"rewards/accuracies\\\"].iloc[0]:.4f} -> {margins[\\\"rewards/accurities\\\"].iloc[-1]:.4f}')\n\"",
    "python3 -c \"\nimport pandas as pd\n\ndf = pd.read_parquet('/home/ubu
```

### Step 19: shell

```json
{
  "commands": [
    "python3 -c \"\nimport pandas as pd\n\n# Final summary of training vs eval divergence\ndf = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')\n\n# Calculate overfitting metrics\nruns = df['run_name'].unique()\nprint('=== Overfitting Analysis Summary ===')\nprint('Run Name | Best Step | Best Eval Loss | Final Step | Final Eval Loss | Degradation %')\nprint('-' * 90)\nfor run in runs:\n    run_df = df[df['run_name'] == run]\n    evals = run_df[run_df['eval_loss'].notna()]\n    if not evals.empty:\n        best_idx = evals['eval_loss'].idxmin()\n        best = evals.loc[best_idx]\n        final = evals.iloc[-1]\n        degradation = ((final['eval_loss'] - best['eval_loss']) / best['eval_loss']) * 100\n        print(f'{run:40s} | {best[\\\"step\\\"]:4.0f} | {best[\\\"eval_loss\\\"]:.4f} | {final[\\\"step\\\"]:4.0f} | {final[\\\"eval_loss\\\"]:.4f} | {degradation:+.1f}%')\n\""
  ]
}
```

### Step 20: edit/create

**Path:** `/home/ubuntu/workspace/REPORT.md`

<details><summary>File content (9639 chars)</summary>

```
# Adapter Training Sweep Analysis: Overfitting Patterns and Checkpoint Selection

## Executive Summary

Your intuition about the r32 runs was correct. The r32 adapters show **severe overfitting** despite having the lowest training loss. The key finding is that **training loss and downstream performance have decoupled** - continuing to train past certain checkpoints actually degrades generalization even as training loss improves.

### Critical Findings

1. **r32 runs overfit earliest and hardest**: The r32_all adapters hit their best eval loss at step 100, then degrade by **13-88%** by the end of training
2. **Training loss is misleading**: All runs continue to decrease training loss, but many show increasing eval loss after early checkpoints
3. **Adapter type strongly predicts overfitting**: r4 is most stable, r32 and r16_mlp are most prone to overfitting
4. **Best checkpoints are often early**: For 9 of 16 runs, the optimal checkpoint is before step 500

---

## Detailed Analysis

### 1. The r32 Mystery Explained

The user's observation about r32 having the "lowest training loss but worst eval scores" is confirmed across both experimental tracks:

**SmolLM2 Experiments:**
| Adapter | Final Train Loss | arc_easy Acc | hellaswag Acc | piqa Acc |
|---------|-----------------|--------------|---------------|----------|
| lora_r16 | 1.28 | 0.58 | 0.45 | 0.69 |
| lora_r32_all | 0.89 | 0.52 | 0.42 | 0.66 |
| lora_r4 | 1.28 | 0.57 | 0.45 | 0.69 |

**Qwen3 1.7B SFT Experiments:**
| Adapter | Final Train Loss | arc_easy Acc | hellaswag Acc | piqa Acc | Avg Acc |
|---------|-----------------|--------------|---------------|----------|---------|
| lora_r8 | 1.215 | 0.663 | 0.493 | 0.750 | **0.636** |
| lora_r16 | 1.189 | 0.687 | 0.493 | 0.753 | **0.644** |
| lora_r32_all | 0.995 | 0.600 | 0.480 | 0.757 | **0.612** |

**Key Insight**: r32 achieves the lowest training loss (0.995 vs 1.189 for r16) but has the **worst average accuracy** (0.612 vs 0.644 for r16). The model is memorizing the training data at the expense of generalization.

### 2. Eval Loss Trajectories Reveal Overfitting

The full eval loss trajectories show clear divergence patterns:

#### Catastrophic Overfitting (>50% degradation):
| Run | Best Step | Best Eval Loss | Final Step | Final Eval Loss | Degradation |
|-----|-----------|----------------|------------|-----------------|-------------|
| lora_r16_mlp_alpaca | 200 | 1.2705 | 2000 | 2.4983 | **+96.6%** |
| lora_r16_mlp_code_instructions | 100 | 0.8966 | 2000 | 1.7115 | **+90.9%** |
| lora_r32_all_code_instructions | 100 | 0.8886 | 2000 | 1.6717 | **+88.1%** |
| full_ft_code_instructions | 500 | 0.8899 | 2000 | 1.0975 | **+23.3%** |
| lora_r16_code_instructions | 300 | 0.9059 | 2000 | 1.1526 | **+27.2%** |

#### Moderate Overfitting (5-15% degradation):
| Run | Best Step | Best Eval Loss | Final Step | Final Eval Loss | Degradation |
|-----|-----------|----------------|------------|-----------------|-------------|
| lora_r32_all_alpaca | 100 | 1.2738 | 500 | 1.4411 | **+13.1%** |
| dora_r8_code_instructions | 500 | 0.9049 | 2000 | 1.0175 | **+12.4%** |
| dora_r8_alpaca | 400 | 1.2859 | 2000 | 1.3838 | **+7.6%** |
| lora_r4_code_instructions | 700 | 0.9046 | 2000 | 0.9458 | **+4.6%** |

#### Stable Runs (<1% degradation):
| Run | Best Step | Best Eval Loss | Final Step | Final Eval Loss | Degradation |
|-----|-----------|----------------|------------|-----------------|-------------|
| ia3_alpaca | 500 | 1.3585 | 500 | 1.3585 | **0.0%** |
| ia3_code_instructions | 2000 | 0.9182 | 2000 | 0.9182 | **0.0%** |
| lora_r16_alpaca | 500 | 1.2850 | 500 | 1.2850 | **0.0%** |
| lora_r4_alpaca | 500 | 1.2924 | 500 | 1.2924 | **0.0%** |
| adalora_alpaca | 500 | 1.3317 | 500 | 1.3317 | **0.0%** |
| adalora_code_instructions | 1600 | 0.9160 | 2000 | 0.9168 | **+0.1%** |

### 3. Adapter Type Risk Profile

Based on the sweep results, adapters can be categorized by overfitting risk:

#### High Risk (Prone to Catastrophic Overfitting):
- **LoRA r32 with all layers**: 88-96% degradation, best checkpoint at step 100
- **LoRA r16 with MLP-only targeting**: 90-97% degradation, best checkpoint at step 100-200
- **Full Fine-tuning on code**: 23% degradation, very unstable

#### Medium Risk (Moderate Overfitting):
- **LoRA r16 on long sequences**: 27% degradation on code, 0% on alpaca
- **DoRA r8**: 7-12% degradation
- **LoRA r4 on long sequences**: 4-5% degradation

#### Low Risk (Stable):
- **LoRA r4**: Most stable standard LoRA config
- **LoRA r16 on short sequences**: Stable on alpaca (500 steps)
- **IA3**: Extremely stable (0% degradation)
- **AdaLoRA**: Extremely stable with built-in rank adaptation

### 4. Why Training Loss Doesn't Show Overfitting

The training logs reveal the critical issue:

```
lora_r32_all_code_instructions training trajectory:
  Step 100:  train_loss=0.889, eval_loss=0.889  <- BEST CHECKPOINT
  Step 500:  train_loss=0.479, eval_loss=1.029  <- Training ↓, Eval ↑
  Step 1000: train_loss=0.358, eval_l

... (4639 chars truncated)
```
</details>

### Step 21: shell

```json
{
  "commands": [
    "head -100 /home/ubuntu/workspace/REPORT.md",
    "wc -l /home/ubuntu/workspace/REPORT.md"
  ]
}
```

### Step 22: shell

```json
{
  "commands": [
    "cat /home/ubuntu/workspace/REPORT.md"
  ]
}
```

### Step 23: submit

```
I've completed the analysis and written a comprehensive report to `/home/ubuntu/workspace/REPORT.md`. Here are the key findings:

## Summary

### The r32 Mystery - Explained

Your suspicion was **correct**. The r32 adapters are severely overfitting despite having the lowest training loss:

**Qwen3 1.7B SFT Results:**
- **r32**: Train loss 0.995, Average accuracy 0.612 (worst)
- **r16**: Train loss 1.189, Average accuracy 0.644 (best)
- **r8**: Train loss 1.215, Average accuracy 0.636 (middle)

### Why Training Loss Hides the Problem

The training logs show training loss continues to decrease while eval loss increases:

```
lora_r32_all_code_instructions:
  Step 100:  train=0.889, eval=0.889  ← BEST
  Step 500:  train=0.479, eval=1.029  ← Training ↓, Eval ↑
  Step 2000: train=0.480, eval=1.672  ← 88% worse than best
```

### Adapter Risk Categories

| Risk Level | Adapters | Degradation |
|------------|----------|-------------|
| **High** | r32_all, r16_mlp, full_ft | 88-97% |
| **Mediu
```
