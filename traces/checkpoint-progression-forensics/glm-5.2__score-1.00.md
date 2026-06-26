# glm-5.2 on Checkpoint Progression Forensics

**Score:** 1.00
**Tool calls:** 84
**Duration:** 20.5 min
**Trace ID:** `23f51756-a58a-46ca-b0fd-a65176f6046b`

---

## Trajectory

### Step 1: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/
```

<details><summary>Output (286 chars)</summary>

```
cross_adapter_comparison.parquet
datasets
eval_results_comparison.parquet
evaluations
experiment_metadata.json
experiment_metadata_v2.json
generations
qwen3_cross_run_comparison.csv
qwen3_cross_run_comparison.parquet
qwen3_training_curves.parquet
runs
training_curves_comparison.parquet
```
</details>

### Step 2: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/runs/ 2>/dev/null
```

<details><summary>Output (889 chars)</summary>

```
adalora_alpaca
adalora_code_instructions
dora_r8_alpaca
dora_r8_code_instructions
full_ft_alpaca
full_ft_code_instructions
ia3_alpaca
ia3_code_instructions
lora_r16_alpaca
lora_r16_code_instructions
lora_r16_mlp_alpaca
lora_r16_mlp_code_instructions
lora_r32_all_alpaca
lora_r32_all_code_instructions
lora_r4_alpaca
lora_r4_code_instructions
qwen3_dpo_b01_lora_r16_qwen3-0.6b
qwen3_dpo_b01_lora_r16_qwen3-1.7b
qwen3_dpo_b01_lora_r32_all_qwen3-1.7b
qwen3_dpo_b01_lora_r8_qwen3-1.7b
qwen3_dpo_b05_lora_r16_qwen3-1.7b
qwen3_dpo_b05_lora_r32_all_qwen3-1.7b
qwen3_dpo_b05_lora_r8_qwen3-1.7b
qwen3_kto_lora_r16_qwen3-1.7b
qwen3_kto_lora_r8_qwen3-1.7b
qwen3_sft_dora_r16_qwen3-1.7b
qwen3_sft_full_ft_qwen3-1.7b
qwen3_sft_lora_r16_qwen3-0.6b
qwen3_sft_lora_r16_qwen3-1.7b
qwen3_sft_lora_r32_all_qwen3-0.6b
qwen3_sft_lora_r32_all_qwen3-1.7b
qwen3_sft_lora_r8_qwen3-0.6b
qwen3_sft_lora_r8_qwen3-1.7b
```
</details>

### Step 3: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/ 2>/dev/null
```

<details><summary>Output (856 chars)</summary>

```
adalora
adalora_alpaca
adalora_code_instructions
dora_r8_alpaca
dora_r8_code_instructions
ia3
ia3_alpaca
ia3_code_instructions
lora_r16
lora_r16_alpaca
lora_r16_code_instructions
lora_r16_mlp_alpaca
lora_r16_mlp_code_instructions
lora_r32_all
lora_r32_all_alpaca
lora_r32_all_code_instructions
lora_r4
lora_r4_alpaca
lora_r4_code_instructions
qwen3_dpo_b01_lora_r16_qwen3-0.6b
qwen3_dpo_b01_lora_r32_all_qwen3-1.7b
qwen3_dpo_b01_lora_r8_qwen3-1.7b
qwen3_dpo_b05_lora_r16_qwen3-1.7b
qwen3_dpo_b05_lora_r32_all_qwen3-1.7b
qwen3_dpo_b05_lora_r8_qwen3-1.7b
qwen3_kto_lora_r16_qwen3-1.7b
qwen3_kto_lora_r8_qwen3-1.7b
qwen3_sft_dora_r16_qwen3-1.7b
qwen3_sft_full_ft_qwen3-1.7b
qwen3_sft_lora_r16_qwen3-0.6b
qwen3_sft_lora_r16_qwen3-1.7b
qwen3_sft_lora_r32_all_qwen3-0.6b
qwen3_sft_lora_r32_all_qwen3-1.7b
qwen3_sft_lora_r8_qwen3-0.6b
qwen3_sft_lora_r8_qwen3-1.7b
```
</details>

### Step 4: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/
```

<details><summary>Output (587 chars)</summary>

```
total 192
drwxr-xr-x.  4 ubuntu ubuntu    187 Jun 25 17:21 .
drwxr-xr-x. 35 ubuntu ubuntu  16384 Jun 25 17:21 ..
-rw-r--r--.  1 ubuntu ubuntu   1104 Jun 25 17:21 adapter_config.json
-rw-r--r--.  1 ubuntu ubuntu 160716 Jun 25 17:21 adapter_weight_stats.json
drwxr-xr-x.  2 ubuntu ubuntu     50 Jun 25 17:21 adapter_weights
drwxr-xr-x.  7 ubuntu ubuntu    116 Jun 25 17:21 checkpoints
-rw-r--r--.  1 ubuntu ubuntu    155 Jun 25 17:21 memory_profile.json
-rw-r--r--.  1 ubuntu ubuntu    580 Jun 25 17:21 training_config.json
-rw-r--r--.  1 ubuntu ubuntu   3594 Jun 25 17:21 training_log.csv
```
</details>

### Step 5: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r4_alpaca/
```

<details><summary>Output (577 chars)</summary>

```
total 76
drwxr-xr-x.  4 ubuntu ubuntu   187 Jun 25 17:21 .
drwxr-xr-x. 35 ubuntu ubuntu 16384 Jun 25 17:21 ..
-rw-r--r--.  1 ubuntu ubuntu  1026 Jun 25 17:21 adapter_config.json
-rw-r--r--.  1 ubuntu ubuntu 44663 Jun 25 17:21 adapter_weight_stats.json
drwxr-xr-x.  2 ubuntu ubuntu    50 Jun 25 17:21 adapter_weights
drwxr-xr-x.  7 ubuntu ubuntu   116 Jun 25 17:21 checkpoints
-rw-r--r--.  1 ubuntu ubuntu   153 Jun 25 17:21 memory_profile.json
-rw-r--r--.  1 ubuntu ubuntu   598 Jun 25 17:21 training_config.json
-rw-r--r--.  1 ubuntu ubuntu  3606 Jun 25 17:21 training_log.csv
```
</details>

### Step 6: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/experiment_metadata.json | python3 -m json.tool | head -80
```

<details><summary>Output (411 chars)</summary>

```
{
    "base_model": "HuggingFaceTB/SmolLM2-135M",
    "adapters": [
        "lora_r4",
        "lora_r16",
        "lora_r32_all",
        "ia3",
        "adalora",
        "full_ft",
        "dora_r8",
        "lora_r16_mlp"
    ],
    "datasets": [
        "alpaca",
        "code_instructions"
    ],
    "max_steps_v1": 500,
    "max_steps_v2": 2000,
    "generated_at": "2026-05-13T03:09:01.202947+00:00"
}
```
</details>

### Step 7: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/
```

<details><summary>Output (402 chars)</summary>

```
total 0
drwxr-xr-x. 7 ubuntu ubuntu 116 Jun 25 17:21 .
drwxr-xr-x. 4 ubuntu ubuntu 187 Jun 25 17:21 ..
drwxr-xr-x. 2 ubuntu ubuntu 127 Jun 25 17:21 checkpoint-100
drwxr-xr-x. 2 ubuntu ubuntu 127 Jun 25 17:21 checkpoint-200
drwxr-xr-x. 2 ubuntu ubuntu 127 Jun 25 17:21 checkpoint-300
drwxr-xr-x. 2 ubuntu ubuntu 127 Jun 25 17:21 checkpoint-400
drwxr-xr-x. 2 ubuntu ubuntu 127 Jun 25 17:21 checkpoint-500
```
</details>

### Step 8: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/training_log.csv
```

<details><summary>Output (3593 chars)</summary>

```
step,loss,eval_loss,learning_rate,epoch,grad_norm
10,1.6788902282714844,,0.000491,0.08,0.7385956645011902
20,1.454610538482666,,0.000481,0.16,0.6349031925201416
30,1.3632939338684082,,0.000471,0.24,0.4665580689907074
40,1.3339543342590332,,0.00046100000000000004,0.32,0.48834550380706787
50,1.2900101661682128,,0.000451,0.4,0.42039546370506287
50,1.2900347709655762,1.2900347709655762,,0.4,
60,1.2384940147399903,,0.000441,0.48,0.4460912346839905
70,1.3020501136779785,,0.000431,0.56,0.4370357394218445
80,1.2247851371765137,,0.000421,0.64,0.41069552302360535
90,1.2350358963012695,,0.00041099999999999996,0.72,0.43958938121795654
100,1.3254374504089355,,0.00040100000000000004,0.8,0.476042240858078
100,1.2738009691238403,1.2738009691238403,,0.8,
110,1.3011079788208009,,0.000391,0.88,0.5789756774902344
120,1.3478520393371582,,0.000381,0.96,0.3788187503814697
130,1.1306018829345703,,0.000371,1.04,0.39384159445762634
140,1.0384330749511719,,0.000361,1.12,0.4341002106666565
150,1.0241544723510743,,0.00035099999999999997,1.2,0.4614233374595642
150,1.2815436124801636,1.2815436124801636,,1.2,
160,0.9399290084838867,,0.00034100000000000005,1.28,0.4648011326789856
170,1.0596712112426758,,0.000331,1.3599999999999999,0.4287526309490204
180,1.036385440826416,,0.000321,1.44,0.5497750639915466
190,1.0680524826049804,,0.000311,1.52,0.5345572829246521
200,1.0837188720703126,,0.000301,1.6,0.4842652678489685
200,1.278459906578064,1.278459906578064,,1.6,
210,1.2111722946166992,,0.00029099999999999997,1.6800000000000002,0.513154149055481
220,1.090952491760254,,0.00028100000000000005,1.76,0.5360168814659119
230,1.0545432090759277,,0.00027100000000000003,1.8399999999999999,0.5167524218559265
240,0.9553266525268554,,0.000261,1.92,0.6017215847969055
250,1.0817943572998048,,0.00025100000000000003,2.0,0.492512047290802
250,1.2794697284698486,1.2794697284698486,,2.0,
260,0.9003968238830566,,0.000241,2.08,0.4205358326435089
270,0.9484155654907227,,0.000231,2.16,0.7089089751243591
280,0.8247574806213379,,0.000221,2.24,0.6251868009567261
290,0.8445838928222656,,0.000211,2.32,0.4967370927333832
300,0.8347192764282226,,0.000201,2.4,0.5420322418212891
300,1.3487833738327026,1.3487833738327026,,2.4,
310,0.9789088249206543,,0.000191,2.48,0.6434655785560608
320,0.8358834266662598,,0.000181,2.56,0.6171281933784485
330,0.8946387290954589,,0.000171,2.64,0.5716249942779541
340,0.770601224899292,,0.000161,2.7199999999999998,0.5906839966773987
350,0.8676647186279297,,0.000151,2.8,0.48331063985824585
350,1.3514587879180908,1.3514587879180908,,2.8,
360,0.8320070266723633,,0.00014099999999999998,2.88,0.6528721451759338
370,0.8447301864624024,,0.000131,2.96,0.5934861302375793
380,0.7062413215637207,,0.000121,3.04,0.4907662868499756
390,0.6500791072845459,,0.000111,3.12,0.48673659563064575
400,0.6877048015594482,,0.000101,3.2,0.5416309833526611
400,1.4348132610321045,1.4348132610321045,,3.2,
410,0.5939682960510254,,9.1e-05,3.2800000000000002,0.5395511984825134
420,0.6863453388214111,,8.1e-05,3.36,0.6360337734222412
430,0.6872247695922852,,7.099999999999999e-05,3.44,0.7402626276016235
440,0.7443608283996582,,6.1e-05,3.52,0.7384811043739319
450,0.660958194732666,,5.1e-05,3.6,0.7115420699119568
450,1.4450159072875977,1.4450159072875977,,3.6,
460,0.7305331707000733,,4.1e-05,3.68,0.6265407800674438
470,0.6537210464477539,,3.1e-05,3.76,0.6096587181091309
480,0.6814323902130127,,2.1000000000000002e-05,3.84,0.6022178530693054
490,0.7454281330108643,,1.1e-05,3.92,0.6387237310409546
500,0.682561206817627,,1e-06,4.0,0.566798985004425
500,1.4411063194274902,1.4411063194274902,,4.0,
500,,,,4.0,
```
</details>

### Step 9: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/training_config.json
```

<details><summary>Output (580 chars)</summary>

```
{
  "adapter_name": "lora_r32_all",
  "adapter_config": {
    "type": "lora",
    "r": 32,
    "lora_alpha": 64,
    "target_modules": "all-linear",
    "lora_dropout": 0.1
  },
  "base_model": "HuggingFaceTB/SmolLM2-135M",
  "dataset": "alpaca",
  "training_args": {
    "max_steps": 500,
    "batch_size": 4,
    "learning_rate": 0.0005,
    "weight_decay": 0.01,
    "seed": 42
  },
  "results": {
    "trainable_params": 9768960,
    "total_params": 144283968,
    "adapter_overhead_pct": 6.7706,
    "elapsed_seconds": 795.54,
    "final_train_loss": 0.9831624612808227
  }
}
```
</details>

### Step 10: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/checkpoint-100/
```

<details><summary>Output (444 chars)</summary>

```
total 3464
drwxr-xr-x. 2 ubuntu ubuntu     127 Jun 25 17:21 .
drwxr-xr-x. 7 ubuntu ubuntu     116 Jun 25 17:21 ..
-rw-r--r--. 1 ubuntu ubuntu    5206 Jun 25 17:21 README.md
-rw-r--r--. 1 ubuntu ubuntu    1104 Jun 25 17:21 adapter_config.json
-rw-r--r--. 1 ubuntu ubuntu 3523144 Jun 25 17:21 tokenizer.json
-rw-r--r--. 1 ubuntu ubuntu     775 Jun 25 17:21 tokenizer_config.json
-rw-r--r--. 1 ubuntu ubuntu    2775 Jun 25 17:21 trainer_state.json
```
</details>

### Step 11: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/checkpoint-500/
```

<details><summary>Output (444 chars)</summary>

```
total 3472
drwxr-xr-x. 2 ubuntu ubuntu     127 Jun 25 17:21 .
drwxr-xr-x. 7 ubuntu ubuntu     116 Jun 25 17:21 ..
-rw-r--r--. 1 ubuntu ubuntu    5206 Jun 25 17:21 README.md
-rw-r--r--. 1 ubuntu ubuntu    1104 Jun 25 17:21 adapter_config.json
-rw-r--r--. 1 ubuntu ubuntu 3523144 Jun 25 17:21 tokenizer.json
-rw-r--r--. 1 ubuntu ubuntu     775 Jun 25 17:21 tokenizer_config.json
-rw-r--r--. 1 ubuntu ubuntu   10845 Jun 25 17:21 trainer_state.json
```
</details>

### Step 12: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/
```

<details><summary>Output (536 chars)</summary>

```
total 1772
drwxr-xr-x.  2 ubuntu ubuntu    177 Jun 25 17:21 .
drwxr-xr-x. 37 ubuntu ubuntu  16384 Jun 25 17:21 ..
-rw-r--r--.  1 ubuntu ubuntu   1364 Jun 25 17:21 eval_results.json
-rw-r--r--.  1 ubuntu ubuntu 335839 Jun 25 17:21 samples_arc_easy.jsonl
-rw-r--r--.  1 ubuntu ubuntu 512618 Jun 25 17:21 samples_boolq.jsonl
-rw-r--r--.  1 ubuntu ubuntu 518908 Jun 25 17:21 samples_hellaswag.jsonl
-rw-r--r--.  1 ubuntu ubuntu 229722 Jun 25 17:21 samples_piqa.jsonl
-rw-r--r--.  1 ubuntu ubuntu 185966 Jun 25 17:21 samples_winogrande.jsonl
```
</details>

### Step 13: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/checkpoint-100/trainer_state.json | python3 -m json.tool
```

<details><summary>Output (3352 chars)</summary>

```
{
    "best_global_step": null,
    "best_metric": null,
    "best_model_checkpoint": null,
    "epoch": 0.8,
    "eval_steps": 50,
    "global_step": 100,
    "is_hyper_param_search": false,
    "is_local_process_zero": true,
    "is_world_process_zero": true,
    "log_history": [
        {
            "epoch": 0.08,
            "grad_norm": 0.7385956645011902,
            "learning_rate": 0.000491,
            "loss": 1.6788902282714844,
            "step": 10
        },
        {
            "epoch": 0.16,
            "grad_norm": 0.6349031925201416,
            "learning_rate": 0.000481,
            "loss": 1.454610538482666,
            "step": 20
        },
        {
            "epoch": 0.24,
            "grad_norm": 0.4665580689907074,
            "learning_rate": 0.000471,
            "loss": 1.3632939338684082,
            "step": 30
        },
        {
            "epoch": 0.32,
            "grad_norm": 0.48834550380706787,
            "learning_rate": 0.00046100000000000004,
            "loss": 1.3339543342590332,
            "step": 40
        },
        {
            "epoch": 0.4,
            "grad_norm": 0.42039546370506287,
            "learning_rate": 0.000451,
            "loss": 1.2900101661682128,
            "step": 50
        },
        {
            "epoch": 0.4,
            "eval_loss": 1.2900347709655762,
            "eval_runtime": 7.8906,
            "eval_samples_per_second": 6.337,
            "eval_steps_per_second": 1.648,
            "step": 50
        },
        {
            "epoch": 0.48,
            "grad_norm": 0.4460912346839905,
            "learning_rate": 0.000441,
            "loss": 1.2384940147399903,
            "step": 60
        },
        {
            "epoch": 0.56,
            "grad_norm": 0.4370357394218445,
            "learning_rate": 0.000431,
            "loss": 1.3020501136779785,
            "step": 70
        },
        {
            "epoch": 0.64,
            "grad_norm": 0.41069552302360535,
            "learning_rate": 0.000421,
            "loss": 1.2247851371765137,
            "step": 80
        },
        {
            "epoch": 0.72,
            "grad_norm": 0.43958938121795654,
            "learning_rate": 0.00041099999999999996,
            "loss": 1.2350358963012695,
            "step": 90
        },
        {
            "epoch": 0.8,
            "grad_norm": 0.476042240858078,
            "learning_rate": 0.00040100000000000004,
            "loss": 1.3254374504089355,
            "step": 100
        },
        {
            "epoch": 0.8,
            "eval_loss": 1.2738009691238403,
            "eval_runtime": 8.6344,
            "eval_samples_per_second": 5.791,
            "eval_steps_per_second": 1.506,
            "step": 100
        }
    ],
    "logging_steps": 10,
    "max_steps": 500,
    "num_input_tokens_seen": 0,
    "num_train_epochs": 4,
    "save_steps": 100,
    "stateful_callbacks": {
        "TrainerControl": {
            "args": {
                "should_epoch_stop": false,
                "should_evaluate": false,
                "should_log": false,
                "should_save": true,
                "should_training_stop": false
            },
            "attributes": {}
        }
    },
    "total_flos": 71253452390400.0,
    "train_batch_size": 4,
    "trial_name": null,
    "trial_params": null
}
```
</details>

### Step 14: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/eval_results.json | python3 -m json.tool
```

<details><summary>Output (1626 chars)</summary>

```
{
    "adapter": "lora_r32_all_alpaca",
    "base_model": "HuggingFaceTB/SmolLM2-135M",
    "benchmarks": [
        "arc_easy",
        "hellaswag",
        "piqa",
        "winogrande",
        "boolq"
    ],
    "limit": 200,
    "results": {
        "arc_easy": {
            "name": "arc_easy",
            "alias": "arc_easy",
            "sample_len": 200,
            "acc,none": 0.51,
            "acc_stderr,none": 0.035436970729343674,
            "acc_norm,none": 0.545,
            "acc_norm_stderr,none": 0.035300219937532865
        },
        "hellaswag": {
            "name": "hellaswag",
            "alias": "hellaswag",
            "sample_len": 200,
            "acc,none": 0.45,
            "acc_stderr,none": 0.03526639466921486,
            "acc_norm,none": 0.49,
            "acc_norm_stderr,none": 0.035436970729343674
        },
        "piqa": {
            "name": "piqa",
            "alias": "piqa",
            "sample_len": 200,
            "acc,none": 0.665,
            "acc_stderr,none": 0.033458517029435815,
            "acc_norm,none": 0.695,
            "acc_norm_stderr,none": 0.032637417254205714
        },
        "winogrande": {
            "name": "winogrande",
            "alias": "winogrande",
            "sample_len": 200,
            "acc,none": 0.54,
            "acc_stderr,none": 0.03533045720097816
        },
        "boolq": {
            "name": "boolq",
            "alias": "boolq",
            "sample_len": 200,
            "acc,none": 0.61,
            "acc_stderr,none": 0.03457567623250012
        }
    },
    "timestamp": "2026-05-13T03:04:02.306948+00:00"
}
```
</details>

### Step 15: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/checkpoint-500/trainer_state.json | python3 -m json.tool
```

<details><summary>Output (13294 chars)</summary>

```
{
    "best_global_step": null,
    "best_metric": null,
    "best_model_checkpoint": null,
    "epoch": 4.0,
    "eval_steps": 50,
    "global_step": 500,
    "is_hyper_param_search": false,
    "is_local_process_zero": true,
    "is_world_process_zero": true,
    "log_history": [
        {
            "epoch": 0.08,
            "grad_norm": 0.7385956645011902,
            "learning_rate": 0.000491,
            "loss": 1.6788902282714844,
            "step": 10
        },
        {
            "epoch": 0.16,
            "grad_norm": 0.6349031925201416,
            "learning_rate": 0.000481,
            "loss": 1.454610538482666,
            "step": 20
        },
        {
            "epoch": 0.24,
            "grad_norm": 0.4665580689907074,
            "learning_rate": 0.000471,
            "loss": 1.3632939338684082,
            "step": 30
        },
        {
            "epoch": 0.32,
            "grad_norm": 0.48834550380706787,
            "learning_rate": 0.00046100000000000004,
            "loss": 1.3339543342590332,
            "step": 40
        },
        {
            "epoch": 0.4,
            "grad_norm": 0.42039546370506287,
            "learning_rate": 0.000451,
            "loss": 1.2900101661682128,
            "step": 50
        },
        {
            "epoch": 0.4,
            "eval_loss": 1.2900347709655762,
            "eval_runtime": 7.8906,
            "eval_samples_per_second": 6.337,
            "eval_steps_per_second": 1.648,
            "step": 50
        },
        {
            "epoch": 0.48,
            "grad_norm": 0.4460912346839905,
            "learning_rate": 0.000441,
            "loss": 1.2384940147399903,
            "step": 60
        },
        {
            "epoch": 0.56,
            "grad_norm": 0.4370357394218445,
            "learning_rate": 0.000431,
            "loss": 1.3020501136779785,
            "step": 70
        },
        {
            "epoch": 0.64,
            "grad_norm": 0.41069552302360535,
            "learning_rate": 0.000421,
            "loss": 1.2247851371765137,
            "step": 80
        },
        {
            "epoch": 0.72,
            "grad_norm": 0.43958938121795654,
            "learning_rate": 0.00041099999999999996,
            "loss": 1.2350358963012695,
            "step": 90
        },
        {
            "epoch": 0.8,
            "grad_norm": 0.476042240858078,
            "learning_rate": 0.00040100000000000004,
            "loss": 1.3254374504089355,
            "step": 100
        },
        {
            "epoch": 0.8,
            "eval_loss": 1.2738009691238403,
            "eval_runtime": 8.6344,
            "eval_samples_per_second": 5.791,
            "eval_steps_per_second": 1.506,
            "step": 100
        },
        {
            "epoch": 0.88,
            "grad_norm": 0.5789756774902344,
            "learning_rate": 0.000391,
            "loss": 1.3011079788208009,
            "step": 110
        },
        {
            "epoch": 0.96,
            "grad_norm": 0.3788187503814697,
            "learning_rate": 0.000381,
            "loss": 1.3478520393371582,
            "step": 120
        },
        {
            "epoch": 1.04,
            "grad_norm": 0.39384159445762634,
            "learning_rate": 0.000371,
            "loss": 1.1306018829345703,
            "step": 130
        },
        {
            "epoch": 1.12,
            "grad_norm": 0.4341002106666565,
            "learning_rate": 0.000361,
            "loss": 1.0384330749511719,
            "step": 140
        },
        {
            "epoch": 1.2,
            "grad_norm": 0.4614233374595642,
            "learning_rate": 0.00035099999999999997,
            "loss": 1.0241544723510743,
            "step": 150
        },
        {
            "epoch": 1.2,
            "eval_loss": 1.2815436124801636,
            "eval_runtime": 8.5828,
            "eval_samples_per_second": 5.826,
            "eval_steps_per_second": 1.515,
            "step": 150
        },
        {
            "epoch": 1.28,
            "grad_norm": 0.4648011326789856,
            "learning_rate": 0.00034100000000000005,
            "loss": 0.9399290084838867,
            "step": 160
        },
        {
            "epoch": 1.3599999999999999,
            "grad_norm": 0.4287526309490204,
            "learning_rate": 0.000331,
            "loss": 1.0596712112426758,
            "step": 170
        },
        {
            "epoch": 1.44,
            "grad_norm": 0.5497750639915466,
            "learning_rate": 0.000321,
            "loss": 1.036385440826416,
            "step": 180
        },
        {
            "epoch": 1.52,
            "grad_norm": 0.5345572829246521,
            "learning_rate": 0.000311,
            "loss": 1.0680524826049804,
            "step": 190
        },
        {
            "epoch": 1.6,
            "grad_norm": 0.4842652678489685,
            "learning_rate": 0.000301,
            "loss": 1.0837188720703126,
            "step": 200
        },
        {
            "epoch": 1.6,
            "eval_loss": 1.278459906578064,
            "eval_runtime": 8.1,
            "eval_samples_per_second": 6.173,
            "eval_steps_per_second": 1.605,
            "step": 200
        },
        {
            "epoch": 1.6800000000000002,
            "grad_norm": 0.513154149055481,
            "learning_rate": 0.00029099999999999997,
            "loss": 1.2111722946166992,
            "step": 210
        },
        {
            "epoch": 1.76,
            "grad_norm": 0.5360168814659119,
            "learning_rate": 0.00028100000000000005,
            "loss": 1.090952491760254,
            "step": 220
        },
        {
            "epoch": 1.8399999999999999,
            "grad_norm": 0.5167524218559265,
            "learning_rate": 0.00027100000000000003,
            "loss": 1.0545432090759277,
            "step": 230
        },
        {
            "epoch": 1.92,
            "grad_norm": 0.6017215847969055,
            "learning_rate": 0.000261,
            "loss": 0.9553266525268554,
            "step": 240
        },
        {
            "epoch": 2.0,
            "grad_norm": 0.492512047290802,
            "learning_rate": 0.00025100000000000003,
            "loss": 1.0817943572998048,
            "step": 250
        },
        {
            "epoch": 2.0,
            "eval_loss": 1.2794697284698486,
            "eval_runtime": 8.5082,
            "eval_samples_per_second": 5.877,
            "eval_steps_per_second": 1.528,
            "step": 250
        },
        {
            "epoch": 2.08,
            "grad_norm": 0.4205358326435089,
            "learning_rate": 0.000241,
            "loss": 0.9003968238830566,
            "step": 260
        },
        {
            "epoch": 2.16,
            "grad_norm": 0.7089089751243591,
            "learning_rate": 0.000231,
            "loss": 0.9484155654907227,
            "step": 270
        },
        {
            "epoch": 2.24,
            "grad_norm": 0.6251868009567261,
            "learning_rate": 0.000221,
            "loss": 0.8247574806213379,
            "step": 280
        },
        {
            "epoch": 2.32,
            "grad_norm": 0.4967370927333832,
            "learning_rate": 0.000211,
            "loss": 0.8445838928222656,
            "step": 290
        },
        {
            "epoch": 2.4,
            "grad_norm": 0.5420322418212891,
            "learning_rate": 0.000201,
            "loss": 0.8347192764282226,
            "step": 300
        },
        {
            "epoch": 2.4,
            "eval_loss": 1.3487833738327026,
            "eval_runtime": 8.2267,
            "eval_samples_per_second": 6.078,
            "eval_steps_per_second": 1.58,
            "step": 300
        },
        {
            "epoch": 2.48,
            "grad_norm": 0.6434655785560608,
            "learning_rate": 0.000191,
            "loss": 0.9789088249206543,
            "step": 310
        },
        {
            "epoch": 2.56,
            "grad_norm": 0.6171281933784485,
            "learning_rate": 0.000181,
            "loss": 0.8358834266662598,
            "step": 320
        },
        {
            "epoch": 2.64,
            "grad_norm": 0.5716249942779541,
            "learning_rate": 0.000171,
            "loss": 0.8946387290954589,
            "step": 330
        },
        {
            "epoch": 2.7199999999999998,
            "grad_norm": 0.5906839966773987,
            "learning_rate": 0.000161,
            "loss": 0.770601224899292,
            "step": 340
        },
        {
            "epoch": 2.8,
            "grad_norm": 0.48331063985824585,
            "learning_rate": 0.000151,
            "loss": 0.8676647186279297,
            "step": 350
        },
        {
            "epoch": 2.8,
            "eval_loss": 1.3514587879180908,
            "eval_runtime": 8.472,
            "eval_samples_per_second": 5.902,
            "eval_steps_per_second": 1.534,
            "step": 350
        },
        {
            "epoch": 2.88,
            "grad_norm": 0.6528721451759338,
            "learning_rate": 0.00014099999999999998,
            "loss": 0.8320070266723633,
            "step": 360
        },
        {
            "epoch": 2.96,
            "grad_norm": 0.5934861302375793,
            "learning_rate": 0.000131,
            "loss": 0.8447301864624024,
            "step": 370
        },
        {
            "epoch": 3.04,
            "grad_norm": 0.4907662868499756,
            "learning_rate": 0.000121,
            "loss": 0.7062413215637207,
            "step": 380
        },
        {
            "epoch": 3.12,
            "grad_norm": 0.48673659563064575,
            "learning_rate": 0.000111,
            "loss": 0.6500791072845459,
            "step": 390
        },
        {
            "epoch": 3.2,
            "grad_norm": 0.5416309833526611,
            "learning_rate": 0.000101,
            "loss": 0.6877048015594482,
            "step": 400
        },
        {
            "epoch": 3.2,
            "eval_loss": 1.4348132610321045,
            "eval_runtime": 8.1816,
            "eval_samples_per_second": 6.111,
            "eval_steps_per_second": 1.589,
            "step": 400
        },
        {
            "epoch": 3.2800000000000002,
            "grad_norm": 0.5395511984825134,
            "learning_rate": 9.1e-05,
            "loss": 0.5939682960510254,
            "step": 410
        },
        {
            "epoch": 3.36,
            "grad_norm": 0.6360337734222412,
            "learning_rate": 8.1e-05,
            "loss": 0.6863453388214111,
            "step": 420
        },
        {
            "epoch": 3.44,
            "grad_norm": 0.7402626276016235,
            "learning_rate": 7.099999999999999e-05,
            "loss": 0.6872247695922852,
            "step": 430
        },
        {
            "epoch": 3.52,
            "grad_norm": 0.7384811043739319,
            "learning_rate": 6.1e-05,
            "loss": 0.7443608283996582,
            "step": 440
        },
        {
            "epoch": 3.6,
            "grad_norm": 0.7115420699119568,
            "learning_rate": 5.1e-05,
            "loss": 0.660958194732666,
            "step": 450
        },
        {
            "epoch": 3.6,
            "eval_loss": 1.4450159072875977,
            "eval_runtime": 8.5817,
            "eval_samples_per_second": 5.826,
            "eval_steps_per_second": 1.515,
            "step": 450
        },
        {
            "epoch": 3.68,
            "grad_norm": 0.6265407800674438,
            "learning_rate": 4.1e-05,
            "loss": 0.7305331707000733,
            "step": 460
        },
        {
            "epoch": 3.76,
            "grad_norm": 0.6096587181091309,
            "learning_rate": 3.1e-05,
            "loss": 0.6537210464477539,
            "step": 470
        },
        {
            "epoch": 3.84,
            "grad_norm": 0.6022178530693054,
            "learning_rate": 2.1000000000000002e-05,
            "loss": 0.6814323902130127,
            "step": 480
        },
        {
            "epoch": 3.92,
            "grad_norm": 0.6387237310409546,
            "learning_rate": 1.1e-05,
            "loss": 0.7454281330108643,
            "step": 490
        },
        {
            "epoch": 4.0,
            "grad_norm": 0.566798985004425,
            "learning_rate": 1e-06,
            "loss": 0.682561206817627,
            "step": 500
        },
        {
            "epoch": 4.0,
            "eval_loss": 1.4411063194274902,
            "eval_runtime": 9.2162,
            "eval_samples_per_second": 5.425,
            "eval_steps_per_second": 1.411,
            "step": 500
        }
    ],
    "logging_steps": 10,
    "max_steps": 500,
    "num_input_tokens_seen": 0,
    "num_train_epochs": 4,
    "save_steps": 100,
    "stateful_callbacks": {
        "TrainerControl": {
            "args": {
                "should_epoch_stop": false,
                "should_evaluate": false,
                "should_log": false,
                "should_save": true,
                "should_training_stop": true
            },
            "attributes": {}
        }
    },
    "total_flos": 356267261952000.0,
    "train_batch_size": 4,
    "trial_name": null,
    "trial_params": null
}
```
</details>

### Step 16: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
df = pd.read_parquet('training_curves_comparison.parquet')
print('Columns:', df.columns.tolist())
print('Shape:', df.shape)
print()
print('Unique runs:', df['run'].unique() if 'run' in df.columns else 'no run col')
print()
print(df.head(20).to_string())
"
```

<details><summary>Output (1656 chars)</summary>

```
Columns: ['run_name', 'step', 'loss', 'eval_loss', 'learning_rate', 'grad_norm']
Shape: (4576, 6)

Unique runs: no run col

          run_name   step      loss  eval_loss  learning_rate  grad_norm
0   adalora_alpaca   10.0  3.966280        NaN       0.000491   0.048049
1   adalora_alpaca   20.0  3.924714        NaN       0.000481   0.058626
2   adalora_alpaca   30.0  3.666683        NaN       0.000471   0.068172
3   adalora_alpaca   40.0  3.302401        NaN       0.000461   0.087289
4   adalora_alpaca   50.0  2.878171        NaN       0.000451   0.109314
5   adalora_alpaca   50.0  2.804040   2.804040            NaN        NaN
6   adalora_alpaca   60.0  2.824110        NaN       0.000441   0.108838
7   adalora_alpaca   70.0  2.687538        NaN       0.000431   0.133866
8   adalora_alpaca   80.0  2.561692        NaN       0.000421   0.206073
9   adalora_alpaca   90.0  2.460023        NaN       0.000411   0.281365
10  adalora_alpaca  100.0  2.480278        NaN       0.000401   0.513039
11  adalora_alpaca  100.0  2.250695   2.250695            NaN        NaN
12  adalora_alpaca  110.0  2.300850        NaN       0.000391   0.265148
13  adalora_alpaca  120.0  2.178442        NaN       0.000381   0.259992
14  adalora_alpaca  130.0  1.994812        NaN       0.000371   0.313104
15  adalora_alpaca  140.0  1.897009        NaN       0.000361   0.226678
16  adalora_alpaca  150.0  1.863371        NaN       0.000351   0.230072
17  adalora_alpaca  150.0  1.773890   1.773890            NaN        NaN
18  adalora_alpaca  160.0  1.707221        NaN       0.000341   0.376458
19  adalora_alpaca  170.0  1.665653        NaN       0.000331   0.244635
```
</details>

### Step 17: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
df = pd.read_parquet('eval_results_comparison.parquet')
print('Columns:', df.columns.tolist())
print('Shape:', df.shape)
print()
print(df.to_string())
"
```

<details><summary>Output (30410 chars)</summary>

```
Columns: ['run_name', 'benchmark', 'metric', 'value']
Shape: (369, 4)

                           run_name   benchmark                metric       value
0                           adalora    arc_easy            sample_len  100.000000
1                           adalora    arc_easy              acc,none    0.580000
2                           adalora    arc_easy       acc_stderr,none    0.049604
3                           adalora    arc_easy         acc_norm,none    0.590000
4                           adalora    arc_easy  acc_norm_stderr,none    0.049431
5                           adalora   hellaswag            sample_len  100.000000
6                           adalora   hellaswag              acc,none    0.450000
7                           adalora   hellaswag       acc_stderr,none    0.050000
8                           adalora   hellaswag         acc_norm,none    0.450000
9                           adalora   hellaswag  acc_norm_stderr,none    0.050000
10                          adalora        piqa            sample_len  100.000000
11                          adalora        piqa              acc,none    0.680000
12                          adalora        piqa       acc_stderr,none    0.046883
13                          adalora        piqa         acc_norm,none    0.660000
14                          adalora        piqa  acc_norm_stderr,none    0.047610
15                   adalora_alpaca    arc_easy            sample_len  200.000000
16                   adalora_alpaca    arc_easy              acc,none    0.585000
17                   adalora_alpaca    arc_easy       acc_stderr,none    0.034928
18                   adalora_alpaca    arc_easy         acc_norm,none    0.595000
19                   adalora_alpaca    arc_easy  acc_norm_stderr,none    0.034798
20                   adalora_alpaca   hellaswag            sample_len  200.000000
21                   adalora_alpaca   hellaswag              acc,none    0.435000
22                   adalora_alpaca   hellaswag       acc_stderr,none    0.035143
23                   adalora_alpaca   hellaswag         acc_norm,none    0.465000
24                   adalora_alpaca   hellaswag  acc_norm_stderr,none    0.035357
25                   adalora_alpaca        piqa            sample_len  200.000000
26                   adalora_alpaca        piqa              acc,none    0.655000
27                   adalora_alpaca        piqa       acc_stderr,none    0.033698
28                   adalora_alpaca        piqa         acc_norm,none    0.660000
29                   adalora_alpaca        piqa  acc_norm_stderr,none    0.033580
30                   adalora_alpaca  winogrande            sample_len  200.000000
31                   adalora_alpaca  winogrande              acc,none    0.475000
32                   adalora_alpaca  winogrande       acc_stderr,none    0.035400
33                   adalora_alpaca       boolq            sample_len  200.000000
34                   adalora_alpaca       boolq              acc,none    0.620000
35                   adalora_alpaca       boolq       acc_stderr,none    0.034408
36        adalora_code_instructions    arc_easy            sample_len  200.000000
37        adalora_code_instructions    arc_easy              acc,none    0.580000
38        adalora_code_instructions    arc_easy       acc_stderr,none    0.034987
39        adalora_code_instructions    arc_easy         acc_norm,none    0.540000
40        adalora_code_instructions    arc_easy  acc_norm_stderr,none    0.035330
41        adalora_code_instructions   hellaswag            sample_len  200.000000
42        adalora_code_instructions   hellaswag              acc,none    0.450000
43        adalora_code_instructions   hellaswag       acc_stderr,none    0.035266
44        adalora_code_instructions   hellaswag         acc_norm,none    0.470000
45        adalora_code_instructions   hellaswag  acc_norm_stderr,none    0.035380
46        adalora_code_instructions        piqa            sample_len  200.000000
47        adalora_code_instructions        piqa              acc,none    0.645000
48        adalora_code_instructions        piqa       acc_stderr,none    0.033921
49        adalora_code_instructions        piqa         acc_norm,none    0.690000
50        adalora_code_instructions        piqa  acc_norm_stderr,none    0.032785
51        adalora_code_instructions  winogrande            sample_len  200.000000
52        adalora_code_instructions  winogrande              acc,none    0.500000
53        adalora_code_instructions  winogrande       acc_stderr,none    0.035444
54        adalora_code_instructions       boolq            sample_len  200.000000
55        adalora_code_instructions       boolq              acc,none    0.625000
56        adalora_code_instructions       boolq       acc_stderr,none    0.034319
57                   dora_r8_alpaca    arc_easy            sample_len  200.000000
58                   dora_r8_alpaca    arc_easy              acc,none    0.535000
59                   dora_r8_alpaca    arc_easy       acc_stderr,none    0.035357
60                   dora_r8_alpaca    arc_easy         acc_norm,none    0.515000
61                   dora_r8_alpaca    arc_easy  acc_norm_stderr,none    0.035428
62                   dora_r8_alpaca   hellaswag            sample_len  200.000000
63                   dora_r8_alpaca   hellaswag              acc,none    0.450000
64                   dora_r8_alpaca   hellaswag       acc_stderr,none    0.035266
65                   dora_r8_alpaca   hellaswag         acc_norm,none    0.465000
66                   dora_r8_alpaca   hellaswag  acc_norm_stderr,none    0.035357
67                   dora_r8_alpaca        piqa            sample_len  200.000000
68                   dora_r8_alpaca        piqa              acc,none    0.680000
69                   dora_r8_alpaca        piqa       acc_stderr,none    0.033068
70                   dora_r8_alpaca        piqa         acc_norm,none    0.680000
71                   dora_r8_alpaca        piqa  acc_norm_stderr,none    0.033068
72                   dora_r8_alpaca  winogrande            sample_len  200.000000
73                   dora_r8_alpaca  winogrande              acc,none    0.485000
74                   dora_r8_alpaca  winogrande       acc_stderr,none    0.035428
75                   dora_r8_alpaca       boolq            sample_len  200.000000
76                   dora_r8_alpaca       boolq              acc,none    0.635000
77                   dora_r8_alpaca       boolq       acc_stderr,none    0.034128
78        dora_r8_code_instructions    arc_easy            sample_len  200.000000
79        dora_r8_code_instructions    arc_easy              acc,none    0.510000
80        dora_r8_code_instructions    arc_easy       acc_stderr,none    0.035437
81        dora_r8_code_instructions    arc_easy         acc_norm,none    0.520000
82        dora_r8_code_instructions    arc_easy  acc_norm_stderr,none    0.035416
83        dora_r8_code_instructions   hellaswag            sample_len  200.000000
84        dora_r8_code_instructions   hellaswag              acc,none    0.440000
85        dora_r8_code_instructions   hellaswag       acc_stderr,none    0.035188
86        dora_r8_code_instructions   hellaswag         acc_norm,none    0.475000
87        dora_r8_code_instructions   hellaswag  acc_norm_stderr,none    0.035400
88        dora_r8_code_instructions        piqa            sample_len  200.000000
89        dora_r8_code_instructions        piqa              acc,none    0.650000
90        dora_r8_code_instructions        piqa       acc_stderr,none    0.033811
91        dora_r8_code_instructions        piqa         acc_norm,none    0.670000
92        dora_r8_code_instructions        piqa  acc_norm_stderr,none    0.033332
93        dora_r8_code_instructions  winogrande            sample_len  200.000000
94        dora_r8_code_instructions  winogrande              acc,none    0.495000
95        dora_r8_code_instructions  winogrande       acc_stderr,none    0.035442
96        dora_r8_code_instructions       boolq            sample_len  200.000000
97        dora_r8_code_instructions       boolq              acc,none    0.605000
98        dora_r8_code_instructions       boolq       acc_stderr,none    0.034654
99                              ia3    arc_easy            sample_len  100.000000
100                             ia3    arc_easy              acc,none    0.620000
101                             ia3    arc_easy       acc_stderr,none    0.048783
102                             ia3    arc_easy         acc_norm,none    0.580000
103                             ia3    arc_easy  acc_norm_stderr,none    0.049604
104                             ia3   hellaswag            sample_len  100.000000
105                             ia3   hellaswag              acc,none    0.440000
106                             ia3   hellaswag       acc_stderr,none    0.049889
107                             ia3   hellaswag         acc_norm,none    0.460000
108                             ia3   hellaswag  acc_norm_stderr,none    0.050091
109                             ia3        piqa            sample_len  100.000000
110                             ia3        piqa              acc,none    0.670000
111                             ia3        piqa       acc_stderr,none    0.047258
112                             ia3        piqa         acc_norm,none    0.650000
113                             ia3        piqa  acc_norm_stderr,none    0.047937
114                      ia3_alpaca    arc_easy            sample_len  200.000000
115                      ia3_alpaca    arc_easy              acc,none    0.600000
116                      ia3_alpaca    arc_easy       acc_stderr,none    0.034728
117                      ia3_alpaca    arc_easy         acc_norm,none    0.595000
118                      ia3_alpaca    arc_easy  acc_norm_stderr,none    0.034798
119                      ia3_alpaca   hellaswag            sample_len  200.000000
120                      ia3_alpaca   hellaswag              acc,none    0.430000
121                      ia3_alpaca   hellaswag       acc_stderr,none    0.035095
122                      ia3_alpaca   hellaswag         acc_norm,none    0.465000
123                      ia3_alpaca   hellaswag  acc_norm_stderr,none    0.035357
124                      ia3_alpaca        piqa            sample_len  200.000000
125                      ia3_alpaca        piqa              acc,none    0.650000
126                      ia3_alpaca        piqa       acc_stderr,none    0.033811
127                      ia3_alpaca        piqa         acc_norm,none    0.650000
128                      ia3_alpaca        piqa  acc_norm_stderr,none    0.033811
129                      ia3_alpaca  winogrande            sample_len  200.000000
130                      ia3_alpaca  winogrande              acc,none    0.485000
131                      ia3_alpaca  winogrande       acc_stderr,none    0.035428
132                      ia3_alpaca       boolq            sample_len  200.000000
133                      ia3_alpaca       boolq              acc,none    0.605000
134                      ia3_alpaca       boolq       acc_stderr,none    0.034654
135           ia3_code_instructions    arc_easy            sample_len  200.000000
136           ia3_code_instructions    arc_easy              acc,none    0.580000
137           ia3_code_instructions    arc_easy       acc_stderr,none    0.034987
138           ia3_code_instructions    arc_easy         acc_norm,none    0.560000
139           ia3_code_instructions    arc_easy  acc_norm_stderr,none    0.035188
140           ia3_code_instructions   hellaswag            sample_len  200.000000
141           ia3_code_instructions   hellaswag              acc,none    0.445000
142           ia3_code_instructions   hellaswag       acc_stderr,none    0.035229
143           ia3_code_instructions   hellaswag         acc_norm,none    0.455000
144           ia3_code_instructions   hellaswag  acc_norm_stderr,none    0.035300
145           ia3_code_instructions        piqa            sample_len  200.000000
146           ia3_code_instructions        piqa              acc,none    0.635000
147           ia3_code_instructions        piqa       acc_stderr,none    0.034128
148           ia3_code_instructions        piqa         acc_norm,none    0.665000
149           ia3_code_instructions        piqa  acc_norm_stderr,none    0.033459
150           ia3_code_instructions  winogrande            sample_len  200.000000
151           ia3_code_instructions  winogrande              acc,none    0.480000
152           ia3_code_instructions  winogrande       acc_stderr,none    0.035416
153           ia3_code_instructions       boolq            sample_len  200.000000
154           ia3_code_instructions       boolq              acc,none    0.640000
155           ia3_code_instructions       boolq       acc_stderr,none    0.034026
156                        lora_r16    arc_easy            sample_len  100.000000
157                        lora_r16    arc_easy              acc,none    0.580000
158                        lora_r16    arc_easy       acc_stderr,none    0.049604
159                        lora_r16    arc_easy         acc_norm,none    0.560000
160                        lora_r16    arc_easy  acc_norm_stderr,none    0.049889
161                        lora_r16   hellaswag            sample_len  100.000000
162                        lora_r16   hellaswag              acc,none    0.450000
163                        lora_r16   hellaswag       acc_stderr,none    0.050000
164                        lora_r16   hellaswag         acc_norm,none    0.470000
165                        lora_r16   hellaswag  acc_norm_stderr,none    0.050161
166                        lora_r16        piqa            sample_len  100.000000
167                        lora_r16        piqa              acc,none    0.690000
168                        lora_r16        piqa       acc_stderr,none    0.046482
169                        lora_r16        piqa         acc_norm,none    0.660000
170                        lora_r16        piqa  acc_norm_stderr,none    0.047610
171                 lora_r16_alpaca    arc_easy            sample_len  200.000000
172                 lora_r16_alpaca    arc_easy              acc,none    0.585000
173                 lora_r16_alpaca    arc_easy       acc_stderr,none    0.034928
174                 lora_r16_alpaca    arc_easy         acc_norm,none    0.570000
175                 lora_r16_alpaca    arc_easy  acc_norm_stderr,none    0.035095
176                 lora_r16_alpaca   hellaswag            sample_len  200.000000
177                 lora_r16_alpaca   hellaswag              acc,none    0.430000
178                 lora_r16_alpaca   hellaswag       acc_stderr,none    0.035095
179                 lora_r16_alpaca   hellaswag         acc_norm,none    0.475000
180                 lora_r16_alpaca   hellaswag  acc_norm_stderr,none    0.035400
181                 lora_r16_alpaca        piqa            sample_len  200.000000
182                 lora_r16_alpaca        piqa              acc,none    0.665000
183                 lora_r16_alpaca        piqa       acc_stderr,none    0.033459
184                 lora_r16_alpaca        piqa         acc_norm,none    0.670000
185                 lora_r16_alpaca        piqa  acc_norm_stderr,none    0.033332
186                 lora_r16_alpaca  winogrande            sample_len  200.000000
187                 lora_r16_alpaca  winogrande              acc,none    0.485000
188                 lora_r16_alpaca  winogrande       acc_stderr,none    0.035428
189                 lora_r16_alpaca       boolq            sample_len  200.000000
190                 lora_r16_alpaca       boolq              acc,none    0.630000
191                 lora_r16_alpaca       boolq       acc_stderr,none    0.034225
192      lora_r16_code_instructions    arc_easy            sample_len  200.000000
193      lora_r16_code_instructions    arc_easy              acc,none    0.485000
194      lora_r16_code_instructions    arc_easy       acc_stderr,none    0.035428
195      lora_r16_code_instructions    arc_easy         acc_norm,none    0.485000
196      lora_r16_code_instructions    arc_easy  acc_norm_stderr,none    0.035428
197      lora_r16_code_instructions   hellaswag            sample_len  200.000000
198      lora_r16_code_instructions   hellaswag              acc,none    0.440000
199      lora_r16_code_instructions   hellaswag       acc_stderr,none    0.035188
200      lora_r16_code_instructions   hellaswag         acc_norm,none    0.495000
201      lora_r16_code_instructions   hellaswag  acc_norm_stderr,none    0.035442
202      lora_r16_code_instructions        piqa            sample_len  200.000000
203      lora_r16_code_instructions        piqa              acc,none    0.635000
204      lora_r16_code_instructions        piqa       acc_stderr,none    0.034128
205      lora_r16_code_instructions        piqa         acc_norm,none    0.685000
206      lora_r16_code_instructions        piqa  acc_norm_stderr,none    0.032929
207      lora_r16_code_instructions  winogrande            sample_len  200.000000
208      lora_r16_code_instructions  winogrande              acc,none    0.490000
209      lora_r16_code_instructions  winogrande       acc_stderr,none    0.035437
210      lora_r16_code_instructions       boolq            sample_len  200.000000
211      lora_r16_code_instructions       boolq              acc,none    0.600000
212      lora_r16_code_instructions       boolq       acc_stderr,none    0.034728
213             lora_r16_mlp_alpaca    arc_easy            sample_len  200.000000
214             lora_r16_mlp_alpaca    arc_easy              acc,none    0.430000
215             lora_r16_mlp_alpaca    arc_easy       acc_stderr,none    0.035095
216             lora_r16_mlp_alpaca    arc_easy         acc_norm,none    0.480000
217             lora_r16_mlp_alpaca    arc_easy  acc_norm_stderr,none    0.035416
218             lora_r16_mlp_alpaca   hellaswag            sample_len  200.000000
219             lora_r16_mlp_alpaca   hellaswag              acc,none    0.400000
220             lora_r16_mlp_alpaca   hellaswag       acc_stderr,none    0.034728
221             lora_r16_mlp_alpaca   hellaswag         acc_norm,none    0.445000
222             lora_r16_mlp_alpaca   hellaswag  acc_norm_stderr,none    0.035229
223             lora_r16_mlp_alpaca        piqa            sample_len  200.000000
224             lora_r16_mlp_alpaca        piqa              acc,none    0.625000
225             lora_r16_mlp_alpaca        piqa       acc_stderr,none    0.034319
226             lora_r16_mlp_alpaca        piqa         acc_norm,none    0.625000
227             lora_r16_mlp_alpaca        piqa  acc_norm_stderr,none    0.034319
228             lora_r16_mlp_alpaca  winogrande            sample_len  200.000000
229             lora_r16_mlp_alpaca  winogrande              acc,none    0.505000
230             lora_r16_mlp_alpaca  winogrande       acc_stderr,none    0.035442
231             lora_r16_mlp_alpaca       boolq            sample_len  200.000000
232             lora_r16_mlp_alpaca       boolq              acc,none    0.595000
233             lora_r16_mlp_alpaca       boolq       acc_stderr,none    0.034798
234  lora_r16_mlp_code_instructions    arc_easy            sample_len  200.000000
235  lora_r16_mlp_code_instructions    arc_easy              acc,none    0.525000
236  lora_r16_mlp_code_instructions    arc_easy       acc_stderr,none    0.035400
237  lora_r16_mlp_code_instructions    arc_easy         acc_norm,none    0.525000
238  lora_r16_mlp_code_instructions    arc_easy  acc_norm_stderr,none    0.035400
239  lora_r16_mlp_code_instructions   hellaswag            sample_len  200.000000
240  lora_r16_mlp_code_instructions   hellaswag              acc,none    0.450000
241  lora_r16_mlp_code_instructions   hellaswag       acc_stderr,none    0.035266
242  lora_r16_mlp_code_instructions   hellaswag         acc_norm,none    0.480000
243  lora_r16_mlp_code_instructions   hellaswag  acc_norm_stderr,none    0.035416
244  lora_r16_mlp_code_instructions        piqa            sample_len  200.000000
245  lora_r16_mlp_code_instructions        piqa              acc,none    0.620000
246  lora_r16_mlp_code_instructions        piqa       acc_stderr,none    0.034408
247  lora_r16_mlp_code_instructions        piqa         acc_norm,none    0.665000
248  lora_r16_mlp_code_instructions        piqa  acc_norm_stderr,none    0.033459
249  lora_r16_mlp_code_instructions  winogrande            sample_len  200.000000
250  lora_r16_mlp_code_instructions  winogrande              acc,none    0.530000
251  lora_r16_mlp_code_instructions  winogrande       acc_stderr,none    0.035380
252  lora_r16_mlp_code_instructions       boolq            sample_len  200.000000
253  lora_r16_mlp_code_instructions       boolq              acc,none    0.610000
254  lora_r16_mlp_code_instructions       boolq       acc_stderr,none    0.034576
255                    lora_r32_all    arc_easy            sample_len  100.000000
256                    lora_r32_all    arc_easy              acc,none    0.520000
257                    lora_r32_all    arc_easy       acc_stderr,none    0.050212
258                    lora_r32_all    arc_easy         acc_norm,none    0.530000
259                    lora_r32_all    arc_easy  acc_norm_stderr,none    0.050161
260                    lora_r32_all   hellaswag            sample_len  100.000000
261                    lora_r32_all   hellaswag              acc,none    0.420000
262                    lora_r32_all   hellaswag       acc_stderr,none    0.049604
263                    lora_r32_all   hellaswag         acc_norm,none    0.450000
264                    lora_r32_all   hellaswag  acc_norm_stderr,none    0.050000
265                    lora_r32_all        piqa            sample_len  100.000000
266                    lora_r32_all        piqa              acc,none    0.660000
267                    lora_r32_all        piqa       acc_stderr,none    0.047610
268                    lora_r32_all        piqa         acc_norm,none    0.690000
269                    lora_r32_all        piqa  acc_norm_stderr,none    0.046482
270             lora_r32_all_alpaca    arc_easy            sample_len  200.000000
271             lora_r32_all_alpaca    arc_easy              acc,none    0.510000
272             lora_r32_all_alpaca    arc_easy       acc_stderr,none    0.035437
273             lora_r32_all_alpaca    arc_easy         acc_norm,none    0.545000
274             lora_r32_all_alpaca    arc_easy  acc_norm_stderr,none    0.035300
275             lora_r32_all_alpaca   hellaswag            sample_len  200.000000
276             lora_r32_all_alpaca   hellaswag              acc,none    0.450000
277             lora_r32_all_alpaca   hellaswag       acc_stderr,none    0.035266
278             lora_r32_all_alpaca   hellaswag         acc_norm,none    0.490000
279             lora_r32_all_alpaca   hellaswag  acc_norm_stderr,none    0.035437
280             lora_r32_all_alpaca        piqa            sample_len  200.000000
281             lora_r32_all_alpaca        piqa              acc,none    0.665000
282             lora_r32_all_alpaca        piqa       acc_stderr,none    0.033459
283             lora_r32_all_alpaca        piqa         acc_norm,none    0.695000
284             lora_r32_all_alpaca        piqa  acc_norm_stderr,none    0.032637
285             lora_r32_all_alpaca  winogrande            sample_len  200.000000
286             lora_r32_all_alpaca  winogrande              acc,none    0.540000
287             lora_r32_all_alpaca  winogrande       acc_stderr,none    0.035330
288             lora_r32_all_alpaca       boolq            sample_len  200.000000
289             lora_r32_all_alpaca       boolq              acc,none    0.610000
290             lora_r32_all_alpaca       boolq       acc_stderr,none    0.034576
291  lora_r32_all_code_instructions    arc_easy            sample_len  200.000000
292  lora_r32_all_code_instructions    arc_easy              acc,none    0.490000
293  lora_r32_all_code_instructions    arc_easy       acc_stderr,none    0.035437
294  lora_r32_all_code_instructions    arc_easy         acc_norm,none    0.510000
295  lora_r32_all_code_instructions    arc_easy  acc_norm_stderr,none    0.035437
296  lora_r32_all_code_instructions   hellaswag            sample_len  200.000000
297  lora_r32_all_code_instructions   hellaswag              acc,none    0.440000
298  lora_r32_all_code_instructions   hellaswag       acc_stderr,none    0.035188
299  lora_r32_all_code_instructions   hellaswag         acc_norm,none    0.475000
300  lora_r32_all_code_instructions   hellaswag  acc_norm_stderr,none    0.035400
301  lora_r32_all_code_instructions        piqa            sample_len  200.000000
302  lora_r32_all_code_instructions        piqa              acc,none    0.650000
303  lora_r32_all_code_instructions        piqa       acc_stderr,none    0.033811
304  lora_r32_all_code_instructions        piqa         acc_norm,none    0.660000
305  lora_r32_all_code_instructions        piqa  acc_norm_stderr,none    0.033580
306  lora_r32_all_code_instructions  winogrande            sample_len  200.000000
307  lora_r32_all_code_instructions  winogrande              acc,none    0.510000
308  lora_r32_all_code_instructions  winogrande       acc_stderr,none    0.035437
309  lora_r32_all_code_instructions       boolq            sample_len  200.000000
310  lora_r32_all_code_instructions       boolq              acc,none    0.630000
311  lora_r32_all_code_instructions       boolq       acc_stderr,none    0.034225
312                         lora_r4    arc_easy            sample_len  100.000000
313                         lora_r4    arc_easy              acc,none    0.570000
314                         lora_r4    arc_easy       acc_stderr,none    0.049757
315                         lora_r4    arc_easy         acc_norm,none    0.600000
316                         lora_r4    arc_easy  acc_norm_stderr,none    0.049237
317                         lora_r4   hellaswag            sample_len  100.000000
318                         lora_r4   hellaswag              acc,none    0.450000
319                         lora_r4   hellaswag       acc_stderr,none    0.050000
320                         lora_r4   hellaswag         acc_norm,none    0.460000
321                         lora_r4   hellaswag  acc_norm_stderr,none    0.050091
322                         lora_r4        piqa            sample_len  100.000000
323                         lora_r4        piqa              acc,none    0.690000
324                         lora_r4        piqa       acc_stderr,none    0.046482
325                         lora_r4        piqa         acc_norm,none    0.660000
326                         lora_r4        piqa  acc_norm_stderr,none    0.047610
327                  lora_r4_alpaca    arc_easy            sample_len  200.000000
328                  lora_r4_alpaca    arc_easy              acc,none    0.590000
329                  lora_r4_alpaca    arc_easy       acc_stderr,none    0.034865
330                  lora_r4_alpaca    arc_easy         acc_norm,none    0.600000
331                  lora_r4_alpaca    arc_easy  acc_norm_stderr,none    0.034728
332                  lora_r4_alpaca   hellaswag            sample_len  200.000000
333                  lora_r4_alpaca   hellaswag              acc,none    0.430000
334                  lora_r4_alpaca   hellaswag       acc_stderr,none    0.035095
335                  lora_r4_alpaca   hellaswag         acc_norm,none    0.480000
336                  lora_r4_alpaca   hellaswag  acc_norm_stderr,none    0.035416
337                  lora_r4_alpaca        piqa            sample_len  200.000000
338                  lora_r4_alpaca        piqa              acc,none    0.665000
339                  lora_r4_alpaca        piqa       acc_stderr,none    0.033459
340                  lora_r4_alpaca        piqa         acc_norm,none    0.665000
341                  lora_r4_alpaca        piqa  acc_norm_stderr,none    0.033459
342                  lora_r4_alpaca  winogrande            sample_len  200.000000
343                  lora_r4_alpaca  winogrande              acc,none    0.515000
344                  lora_r4_alpaca  winogrande       acc_stderr,none    0.035428
345                  lora_r4_alpaca       boolq            sample_len  200.000000
346                  lora_r4_alpaca       boolq              acc,none    0.625000
347                  lora_r4_alpaca       boolq       acc_stderr,none    0.034319
348       lora_r4_code_instructions    arc_easy            sample_len  200.000000
349       lora_r4_code_instructions    arc_easy              acc,none    0.540000
350       lora_r4_code_instructions    arc_easy       acc_stderr,none    0.035330
351       lora_r4_code_instructions    arc_easy         acc_norm,none    0.540000
352       lora_r4_code_instructions    arc_easy  acc_norm_stderr,none    0.035330
353       lora_r4_code_instructions   hellaswag            sample_len  200.000000
354       lora_r4_code_instructions   hellaswag              acc,none    0.435000
355       lora_r4_code_instructions   hellaswag       acc_stderr,none    0.035143
356       lora_r4_code_instructions   hellaswag         acc_norm,none    0.480000
357       lora_r4_code_instructions   hellaswag  acc_norm_stderr,none    0.035416
358       lora_r4_code_instructions        piqa            sample_len  200.000000
359       lora_r4_code_instructions        piqa              acc,none    0.645000
360       lora_r4_code_instructions        piqa       acc_stderr,none    0.033921
361       lora_r4_code_instructions        piqa         acc_norm,none    0.670000
362       lora_r4_code_instructions        piqa  acc_norm_stderr,none    0.033332
363       lora_r4_code_instructions  winogrande            sample_len  200.000000
364       lora_r4_code_instructions  winogrande              acc,none    0.475000
365       lora_r4_code_instructions  winogrande       acc_stderr,none    0.035400
366       lora_r4_code_instructions       boolq            sample_len  200.000000
367       lora_r4_code_instructions       boolq              acc,none    0.610000
368       lora_r4_code_instructions       boolq       acc_stderr,none    0.034576
```
</details>

### Step 18: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
df = pd.read_parquet('cross_adapter_comparison.parquet')
print('Columns:', df.columns.tolist())
print('Shape:', df.shape)
print()
print(df.to_string())
"
```

<details><summary>Output (3045 chars)</summary>

```
Columns: ['run_name', 'adapter', 'dataset', 'type', 'trainable_params', 'total_params', 'overhead_pct', 'final_train_loss', 'elapsed_seconds', 'max_steps']
Shape: (16, 10)

                          run_name       adapter            dataset     type  trainable_params  total_params  overhead_pct  final_train_loss  elapsed_seconds  max_steps
0                   adalora_alpaca       adalora             alpaca  adalora            922560     135437628        0.6812          1.797923           536.75        500
1        adalora_code_instructions       adalora  code_instructions  adalora            922560     135437628        0.6812          0.906270          1960.45       2000
2                   dora_r8_alpaca       dora_r8             alpaca     dora            483840     134998848        0.3584          1.114040          2815.13       2000
3        dora_r8_code_instructions       dora_r8  code_instructions     dora            483840     134998848        0.3584          0.698994          2687.35       2000
4                   full_ft_alpaca       full_ft             alpaca     full         134515008     134515008      100.0000          1.224169           447.77        500
5        full_ft_code_instructions       full_ft  code_instructions     full         134515008     134515008      100.0000          0.509005          1889.75       2000
6                       ia3_alpaca           ia3             alpaca      ia3             74880     134589888        0.0556          1.556490           449.57        500
7            ia3_code_instructions           ia3  code_instructions      ia3             74880     134589888        0.0556          0.848178          2414.05       2000
8                  lora_r16_alpaca      lora_r16             alpaca     lora            921600     135436608        0.6805          1.289507           479.97        500
9       lora_r16_code_instructions      lora_r16  code_instructions     lora            921600     135436608        0.6805          0.617452          1979.06       2000
10             lora_r16_mlp_alpaca  lora_r16_mlp             alpaca     lora           3041280     137556288        2.2109          0.440825          2876.91       2000
11  lora_r16_mlp_code_instructions  lora_r16_mlp  code_instructions     lora           3041280     137556288        2.2109          0.318423          2723.10       2000
12             lora_r32_all_alpaca  lora_r32_all             alpaca     lora           9768960     144283968        6.7706          0.983162           795.54        500
13  lora_r32_all_code_instructions  lora_r32_all  code_instructions     lora           9768960     144283968        6.7706          0.267194          3248.92       2000
14                  lora_r4_alpaca       lora_r4             alpaca     lora            230400     134745408        0.1710          1.362684           516.02        500
15       lora_r4_code_instructions       lora_r4  code_instructions     lora            230400     134745408        0.1710          0.762220          2179.49       2000
```
</details>

### Step 19: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd

df = pd.read_parquet('training_curves_comparison.parquet')
# Filter only SmolLM2 runs (no qwen3_ prefix)
smol = df[~df['run_name'].str.startswith('qwen3_')]
print('SmolLM2 runs:', sorted(smol['run_name'].unique()))
print()
print('Total rows:', len(smol))

# For each run, show the eval_loss trajectory
for run in sorted(smol['run_name'].unique()):
    run_df = smol[smol['run_name'] == run]
    eval_df = run_df[run_df['eval_loss'].notna()]
    if len(eval_df) > 0:
        print(f'\n=== {run} ===')
        for _, row in eval_df.iterrows():
            print(f'  step {int(row[\"step\"]):>5}: train_loss={row[\"loss\"]:.4f}  eval_loss={row[\"eval_loss\"]:.4f}')
"
```

<details><summary>Output (13908 chars)</summary>

```
SmolLM2 runs: ['adalora_alpaca', 'adalora_code_instructions', 'dora_r8_alpaca', 'dora_r8_code_instructions', 'full_ft_alpaca', 'full_ft_code_instructions', 'ia3_alpaca', 'ia3_code_instructions', 'lora_r16_alpaca', 'lora_r16_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_mlp_code_instructions', 'lora_r32_all_alpaca', 'lora_r32_all_code_instructions', 'lora_r4_alpaca', 'lora_r4_code_instructions']

Total rows: 4576

=== adalora_alpaca ===
  step    50: train_loss=2.8040  eval_loss=2.8040
  step   100: train_loss=2.2507  eval_loss=2.2507
  step   150: train_loss=1.7739  eval_loss=1.7739
  step   200: train_loss=1.4684  eval_loss=1.4684
  step   250: train_loss=1.3858  eval_loss=1.3858
  step   300: train_loss=1.3575  eval_loss=1.3575
  step   350: train_loss=1.3447  eval_loss=1.3447
  step   400: train_loss=1.3365  eval_loss=1.3365
  step   450: train_loss=1.3332  eval_loss=1.3332
  step   500: train_loss=1.3317  eval_loss=1.3317

=== adalora_code_instructions ===
  step   100: train_loss=1.2917  eval_loss=1.2917
  step   200: train_loss=1.0032  eval_loss=1.0032
  step   300: train_loss=0.9617  eval_loss=0.9617
  step   400: train_loss=0.9495  eval_loss=0.9495
  step   500: train_loss=0.9391  eval_loss=0.9391
  step   600: train_loss=0.9348  eval_loss=0.9348
  step   700: train_loss=0.9267  eval_loss=0.9267
  step   800: train_loss=0.9249  eval_loss=0.9249
  step   900: train_loss=0.9250  eval_loss=0.9250
  step  1000: train_loss=0.9203  eval_loss=0.9203
  step  1100: train_loss=0.9179  eval_loss=0.9179
  step  1200: train_loss=0.9198  eval_loss=0.9198
  step  1300: train_loss=0.9164  eval_loss=0.9164
  step  1400: train_loss=0.9178  eval_loss=0.9178
  step  1500: train_loss=0.9169  eval_loss=0.9169
  step  1600: train_loss=0.9160  eval_loss=0.9160
  step  1700: train_loss=0.9169  eval_loss=0.9169
  step  1800: train_loss=0.9175  eval_loss=0.9175
  step  1900: train_loss=0.9173  eval_loss=0.9173
  step  2000: train_loss=0.9168  eval_loss=0.9168

=== dora_r8_alpaca ===
  step   100: train_loss=1.3130  eval_loss=1.3130
  step   200: train_loss=1.2917  eval_loss=1.2917
  step   300: train_loss=1.2935  eval_loss=1.2935
  step   400: train_loss=1.2859  eval_loss=1.2859
  step   500: train_loss=1.2879  eval_loss=1.2879
  step   600: train_loss=1.2930  eval_loss=1.2930
  step   700: train_loss=1.3044  eval_loss=1.3044
  step   800: train_loss=1.3034  eval_loss=1.3034
  step   900: train_loss=1.3168  eval_loss=1.3168
  step  1000: train_loss=1.3145  eval_loss=1.3145
  step  1100: train_loss=1.3238  eval_loss=1.3238
  step  1200: train_loss=1.3376  eval_loss=1.3376
  step  1300: train_loss=1.3478  eval_loss=1.3478
  step  1400: train_loss=1.3627  eval_loss=1.3627
  step  1500: train_loss=1.3510  eval_loss=1.3510
  step  1600: train_loss=1.3667  eval_loss=1.3667
  step  1700: train_loss=1.3677  eval_loss=1.3677
  step  1800: train_loss=1.3784  eval_loss=1.3784
  step  1900: train_loss=1.3834  eval_loss=1.3834
  step  2000: train_loss=1.3838  eval_loss=1.3838

=== dora_r8_code_instructions ===
  step   100: train_loss=0.9396  eval_loss=0.9396
  step   200: train_loss=0.9259  eval_loss=0.9259
  step   300: train_loss=0.9097  eval_loss=0.9097
  step   400: train_loss=0.9125  eval_loss=0.9125
  step   500: train_loss=0.9049  eval_loss=0.9049
  step   600: train_loss=0.9168  eval_loss=0.9168
  step   700: train_loss=0.9117  eval_loss=0.9117
  step   800: train_loss=0.9317  eval_loss=0.9317
  step   900: train_loss=0.9366  eval_loss=0.9366
  step  1000: train_loss=0.9312  eval_loss=0.9312
  step  1100: train_loss=0.9489  eval_loss=0.9489
  step  1200: train_loss=0.9576  eval_loss=0.9576
  step  1300: train_loss=0.9727  eval_loss=0.9727
  step  1400: train_loss=0.9851  eval_loss=0.9851
  step  1500: train_loss=0.9902  eval_loss=0.9902
  step  1600: train_loss=0.9984  eval_loss=0.9984
  step  1700: train_loss=1.0079  eval_loss=1.0079
  step  1800: train_loss=1.0150  eval_loss=1.0150
  step  1900: train_loss=1.0179  eval_loss=1.0179
  step  2000: train_loss=1.0175  eval_loss=1.0175

=== full_ft_alpaca ===
  step    50: train_loss=1.3347  eval_loss=1.3347
  step   100: train_loss=1.2916  eval_loss=1.2916
  step   150: train_loss=1.2854  eval_loss=1.2854
  step   200: train_loss=1.2768  eval_loss=1.2768
  step   250: train_loss=1.2716  eval_loss=1.2716
  step   300: train_loss=1.2728  eval_loss=1.2728
  step   350: train_loss=1.2712  eval_loss=1.2712
  step   400: train_loss=1.2722  eval_loss=1.2722
  step   450: train_loss=1.2726  eval_loss=1.2726
  step   500: train_loss=1.2727  eval_loss=1.2727

=== full_ft_code_instructions ===
  step   100: train_loss=0.9157  eval_loss=0.9157
  step   200: train_loss=0.8970  eval_loss=0.8970
  step   300: train_loss=0.8902  eval_loss=0.8902
  step   400: train_loss=0.8944  eval_loss=0.8944
  step   500: train_loss=0.8899  eval_loss=0.8899
  step   600: train_loss=0.9035  eval_loss=0.9035
  step   700: train_loss=0.9171  eval_loss=0.9171
  step   800: train_loss=0.9434  eval_loss=0.9434
  step   900: train_loss=0.9649  eval_loss=0.9649
  step  1000: train_loss=0.9618  eval_loss=0.9618
  step  1100: train_loss=0.9841  eval_loss=0.9841
  step  1200: train_loss=1.0108  eval_loss=1.0108
  step  1300: train_loss=1.0288  eval_loss=1.0288
  step  1400: train_loss=1.0457  eval_loss=1.0457
  step  1500: train_loss=1.0521  eval_loss=1.0521
  step  1600: train_loss=1.0718  eval_loss=1.0718
  step  1700: train_loss=1.0816  eval_loss=1.0816
  step  1800: train_loss=1.0889  eval_loss=1.0889
  step  1900: train_loss=1.0967  eval_loss=1.0967
  step  2000: train_loss=1.0975  eval_loss=1.0975

=== ia3_alpaca ===
  step    50: train_loss=2.0330  eval_loss=2.0330
  step   100: train_loss=1.7685  eval_loss=1.7685
  step   150: train_loss=1.5808  eval_loss=1.5808
  step   200: train_loss=1.4624  eval_loss=1.4624
  step   250: train_loss=1.4106  eval_loss=1.4106
  step   300: train_loss=1.3846  eval_loss=1.3846
  step   350: train_loss=1.3705  eval_loss=1.3705
  step   400: train_loss=1.3631  eval_loss=1.3631
  step   450: train_loss=1.3597  eval_loss=1.3597
  step   500: train_loss=1.3585  eval_loss=1.3585

=== ia3_code_instructions ===
  step   100: train_loss=1.0567  eval_loss=1.0567
  step   200: train_loss=0.9900  eval_loss=0.9900
  step   300: train_loss=0.9674  eval_loss=0.9674
  step   400: train_loss=0.9555  eval_loss=0.9555
  step   500: train_loss=0.9467  eval_loss=0.9467
  step   600: train_loss=0.9402  eval_loss=0.9402
  step   700: train_loss=0.9329  eval_loss=0.9329
  step   800: train_loss=0.9301  eval_loss=0.9301
  step   900: train_loss=0.9285  eval_loss=0.9285
  step  1000: train_loss=0.9245  eval_loss=0.9245
  step  1100: train_loss=0.9225  eval_loss=0.9225
  step  1200: train_loss=0.9221  eval_loss=0.9221
  step  1300: train_loss=0.9212  eval_loss=0.9212
  step  1400: train_loss=0.9199  eval_loss=0.9199
  step  1500: train_loss=0.9193  eval_loss=0.9193
  step  1600: train_loss=0.9189  eval_loss=0.9189
  step  1700: train_loss=0.9187  eval_loss=0.9187
  step  1800: train_loss=0.9183  eval_loss=0.9183
  step  1900: train_loss=0.9185  eval_loss=0.9185
  step  2000: train_loss=0.9182  eval_loss=0.9182

=== lora_r16_alpaca ===
  step    50: train_loss=1.3453  eval_loss=1.3453
  step   100: train_loss=1.3061  eval_loss=1.3061
  step   150: train_loss=1.2965  eval_loss=1.2965
  step   200: train_loss=1.2890  eval_loss=1.2890
  step   250: train_loss=1.2870  eval_loss=1.2870
  step   300: train_loss=1.2913  eval_loss=1.2913
  step   350: train_loss=1.2858  eval_loss=1.2858
  step   400: train_loss=1.2854  eval_loss=1.2854
  step   450: train_loss=1.2874  eval_loss=1.2874
  step   500: train_loss=1.2850  eval_loss=1.2850

=== lora_r16_code_instructions ===
  step   100: train_loss=0.9302  eval_loss=0.9302
  step   200: train_loss=0.9189  eval_loss=0.9189
  step   300: train_loss=0.9059  eval_loss=0.9059
  step   400: train_loss=0.9145  eval_loss=0.9145
  step   500: train_loss=0.9081  eval_loss=0.9081
  step   600: train_loss=0.9262  eval_loss=0.9262
  step   700: train_loss=0.9300  eval_loss=0.9300
  step   800: train_loss=0.9616  eval_loss=0.9616
  step   900: train_loss=0.9903  eval_loss=0.9903
  step  1000: train_loss=0.9746  eval_loss=0.9746
  step  1100: train_loss=1.0019  eval_loss=1.0019
  step  1200: train_loss=1.0299  eval_loss=1.0299
  step  1300: train_loss=1.0545  eval_loss=1.0545
  step  1400: train_loss=1.0934  eval_loss=1.0934
  step  1500: train_loss=1.0837  eval_loss=1.0837
  step  1600: train_loss=1.1079  eval_loss=1.1079
  step  1700: train_loss=1.1302  eval_loss=1.1302
  step  1800: train_loss=1.1423  eval_loss=1.1423
  step  1900: train_loss=1.1500  eval_loss=1.1500
  step  2000: train_loss=1.1526  eval_loss=1.1526

=== lora_r16_mlp_alpaca ===
  step   100: train_loss=1.2724  eval_loss=1.2724
  step   200: train_loss=1.2705  eval_loss=1.2705
  step   300: train_loss=1.3309  eval_loss=1.3309
  step   400: train_loss=1.3951  eval_loss=1.3951
  step   500: train_loss=1.4349  eval_loss=1.4349
  step   600: train_loss=1.5341  eval_loss=1.5341
  step   700: train_loss=1.7194  eval_loss=1.7194
  step   800: train_loss=1.8759  eval_loss=1.8759
  step   900: train_loss=1.9592  eval_loss=1.9592
  step  1000: train_loss=1.9748  eval_loss=1.9748
  step  1100: train_loss=2.1193  eval_loss=2.1193
  step  1200: train_loss=2.2358  eval_loss=2.2358
  step  1300: train_loss=2.3121  eval_loss=2.3121
  step  1400: train_loss=2.3703  eval_loss=2.3703
  step  1500: train_loss=2.3682  eval_loss=2.3682
  step  1600: train_loss=2.4315  eval_loss=2.4315
  step  1700: train_loss=2.4552  eval_loss=2.4552
  step  1800: train_loss=2.4854  eval_loss=2.4854
  step  1900: train_loss=2.4845  eval_loss=2.4845
  step  2000: train_loss=2.4983  eval_loss=2.4983

=== lora_r16_mlp_code_instructions ===
  step   100: train_loss=0.8966  eval_loss=0.8966
  step   200: train_loss=0.9022  eval_loss=0.9022
  step   300: train_loss=0.9191  eval_loss=0.9191
  step   400: train_loss=0.9731  eval_loss=0.9731
  step   500: train_loss=0.9578  eval_loss=0.9578
  step   600: train_loss=1.0718  eval_loss=1.0718
  step   700: train_loss=1.1227  eval_loss=1.1227
  step   800: train_loss=1.2635  eval_loss=1.2635
  step   900: train_loss=1.3567  eval_loss=1.3567
  step  1000: train_loss=1.3168  eval_loss=1.3168
  step  1100: train_loss=1.4010  eval_loss=1.4010
  step  1200: train_loss=1.4734  eval_loss=1.4734
  step  1300: train_loss=1.5482  eval_loss=1.5482
  step  1400: train_loss=1.6175  eval_loss=1.6175
  step  1500: train_loss=1.6147  eval_loss=1.6147
  step  1600: train_loss=1.6457  eval_loss=1.6457
  step  1700: train_loss=1.6763  eval_loss=1.6763
  step  1800: train_loss=1.6987  eval_loss=1.6987
  step  1900: train_loss=1.7022  eval_loss=1.7022
  step  2000: train_loss=1.7115  eval_loss=1.7115

=== lora_r32_all_alpaca ===
  step    50: train_loss=1.2900  eval_loss=1.2900
  step   100: train_loss=1.2738  eval_loss=1.2738
  step   150: train_loss=1.2815  eval_loss=1.2815
  step   200: train_loss=1.2785  eval_loss=1.2785
  step   250: train_loss=1.2795  eval_loss=1.2795
  step   300: train_loss=1.3488  eval_loss=1.3488
  step   350: train_loss=1.3515  eval_loss=1.3515
  step   400: train_loss=1.4348  eval_loss=1.4348
  step   450: train_loss=1.4450  eval_loss=1.4450
  step   500: train_loss=1.4411  eval_loss=1.4411

=== lora_r32_all_code_instructions ===
  step   100: train_loss=0.8886  eval_loss=0.8886
  step   200: train_loss=0.9030  eval_loss=0.9030
  step   300: train_loss=0.9429  eval_loss=0.9429
  step   400: train_loss=1.0223  eval_loss=1.0223
  step   500: train_loss=1.0293  eval_loss=1.0293
  step   600: train_loss=1.1422  eval_loss=1.1422
  step   700: train_loss=1.2154  eval_loss=1.2154
  step   800: train_loss=1.3218  eval_loss=1.3218
  step   900: train_loss=1.4070  eval_loss=1.4070
  step  1000: train_loss=1.3586  eval_loss=1.3586
  step  1100: train_loss=1.4138  eval_loss=1.4138
  step  1200: train_loss=1.4756  eval_loss=1.4756
  step  1300: train_loss=1.5353  eval_loss=1.5353
  step  1400: train_loss=1.5881  eval_loss=1.5881
  step  1500: train_loss=1.5806  eval_loss=1.5806
  step  1600: train_loss=1.6064  eval_loss=1.6064
  step  1700: train_loss=1.6373  eval_loss=1.6373
  step  1800: train_loss=1.6632  eval_loss=1.6632
  step  1900: train_loss=1.6641  eval_loss=1.6641
  step  2000: train_loss=1.6717  eval_loss=1.6717

=== lora_r4_alpaca ===
  step    50: train_loss=1.4845  eval_loss=1.4845
  step   100: train_loss=1.3345  eval_loss=1.3345
  step   150: train_loss=1.3157  eval_loss=1.3157
  step   200: train_loss=1.3049  eval_loss=1.3049
  step   250: train_loss=1.2995  eval_loss=1.2995
  step   300: train_loss=1.2987  eval_loss=1.2987
  step   350: train_loss=1.2952  eval_loss=1.2952
  step   400: train_loss=1.2928  eval_loss=1.2928
  step   450: train_loss=1.2936  eval_loss=1.2936
  step   500: train_loss=1.2924  eval_loss=1.2924

=== lora_r4_code_instructions ===
  step   100: train_loss=0.9525  eval_loss=0.9525
  step   200: train_loss=0.9320  eval_loss=0.9320
  step   300: train_loss=0.9141  eval_loss=0.9141
  step   400: train_loss=0.9129  eval_loss=0.9129
  step   500: train_loss=0.9067  eval_loss=0.9067
  step   600: train_loss=0.9131  eval_loss=0.9131
  step   700: train_loss=0.9046  eval_loss=0.9046
  step   800: train_loss=0.9166  eval_loss=0.9166
  step   900: train_loss=0.9181  eval_loss=0.9181
  step  1000: train_loss=0.9121  eval_loss=0.9121
  step  1100: train_loss=0.9156  eval_loss=0.9156
  step  1200: train_loss=0.9232  eval_loss=0.9232
  step  1300: train_loss=0.9257  eval_loss=0.9257
  step  1400: train_loss=0.9301  eval_loss=0.9301
  step  1500: train_loss=0.9351  eval_loss=0.9351
  step  1600: train_loss=0.9383  eval_loss=0.9383
  step  1700: train_loss=0.9406  eval_loss=0.9406
  step  1800: train_loss=0.9462  eval_loss=0.9462
  step  1900: train_loss=0.9463  eval_loss=0.9463
  step  2000: train_loss=0.9458  eval_loss=0.9458
```
</details>

### Step 20: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# For each run, get the train loss trajectory (rows where learning_rate is not NaN = training logs)
# and eval_loss trajectory, then compute the divergence
runs = sorted(smol['run_name'].unique())

print('RUN | MAX_STEPS | TRAIN_LOSS_START | TRAIN_LOSS_END | EVAL_LOSS_MIN | EVAL_LOSS_MIN_STEP | EVAL_LOSS_END | DIVERGENCE')
print('-' * 120)
for run in runs:
    run_df = smol[smol['run_name'] == run]
    train_df = run_df[run_df['learning_rate'].notna()].copy()
    eval_df = run_df[run_df['eval_loss'].notna()].copy()
    
    max_step = int(train_df['step'].max()) if len(train_df) > 0 else 0
    train_start = train_df.iloc[0]['loss'] if len(train_df) > 0 else np.nan
    train_end = train_df.iloc[-1]['loss'] if len(train_df) > 0 else np.nan
    
    if len(eval_df) > 0:
        eval_min_idx = eval_df['eval_loss'].idxmin()
        eval_min = eval_df.loc[eval_min_idx, 'eval_loss']
        eval_min_step = int(eval_df.loc[eval_min_idx, 'step'])
        eval_end = eval_df.iloc[-1]['eval_loss']
        divergence = eval_end - eval_min
    else:
        eval_min = np.nan
        eval_min_step = 0
        eval_end = np.nan
        divergence = np.nan
    
    print(f'{run:40s} | {max_step:4d} | {train_start:.4f} | {train_end:.4f} | {eval_min:.4f} | {eval_min_step:4d} | {eval_end:.4f} | {divergence:+.4f}')
"
```

<details><summary>Output (1854 chars)</summary>

```
RUN | MAX_STEPS | TRAIN_LOSS_START | TRAIN_LOSS_END | EVAL_LOSS_MIN | EVAL_LOSS_MIN_STEP | EVAL_LOSS_END | DIVERGENCE
------------------------------------------------------------------------------------------------------------------------
adalora_alpaca                           |  500 | 3.9663 | 1.3415 | 1.3317 |  500 | 1.3317 | +0.0000
adalora_code_instructions                | 2000 | 2.8974 | 0.8018 | 0.9160 | 1600 | 0.9168 | +0.0008
dora_r8_alpaca                           | 2000 | 2.3938 | 0.9670 | 1.2859 |  400 | 1.3838 | +0.0978
dora_r8_code_instructions                | 2000 | 1.2930 | 0.5657 | 0.9049 |  500 | 1.0175 | +0.1126
full_ft_alpaca                           |  500 | 2.1625 | 1.1045 | 1.2712 |  350 | 1.2727 | +0.0015
full_ft_code_instructions                | 2000 | 1.2569 | 0.3230 | 0.8899 |  500 | 1.0975 | +0.2076
ia3_alpaca                               |  500 | 2.3661 | 1.3538 | 1.3585 |  500 | 1.3585 | +0.0000
ia3_code_instructions                    | 2000 | 1.2997 | 0.7925 | 0.9182 | 2000 | 0.9182 | +0.0000
lora_r16_alpaca                          |  500 | 2.2299 | 1.2096 | 1.2850 |  500 | 1.2850 | +0.0000
lora_r16_code_instructions               | 2000 | 1.2795 | 0.4205 | 0.9059 |  300 | 1.1526 | +0.2467
lora_r16_mlp_alpaca                      | 2000 | 2.2572 | 0.0936 | 1.2705 |  200 | 2.4983 | +1.2278
lora_r16_mlp_code_instructions           | 2000 | 1.2021 | 0.0977 | 0.8966 |  100 | 1.7115 | +0.8149
lora_r32_all_alpaca                      |  500 | 1.6789 | 0.6826 | 1.2738 |  100 | 1.4411 | +0.1673
lora_r32_all_code_instructions           | 2000 | 1.1250 | 0.0853 | 0.8886 |  100 | 1.6717 | +0.7831
lora_r4_alpaca                           |  500 | 2.3704 | 1.2701 | 1.2924 |  500 | 1.2924 | +0.0000
lora_r4_code_instructions                | 2000 | 1.3014 | 0.6762 | 0.9046 |  700 | 0.9458 | +0.0413
```
</details>

### Step 21: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# Also show the train loss in the same windowed eval steps for the key runs
# Specifically look at the train_loss at the eval steps to see the gap
runs_to_examine = ['lora_r32_all_alpaca', 'lora_r32_all_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_mlp_code_instructions', 
                   'full_ft_code_instructions', 'lora_r16_code_instructions', 'dora_r8_code_instructions',
                   'lora_r4_code_instructions', 'ia3_code_instructions', 'adalora_code_instructions']

for run in runs_to_examine:
    run_df = smol[smol['run_name'] == run]
    eval_df = run_df[run_df['eval_loss'].notna()].copy()
    train_df = run_df[run_df['learning_rate'].notna()].copy()
    
    print(f'\n=== {run} (train vs eval at checkpoint steps) ===')
    print(f'  {\"Step\":>5s}  {\"TrainLoss\":>10s}  {\"EvalLoss\":>10s}  {\"Gap\":>8s}')
    
    for _, erow in eval_df.iterrows():
        step = int(erow['step'])
        eval_loss = erow['eval_loss']
        # find closest train loss at this step
        closest = train_df.iloc[(train_df['step'] - step).abs().argsort()[:1]]
        if len(closest) > 0:
            train_loss = closest.iloc[0]['loss']
            gap = eval_loss - train_loss
            print(f'  {step:5d}  {train_loss:10.4f}  {eval_loss:10.4f}  {gap:+8.4f}')
"
```

<details><summary>Output (9103 chars)</summary>

```
=== lora_r32_all_alpaca (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
     50      1.2900      1.2900   +0.0000
    100      1.3254      1.2738   -0.0516
    150      1.0242      1.2815   +0.2574
    200      1.0837      1.2785   +0.1947
    250      1.0818      1.2795   +0.1977
    300      0.8347      1.3488   +0.5141
    350      0.8677      1.3515   +0.4838
    400      0.6877      1.4348   +0.7471
    450      0.6610      1.4450   +0.7841
    500      0.6826      1.4411   +0.7585

=== lora_r32_all_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.7835      0.8886   +0.1051
    200      0.6114      0.9030   +0.2916
    300      0.5211      0.9429   +0.4218
    400      0.3568      1.0223   +0.6655
    500      0.4120      1.0293   +0.6172
    600      0.3310      1.1422   +0.8113
    700      0.2350      1.2154   +0.9804
    800      0.1828      1.3218   +1.1391
    900      0.1747      1.4070   +1.2323
   1000      0.1622      1.3586   +1.1964
   1100      0.1351      1.4138   +1.2787
   1200      0.1394      1.4756   +1.3362
   1300      0.0994      1.5353   +1.4359
   1400      0.0764      1.5881   +1.5117
   1500      0.1019      1.5806   +1.4787
   1600      0.0978      1.6064   +1.5086
   1700      0.0784      1.6373   +1.5589
   1800      0.0981      1.6632   +1.5652
   1900      0.0696      1.6641   +1.5945
   2000      0.0853      1.6717   +1.5864

=== lora_r16_mlp_alpaca (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      1.2406      1.2724   +0.0318
    200      1.1633      1.2705   +0.1072
    300      1.0519      1.3309   +0.2790
    400      0.7864      1.3951   +0.6087
    500      0.8195      1.4349   +0.6153
    600      0.6645      1.5341   +0.8696
    700      0.4105      1.7194   +1.3089
    800      0.3751      1.8759   +1.5008
    900      0.2227      1.9592   +1.7366
   1000      0.2732      1.9748   +1.7016
   1100      0.1886      2.1193   +1.9307
   1200      0.1745      2.2358   +2.0613
   1300      0.1397      2.3121   +2.1724
   1400      0.1117      2.3703   +2.2586
   1500      0.1143      2.3682   +2.2539
   1600      0.1259      2.4315   +2.3056
   1700      0.1081      2.4552   +2.3471
   1800      0.0992      2.4854   +2.3863
   1900      0.0875      2.4845   +2.3970
   2000      0.0936      2.4983   +2.4047

=== lora_r16_mlp_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.7744      0.8966   +0.1221
    200      0.6523      0.9022   +0.2499
    300      0.6192      0.9191   +0.3000
    400      0.4478      0.9731   +0.5253
    500      0.5012      0.9578   +0.4566
    600      0.4475      1.0718   +0.6243
    700      0.3504      1.1227   +0.7723
    800      0.2644      1.2635   +0.9991
    900      0.2325      1.3567   +1.1242
   1000      0.2047      1.3168   +1.1121
   1100      0.1863      1.4010   +1.2147
   1200      0.1706      1.4734   +1.3027
   1300      0.1223      1.5482   +1.4259
   1400      0.0971      1.6175   +1.5204
   1500      0.1196      1.6147   +1.4951
   1600      0.1169      1.6457   +1.5288
   1700      0.0918      1.6763   +1.5845
   1800      0.1076      1.6987   +1.5911
   1900      0.0816      1.7022   +1.6206
   2000      0.0977      1.7115   +1.6137

=== full_ft_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.7952      0.9157   +0.1205
    200      0.6526      0.8970   +0.2444
    300      0.6615      0.8902   +0.2288
    400      0.5524      0.8944   +0.3420
    500      0.6085      0.8899   +0.2814
    600      0.6162      0.9035   +0.2874
    700      0.6335      0.9171   +0.2835
    800      0.5110      0.9434   +0.4325
    900      0.6008      0.9649   +0.3641
   1000      0.3723      0.9618   +0.5895
   1100      0.5181      0.9841   +0.4660
   1200      0.4165      1.0108   +0.5943
   1300      0.3507      1.0288   +0.6781
   1400      0.3097      1.0457   +0.7360
   1500      0.3531      1.0521   +0.6990
   1600      0.3920      1.0718   +0.6798
   1700      0.3303      1.0816   +0.7513
   1800      0.3402      1.0889   +0.7487
   1900      0.2933      1.0967   +0.8034
   2000      0.3230      1.0975   +0.7745

=== lora_r16_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.8073      0.9302   +0.1229
    200      0.7185      0.9189   +0.2004
    300      0.7589      0.9059   +0.1471
    400      0.6549      0.9145   +0.2596
    500      0.7017      0.9081   +0.2064
    600      0.7312      0.9262   +0.1950
    700      0.7735      0.9300   +0.1565
    800      0.6152      0.9616   +0.3463
    900      0.7364      0.9903   +0.2539
   1000      0.4716      0.9746   +0.5030
   1100      0.6691      1.0019   +0.3328
   1200      0.5296      1.0299   +0.5003
   1300      0.4560      1.0545   +0.5985
   1400      0.4234      1.0934   +0.6700
   1500      0.4746      1.0837   +0.6092
   1600      0.4959      1.1079   +0.6120
   1700      0.4612      1.1302   +0.6690
   1800      0.4373      1.1423   +0.7050
   1900      0.3897      1.1500   +0.7603
   2000      0.4205      1.1526   +0.7321

=== dora_r8_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.8204      0.9396   +0.1192
    200      0.7253      0.9259   +0.2006
    300      0.7845      0.9097   +0.1252
    400      0.6925      0.9125   +0.2200
    500      0.7380      0.9049   +0.1669
    600      0.7773      0.9168   +0.1395
    700      0.8372      0.9117   +0.0745
    800      0.6865      0.9317   +0.2452
    900      0.8316      0.9366   +0.1050
   1000      0.5270      0.9312   +0.4042
   1100      0.7653      0.9489   +0.1837
   1200      0.6277      0.9576   +0.3299
   1300      0.5429      0.9727   +0.4299
   1400      0.5440      0.9851   +0.4411
   1500      0.5833      0.9902   +0.4069
   1600      0.6300      0.9984   +0.3684
   1700      0.5728      1.0079   +0.4351
   1800      0.5797      1.0150   +0.4353
   1900      0.5121      1.0179   +0.5058
   2000      0.5657      1.0175   +0.4517

=== lora_r4_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.8315      0.9525   +0.1210
    200      0.7292      0.9320   +0.2028
    300      0.8056      0.9141   +0.1085
    400      0.7141      0.9129   +0.1987
    500      0.7659      0.9067   +0.1407
    600      0.8079      0.9131   +0.1052
    700      0.8888      0.9046   +0.0157
    800      0.7385      0.9166   +0.1781
    900      0.9054      0.9181   +0.0128
   1000      0.5591      0.9121   +0.3530
   1100      0.8377      0.9156   +0.0779
   1200      0.6958      0.9232   +0.2274
   1300      0.6174      0.9257   +0.3083
   1400      0.6320      0.9301   +0.2981
   1500      0.6702      0.9351   +0.2649
   1600      0.7451      0.9383   +0.1932
   1700      0.6540      0.9406   +0.2865
   1800      0.6796      0.9462   +0.2666
   1900      0.6029      0.9463   +0.3433
   2000      0.6762      0.9458   +0.2697

=== ia3_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      0.9314      1.0567   +0.1253
    200      0.7937      0.9900   +0.1964
    300      0.8487      0.9674   +0.1187
    400      0.7660      0.9555   +0.1896
    500      0.8142      0.9467   +0.1325
    600      0.8714      0.9402   +0.0688
    700      0.9549      0.9329   -0.0220
    800      0.8176      0.9301   +0.1126
    900      1.0003      0.9285   -0.0718
   1000      0.6220      0.9245   +0.3024
   1100      0.9329      0.9225   -0.0104
   1200      0.7770      0.9221   +0.1451
   1300      0.6963      0.9212   +0.2249
   1400      0.7431      0.9199   +0.1768
   1500      0.7813      0.9193   +0.1380
   1600      0.8786      0.9189   +0.0404
   1700      0.7407      0.9187   +0.1781
   1800      0.7993      0.9183   +0.1190
   1900      0.7041      0.9185   +0.2143
   2000      0.7925      0.9182   +0.1257

=== adalora_code_instructions (train vs eval at checkpoint steps) ===
   Step   TrainLoss    EvalLoss       Gap
    100      1.1983      1.2917   +0.0935
    200      0.8133      1.0032   +0.1899
    300      0.8629      0.9617   +0.0988
    400      0.7773      0.9495   +0.1722
    500      0.8278      0.9391   +0.1113
    600      0.8898      0.9348   +0.0450
    700      0.9709      0.9267   -0.0442
    800      0.8291      0.9249   +0.0958
    900      1.0103      0.9250   -0.0853
   1000      0.6320      0.9203   +0.2882
   1100      0.9323      0.9179   -0.0144
   1200      0.7915      0.9198   +0.1283
   1300      0.7081      0.9164   +0.2083
   1400      0.7474      0.9178   +0.1705
   1500      0.7873      0.9169   +0.1295
   1600      0.8909      0.9160   +0.0251
   1700      0.7531      0.9169   +0.1639
   1800      0.8035      0.9175   +0.1140
   1900      0.7074      0.9173   +0.2098
   2000      0.8018      0.9168   +0.1150
```
</details>

### Step 22: bash

```bash
for run in lora_r32_all_alpaca lora_r32_all_code_instructions lora_r16_mlp_alpaca lora_r16_mlp_code_instructions lora_r16_alpaca lora_r4_alpaca lora_r16_code_instructions ia3_alpaca adalora_alpaca dora_r8_alpaca full_ft_alpaca; do
  echo "=== $run ==="
  cat /home/ubuntu/workspace/training-export-proprietary/runs/$run/adapter_config.json 2>/dev/null | python3 -c "import sys,json; d=json.load(sys.stdin); print(json.dumps({k:d[k] for k in ['peft_type','r','lora_alpha','target_modules','lora_dropout','bias','task_type'] if k in d}, indent=2))" 2>/dev/null || echo "(no adapter_config or parse error)"
  echo ""
done
```

<details><summary>Output (2307 chars)</summary>

```
=== lora_r32_all_alpaca ===
{
  "peft_type": "LORA",
  "r": 32,
  "lora_alpha": 64,
  "target_modules": [
    "up_proj",
    "q_proj",
    "k_proj",
    "gate_proj",
    "o_proj",
    "down_proj",
    "v_proj"
  ],
  "lora_dropout": 0.1,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== lora_r32_all_code_instructions ===
{
  "peft_type": "LORA",
  "r": 32,
  "lora_alpha": 64,
  "target_modules": [
    "q_proj",
    "k_proj",
    "v_proj",
    "o_proj",
    "up_proj",
    "gate_proj",
    "down_proj"
  ],
  "lora_dropout": 0.1,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== lora_r16_mlp_alpaca ===
{
  "peft_type": "LORA",
  "r": 16,
  "lora_alpha": 32,
  "target_modules": [
    "up_proj",
    "gate_proj",
    "down_proj"
  ],
  "lora_dropout": 0.05,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== lora_r16_mlp_code_instructions ===
{
  "peft_type": "LORA",
  "r": 16,
  "lora_alpha": 32,
  "target_modules": [
    "up_proj",
    "gate_proj",
    "down_proj"
  ],
  "lora_dropout": 0.05,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== lora_r16_alpaca ===
{
  "peft_type": "LORA",
  "r": 16,
  "lora_alpha": 32,
  "target_modules": [
    "q_proj",
    "v_proj"
  ],
  "lora_dropout": 0.05,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== lora_r4_alpaca ===
{
  "peft_type": "LORA",
  "r": 4,
  "lora_alpha": 8,
  "target_modules": [
    "q_proj",
    "v_proj"
  ],
  "lora_dropout": 0.05,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== lora_r16_code_instructions ===
{
  "peft_type": "LORA",
  "r": 16,
  "lora_alpha": 32,
  "target_modules": [
    "q_proj",
    "v_proj"
  ],
  "lora_dropout": 0.05,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== ia3_alpaca ===
{
  "peft_type": "IA3",
  "target_modules": [
    "v_proj",
    "q_proj",
    "down_proj",
    "k_proj"
  ],
  "task_type": "CAUSAL_LM"
}

=== adalora_alpaca ===
{
  "peft_type": "ADALORA",
  "r": 8,
  "lora_alpha": 32,
  "target_modules": [
    "q_proj",
    "v_proj"
  ],
  "lora_dropout": 0.0,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== dora_r8_alpaca ===
{
  "peft_type": "LORA",
  "r": 8,
  "lora_alpha": 16,
  "target_modules": [
    "q_proj",
    "v_proj"
  ],
  "lora_dropout": 0.05,
  "bias": "none",
  "task_type": "CAUSAL_LM"
}

=== full_ft_alpaca ===
(no adapter_config or parse error)
```
</details>

### Step 23: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# Compute grad_norm trends (first 25% vs last 25%)
runs = sorted(smol['run_name'].unique())
print(f'{\"Run\":>40s} | {\"Steps\":>5s} | {\"GradNorm_Early\":>14s} | {\"GradNorm_Late\":>14s} | {\"Ratio\":>8s}')
print('-'*95)
for run in runs:
    run_df = smol[smol['run_name'] == run]
    train_df = run_df[run_df['learning_rate'].notna()].copy()
    if len(train_df) == 0 or train_df['grad_norm'].isna().all():
        continue
    max_step = train_df['step'].max()
    early = train_df[train_df['step'] <= max_step*0.25]['grad_norm'].mean()
    late = train_df[train_df['step'] >= max_step*0.75]['grad_norm'].mean()
    ratio = late / early if early and early > 0 else float('nan')
    print(f'{run:>40s} | {int(max_step):5d} | {early:14.4f} | {late:14.4f} | {ratio:8.2f}')
"
```

<details><summary>Output (1693 chars)</summary>

```
                                     Run | Steps | GradNorm_Early |  GradNorm_Late |    Ratio
-----------------------------------------------------------------------------------------------
                          adalora_alpaca |   500 |         0.1783 |         0.2871 |     1.61
               adalora_code_instructions |  2000 |         0.2054 |         0.2962 |     1.44
                          dora_r8_alpaca |  2000 |         0.4691 |         0.7742 |     1.65
               dora_r8_code_instructions |  2000 |         0.4453 |         0.7717 |     1.73
                          full_ft_alpaca |   500 |         3.1627 |         2.5617 |     0.81
               full_ft_code_instructions |  2000 |         2.7384 |         2.4896 |     0.91
                              ia3_alpaca |   500 |         0.3688 |         0.2954 |     0.80
                   ia3_code_instructions |  2000 |         0.2996 |         0.2877 |     0.96
                         lora_r16_alpaca |   500 |         0.5470 |         0.4654 |     0.85
              lora_r16_code_instructions |  2000 |         0.4448 |         0.7800 |     1.75
                     lora_r16_mlp_alpaca |  2000 |         0.4582 |         0.3308 |     0.72
          lora_r16_mlp_code_instructions |  2000 |         0.4207 |         0.3364 |     0.80
                     lora_r32_all_alpaca |   500 |         0.4930 |         0.6099 |     1.24
          lora_r32_all_code_instructions |  2000 |         0.4839 |         0.2168 |     0.45
                          lora_r4_alpaca |   500 |         0.4528 |         0.4344 |     0.96
               lora_r4_code_instructions |  2000 |         0.4511 |         0.7289 |     1.62
```
</details>

### Step 24: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# For each run, compute the train loss trajectory in windowed averages (smoothed)
# to compare with eval loss divergence
# Show the rolling average of train loss
runs = sorted(smol['run_name'].unique())

# For the key comparison, show train loss at 25%, 50%, 75%, 100% of training
print(f'{\"Run\":>40s} | {\"Train_25%\":>9s} | {\"Train_50%\":>9s} | {\"Train_75%\":>9s} | {\"Train_100%\":>10s} | {\"Eval_25%\":>9s} | {\"Eval_50%\":>9s} | {\"Eval_75%\":>9s} | {\"Eval_100%\":>10s}')
print('-' * 130)
for run in runs:
    run_df = smol[smol['run_name'] == run]
    train_df = run_df[run_df['learning_rate'].notna()].copy()
    eval_df = run_df[run_df['eval_loss'].notna()].copy()
    if len(train_df) == 0:
        continue
    max_step = train_df['step'].max()
    
    def avg_window(df, col, lo, hi, max_s):
        mask = (df['step'] >= lo*max_s) & (df['step'] <= hi*max_s)
        vals = df.loc[mask, col]
        return vals.mean() if len(vals) > 0 else np.nan
    
    t25 = avg_window(train_df, 'loss', 0.0, 0.25, max_step)
    t50 = avg_window(train_df, 'loss', 0.25, 0.5, max_step)
    t75 = avg_window(train_df, 'loss', 0.5, 0.75, max_step)
    t100 = avg_window(train_df, 'loss', 0.75, 1.01, max_step)
    
    e25 = avg_window(eval_df, 'eval_loss', 0.0, 0.25, max_step) if len(eval_df) > 0 else np.nan
    e50 = avg_window(eval_df, 'eval_loss', 0.25, 0.5, max_step) if len(eval_df) > 0 else np.nan
    e75 = avg_window(eval_df, 'eval_loss', 0.5, 0.75, max_step) if len(eval_df) > 0 else np.nan
    e100 = avg_window(eval_df, 'eval_loss', 0.75, 1.01, max_step) if len(eval_df) > 0 else np.nan
    
    print(f'{run:>40s} | {t25:9.4f} | {t50:9.4f} | {t75:9.4f} | {t100:10.4f} | {e25:9.4f} | {e50:9.4f} | {e75:9.4f} | {e100:10.4f}')
"
```

<details><summary>Output (2493 chars)</summary>

```
                                     Run | Train_25% | Train_50% | Train_75% | Train_100% |  Eval_25% |  Eval_50% |  Eval_75% |  Eval_100%
----------------------------------------------------------------------------------------------------------------------------------
                          adalora_alpaca |    2.9359 |    1.6183 |    1.3746 |     1.3236 |    2.5274 |    1.5427 |    1.3627 |     1.3338
               adalora_code_instructions |    1.1582 |    0.8530 |    0.8164 |     0.7953 |    1.0290 |    0.9284 |    0.9182 |     0.9169
                          dora_r8_alpaca |    1.3123 |    1.1365 |    1.0349 |     0.9744 |    1.2944 |    1.3033 |    1.3396 |     1.3718
               dora_r8_code_instructions |    0.8665 |    0.7241 |    0.6304 |     0.5742 |    0.9185 |    0.9222 |    0.9643 |     1.0078
                          full_ft_alpaca |    1.4854 |    1.1867 |    1.1506 |     1.0941 |    1.3131 |    1.2779 |    1.2719 |     1.2725
               full_ft_code_instructions |    0.7709 |    0.5340 |    0.4005 |     0.3314 |    0.8975 |    0.9301 |    1.0139 |     1.0814
                              ia3_alpaca |    2.0415 |    1.4985 |    1.3833 |     1.3330 |    1.9007 |    1.4846 |    1.3886 |     1.3604
                   ia3_code_instructions |    0.9638 |    0.8375 |    0.8028 |     0.7865 |    0.9833 |    0.9338 |    0.9216 |     0.9187
                         lora_r16_alpaca |    1.4921 |    1.2463 |    1.2397 |     1.1951 |    1.3257 |    1.2908 |    1.2880 |     1.2859
              lora_r16_code_instructions |    0.8410 |    0.6574 |    0.5251 |     0.4466 |    0.9155 |    0.9485 |    1.0397 |     1.1278
                     lora_r16_mlp_alpaca |    1.0813 |    0.4302 |    0.1561 |     0.1009 |    1.3407 |    1.7497 |    2.2301 |     2.4539
          lora_r16_mlp_code_instructions |    0.7130 |    0.3166 |    0.1452 |     0.1014 |    0.9298 |    1.1815 |    1.4953 |     1.6748
                     lora_r32_all_alpaca |    1.3413 |    1.0596 |    0.8815 |     0.6854 |    1.2819 |    1.2798 |    1.3266 |     1.4403
          lora_r32_all_code_instructions |    0.6421 |    0.2280 |    0.1138 |     0.0873 |    0.9572 |    1.2457 |    1.4920 |     1.6372
                          lora_r4_alpaca |    1.6510 |    1.2816 |    1.2851 |     1.2520 |    1.4095 |    1.3067 |    1.2978 |     1.2929
               lora_r4_code_instructions |    0.8908 |    0.7729 |    0.7104 |     0.6731 |    0.9236 |    0.9119 |    0.9236 |     0.9420
```
</details>

### Step 25: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json

for run in ['lora_r32_all_alpaca', 'lora_r32_all_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_mlp_code_instructions', 'lora_r16_alpaca', 'lora_r4_alpaca']:
    try:
        with open(f'runs/{run}/adapter_weight_stats.json') as f:
            stats = json.load(f)
        # Show top-level structure
        if isinstance(stats, dict):
            print(f'=== {run} ===')
            keys = list(stats.keys())[:5]
            print(f'  Keys: {keys}')
            # Show first entry
            for k in keys[:2]:
                v = stats[k]
                if isinstance(v, dict):
                    print(f'  {k}: {list(v.keys())[:5]}')
                    for vk in list(v.keys())[:3]:
                        print(f'    {vk}: {v[vk]}')
                else:
                    print(f'  {k}: {v}')
        elif isinstance(stats, list):
            print(f'=== {run} === (list of {len(stats)} items)')
            print(f'  First item: {json.dumps(stats[0], indent=2)[:500]}')
        print()
    except Exception as e:
        print(f'=== {run} === ERROR: {e}')
        print()
"
```

<details><summary>Output (4769 chars)</summary>

```
=== lora_r32_all_alpaca ===
  Keys: ['base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.k_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.k_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_A.default.weight']
  base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [32, 576]
    num_params: 18432
    mean: 8.278754103230312e-05
  base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [576, 32]
    num_params: 18432
    mean: 1.4135112905933056e-05

=== lora_r32_all_code_instructions ===
  Keys: ['base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.k_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.k_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_A.default.weight']
  base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [32, 576]
    num_params: 18432
    mean: -2.5455254217376933e-05
  base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [576, 32]
    num_params: 18432
    mean: 3.757287049666047e-05

=== lora_r16_mlp_alpaca ===
  Keys: ['base_model.model.model.layers.0.mlp.gate_proj.lora_A.default.weight', 'base_model.model.model.layers.0.mlp.gate_proj.lora_B.default.weight', 'base_model.model.model.layers.0.mlp.up_proj.lora_A.default.weight', 'base_model.model.model.layers.0.mlp.up_proj.lora_B.default.weight', 'base_model.model.model.layers.0.mlp.down_proj.lora_A.default.weight']
  base_model.model.model.layers.0.mlp.gate_proj.lora_A.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [16, 576]
    num_params: 9216
    mean: -0.00027835307992063463
  base_model.model.model.layers.0.mlp.gate_proj.lora_B.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [1536, 16]
    num_params: 24576
    mean: -0.0006132174166850746

=== lora_r16_mlp_code_instructions ===
  Keys: ['base_model.model.model.layers.0.mlp.gate_proj.lora_A.default.weight', 'base_model.model.model.layers.0.mlp.gate_proj.lora_B.default.weight', 'base_model.model.model.layers.0.mlp.up_proj.lora_A.default.weight', 'base_model.model.model.layers.0.mlp.up_proj.lora_B.default.weight', 'base_model.model.model.layers.0.mlp.down_proj.lora_A.default.weight']
  base_model.model.model.layers.0.mlp.gate_proj.lora_A.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [16, 576]
    num_params: 9216
    mean: -0.0005185520858503878
  base_model.model.model.layers.0.mlp.gate_proj.lora_B.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [1536, 16]
    num_params: 24576
    mean: 0.00011305411317152902

=== lora_r16_alpaca ===
  Keys: ['base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_B.default.weight', 'base_model.model.model.layers.1.self_attn.q_proj.lora_A.default.weight']
  base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [16, 576]
    num_params: 9216
    mean: -0.0001500287908129394
  base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [576, 16]
    num_params: 9216
    mean: -5.1450656428642105e-06

=== lora_r4_alpaca ===
  Keys: ['base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_B.default.weight', 'base_model.model.model.layers.1.self_attn.q_proj.lora_A.default.weight']
  base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [4, 576]
    num_params: 2304
    mean: 0.00045009111636318266
  base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight: ['shape', 'num_params', 'mean', 'std', 'norm']
    shape: [576, 4]
    num_params: 2304
    mean: -0.00010187891166424379
```
</details>

### Step 26: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json
import numpy as np

# Compare adapter weight norms across runs
runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'lora_r16_mlp_alpaca',
        'lora_r4_code_instructions', 'lora_r16_code_instructions', 'lora_r32_all_code_instructions', 'lora_r16_mlp_code_instructions']

for run in runs:
    with open(f'runs/{run}/adapter_weight_stats.json') as f:
        stats = json.load(f)
    
    # Collect all B matrix norms (the update magnitude)
    b_norms = []
    a_norms = []
    for key, val in stats.items():
        if '.lora_B.' in key and 'norm' in val:
            b_norms.append(val['norm'])
        if '.lora_A.' in key and 'norm' in val:
            a_norms.append(val['norm'])
    
    if b_norms:
        print(f'{run:45s} | B_norms: mean={np.mean(b_norms):.6f} max={np.max(b_norms):.6f} min={np.min(b_norms):.6f} | A_norms: mean={np.mean(a_norms):.6f} max={np.max(a_norms):.6f}')
    else:
        print(f'{run:45s} | No B norms found')
"
```

<details><summary>Output (1079 chars)</summary>

```
lora_r4_alpaca                                | B_norms: mean=0.691288 max=1.037621 min=0.381336 | A_norms: mean=1.678183 max=1.997572
lora_r16_alpaca                               | B_norms: mean=0.891776 max=1.366370 min=0.478331 | A_norms: mean=2.812618 max=3.183390
lora_r32_all_alpaca                           | B_norms: mean=1.236518 max=2.310783 min=0.422512 | A_norms: mean=3.797951 max=4.477259
lora_r16_mlp_alpaca                           | B_norms: mean=3.042427 max=4.190572 min=1.270104 | A_norms: mean=4.743719 max=6.166615
lora_r4_code_instructions                     | B_norms: mean=1.185387 max=2.037512 min=0.533328 | A_norms: mean=2.503266 max=3.062657
lora_r16_code_instructions                    | B_norms: mean=1.966204 max=3.282027 min=0.890994 | A_norms: mean=4.140531 max=4.981822
lora_r32_all_code_instructions                | B_norms: mean=2.125558 max=4.215839 min=0.616499 | A_norms: mean=4.364107 max=5.857017
lora_r16_mlp_code_instructions                | B_norms: mean=2.624478 max=3.532342 min=1.168700 | A_norms: mean=4.107910 max=4.934408
```
</details>

### Step 27: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json
import numpy as np

# For the problematic runs, look at per-layer B norms to see which layers have the largest updates
for run in ['lora_r32_all_alpaca', 'lora_r32_all_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_alpaca']:
    with open(f'runs/{run}/adapter_weight_stats.json') as f:
        stats = json.load(f)
    
    print(f'=== {run} ===')
    # Group by module type and layer
    by_module = {}
    for key, val in stats.items():
        if '.lora_B.' not in key or 'norm' not in val:
            continue
        # Extract module type and layer
        parts = key.split('.')
        layer_idx = None
        module_type = None
        for i, p in enumerate(parts):
            if p == 'layers':
                layer_idx = int(parts[i+1])
            if p in ['q_proj', 'k_proj', 'v_proj', 'o_proj', 'gate_proj', 'up_proj', 'down_proj']:
                module_type = p
        
        if layer_idx is not None and module_type is not None:
            mt = f'layer_{layer_idx:02d}_{module_type}'
            by_module[mt] = val['norm']
    
    # Show all entries sorted
    for k in sorted(by_module.keys()):
        print(f'  {k}: {by_module[k]:.6f}')
    print()
" | head -80
```

<details><summary>Output (2446 chars)</summary>

```
=== lora_r32_all_alpaca ===
  layer_00_down_proj: 1.120445
  layer_00_gate_proj: 1.882886
  layer_00_k_proj: 0.507286
  layer_00_o_proj: 0.805347
  layer_00_q_proj: 1.056743
  layer_00_up_proj: 1.750211
  layer_00_v_proj: 0.438250
  layer_01_down_proj: 0.967557
  layer_01_gate_proj: 1.829075
  layer_01_k_proj: 0.541411
  layer_01_o_proj: 0.870691
  layer_01_q_proj: 0.974326
  layer_01_up_proj: 1.767043
  layer_01_v_proj: 0.482334
  layer_02_down_proj: 0.784003
  layer_02_gate_proj: 1.878810
  layer_02_k_proj: 0.634806
  layer_02_o_proj: 0.996220
  layer_02_q_proj: 1.021009
  layer_02_up_proj: 1.800722
  layer_02_v_proj: 0.493253
  layer_03_down_proj: 1.216371
  layer_03_gate_proj: 1.911236
  layer_03_k_proj: 0.569394
  layer_03_o_proj: 1.060903
  layer_03_q_proj: 1.036460
  layer_03_up_proj: 1.816402
  layer_03_v_proj: 0.422512
  layer_04_down_proj: 1.223971
  layer_04_gate_proj: 1.904513
  layer_04_k_proj: 0.577718
  layer_04_o_proj: 1.062259
  layer_04_q_proj: 1.023808
  layer_04_up_proj: 1.844590
  layer_04_v_proj: 0.438220
  layer_05_down_proj: 1.205312
  layer_05_gate_proj: 1.951772
  layer_05_k_proj: 0.582200
  layer_05_o_proj: 1.098934
  layer_05_q_proj: 1.006970
  layer_05_up_proj: 1.876004
  layer_05_v_proj: 0.444873
  layer_06_down_proj: 1.264352
  layer_06_gate_proj: 2.020310
  layer_06_k_proj: 0.636960
  layer_06_o_proj: 1.019251
  layer_06_q_proj: 1.096645
  layer_06_up_proj: 1.894189
  layer_06_v_proj: 0.472235
  layer_07_down_proj: 1.268298
  layer_07_gate_proj: 2.017085
  layer_07_k_proj: 0.603169
  layer_07_o_proj: 1.018477
  layer_07_q_proj: 1.017274
  layer_07_up_proj: 1.903372
  layer_07_v_proj: 0.438254
  layer_08_down_proj: 1.213458
  layer_08_gate_proj: 2.013372
  layer_08_k_proj: 0.614808
  layer_08_o_proj: 1.069341
  layer_08_q_proj: 1.005978
  layer_08_up_proj: 1.921307
  layer_08_v_proj: 0.440127
  layer_09_down_proj: 0.937504
  layer_09_gate_proj: 2.001638
  layer_09_k_proj: 0.681433
  layer_09_o_proj: 1.119661
  layer_09_q_proj: 1.008770
  layer_09_up_proj: 1.851416
  layer_09_v_proj: 0.450449
  layer_10_down_proj: 1.140032
  layer_10_gate_proj: 1.962505
  layer_10_k_proj: 0.660475
  layer_10_o_proj: 1.127396
  layer_10_q_proj: 1.066808
  layer_10_up_proj: 1.827402
  layer_10_v_proj: 0.494072
  layer_11_down_proj: 0.717837
  layer_11_gate_proj: 2.014840

stderr:
Traceback (most recent call last):
  File "<string>", line 32, in <module>
BrokenPipeError: [Errno 32] Broken pipe
```
</details>

### Step 28: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/experiment_metadata_v2.json | python3 -m json.tool
```

<details><summary>Output (1653 chars)</summary>

```
{
    "models": {
        "qwen3-1.7b": "Qwen/Qwen3-1.7B-Base",
        "qwen3-0.6b": "Qwen/Qwen3-0.6B-Base"
    },
    "paradigms": [
        "sft",
        "dpo",
        "kto"
    ],
    "sft_adapters_by_model": {
        "qwen3-1.7b": [
            "lora_r8",
            "lora_r16",
            "lora_r32_all",
            "dora_r16",
            "full_ft"
        ],
        "qwen3-0.6b": [
            "lora_r8",
            "lora_r16",
            "lora_r32_all"
        ]
    },
    "dpo_adapters_by_model": {
        "qwen3-1.7b": [
            "lora_r8",
            "lora_r16",
            "lora_r32_all"
        ],
        "qwen3-0.6b": [
            "lora_r16"
        ]
    },
    "kto_adapters_by_model": {
        "qwen3-1.7b": [
            "lora_r8",
            "lora_r16"
        ]
    },
    "dpo_betas_by_model": {
        "qwen3-1.7b": [
            0.1,
            0.5
        ],
        "qwen3-0.6b": [
            0.1
        ]
    },
    "simpo_config": {
        "beta": 2.5,
        "gamma": 1.0
    },
    "sft_dataset": "trl-lib/ultrafeedback_binarized",
    "dpo_dataset": "trl-lib/ultrafeedback_binarized",
    "kto_dataset": "trl-lib/kto-mix-14k",
    "eval_benchmarks": [
        "arc_easy",
        "hellaswag",
        "piqa",
        "winogrande",
        "mmlu"
    ],
    "eval_limit": 300,
    "sft_steps": {
        "qwen3-1.7b": 2000,
        "qwen3-0.6b": 2000
    },
    "dpo_steps": {
        "qwen3-1.7b": 1000,
        "qwen3-0.6b": 1000
    },
    "kto_steps": {
        "qwen3-1.7b": 1000
    },
    "max_seq_length": 1024,
    "generated_at": "2026-05-18T07:19:51.837930+00:00",
    "version": "v2"
}
```
</details>

### Step 29: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json, os

# Check what's in each checkpoint's trainer_state for a few key runs
for run in ['lora_r32_all_alpaca', 'lora_r32_all_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_alpaca']:
    ckpt_dir = f'runs/{run}/checkpoints'
    if not os.path.exists(ckpt_dir):
        print(f'{run}: no checkpoints dir')
        continue
    ckpts = sorted(os.listdir(ckpt_dir))
    print(f'{run}: checkpoints={ckpts}')
    # Load the last checkpoint's trainer_state
    last_ckpt = ckpts[-1]
    ts_path = f'{ckpt_dir}/{last_ckpt}/trainer_state.json'
    if os.path.exists(ts_path):
        with open(ts_path) as f:
            ts = json.load(f)
        # Count log entries
        log_entries = ts.get('log_history', [])
        eval_entries = [e for e in log_entries if 'eval_loss' in e]
        print(f'  {last_ckpt}: {len(log_entries)} log entries, {len(eval_entries)} eval entries')
        if eval_entries:
            for e in eval_entries:
                print(f'    step {e.get(\"step\")}: eval_loss={e.get(\"eval_loss\")}')
    print()
"
```

<details><summary>Output (2432 chars)</summary>

```
lora_r32_all_alpaca: checkpoints=['checkpoint-100', 'checkpoint-200', 'checkpoint-300', 'checkpoint-400', 'checkpoint-500']
  checkpoint-500: 60 log entries, 10 eval entries
    step 50: eval_loss=1.2900347709655762
    step 100: eval_loss=1.2738009691238403
    step 150: eval_loss=1.2815436124801636
    step 200: eval_loss=1.278459906578064
    step 250: eval_loss=1.2794697284698486
    step 300: eval_loss=1.3487833738327026
    step 350: eval_loss=1.3514587879180908
    step 400: eval_loss=1.4348132610321045
    step 450: eval_loss=1.4450159072875977
    step 500: eval_loss=1.4411063194274902

lora_r32_all_code_instructions: checkpoints=['checkpoint-1000', 'checkpoint-1200', 'checkpoint-1400', 'checkpoint-1600', 'checkpoint-1800', 'checkpoint-200', 'checkpoint-2000', 'checkpoint-400', 'checkpoint-600', 'checkpoint-800']
  checkpoint-800: 168 log entries, 8 eval entries
    step 100: eval_loss=0.8886348605155945
    step 200: eval_loss=0.903027355670929
    step 300: eval_loss=0.9428920149803162
    step 400: eval_loss=1.022294044494629
    step 500: eval_loss=1.0292561054229736
    step 600: eval_loss=1.1422353982925415
    step 700: eval_loss=1.2153798341751099
    step 800: eval_loss=1.3218454122543335

lora_r16_mlp_alpaca: checkpoints=['checkpoint-1000', 'checkpoint-1200', 'checkpoint-1400', 'checkpoint-1600', 'checkpoint-1800', 'checkpoint-200', 'checkpoint-2000', 'checkpoint-400', 'checkpoint-600', 'checkpoint-800']
  checkpoint-800: 168 log entries, 8 eval entries
    step 100: eval_loss=1.272390365600586
    step 200: eval_loss=1.2704960107803345
    step 300: eval_loss=1.3308501243591309
    step 400: eval_loss=1.3950756788253784
    step 500: eval_loss=1.4348504543304443
    step 600: eval_loss=1.53412663936615
    step 700: eval_loss=1.7193588018417358
    step 800: eval_loss=1.8759483098983765

lora_r16_alpaca: checkpoints=['checkpoint-100', 'checkpoint-200', 'checkpoint-300', 'checkpoint-400', 'checkpoint-500']
  checkpoint-500: 60 log entries, 10 eval entries
    step 50: eval_loss=1.345308780670166
    step 100: eval_loss=1.3061197996139526
    step 150: eval_loss=1.2965344190597534
    step 200: eval_loss=1.2889927625656128
    step 250: eval_loss=1.286950945854187
    step 300: eval_loss=1.291347861289978
    step 350: eval_loss=1.285811185836792
    step 400: eval_loss=1.2853827476501465
    step 450: eval_loss=1.2873784303665161
    step 500: eval_loss=1.284986138343811
```
</details>

### Step 30: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json, os

# Look at the last checkpoint trainer_state for runs with 2000 steps to get full eval trajectories
for run in ['lora_r32_all_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_mlp_code_instructions',
            'full_ft_code_instructions', 'lora_r16_code_instructions', 'dora_r8_code_instructions',
            'lora_r4_code_instructions', 'ia3_code_instructions', 'adalora_code_instructions',
            'dora_r8_alpaca', 'full_ft_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'lora_r4_alpaca', 'lora_r16_alpaca']:
    ckpt_dir = f'runs/{run}/checkpoints'
    if not os.path.exists(ckpt_dir):
        print(f'{run}: no checkpoints dir')
        continue
    ckpts = sorted(os.listdir(ckpt_dir), key=lambda x: int(x.split('-')[1]))
    last_ckpt = ckpts[-1]
    ts_path = f'{ckpt_dir}/{last_ckpt}/trainer_state.json'
    if os.path.exists(ts_path):
        with open(ts_path) as f:
            ts = json.load(f)
        max_step = ts.get('global_step', 0)
        log_entries = ts.get('log_history', [])
        eval_entries = [e for e in log_entries if 'eval_loss' in e]
        # Also check if best_model_checkpoint is set
        best = ts.get('best_model_checkpoint')
        best_metric = ts.get('best_metric')
        print(f'{run}: max_step={max_step}, eval_entries={len(eval_entries)}, best_ckpt={best}, best_metric={best_metric}')
"
```

<details><summary>Output (1306 chars)</summary>

```
lora_r32_all_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
lora_r16_mlp_alpaca: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
lora_r16_mlp_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
full_ft_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
lora_r16_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
dora_r8_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
lora_r4_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
ia3_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
adalora_code_instructions: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
dora_r8_alpaca: max_step=2000, eval_entries=20, best_ckpt=None, best_metric=None
full_ft_alpaca: max_step=500, eval_entries=10, best_ckpt=None, best_metric=None
ia3_alpaca: max_step=500, eval_entries=10, best_ckpt=None, best_metric=None
adalora_alpaca: max_step=500, eval_entries=10, best_ckpt=None, best_metric=None
lora_r4_alpaca: max_step=500, eval_entries=10, best_ckpt=None, best_metric=None
lora_r16_alpaca: max_step=500, eval_entries=10, best_ckpt=None, best_metric=None
```
</details>

### Step 31: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json, os

# Get full eval trajectories from the last checkpoint for all 2000-step runs
runs_2000 = ['lora_r32_all_code_instructions', 'lora_r16_mlp_alpaca', 'lora_r16_mlp_code_instructions',
            'full_ft_code_instructions', 'lora_r16_code_instructions', 'dora_r8_code_instructions',
            'lora_r4_code_instructions', 'ia3_code_instructions', 'adalora_code_instructions',
            'dora_r8_alpaca']

for run in runs_2000:
    ckpt_dir = f'runs/{run}/checkpoints'
    ckpts = sorted(os.listdir(ckpt_dir), key=lambda x: int(x.split('-')[1]))
    last_ckpt = ckpts[-1]
    ts_path = f'{ckpt_dir}/{last_ckpt}/trainer_state.json'
    with open(ts_path) as f:
        ts = json.load(f)
    eval_entries = [e for e in ts.get('log_history', []) if 'eval_loss' in e]
    
    # Find the min eval_loss and its step
    min_eval = min(eval_entries, key=lambda e: e['eval_loss'])
    
    print(f'{run}:')
    print(f'  Best eval_loss: {min_eval[\"eval_loss\"]:.4f} at step {min_eval[\"step\"]}')
    print(f'  Final eval_loss: {eval_entries[-1][\"eval_loss\"]:.4f} at step {eval_entries[-1][\"step\"]}')
    print(f'  Overfit delta: {eval_entries[-1][\"eval_loss\"] - min_eval[\"eval_loss\"]:+.4f}')
    print()
"
```

<details><summary>Output (1280 chars)</summary>

```
lora_r32_all_code_instructions:
  Best eval_loss: 0.8886 at step 100
  Final eval_loss: 1.6717 at step 2000
  Overfit delta: +0.7831

lora_r16_mlp_alpaca:
  Best eval_loss: 1.2705 at step 200
  Final eval_loss: 2.4983 at step 2000
  Overfit delta: +1.2278

lora_r16_mlp_code_instructions:
  Best eval_loss: 0.8966 at step 100
  Final eval_loss: 1.7115 at step 2000
  Overfit delta: +0.8149

full_ft_code_instructions:
  Best eval_loss: 0.8899 at step 500
  Final eval_loss: 1.0975 at step 2000
  Overfit delta: +0.2076

lora_r16_code_instructions:
  Best eval_loss: 0.9059 at step 300
  Final eval_loss: 1.1526 at step 2000
  Overfit delta: +0.2467

dora_r8_code_instructions:
  Best eval_loss: 0.9049 at step 500
  Final eval_loss: 1.0175 at step 2000
  Overfit delta: +0.1126

lora_r4_code_instructions:
  Best eval_loss: 0.9046 at step 700
  Final eval_loss: 0.9458 at step 2000
  Overfit delta: +0.0413

ia3_code_instructions:
  Best eval_loss: 0.9182 at step 2000
  Final eval_loss: 0.9182 at step 2000
  Overfit delta: +0.0000

adalora_code_instructions:
  Best eval_loss: 0.9160 at step 1600
  Final eval_loss: 0.9168 at step 2000
  Overfit delta: +0.0008

dora_r8_alpaca:
  Best eval_loss: 1.2859 at step 400
  Final eval_loss: 1.3838 at step 2000
  Overfit delta: +0.0978
```
</details>

### Step 32: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# Compute the train-eval gap for the lora_r32_all_alpaca in detail at each eval step
# Also show the smoothed train loss (5-step rolling average)
run = 'lora_r32_all_alpaca'
run_df = smol[smol['run_name'] == run]
train_df = run_df[run_df['learning_rate'].notna()].copy()
eval_df = run_df[run_df['eval_loss'].notna()].copy()

# Rolling average of train loss
train_df['loss_smoothed'] = train_df['loss'].rolling(window=5, center=True, min_periods=1).mean()

print(f'=== {run}: Detailed train vs eval ===')
print(f'{\"Step\":>5s}  {\"RawTrain\":>8s}  {\"Smoothed\":>8s}  {\"EvalLoss\":>8s}  {\"Gap(sm)\":>8s}  {\"GradNorm\":>8s}')
for _, erow in eval_df.iterrows():
    step = int(erow['step'])
    eval_loss = erow['eval_loss']
    closest = train_df.iloc[(train_df['step'] - step).abs().argsort()[:1]]
    if len(closest) > 0:
        raw = closest.iloc[0]['loss']
        smoothed = closest.iloc[0]['loss_smoothed']
        gn = closest.iloc[0]['grad_norm']
        gap = eval_loss - smoothed
        print(f'{step:5d}  {raw:8.4f}  {smoothed:8.4f}  {eval_loss:8.4f}  {gap:+8.4f}  {gn:8.4f}')

print()
# Also do lora_r16_mlp_alpaca 
run = 'lora_r16_mlp_alpaca'
run_df = smol[smol['run_name'] == run]
train_df = run_df[run_df['learning_rate'].notna()].copy()
eval_df = run_df[run_df['eval_loss'].notna()].copy()
train_df['loss_smoothed'] = train_df['loss'].rolling(window=5, center=True, min_periods=1).mean()

print(f'=== {run}: Detailed train vs eval ===')
print(f'{\"Step\":>5s}  {\"RawTrain\":>8s}  {\"Smoothed\":>8s}  {\"EvalLoss\":>8s}  {\"Gap(sm)\":>8s}  {\"GradNorm\":>8s}')
for _, erow in eval_df.iterrows():
    step = int(erow['step'])
    eval_loss = erow['eval_loss']
    closest = train_df.iloc[(train_df['step'] - step).abs().argsort()[:1]]
    if len(closest) > 0:
        raw = closest.iloc[0]['loss']
        smoothed = closest.iloc[0]['loss_smoothed']
        gn = closest.iloc[0]['grad_norm']
        gap = eval_loss - smoothed
        print(f'{step:5d}  {raw:8.4f}  {smoothed:8.4f}  {eval_loss:8.4f}  {gap:+8.4f}  {gn:8.4f}')
"
```

<details><summary>Output (1896 chars)</summary>

```
=== lora_r32_all_alpaca: Detailed train vs eval ===
 Step  RawTrain  Smoothed  EvalLoss   Gap(sm)  GradNorm
   50    1.2900    1.3056    1.2900   -0.0155    0.4204
  100    1.3254    1.2868    1.2738   -0.0130    0.4760
  150    1.0242    1.0386    1.2815   +0.2430    0.4614
  200    1.0837    1.0981    1.2785   +0.1804    0.4843
  250    1.0818    0.9881    1.2795   +0.2914    0.4925
  300    0.8347    0.8638    1.3488   +0.4850    0.5420
  350    0.8677    0.8419    1.3515   +0.5095    0.4833
  400    0.6877    0.6649    1.4348   +0.7699    0.5416
  450    0.6610    0.6954    1.4450   +0.7497    0.7115
  500    0.6826    0.7031    1.4411   +0.7380    0.5668

=== lora_r16_mlp_alpaca: Detailed train vs eval ===
 Step  RawTrain  Smoothed  EvalLoss   Gap(sm)  GradNorm
  100    1.2406    1.2976    1.2724   -0.0252    0.3522
  200    1.1633    1.2402    1.2705   +0.0303    0.4031
  300    1.0519    1.0494    1.3309   +0.2815    0.4899
  400    0.7864    0.7534    1.3951   +0.6417    0.5224
  500    0.8195    0.7283    1.4349   +0.7065    0.5819
  600    0.6645    0.6701    1.5341   +0.8641    0.7522
  700    0.4105    0.4146    1.7194   +1.3047    0.7396
  800    0.3751    0.3645    1.8759   +1.5114    0.6468
  900    0.2227    0.2464    1.9592   +1.7128    0.5699
 1000    0.2732    0.2354    1.9748   +1.7394    0.6674
 1100    0.1886    0.2023    2.1193   +1.9170    0.3847
 1200    0.1745    0.1683    2.2358   +2.0675    0.3843
 1300    0.1397    0.1360    2.3121   +2.1761    0.3730
 1400    0.1117    0.1123    2.3703   +2.2580    0.4607
 1500    0.1143    0.1143    2.3682   +2.2539    0.3718
 1600    0.1259    0.1109    2.4315   +2.3206    0.4341
 1700    0.1081    0.1033    2.4552   +2.3519    0.3683
 1800    0.0992    0.1004    2.4854   +2.3850    0.3481
 1900    0.0875    0.0947    2.4845   +2.3898    0.2324
 2000    0.0936    0.0900    2.4983   +2.4083    0.3311
```
</details>

### Step 33: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

# Build a summary table: final eval results per run, alongside training metrics
eval_df = pd.read_parquet('eval_results_comparison.parquet')
train_df = pd.read_parquet('training_curves_comparison.parquet')
summary_df = pd.read_parquet('cross_adapter_comparison.parquet')

# Filter SmolLM2 runs (no qwen3_ prefix)
smol_runs = [r for r in summary_df['run_name'].unique() if not r.startswith('qwen3_')]

# For each run, get the avg benchmark score
print(f'{\"Run\":>40s} | {\"arc\":>6s} | {\"hella\":>6s} | {\"piqa\":>6s} | {\"wino\":>6s} | {\"boolq\":>6s} | {\"AvgAcc\":>7s} | {\"FTrainLoss\":>10s} | {\"FEvalLoss\":>9s} | {\"MinEval\":>7s} | {\"Overfit\":>7s}')
print('-' * 135)
for run in sorted(smol_runs):
    srow = summary_df[summary_df['run_name'] == run].iloc[0]
    
    # Get eval results
    run_evals = eval_df[(eval_df['run_name'] == run) & (eval_df['metric'] == 'acc,none')]
    scores = {}
    for _, r in run_evals.iterrows():
        scores[r['benchmark']] = r['value']
    
    arc = scores.get('arc_easy', np.nan)
    hella = scores.get('hellaswag', np.nan)
    piqa = scores.get('piqa', np.nan)
    wino = scores.get('winogrande', np.nan)
    boolq = scores.get('boolq', np.nan)
    avg_acc = np.nanmean(list(scores.values()))
    
    # Get training metrics
    run_train = train_df[train_df['run_name'] == run]
    eval_rows = run_train[run_train['eval_loss'].notna()]
    train_rows = run_train[run_train['learning_rate'].notna()]
    
    final_train = train_rows.iloc[-1]['loss'] if len(train_rows) > 0 else np.nan
    final_eval = eval_rows.iloc[-1]['eval_loss'] if len(eval_rows) > 0 else np.nan
    min_eval = eval_rows['eval_loss'].min() if len(eval_rows) > 0 else np.nan
    overfit = final_eval - min_eval if not np.isnan(final_eval) else np.nan
    
    print(f'{run:>40s} | {arc:6.3f} | {hella:6.3f} | {piqa:6.3f} | {wino:6.3f} | {boolq:6.3f} | {avg_acc:7.3f} | {final_train:10.4f} | {final_eval:9.4f} | {min_eval:7.4f} | {overfit:+7.4f}')
"
```

<details><summary>Output (2639 chars)</summary>

```
                                     Run |    arc |  hella |   piqa |   wino |  boolq |  AvgAcc | FTrainLoss | FEvalLoss | MinEval | Overfit
---------------------------------------------------------------------------------------------------------------------------------------
                          adalora_alpaca |  0.585 |  0.435 |  0.655 |  0.475 |  0.620 |   0.554 |     1.3415 |    1.3317 |  1.3317 | +0.0000
               adalora_code_instructions |  0.580 |  0.450 |  0.645 |  0.500 |  0.625 |   0.560 |     0.8018 |    0.9168 |  0.9160 | +0.0008
                          dora_r8_alpaca |  0.535 |  0.450 |  0.680 |  0.485 |  0.635 |   0.557 |     0.9670 |    1.3838 |  1.2859 | +0.0978
               dora_r8_code_instructions |  0.510 |  0.440 |  0.650 |  0.495 |  0.605 |   0.540 |     0.5657 |    1.0175 |  0.9049 | +0.1126
                          full_ft_alpaca |    nan |    nan |    nan |    nan |    nan |     nan |     1.1045 |    1.2727 |  1.2712 | +0.0015
               full_ft_code_instructions |    nan |    nan |    nan |    nan |    nan |     nan |     0.3230 |    1.0975 |  0.8899 | +0.2076
                              ia3_alpaca |  0.600 |  0.430 |  0.650 |  0.485 |  0.605 |   0.554 |     1.3538 |    1.3585 |  1.3585 | +0.0000
                   ia3_code_instructions |  0.580 |  0.445 |  0.635 |  0.480 |  0.640 |   0.556 |     0.7925 |    0.9182 |  0.9182 | +0.0000
                         lora_r16_alpaca |  0.585 |  0.430 |  0.665 |  0.485 |  0.630 |   0.559 |     1.2096 |    1.2850 |  1.2850 | +0.0000
              lora_r16_code_instructions |  0.485 |  0.440 |  0.635 |  0.490 |  0.600 |   0.530 |     0.4205 |    1.1526 |  0.9059 | +0.2467
                     lora_r16_mlp_alpaca |  0.430 |  0.400 |  0.625 |  0.505 |  0.595 |   0.511 |     0.0936 |    2.4983 |  1.2705 | +1.2278
          lora_r16_mlp_code_instructions |  0.525 |  0.450 |  0.620 |  0.530 |  0.610 |   0.547 |     0.0977 |    1.7115 |  0.8966 | +0.8149
                     lora_r32_all_alpaca |  0.510 |  0.450 |  0.665 |  0.540 |  0.610 |   0.555 |     0.6826 |    1.4411 |  1.2738 | +0.1673
          lora_r32_all_code_instructions |  0.490 |  0.440 |  0.650 |  0.510 |  0.630 |   0.544 |     0.0853 |    1.6717 |  0.8886 | +0.7831
                          lora_r4_alpaca |  0.590 |  0.430 |  0.665 |  0.515 |  0.625 |   0.565 |     1.2701 |    1.2924 |  1.2924 | +0.0000
               lora_r4_code_instructions |  0.540 |  0.435 |  0.645 |  0.475 |  0.610 |   0.541 |     0.6762 |    0.9458 |  0.9046 | +0.0413

stderr:
<string>:30: RuntimeWarning: Mean of empty slice
<string>:30: RuntimeWarning: Mean of empty slice
```
</details>

### Step 34: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/ | grep -v qwen3 | grep -E "full_ft|lora_r32_all$"
```

<details><summary>Output (12 chars)</summary>

```
lora_r32_all
```
</details>

### Step 35: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/full_ft_alpaca/ 2>/dev/null; ls /home/ubuntu/workspace/training-export-proprietary/evaluations/full_ft_code_instructions/ 2>/dev/null; ls /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all/ 2>/dev/null
```

<details><summary>Output (96 chars)</summary>

```
eval_results.json
merged_model
samples_arc_easy.jsonl
samples_hellaswag.jsonl
samples_piqa.jsonl
```
</details>

### Step 36: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/full_ft_alpaca/eval_results.json | python3 -m json.tool
```

<details><summary>Output (0 chars)</summary>

```

```
</details>

### Step 37: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/full_ft_code_instructions/eval_results.json | python3 -m json.tool
```

<details><summary>Output (0 chars)</summary>

```

```
</details>

### Step 38: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/ | grep -v qwen3 | sort
```

<details><summary>Output (342 chars)</summary>

```
adalora
adalora_alpaca
adalora_code_instructions
dora_r8_alpaca
dora_r8_code_instructions
ia3
ia3_alpaca
ia3_code_instructions
lora_r16
lora_r16_alpaca
lora_r16_code_instructions
lora_r16_mlp_alpaca
lora_r16_mlp_code_instructions
lora_r32_all
lora_r32_all_alpaca
lora_r32_all_code_instructions
lora_r4
lora_r4_alpaca
lora_r4_code_instructions
```
</details>

### Step 39: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/ | grep full_ft
```

<details><summary>Output (28 chars)</summary>

```
qwen3_sft_full_ft_qwen3-1.7b
```
</details>

### Step 40: bash

```bash
# Check if full_ft eval results are in the runs directory or elsewhere
ls /home/ubuntu/workspace/training-export-proprietary/runs/full_ft_alpaca/
echo "---"
ls /home/ubuntu/workspace/training-export-proprietary/runs/full_ft_code_instructions/
```

<details><summary>Output (195 chars)</summary>

```
adapter_weight_stats.json
checkpoints
memory_profile.json
training_config.json
training_log.csv
---
adapter_weight_stats.json
checkpoints
memory_profile.json
training_config.json
training_log.csv
```
</details>

### Step 41: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/full_ft_alpaca/training_config.json | python3 -m json.tool
```

<details><summary>Output (540 chars)</summary>

```
{
    "adapter_name": "full_ft",
    "adapter_config": {
        "type": "full"
    },
    "base_model": "HuggingFaceTB/SmolLM2-135M",
    "dataset": "alpaca",
    "training_args": {
        "max_steps": 500,
        "batch_size": 4,
        "learning_rate": 1e-05,
        "weight_decay": 0.01,
        "seed": 42
    },
    "results": {
        "trainable_params": 134515008,
        "total_params": 134515008,
        "adapter_overhead_pct": 100.0,
        "elapsed_seconds": 447.77,
        "final_train_loss": 1.224168872833252
    }
}
```
</details>

### Step 42: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/full_ft_code_instructions/training_config.json | python3 -m json.tool
```

<details><summary>Output (582 chars)</summary>

```
{
    "adapter_name": "full_ft",
    "adapter_config": {
        "type": "full"
    },
    "base_model": "HuggingFaceTB/SmolLM2-135M",
    "dataset": "code_instructions",
    "training_args": {
        "max_steps": 2000,
        "logging_steps": 5,
        "batch_size": 4,
        "learning_rate": 1e-05,
        "weight_decay": 0.01,
        "seed": 42
    },
    "results": {
        "trainable_params": 134515008,
        "total_params": 134515008,
        "adapter_overhead_pct": 100.0,
        "elapsed_seconds": 1889.75,
        "final_train_loss": 0.5090054859519004
    }
}
```
</details>

### Step 43: bash

```bash
# Now let me check the training configs for all runs to understand LR and steps
cd /home/ubuntu/workspace/training-export-proprietary && for run in adalora_alpaca adalora_code_instructions dora_r8_alpaca dora_r8_code_instructions ia3_alpaca ia3_code_instructions lora_r16_alpaca lora_r16_code_instructions lora_r16_mlp_alpaca lora_r16_mlp_code_instructions lora_r32_all_alpaca lora_r32_all_code_instructions lora_r4_alpaca lora_r4_code_instructions; do
  echo "=== $run ==="
  python3 -c "
import json
with open('runs/$run/training_config.json') as f:
    d = json.load(f)
ta = d['training_args']
print(f'  lr={ta[\"learning_rate\"]}, max_steps={ta[\"max_steps\"]}, bs={ta[\"batch_size\"]}, wd={ta[\"weight_decay\"]}')
rc = d.get('results', {})
print(f'  trainable={rc.get(\"trainable_params\",\"?\")}, overhead={rc.get(\"adapter_overhead_pct\",\"?\")}%, final_loss={rc.get(\"final_train_loss\",\"?\")}')
" 2>/dev/null || echo "  ERROR"
done
```

<details><summary>Output (1960 chars)</summary>

```
=== adalora_alpaca ===
  lr=0.0005, max_steps=500, bs=4, wd=0.01
  trainable=922560, overhead=0.6812%, final_loss=1.7979225234985352
=== adalora_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=922560, overhead=0.6812%, final_loss=0.9062701214551926
=== dora_r8_alpaca ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=483840, overhead=0.3584%, final_loss=1.1140400230884553
=== dora_r8_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=483840, overhead=0.3584%, final_loss=0.698994244813919
=== ia3_alpaca ===
  lr=0.0005, max_steps=500, bs=4, wd=0.01
  trainable=74880, overhead=0.0556%, final_loss=1.5564904956817627
=== ia3_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=74880, overhead=0.0556%, final_loss=0.848178494811058
=== lora_r16_alpaca ===
  lr=0.0005, max_steps=500, bs=4, wd=0.01
  trainable=921600, overhead=0.6805%, final_loss=1.2895070629119874
=== lora_r16_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=921600, overhead=0.6805%, final_loss=0.617451669037342
=== lora_r16_mlp_alpaca ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=3041280, overhead=2.2109%, final_loss=0.44082465904951096
=== lora_r16_mlp_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=3041280, overhead=2.2109%, final_loss=0.3184229529350996
=== lora_r32_all_alpaca ===
  lr=0.0005, max_steps=500, bs=4, wd=0.01
  trainable=9768960, overhead=6.7706%, final_loss=0.9831624612808227
=== lora_r32_all_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=9768960, overhead=6.7706%, final_loss=0.26719389389455317
=== lora_r4_alpaca ===
  lr=0.0005, max_steps=500, bs=4, wd=0.01
  trainable=230400, overhead=0.171%, final_loss=1.3626840934753417
=== lora_r4_code_instructions ===
  lr=0.0005, max_steps=2000, bs=4, wd=0.01
  trainable=230400, overhead=0.171%, final_loss=0.7622196156978607
```
</details>

### Step 44: bash

```bash
# Now let me look at the PEFT source to understand how these adapters work
ls /home/ubuntu/workspace/peft/src/peft/
```

<details><summary>Output (159 chars)</summary>

```
__init__.py
auto.py
config.py
functional.py
helpers.py
import_utils.py
mapping.py
mapping_func.py
mixed_model.py
optimizers
peft_model.py
py.typed
tuners
utils
```
</details>

### Step 45: bash

```bash
ls /home/ubuntu/workspace/peft/
```

<details><summary>Output (140 chars)</summary>

```
CONTRIBUTING.md
LICENSE
Makefile
README.md
docker
docs
examples
method_comparison
pyproject.toml
requirements.txt
scripts
setup.py
src
tests
```
</details>

### Step 46: bash

```bash
ls /home/ubuntu/workspace/peft/src/peft/tuners/
```

<details><summary>Output (362 chars)</summary>

```
__init__.py
_buffer_dict.py
adalora
adamss
adaption_prompt
beft
boft
c3a
cartridge
cpt
delora
fourierft
gralora
hira
hra
ia3
lily
ln_tuning
loha
lokr
lora
lycoris_utils.py
miss
mixed
multitask_prompt_tuning
oft
osf
p_tuning
peanut
poly
prefix_tuning
prompt_tuning
psoft
pvera
randlora
road
shira
tinylora
trainable_tokens
tuners_utils.py
vblora
vera
waveft
xlora
```
</details>

### Step 47: bash

```bash
ls /home/ubuntu/workspace/peft/src/peft/tuners/lora/
```

<details><summary>Output (212 chars)</summary>

```
__init__.py
aqlm.py
arrow.py
awq.py
bnb.py
config.py
conversion.py
corda.py
dora.py
eetq.py
eva.py
gptq.py
hqq.py
inc.py
intruders.py
layer.py
loraga.py
model.py
te.py
torchao.py
tp_layer.py
variants.py
velora.py
```
</details>

### Step 48: bash

```bash
ls /home/ubuntu/workspace/peft/src/peft/tuners/ia3/
```

<details><summary>Output (46 chars)</summary>

```
__init__.py
bnb.py
config.py
layer.py
model.py
```
</details>

### Step 49: bash

```bash
ls /home/ubuntu/workspace/peft/src/peft/tuners/adalora/
```

<details><summary>Output (54 chars)</summary>

```
__init__.py
bnb.py
config.py
gptq.py
layer.py
model.py
```
</details>

### Step 50: bash

```bash
# Look at the lora layer implementation to understand how the forward pass works with scaling
grep -n "def forward" /home/ubuntu/workspace/peft/src/peft/tuners/lora/layer.py | head -20
```

<details><summary>Output (483 chars)</summary>

```
84:    def forward(
950:    def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
1304:    def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
1616:    def forward(self, x: torch.Tensor, *args, **kwargs) -> torch.Tensor:
2012:    def forward(self, query: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
2119:    def forward(self, W):
2465:    def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
```
</details>

### Step 51: bash

```bash
# Look at the scaling and how alpha/r affects the update
grep -n "scaling\|alpha\|lora_alpha\|dropout" /home/ubuntu/workspace/peft/src/peft/tuners/lora/layer.py | head -30
```

<details><summary>Output (1797 chars)</summary>

```
108:    other_param_names: tuple[str, ...] = ("r", "lora_alpha", "scaling", "lora_dropout")
113:        self.lora_alpha = {}
114:        self.scaling = {}
115:        self.lora_dropout = nn.ModuleDict({})
161:        lora_alpha: int,
166:        lora_dropout = config.lora_dropout
192:        self.lora_alpha[adapter_name] = lora_alpha
193:        if lora_dropout > 0.0:
194:            lora_dropout_layer = nn.Dropout(p=lora_dropout)
196:            lora_dropout_layer = nn.Identity()
198:        self.lora_dropout.update(nn.ModuleDict({adapter_name: lora_dropout_layer}))
217:            self.scaling[adapter_name] = lora_alpha / math.sqrt(r)
219:            self.scaling[adapter_name] = lora_alpha / r
333:        scale_factor = self.scaling[adapter_name]
378:            Sr /= self.scaling[adapter_name]
384:            Sr /= self.scaling[adapter_name]
395:        weight = weight.data - self.scaling[adapter_name] * lora_B @ lora_A
463:        # Apply alpha
464:        S /= self.scaling[adapter_name]
474:        delta = self.scaling[adapter_name] * lora_B @ lora_A
599:        scaling_factor = self.scaling[adapter_name]
614:            lora_A_weight = lora_A_weight / scaling_factor
615:            lora_B_weight = lora_B_weight / scaling_factor
626:        # Modify base weights: W_new = W_old - scaling * (B @ A)
629:        weight_offset = scaling_factor * (lora_B_weight.float() @ lora_A_weight.float())
649:        The initial scale is determined by the configured `r` (rank) and `lora_alpha`.
651:        if adapter not in self.scaling:
655:            self.scaling[adapter] = scale * self.lora_alpha[adapter] / math.sqrt(self.r[adapter])
657:            self.scaling[adapter] = scale * self.lora_alpha[adapter] / self.r[adapter]
668:            self.scaling[active_adapter] *= scale
```
</details>

### Step 52: read

**Path:** `/home/ubuntu/workspace/peft/src/peft/tuners/lora/layer.py`

<details><summary>Output (3482 chars)</summary>

```
<path>/home/ubuntu/workspace/peft/src/peft/tuners/lora/layer.py</path>
<type>file</type>
<content>
940: 
941:         if cast_to_fp32:
942:             output_tensor = output_tensor.to(dtype=dtype)
943: 
944:             # cast back the weights
945:             self.lora_A[adapter].weight.data = weight_A.to(dtype)
946:             self.lora_B[adapter].weight.data = weight_B.to(dtype)
947: 
948:         return output_tensor
949: 
950:     def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
951:         self._check_forward_args(x, *args, **kwargs)
952:         adapter_names = kwargs.pop("adapter_names", None)
953:         variant_kwargs = {k: kwargs.pop(k, None) for k in VARIANT_KWARG_KEYS}  # don't pass these to base_layer
954: 
955:         if self.disable_adapters:
956:             if self.merged:
957:                 self.unmerge()
958:             result = self.base_layer(x, *args, **kwargs)
959:         elif adapter_names is not None:
960:             result = self._mixed_batch_forward(x, *args, adapter_names=adapter_names, **variant_kwargs, **kwargs)
961:         elif self.merged:
962:             result = self.base_layer(x, *args, **kwargs)
963:         else:
964:             result = self.base_layer(x, *args, **kwargs)
965:             torch_result_dtype = result.dtype
966: 
967:             lora_A_keys = self.lora_A.keys()
968:             for active_adapter in self.active_adapters:
969:                 if active_adapter not in lora_A_keys:
970:                     continue
971: 
972:                 lora_A = self.lora_A[active_adapter]
973:                 lora_B = self.lora_B[active_adapter]
974:                 dropout = self.lora_dropout[active_adapter]
975:                 scaling = self.scaling[active_adapter]
976:                 x = self._cast_input_dtype(x, lora_A.weight.dtype)
977:                 if active_adapter not in self.lora_variant:  # vanilla LoRA
978:                     result = result + lora_B(lora_A(dropout(x))) * scaling
979:                 else:
980:                     result = self.lora_variant[active_adapter].forward(
981:                         self,
982:                         active_adapter=active_adapter,
983:                         x=x,
984:                         result=result,
985:                         **variant_kwargs,
986:                         **kwargs,
987:                     )
988: 
989:             result = result.to(torch_result_dtype)
990: 
991:         return result
992: 
993:     def supports_lora_conversion(self, adapter_name: str = "default") -> bool:
994:         return True
995: 
996:     def __repr__(self) -> str:
997:         rep = super().__repr__()
998:         return "lora." + rep
999: 
1000: 
1001: class _LoraEmbeddingAHolder(nn.Module):
1002:     """
1003:     A "fake" module to hold the lora_embedding_A weights for the TP hooks.
1004:     """
1005: 
1006:     def __init__(self, lora_embedding_A_weight):
1007:         super().__init__()
1008:         self.weight = lora_embedding_A_weight.T  # lora_embedding_A shape is (r, vocab_size)
1009: 
1010: 
1011: class Embedding(nn.Module, LoraLayer):
1012:     # LoRA implemented in a Embedding layer
1013:     def __init__(
1014:         self,
1015:         base_layer: nn.Module,
1016:         adapter_name: str,
1017:         config: LoraConfig,
1018:         r: int = 0,
1019:         lora_alpha: int = 1,

(Showing lines 940-1019 of 2533. Use offset=1020 to continue.)
</content>
```
</details>

### Step 53: bash

```bash
# Look at the ia3 layer forward to understand how it works
grep -n "def forward\|scaling\|ia3" /home/ubuntu/workspace/peft/src/peft/tuners/ia3/layer.py | head -30
```

<details><summary>Output (2092 chars)</summary>

```
30:    adapter_layer_names = ("ia3_l",)
34:        self.ia3_l = nn.ParameterDict({})
57:        init_ia3_weights = config.init_ia3_weights
66:        self.ia3_l[adapter_name] = nn.Parameter(weight)
67:        if init_ia3_weights:
68:            self.reset_ia3_parameters(adapter_name)
72:    def reset_ia3_parameters(self, adapter_name):
73:        if adapter_name in self.ia3_l.keys():
75:            nn.init.constant_(self.ia3_l[adapter_name], 1.0)
115:            if active_adapter in self.ia3_l.keys():
117:                ia3_l = transpose(self.ia3_l[active_adapter].data, self.fan_in_fan_out)
121:                    orig_weights = torch.mul(orig_weights, ia3_l)
129:                    base_layer.weight.data = torch.mul(base_layer.weight.data, ia3_l).to(orig_dtype)
132:                    scaling = self.ia3_l[active_adapter].reshape(base_layer.bias.shape)
134:                    base_layer.bias.data = torch.mul(base_layer.bias.data, scaling.data).to(orig_dtype)
149:            if active_adapter in self.ia3_l.keys():
152:                ia3_l = transpose(self.ia3_l[active_adapter].data, self.fan_in_fan_out) + 1e-8
154:                base_layer.weight.data = torch.div(base_layer.weight.data, ia3_l).to(orig_dtype)
157:                    scaling = self.ia3_l[active_adapter].reshape(base_layer.bias.shape)
159:                    base_layer.bias.data = torch.div(base_layer.bias.data, scaling.data + 1e-8).to(orig_dtype)
161:    def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
170:            ia3_scaling = 1
172:                if active_adapter not in self.ia3_l.keys():
174:                dtype = self.ia3_l[active_adapter].dtype
175:                ia3_scaling *= self.ia3_l[active_adapter].flatten()
179:                # TODO: weight.dtype can be != self.ia3_l[self.active_adapters].dtype
181:                interm = (x * ia3_scaling).to(previous_dtype)
186:                result = (result * ia3_scaling).to(result_dtype)
209:        init_ia3_weights = config.init_ia3_weights
216:        self.ia3_l[adapter_name] = nn.Parameter(weight)
```
</details>

### Step 54: read

**Path:** `/home/ubuntu/workspace/peft/src/peft/tuners/ia3/layer.py`

<details><summary>Output (2401 chars)</summary>

```
<path>/home/ubuntu/workspace/peft/src/peft/tuners/ia3/layer.py</path>
<type>file</type>
<content>
161:     def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
162:         dtype = previous_dtype = x.dtype
163:         if self.disable_adapters:
164:             if self.merged:
165:                 self.unmerge()
166:             result = self.base_layer(x, *args, **kwargs)
167:         elif self.merged:
168:             result = self.base_layer(x, *args, **kwargs)
169:         else:
170:             ia3_scaling = 1
171:             for active_adapter in self.active_adapters:
172:                 if active_adapter not in self.ia3_l.keys():
173:                     continue
174:                 dtype = self.ia3_l[active_adapter].dtype
175:                 ia3_scaling *= self.ia3_l[active_adapter].flatten()
176: 
177:             if self.is_feedforward:
178:                 x = x.to(dtype)
179:                 # TODO: weight.dtype can be != self.ia3_l[self.active_adapters].dtype
180:                 # e.g. bf16 vs fp32. Is that okay?
181:                 interm = (x * ia3_scaling).to(previous_dtype)
182:                 result = self.base_layer(interm, *args, **kwargs)
183:             else:
184:                 result = self.base_layer(x, *args, **kwargs)
185:                 result_dtype = result.dtype
186:                 result = (result * ia3_scaling).to(result_dtype)
187: 
188:         return result
189: 
190: 
191: class _ConvNd(nn.Module, IA3Layer):
192:     def __init__(
193:         self,
194:         base_layer: nn.Module,
195:         adapter_name: str,
196:         config: IA3Config,
197:         is_feedforward: bool = False,  # Set to True if the layer is treated as a feedforward layer
198:         **kwargs,
199:     ) -> None:
200:         super().__init__()
201:         IA3Layer.__init__(self, base_layer, is_feedforward=is_feedforward)
202:         self.fan_in_fan_out = config.fan_in_fan_out
203:         self._active_adapter = adapter_name
204:         self._kernel_dim = base_layer.weight.dim()
205: 
206:         self.update_layer(adapter_name, config=config)
207: 
208:     def update_layer(self, adapter_name: str, config: IA3Config, **kwargs):
209:         init_ia3_weights = config.init_ia3_weights
210:         inference_mode = config.inference_mode

(Showing lines 161-210 of 336. Use offset=211 to continue.)
</content>
```
</details>

### Step 55: bash

```bash
# Look at dora implementation 
grep -n "def forward\|magnitude\|direction\|dora" /home/ubuntu/workspace/peft/src/peft/tuners/lora/dora.py | head -40
```

<details><summary>Output (1274 chars)</summary>

```
66:        self._dora_cache: dict[str, Any] = {}  # small ad hoc cache; values are not part of the state_dict
70:        self._dora_cache[key] = value
74:        return self._dora_cache.get(key, default)
77:        self._dora_cache.clear()
132:    def forward(self, x, *, lora_A, lora_B, scaling, base_layer, base_result=None, adapter_name="default"):
140:        magnitude = self.weight
153:        mag_norm_scale = (magnitude / weight_norm).view(1, -1)
165:        result_dora = (mag_norm_scale - 1) * base_result + mag_norm_scale * lora_result * scaling
166:        return result_dora
170:        return "lora.dora." + rep
178:    def forward(self, x, *, lora_A, lora_B, scaling, base_layer, embed_fn, adapter_name="default"):
184:        magnitude = self.weight
196:        mag_norm_scale = magnitude / weight_norm
197:        result_dora = mag_norm_scale * (embed_fn(x, lora_A) @ lora_B) * scaling
198:        return mag_norm_scale, result_dora
202:        return "lora.dora." + rep
223:    def forward(
234:        magnitude = self.weight
245:        mag_norm_scale = magnitude / weight_norm
264:        result_dora = (mag_norm_scale - 1) * base_result + mag_norm_scale * lora_B(lora_A(x)) * scaling
265:        return result_dora
269:        return "lora.dora." + rep
```
</details>

### Step 56: bash

```bash
# Look at adalora implementation to understand rank adaptation
grep -n "def forward\|rank\|mask\|adalora\|rank_pattern\|rho\|step" /home/ubuntu/workspace/peft/src/peft/tuners/adalora/layer.py | head -40
```

<details><summary>Output (2480 chars)</summary>

```
39:    # Note: ranknum doesn't need to be included as it is not an nn.Module
42:    other_param_names = ("r", "lora_alpha", "scaling", "lora_dropout", "ranknum")
49:        self.ranknum = nn.ParameterDict({})
74:        # The current rank. ranknum is deterministic (always set to float(r)) and is not saved
82:            self.ranknum[adapter_name] = nn.Parameter(torch.randn(1), requires_grad=False)
83:            self.ranknum[adapter_name].data.fill_(float(r))
84:            self.ranknum[adapter_name].requires_grad = False
172:            / (self.ranknum[adapter] + 1e-5)
175:    def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
192:                ranknum = self.ranknum[active_adapter] + 1e-5
195:                result += (dropout(x) @ (lora_A * lora_E).T @ lora_B.T) * scaling / ranknum
201:        return "adalora." + rep
244:        # Current rank — see note in AdaLoraLayer.update_layer about _skip_init_on_device.
246:            self.ranknum[adapter_name] = nn.Parameter(torch.randn(1), requires_grad=False)
247:            self.ranknum[adapter_name].data.fill_(float(r))
248:            self.ranknum[adapter_name].requires_grad = False
307:            / (self.ranknum[adapter] + 1e-5)
311:    def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
328:                ranknum = self.ranknum[active_adapter] + 1e-5
332:                delta_w = (lora_B @ (lora_A * lora_E) * scaling / ranknum).reshape(base.weight.shape)
347:        return "adalora." + rep
371:    def set_total_step(self, total_step):
372:        self.peft_config.total_step = total_step
387:        # The total final rank budget
390:    def budget_schedule(self, step: int):
393:        total_step = self.peft_config.total_step
395:        if step <= tinit:
397:            mask_ind = False
399:        elif step > total_step - tfinal:
401:            mask_ind = True
404:            mul_coeff = 1 - (step - tinit) / (total_step - tfinal - tinit)
406:            mask_ind = True if step % self.peft_config.deltaT == 0 else False
407:        return budget, mask_ind
440:    def mask_to_budget(self, model, budget):
477:        # Get the threshold by ranking ipt
478:        mask_threshold = torch.kthvalue(
483:        rank_pattern = {}
488:                    p.masked_fill_(triplet_ipt[n] <= mask_threshold, 0.0)
489:                    rank_pattern[n] = (~(triplet_ipt[n] <= mask_threshold)).view(-1).tolist()
490:        return rank_pattern
```
</details>

### Step 57: read

**Path:** `/home/ubuntu/workspace/peft/src/peft/tuners/adalora/layer.py`

<details><summary>Output (1807 chars)</summary>

```
<path>/home/ubuntu/workspace/peft/src/peft/tuners/adalora/layer.py</path>
<type>file</type>
<content>
175:     def forward(self, x: torch.Tensor, *args: Any, **kwargs: Any) -> torch.Tensor:
176:         if self.disable_adapters:
177:             if self.merged:
178:                 self.unmerge()
179:             result = self.base_layer(x, *args, **kwargs)
180:         elif self.merged:
181:             result = self.base_layer(x, *args, **kwargs)
182:         else:
183:             result = self.base_layer(x, *args, **kwargs)
184:             for active_adapter in self.active_adapters:
185:                 if active_adapter not in self.lora_A.keys():
186:                     continue
187:                 lora_A = self.lora_A[active_adapter]
188:                 lora_B = self.lora_B[active_adapter]
189:                 lora_E = self.lora_E[active_adapter]
190:                 dropout = self.lora_dropout[active_adapter]
191:                 scaling = self.scaling[active_adapter]
192:                 ranknum = self.ranknum[active_adapter] + 1e-5
193: 
194:                 x = self._cast_input_dtype(x, lora_A.dtype)
195:                 result += (dropout(x) @ (lora_A * lora_E).T @ lora_B.T) * scaling / ranknum
196: 
197:         return result
198: 
199:     def __repr__(self) -> str:
200:         rep = super().__repr__()
201:         return "adalora." + rep
202: 
203: 
204: class SVDConv2d(nn.Module, AdaLoraLayer):
205:     # SVD-based adaptation by a Conv2d layer
206:     def __init__(
207:         self,
208:         base_layer: nn.Module,
209:         adapter_name: str,
210:         config: AdaLoraConfig,
211:         r: int = 0,
212:         lora_alpha: int = 1,
213:         **kwargs,
214:     ) -> None:

(Showing lines 175-214 of 515. Use offset=215 to continue.)
</content>
```
</details>

### Step 58: bash

```bash
# Look at adalora config to understand the rank pruning parameters
grep -n "total_step\|tinit\|tfinal\|deltaT\|rank\|rho\|class AdaLoraConfig" /home/ubuntu/workspace/peft/src/peft/tuners/adalora/config.py | head -30
```

<details><summary>Output (2521 chars)</summary>

```
24:class AdaLoraConfig(LoraConfig):
28:    AdaLoRA has three phases defined by `tinit`, `tfinal` and `total_step`.
30:    The initial phase can be understood as a step for pre-training the adapters so that when reducing their rank, there
32:    supplying `tinit`.
34:    After the initial phase is over (`tinit` steps have passed) and the final phase has not begun, AdaLoRA reduces the
35:    budget of how much rank each layer is allowed to have with each step. This is where the reduction of rank is
36:    happening. This goes on until `total_step - tfinal` steps are reached.
38:    The last phase, beginning once `total_step - tfinal` steps are reached, does not change the layer ranks anymore but
39:    fine-tunes the reduced-rank layers that resulted from the previous phase.
41:    A practical example: `tinit` is 10, `tfinal` is 20, `total_step` is 100. We spend 10 steps doing pre-training
42:    without rank reduction because our budget is constant (init phase), then we spend 80 (100-20) steps in the
47:        target_r (`int`): The target average rank of incremental matrix.
48:        init_r (`int`): The initial rank for each incremental matrix.
49:        tinit (`int`): The steps of initial fine-tuning warmup.
50:        tfinal (`int`): The number of steps of final fine-tuning.
51:        deltaT (`int`): The time internval between two budget allocations.
55:        total_step (`int`): The total training steps that should be specified before training.
56:        rank_pattern (`list`): The allocated rank for each weight matrix by RankAllocator.
61:    tinit: int = field(default=0, metadata={"help": "The steps of initial warmup."})
62:    tfinal: int = field(default=0, metadata={"help": "The steps of final warmup."})
63:    deltaT: int = field(default=1, metadata={"help": "Step interval of rank allocation."})
67:    total_step: Optional[int] = field(default=None, metadata={"help": "The total training steps."})
68:    rank_pattern: Optional[dict] = field(default=None, metadata={"help": "The saved rank pattern."})
98:                "If you intended to set the initial rank, use `init_r` instead."
101:        if self.total_step is None or self.total_step <= 0:
102:            raise ValueError("AdaLoRA does not work when `total_step` is None, supply a value > 0.")
104:        if self.tinit >= (self.total_step - self.tfinal):
106:                "The supplied schedule values don't allow for a budgeting phase. Decrease `tfinal`/`tinit` or "
107:                "increase `total_step`."
```
</details>

### Step 59: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/adalora_alpaca/adapter_config.json | python3 -m json.tool
```

<details><summary>Output (1293 chars)</summary>

```
{
    "alora_invocation_tokens": null,
    "alpha_pattern": {},
    "arrow_config": null,
    "auto_mapping": null,
    "base_model_name_or_path": "HuggingFaceTB/SmolLM2-135M",
    "beta1": 0.85,
    "beta2": 0.85,
    "bias": "none",
    "corda_config": null,
    "deltaT": 1,
    "ensure_weight_tying": false,
    "eva_config": null,
    "exclude_modules": null,
    "fan_in_fan_out": false,
    "inference_mode": true,
    "init_lora_weights": true,
    "init_r": 16,
    "layer_replication": null,
    "layers_pattern": null,
    "layers_to_transform": null,
    "loftq_config": {},
    "lora_alpha": 32,
    "lora_bias": false,
    "lora_dropout": 0.0,
    "lora_ga_config": null,
    "megatron_config": null,
    "megatron_core": "megatron.core",
    "modules_to_save": null,
    "orth_reg_weight": 0.5,
    "peft_type": "ADALORA",
    "peft_version": "0.19.1",
    "qalora_group_size": 16,
    "r": 8,
    "rank_pattern": null,
    "revision": null,
    "target_modules": [
        "q_proj",
        "v_proj"
    ],
    "target_parameters": null,
    "target_r": 8,
    "task_type": "CAUSAL_LM",
    "tfinal": 0,
    "tinit": 0,
    "total_step": 500,
    "trainable_token_indices": null,
    "use_bdlora": null,
    "use_dora": false,
    "use_qalora": false,
    "use_rslora": false
}
```
</details>

### Step 60: bash

```bash
# Look at dora adapter config
cat /home/ubuntu/workspace/training-export-proprietary/runs/dora_r8_alpaca/adapter_config.json | python3 -c "import sys,json; d=json.load(sys.stdin); print(json.dumps({k:d[k] for k in ['peft_type','r','lora_alpha','target_modules','lora_dropout','use_dora','task_type'] if k in d}, indent=2))"
```

<details><summary>Output (181 chars)</summary>

```
{
  "peft_type": "LORA",
  "r": 8,
  "lora_alpha": 16,
  "target_modules": [
    "q_proj",
    "v_proj"
  ],
  "lora_dropout": 0.05,
  "use_dora": true,
  "task_type": "CAUSAL_LM"
}
```
</details>

### Step 61: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/generations/ | grep -v qwen3 | sort
```

<details><summary>Output (0 chars)</summary>

```

```
</details>

### Step 62: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

# Comprehensive summary table
eval_df = pd.read_parquet('eval_results_comparison.parquet')
train_df = pd.read_parquet('training_curves_comparison.parquet')
summary_df = pd.read_parquet('cross_adapter_comparison.parquet')

# Filter SmolLM2
smol_runs = [r for r in summary_df['run_name'].unique() if not r.startswith('qwen3_')]

# Compute for each run:
# 1. Trainable params
# 2. Final train loss (from training_curves)
# 3. Best eval loss and step
# 4. Final eval loss
# 5. Overfit gap (final eval - best eval)
# 6. Train-eval gap at end (final eval - final train)
# 7. Avg benchmark accuracy
# 8. Turn point (first step where eval starts rising)

results = []
for run in sorted(smol_runs):
    srow = summary_df[summary_df['run_name'] == run].iloc[0]
    
    run_train = train_df[train_df['run_name'] == run]
    eval_rows = run_train[run_train['eval_loss'].notna()].copy()
    train_rows = run_train[run_train['learning_rate'].notna()]
    
    final_train = train_rows.iloc[-1]['loss'] if len(train_rows) > 0 else np.nan
    final_eval = eval_rows.iloc[-1]['eval_loss'] if len(eval_rows) > 0 else np.nan
    best_eval = eval_rows['eval_loss'].min() if len(eval_rows) > 0 else np.nan
    best_step = eval_rows.loc[eval_rows['eval_loss'].idxmin(), 'step'] if len(eval_rows) > 0 else np.nan
    overfit_gap = final_eval - best_eval if not np.isnan(final_eval) else np.nan
    train_eval_gap = final_eval - final_train if not np.isnan(final_eval) else np.nan
    
    # Find turn point (first step after best where eval starts rising)
    if len(eval_rows) > 2:
        best_idx = eval_rows['eval_loss'].idxmin()
        best_pos = eval_rows.index.get_loc(best_idx)
        if best_pos < len(eval_rows) - 1:
            turn_step = int(eval_rows.iloc[best_pos + 1]['step'])
        else:
            turn_step = int(best_step)
    else:
        turn_step = 0
    
    # Get benchmark avg
    run_evals = eval_df[(eval_df['run_name'] == run) & (eval_df['metric'] == 'acc,none')]
    avg_acc = run_evals['value'].mean() if len(run_evals) > 0 else np.nan
    
    adapter_type = srow['type']
    dataset = srow['dataset']
    trainable = srow['trainable_params']
    overhead = srow['overhead_pct']
    
    results.append({
        'run': run,
        'type': adapter_type,
        'dataset': dataset,
        'trainable': trainable,
        'overhead_pct': overhead,
        'final_train_loss': final_train,
        'best_eval_loss': best_eval,
        'best_step': int(best_step) if not np.isnan(best_step) else 0,
        'final_eval_loss': final_eval,
        'overfit_gap': overfit_gap,
        'train_eval_gap': train_eval_gap,
        'turn_step': turn_step,
        'avg_bench_acc': avg_acc,
    })

rdf = pd.DataFrame(results)
# Save as CSV for reference
rdf.to_csv('smollm2_analysis_summary.csv', index=False)
print(rdf.to_string(index=False))
"
```

<details><summary>Output (3382 chars)</summary>

```
                           run    type           dataset  trainable  overhead_pct  final_train_loss  best_eval_loss  best_step  final_eval_loss  overfit_gap  train_eval_gap  turn_step  avg_bench_acc
                adalora_alpaca adalora            alpaca     922560        0.6812          1.341454        1.331713        500         1.331713     0.000000       -0.009741        500          0.554
     adalora_code_instructions adalora code_instructions     922560        0.6812          0.801815        0.915998       1600         0.916812     0.000814        0.114996       1700          0.560
                dora_r8_alpaca    dora            alpaca     483840        0.3584          0.967050        1.285941        400         1.383755     0.097814        0.416705        500          0.557
     dora_r8_code_instructions    dora code_instructions     483840        0.3584          0.565750        0.904891        500         1.017454     0.112563        0.451704        600          0.540
                full_ft_alpaca    full            alpaca  134515008      100.0000          1.104454        1.271201        350         1.272746     0.001546        0.168292        400            NaN
     full_ft_code_instructions    full code_instructions  134515008      100.0000          0.322983        0.889914        500         1.097499     0.207584        0.774515        600            NaN
                    ia3_alpaca     ia3            alpaca      74880        0.0556          1.353783        1.358544        500         1.358544     0.000000        0.004761        500          0.554
         ia3_code_instructions     ia3 code_instructions      74880        0.0556          0.792456        0.918203       2000         0.918203     0.000000        0.125746       2000          0.556
               lora_r16_alpaca    lora            alpaca     921600        0.6805          1.209589        1.284986        500         1.284986     0.000000        0.075397        500          0.559
    lora_r16_code_instructions    lora code_instructions     921600        0.6805          0.420488        0.905935        300         1.152619     0.246685        0.732132        400          0.530
           lora_r16_mlp_alpaca    lora            alpaca    3041280        2.2109          0.093635        1.270496        200         2.498326     1.227830        2.404691        300          0.511
lora_r16_mlp_code_instructions    lora code_instructions    3041280        2.2109          0.097705        0.896585        100         1.711451     0.814867        1.613747        200          0.547
           lora_r32_all_alpaca    lora            alpaca    9768960        6.7706          0.682561        1.273801        100         1.441106     0.167305        0.758545        150          0.555
lora_r32_all_code_instructions    lora code_instructions    9768960        6.7706          0.085292        0.888635        100         1.671726     0.783091        1.586434        200          0.544
                lora_r4_alpaca    lora            alpaca     230400        0.1710          1.270067        1.292421        500         1.292421     0.000000        0.022354        500          0.565
     lora_r4_code_instructions    lora code_instructions     230400        0.1710          0.676179        0.904566        700         0.945839     0.041273        0.269660        800          0.541
```
</details>

### Step 63: read

**Path:** `/home/ubuntu/workspace/peft/src/peft/tuners/lora/dora.py`

<details><summary>Output (3990 chars)</summary>

```
<path>/home/ubuntu/workspace/peft/src/peft/tuners/lora/dora.py</path>
<type>file</type>
<content>
125:                 weight=weight.to(lora_A.device), lora_weight=lora_weight, scaling=scaling
126:             )
127: 
128:         if place_on_cpu:
129:             weight_norm = weight_norm.to("cpu")
130:         self.weight = nn.Parameter(weight_norm, requires_grad=True)
131: 
132:     def forward(self, x, *, lora_A, lora_B, scaling, base_layer, base_result=None, adapter_name="default"):
133:         """
134:         For DoRA, calculate the extra output from LoRA with DoRA applied. This should be added on top of the base layer
135:         output.
136:         """
137:         lora_weight = self.get_lora_weight(lora_A=lora_A, lora_B=lora_B, adapter_name=adapter_name)
138:         lora_weight = lora_weight.to(x.dtype)
139: 
140:         magnitude = self.weight
141:         weight = dequantize_module_weight(base_layer)
142:         weight = weight.to(x.dtype)
143:         weight_norm = self.get_weight_norm(
144:             weight=weight, lora_weight=lora_weight.detach(), scaling=scaling, adapter_name=adapter_name
145:         )
146:         # see section 4.3 of DoRA (https://huggingface.co/papers/2402.09353)
147:         # "[...] we suggest treating ||V +∆V ||_c in
148:         # Eq. (5) as a constant, thereby detaching it from the gradient
149:         # graph. This means that while ||V + ∆V ||_c dynamically
150:         # reflects the updates of ∆V , it won’t receive any gradient
151:         # during backpropagation"
152:         weight_norm = weight_norm.detach()
153:         mag_norm_scale = (magnitude / weight_norm).view(1, -1)
154: 
155:         lora_result = lora_B(lora_A(x))
156: 
157:         bias = None
158:         if base_result is not None:
159:             bias = base_layer.bias
160:             if bias is not None:
161:                 base_result = base_result - bias
162:         else:
163:             base_result = F.linear(x, transpose(weight, self.fan_in_fan_out))
164: 
165:         result_dora = (mag_norm_scale - 1) * base_result + mag_norm_scale * lora_result * scaling
166:         return result_dora
167: 
168:     def __repr__(self) -> str:
169:         rep = super().__repr__()
170:         return "lora.dora." + rep
171: 
172: 
173: class DoraEmbeddingLayer(DoraLinearLayer):
174:     @cache_decorator("lora-weight")
175:     def get_lora_weight(self, lora_A, lora_B, adapter_name: Optional[str] = None):
176:         return (lora_A @ lora_B).T
177: 
178:     def forward(self, x, *, lora_A, lora_B, scaling, base_layer, embed_fn, adapter_name="default"):
179:         """
180:         For DoRA, calculate the extra output from LoRA with DoRA applied. This should be added on top of the base layer
181:         output.
182:         """
183:         lora_weight = self.get_lora_weight(lora_A=lora_A, lora_B=lora_B, adapter_name=adapter_name)
184:         magnitude = self.weight
185:         weight = base_layer.weight
186:         weight_norm = self.get_weight_norm(
187:             weight=weight, lora_weight=lora_weight.detach(), scaling=scaling, adapter_name=adapter_name
188:         )
189:         # see section 4.3 of DoRA (https://huggingface.co/papers/2402.09353)
190:         # "[...] we suggest treating ||V +∆V ||_c in
191:         # Eq. (5) as a constant, thereby detaching it from the gradient
192:         # graph. This means that while ||V + ∆V ||_c dynamically
193:         # reflects the updates of ∆V , it won’t receive any gradient
194:         # during backpropagation"
195:         weight_norm = weight_norm.detach()
196:         mag_norm_scale = magnitude / weight_norm
197:         result_dora = mag_norm_scale * (embed_fn(x, lora_A) @ lora_B) * scaling
198:         return mag_norm_scale, result_dora
199: 
200:     def __repr__(self) -> str:
201:         rep = super().__repr__()
202:         return "lora.dora." + rep
203: 
204: 

(Showing lines 125-204 of 287. Use offset=205 to continue.)
</content>
```
</details>

### Step 64: bash

```bash
# Check the lora config for use_rslora (rank-stabilized LoRA)
grep -n "use_rslora\|rslora\|rsloRA\|sqrt" /home/ubuntu/workspace/peft/src/peft/tuners/lora/config.py | head -20
```

<details><summary>Output (568 chars)</summary>

```
405:        use_rslora (`bool`):
407:            adapter scaling factor to `lora_alpha/math.sqrt(r)`, since it was proven to work better. Otherwise, it will
548:    use_rslora: bool = field(
553:                " which sets the adapter scaling factor to `lora_alpha/math.sqrt(r)`, since it"
922:        # be correctly done when using rslora + rank_pattern/alpha_pattern. We can't really know if the user intends
926:            self.use_rslora
939:                "base weights; if you intend to do this, please ensure not to use rslora or rank_pattern/alpha_pattern."
```
</details>

### Step 65: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && for run in lora_r32_all_alpaca lora_r16_mlp_alpaca lora_r4_alpaca dora_r8_alpaca full_ft_alpaca ia3_alpaca adalora_alpaca; do
  echo "=== $run ==="
  cat runs/$run/memory_profile.json | python3 -m json.tool 2>/dev/null
  echo ""
done
```

<details><summary>Output (1328 chars)</summary>

```
=== lora_r32_all_alpaca ===
{
    "trainable_params": 9768960,
    "total_params": 144283968,
    "adapter_overhead_pct": 6.7706,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 577.14
}

=== lora_r16_mlp_alpaca ===
{
    "trainable_params": 3041280,
    "total_params": 137556288,
    "adapter_overhead_pct": 2.2109,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 550.23
}

=== lora_r4_alpaca ===
{
    "trainable_params": 230400,
    "total_params": 134745408,
    "adapter_overhead_pct": 0.171,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 538.98
}

=== dora_r8_alpaca ===
{
    "trainable_params": 483840,
    "total_params": 134998848,
    "adapter_overhead_pct": 0.3584,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 540.0
}

=== full_ft_alpaca ===
{
    "trainable_params": 134515008,
    "total_params": 134515008,
    "adapter_overhead_pct": 100.0,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 538.06
}

=== ia3_alpaca ===
{
    "trainable_params": 74880,
    "total_params": 134589888,
    "adapter_overhead_pct": 0.0556,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 538.36
}

=== adalora_alpaca ===
{
    "trainable_params": 922560,
    "total_params": 135437628,
    "adapter_overhead_pct": 0.6812,
    "peak_memory_mb": "cpu_only",
    "model_size_mb": 541.75
}
```
</details>

### Step 66: bash

```bash
# Let me look at the datasets to understand their sizes
ls /home/ubuntu/workspace/training-export-proprietary/datasets/
cat /home/ubuntu/workspace/training-export-proprietary/datasets/*.json 2>/dev/null | head -50
ls -la /home/ubuntu/workspace/training-export-proprietary/datasets/
```

<details><summary>Output (314 chars)</summary>

```
alpaca
code_instructions
kto_mix
total 16
drwxr-xr-x. 5 ubuntu ubuntu    60 Jun 25 17:21 .
drwxr-xr-x. 6 ubuntu ubuntu 16384 Jun 25 17:29 ..
drwxr-xr-x. 2 ubuntu ubuntu    63 Jun 25 17:21 alpaca
drwxr-xr-x. 2 ubuntu ubuntu    63 Jun 25 17:21 code_instructions
drwxr-xr-x. 2 ubuntu ubuntu    32 Jun 25 17:21 kto_mix
```
</details>

### Step 67: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/
ls -la /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/
cat /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/dataset_info.json 2>/dev/null | python3 -m json.tool | head -20
cat /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/dataset_dict.json 2>/dev/null | python3 -m json.tool | head -20
```

<details><summary>Output (674 chars)</summary>

```
total 292
drwxr-xr-x. 2 ubuntu ubuntu     63 Jun 25 17:21 .
drwxr-xr-x. 5 ubuntu ubuntu     60 Jun 25 17:21 ..
-rw-r--r--. 1 ubuntu ubuntu    113 Jun 25 17:21 metadata.json
-rw-r--r--. 1 ubuntu ubuntu 264805 Jun 25 17:21 train.jsonl
-rw-r--r--. 1 ubuntu ubuntu  28097 Jun 25 17:21 val.jsonl
total 196
drwxr-xr-x. 2 ubuntu ubuntu     63 Jun 25 17:21 .
drwxr-xr-x. 5 ubuntu ubuntu     60 Jun 25 17:21 ..
-rw-r--r--. 1 ubuntu ubuntu    146 Jun 25 17:21 metadata.json
-rw-r--r--. 1 ubuntu ubuntu 175040 Jun 25 17:21 train.jsonl
-rw-r--r--. 1 ubuntu ubuntu  19025 Jun 25 17:21 val.jsonl

stderr:
Expecting value: line 1 column 1 (char 0)
Expecting value: line 1 column 1 (char 0)
```
</details>

### Step 68: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/metadata.json
echo "---"
cat /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/metadata.json
echo "---"
wc -l /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/train.jsonl
wc -l /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/val.jsonl
wc -l /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/train.jsonl
wc -l /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/val.jsonl
```

<details><summary>Output (614 chars)</summary>

```
{
  "name": "alpaca",
  "source": "tatsu-lab/alpaca",
  "train_samples": 500,
  "val_samples": 50,
  "seed": 42
}---
{
  "name": "code_instructions",
  "source": "code-filtered alpaca or CodeAlpaca-20k",
  "train_samples": 500,
  "val_samples": 50,
  "seed": 42
}---
500 /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/train.jsonl
50 /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/val.jsonl
500 /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/train.jsonl
50 /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/val.jsonl
```
</details>

### Step 69: bash

```bash
# Check first sample of each dataset
head -1 /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/train.jsonl | python3 -m json.tool
echo "---"
head -1 /home/ubuntu/workspace/training-export-proprietary/datasets/code_instructions/train.jsonl | python3 -m json.tool
```

<details><summary>Output (1372 chars)</summary>

```
{
    "text": "Below is an instruction that describes a task, paired with an input that provides further context. Write a response that appropriately completes the request.\n\n### Instruction:\nDescribe the character of the protagonist in the given TV show.\n\n### Input:\nGame of Thrones\n\n### Response:\nThe protagonist of Game of Thrones is the longsuffering and honorable Eddard \"Ned\" Stark. Ned is the head of an ancient and powerful house in the north of the Seven Kingdoms, but he is nothing like the scheming lords of the south. He is a man of incredible honor and integrity, a loyal friend and the driving force behind his family. Despite facing tremendous odds, Ned remains steadfast and determined in his duty to do what is right, even if it means great personal cost. In many ways, Ned serves as a moral compass for the show, and his sense of duty and justice serves as a contrast to the political machinations of the south."
}
---
{
    "text": "### Instruction:\nWrite a code to remove the oldest elements from a list until the list contains at most 10 elements.\n### Input:\nlist = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]\n### Response:\ndef remove_old_elements(lst):\n  for i in range(len(lst) - 10):\n    lst.pop(0)\n  return lst\n\nlist = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]\nprint(remove_old_elements(list)) # [3, 4, 5, 6, 7, 8, 9, 10, 11, 12]"
}
```
</details>

### Step 70: bash

```bash
# Check if there are per-checkpoint eval results
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/
echo "---"
# Check if there are checkpoint-specific evaluation directories anywhere
find /home/ubuntu/workspace/training-export-proprietary/evaluations/ -name "*checkpoint*" 2>/dev/null | head -10
echo "---"
# Check if eval_results.json mentions which checkpoint was evaluated
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/eval_results.json | python3 -c "import sys,json; d=json.load(sys.stdin); print(json.dumps(d, indent=2))" | head -20
```

<details><summary>Output (597 chars)</summary>

```
eval_results.json
samples_arc_easy.jsonl
samples_boolq.jsonl
samples_hellaswag.jsonl
samples_piqa.jsonl
samples_winogrande.jsonl
---
---
{
  "adapter": "lora_r32_all_alpaca",
  "base_model": "HuggingFaceTB/SmolLM2-135M",
  "benchmarks": [
    "arc_easy",
    "hellaswag",
    "piqa",
    "winogrande",
    "boolq"
  ],
  "limit": 200,
  "results": {
    "arc_easy": {
      "name": "arc_easy",
      "alias": "arc_easy",
      "sample_len": 200,
      "acc,none": 0.51,
      "acc_stderr,none": 0.035436970729343674,
      "acc_norm,none": 0.545,
      "acc_norm_stderr,none": 0.035300219937532865
```
</details>

### Step 71: bash

```bash
# Now look at the intermediate checkpoint READMEs to see if they contain useful info
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/checkpoint-100/README.md | head -40
```

<details><summary>Output (941 chars)</summary>

```
---
base_model: HuggingFaceTB/SmolLM2-135M
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:HuggingFaceTB/SmolLM2-135M
- lora
- transformers
---

# Model Card for Model ID

<!-- Provide a quick summary of what the model is/does. -->



## Model Details

### Model Description

<!-- Provide a longer summary of what this model is. -->



- **Developed by:** [More Information Needed]
- **Funded by [optional]:** [More Information Needed]
- **Shared by [optional]:** [More Information Needed]
- **Model type:** [More Information Needed]
- **Language(s) (NLP):** [More Information Needed]
- **License:** [More Information Needed]
- **Finetuned from model [optional]:** [More Information Needed]

### Model Sources [optional]

<!-- Provide the basic links for the model. -->

- **Repository:** [More Information Needed]
- **Paper [optional]:** [More Information Needed]
- **Demo [optional]:** [More Information Needed]
```
</details>

### Step 72: bash

```bash
# Check intermediate checkpoint trainer states for the lora_r32_all_alpaca run
# This gives us the eval_loss at each checkpoint step
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json, os

# Get trainer states from intermediate checkpoints for lora_r32_all_alpaca
run = 'lora_r32_all_alpaca'
ckpt_dir = f'runs/{run}/checkpoints'
ckpts = sorted(os.listdir(ckpt_dir), key=lambda x: int(x.split('-')[1]))
for ckpt in ckpts:
    ts_path = f'{ckpt_dir}/{ckpt}/trainer_state.json'
    with open(ts_path) as f:
        ts = json.load(f)
    eval_entries = [e for e in ts.get('log_history', []) if 'eval_loss' in e]
    last_eval = eval_entries[-1] if eval_entries else None
    if last_eval:
        print(f'{ckpt}: step={last_eval[\"step\"]}, eval_loss={last_eval[\"eval_loss\"]:.4f}')
"
```

<details><summary>Output (214 chars)</summary>

```
checkpoint-100: step=100, eval_loss=1.2738
checkpoint-200: step=200, eval_loss=1.2785
checkpoint-300: step=300, eval_loss=1.3488
checkpoint-400: step=400, eval_loss=1.4348
checkpoint-500: step=500, eval_loss=1.4411
```
</details>

### Step 73: bash

```bash
# Now let's understand the training schedule differences
# Some runs train 500 steps (1 epoch based on 500 samples, bs=4), others train 2000 steps (4 epochs)
# Let me verify epochs from training logs
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# Get max epoch per run
for run in sorted(smol['run_name'].unique()):
    run_df = smol[smol['run_name'] == run]
    train_df = run_df[run_df['learning_rate'].notna()]
    max_step = int(train_df['step'].max())
    max_epoch = train_df['epoch'].max() if 'epoch' in train_df.columns else 'N/A'
    print(f'{run:45s} | max_step={max_step:5d} | max_epoch={max_epoch}')
"
```

<details><summary>Output (1263 chars)</summary>

```
adalora_alpaca                                | max_step=  500 | max_epoch=N/A
adalora_code_instructions                     | max_step= 2000 | max_epoch=N/A
dora_r8_alpaca                                | max_step= 2000 | max_epoch=N/A
dora_r8_code_instructions                     | max_step= 2000 | max_epoch=N/A
full_ft_alpaca                                | max_step=  500 | max_epoch=N/A
full_ft_code_instructions                     | max_step= 2000 | max_epoch=N/A
ia3_alpaca                                    | max_step=  500 | max_epoch=N/A
ia3_code_instructions                         | max_step= 2000 | max_epoch=N/A
lora_r16_alpaca                               | max_step=  500 | max_epoch=N/A
lora_r16_code_instructions                    | max_step= 2000 | max_epoch=N/A
lora_r16_mlp_alpaca                           | max_step= 2000 | max_epoch=N/A
lora_r16_mlp_code_instructions                | max_step= 2000 | max_epoch=N/A
lora_r32_all_alpaca                           | max_step=  500 | max_epoch=N/A
lora_r32_all_code_instructions                | max_step= 2000 | max_epoch=N/A
lora_r4_alpaca                                | max_step=  500 | max_epoch=N/A
lora_r4_code_instructions                     | max_step= 2000 | max_epoch=N/A
```
</details>

### Step 74: bash

```bash
# Get epoch from training_log.csv
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd

for run in ['lora_r32_all_alpaca', 'lora_r4_alpaca', 'lora_r16_mlp_alpaca', 'dora_r8_alpaca', 'full_ft_alpaca', 'lora_r16_code_instructions', 'lora_r32_all_code_instructions']:
    df = pd.read_csv(f'runs/{run}/training_log.csv')
    train_df = df[df['learning_rate'].notna()]
    max_epoch = train_df['epoch'].max()
    max_step = train_df['step'].max()
    print(f'{run:45s} | max_step={max_step:5.0f} | max_epoch={max_epoch:.1f} | steps_per_epoch={max_step/max_epoch if max_epoch > 0 else \"N/A\":.1f}')
"
```

<details><summary>Output (724 chars)</summary>

```
lora_r32_all_alpaca                           | max_step=  500 | max_epoch=4.0 | steps_per_epoch=125.0
lora_r4_alpaca                                | max_step=  500 | max_epoch=4.0 | steps_per_epoch=125.0
lora_r16_mlp_alpaca                           | max_step= 2000 | max_epoch=16.0 | steps_per_epoch=125.0
dora_r8_alpaca                                | max_step= 2000 | max_epoch=16.0 | steps_per_epoch=125.0
full_ft_alpaca                                | max_step=  500 | max_epoch=4.0 | steps_per_epoch=125.0
lora_r16_code_instructions                    | max_step= 2000 | max_epoch=16.0 | steps_per_epoch=125.0
lora_r32_all_code_instructions                | max_step= 2000 | max_epoch=16.0 | steps_per_epoch=125.0
```
</details>

### Step 75: bash

```bash
# Let's understand the training schedule pattern more
# 500 steps = 4 epochs, 2000 steps = 16 epochs
# With 500 training samples and bs=4: 125 steps per epoch
# So some runs train for 4 epochs, others for 16 epochs

# Let me now check which runs have 500 vs 2000 steps and map them to the adapter type
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd

df = pd.read_csv('cross_adapter_comparison.csv' if False else None)
import json

summary = pd.read_parquet('cross_adapter_comparison.parquet')
smol = summary[~summary['run_name'].str.startswith('qwen3_')]

for _, row in smol.sort_values('run_name').iterrows():
    print(f'{row[\"run_name\"]:45s} | type={row[\"type\"]:8s} | steps={row[\"max_steps\"]:5d} | trainable={row[\"trainable_params\"]:10d} | overhead={row[\"overhead_pct\"]:6.2f}% | final_train={row[\"final_train_loss\"]:.4f}')
"
```

<details><summary>Output (0 chars)</summary>

```

```
</details>

### Step 76: bash

```bash
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd

summary = pd.read_parquet('cross_adapter_comparison.parquet')
smol = summary[~summary['run_name'].str.startswith('qwen3_')]

for _, row in smol.sort_values('run_name').iterrows():
    print(f'{row[\"run_name\"]:45s} | type={row[\"type\"]:8s} | steps={row[\"max_steps\"]:5d} | trainable={row[\"trainable_params\"]:10d} | overhead={row[\"overhead_pct\"]:6.2f}% | final_train={row[\"final_train_loss\"]:.4f}')
"
```

<details><summary>Output (2223 chars)</summary>

```
adalora_alpaca                                | type=adalora  | steps=  500 | trainable=    922560 | overhead=  0.68% | final_train=1.7979
adalora_code_instructions                     | type=adalora  | steps= 2000 | trainable=    922560 | overhead=  0.68% | final_train=0.9063
dora_r8_alpaca                                | type=dora     | steps= 2000 | trainable=    483840 | overhead=  0.36% | final_train=1.1140
dora_r8_code_instructions                     | type=dora     | steps= 2000 | trainable=    483840 | overhead=  0.36% | final_train=0.6990
full_ft_alpaca                                | type=full     | steps=  500 | trainable= 134515008 | overhead=100.00% | final_train=1.2242
full_ft_code_instructions                     | type=full     | steps= 2000 | trainable= 134515008 | overhead=100.00% | final_train=0.5090
ia3_alpaca                                    | type=ia3      | steps=  500 | trainable=     74880 | overhead=  0.06% | final_train=1.5565
ia3_code_instructions                         | type=ia3      | steps= 2000 | trainable=     74880 | overhead=  0.06% | final_train=0.8482
lora_r16_alpaca                               | type=lora     | steps=  500 | trainable=    921600 | overhead=  0.68% | final_train=1.2895
lora_r16_code_instructions                    | type=lora     | steps= 2000 | trainable=    921600 | overhead=  0.68% | final_train=0.6175
lora_r16_mlp_alpaca                           | type=lora     | steps= 2000 | trainable=   3041280 | overhead=  2.21% | final_train=0.4408
lora_r16_mlp_code_instructions                | type=lora     | steps= 2000 | trainable=   3041280 | overhead=  2.21% | final_train=0.3184
lora_r32_all_alpaca                           | type=lora     | steps=  500 | trainable=   9768960 | overhead=  6.77% | final_train=0.9832
lora_r32_all_code_instructions                | type=lora     | steps= 2000 | trainable=   9768960 | overhead=  6.77% | final_train=0.2672
lora_r4_alpaca                                | type=lora     | steps=  500 | trainable=    230400 | overhead=  0.17% | final_train=1.3627
lora_r4_code_instructions                     | type=lora     | steps= 2000 | trainable=    230400 | overhead=  0.17% | final_train=0.7622
```
</details>

### Step 77: bash

```bash
# Let me also check the learning rate schedules - are they all using the same LR?
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# Check initial and peak LR for each run
for run in sorted(smol['run_name'].unique()):
    run_df = smol[smol['run_name'] == run]
    train_df = run_df[run_df['learning_rate'].notna()]
    lr_max = train_df['learning_rate'].max()
    lr_min = train_df['learning_rate'].min()
    lr_first = train_df.iloc[0]['learning_rate']
    lr_last = train_df.iloc[-1]['learning_rate']
    print(f'{run:45s} | lr_first={lr_first:.6f} | lr_max={lr_max:.6f} | lr_min={lr_min:.6f} | lr_last={lr_last:.6f}')
"
```

<details><summary>Output (1935 chars)</summary>

```
adalora_alpaca                                | lr_first=0.000491 | lr_max=0.000491 | lr_min=0.000001 | lr_last=0.000001
adalora_code_instructions                     | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
dora_r8_alpaca                                | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
dora_r8_code_instructions                     | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
full_ft_alpaca                                | lr_first=0.000010 | lr_max=0.000010 | lr_min=0.000000 | lr_last=0.000000
full_ft_code_instructions                     | lr_first=0.000010 | lr_max=0.000010 | lr_min=0.000000 | lr_last=0.000000
ia3_alpaca                                    | lr_first=0.000491 | lr_max=0.000491 | lr_min=0.000001 | lr_last=0.000001
ia3_code_instructions                         | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
lora_r16_alpaca                               | lr_first=0.000491 | lr_max=0.000491 | lr_min=0.000001 | lr_last=0.000001
lora_r16_code_instructions                    | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
lora_r16_mlp_alpaca                           | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
lora_r16_mlp_code_instructions                | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
lora_r32_all_alpaca                           | lr_first=0.000491 | lr_max=0.000491 | lr_min=0.000001 | lr_last=0.000001
lora_r32_all_code_instructions                | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
lora_r4_alpaca                                | lr_first=0.000491 | lr_max=0.000491 | lr_min=0.000001 | lr_last=0.000001
lora_r4_code_instructions                     | lr_first=0.000499 | lr_max=0.000499 | lr_min=0.000000 | lr_last=0.000000
```
</details>

### Step 78: bash

```bash
# Final check: verify the adapter weight norm comparison for all adapter types
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json, numpy as np, os

# For all SmolLM2 runs, summarize the adapter weight statistics
runs = [r for r in os.listdir('runs') if not r.startswith('qwen3_')]
for run in sorted(runs):
    stats_path = f'runs/{run}/adapter_weight_stats.json'
    if not os.path.exists(stats_path):
        continue
    with open(stats_path) as f:
        stats = json.load(f)
    
    # Collect all norms
    all_norms = []
    b_norms = []
    for key, val in stats.items():
        if 'norm' in val:
            all_norms.append(val['norm'])
            if 'lora_B' in key or 'lora_B' in key:
                b_norms.append(val['norm'])
    
    if all_norms:
        print(f'{run:45s} | all_norms: mean={np.mean(all_norms):.4f} max={np.max(all_norms):.4f} | B_norms: mean={np.mean(b_norms):.4f} max={np.max(b_norms):.4f}' if b_norms else f'{run:45s} | all_norms: mean={np.mean(all_norms):.4f} max={np.max(all_norms):.4f}')
"
```

<details><summary>Output (1737 chars)</summary>

```
adalora_alpaca                                | all_norms: mean=2.7921 max=4.0147 | B_norms: mean=3.9995 max=4.0147
adalora_code_instructions                     | all_norms: mean=2.8613 max=4.0000 | B_norms: mean=4.0000 max=4.0000
dora_r8_alpaca                                | all_norms: mean=31.0141 max=161.5218 | B_norms: mean=1.6124 max=2.8352
dora_r8_code_instructions                     | all_norms: mean=30.9630 max=161.5381 | B_norms: mean=1.5232 max=2.5789
full_ft_alpaca                                | all_norms: mean=101.9546 max=712.8192
full_ft_code_instructions                     | all_norms: mean=101.9459 max=712.5477
ia3_alpaca                                    | all_norms: mean=22.7054 max=39.2846
ia3_code_instructions                         | all_norms: mean=22.6201 max=39.1196
lora_r16_alpaca                               | all_norms: mean=1.8522 max=3.1834 | B_norms: mean=0.8918 max=1.3664
lora_r16_code_instructions                    | all_norms: mean=3.0534 max=4.9818 | B_norms: mean=1.9662 max=3.2820
lora_r16_mlp_alpaca                           | all_norms: mean=3.8931 max=6.1666 | B_norms: mean=3.0424 max=4.1906
lora_r16_mlp_code_instructions                | all_norms: mean=3.3662 max=4.9344 | B_norms: mean=2.6245 max=3.5323
lora_r32_all_alpaca                           | all_norms: mean=2.5172 max=4.4773 | B_norms: mean=1.2365 max=2.3108
lora_r32_all_code_instructions                | all_norms: mean=3.2448 max=5.8570 | B_norms: mean=2.1256 max=4.2158
lora_r4_alpaca                                | all_norms: mean=1.1847 max=1.9976 | B_norms: mean=0.6913 max=1.0376
lora_r4_code_instructions                     | all_norms: mean=1.8443 max=3.0627 | B_norms: mean=1.1854 max=2.0375
```
</details>

### Step 79: bash

```bash
# Let me also check the lora_r16_mlp configs more carefully to understand target modules
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json

for run in ['lora_r16_mlp_alpaca', 'lora_r16_mlp_code_instructions', 'lora_r32_all_alpaca', 'lora_r32_all_code_instructions']:
    with open(f'runs/{run}/adapter_config.json') as f:
        d = json.load(f)
    r = d.get('r', 'N/A')
    alpha = d.get('lora_alpha', 'N/A')
    targets = d.get('target_modules', [])
    dropout = d.get('lora_dropout', 'N/A')
    scaling = alpha / r if isinstance(r, int) and isinstance(alpha, int) else 'N/A'
    print(f'{run}:')
    print(f'  r={r}, alpha={alpha}, scaling={scaling}, dropout={dropout}')
    print(f'  target_modules={targets}')
    # Count how many adapter matrices per layer
    # For SmolLM2-135M, there are 12 layers (0-11)
    # q,k,v,o = attention (4), gate,up,down = MLP (3)
    if isinstance(targets, list):
        attn = [t for t in targets if t in ['q_proj','k_proj','v_proj','o_proj']]
        mlp = [t for t in targets if t in ['gate_proj','up_proj','down_proj']]
        print(f'  attention modules: {attn}')
        print(f'  mlp modules: {mlp}')
    print()
"
```

<details><summary>Output (966 chars)</summary>

```
lora_r16_mlp_alpaca:
  r=16, alpha=32, scaling=2.0, dropout=0.05
  target_modules=['up_proj', 'gate_proj', 'down_proj']
  attention modules: []
  mlp modules: ['up_proj', 'gate_proj', 'down_proj']

lora_r16_mlp_code_instructions:
  r=16, alpha=32, scaling=2.0, dropout=0.05
  target_modules=['up_proj', 'gate_proj', 'down_proj']
  attention modules: []
  mlp modules: ['up_proj', 'gate_proj', 'down_proj']

lora_r32_all_alpaca:
  r=32, alpha=64, scaling=2.0, dropout=0.1
  target_modules=['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  attention modules: ['q_proj', 'k_proj', 'o_proj', 'v_proj']
  mlp modules: ['up_proj', 'gate_proj', 'down_proj']

lora_r32_all_code_instructions:
  r=32, alpha=64, scaling=2.0, dropout=0.1
  target_modules=['q_proj', 'k_proj', 'v_proj', 'o_proj', 'up_proj', 'gate_proj', 'down_proj']
  attention modules: ['q_proj', 'k_proj', 'v_proj', 'o_proj']
  mlp modules: ['up_proj', 'gate_proj', 'down_proj']
```
</details>

### Step 80: bash

```bash
# Let me also check the dora and adalora configs
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import json

for run in ['dora_r8_alpaca', 'dora_r8_code_instructions', 'adalora_alpaca', 'adalora_code_instructions', 'ia3_alpaca', 'ia3_code_instructions']:
    with open(f'runs/{run}/adapter_config.json') as f:
        d = json.load(f)
    print(f'=== {run} ===')
    print(f'  peft_type={d.get(\"peft_type\",\"N/A\")}')
    if 'r' in d:
        print(f'  r={d[\"r\"]}, alpha={d.get(\"lora_alpha\",\"N/A\")}, scaling={d.get(\"lora_alpha\",0)/d[\"r\"] if d[\"r\"] > 0 else \"N/A\"}')
    print(f'  target_modules={d.get(\"target_modules\",\"N/A\")}')
    print(f'  dropout={d.get(\"lora_dropout\",\"N/A\")}')
    if d.get('peft_type') == 'ADALORA':
        print(f'  init_r={d.get(\"init_r\")}, target_r={d.get(\"target_r\")}, tinit={d.get(\"tinit\")}, tfinal={d.get(\"tfinal\")}, total_step={d.get(\"total_step\")}')
    if d.get('use_dora'):
        print(f'  use_dora=True')
    print()
"
```

<details><summary>Output (900 chars)</summary>

```
=== dora_r8_alpaca ===
  peft_type=LORA
  r=8, alpha=16, scaling=2.0
  target_modules=['q_proj', 'v_proj']
  dropout=0.05
  use_dora=True

=== dora_r8_code_instructions ===
  peft_type=LORA
  r=8, alpha=16, scaling=2.0
  target_modules=['q_proj', 'v_proj']
  dropout=0.05
  use_dora=True

=== adalora_alpaca ===
  peft_type=ADALORA
  r=8, alpha=32, scaling=4.0
  target_modules=['q_proj', 'v_proj']
  dropout=0.0
  init_r=16, target_r=8, tinit=0, tfinal=0, total_step=500

=== adalora_code_instructions ===
  peft_type=ADALORA
  r=8, alpha=32, scaling=4.0
  target_modules=['q_proj', 'v_proj']
  dropout=0.0
  init_r=16, target_r=8, tinit=0, tfinal=0, total_step=2000

=== ia3_alpaca ===
  peft_type=IA3
  target_modules=['v_proj', 'q_proj', 'down_proj', 'k_proj']
  dropout=N/A

=== ia3_code_instructions ===
  peft_type=IA3
  target_modules=['q_proj', 'v_proj', 'down_proj', 'k_proj']
  dropout=N/A
```
</details>

### Step 81: bash

```bash
# Let me now look at the detailed training trajectory for a stable run vs unstable run for the alpaca dataset
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

# Compare 4 alpaca runs side by side: lora_r4, lora_r16, lora_r32_all, lora_r16_mlp
# But lora_r16_mlp and dora_r8 are 2000 steps while others are 500
# For comparison, show the first 500 steps of each

runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'lora_r16_mlp_alpaca', 'dora_r8_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'full_ft_alpaca']
eval_steps = [50, 100, 150, 200, 250, 300, 350, 400, 450, 500]

print('Eval Loss Trajectory (alpaca dataset, first 500 steps):')
print(f'{\"Step\":>5s}', end='')
for run in runs:
    label = run.replace('_alpaca','')
    print(f'  {label:>14s}', end='')
print()
print('-' * (5 + 16*len(runs)))

for step in eval_steps:
    print(f'{step:5d}', end='')
    for run in runs:
        run_df = smol[smol['run_name'] == run]
        eval_df = run_df[run_df['eval_loss'].notna()]
        row = eval_df[eval_df['step'] == step]
        if len(row) > 0:
            val = row.iloc[0]['eval_loss']
            print(f'  {val:14.4f}', end='')
        else:
            print(f'  {\"--\":>14s}', end='')
    print()
"
```

<details><summary>Output (1663 chars)</summary>

```
Eval Loss Trajectory (alpaca dataset, first 500 steps):
 Step         lora_r4        lora_r16    lora_r32_all    lora_r16_mlp         dora_r8             ia3         adalora         full_ft
-------------------------------------------------------------------------------------------------------------------------------------
   50          1.4845          1.3453          1.2900              --              --          2.0330          2.8040          1.3347
  100          1.3345          1.3061          1.2738          1.2724          1.3130          1.7685          2.2507          1.2916
  150          1.3157          1.2965          1.2815              --              --          1.5808          1.7739          1.2854
  200          1.3049          1.2890          1.2785          1.2705          1.2917          1.4624          1.4684          1.2768
  250          1.2995          1.2870          1.2795              --              --          1.4106          1.3858          1.2716
  300          1.2987          1.2913          1.3488          1.3309          1.2935          1.3846          1.3575          1.2728
  350          1.2952          1.2858          1.3515              --              --          1.3705          1.3447          1.2712
  400          1.2928          1.2854          1.4348          1.3951          1.2859          1.3631          1.3365          1.2722
  450          1.2936          1.2874          1.4450              --              --          1.3597          1.3332          1.2726
  500          1.2924          1.2850          1.4411          1.4349          1.2879          1.3585          1.3317          1.2727
```
</details>

### Step 82: bash

```bash
# Same comparison for code_instructions dataset
cd /home/ubuntu/workspace/training-export-proprietary && python3 -c "
import pandas as pd
import numpy as np

df = pd.read_parquet('training_curves_comparison.parquet')
smol = df[~df['run_name'].str.startswith('qwen3_')]

runs = ['lora_r4_code_instructions', 'lora_r16_code_instructions', 'lora_r32_all_code_instructions', 
        'lora_r16_mlp_code_instructions', 'dora_r8_code_instructions', 'ia3_code_instructions', 
        'adalora_code_instructions', 'full_ft_code_instructions']
eval_steps = [100, 200, 300, 400, 500, 700, 1000, 1500, 2000]

print('Eval Loss Trajectory (code_instructions dataset):')
print(f'{\"Step\":>5s}', end='')
for run in runs:
    label = run.replace('_code_instructions','')
    print(f'  {label:>14s}', end='')
print()
print('-' * (5 + 16*len(runs)))

for step in eval_steps:
    print(f'{step:5d}', end='')
    for run in runs:
        run_df = smol[smol['run_name'] == run]
        eval_df = run_df[run_df['eval_loss'].notna()]
        row = eval_df[eval_df['step'] == step]
        if len(row) > 0:
            val = row.iloc[0]['eval_loss']
            print(f'  {val:14.4f}', end='')
        else:
            print(f'  {\"--\":>14s}', end='')
    print()
"
```

<details><summary>Output (1523 chars)</summary>

```
Eval Loss Trajectory (code_instructions dataset):
 Step         lora_r4        lora_r16    lora_r32_all    lora_r16_mlp         dora_r8             ia3         adalora         full_ft
-------------------------------------------------------------------------------------------------------------------------------------
  100          0.9525          0.9302          0.8886          0.8966          0.9396          1.0567          1.2917          0.9157
  200          0.9320          0.9189          0.9030          0.9022          0.9259          0.9900          1.0032          0.8970
  300          0.9141          0.9059          0.9429          0.9191          0.9097          0.9674          0.9617          0.8902
  400          0.9129          0.9145          1.0223          0.9731          0.9125          0.9555          0.9495          0.8944
  500          0.9067          0.9081          1.0293          0.9578          0.9049          0.9467          0.9391          0.8899
  700          0.9046          0.9300          1.2154          1.1227          0.9117          0.9329          0.9267          0.9171
 1000          0.9121          0.9746          1.3586          1.3168          0.9312          0.9245          0.9203          0.9618
 1500          0.9351          1.0837          1.5806          1.6147          0.9902          0.9193          0.9169          1.0521
 2000          0.9458          1.1526          1.6717          1.7115          1.0175          0.9182          0.9168          1.0975
```
</details>

### Step 83: write

**Path:** `/home/ubuntu/workspace/REPORT.md`

```
# SmolLM2-135M Adapter Training Sweep: Overfitting Trajectory Analysis

## Executive Summary

The SmolLM2-135M PEFT sweep trained 8 adapter configurations (lora\_r4, lora\_r16, lora\_r32\_all, lora\_r16\_mlp, ia3, adalora, dora\_r8, full\_ft) across 2 datasets (alpaca, code\_instructions), producing 16 runs. The central mystery — **lora\_r32\_all\_alpaca has the lowest final training loss (0.68) but the worst eval loss (1.44) and mediocre benchmark scores** — is explained by classic overfitting that is invisible in the final training loss but unmistakable in the eval\_loss trajectory.

Training loss monotonically decreases for every run because the model memorizes the 500-sample training set. Eval loss, however, tells a different story: **6 of 16 runs begin overfitting partway through training**, with eval loss rising significantly above its minimum. The worst case (lora\_r16\_mlp\_alpaca) sees eval loss climb from 1.27 to 2.50 — nearly doubling — while training loss drops to 0.09.

The overfitting is **capacity-driven and module-target-driven**: high-parameter-count adapters (r=32 all-linear, r=16 MLP-only) and long training schedules (2000 steps = 16 epochs) are the primary risk factors. No early stopping or best-checkpoint tracking was configured, so the deployed models are always the final (most overfit) checkpoints.

---

## 1. Experimental Setup

### Base Model & Datasets
- **Base model**: HuggingFaceTB/SmolLM2-135M (12-layer decoder-only, ~135M params)
- **Datasets**: 500 training samples, 50 validation samples each
  - `alpaca`: General instruction-following (tatsu-lab/alpaca)
  - `code_instructions`: Code-filtered instruction data
- **Batch size**: 4 (125 steps/epoch)

### Training Schedules
Two training durations were used, creating a natural experiment in overfitting:

| Duration | Epochs | Runs |
|----------|--------|------|
| 500 steps | 4 epochs | lora\_r4\_alpaca, lora\_r16\_alpaca, lora\_r32\_all\_alpaca, ia3\_alpaca, adalora\_alpaca, full\_ft\_alpaca |
| 2000 steps | 16 epochs | All code\_instructions runs + dora\_r8\_alpaca, lora\_r16\_mlp\_alpaca |

### Hyperparameters
- **Learning rate**: 5e-4 for all PEFT adapters; 1e-5 for full\_ft (50x lower)
- **LR schedule**: Cosine decay to ~0
- **Weight decay**: 0.01
- **Seed**: 42
- **Eval frequency**: Every 50 steps (500-step runs) or every 100 steps (2000-step runs)
- **Checkpoint frequency**: Every 100 steps

### Adapter Configurations

| Adapter | PEFT Type | r | Alpha | Scaling | Target Modules | Trainable Params | Overhead |
|---------|-----------|---|-------|---------|-----------------|-----------------|----------|
| lora\_r4 | LoRA | 4 | 8 | 2.0 | q\_proj, v\_proj (attn) | 230,400 | 0.17% |
| lora\_r16 | LoRA | 16 | 32 | 2.0 | q\_proj, v\_proj (attn) | 921,600 | 0.68% |
| lora\_r32\_all | LoRA | 32 | 64 | 2.0 | all 7 linear modules | 9,768,960 | 6.77% |
| lora\_r16\_mlp | LoRA | 16 | 32 | 2.0 | gate\_proj, up\_proj, down\_proj (MLP only) | 3,041,280 | 2.21% |
| dora\_r8 | LoRA+DoRA | 8 | 16 | 2.0 | q\_proj, v\_proj (attn) | 483,840 | 0.36% |
| adalora | AdaLoRA | 8 (init 16) | 32 | 4.0 | q\_proj, v\_proj (attn) | 922,560 | 0.68% |
| ia3 | IA³ | — | — | — | q\_proj, k\_proj, v\_proj, down\_proj | 74,880 | 0.06% |
| full\_ft | Full FT | — | — | — | all weights | 134,515,008 | 100% |

**Key configuration notes:**
- All LoRA configs use `scaling = alpha/r = 2.0` (except adalora at 4.0)
- lora\_r32\_all targets all 7 linear module types (4 attention + 3 MLP), at r=32
- lora\_r16\_mlp targets **only MLP modules** — no attention adaptation
- AdaLoRA uses adaptive rank pruning (init\_r=16 → target\_r=8) with importance-based budgeting
- DoRA decomposes the weight update into magnitude and direction components
- IA³ learns only per-channel scaling vectors (no low-rank deltas)

---

## 2. The Core Finding: Train Loss vs. Eval Loss Divergence

### 2.1 The lora\_r32\_all\_alpaca Case

This is the run that triggered the investigation. Here is the full trajectory:

| Step | Epoch | Train Loss | Eval Loss | Train→Eval Gap |
|------|-------|-----------|-----------|----------------|
| 50 | 0.4 | 1.290 | 1.290 | +0.000 |
| 100 | 0.8 | 1.325 | **1.274** ← best | −0.052 |
| 150 | 1.2 | 1.024 | 1.282 | +0.257 |
| 200 | 1.6 | 1.084 | 1.278 | +0.195 |
| 250 | 2.0 | 1.082 | 1.279 | +0.198 |
| 300 | 2.4 | 0.835 | 1.349 | +0.514 |
| 350 | 2.8 | 0.868 | 1.351 | +0.484 |
| 400 | 3.2 | 0.688 | 1.435 | +0.747 |
| 450 | 3.6 | 0.661 | 1.445 | +0.784 |
| 500 | 4.0 | **0.683** | **1.441** | **+0.759** |

**What happened**: Training loss dropped 59% (1.68 → 0.68), while eval loss *rose* 13% (1.27 → 1.44). The best eval checkpoint was step 100 (eval\_loss 1.274) — after just 0.8 epochs. Every subsequent checkpoint was worse. The final checkpoint is 0.167 eval-loss points above the best, and the train→eval gap has grown to +0.76.

The final training loss (0.68) is the lowest of any alpaca run, which is exactly what you'd expect from a high-capacity adapter memorizing 500 examples. But this "success" on training loss is actually the symptom of the problem.

### 2.2 The Wider Pattern: Overfit Gap Across All 16 Runs

The **overfit gap** (final eval loss − best eval loss) quantifies how much the model degraded after reaching its generalization peak:

| Run | Type | Steps | Trainable Params | Best Eval Loss | Best Step | Final Eval Loss | Overfit Gap | Severity |
|-----|------|-------|-----------------|---------------|-----------|----------------|-------------|----------|
| lora\_r16\_mlp\_alpaca | LoRA (MLP) | 2000 | 3,041,280 | 1.270 | 200 | 2.498 | **+1.228** | Catastrophic |
| lora\_r16\_mlp\_code | LoRA (MLP) | 2000 | 3,041,280 | 0.897 | 100 | 1.711 | **+0.815** | Catastrophic |
| lora\_r32\_all\_code | LoRA (all) | 2000 | 9,768,960 | 0.889 | 100 | 1.672 | **+0.783** | Severe |
| lora\_r32\_all\_alpaca | LoRA (all) | 500 | 9,768,960 | 1.274 | 100 | 1.441 | **+0.167** | Moderate |
| lora\_r16\_code | LoRA (attn) | 2000 | 921,600 | 0.906 | 300 | 1.153 | **+0.247** | Moderate |
| full\_ft\_code | Full FT | 2000 | 134,515,008 | 0.890 | 500 | 1.098 | **+0.208** | Moderate |
| dora\_r8\_code | DoRA | 2000 | 483,840 | 0.905 | 500 | 1.018 | +0.113 | Mild |
| dora\_r8\_alpaca | DoRA | 2000 | 483,840 | 1.286 | 400 | 1.384 | +0.098 | Mild |
| lora\_r4\_code | LoRA (attn) | 2000 | 230,400 | 0.905 | 700 | 0.946 | +0.041 | Minimal |
| adalora\_code | AdaLoRA | 2000 | 922,560 | 0.916 | 1600 | 0.917 | +0.001 | Stable |
| full\_ft\_alpaca | Full FT | 500 | 134,515,008 | 1.271 | 350 | 1.273 | +0.002 | Stable |
| ia3\_code | IA³ | 2000 | 74,880 | 0.918 | 2000 | 0.918 | +0.000 | Stable |
| ia3\_alpaca | IA³ | 500 | 74,880 | 1.359 | 500 | 1.359 | +0.000 | Stable |
| adalora\_alpaca | AdaLoRA | 500 | 922,560 | 1.332 | 500 | 1.332 | +0.000 | Stable |
| lora\_r16\_alpaca | LoRA (attn) | 500 | 921,600 | 1.285 | 500 | 1.285 | +0.000 | Stable |
| lora\_r4\_alpaca | LoRA (attn) | 500 | 230,400 | 1.292 | 500 | 1.292 | +0.000 | Stable |

### 2.3 Three Clear Tiers of Overfitting Risk

**Tier 1 — Catastrophic (gap > 0.5)**: lora\_r16\_mlp (both datasets), lora\_r32\_all\_code
- Eval loss at the end is 47–97% above the minimum
- Best checkpoint is very early (step 100–200, < 2 epochs)
- Training loss approaches 0.09–0.10 (near-perfect memorization)

**Tier 2 — Moderate (gap 0.1–0.5)**: lora\_r32\_all\_alpaca, lora\_r16\_code, full\_ft\_code, dora\_r8 (both)
- Eval loss rises 10–25% above minimum
- Best checkpoint in the first 300–500 steps
- Training loss is low but not zero

**Tier 3 — Stable (gap < 0.05)**: lora\_r4 (both), lora\_r16\_alpaca, ia3 (both), adalora (both), full\_ft\_alpaca
- Eval loss either monotonically decreases or plateaus
- Best checkpoint is at or near the final step
- These are safe to deploy as-is

---

## 3. Side-by-Side Eval Loss Trajectories

### 3.1 Alpaca Dataset (first 500 steps)

```
 Step    lora_r4    lora_r16  lora_r32_all  lora_r16_mlp   dora_r8      ia3    adalora    full_ft
-------------------------------------------------------------------------------------------------
   50     1.4845      1.3453       1.2900          --        --       2.0330    2.8040     1.3347
  100     1.3345      1.3061       1.2738        1.2724    1.3130     1.7685    2.2507     1.2916
  150     1.3157      1.2965       1.2815          --        --       1.5808    1.7739     1.2854
  200     1.3049      1.2890       1.2785        1.2705    1.2917     1.4624    1.4684     1.2768
  250     1.2995      1.2870       1.2795          --        --       1.4106    1.3858     1.2716
  300     1.2987      1.2913       1.3488  ←div    1.3309    1.2935     1.3846    1.3575     1.2728
  350     1.2952      1.2858       1.3515          --        --       1.3705    1.3447     1.2712
  400     1.2928      1.2854       1.4348        1.3951    1.2859     1.3631    1.3365     1.2722
  450     1.2936      1.2874       1.4450          --        --       1.3597    1.3332     1.2726
  500     1.2924      1.2850       1.4411        1.4349    1.2879     1.3585    1.3317     1.2727
```

**Observations**:
- **lora\_r4, lora\_r16, full\_ft, adalora**: Eval loss decreases or plateaus throughout. Safe.
- **ia3**: Starts high (2.03), converges slowly, never overfits. Stable.
- **lora\_r32\_all**: Best at step 100 (1.274), then climbs steadily to 1.441. The divergence begins at step 300 (epoch 2.4).
- **lora\_r16\_mlp**: Best at step 200 (1.270), then climbs sharply. By step 500 it's already at 1.435 and still rising (it will reach 2.498 by step 2000).
- **dora\_r8**: Slight upward drift after step 400, but mild.

### 3.2 Code Instructions Dataset (full 2000 steps)

```
 Step    lora_r4    lora_r16  lora_r32_all  lora_r16_mlp   dora_r8      ia3    adalora    full_ft
-------------------------------------------------------------------------------------------------
  100     0.9525      0.9302       0.8886        0.8966    0.9396     1.0567    1.2917     0.9157
  200     0.9320      0.9189       0.9030        0.9022    0.9259     0.9900    1.0032     0.8970
  300     0.9141      0.9059       0.9429        0.9191    0.9097     0.9674    0.9617     0.8902
  400     0.9129      0.9145  ←    1.0223        0.9731    0.9125     0.9555    0.9495     0.8944
  500     0.9067      0.9081  ←    1.0293        0.9578    0.9049     0.9467    0.9391     0.8899
  700     0.9046      0.9300       1.2154        1.1227    0.9117     0.9329    0.9267     0.9171
 1000     0.9121      0.9746       1.3586        1.3168    0.9312     0.9245    0.9203     0.9618
 1500     0.9351      1.0837       1.5806        1.6147    0.9902     0.9193    0.9169     1.0521
 2000     0.9458      1.1526       1.6717        1.7115    1.0175     0.9182    0.9168     1.0975
```

**Observations**:
- **lora\_r32\_all and lora\_r16\_mlp**: Eval loss starts rising almost immediately (by step 300–400). By step 2000, eval loss has nearly doubled from the minimum. This is severe overfitting.
- **lora\_r16**: Overfits moderately. Best at step 300 (0.906), rises to 1.153 by step 2000.
- **full\_ft**: Best at step 500 (0.890), then climbs to 1.098. The 16-epoch schedule is too long despite the low LR.
- **lora\_r4, ia3, adalora**: Remarkably stable. lora\_r4 shows minimal drift (+0.04). ia3 and adalora actually reach their best at the final step.
- **dora\_r8**: Mild overfitting. Best at step 500, rises by +0.11.

### 3.3 The Train→Eval Gap: How It Grows

The gap between training loss and eval loss is the direct measure of memorization vs. generalization. For the most problematic runs, this gap grows to extreme levels:

| Run | Step 100 Gap | Step 500 Gap | Step 1000 Gap | Step 2000 Gap |
|-----|-------------|-------------|--------------|--------------|
| lora\_r16\_mlp\_alpaca | +0.032 | +0.615 | +1.702 | +2.405 |
| lora\_r16\_mlp\_code | +0.122 | +0.457 | +1.112 | +1.614 |
| lora\_r32\_all\_code | +0.105 | +0.617 | +1.196 | +1.586 |
| lora\_r32\_all\_alpaca | −0.052 | +0.759 | — | — |
| full\_ft\_code | +0.121 | +0.281 | +0.590 | +0.775 |
| lora\_r16\_code | +0.123 | +0.206 | +0.503 | +0.732 |
| lora\_r4\_code | +0.121 | +0.141 | +0.353 | +0.270 |
| ia3\_code | +0.125 | +0.133 | +0.302 | +0.126 |

A gap above ~0.3 indicates meaningful divergence. The catastrophic runs reach gaps of 1.5–2.4, meaning the model's performance on held-out data is dramatically worse than what training loss suggests.

---

## 4. Why Training Loss Looks Fine But Performance Doesn't Follow

### 4.1 The Mechanism: Memorization Capacity

With only 500 training samples and batch size 4, each epoch is 125 steps. At 500 steps the model sees each sample 4 times; at 2000 steps it sees each sample 16 times. High-capacity adapters have enough parameters to memorize the training set:

- **lora\_r32\_all**: 9.77M trainable params for 500 samples → ~19,500 params per training sample
- **lora\_r16\_mlp**: 3.04M trainable params → ~6,080 params per training sample
- **lora\_r4**: 230K trainable params → ~460 params per sample (still enough to memorize, but slower)

Training loss reflects how well the model fits the training distribution. Once the adapter has enough capacity, it can drive training loss toward zero by memorizing specific input→output mappings without learning generalizable patterns. This is why training loss is **not a reliable signal** for model quality — it measures in-distribution fit, not generalization.

### 4.2 Why Higher-Capacity Adapters Are More Prone

The PEFT source code reveals the mechanism. For LoRA ([`lora/layer.py:978`](../peft/src/peft/tuners/lora/layer.py)):

```python
result = result + lora_B(lora_A(dropout(x))) * scaling
```

The update ΔW = scaling × B @ A, where scaling = alpha/r. The effective rank of the update is r. Higher r means:
1. More directions in which the weight matrix can be modified
2. More capacity to fit idiosyncratic training patterns
3. Faster memorization (fewer epochs needed to drive train loss to zero)

For lora\_r32\_all with r=32 across all 7 module types, the total update space is enormous: 9.77M parameters can represent a delta that perfectly fits 500 examples while degrading the base model's general capabilities.

### 4.3 Why MLP-Only Targeting Is Especially Dangerous

The lora\_r16\_mlp config targets only `gate_proj`, `up_proj`, and `down_proj` — the feedforward network modules. This is particularly problematic because:

1. **MLP modules are the largest weight matrices** in the transformer (e.g., gate\_proj is 576×1536 vs q\_proj at 576×576), giving the adapter more raw capacity per module.
2. **MLP layers store factual knowledge and feature transformations**. Modifying only MLP layers means the adapter can't distribute changes across attention (which controls information routing) and MLP (which controls feature transformations). All learning pressure is concentrated in the MLP, which appears more prone to destructive memorization.
3. **The adapter weight norms confirm this**: lora\_r16\_mlp has the highest mean B-matrix norm (3.04) of any LoRA config, indicating large weight updates relative to the base model.

### 4.4 Why IA³ and AdaLoRA Are Stable

**IA³** ([`ia3/layer.py:175`](../peft/src/peft/tuners/ia3/layer.py)):
```python
ia3_scaling *= self.ia3_l[active_adapter].flatten()
# Either: x = x * ia3_scaling (feedforward) or: result = result * ia3_scaling (attention)
```

IA³ learns only a **per-channel scaling vector** — not a low-rank weight delta. With only 74,880 total parameters (0.06% of the model), it has fundamentally limited capacity to memorize. The scaling operation preserves the base model's representational structure, just reweighting existing features. This makes IA³ almost immune to overfitting on small datasets, at the cost of slower convergence and lower peak performance.

**AdaLoRA** ([`adalora/layer.py:195`](../peft/src/peft/tuners/adalora/layer.py)):
```python
result += (dropout(x) @ (lora_A * lora_E).T @ lora_B.T) * scaling / ranknum
```

AdaLoRA uses **importance-based rank allocation** — it starts with init\_r=16 and prunes to target\_r=8 during training, guided by an importance score. This built-in capacity reduction acts as a regularizer: the adapter literally shrinks its own capacity as training progresses, which prevents the uncontrolled parameter growth that drives overfitting. The config shows `tinit=0, tfinal=0, deltaT=1, total_step=500/2000`, meaning rank pruning happens continuously throughout training.

### 4.5 Why DoRA Shows Mild (Not Severe) Overfitting

DoRA ([`lora/dora.py:153-165`](../peft/src/peft/tuners/lora/dora.py)):
```python
mag_norm_scale = (magnitude / weight_norm).view(1, -1)
result_dora = (mag_norm_scale - 1) * base_result + mag_norm_scale * lora_result * scaling
```

DoRA decomposes the weight update into a **magnitude vector** and a **direction matrix**. The magnitude is normalized against the combined base+adapter weight norm (detached from gradients per Section 4.3 of the DoRA paper). This normalization provides implicit regularization: the adapter can't simply scale up its updates indefinitely, and the direction component is constrained by the base weight's geometry. This explains why dora\_r8 (483K params, same target modules as lora\_r4/r16) overfits less than vanilla LoRA at comparable or higher rank — the magnitude/direction decomposition acts as a brake on memorization.

### 4.6 Why full\_ft Overfits on code\_instructions but Not alpaca

Full fine-tuning uses lr=1e-5 (50x lower than PEFT adapters). On alpaca (500 steps, 4 epochs), this is conservative enough that the model barely overfits (gap +0.002). On code\_instructions (2000 steps, 16 epochs), the extended training schedule overwhelms the low learning rate — by step 500 the model has already found its best generalization point, and the remaining 1500 steps of training drive it into overfitting (final gap +0.208). The lesson: **low learning rate is not a substitute for early stopping** when training for too many epochs.

---

## 5. Downstream Benchmark Performance

The lm-evaluation-harness benchmarks were run on the **final checkpoints** (not the best-eval-loss checkpoints). This means the benchmark scores reflect the overfit state, not the peak generalization:

| Run | Overfit Gap | ARC-Easy | HellaSwag | PIQA | Winogrande | BoolQ | Avg Acc |
|-----|------------|----------|-----------|------|------------|-------|---------|
| lora\_r4\_alpaca | 0.000 | 0.590 | 0.430 | 0.665 | 0.515 | 0.625 | **0.565** |
| lora\_r16\_alpaca | 0.000 | 0.585 | 0.430 | 0.665 | 0.485 | 0.630 | **0.559** |
| dora\_r8\_alpaca | +0.098 | 0.535 | 0.450 | 0.680 | 0.485 | 0.635 | 0.557 |
| lora\_r32\_all\_alpaca | +0.167 | 0.510 | 0.450 | 0.665 | 0.540 | 0.610 | 0.555 |
| adalora\_alpaca | 0.000 | 0.585 | 0.435 | 0.655 | 0.475 | 0.620 | 0.554 |
| ia3\_alpaca | 0.000 | 0.600 | 0.430 | 0.650 | 0.485 | 0.605 | 0.554 |
| lora\_r16\_mlp\_alpaca | +1.228 | 0.430 | 0.400 | 0.625 | 0.505 | 0.595 | **0.511** |
| lora\_r4\_code | +0.041 | 0.540 | 0.435 | 0.645 | 0.475 | 0.610 | 0.541 |
| adalora\_code | +0.001 | 0.580 | 0.450 | 0.645 | 0.500 | 0.625 | **0.560** |
| ia3\_code | 0.000 | 0.580 | 0.445 | 0.635 | 0.480 | 0.640 | 0.556 |
| lora\_r32\_all\_code | +0.783 | 0.490 | 0.440 | 0.650 | 0.510 | 0.630 | 0.544 |
| lora\_r16\_mlp\_code | +0.815 | 0.525 | 0.450 | 0.620 | 0.530 | 0.610 | 0.547 |
| dora\_r8\_code | +0.113 | 0.510 | 0.440 | 0.650 | 0.495 | 0.605 | 0.540 |
| lora\_r16\_code | +0.247 | 0.485 | 0.440 | 0.635 | 0.490 | 0.600 | 0.530 |

**Key observations**:
1. **lora\_r16\_mlp\_alpaca** has the worst average benchmark accuracy (0.511) — directly reflecting its catastrophic overfitting (gap +1.228). ARC-Easy dropped to 0.430 from ~0.585 for stable runs.
2. **lora\_r32\_all\_alpaca** (the run that triggered this investigation) scores 0.555 avg — decent but not the best. Its ARC-Easy accuracy (0.510) is well below the stable lora\_r4 (0.590) and lora\_r16 (0.585), confirming that overfitting hurts downstream reasoning.
3. **The best-performing runs are the stable ones**: lora\_r4\_alpaca (0.565), lora\_r16\_alpaca (0.559), adalora\_code (0.560). These runs didn't overfit, so their final checkpoint is also their best checkpoint.
4. **Overfit runs would likely score higher if evaluated at their best checkpoint**. Since no per-checkpoint benchmark evaluations were saved, we can't confirm this directly, but the eval\_loss trajectory strongly suggests it.

---

## 6. Grad Norm: An Unreliable Early Warning Signal

Gradient norms were examined as a potential early indicator of overfitting:

| Run | Grad Norm (early 25%) | Grad Norm (late 25%) | Ratio (late/early) |
|-----|----------------------|---------------------|-------------------|
| lora\_r16\_mlp\_alpaca | 0.458 | 0.331 | 0.72 |
| lora\_r32\_all\_code | 0.484 | 0.217 | 0.45 |
| lora\_r32\_all\_alpaca | 0.493 | 0.610 | 1.24 |
| lora\_r16\_code | 0.445 | 0.780 | 1.75 |
| dora\_r8\_alpaca | 0.469 | 0.774 | 1.65 |
| ia3\_code | 0.300 | 0.288 | 0.96 |
| adalora\_code | 0.205 | 0.296 | 1.44 |
| lora\_r4\_alpaca | 0.453 | 0.434 | 0.96 |

**Grad norm is not a reliable overfitting signal.** The worst overfitter (lora\_r16\_mlp) has a *decreasing* grad norm ratio (0.72) — the model has converged on the training set and gradients are small, but it's destructively overfitting. Meanwhile, some stable runs (adalora\_code) show increasing grad norms (1.44). The grad norm reflects training dynamics (how far the model is from the training loss minimum), not generalization.

**The only reliable early warning is the eval\_loss trajectory itself.** Specifically, the point where eval\_loss stops decreasing and begins to rise — this is the "turning point" visible in the checkpoint eval data.

---

## 7. Adapter Weight Norm Analysis

The final adapter weight norms (Frobenius norm of the B matrices, which control the magnitude of the weight update) provide insight into why certain configs overfit:

| Run | B-norm Mean | B-norm Max | Overfit Gap |
|-----|------------|-----------|-------------|
| lora\_r4\_alpaca | 0.69 | 1.04 | 0.000 |
| lora\_r16\_alpaca | 0.89 | 1.37 | 0.000 |
| lora\_r32\_all\_alpaca | 1.24 | 2.31 | +0.167 |
| lora\_r16\_mlp\_alpaca | **3.04** | **4.19** | **+1.228** |
| lora\_r4\_code | 1.19 | 2.04 | +0.041 |
| lora\_r16\_code | 1.97 | 3.28 | +0.247 |
| lora\_r32\_all\_code | 2.13 | 4.22 | +0.783 |
| lora\_r16\_mlp\_code | **2.62** | 3.53 | **+0.815** |

There is a clear correlation: **higher B-matrix norms correspond to larger overfit gaps**. The lora\_r16\_mlp runs have the highest B-norms (3.04 and 2.62 mean) and the worst overfitting. This makes sense: the B matrix is initialized to zero and grows during training. Large B-norms mean the adapter has made large modifications to the base model's weights, increasing the risk of destructive interference with pre-trained capabilities.

The per-module breakdown for lora\_r32\_all\_alpaca shows that MLP modules (gate\_proj, up\_proj) consistently have the highest B-norms (~1.8–2.3), while attention value projection (v\_proj) has the lowest (~0.44–0.49). This confirms that MLP-targeting concentrates the largest weight changes in the most knowledge-sensitive layers.

---

## 8. Checkpoint Recommendations

### 8.1 Runs Where You Should Deploy an Early Checkpoint

For overfitting runs, the best checkpoint (by eval loss) is much earlier than the final one:

| Run | Best Checkpoint | Best Eval Loss | Final Eval Loss | Improvement |
|-----|----------------|---------------|----------------|-------------|
| lora\_r16\_mlp\_alpaca | **checkpoint-200** | 1.270 | 2.498 | 49% better |
| lora\_r16\_mlp\_code | **checkpoint-100** | 0.897 | 1.711 | 48% better |
| lora\_r32\_all\_code | **checkpoint-100** | 0.889 | 1.672 | 47% better |
| lora\_r32\_all\_alpaca | **checkpoint-100** | 1.274 | 1.441 | 12% better |
| lora\_r16\_code | **checkpoint-300** | 0.906 | 1.153 | 21% better |
| full\_ft\_code | **checkpoint-500** | 0.890 | 1.098 | 19% better |
| dora\_r8\_alpaca | **checkpoint-400** | 1.286 | 1.384 | 7% better |
| dora\_r8\_code | **checkpoint-500** | 0.905 | 1.018 | 11% better |

### 8.2 Runs Where the Final Checkpoint Is Fine

These runs never overfit — the final checkpoint is also the best:

| Run | Best = Final Step | Eval Loss |
|-----|------------------|-----------|
| lora\_r4\_alpaca | 500 | 1.292 |
| lora\_r16\_alpaca | 500 | 1.285 |
| ia3\_alpaca | 500 | 1.359 |
| ia3\_code | 2000 | 0.918 |
| adalora\_alpaca | 500 | 1.332 |
| adalora\_code | ~1600 (gap only +0.001) | 0.917 |
| full\_ft\_alpaca | 500 | 1.273 |
| lora\_r4\_code | ~700 (gap only +0.041) | 0.946 |

### 8.3 Deployment Recommendation Summary

**Best overall performers (by avg benchmark accuracy at current final checkpoint):**
1. lora\_r4\_alpaca — 0.565 avg, stable, deploy final (checkpoint-500)
2. lora\_r16\_alpaca — 0.559 avg, stable, deploy final (checkpoint-500)
3. adalora\_code — 0.560 avg, stable, deploy final (checkpoint-2000)

**Runs that would benefit most from checkpoint rollback:**
1. lora\_r16\_mlp (both datasets) — deploy checkpoint-100/200 instead of final
2. lora\_r32\_all\_code — deploy checkpoint-100 instead of final
3. lora\_r16\_code — deploy checkpoint-300 instead of final

**Runs to reconsider entirely:**
- lora\_r16\_mlp: Even at its best checkpoint, the MLP-only targeting strategy underperforms attention-targeting configs. Consider switching to q\_proj/v\_proj targeting.
- lora\_r32\_all: The high capacity (r=32, all modules) provides no benefit over lora\_r16 (q/v only) while being more prone to overfitting. The extra parameters are a liability on this dataset size.

---

## 9. Root Causes and Recommendations

### 9.1 Root Causes

1. **No early stopping or best-checkpoint tracking**: All `trainer_state.json` files show `best_model_checkpoint: null` and `best_metric: null`. The HuggingFace Trainer was not configured with `load_best_model_at_end=True` or `save_total_limit`. Every run deployed its final checkpoint regardless of eval loss trajectory.

2. **Excessive training duration for small datasets**: 500 training samples × 16 epochs = 8,000 sample exposures. High-capacity adapters can memorize this in 1–2 epochs; the remaining 14 epochs are pure overfitting.

3. **Uniform learning rate across adapter capacities**: All PEFT runs use lr=5e-4 regardless of adapter size. A 9.77M-parameter lora\_r32\_all adapter at lr=5e-4 makes much larger updates per step than a 230K lora\_r4 adapter at the same LR, leading to faster memorization.

4. **Module targeting strategy**: Targeting MLP-only or all-linear modules concentrates updates in the most sensitive parts of the model. Attention-only targeting (q\_proj, v\_proj) is more stable because attention modules primarily route information rather than store it.

### 9.2 Recommendations

1. **Enable early stopping immediately**: Set `load_best_model_at_end=True`, `metric_for_best_model="eval_loss"`, and `save_total_limit=3` in TrainingArguments. This is the single highest-impact fix.

2. **Reduce training steps for small datasets**: For 500 training samples, 250–500 steps (2–4 epochs) is sufficient for stable adapters. Cap at 500 steps unless you have >5K training samples.

3. **Scale learning rate by adapter capacity**: Consider reducing LR for high-capacity adapters. lora\_r32\_all at lr=2e-4 or lora\_r16\_mlp at lr=1e-4 would likely overfit less. Alternatively, use rank-stabilized LoRA (`use_rslora=True`) which changes scaling to `alpha/sqrt(r)`, providing implicit regularization at higher ranks.

4. **Prefer attention-only targeting**: The q\_proj/v\_proj targeting pattern (used by lora\_r4, lora\_r16, dora\_r8, adalora) is consistently more stable than MLP-only or all-linear targeting. Only add MLP modules if you have a large dataset (>10K samples).

5. **Use IA³ or AdaLoRA for very small datasets**: If working with <1K samples, IA³ and AdaLoRA are the most overfit-resistant options. IA³ trades peak performance for stability; AdaLoRA's rank pruning provides a good balance.

6. **Re-run benchmarks on best checkpoints**: The current benchmark scores reflect the overfit state. Re-evaluating the recommended early checkpoints would likely show 2–5 point improvements on ARC-Easy and similar benchmarks for the overfitting runs.

---

## 10. Methodology and Data Sources

This analysis was conducted using:
- **Training curves**: `training_curves_comparison.parquet` (4,576 rows for 16 SmolLM2 runs, filtered from the combined file that also contains Qwen3 experiments)
- **Cross-adapter summary**: `cross_adapter_comparison.parquet` (final train loss, param counts, timing)
- **Eval results**: `eval_results_comparison.parquet` (5 benchmarks × 16 SmolLM2 runs)
- **Per-run training logs**: `runs/*/training_log.csv` (step-by-step loss, eval\_loss, LR, grad\_norm)
- **Checkpoint trainer states**: `runs/*/checkpoints/checkpoint-*/trainer_state.json` (full log history at each checkpoint)
- **Adapter configs**: `runs/*/adapter_config.json` (PEFT type, rank, alpha, target modules, dropout)
- **Adapter weight stats**: `runs/*/adapter_weight_stats.json` (per-matrix shape, mean, std, norm)
- **PEFT source code**: `/home/ubuntu/workspace/peft/src/peft/tuners/` (lora, ia3, adalora, dora implementations)
- **Dataset metadata**: `datasets/*/metadata.json` (sample counts, sources)

All Qwen3 runs and evaluations were excluded per instructions. Only the 16 SmolLM2-135M runs (8 adapters × 2 datasets) were analyzed.

```

_wrote 29400 bytes to /home/ubuntu/workspace/REPORT.md_

### Step 84: bash

```bash
wc -l /home/ubuntu/workspace/REPORT.md && echo "---" && head -5 /home/ubuntu/workspace/REPORT.md && echo "..." && tail -5 /home/ubuntu/workspace/REPORT.md
```

<details><summary>Output (1060 chars)</summary>

```
424 /home/ubuntu/workspace/REPORT.md
---
# SmolLM2-135M Adapter Training Sweep: Overfitting Trajectory Analysis

## Executive Summary

The SmolLM2-135M PEFT sweep trained 8 adapter configurations (lora\_r4, lora\_r16, lora\_r32\_all, lora\_r16\_mlp, ia3, adalora, dora\_r8, full\_ft) across 2 datasets (alpaca, code\_instructions), producing 16 runs. The central mystery — **lora\_r32\_all\_alpaca has the lowest final training loss (0.68) but the worst eval loss (1.44) and mediocre benchmark scores** — is explained by classic overfitting that is invisible in the final training loss but unmistakable in the eval\_loss trajectory.
...
- **Adapter weight stats**: `runs/*/adapter_weight_stats.json` (per-matrix shape, mean, std, norm)
- **PEFT source code**: `/home/ubuntu/workspace/peft/src/peft/tuners/` (lora, ia3, adalora, dora implementations)
- **Dataset metadata**: `datasets/*/metadata.json` (sample counts, sources)

All Qwen3 runs and evaluations were excluded per instructions. Only the 16 SmolLM2-135M runs (8 adapters × 2 datasets) were analyzed.
```
</details>
