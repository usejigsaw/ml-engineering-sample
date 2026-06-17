# glm-5.1 on Checkpoint Progression Forensics

**Score:** 0.593
**Tool calls:** 95
**Duration:** 79.3 min
**Trace ID:** `bb8da7ff-ea72-4639-a139-dd40b96f4971`

---

## Trajectory

### Step 1: bash

```bash
find /home/ubuntu/workspace/training-export-proprietary/ -type f | head -80
```

<details><summary>Output (9461 chars)</summary>

```
/home/ubuntu/workspace/training-export-proprietary/generations/qwen3_dpo_b01_lora_r16_qwen3-0.6b/completions.jsonl
/home/ubuntu/workspace/training-export-proprietary/generations/qwen3_sft_lora_r16_qwen3-0.6b/completions.jsonl
/home/ubuntu/workspace/training-export-proprietary/generations/qwen3_sft_lora_r32_all_qwen3-0.6b/completions.jsonl
/home/ubuntu/workspace/training-export-proprietary/generations/qwen3_sft_lora_r8_qwen3-0.6b/completions.jsonl
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/adapter_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/adapter_weight_stats.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/memory_profile.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/training_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/training_log.csv
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/adapter_weights/README.md
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/adapter_weights/adapter_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-100/README.md
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-100/adapter_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-100/tokenizer.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-100/tokenizer_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-100/trainer_state.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-200/README.md
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-200/adapter_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-200/tokenizer.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-200/tokenizer_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-200/trainer_state.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-300/README.md
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-300/adapter_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-300/tokenizer.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-300/tokenizer_config.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-300/trainer_state.json
/home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/checkpoints/checkpoint-400/README.md
/home/ubuntu/workspace/trai

... (6461 chars truncated)
```
</details>

### Step 2: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/
```

<details><summary>Output (988 chars)</summary>

```
total 516
drwxr-xr-x.  6 ubuntu ubuntu   4096 Jun 15 03:10 .
drwxr-xr-x.  4 ubuntu ubuntu     66 Jun 15 03:10 ..
-rw-r--r--.  1 ubuntu ubuntu   7102 Jun 15 03:10 cross_adapter_comparison.parquet
drwxr-xr-x.  5 ubuntu ubuntu     60 Jun 15 03:10 datasets
-rw-r--r--.  1 ubuntu ubuntu   4422 Jun 15 03:10 eval_results_comparison.parquet
drwxr-xr-x. 37 ubuntu ubuntu   4096 Jun 15 03:10 evaluations
-rw-r--r--.  1 ubuntu ubuntu    355 Jun 15 03:10 experiment_metadata.json
-rw-r--r--.  1 ubuntu ubuntu   1369 Jun 15 03:10 experiment_metadata_v2.json
drwxr-xr-x.  6 ubuntu ubuntu    161 Jun 15 03:10 generations
-rw-r--r--.  1 ubuntu ubuntu  47752 Jun 15 03:10 qwen3_cross_run_comparison.csv
-rw-r--r--.  1 ubuntu ubuntu 158622 Jun 15 03:10 qwen3_cross_run_comparison.parquet
-rw-r--r--.  1 ubuntu ubuntu 190004 Jun 15 03:10 qwen3_training_curves.parquet
drwxr-xr-x. 35 ubuntu ubuntu   4096 Jun 15 03:10 runs
-rw-r--r--.  1 ubuntu ubuntu  88548 Jun 15 03:10 training_curves_comparison.parquet

```
</details>

### Step 3: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/runs/
```

<details><summary>Output (890 chars)</summary>

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

### Step 4: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/
```

<details><summary>Output (857 chars)</summary>

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

### Step 5: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/experiment_metadata.json
```

<details><summary>Output (355 chars)</summary>

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

### Step 6: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/experiment_metadata_v2.json
```

<details><summary>Output (1369 chars)</summary>

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

### Step 7: bash

```bash
for run in /home/ubuntu/workspace/training-export-proprietary/runs/*/; do
  name=$(basename "$run")
  has_csv=$(test -f "$run/training_log.csv" && echo "yes" || echo "no")
  checkpoints=$(ls -d "$run"/checkpoints/checkpoint-* 2>/dev/null | wc -l)
  echo "$name: csv=$has_csv checkpoints=$checkpoints"
done
```

<details><summary>Output (1667 chars)</summary>

```
adalora_alpaca: csv=yes checkpoints=5
adalora_code_instructions: csv=yes checkpoints=10
dora_r8_alpaca: csv=yes checkpoints=10
dora_r8_code_instructions: csv=yes checkpoints=10
full_ft_alpaca: csv=yes checkpoints=5
full_ft_code_instructions: csv=yes checkpoints=10
ia3_alpaca: csv=yes checkpoints=5
ia3_code_instructions: csv=yes checkpoints=10
lora_r16_alpaca: csv=yes checkpoints=5
lora_r16_code_instructions: csv=yes checkpoints=10
lora_r16_mlp_alpaca: csv=yes checkpoints=10
lora_r16_mlp_code_instructions: csv=yes checkpoints=10
lora_r32_all_alpaca: csv=yes checkpoints=5
lora_r32_all_code_instructions: csv=yes checkpoints=10
lora_r4_alpaca: csv=yes checkpoints=5
lora_r4_code_instructions: csv=yes checkpoints=10
qwen3_dpo_b01_lora_r16_qwen3-0.6b: csv=yes checkpoints=5
qwen3_dpo_b01_lora_r16_qwen3-1.7b: csv=yes checkpoints=5
qwen3_dpo_b01_lora_r32_all_qwen3-1.7b: csv=yes checkpoints=5
qwen3_dpo_b01_lora_r8_qwen3-1.7b: csv=yes checkpoints=5
qwen3_dpo_b05_lora_r16_qwen3-1.7b: csv=yes checkpoints=5
qwen3_dpo_b05_lora_r32_all_qwen3-1.7b: csv=yes checkpoints=5
qwen3_dpo_b05_lora_r8_qwen3-1.7b: csv=yes checkpoints=5
qwen3_kto_lora_r16_qwen3-1.7b: csv=yes checkpoints=5
qwen3_kto_lora_r8_qwen3-1.7b: csv=yes checkpoints=5
qwen3_sft_dora_r16_qwen3-1.7b: csv=yes checkpoints=10
qwen3_sft_full_ft_qwen3-1.7b: csv=yes checkpoints=10
qwen3_sft_lora_r16_qwen3-0.6b: csv=yes checkpoints=10
qwen3_sft_lora_r16_qwen3-1.7b: csv=yes checkpoints=10
qwen3_sft_lora_r32_all_qwen3-0.6b: csv=yes checkpoints=10
qwen3_sft_lora_r32_all_qwen3-1.7b: csv=yes checkpoints=10
qwen3_sft_lora_r8_qwen3-0.6b: csv=yes checkpoints=10
qwen3_sft_lora_r8_qwen3-1.7b: csv=yes checkpoints=10

```
</details>

### Step 8: bash

```bash
head -5 /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/training_log.csv
```

<details><summary>Output (288 chars)</summary>

```
step,loss,eval_loss,learning_rate,epoch,grad_norm
10,1.6788902282714844,,0.000491,0.08,0.7385956645011902
20,1.454610538482666,,0.000481,0.16,0.6349031925201416
30,1.3632939338684082,,0.000471,0.24,0.4665580689907074
40,1.3339543342590332,,0.00046100000000000004,0.32,0.48834550380706787

```
</details>

### Step 9: bash

```bash
head -5 /home/ubuntu/workspace/training-export-proprietary/runs/lora_r16_alpaca/training_log.csv
```

<details><summary>Output (286 chars)</summary>

```
step,loss,eval_loss,learning_rate,epoch,grad_norm
10,2.2299196243286135,,0.000491,0.08,0.7160831689834595
20,1.9618858337402343,,0.000481,0.16,0.739566445350647
30,1.610410499572754,,0.000471,0.24,0.5257897973060608
40,1.4328896522521972,,0.00046100000000000004,0.32,0.9020752906799316

```
</details>

### Step 10: bash

```bash
# Let's look at the full training log for lora_r32_all_alpaca (the r32 run the user is concerned about)
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/training_log.csv
```

<details><summary>Output (3594 chars)</summary>

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
420,0.6863453388214111,,8.1e-05,3.36,0.6

... (594 chars truncated)
```
</details>

### Step 11: bash

```bash
# Look at eval_loss entries across runs - how many have eval_loss values?
for run in /home/ubuntu/workspace/training-export-proprietary/runs/*/; do
  name=$(basename "$run")
  eval_count=$(awk -F',' 'NR>1 && $3!="" {count++} END{print count+0}' "$run/training_log.csv")
  echo "$name: eval_loss_entries=$eval_count"
done
```

<details><summary>Output (1616 chars)</summary>

```
adalora_alpaca: eval_loss_entries=10
adalora_code_instructions: eval_loss_entries=20
dora_r8_alpaca: eval_loss_entries=20
dora_r8_code_instructions: eval_loss_entries=20
full_ft_alpaca: eval_loss_entries=10
full_ft_code_instructions: eval_loss_entries=20
ia3_alpaca: eval_loss_entries=10
ia3_code_instructions: eval_loss_entries=20
lora_r16_alpaca: eval_loss_entries=10
lora_r16_code_instructions: eval_loss_entries=20
lora_r16_mlp_alpaca: eval_loss_entries=20
lora_r16_mlp_code_instructions: eval_loss_entries=20
lora_r32_all_alpaca: eval_loss_entries=10
lora_r32_all_code_instructions: eval_loss_entries=20
lora_r4_alpaca: eval_loss_entries=10
lora_r4_code_instructions: eval_loss_entries=20
qwen3_dpo_b01_lora_r16_qwen3-0.6b: eval_loss_entries=10
qwen3_dpo_b01_lora_r16_qwen3-1.7b: eval_loss_entries=10
qwen3_dpo_b01_lora_r32_all_qwen3-1.7b: eval_loss_entries=10
qwen3_dpo_b01_lora_r8_qwen3-1.7b: eval_loss_entries=10
qwen3_dpo_b05_lora_r16_qwen3-1.7b: eval_loss_entries=10
qwen3_dpo_b05_lora_r32_all_qwen3-1.7b: eval_loss_entries=10
qwen3_dpo_b05_lora_r8_qwen3-1.7b: eval_loss_entries=10
qwen3_kto_lora_r16_qwen3-1.7b: eval_loss_entries=10
qwen3_kto_lora_r8_qwen3-1.7b: eval_loss_entries=10
qwen3_sft_dora_r16_qwen3-1.7b: eval_loss_entries=20
qwen3_sft_full_ft_qwen3-1.7b: eval_loss_entries=20
qwen3_sft_lora_r16_qwen3-0.6b: eval_loss_entries=20
qwen3_sft_lora_r16_qwen3-1.7b: eval_loss_entries=20
qwen3_sft_lora_r32_all_qwen3-0.6b: eval_loss_entries=20
qwen3_sft_lora_r32_all_qwen3-1.7b: eval_loss_entries=20
qwen3_sft_lora_r8_qwen3-0.6b: eval_loss_entries=20
qwen3_sft_lora_r8_qwen3-1.7b: eval_loss_entries=20

```
</details>

### Step 12: bash

```bash
# Check checkpoint trainer_state.json for eval metrics
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/checkpoints/checkpoint-500/trainer_state.json | python3 -m json.tool | head -60
```

<details><summary>Output (1697 chars)</summary>

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

```
</details>

### Step 13: bash

```bash
# Extract eval_loss trajectory for the key runs we want to compare
# Let's first understand the v1 runs (alpaca/code_instructions) better
python3 << 'PYEOF'
import csv
import json
import os

base = "/home/ubuntu/workspace/training-export-proprietary/runs"

# V1 runs (SmolLM2-135M) - pick the most interesting ones for comparison
v1_runs = [
    "lora_r4_alpaca",
    "lora_r16_alpaca", 
    "lora_r32_all_alpaca",
    "ia3_alpaca",
    "adalora_alpaca",
    "dora_r8_alpaca",
    "lora_r16_mlp_alpaca",
    "full_ft_alpaca",
]

print("=== V1 (SmolLM2-135M) Eval Loss Trajectories ===")
for run_name in v1_runs:
    csv_path = f"{base}/{run_name}/training_log.csv"
    if not os.path.exists(csv_path):
        continue
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        eval_points = []
        for row in reader:
            if row.get('eval_loss') and row['eval_loss'].strip():
                step = int(row['step'])
                eval_loss = float(row['eval_loss'])
                train_loss = float(row['loss'])
                eval_points.append((step, train_loss, eval_loss))
    print(f"\n{run_name}:")
    print(f"  Step | Train Loss | Eval Loss | Gap")
    for step, tl, el in eval_points:
        gap = el - tl
        print(f"  {step:4d} | {tl:.4f}    | {el:.4f}   | {gap:+.4f}")
PYEOF
```

<details><summary>Output (4496 chars)</summary>

```
=== V1 (SmolLM2-135M) Eval Loss Trajectories ===

lora_r4_alpaca:
  Step | Train Loss | Eval Loss | Gap
    50 | 1.4845    | 1.4845   | +0.0000
   100 | 1.3345    | 1.3345   | +0.0000
   150 | 1.3157    | 1.3157   | +0.0000
   200 | 1.3049    | 1.3049   | +0.0000
   250 | 1.2995    | 1.2995   | +0.0000
   300 | 1.2987    | 1.2987   | +0.0000
   350 | 1.2952    | 1.2952   | +0.0000
   400 | 1.2928    | 1.2928   | +0.0000
   450 | 1.2936    | 1.2936   | +0.0000
   500 | 1.2924    | 1.2924   | +0.0000

lora_r16_alpaca:
  Step | Train Loss | Eval Loss | Gap
    50 | 1.3453    | 1.3453   | +0.0000
   100 | 1.3061    | 1.3061   | +0.0000
   150 | 1.2965    | 1.2965   | +0.0000
   200 | 1.2890    | 1.2890   | +0.0000
   250 | 1.2870    | 1.2870   | +0.0000
   300 | 1.2913    | 1.2913   | +0.0000
   350 | 1.2858    | 1.2858   | +0.0000
   400 | 1.2854    | 1.2854   | +0.0000
   450 | 1.2874    | 1.2874   | +0.0000
   500 | 1.2850    | 1.2850   | +0.0000

lora_r32_all_alpaca:
  Step | Train Loss | Eval Loss | Gap
    50 | 1.2900    | 1.2900   | +0.0000
   100 | 1.2738    | 1.2738   | +0.0000
   150 | 1.2815    | 1.2815   | +0.0000
   200 | 1.2785    | 1.2785   | +0.0000
   250 | 1.2795    | 1.2795   | +0.0000
   300 | 1.3488    | 1.3488   | +0.0000
   350 | 1.3515    | 1.3515   | +0.0000
   400 | 1.4348    | 1.4348   | +0.0000
   450 | 1.4450    | 1.4450   | +0.0000
   500 | 1.4411    | 1.4411   | +0.0000

ia3_alpaca:
  Step | Train Loss | Eval Loss | Gap
    50 | 2.0330    | 2.0330   | +0.0000
   100 | 1.7685    | 1.7685   | +0.0000
   150 | 1.5808    | 1.5808   | +0.0000
   200 | 1.4624    | 1.4624   | +0.0000
   250 | 1.4106    | 1.4106   | +0.0000
   300 | 1.3846    | 1.3846   | +0.0000
   350 | 1.3705    | 1.3705   | +0.0000
   400 | 1.3631    | 1.3631   | +0.0000
   450 | 1.3597    | 1.3597   | +0.0000
   500 | 1.3585    | 1.3585   | +0.0000

adalora_alpaca:
  Step | Train Loss | Eval Loss | Gap
    50 | 2.8040    | 2.8040   | +0.0000
   100 | 2.2507    | 2.2507   | +0.0000
   150 | 1.7739    | 1.7739   | +0.0000
   200 | 1.4684    | 1.4684   | +0.0000
   250 | 1.3858    | 1.3858   | +0.0000
   300 | 1.3575    | 1.3575   | +0.0000
   350 | 1.3447    | 1.3447   | +0.0000
   400 | 1.3365    | 1.3365   | +0.0000
   450 | 1.3332    | 1.3332   | +0.0000
   500 | 1.3317    | 1.3317   | +0.0000

dora_r8_alpaca:
  Step | Train Loss | Eval Loss | Gap
   100 | 1.3130    | 1.3130   | +0.0000
   200 | 1.2917    | 1.2917   | +0.0000
   300 | 1.2935    | 1.2935   | +0.0000
   400 | 1.2859    | 1.2859   | +0.0000
   500 | 1.2879    | 1.2879   | +0.0000
   600 | 1.2930    | 1.2930   | +0.0000
   700 | 1.3044    | 1.3044   | +0.0000
   800 | 1.3034    | 1.3034   | +0.0000
   900 | 1.3168    | 1.3168   | +0.0000
  1000 | 1.3145    | 1.3145   | +0.0000
  1100 | 1.3238    | 1.3238   | +0.0000
  1200 | 1.3376    | 1.3376   | +0.0000
  1300 | 1.3478    | 1.3478   | +0.0000
  1400 | 1.3627    | 1.3627   | +0.0000
  1500 | 1.3510    | 1.3510   | +0.0000
  1600 | 1.3667    

... (1496 chars truncated)
```
</details>

### Step 14: bash

```bash
# The eval rows have both loss and eval_loss - the loss in those rows equals eval_loss (it's a duplicate)
# I need to properly separate training loss rows from eval rows
python3 << 'PYEOF'
import csv
import json
import os

base = "/home/ubuntu/workspace/training-export-proprietary/runs"

# Let's look at lora_r32_all_alpaca more carefully
csv_path = f"{base}/lora_r32_all_alpaca/training_log.csv"
with open(csv_path) as f:
    reader = csv.DictReader(f)
    for row in reader:
        step = int(row['step'])
        loss = row['loss']
        eval_loss = row['eval_loss']
        lr = row['learning_rate']
        grad = row['grad_norm']
        has_eval = bool(eval_loss and eval_loss.strip())
        if has_eval or step <= 60:
            print(f"Step {step:4d} | loss={loss:20s} | eval_loss={eval_loss:20s} | lr={lr:10s} | grad={grad}")
PYEOF
```

<details><summary>Output (1642 chars)</summary>

```
Step   10 | loss=1.6788902282714844   | eval_loss=                     | lr=0.000491   | grad=0.7385956645011902
Step   20 | loss=1.454610538482666    | eval_loss=                     | lr=0.000481   | grad=0.6349031925201416
Step   30 | loss=1.3632939338684082   | eval_loss=                     | lr=0.000471   | grad=0.4665580689907074
Step   40 | loss=1.3339543342590332   | eval_loss=                     | lr=0.00046100000000000004 | grad=0.48834550380706787
Step   50 | loss=1.2900101661682128   | eval_loss=                     | lr=0.000451   | grad=0.42039546370506287
Step   50 | loss=1.2900347709655762   | eval_loss=1.2900347709655762   | lr=           | grad=
Step   60 | loss=1.2384940147399903   | eval_loss=                     | lr=0.000441   | grad=0.4460912346839905
Step  100 | loss=1.2738009691238403   | eval_loss=1.2738009691238403   | lr=           | grad=
Step  150 | loss=1.2815436124801636   | eval_loss=1.2815436124801636   | lr=           | grad=
Step  200 | loss=1.278459906578064    | eval_loss=1.278459906578064    | lr=           | grad=
Step  250 | loss=1.2794697284698486   | eval_loss=1.2794697284698486   | lr=           | grad=
Step  300 | loss=1.3487833738327026   | eval_loss=1.3487833738327026   | lr=           | grad=
Step  350 | loss=1.3514587879180908   | eval_loss=1.3514587879180908   | lr=           | grad=
Step  400 | loss=1.4348132610321045   | eval_loss=1.4348132610321045   | lr=           | grad=
Step  450 | loss=1.4450159072875977   | eval_loss=1.4450159072875977   | lr=           | grad=
Step  500 | loss=1.4411063194274902   | eval_loss=1.4411063194274902   | lr=           | grad=

```
</details>

### Step 15: bash

```bash
# OK, so in eval rows, the "loss" field contains eval_loss and eval_loss is the same value.
# The training loss trajectory comes from the non-eval rows.
# Let me properly extract both training and eval trajectories for all runs.

python3 << 'PYEOF'
import csv
import json
import os

base = "/home/ubuntu/workspace/training-export-proprietary/runs"

def parse_run(run_name):
    csv_path = f"{base}/{run_name}/training_log.csv"
    train_points = []
    eval_points = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            has_eval = bool(row.get('eval_loss') and row['eval_loss'].strip())
            if has_eval:
                eval_points.append((step, float(row['eval_loss'])))
            else:
                train_points.append((step, float(row['loss']), float(row.get('grad_norm') or 0), float(row.get('learning_rate') or 0)))
    return train_points, eval_points

# Now let's look at the key v1 alpaca runs - training loss vs eval loss
v1_runs = [
    "lora_r4_alpaca",
    "lora_r16_alpaca", 
    "lora_r32_all_alpaca",
    "ia3_alpaca",
    "adalora_alpaca",
    "dora_r8_alpaca",
    "lora_r16_mlp_alpaca",
    "full_ft_alpaca",
]

print("=== V1 SmolLM2-135M + Alpaca: Training Loss at Eval Checkpoints ===\n")
for run_name in v1_runs:
    train_pts, eval_pts = parse_run(run_name)
    
    # Get last training loss (final step)
    final_train = train_pts[-1][1] if train_pts else None
    # Get last eval loss
    final_eval = eval_pts[-1][1] if eval_pts else None
    # Get min eval loss and its step
    min_eval = min(eval_pts, key=lambda x: x[1]) if eval_pts else None
    
    # Check if eval loss is increasing (overfitting)
    if len(eval_pts) >= 2:
        first_eval = eval_pts[0][1]
        last_eval = eval_pts[-1][1]
        eval_delta = last_eval - first_eval
    else:
        eval_delta = None
    
    # Check if eval loss has a U-shape (first decreases then increases)
    if len
```

<details><summary>Output (69 chars)</summary>

```
=== V1 SmolLM2-135M + Alpaca: Training Loss at Eval Checkpoints ===


```
</details>

### Step 16: bash

```bash
python3 << 'PYEOF'
import csv
import json
import os

base = "/home/ubuntu/workspace/training-export-proprietary/runs"

def parse_run(run_name):
    csv_path = f"{base}/{run_name}/training_log.csv"
    train_points = []
    eval_points = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            has_eval = bool(row.get('eval_loss') and row['eval_loss'].strip())
            if has_eval:
                eval_points.append((step, float(row['eval_loss'])))
            else:
                train_points.append((step, float(row['loss']), float(row.get('grad_norm') or 0), float(row.get('learning_rate') or 0)))
    return train_points, eval_points

v1_runs = [
    "lora_r4_alpaca",
    "lora_r16_alpaca", 
    "lora_r32_all_alpaca",
    "ia3_alpaca",
    "adalora_alpaca",
    "dora_r8_alpaca",
    "lora_r16_mlp_alpaca",
    "full_ft_alpaca",
]

for run_name in v1_runs:
    train_pts, eval_pts = parse_run(run_name)
    
    final_train = train_pts[-1][1] if train_pts else None
    final_eval = eval_pts[-1][1] if eval_pts else None
    
    if len(eval_pts) >= 3:
        min_step, min_val = min(eval_pts, key=lambda x: x[1])
        overshoot = eval_pts[-1][1] - min_val
    else:
        min_step = None
        min_val = None
        overshoot = None
    
    print(f"\n{run_name}:")
    print(f"  Final train loss: {final_train:.4f}")
    print(f"  Final eval loss:  {final_eval:.4f}")
    if min_val is not None:
        print(f"  Best eval loss:   {min_val:.4f} @ step {min_step}")
        print(f"  Eval overshoot:   {overshoot:.4f}")
    print(f"  Eval trajectory:  {' -> '.join(f'{el:.4f}' for _, el in eval_pts)}")
PYEOF
```

### Step 17: bash

```bash
python3 -c "
import csv, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
run_name = 'lora_r32_all_alpaca'
csv_path = os.path.join(base, run_name, 'training_log.csv')
with open(csv_path) as f:
    reader = csv.DictReader(f)
    for i, row in enumerate(reader):
        print(i, row)
" 2>&1 | head -60
```

<details><summary>Output (8922 chars)</summary>

```
0 {'step': '10', 'loss': '1.6788902282714844', 'eval_loss': '', 'learning_rate': '0.000491', 'epoch': '0.08', 'grad_norm': '0.7385956645011902'}
1 {'step': '20', 'loss': '1.454610538482666', 'eval_loss': '', 'learning_rate': '0.000481', 'epoch': '0.16', 'grad_norm': '0.6349031925201416'}
2 {'step': '30', 'loss': '1.3632939338684082', 'eval_loss': '', 'learning_rate': '0.000471', 'epoch': '0.24', 'grad_norm': '0.4665580689907074'}
3 {'step': '40', 'loss': '1.3339543342590332', 'eval_loss': '', 'learning_rate': '0.00046100000000000004', 'epoch': '0.32', 'grad_norm': '0.48834550380706787'}
4 {'step': '50', 'loss': '1.2900101661682128', 'eval_loss': '', 'learning_rate': '0.000451', 'epoch': '0.4', 'grad_norm': '0.42039546370506287'}
5 {'step': '50', 'loss': '1.2900347709655762', 'eval_loss': '1.2900347709655762', 'learning_rate': '', 'epoch': '0.4', 'grad_norm': ''}
6 {'step': '60', 'loss': '1.2384940147399903', 'eval_loss': '', 'learning_rate': '0.000441', 'epoch': '0.48', 'grad_norm': '0.4460912346839905'}
7 {'step': '70', 'loss': '1.3020501136779785', 'eval_loss': '', 'learning_rate': '0.000431', 'epoch': '0.56', 'grad_norm': '0.4370357394218445'}
8 {'step': '80', 'loss': '1.2247851371765137', 'eval_loss': '', 'learning_rate': '0.000421', 'epoch': '0.64', 'grad_norm': '0.41069552302360535'}
9 {'step': '90', 'loss': '1.2350358963012695', 'eval_loss': '', 'learning_rate': '0.00041099999999999996', 'epoch': '0.72', 'grad_norm': '0.43958938121795654'}
10 {'step': '100', 'loss': '1.3254374504089355', 'eval_loss': '', 'learning_rate': '0.00040100000000000004', 'epoch': '0.8', 'grad_norm': '0.476042240858078'}
11 {'step': '100', 'loss': '1.2738009691238403', 'eval_loss': '1.2738009691238403', 'learning_rate': '', 'epoch': '0.8', 'grad_norm': ''}
12 {'step': '110', 'loss': '1.3011079788208009', 'eval_loss': '', 'learning_rate': '0.000391', 'epoch': '0.88', 'grad_norm': '0.5789756774902344'}
13 {'step': '120', 'loss': '1.3478520393371582', 'eval_loss': '', 'learning_rate': '0.000381', 'epoch': '0.96', 'grad_norm': '0.3788187503814697'}
14 {'step': '130', 'loss': '1.1306018829345703', 'eval_loss': '', 'learning_rate': '0.000371', 'epoch': '1.04', 'grad_norm': '0.39384159445762634'}
15 {'step': '140', 'loss': '1.0384330749511719', 'eval_loss': '', 'learning_rate': '0.000361', 'epoch': '1.12', 'grad_norm': '0.4341002106666565'}
16 {'step': '150', 'loss': '1.0241544723510743', 'eval_loss': '', 'learning_rate': '0.00035099999999999997', 'epoch': '1.2', 'grad_norm': '0.4614233374595642'}
17 {'step': '150', 'loss': '1.2815436124801636', 'eval_loss': '1.2815436124801636', 'learning_rate': '', 'epoch': '1.2', 'grad_norm': ''}
18 {'step': '160', 'loss': '0.9399290084838867', 'eval_loss': '', 'learning_rate': '0.00034100000000000005', 'epoch': '1.28', 'grad_norm': '0.4648011326789856'}
19 {'step': '170', 'loss': '1.0596712112426758', 'eval_loss': '', 'learning_rate': '0.000331', 'epoch': '1.3599999999999999', 'grad_norm': '0.4287526309490204'}
20 {'step': '180', 'los

... (5922 chars truncated)
```
</details>

### Step 18: bash

```bash
# Now I see! The eval rows have the eval_loss in both the loss and eval_loss columns.
# The training loss is from the non-eval rows.
# Key finding: lora_r32_all_alpaca training loss drops from 1.68 to 0.68 but eval loss RISES from 1.29 to 1.44 - classic overfitting!
# Let me now do a comprehensive analysis across all runs.

python3 << 'PYEOF'
import csv, json, os

base = "/home/ubuntu/workspace/training-export-proprietary/runs"

def parse_run(run_name):
    csv_path = f"{base}/{run_name}/training_log.csv"
    train_points = []
    eval_points = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            has_eval = bool(row.get('eval_loss') and row['eval_loss'].strip())
            if has_eval:
                eval_points.append((step, float(row['eval_loss'])))
            else:
                train_points.append({
                    'step': step,
                    'loss': float(row['loss']),
                    'grad_norm': float(row.get('grad_norm') or 0),
                    'lr': float(row.get('learning_rate') or 0)
                })
    return train_points, eval_points

# Analyze all v1 alpaca runs
v1_alpaca = [
    "lora_r4_alpaca", "lora_r16_alpaca", "lora_r32_all_alpaca",
    "ia3_alpaca", "adalora_alpaca", "dora_r8_alpaca",
    "lora_r16_mlp_alpaca", "full_ft_alpaca"
]

v1_code = [
    "lora_r4_code_instructions", "lora_r16_code_instructions", "lora_r32_all_code_instructions",
    "ia3_code_instructions", "adalora_code_instructions", "dora_r8_code_instructions",
    "lora_r16_mlp_code_instructions", "full_ft_code_instructions"
]

print("=" * 100)
print("V1 SmolLM2-135M ALPACA: Training Loss vs Eval Loss Divergence")
print("=" * 100)

for run_name in v1_alpaca:
    train_pts, eval_pts = parse_run(run_name)
    if not eval_pts:
        continue
    
    # Get training loss at each eval step (approximate by finding nearest train step)
    train_at_eval = {}
    for tp in tra
```

<details><summary>Output (264 chars)</summary>

```
====================================================================================================
V1 SmolLM2-135M ALPACA: Training Loss vs Eval Loss Divergence
====================================================================================================

```
</details>

### Step 19: bash

```bash
python3 -u << 'PYEOF'
import csv, json, os

base = "/home/ubuntu/workspace/training-export-proprietary/runs"

def parse_run(run_name):
    csv_path = f"{base}/{run_name}/training_log.csv"
    train_points = []
    eval_points = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            has_eval = bool(row.get('eval_loss') and row['eval_loss'].strip())
            if has_eval:
                eval_points.append((step, float(row['eval_loss'])))
            else:
                train_points.append({
                    'step': step,
                    'loss': float(row['loss']),
                    'grad_norm': float(row.get('grad_norm') or 0),
                    'lr': float(row.get('learning_rate') or 0)
                })
    return train_points, eval_points

v1_alpaca = [
    "lora_r4_alpaca", "lora_r16_alpaca", "lora_r32_all_alpaca",
    "ia3_alpaca", "adalora_alpaca", "dora_r8_alpaca",
    "lora_r16_mlp_alpaca", "full_ft_alpaca"
]

for run_name in v1_alpaca:
    train_pts, eval_pts = parse_run(run_name)
    if not eval_pts:
        print(f"{run_name}: NO EVAL DATA")
        continue
    
    final_train = train_pts[-1]['loss']
    final_eval = eval_pts[-1][1]
    min_eval_step, min_eval_val = min(eval_pts, key=lambda x: x[1])
    
    # Find divergence point
    divergence_step = None
    for i in range(1, len(eval_pts)):
        if eval_pts[i][1] > eval_pts[i-1][1]:
            # Check if subsequent points continue rising
            rising = True
            for j in range(i+1, len(eval_pts)):
                if eval_pts[j][1] < eval_pts[i][1]:
                    rising = False
                    break
            if rising:
                divergence_step = eval_pts[i-1][0]
                break
    
    gap = final_eval - final_train
    overshoot = final_eval - min_eval_val
    
    print(f"\n{run_name}:")
    print(f"  Train: {train_pts[0]['loss']:.4f} -> {final_train:.4
```

### Step 20: bash

```bash
python3 << 'PYEOF'
import csv, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '')
            if ev and ev.strip():
                eval_pts.append((step, float(ev)))
            else:
                train_pts.append({'step': step, 'loss': float(row['loss']), 'grad_norm': float(row.get('grad_norm') or '0'), 'lr': float(row.get('learning_rate') or '0')})
    return train_pts, eval_pts

runs = ["lora_r4_alpaca", "lora_r16_alpaca", "lora_r32_all_alpaca", "ia3_alpaca", "adalora_alpaca", "dora_r8_alpaca", "lora_r16_mlp_alpaca", "full_ft_alpaca"]

for rn in runs:
    tp, ep = parse_run(rn)
    ft = tp[-1]['loss'] if tp else 0
    fe = ep[-1][1] if ep else 0
    me = min(ep, key=lambda x: x[1]) if ep else (0, 0)
    ms, mv = me
    print(f"{rn}: train={ft:.4f} eval={fe:.4f} best_eval={mv:.4f}@{ms} gap={fe-ft:.4f} overshoot={fe-mv:.4f}")
    print(f"  eval_trail: {[(s, round(e, 4)) for s, e in ep]}")
PYEOF
```

### Step 21: bash

```bash
python3 -c "
import csv, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
run_name = 'lora_r4_alpaca'
csv_path = os.path.join(base, run_name, 'training_log.csv')
with open(csv_path) as f:
    content = f.read()
print(content[:500])
"
```

<details><summary>Output (501 chars)</summary>

```
step,loss,eval_loss,learning_rate,epoch,grad_norm
10,2.370376205444336,,0.000491,0.08,0.34562116861343384
20,2.3448015213012696,,0.000481,0.16,0.5266590118408203
30,2.090583610534668,,0.000471,0.24,0.530121922492981
40,1.7852869033813477,,0.00046100000000000004,0.32,0.5756124258041382
50,1.525878620147705,,0.000451,0.4,0.4649342894554138
50,1.484494924545288,1.484494924545288,,0.4,
60,1.4268163681030273,,0.000441,0.48,0.41904351115226746
70,1.4194287300109862,,0.000431,0.56,0.3881954550743103
80

```
</details>

### Step 22: bash

```bash
python3 << 'SCRIPT'
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '')
            if ev and ev.strip():
                eval_pts.append((step, float(ev)))
            else:
                train_pts.append({
                    'step': step,
                    'loss': float(row['loss']),
                    'grad_norm': float(row['grad_norm']) if row['grad_norm'] else 0.0,
                    'lr': float(row['learning_rate']) if row['learning_rate'] else 0.0
                })
    return train_pts, eval_pts

runs = ["lora_r4_alpaca", "lora_r16_alpaca", "lora_r32_all_alpaca", "ia3_alpaca", "adalora_alpaca", "dora_r8_alpaca", "lora_r16_mlp_alpaca", "full_ft_alpaca"]

for rn in runs:
    tp, ep = parse_run(rn)
    ft = tp[-1]['loss']
    fe = ep[-1][1]
    ms, mv = min(ep, key=lambda x: x[1])
    print(f"RUN: {rn}")
    print(f"  final_train={ft:.4f} final_eval={fe:.4f} best_eval={mv:.4f}@step{ms} gap={fe-ft:.4f} overshoot={fe-mv:.4f}")
    print(f"  eval_steps: {[s for s,e in ep]}")
    print(f"  eval_vals:  {[round(e,4) for s,e in ep]}")
    print()
SCRIPT
```

### Step 23: bash

```bash
python3 -u -c 'print("hello")'
```

<details><summary>Output (6 chars)</summary>

```
hello

```
</details>

### Step 24: bash

```bash
python3 -u << 'SCRIPT'
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '')
            if ev and ev.strip():
                eval_pts.append((step, float(ev)))
            else:
                train_pts.append({
                    'step': step,
                    'loss': float(row['loss']),
                    'grad_norm': float(row['grad_norm']) if row['grad_norm'] else 0.0,
                    'lr': float(row['learning_rate']) if row['learning_rate'] else 0.0
                })
    return train_pts, eval_pts

rn = "lora_r4_alpaca"
tp, ep = parse_run(rn)
ft = tp[-1]['loss']
fe = ep[-1][1]
ms, mv = min(ep, key=lambda x: x[1])
print(f"RUN: {rn}")
print(f"  final_train={ft:.4f} final_eval={fe:.4f} best_eval={mv:.4f}@step{ms}")
SCRIPT
```

### Step 25: bash

```bash
python3 -u -c "
import csv, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
csv_path = os.path.join(base, 'lora_r4_alpaca', 'training_log.csv')
train_pts = []
eval_pts = []
with open(csv_path) as f:
    reader = csv.DictReader(f)
    for row in reader:
        step = int(row['step'])
        ev = row.get('eval_loss', '')
        if ev and ev.strip():
            eval_pts.append((step, float(ev)))
        else:
            train_pts.append({'step': step, 'loss': float(row['loss'])})
ft = train_pts[-1]['loss']
fe = eval_pts[-1][1]
ms, mv = min(eval_pts, key=lambda x: x[1])
print(f'final_train={ft:.4f} final_eval={fe:.4f} best_eval={mv:.4f}@step{ms}')
print(f'eval_vals: {[(s, round(e,4)) for s,e in eval_pts]}')
"

```

### Step 26: bash

```bash
python3 -c "
import csv, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
csv_path = os.path.join(base, 'lora_r4_alpaca', 'training_log.csv')
with open(csv_path) as f:
    reader = csv.DictReader(f)
    train_pts = []
    eval_pts = []
    for row in reader:
        step = int(row['step'])
        ev = row.get('eval_loss', '')
        if ev and ev.strip():
            eval_pts.append((step, float(ev)))
        else:
            train_pts.append((step, float(row['loss'])))
print('train_pts:', len(train_pts))
print('eval_pts:', len(eval_pts))
ft = train_pts[-1][1]
fe = eval_pts[-1][1]
print('final_train:', ft)
print('final_eval:', fe)
" 2>&1
```

<details><summary>Output (125 chars)</summary>

```
Traceback (most recent call last):
  File "<string>", line 15, in <module>
ValueError: could not convert string to float: ''

```
</details>

### Step 27: bash

```bash
python3 -c "
import csv, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
csv_path = os.path.join(base, 'lora_r4_alpaca', 'training_log.csv')
with open(csv_path) as f:
    reader = csv.DictReader(f)
    train_pts = []
    eval_pts = []
    for row in reader:
        step = int(row['step'])
        ev = row.get('eval_loss', '').strip()
        loss = row.get('loss', '').strip()
        lr = row.get('learning_rate', '').strip()
        if ev:
            eval_pts.append((step, float(ev)))
        if lr:
            train_pts.append((step, float(loss)))
ft = train_pts[-1][1]
fe = eval_pts[-1][1]
ms, mv = min(eval_pts, key=lambda x: x[1])
print(f'lora_r4_alpaca: final_train={ft:.4f} final_eval={fe:.4f} best_eval={mv:.4f}@step{ms} gap={fe-ft:.4f}')
print(f'eval_vals: {[(s, round(e,4)) for s,e in eval_pts]}')
"
```

<details><summary>Output (250 chars)</summary>

```
lora_r4_alpaca: final_train=1.2701 final_eval=1.2924 best_eval=1.2924@step500 gap=0.0224
eval_vals: [(50, 1.4845), (100, 1.3345), (150, 1.3157), (200, 1.3049), (250, 1.2995), (300, 1.2987), (350, 1.2952), (400, 1.2928), (450, 1.2936), (500, 1.2924)]

```
</details>

### Step 28: bash

```bash
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            loss = row.get('loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            grad = row.get('grad_norm', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append({'step': step, 'loss': float(loss), 'lr': float(lr), 'grad_norm': float(grad) if grad else 0.0})
    return train_pts, eval_pts

v1_alpaca = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'dora_r8_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in v1_alpaca:
    tp, ep = parse_run(rn)
    ft = tp[-1]['loss']
    fe = ep[-1][1]
    ms, mv = min(ep, key=lambda x: x[1])
    overshoot = fe - mv
    gap = fe - ft
    # Find divergence: first step where eval_loss starts consistently rising
    div_step = None
    for i in range(1, len(ep)):
        if ep[i][1] > ep[i-1][1]:
            still_rising = all(ep[j][1] >= ep[i][1] for j in range(i, len(ep)))
            if still_rising:
                div_step = ep[i-1][0]
                break
    print(f'{rn}:')
    print(f'  final_train={ft:.4f}  final_eval={fe:.4f}  best_eval={mv:.4f}@step{ms}')
    print(f'  train_eval_gap={gap:.4f}  overshoot={overshoot:.4f}  divergence@step={div_step}')
    print(f'  eval_trajectory: {[(s, round(e,4)) for s,e in ep]}')
    print()
"
```

<details><summary>Output (2845 chars)</summary>

```
lora_r4_alpaca:
  final_train=1.2701  final_eval=1.2924  best_eval=1.2924@step500
  train_eval_gap=0.0224  overshoot=0.0000  divergence@step=None
  eval_trajectory: [(50, 1.4845), (100, 1.3345), (150, 1.3157), (200, 1.3049), (250, 1.2995), (300, 1.2987), (350, 1.2952), (400, 1.2928), (450, 1.2936), (500, 1.2924)]

lora_r16_alpaca:
  final_train=1.2096  final_eval=1.2850  best_eval=1.2850@step500
  train_eval_gap=0.0754  overshoot=0.0000  divergence@step=None
  eval_trajectory: [(50, 1.3453), (100, 1.3061), (150, 1.2965), (200, 1.289), (250, 1.287), (300, 1.2913), (350, 1.2858), (400, 1.2854), (450, 1.2874), (500, 1.285)]

lora_r32_all_alpaca:
  final_train=0.6826  final_eval=1.4411  best_eval=1.2738@step100
  train_eval_gap=0.7585  overshoot=0.1673  divergence@step=200
  eval_trajectory: [(50, 1.29), (100, 1.2738), (150, 1.2815), (200, 1.2785), (250, 1.2795), (300, 1.3488), (350, 1.3515), (400, 1.4348), (450, 1.445), (500, 1.4411)]

ia3_alpaca:
  final_train=1.3538  final_eval=1.3585  best_eval=1.3585@step500
  train_eval_gap=0.0048  overshoot=0.0000  divergence@step=None
  eval_trajectory: [(50, 2.033), (100, 1.7685), (150, 1.5808), (200, 1.4624), (250, 1.4106), (300, 1.3846), (350, 1.3705), (400, 1.3631), (450, 1.3597), (500, 1.3585)]

adalora_alpaca:
  final_train=1.3415  final_eval=1.3317  best_eval=1.3317@step500
  train_eval_gap=-0.0097  overshoot=0.0000  divergence@step=None
  eval_trajectory: [(50, 2.804), (100, 2.2507), (150, 1.7739), (200, 1.4684), (250, 1.3858), (300, 1.3575), (350, 1.3447), (400, 1.3365), (450, 1.3332), (500, 1.3317)]

dora_r8_alpaca:
  final_train=0.9670  final_eval=1.3838  best_eval=1.2859@step400
  train_eval_gap=0.4167  overshoot=0.0978  divergence@step=400
  eval_trajectory: [(100, 1.313), (200, 1.2917), (300, 1.2935), (400, 1.2859), (500, 1.2879), (600, 1.293), (700, 1.3044), (800, 1.3034), (900, 1.3168), (1000, 1.3145), (1100, 1.3238), (1200, 1.3376), (1300, 1.3478), (1400, 1.3627), (1500, 1.351), (1600, 1.3667), (1700, 1.3677), (1800, 1.3784), (1900, 1.3834), (2000, 1.3838)]

lora_r16_mlp_alpaca:
  final_train=0.0936  final_eval=2.4983  best_eval=1.2705@step200
  train_eval_gap=2.4047  overshoot=1.2278  divergence@step=200
  eval_trajectory: [(100, 1.2724), (200, 1.2705), (300, 1.3309), (400, 1.3951), (500, 1.4349), (600, 1.5341), (700, 1.7194), (800, 1.8759), (900, 1.9592), (1000, 1.9748), (1100, 2.1193), (1200, 2.2358), (1300, 2.3121), (1400, 2.3703), (1500, 2.3682), (1600, 2.4315), (1700, 2.4552), (1800, 2.4854), (1900, 2.4845), (2000, 2.4983)]

full_ft_alpaca:
  final_train=1.1045  final_eval=1.2727  best_eval=1.2712@step350
  train_eval_gap=0.1683  overshoot=0.0015  divergence@step=350
  eval_trajectory: [(50, 1.3347), (100, 1.2916), (150, 1.2854), (200, 1.2768), (250, 1.2716), (300, 1.2728), (350, 1.2712), (400, 1.2722), (450, 1.2726), (500, 1.2727)]


```
</details>

### Step 29: bash

```bash
# Now do the same for code_instructions and v2 (qwen3) runs
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            loss = row.get('loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            grad = row.get('grad_norm', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append({'step': step, 'loss': float(loss), 'lr': float(lr), 'grad_norm': float(grad) if grad else 0.0})
    return train_pts, eval_pts

# V1 code_instructions
v1_code = ['lora_r4_code_instructions', 'lora_r16_code_instructions', 'lora_r32_all_code_instructions', 'ia3_code_instructions', 'adalora_code_instructions', 'dora_r8_code_instructions', 'lora_r16_mlp_code_instructions', 'full_ft_code_instructions']

print('=== V1 SmolLM2-135M CODE_INSTRUCTIONS ===')
for rn in v1_code:
    tp, ep = parse_run(rn)
    ft = tp[-1]['loss']
    fe = ep[-1][1]
    ms, mv = min(ep, key=lambda x: x[1])
    overshoot = fe - mv
    gap = fe - ft
    div_step = None
    for i in range(1, len(ep)):
        if ep[i][1] > ep[i-1][1]:
            still_rising = all(ep[j][1] >= ep[i][1] for j in range(i, len(ep)))
            if still_rising:
                div_step = ep[i-1][0]
                break
    print(f'{rn}:')
    print(f'  final_train={ft:.4f}  final_eval={fe:.4f}  best_eval={mv:.4f}@step{ms}')
    print(f'  gap={gap:.4f}  overshoot={overshoot:.4f}  div@step={div_step}')
    print(f'  eval: {[(s, round(e,4)) for s,e in ep]}')
    print()
"

```

<details><summary>Output (3713 chars)</summary>

```
=== V1 SmolLM2-135M CODE_INSTRUCTIONS ===
lora_r4_code_instructions:
  final_train=0.6762  final_eval=0.9458  best_eval=0.9046@step700
  gap=0.2697  overshoot=0.0413  div@step=1000
  eval: [(100, 0.9525), (200, 0.932), (300, 0.9141), (400, 0.9129), (500, 0.9067), (600, 0.9131), (700, 0.9046), (800, 0.9166), (900, 0.9181), (1000, 0.9121), (1100, 0.9156), (1200, 0.9232), (1300, 0.9257), (1400, 0.9301), (1500, 0.9351), (1600, 0.9383), (1700, 0.9406), (1800, 0.9462), (1900, 0.9463), (2000, 0.9458)]

lora_r16_code_instructions:
  final_train=0.4205  final_eval=1.1526  best_eval=0.9059@step300
  gap=0.7321  overshoot=0.2467  div@step=500
  eval: [(100, 0.9302), (200, 0.9189), (300, 0.9059), (400, 0.9145), (500, 0.9081), (600, 0.9262), (700, 0.93), (800, 0.9616), (900, 0.9903), (1000, 0.9746), (1100, 1.0019), (1200, 1.0299), (1300, 1.0545), (1400, 1.0934), (1500, 1.0837), (1600, 1.1079), (1700, 1.1302), (1800, 1.1423), (1900, 1.15), (2000, 1.1526)]

lora_r32_all_code_instructions:
  final_train=0.0853  final_eval=1.6717  best_eval=0.8886@step100
  gap=1.5864  overshoot=0.7831  div@step=100
  eval: [(100, 0.8886), (200, 0.903), (300, 0.9429), (400, 1.0223), (500, 1.0293), (600, 1.1422), (700, 1.2154), (800, 1.3218), (900, 1.407), (1000, 1.3586), (1100, 1.4138), (1200, 1.4756), (1300, 1.5353), (1400, 1.5881), (1500, 1.5806), (1600, 1.6064), (1700, 1.6373), (1800, 1.6632), (1900, 1.6641), (2000, 1.6717)]

ia3_code_instructions:
  final_train=0.7925  final_eval=0.9182  best_eval=0.9182@step2000
  gap=0.1257  overshoot=0.0000  div@step=None
  eval: [(100, 1.0567), (200, 0.99), (300, 0.9674), (400, 0.9555), (500, 0.9467), (600, 0.9402), (700, 0.9329), (800, 0.9301), (900, 0.9285), (1000, 0.9245), (1100, 0.9225), (1200, 0.9221), (1300, 0.9212), (1400, 0.9199), (1500, 0.9193), (1600, 0.9189), (1700, 0.9187), (1800, 0.9183), (1900, 0.9185), (2000, 0.9182)]

adalora_code_instructions:
  final_train=0.8018  final_eval=0.9168  best_eval=0.9160@step1600
  gap=0.1150  overshoot=0.0008  div@step=None
  eval: [(100, 1.2917), (200, 1.0032), (300, 0.9617), (400, 0.9495), (500, 0.9391), (600, 0.9348), (700, 0.9267), (800, 0.9249), (900, 0.925), (1000, 0.9203), (1100, 0.9179), (1200, 0.9198), (1300, 0.9164), (1400, 0.9178), (1500, 0.9169), (1600, 0.916), (1700, 0.9169), (1800, 0.9175), (1900, 0.9173), (2000, 0.9168)]

dora_r8_code_instructions:
  final_train=0.5657  final_eval=1.0175  best_eval=0.9049@step500
  gap=0.4517  overshoot=0.1126  div@step=1000
  eval: [(100, 0.9396), (200, 0.9259), (300, 0.9097), (400, 0.9125), (500, 0.9049), (600, 0.9168), (700, 0.9117), (800, 0.9317), (900, 0.9366), (1000, 0.9312), (1100, 0.9489), (1200, 0.9576), (1300, 0.9727), (1400, 0.9851), (1500, 0.9902), (1600, 0.9984), (1700, 1.0079), (1800, 1.015), (1900, 1.0179), (2000, 1.0175)]

lora_r16_mlp_code_instructions:
  final_train=0.0977  final_eval=1.7115  best_eval=0.8966@step100
  gap=1.6137  overshoot=0.8149  div@step=100
  eval: [(100, 0.8966), (200, 0.9022), (300, 0.9191), (400, 0.973

... (713 chars truncated)
```
</details>

### Step 30: bash

```bash
# Now look at v2 (qwen3) runs
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            loss = row.get('loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            grad = row.get('grad_norm', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append({'step': step, 'loss': float(loss), 'lr': float(lr), 'grad_norm': float(grad) if grad else 0.0})
    return train_pts, eval_pts

v2_runs = [d for d in os.listdir(base) if d.startswith('qwen3_')]
v2_runs.sort()

for rn in v2_runs:
    tp, ep = parse_run(rn)
    ft = tp[-1]['loss']
    fe = ep[-1][1]
    ms, mv = min(ep, key=lambda x: x[1])
    overshoot = fe - mv
    gap = fe - ft
    div_step = None
    for i in range(1, len(ep)):
        if ep[i][1] > ep[i-1][1]:
            still_rising = all(ep[j][1] >= ep[i][1] for j in range(i, len(ep)))
            if still_rising:
                div_step = ep[i-1][0]
                break
    print(f'{rn}:')
    print(f'  final_train={ft:.4f}  final_eval={fe:.4f}  best_eval={mv:.4f}@step{ms}')
    print(f'  gap={gap:.4f}  overshoot={overshoot:.4f}  div@step={div_step}')
    print(f'  eval: {[(s, round(e,4)) for s,e in ep]}')
    print()
"

```

<details><summary>Output (6447 chars)</summary>

```
qwen3_dpo_b01_lora_r16_qwen3-0.6b:
  final_train=0.0649  final_eval=1.1780  best_eval=0.7894@step200
  gap=1.1131  overshoot=0.3886  div@step=200
  eval: [(100, 0.8448), (200, 0.7894), (300, 0.934), (400, 0.9465), (500, 0.9943), (600, 0.9982), (700, 1.178), (800, 1.1676), (900, 1.1621), (1000, 1.178)]

qwen3_dpo_b01_lora_r16_qwen3-1.7b:
  final_train=0.0702  final_eval=1.0909  best_eval=0.7547@step100
  gap=1.0207  overshoot=0.3362  div@step=100
  eval: [(100, 0.7547), (200, 0.8205), (300, 0.8618), (400, 0.9222), (500, 0.8916), (600, 0.9392), (700, 1.0975), (800, 1.0717), (900, 1.0905), (1000, 1.0909)]

qwen3_dpo_b01_lora_r32_all_qwen3-1.7b:
  final_train=0.0443  final_eval=2.4767  best_eval=1.5983@step200
  gap=2.4324  overshoot=0.8784  div@step=200
  eval: [(100, 2.0818), (200, 1.5983), (300, 1.8857), (400, 2.4967), (500, 2.3967), (600, 2.7166), (700, 2.3889), (800, 2.4438), (900, 2.4587), (1000, 2.4767)]

qwen3_dpo_b01_lora_r8_qwen3-1.7b:
  final_train=0.1638  final_eval=0.7760  best_eval=0.6407@step100
  gap=0.6122  overshoot=0.1354  div@step=100
  eval: [(100, 0.6407), (200, 0.6431), (300, 0.7191), (400, 0.7153), (500, 0.6828), (600, 0.7165), (700, 0.7741), (800, 0.7768), (900, 0.7767), (1000, 0.776)]

qwen3_dpo_b05_lora_r16_qwen3-1.7b:
  final_train=0.0461  final_eval=1.8553  best_eval=1.1002@step100
  gap=1.8092  overshoot=0.7551  div@step=100
  eval: [(100, 1.1002), (200, 1.4372), (300, 1.5975), (400, 1.6755), (500, 1.6488), (600, 1.6686), (700, 1.8338), (800, 1.8339), (900, 1.8436), (1000, 1.8553)]

qwen3_dpo_b05_lora_r32_all_qwen3-1.7b:
  final_train=0.0433  final_eval=6.0224  best_eval=5.0377@step200
  gap=5.9791  overshoot=0.9847  div@step=800
  eval: [(100, 6.7121), (200, 5.0377), (300, 7.224), (400, 7.9284), (500, 6.6672), (600, 5.6734), (700, 6.229), (800, 5.9453), (900, 5.957), (1000, 6.0224)]

qwen3_dpo_b05_lora_r8_qwen3-1.7b:
  final_train=0.0631  final_eval=1.1857  best_eval=0.7810@step100
  gap=1.1226  overshoot=0.4047  div@step=100
  eval: [(100, 0.781), (200, 0.8983), (300, 1.0698), (400, 1.1116), (500, 1.0902), (600, 1.0401), (700, 1.163), (800, 1.1479), (900, 1.1639), (1000, 1.1857)]

qwen3_kto_lora_r16_qwen3-1.7b:
  final_train=0.1586  final_eval=0.3531  best_eval=0.3531@step1000
  gap=0.1944  overshoot=0.0000  div@step=None
  eval: [(100, 0.3996), (200, 0.3798), (300, 0.3672), (400, 0.3608), (500, 0.3576), (600, 0.3545), (700, 0.3551), (800, 0.3541), (900, 0.3541), (1000, 0.3531)]

qwen3_kto_lora_r8_qwen3-1.7b:
  final_train=0.2141  final_eval=0.3557  best_eval=0.3557@step1000
  gap=0.1416  overshoot=0.0000  div@step=None
  eval: [(100, 0.4114), (200, 0.3863), (300, 0.3727), (400, 0.365), (500, 0.3609), (600, 0.3594), (700, 0.3589), (800, 0.3562), (900, 0.3563), (1000, 0.3557)]

qwen3_sft_dora_r16_qwen3-1.7b:
  final_train=1.0460  final_eval=1.2833  best_eval=1.2589@step600
  gap=0.2373  overshoot=0.0245  div@step=900
  eval: [(100, 1.2848), (200, 1.2729), (300, 1.2677), (400, 1.2634), (500, 1.2618), (600, 1.2589), (700,

... (3447 chars truncated)
```
</details>

### Step 31: bash

```bash
# Now let's look at the evaluation results (benchmark scores)
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/
```

<details><summary>Output (129 chars)</summary>

```
eval_results.json
samples_arc_easy.jsonl
samples_boolq.jsonl
samples_hellaswag.jsonl
samples_piqa.jsonl
samples_winogrande.jsonl

```
</details>

### Step 32: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r32_all_alpaca/eval_results.json
```

<details><summary>Output (1364 chars)</summary>

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

### Step 33: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r16_alpaca/eval_results.json
```

<details><summary>Output (1356 chars)</summary>

```
{
  "adapter": "lora_r16_alpaca",
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
      "acc,none": 0.585,
      "acc_stderr,none": 0.0349281387189735,
      "acc_norm,none": 0.57,
      "acc_norm_stderr,none": 0.03509498954918328
    },
    "hellaswag": {
      "name": "hellaswag",
      "alias": "hellaswag",
      "sample_len": 200,
      "acc,none": 0.43,
      "acc_stderr,none": 0.03509498954918329,
      "acc_norm,none": 0.475,
      "acc_norm_stderr,none": 0.0353997274497642
    },
    "piqa": {
      "name": "piqa",
      "alias": "piqa",
      "sample_len": 200,
      "acc,none": 0.665,
      "acc_stderr,none": 0.033458517029435815,
      "acc_norm,none": 0.67,
      "acc_norm_stderr,none": 0.033332495801873405
    },
    "winogrande": {
      "name": "winogrande",
      "alias": "winogrande",
      "sample_len": 200,
      "acc,none": 0.485,
      "acc_stderr,none": 0.03542810683297719
    },
    "boolq": {
      "name": "boolq",
      "alias": "boolq",
      "sample_len": 200,
      "acc,none": 0.63,
      "acc_stderr,none": 0.03422508997679329
    }
  },
  "timestamp": "2026-05-13T02:56:29.544200+00:00"
}
```
</details>

### Step 34: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r4_alpaca/eval_results.json
```

<details><summary>Output (1353 chars)</summary>

```
{
  "adapter": "lora_r4_alpaca",
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
      "acc,none": 0.59,
      "acc_stderr,none": 0.03486513859784927,
      "acc_norm,none": 0.6,
      "acc_norm_stderr,none": 0.0347279448103939
    },
    "hellaswag": {
      "name": "hellaswag",
      "alias": "hellaswag",
      "sample_len": 200,
      "acc,none": 0.43,
      "acc_stderr,none": 0.03509498954918329,
      "acc_norm,none": 0.48,
      "acc_norm_stderr,none": 0.03541569365103447
    },
    "piqa": {
      "name": "piqa",
      "alias": "piqa",
      "sample_len": 200,
      "acc,none": 0.665,
      "acc_stderr,none": 0.03345851702943581,
      "acc_norm,none": 0.665,
      "acc_norm_stderr,none": 0.03345851702943581
    },
    "winogrande": {
      "name": "winogrande",
      "alias": "winogrande",
      "sample_len": 200,
      "acc,none": 0.515,
      "acc_stderr,none": 0.03542810683297719
    },
    "boolq": {
      "name": "boolq",
      "alias": "boolq",
      "sample_len": 200,
      "acc,none": 0.625,
      "acc_stderr,none": 0.03431856376795913
    }
  },
  "timestamp": "2026-05-13T03:07:25.962486+00:00"
}
```
</details>

### Step 35: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/evaluations/lora_r16_mlp_alpaca/eval_results.json
```

<details><summary>Output (1359 chars)</summary>

```
{
  "adapter": "lora_r16_mlp_alpaca",
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
      "acc,none": 0.43,
      "acc_stderr,none": 0.03509498954918329,
      "acc_norm,none": 0.48,
      "acc_norm_stderr,none": 0.03541569365103447
    },
    "hellaswag": {
      "name": "hellaswag",
      "alias": "hellaswag",
      "sample_len": 200,
      "acc,none": 0.4,
      "acc_stderr,none": 0.03472794481039391,
      "acc_norm,none": 0.445,
      "acc_norm_stderr,none": 0.03522897106090459
    },
    "piqa": {
      "name": "piqa",
      "alias": "piqa",
      "sample_len": 200,
      "acc,none": 0.625,
      "acc_stderr,none": 0.03431856376795913,
      "acc_norm,none": 0.625,
      "acc_norm_stderr,none": 0.03431856376795913
    },
    "winogrande": {
      "name": "winogrande",
      "alias": "winogrande",
      "sample_len": 200,
      "acc,none": 0.505,
      "acc_stderr,none": 0.035442288003096976
    },
    "boolq": {
      "name": "boolq",
      "alias": "boolq",
      "sample_len": 200,
      "acc,none": 0.595,
      "acc_stderr,none": 0.034798414450104
    }
  },
  "timestamp": "2026-05-13T03:00:06.845087+00:00"
}
```
</details>

### Step 36: bash

```bash
# Collect all eval results for comparison
python3 -c "
import json, os, glob

base = '/home/ubuntu/workspace/training-export-proprietary/evaluations'
runs = sorted(os.listdir(base))

print(f'{'Run':<45} {'arc_e':>6} {'hellas':>6} {'piqa':>6} {'wino':>6} {'boolq':>6} {'avg':>6}')
print('-' * 90)

for rn in runs:
    eval_path = os.path.join(base, rn, 'eval_results.json')
    if not os.path.exists(eval_path):
        continue
    with open(eval_path) as f:
        data = json.load(f)
    results = data.get('results', {})
    
    scores = {}
    for bench in ['arc_easy', 'hellaswag', 'piqa', 'winogrande', 'boolq']:
        if bench in results:
            # Use acc_norm if available, else acc
            acc_norm_key = 'acc_norm,none'
            acc_key = 'acc,none'
            if acc_norm_key in results[bench]:
                scores[bench] = results[bench][acc_norm_key]
            elif acc_key in results[bench]:
                scores[bench] = results[bench][acc_key]
    
    arc = scores.get('arc_easy', 0)
    hell = scores.get('hellaswag', 0)
    piqa = scores.get('piqa', 0)
    wino = scores.get('winogrande', 0)
    boolq = scores.get('boolq', 0)
    avg = sum(scores.values()) / len(scores) if scores else 0
    
    print(f'{rn:<45} {arc:>6.3f} {hell:>6.3f} {piqa:>6.3f} {wino:>6.3f} {boolq:>6.3f} {avg:>6.3f}')
"

```

<details><summary>Output (3259 chars)</summary>

```
Run                                            arc_e hellas   piqa   wino  boolq    avg
------------------------------------------------------------------------------------------
adalora                                        0.590  0.450  0.660  0.000  0.000  0.567
adalora_alpaca                                 0.595  0.465  0.660  0.475  0.620  0.563
adalora_code_instructions                      0.540  0.470  0.690  0.500  0.625  0.565
dora_r8_alpaca                                 0.515  0.465  0.680  0.485  0.635  0.556
dora_r8_code_instructions                      0.520  0.475  0.670  0.495  0.605  0.553
ia3                                            0.580  0.460  0.650  0.000  0.000  0.563
ia3_alpaca                                     0.595  0.465  0.650  0.485  0.605  0.560
ia3_code_instructions                          0.560  0.455  0.665  0.480  0.640  0.560
lora_r16                                       0.560  0.470  0.660  0.000  0.000  0.563
lora_r16_alpaca                                0.570  0.475  0.670  0.485  0.630  0.566
lora_r16_code_instructions                     0.485  0.495  0.685  0.490  0.600  0.551
lora_r16_mlp_alpaca                            0.480  0.445  0.625  0.505  0.595  0.530
lora_r16_mlp_code_instructions                 0.525  0.480  0.665  0.530  0.610  0.562
lora_r32_all                                   0.530  0.450  0.690  0.000  0.000  0.557
lora_r32_all_alpaca                            0.545  0.490  0.695  0.540  0.610  0.576
lora_r32_all_code_instructions                 0.510  0.475  0.660  0.510  0.630  0.557
lora_r4                                        0.600  0.460  0.660  0.000  0.000  0.573
lora_r4_alpaca                                 0.600  0.480  0.665  0.515  0.625  0.577
lora_r4_code_instructions                      0.540  0.480  0.670  0.475  0.610  0.555
qwen3_dpo_b01_lora_r16_qwen3-0.6b              0.587  0.523  0.673  0.593  0.000  0.594
qwen3_dpo_b01_lora_r32_all_qwen3-1.7b          0.533  0.543  0.697  0.603  0.000  0.594
qwen3_dpo_b01_lora_r8_qwen3-1.7b               0.577  0.600  0.767  0.630  0.000  0.643
qwen3_dpo_b05_lora_r16_qwen3-1.7b              0.630  0.600  0.767  0.627  0.000  0.656
qwen3_dpo_b05_lora_r32_all_qwen3-1.7b          0.590  0.567  0.727  0.603  0.000  0.622
qwen3_dpo_b05_lora_r8_qwen3-1.7b               0.593  0.603  0.763  0.620  0.000  0.645
qwen3_kto_lora_r16_qwen3-1.7b                  0.563  0.603  0.753  0.627  0.000  0.637
qwen3_kto_lora_r8_qwen3-1.7b                   0.543  0.600  0.760  0.607  0.000  0.627
qwen3_sft_dora_r16_qwen3-1.7b                  0.670  0.590  0.770  0.613  0.000  0.661
qwen3_sft_full_ft_qwen3-1.7b                   0.690  0.587  0.780  0.630  0.000  0.672
qwen3_sft_lora_r16_qwen3-0.6b                  0.553  0.520  0.680  0.610  0.000  0.591
qwen3_sft_lora_r16_qwen3-1.7b                  0.653  0.600  0.777  0.623  0.000  0.663
qwen3_sft_lora_r32_all_qwen3-0.6b              0.547  0.517  0.700  0.560  0.000  0.581
qwen3

... (259 chars truncated)
```
</details>

### Step 37: bash

```bash
# Now let's look at adapter configs to understand what differentiates these runs
python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'
v1_runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'dora_r8_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in v1_runs:
    config_path = os.path.join(base, rn, 'adapter_config.json')
    training_path = os.path.join(base, rn, 'training_config.json')
    
    print(f'\n=== {rn} ===')
    if os.path.exists(config_path):
        with open(config_path) as f:
            cfg = json.load(f)
        print(f'  Adapter type: {cfg.get(\"peft_type\", \"N/A\")}')
        print(f'  r: {cfg.get(\"r\", \"N/A\")}')
        print(f'  target_modules: {cfg.get(\"target_modules\", \"N/A\")}')
        print(f'  lora_alpha: {cfg.get(\"lora_alpha\", \"N/A\")}')
        print(f'  lora_dropout: {cfg.get(\"lora_dropout\", \"N/A\")}')
    
    if os.path.exists(training_path):
        with open(training_path) as f:
            tcfg = json.load(f)
        print(f'  learning_rate: {tcfg.get(\"learning_rate\", \"N/A\")}')
        print(f'  num_train_epochs: {tcfg.get(\"num_train_epochs\", \"N/A\")}')
        print(f'  max_steps: {tcfg.get(\"max_steps\", \"N/A\")}')
        print(f'  per_device_train_batch_size: {tcfg.get(\"per_device_train_batch_size\", \"N/A\")}')
        print(f'  warmup_steps: {tcfg.get(\"warmup_steps\", \"N/A\")}')
        print(f'  lr_scheduler_type: {tcfg.get(\"lr_scheduler_type\", \"N/A\")}')
        print(f'  weight_decay: {tcfg.get(\"weight_decay\", \"N/A\")}')
"

```

<details><summary>Output (2331 chars)</summary>

```

=== lora_r4_alpaca ===
  Adapter type: LORA
  r: 4
  target_modules: ['q_proj', 'v_proj']
  lora_alpha: 8
  lora_dropout: 0.05
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== lora_r16_alpaca ===
  Adapter type: LORA
  r: 16
  target_modules: ['q_proj', 'v_proj']
  lora_alpha: 32
  lora_dropout: 0.05
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== lora_r32_all_alpaca ===
  Adapter type: LORA
  r: 32
  target_modules: ['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  lora_alpha: 64
  lora_dropout: 0.1
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== ia3_alpaca ===
  Adapter type: IA3
  r: N/A
  target_modules: ['v_proj', 'q_proj', 'down_proj', 'k_proj']
  lora_alpha: N/A
  lora_dropout: N/A
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== adalora_alpaca ===
  Adapter type: ADALORA
  r: 8
  target_modules: ['q_proj', 'v_proj']
  lora_alpha: 32
  lora_dropout: 0.0
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== dora_r8_alpaca ===
  Adapter type: LORA
  r: 8
  target_modules: ['q_proj', 'v_proj']
  lora_alpha: 16
  lora_dropout: 0.05
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== lora_r16_mlp_alpaca ===
  Adapter type: LORA
  r: 16
  target_modules: ['up_proj', 'gate_proj', 'down_proj']
  lora_alpha: 32
  lora_dropout: 0.05
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

=== full_ft_alpaca ===
  learning_rate: N/A
  num_train_epochs: N/A
  max_steps: N/A
  per_device_train_batch_size: N/A
  warmup_steps: N/A
  lr_scheduler_type: N/A
  weight_decay: N/A

```
</details>

### Step 38: bash

```bash
# Check the training configs - they seem to be empty, let's look at trainer_state for more info
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

### Step 39: bash

```bash
# Get all training configs 
python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'
v1_runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'dora_r8_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in v1_runs:
    path = os.path.join(base, rn, 'training_config.json')
    if os.path.exists(path):
        with open(path) as f:
            cfg = json.load(f)
        print(f'{rn}:')
        adapter = cfg.get('adapter_config', {})
        args = cfg.get('training_args', {})
        results = cfg.get('results', {})
        print(f'  r={adapter.get(\"r\",\"-\")} alpha={adapter.get(\"lora_alpha\",\"-\")} targets={adapter.get(\"target_modules\",\"-\")} dropout={adapter.get(\"lora_dropout\",\"-\")}')
        print(f'  lr={args.get(\"learning_rate\",\"-\")} max_steps={args.get(\"max_steps\",\"-\")} bs={args.get(\"batch_size\",\"-\")}')
        print(f'  trainable={results.get(\"trainable_params\",\"-\")} total={results.get(\"total_params\",\"-\")} overhead={results.get(\"adapter_overhead_pct\",\"-\")}%')
        print()
"

```

<details><summary>Output (1267 chars)</summary>

```
lora_r4_alpaca:
  r=4 alpha=8 targets=['q_proj', 'v_proj'] dropout=0.05
  lr=0.0005 max_steps=500 bs=4
  trainable=230400 total=134745408 overhead=0.171%

lora_r16_alpaca:
  r=16 alpha=32 targets=['q_proj', 'v_proj'] dropout=0.05
  lr=0.0005 max_steps=500 bs=4
  trainable=921600 total=135436608 overhead=0.6805%

lora_r32_all_alpaca:
  r=32 alpha=64 targets=all-linear dropout=0.1
  lr=0.0005 max_steps=500 bs=4
  trainable=9768960 total=144283968 overhead=6.7706%

ia3_alpaca:
  r=- alpha=- targets=['q_proj', 'v_proj', 'k_proj', 'down_proj'] dropout=-
  lr=0.0005 max_steps=500 bs=4
  trainable=74880 total=134589888 overhead=0.0556%

adalora_alpaca:
  r=- alpha=32 targets=['q_proj', 'v_proj'] dropout=-
  lr=0.0005 max_steps=500 bs=4
  trainable=922560 total=135437628 overhead=0.6812%

dora_r8_alpaca:
  r=8 alpha=16 targets=['q_proj', 'v_proj'] dropout=0.05
  lr=0.0005 max_steps=2000 bs=4
  trainable=483840 total=134998848 overhead=0.3584%

lora_r16_mlp_alpaca:
  r=16 alpha=32 targets=['gate_proj', 'up_proj', 'down_proj'] dropout=0.05
  lr=0.0005 max_steps=2000 bs=4
  trainable=3041280 total=137556288 overhead=2.2109%

full_ft_alpaca:
  r=- alpha=- targets=- dropout=-
  lr=1e-05 max_steps=500 bs=4
  trainable=134515008 total=134515008 overhead=100.0%


```
</details>

### Step 40: bash

```bash
# Now look at adapter weight stats to understand magnitude/health
python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'
v1_runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'dora_r8_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in v1_runs:
    path = os.path.join(base, rn, 'adapter_weight_stats.json')
    if os.path.exists(path):
        with open(path) as f:
            stats = json.load(f)
        print(f'\n{rn}:')
        for layer_name, layer_stats in stats.items():
            print(f'  {layer_name}: norm={layer_stats.get(\"l2_norm\", \"-\"):.4f} max={layer_stats.get(\"max_abs\", \"-\"):.6f} mean_abs={layer_stats.get(\"mean_abs\", \"-\"):.6f}')
"

```

<details><summary>Output (17 chars)</summary>

```

lora_r4_alpaca:

```
</details>

### Step 41: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 42: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 43: bash

```bash
head -100 /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 44: bash

```bash
wc -c /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 45: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 46: bash

```bash
ls -la /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 47: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 48: bash

```bash
echo "test"
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 49: bash

```bash
echo "test"
```

<details><summary>Output (23 chars)</summary>

```
Bash session restarted.
```
</details>

### Step 50: bash

```bash
python3 -c "
import json
with open('/home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json') as f:
    stats = json.load(f)
for k, v in stats.items():
    print(f'{k}: {v}')
"
```

<details><summary>Output (164 chars)</summary>

```
Error calling tool 'bash': Bash session timed out waiting for output after 120.0s. Background processes may still be running. Use restart=true to get a new session.
```
</details>

### Step 51: bash

```bash
python3 -c "import json; f=open('/home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json'); d=json.load(f); print(list(d.keys())[:5])"
```

<details><summary>Output (23 chars)</summary>

```
Bash session restarted.
```
</details>

### Step 52: bash

```bash
python3 -c "
import json
with open('/home/ubuntu/workspace/training-export-proprietary/runs/lora_r32_all_alpaca/adapter_weight_stats.json') as f:
    d = json.load(f)
print(type(d))
if isinstance(d, dict):
    print(list(d.keys())[:5])
    for k in list(d.keys())[:2]:
        print(k, d[k])
elif isinstance(d, list):
    print(len(d))
    print(d[0])
"
```

<details><summary>Output (1024 chars)</summary>

```
<class 'dict'>
['base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.k_proj.lora_A.default.weight', 'base_model.model.model.layers.0.self_attn.k_proj.lora_B.default.weight', 'base_model.model.model.layers.0.self_attn.v_proj.lora_A.default.weight']
base_model.model.model.layers.0.self_attn.q_proj.lora_A.default.weight {'shape': [32, 576], 'num_params': 18432, 'mean': 8.278754103230312e-05, 'std': 0.025924116373062134, 'norm': 3.5194971561431885, 'abs_mean': 0.02200385555624962, 'sparsity': 0.0, 'min': -0.06813261657953262, 'max': 0.06689862906932831}
base_model.model.model.layers.0.self_attn.q_proj.lora_B.default.weight {'shape': [576, 32], 'num_params': 18432, 'mean': 1.4135112905933056e-05, 'std': 0.007783845998346806, 'norm': 1.0567426681518555, 'abs_mean': 0.006194498389959335, 'sparsity': 0.00010850694525288418, 'min': -0.036201830953359604, 'max': 0.03585277125239372}

```
</details>

### Step 53: bash

```bash
# Get weight norm summaries across layers for each adapter config
python3 -c "
import json, os, re
import numpy as np

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

v1_runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'dora_r8_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in v1_runs:
    path = os.path.join(base, rn, 'adapter_weight_stats.json')
    if not os.path.exists(path):
        print(f'{rn}: NO WEIGHT STATS')
        continue
    with open(path) as f:
        stats = json.load(f)
    
    # Group by layer type (lora_A, lora_B, etc.)
    groups = {}
    for key, val in stats.items():
        # Extract the type
        if 'lora_A' in key:
            gtype = 'lora_A'
        elif 'lora_B' in key:
            gtype = 'lora_B'
        elif 'ia3' in key.lower():
            gtype = 'ia3'
        else:
            gtype = 'other'
        
        if gtype not in groups:
            groups[gtype] = []
        groups[gtype].append(val['norm'])
    
    print(f'{rn}:')
    for gtype, norms in groups.items():
        print(f'  {gtype}: norm mean={np.mean(norms):.4f} max={np.max(norms):.4f} min={np.min(norms):.4f}')
    print()
"
```

<details><summary>Output (932 chars)</summary>

```
lora_r4_alpaca:
  lora_A: norm mean=1.6782 max=1.9976 min=1.4146
  lora_B: norm mean=0.6913 max=1.0376 min=0.3813

lora_r16_alpaca:
  lora_A: norm mean=2.8126 max=3.1834 min=2.5218
  lora_B: norm mean=0.8918 max=1.3664 min=0.4783

lora_r32_all_alpaca:
  lora_A: norm mean=3.7980 max=4.4773 min=3.3470
  lora_B: norm mean=1.2365 max=2.3108 min=0.4225

ia3_alpaca:
  ia3: norm mean=22.7054 max=39.2846 min=13.7473

adalora_alpaca:
  lora_A: norm mean=4.0000 max=4.0001 min=4.0000
  lora_B: norm mean=3.9995 max=4.0147 min=3.9560
  other: norm mean=0.3767 max=0.4696 min=0.1996

dora_r8_alpaca:
  lora_A: norm mean=3.2730 max=4.1230 min=2.5622
  lora_B: norm mean=1.6124 max=2.8352 min=0.7400
  other: norm mean=88.1568 max=161.5218 min=14.7589

lora_r16_mlp_alpaca:
  lora_A: norm mean=4.7437 max=6.1666 min=3.6855
  lora_B: norm mean=3.0424 max=4.1906 min=1.2701

full_ft_alpaca:
  other: norm mean=101.9546 max=712.8192 min=0.9561


```
</details>

### Step 54: bash

```bash
# Now check checkpoint-level eval loss and grad_norm patterns from trainer_state.json
# This will help us see the divergence pattern more clearly at each checkpoint

python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

# Get trainer_state from each checkpoint for lora_r32_all_alpaca
run = 'lora_r32_all_alpaca'
ckpts = sorted(os.listdir(os.path.join(base, run, 'checkpoints')))
print(f'Checkpoints for {run}: {ckpts}')

for ckpt in ckpts:
    state_path = os.path.join(base, run, 'checkpoints', ckpt, 'trainer_state.json')
    with open(state_path) as f:
        state = json.load(f)
    # Extract eval entries
    eval_entries = [e for e in state.get('log_history', []) if 'eval_loss' in e]
    print(f'  {ckpt}: {len(eval_entries)} eval entries, last eval_loss={eval_entries[-1][\"eval_loss\"]:.4f}' if eval_entries else f'  {ckpt}: no eval entries')
"

```

<details><summary>Output (409 chars)</summary>

```
Checkpoints for lora_r32_all_alpaca: ['checkpoint-100', 'checkpoint-200', 'checkpoint-300', 'checkpoint-400', 'checkpoint-500']
  checkpoint-100: 2 eval entries, last eval_loss=1.2738
  checkpoint-200: 4 eval entries, last eval_loss=1.2785
  checkpoint-300: 6 eval entries, last eval_loss=1.3488
  checkpoint-400: 8 eval entries, last eval_loss=1.4348
  checkpoint-500: 10 eval entries, last eval_loss=1.4411

```
</details>

### Step 55: bash

```bash
# Now let's look at grad_norm evolution - this is often an early warning signal
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            loss = row.get('loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            grad = row.get('grad_norm', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append({'step': step, 'loss': float(loss), 'lr': float(lr), 'grad_norm': float(grad) if grad else 0.0})
    return train_pts, eval_pts

# Focus on key comparison runs
runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca', 'dora_r8_alpaca', 'ia3_alpaca']

print('Grad norm evolution (sampled every 50 steps):')
for rn in runs:
    tp, ep = parse_run(rn)
    # Sample grad_norm at regular intervals
    grad_samples = [(p['step'], p['grad_norm']) for p in tp if p['step'] % 50 == 0]
    print(f'\n{rn}:')
    for step, gn in grad_samples:
        print(f'  step {step:4d}: grad_norm={gn:.4f}')
"

```

<details><summary>Output (4072 chars)</summary>

```
Grad norm evolution (sampled every 50 steps):

lora_r4_alpaca:
  step   50: grad_norm=0.4649
  step  100: grad_norm=0.4480
  step  150: grad_norm=0.4552
  step  200: grad_norm=0.5301
  step  250: grad_norm=0.3584
  step  300: grad_norm=0.5140
  step  350: grad_norm=0.3035
  step  400: grad_norm=0.4421
  step  450: grad_norm=0.4848
  step  500: grad_norm=0.3855

lora_r16_alpaca:
  step   50: grad_norm=0.5323
  step  100: grad_norm=0.4931
  step  150: grad_norm=0.4675
  step  200: grad_norm=0.5496
  step  250: grad_norm=0.3918
  step  300: grad_norm=0.4596
  step  350: grad_norm=0.3459
  step  400: grad_norm=0.4439
  step  450: grad_norm=0.5132
  step  500: grad_norm=0.4227

lora_r32_all_alpaca:
  step   50: grad_norm=0.4204
  step  100: grad_norm=0.4760
  step  150: grad_norm=0.4614
  step  200: grad_norm=0.4843
  step  250: grad_norm=0.4925
  step  300: grad_norm=0.5420
  step  350: grad_norm=0.4833
  step  400: grad_norm=0.5416
  step  450: grad_norm=0.7115
  step  500: grad_norm=0.5668

lora_r16_mlp_alpaca:
  step   50: grad_norm=0.2830
  step  100: grad_norm=0.3522
  step  150: grad_norm=0.3580
  step  200: grad_norm=0.4031
  step  250: grad_norm=0.4020
  step  300: grad_norm=0.4899
  step  350: grad_norm=0.4308
  step  400: grad_norm=0.5224
  step  450: grad_norm=0.6869
  step  500: grad_norm=0.5819
  step  550: grad_norm=0.6823
  step  600: grad_norm=0.7522
  step  650: grad_norm=0.4983
  step  700: grad_norm=0.7396
  step  750: grad_norm=0.7030
  step  800: grad_norm=0.6468
  step  850: grad_norm=0.6298
  step  900: grad_norm=0.5699
  step  950: grad_norm=0.5905
  step 1000: grad_norm=0.6674
  step 1050: grad_norm=0.6145
  step 1100: grad_norm=0.3847
  step 1150: grad_norm=0.6039
  step 1200: grad_norm=0.3843
  step 1250: grad_norm=0.4069
  step 1300: grad_norm=0.3730
  step 1350: grad_norm=0.4042
  step 1400: grad_norm=0.4607
  step 1450: grad_norm=0.4328
  step 1500: grad_norm=0.3718
  step 1550: grad_norm=0.3409
  step 1600: grad_norm=0.4341
  step 1650: grad_norm=0.2642
  step 1700: grad_norm=0.3683
  step 1750: grad_norm=0.3184
  step 1800: grad_norm=0.3481
  step 1850: grad_norm=0.4085
  step 1900: grad_norm=0.2324
  step 1950: grad_norm=0.3990
  step 2000: grad_norm=0.3311

full_ft_alpaca:
  step   50: grad_norm=2.5516
  step  100: grad_norm=3.2527
  step  150: grad_norm=2.7514
  step  200: grad_norm=2.7350
  step  250: grad_norm=2.5297
  step  300: grad_norm=2.4231
  step  350: grad_norm=2.2739
  step  400: grad_norm=2.4142
  step  450: grad_norm=2.7311
  step  500: grad_norm=2.4095

dora_r8_alpaca:
  step   50: grad_norm=0.4243
  step  100: grad_norm=0.4536
  step  150: grad_norm=0.4264
  step  200: grad_norm=0.5091
  step  250: grad_norm=0.3696
  step  300: grad_norm=0.4330
  step  350: grad_norm=0.3345
  step  400: grad_norm=0.4641
  step  450: grad_norm=0.6680
  step  500: grad_norm=0.4374
  step  550: grad_norm=0.4654
  step  600: grad_norm=0.4824
  step  650: grad_norm=0.4040
  step  700: grad_norm=0.6537
  step  750: grad_nor

... (1072 chars truncated)
```
</details>

### Step 56: bash

```bash
# Now let's check the checkpoint adapter configs to see how weights evolve
python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'
run = 'lora_r32_all_alpaca'

# Check each checkpoint's adapter_config
for ckpt in sorted(os.listdir(os.path.join(base, run, 'checkpoints'))):
    cfg_path = os.path.join(base, run, 'checkpoints', ckpt, 'adapter_config.json')
    if os.path.exists(cfg_path):
        with open(cfg_path) as f:
            cfg = json.load(f)
        print(f'{ckpt}: r={cfg.get(\"r\")} alpha={cfg.get(\"lora_alpha\")} targets={cfg.get(\"target_modules\")}')
    
    # Also check README for any notes
    readme_path = os.path.join(base, run, 'checkpoints', ckpt, 'README.md')
    if os.path.exists(readme_path):
        with open(readme_path) as f:
            content = f.read()
        if content.strip():
            print(f'  README: {content[:200]}')
"
```

<details><summary>Output (1635 chars)</summary>

```
checkpoint-100: r=32 alpha=64 targets=['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  README: ---
base_model: HuggingFaceTB/SmolLM2-135M
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:HuggingFaceTB/SmolLM2-135M
- lora
- transformers
---

# Model Card for Model ID


checkpoint-200: r=32 alpha=64 targets=['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  README: ---
base_model: HuggingFaceTB/SmolLM2-135M
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:HuggingFaceTB/SmolLM2-135M
- lora
- transformers
---

# Model Card for Model ID


checkpoint-300: r=32 alpha=64 targets=['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  README: ---
base_model: HuggingFaceTB/SmolLM2-135M
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:HuggingFaceTB/SmolLM2-135M
- lora
- transformers
---

# Model Card for Model ID


checkpoint-400: r=32 alpha=64 targets=['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  README: ---
base_model: HuggingFaceTB/SmolLM2-135M
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:HuggingFaceTB/SmolLM2-135M
- lora
- transformers
---

# Model Card for Model ID


checkpoint-500: r=32 alpha=64 targets=['up_proj', 'q_proj', 'k_proj', 'gate_proj', 'o_proj', 'down_proj', 'v_proj']
  README: ---
base_model: HuggingFaceTB/SmolLM2-135M
library_name: peft
pipeline_tag: text-generation
tags:
- base_model:adapter:HuggingFaceTB/SmolLM2-135M
- lora
- transformers
---

# Model Card for Model ID



```
</details>

### Step 57: bash

```bash
# Look at the memory profiles for additional info
python3 -c "
import json, os
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
v1_runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'ia3_alpaca', 'adalora_alpaca', 'dora_r8_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']
for rn in v1_runs:
    path = os.path.join(base, rn, 'memory_profile.json')
    if os.path.exists(path):
        with open(path) as f:
            d = json.load(f)
        print(f'{rn}: {d}')
"
```

<details><summary>Output (1280 chars)</summary>

```
lora_r4_alpaca: {'trainable_params': 230400, 'total_params': 134745408, 'adapter_overhead_pct': 0.171, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 538.98}
lora_r16_alpaca: {'trainable_params': 921600, 'total_params': 135436608, 'adapter_overhead_pct': 0.6805, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 541.75}
lora_r32_all_alpaca: {'trainable_params': 9768960, 'total_params': 144283968, 'adapter_overhead_pct': 6.7706, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 577.14}
ia3_alpaca: {'trainable_params': 74880, 'total_params': 134589888, 'adapter_overhead_pct': 0.0556, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 538.36}
adalora_alpaca: {'trainable_params': 922560, 'total_params': 135437628, 'adapter_overhead_pct': 0.6812, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 541.75}
dora_r8_alpaca: {'trainable_params': 483840, 'total_params': 134998848, 'adapter_overhead_pct': 0.3584, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 540.0}
lora_r16_mlp_alpaca: {'trainable_params': 3041280, 'total_params': 137556288, 'adapter_overhead_pct': 2.2109, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 550.23}
full_ft_alpaca: {'trainable_params': 134515008, 'total_params': 134515008, 'adapter_overhead_pct': 100.0, 'peak_memory_mb': 'cpu_only', 'model_size_mb': 538.06}

```
</details>

### Step 58: bash

```bash
# Now look at the Qwen3 v2 runs in more detail - adapter configs and training configs
python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'
v2_runs = sorted([d for d in os.listdir(base) if d.startswith('qwen3_')])

for rn in v2_runs:
    tc_path = os.path.join(base, rn, 'training_config.json')
    ac_path = os.path.join(base, rn, 'adapter_config.json')
    
    print(f'\n{rn}:')
    if os.path.exists(tc_path):
        with open(tc_path) as f:
            tc = json.load(f)
        adapter = tc.get('adapter_config', {})
        args = tc.get('training_args', {})
        results = tc.get('results', {})
        print(f'  r={adapter.get(\"r\",\"-\")} alpha={adapter.get(\"lora_alpha\",\"-\")} targets={adapter.get(\"target_modules\",\"-\")} dropout={adapter.get(\"lora_dropout\",\"-\")}')
        print(f'  lr={args.get(\"learning_rate\",\"-\")} max_steps={args.get(\"max_steps\",\"-\")} bs={args.get(\"batch_size\",\"-\")}')
        print(f'  trainable={results.get(\"trainable_params\",\"-\")} total={results.get(\"total_params\",\"-\")} overhead={results.get(\"adapter_overhead_pct\",\"-\")}%')
    elif os.path.exists(ac_path):
        with open(ac_path) as f:
            ac = json.load(f)
        print(f'  type={ac.get(\"peft_type\",\"-\")} r={ac.get(\"r\",\"-\")} alpha={ac.get(\"lora_alpha\",\"-\")} targets={ac.get(\"target_modules\",\"-\")}')
"
```

<details><summary>Output (3188 chars)</summary>

```

qwen3_dpo_b01_lora_r16_qwen3-0.6b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=4587520 total=605224960 overhead=0.758%

qwen3_dpo_b01_lora_r16_qwen3-1.7b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=6422528 total=1733420032 overhead=0.3705%

qwen3_dpo_b01_lora_r32_all_qwen3-1.7b:
  r=32 alpha=64 targets=all-linear dropout=0.1
  lr=5e-05 max_steps=1000 bs=4
  trainable=34865152 total=1790305280 overhead=1.9474%

qwen3_dpo_b01_lora_r8_qwen3-1.7b:
  r=8 alpha=16 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=3211264 total=1726997504 overhead=0.1859%

qwen3_dpo_b05_lora_r16_qwen3-1.7b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=6422528 total=1733420032 overhead=0.3705%

qwen3_dpo_b05_lora_r32_all_qwen3-1.7b:
  r=32 alpha=64 targets=all-linear dropout=0.1
  lr=5e-05 max_steps=1000 bs=4
  trainable=34865152 total=1790305280 overhead=1.9474%

qwen3_dpo_b05_lora_r8_qwen3-1.7b:
  r=8 alpha=16 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=3211264 total=1726997504 overhead=0.1859%

qwen3_kto_lora_r16_qwen3-1.7b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=6422528 total=1733420032 overhead=0.3705%

qwen3_kto_lora_r8_qwen3-1.7b:
  r=8 alpha=16 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=5e-05 max_steps=1000 bs=4
  trainable=3211264 total=1726997504 overhead=0.1859%

qwen3_sft_dora_r16_qwen3-1.7b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=0.0002 max_steps=2000 bs=4
  trainable=6594560 total=1727169536 overhead=0.3818%

qwen3_sft_full_ft_qwen3-1.7b:
  r=- alpha=- targets=- dropout=-
  lr=5e-06 max_steps=2000 bs=4
  trainable=1720574976 total=1720574976 overhead=100.0%

qwen3_sft_lora_r16_qwen3-0.6b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=0.0002 max_steps=2000 bs=4
  trainable=4587520 total=600637440 overhead=0.7638%

qwen3_sft_lora_r16_qwen3-1.7b:
  r=16 alpha=32 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=0.0002 max_steps=2000 bs=4
  trainable=6422528 total=1726997504 overhead=0.3719%

qwen3_sft_lora_r32_all_qwen3-0.6b:
  r=32 alpha=64 targets=all-linear dropout=0.1
  lr=0.0002 max_steps=2000 bs=4
  trainable=20185088 total=616235008 overhead=3.2756%

qwen3_sft_lora_r32_all_qwen3-1.7b:
  r=32 alpha=64 targets=all-linear dropout=0.1
  lr=0.0002 max_steps=2000 bs=4
  trainable=34865152 total=1755440128 overhead=1.9861%

qwen3_sft_lora_r8_qwen3-0.6b:
  r=8 alpha=16 targets=['q_proj', 'k_proj', 'v_proj', 'o_proj'] dropout=0.05
  lr=0.0002 max_steps=2000 bs=4
  trainable=2293760 total=598343680 overhead=0.3834%

qwen3

... (188 chars truncated)
```
</details>

### Step 59: bash

```bash
# Now let's look at the qwen3 eval results more carefully - we only saw arc_easy, hellaswag, piqa, winogrande (no boolq)
# Let's also look at the parquet files for cross-run comparison
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/eval_results_comparison.parquet')
print(df.columns.tolist())
print(df.shape)
print(df.head(10).to_string())
"
```

<details><summary>Output (670 chars)</summary>

```
['run_name', 'benchmark', 'metric', 'value']
(369, 4)
  run_name  benchmark                metric       value
0  adalora   arc_easy            sample_len  100.000000
1  adalora   arc_easy              acc,none    0.580000
2  adalora   arc_easy       acc_stderr,none    0.049604
3  adalora   arc_easy         acc_norm,none    0.590000
4  adalora   arc_easy  acc_norm_stderr,none    0.049431
5  adalora  hellaswag            sample_len  100.000000
6  adalora  hellaswag              acc,none    0.450000
7  adalora  hellaswag       acc_stderr,none    0.050000
8  adalora  hellaswag         acc_norm,none    0.450000
9  adalora  hellaswag  acc_norm_stderr,none    0.050000

```
</details>

### Step 60: bash

```bash
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/eval_results_comparison.parquet')
# Get just the acc_norm scores for comparison
acc_norm = df[df['metric'] == 'acc_norm,none'][['run_name', 'benchmark', 'value']].pivot(index='run_name', columns='benchmark', values='value')
acc_norm['avg'] = acc_norm.mean(axis=1)
acc_norm = acc_norm.sort_values('avg', ascending=False)
print(acc_norm.to_string())
"
```

<details><summary>Output (1449 chars)</summary>

```
benchmark                       arc_easy  hellaswag   piqa       avg
run_name                                                            
lora_r4_alpaca                     0.600      0.480  0.665  0.581667
lora_r32_all_alpaca                0.545      0.490  0.695  0.576667
adalora_alpaca                     0.595      0.465  0.660  0.573333
lora_r4                            0.600      0.460  0.660  0.573333
lora_r16_alpaca                    0.570      0.475  0.670  0.571667
ia3_alpaca                         0.595      0.465  0.650  0.570000
adalora                            0.590      0.450  0.660  0.566667
adalora_code_instructions          0.540      0.470  0.690  0.566667
lora_r4_code_instructions          0.540      0.480  0.670  0.563333
lora_r16                           0.560      0.470  0.660  0.563333
ia3                                0.580      0.460  0.650  0.563333
ia3_code_instructions              0.560      0.455  0.665  0.560000
lora_r16_mlp_code_instructions     0.525      0.480  0.665  0.556667
lora_r32_all                       0.530      0.450  0.690  0.556667
dora_r8_code_instructions          0.520      0.475  0.670  0.555000
lora_r16_code_instructions         0.485      0.495  0.685  0.555000
dora_r8_alpaca                     0.515      0.465  0.680  0.553333
lora_r32_all_code_instructions     0.510      0.475  0.660  0.548333
lora_r16_mlp_alpaca                0.480      0.445  0.625  0.516667

```
</details>

### Step 61: bash

```bash
# Look at the cross_adapter_comparison parquet
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/cross_adapter_comparison.parquet')
print(df.columns.tolist())
print(df.shape)
print(df.head(5).to_string())
"
```

<details><summary>Output (1104 chars)</summary>

```
['run_name', 'adapter', 'dataset', 'type', 'trainable_params', 'total_params', 'overhead_pct', 'final_train_loss', 'elapsed_seconds', 'max_steps']
(16, 10)
                    run_name  adapter            dataset     type  trainable_params  total_params  overhead_pct  final_train_loss  elapsed_seconds  max_steps
0             adalora_alpaca  adalora             alpaca  adalora            922560     135437628        0.6812          1.797923           536.75        500
1  adalora_code_instructions  adalora  code_instructions  adalora            922560     135437628        0.6812          0.906270          1960.45       2000
2             dora_r8_alpaca  dora_r8             alpaca     dora            483840     134998848        0.3584          1.114040          2815.13       2000
3  dora_r8_code_instructions  dora_r8  code_instructions     dora            483840     134998848        0.3584          0.698994          2687.35       2000
4             full_ft_alpaca  full_ft             alpaca     full         134515008     134515008      100.0000          1.224169           447.77        500

```
</details>

### Step 62: bash

```bash
# Look at the qwen3_cross_run_comparison parquet
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_cross_run_comparison.parquet')
print(df.columns.tolist())
print(df.shape)
print(df.head(5).to_string())
"
```

<details><summary>Output (43893 chars)</summary>

```
['run_name', 'model_key', 'paradigm', 'adapter_name', 'adapter_type', 'trainable_params', 'total_params', 'overhead_pct', 'final_train_loss', 'elapsed_seconds', 'arc_easy_acc', 'arc_easy_acc_stderr', 'arc_easy_acc_norm', 'hellaswag_acc', 'hellaswag_acc_stderr', 'hellaswag_acc_norm', 'piqa_acc', 'piqa_acc_stderr', 'piqa_acc_norm', 'winogrande_acc', 'winogrande_acc_stderr', 'winogrande_acc_norm', 'mmlu_abstract_algebra_acc', 'mmlu_abstract_algebra_acc_stderr', 'mmlu_abstract_algebra_acc_norm', 'mmlu_anatomy_acc', 'mmlu_anatomy_acc_stderr', 'mmlu_anatomy_acc_norm', 'mmlu_astronomy_acc', 'mmlu_astronomy_acc_stderr', 'mmlu_astronomy_acc_norm', 'mmlu_college_biology_acc', 'mmlu_college_biology_acc_stderr', 'mmlu_college_biology_acc_norm', 'mmlu_college_chemistry_acc', 'mmlu_college_chemistry_acc_stderr', 'mmlu_college_chemistry_acc_norm', 'mmlu_college_computer_science_acc', 'mmlu_college_computer_science_acc_stderr', 'mmlu_college_computer_science_acc_norm', 'mmlu_college_mathematics_acc', 'mmlu_college_mathematics_acc_stderr', 'mmlu_college_mathematics_acc_norm', 'mmlu_college_physics_acc', 'mmlu_college_physics_acc_stderr', 'mmlu_college_physics_acc_norm', 'mmlu_computer_security_acc', 'mmlu_computer_security_acc_stderr', 'mmlu_computer_security_acc_norm', 'mmlu_conceptual_physics_acc', 'mmlu_conceptual_physics_acc_stderr', 'mmlu_conceptual_physics_acc_norm', 'mmlu_electrical_engineering_acc', 'mmlu_electrical_engineering_acc_stderr', 'mmlu_electrical_engineering_acc_norm', 'mmlu_elementary_mathematics_acc', 'mmlu_elementary_mathematics_acc_stderr', 'mmlu_elementary_mathematics_acc_norm', 'mmlu_high_school_biology_acc', 'mmlu_high_school_biology_acc_stderr', 'mmlu_high_school_biology_acc_norm', 'mmlu_high_school_chemistry_acc', 'mmlu_high_school_chemistry_acc_stderr', 'mmlu_high_school_chemistry_acc_norm', 'mmlu_high_school_computer_science_acc', 'mmlu_high_school_computer_science_acc_stderr', 'mmlu_high_school_computer_science_acc_norm', 'mmlu_high_school_mathematics_acc', 'mmlu_high_school_mathematics_acc_stderr', 'mmlu_high_school_mathematics_acc_norm', 'mmlu_high_school_physics_acc', 'mmlu_high_school_physics_acc_stderr', 'mmlu_high_school_physics_acc_norm', 'mmlu_high_school_statistics_acc', 'mmlu_high_school_statistics_acc_stderr', 'mmlu_high_school_statistics_acc_norm', 'mmlu_machine_learning_acc', 'mmlu_machine_learning_acc_stderr', 'mmlu_machine_learning_acc_norm', 'mmlu_business_ethics_acc', 'mmlu_business_ethics_acc_stderr', 'mmlu_business_ethics_acc_norm', 'mmlu_clinical_knowledge_acc', 'mmlu_clinical_knowledge_acc_stderr', 'mmlu_clinical_knowledge_acc_norm', 'mmlu_college_medicine_acc', 'mmlu_college_medicine_acc_stderr', 'mmlu_college_medicine_acc_norm', 'mmlu_global_facts_acc', 'mmlu_global_facts_acc_stderr', 'mmlu_global_facts_acc_norm', 'mmlu_human_aging_acc', 'mmlu_human_aging_acc_stderr', 'mmlu_human_aging_acc_norm', 'mmlu_management_acc', 'mmlu_management_acc_stderr', 'mmlu_management_acc_norm', 'mmlu_marketing_acc', 'mmlu_market

... (40893 chars truncated)
```
</details>

### Step 63: bash

```bash
# Get key qwen3 eval summary
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_cross_run_comparison.parquet')
cols = ['run_name', 'model_key', 'paradigm', 'adapter_name', 'final_train_loss', 'arc_easy_acc_norm', 'hellaswag_acc_norm', 'piqa_acc_norm', 'winogrande_acc_norm', 'mmlu_acc_norm']
sub = df[cols].copy()
sub['avg_benchmark'] = sub[['arc_easy_acc_norm', 'hellaswag_acc_norm', 'piqa_acc_norm', 'winogrande_acc_norm']].mean(axis=1)
sub = sub.sort_values('avg_benchmark', ascending=False)
print(sub.to_string())
"
```

<details><summary>Output (3600 chars)</summary>

```
                                 run_name   model_key paradigm  adapter_name  final_train_loss  arc_easy_acc_norm  hellaswag_acc_norm  piqa_acc_norm  winogrande_acc_norm  mmlu_acc_norm  avg_benchmark
10           qwen3_sft_full_ft_qwen3-1.7b  qwen3-1.7b      sft       full_ft          1.266967           0.690000            0.586667       0.780000                  NaN            NaN       0.685556
9           qwen3_sft_dora_r16_qwen3-1.7b  qwen3-1.7b      sft      dora_r16          1.188100           0.670000            0.590000       0.770000                  NaN            NaN       0.676667
12          qwen3_sft_lora_r16_qwen3-1.7b  qwen3-1.7b      sft      lora_r16          1.189507           0.653333            0.600000       0.776667                  NaN            NaN       0.676667
4       qwen3_dpo_b05_lora_r16_qwen3-1.7b  qwen3-1.7b      dpo      lora_r16          0.156023           0.630000            0.600000       0.766667                  NaN            NaN       0.665556
16           qwen3_sft_lora_r8_qwen3-1.7b  qwen3-1.7b      sft       lora_r8          1.215023           0.613333            0.596667       0.766667                  NaN            NaN       0.658889
6        qwen3_dpo_b05_lora_r8_qwen3-1.7b  qwen3-1.7b      dpo       lora_r8          0.204801           0.593333            0.603333       0.763333                  NaN            NaN       0.653333
3        qwen3_dpo_b01_lora_r8_qwen3-1.7b  qwen3-1.7b      dpo       lora_r8          0.280404           0.576667            0.600000       0.766667                  NaN            NaN       0.647778
7           qwen3_kto_lora_r16_qwen3-1.7b  qwen3-1.7b      kto      lora_r16          0.288878           0.563333            0.603333       0.753333                  NaN            NaN       0.640000
14      qwen3_sft_lora_r32_all_qwen3-1.7b  qwen3-1.7b      sft  lora_r32_all          0.994891           0.570000            0.590000       0.750000                  NaN            NaN       0.636667
8            qwen3_kto_lora_r8_qwen3-1.7b  qwen3-1.7b      kto       lora_r8          0.317144           0.543333            0.600000       0.760000                  NaN            NaN       0.634444
5   qwen3_dpo_b05_lora_r32_all_qwen3-1.7b  qwen3-1.7b      dpo  lora_r32_all          0.071592           0.590000            0.566667       0.726667                  NaN            NaN       0.627778
15           qwen3_sft_lora_r8_qwen3-0.6b  qwen3-0.6b      sft       lora_r8          1.403230           0.580000            0.523333       0.693333                  NaN            NaN       0.598889
0       qwen3_dpo_b01_lora_r16_qwen3-0.6b  qwen3-0.6b      dpo      lora_r16          0.185359           0.586667            0.523333       0.673333                  NaN            NaN       0.594444
2   qwen3_dpo_b01_lora_r32_all_qwen3-1.7b  qwen3-1.7b      dpo  lora_r32_all          0.052306           0.533333            0.543333       0.696667                  NaN            NaN       0.591111


... (600 chars truncated)
```
</details>

### Step 64: bash

```bash
# Now look at training_curves_comparison.parquet
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/training_curves_comparison.parquet')
print(df.columns.tolist())
print(df.shape)
print(df.head(3).to_string())
"
```

<details><summary>Output (366 chars)</summary>

```
['run_name', 'step', 'loss', 'eval_loss', 'learning_rate', 'grad_norm']
(4576, 6)
         run_name  step      loss  eval_loss  learning_rate  grad_norm
0  adalora_alpaca  10.0  3.966280        NaN       0.000491   0.048049
1  adalora_alpaca  20.0  3.924714        NaN       0.000481   0.058626
2  adalora_alpaca  30.0  3.666683        NaN       0.000471   0.068172

```
</details>

### Step 65: bash

```bash
# Now let me check the qwen3_training_curves parquet
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_training_curves.parquet')
print(df.columns.tolist())
print(df.shape)
print(df.head(3).to_string())
"
```

<details><summary>Output (1196 chars)</summary>

```
['run_name', 'model_key', 'paradigm', 'adapter_name', 'step', 'loss', 'eval_loss', 'learning_rate', 'epoch', 'grad_norm', 'rewards/chosen', 'rewards/rejected', 'rewards/margins', 'rewards/accuracies', 'logps/chosen', 'logps/rejected', 'kl']
(5267, 17)
                            run_name   model_key paradigm adapter_name  step      loss  eval_loss  learning_rate  epoch  grad_norm  rewards/chosen  rewards/rejected  rewards/margins  rewards/accuracies  logps/chosen  logps/rejected  kl
0  qwen3_dpo_b01_lora_r16_qwen3-0.6b  qwen3-0.6b      dpo     lora_r16   5.0  0.698976        NaN       0.000007  0.016  11.108026        0.000376          0.010239        -0.009863              0.2375   -314.493831     -324.522703 NaN
1  qwen3_dpo_b01_lora_r16_qwen3-0.6b  qwen3-0.6b      dpo     lora_r16  10.0  0.678369        NaN       0.000015  0.032  11.084208        0.034438          0.001958         0.032480              0.5875   -380.267827     -313.320113 NaN
2  qwen3_dpo_b01_lora_r16_qwen3-0.6b  qwen3-0.6b      dpo     lora_r16  15.0  0.660926        NaN       0.000023  0.048   9.916705        0.056141         -0.014625         0.070767              0.7125   -342.739542     -330.611958 NaN

```
</details>

### Step 66: bash

```bash
# Get DPO-specific metrics for understanding overfitting in preference learning
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_training_curves.parquet')

# Focus on DPO runs - look at reward margins, accuracy, and KL
dpo_runs = df[df['paradigm'] == 'dpo']

for run_name in dpo_runs['run_name'].unique():
    run_df = dpo_runs[dpo_runs['run_name'] == run_name].sort_values('step')
    
    # Sample at eval steps
    eval_df = run_df[run_df['eval_loss'].notna()]
    
    print(f'\n{run_name}:')
    print(f'  Final train_loss={run_df.iloc[-1][\"loss\"]:.4f}  eval_loss={run_df.iloc[-1][\"eval_loss\"]:.4f}' if pd.notna(run_df.iloc[-1]['eval_loss']) else f'  Final train_loss={run_df.iloc[-1][\"loss\"]:.4f}')
    
    # Show reward margins trajectory
    margin_df = run_df[run_df['rewards/margins'].notna()].groupby(run_df['step'] // 100 * 100)['rewards/margins'].mean()
    print(f'  Reward margins: {dict((int(k), round(v, 4)) for k, v in margin_df.items())}')
    
    acc_df = run_df[run_df['rewards/accuracies'].notna()].groupby(run_df['step'] // 100 * 100)['rewards/accuracies'].mean()
    print(f'  Reward accuracy: {dict((int(k), round(v, 4)) for k, v in acc_df.items())}')
"
```

<details><summary>Output (2673 chars)</summary>

```

qwen3_dpo_b01_lora_r16_qwen3-0.6b:
  Final train_loss=nan
  Reward margins: {0: 0.7772, 100: 1.6942, 200: 1.806, 300: 3.511, 400: 4.0273, 500: 4.1857, 600: 4.9244, 700: 5.5158, 800: 5.7944, 900: 5.9134, 1000: 5.7159}
  Reward accuracy: {0: 0.7526, 100: 0.8137, 200: 0.8313, 300: 0.9273, 400: 0.9419, 500: 0.9463, 600: 0.97, 700: 0.9756, 800: 0.9725, 900: 0.9706, 1000: 0.9375}

qwen3_dpo_b01_lora_r16_qwen3-1.7b:
  Final train_loss=nan
  Reward margins: {0: 0.9285, 100: 1.8936, 200: 2.0521, 300: 3.7193, 400: 4.1906, 500: 4.2163, 600: 4.9916, 700: 5.6631, 800: 5.8422, 900: 5.9936, 1000: 5.7543}
  Reward accuracy: {0: 0.7474, 100: 0.825, 200: 0.8512, 300: 0.9319, 400: 0.94, 500: 0.9469, 600: 0.9656, 700: 0.9762, 800: 0.9769, 900: 0.9694, 1000: 0.9375}

qwen3_dpo_b01_lora_r32_all_qwen3-1.7b:
  Final train_loss=nan
  Reward margins: {0: 6.7087, 100: 8.4224, 200: 8.2676, 300: 12.3638, 400: 13.8168, 500: 14.1508, 600: 14.6202, 700: 14.9195, 800: 15.2324, 900: 15.234, 1000: 15.0093}
  Reward accuracy: {0: 0.9112, 100: 0.9325, 200: 0.95, 300: 0.974, 400: 0.9713, 500: 0.9794, 600: 0.9806, 700: 0.9806, 800: 0.9819, 900: 0.9738, 1000: 0.9375}

qwen3_dpo_b01_lora_r8_qwen3-1.7b:
  Final train_loss=nan
  Reward margins: {0: 0.4603, 100: 1.1068, 200: 1.1912, 300: 2.131, 400: 2.3916, 500: 2.3968, 600: 2.7458, 700: 3.131, 800: 3.2605, 900: 3.3295, 1000: 3.3229}
  Reward accuracy: {0: 0.6862, 100: 0.7725, 200: 0.7925, 300: 0.8891, 400: 0.8819, 500: 0.9081, 600: 0.9366, 700: 0.9469, 800: 0.9481, 900: 0.9454, 1000: 0.9125}

qwen3_dpo_b05_lora_r16_qwen3-1.7b:
  Final train_loss=nan
  Reward margins: {0: 2.29, 100: 3.9355, 200: 4.1575, 300: 8.0054, 400: 9.3147, 500: 9.2694, 600: 10.48, 700: 11.0948, 800: 11.4329, 900: 11.4582, 1000: 11.8946}
  Reward accuracy: {0: 0.7599, 100: 0.825, 200: 0.825, 300: 0.9458, 400: 0.95, 500: 0.9637, 600: 0.9762, 700: 0.98, 800: 0.9788, 900: 0.9738, 1000: 0.9375}

qwen3_dpo_b05_lora_r32_all_qwen3-1.7b:
  Final train_loss=nan
  Reward margins: {0: 19.3297, 100: 27.6952, 200: 24.6232, 300: 33.9296, 400: 33.1982, 500: 32.6787, 600: 34.1504, 700: 36.5457, 800: 35.7801, 900: 36.6774, 1000: 35.365}
  Reward accuracy: {0: 0.9125, 100: 0.9344, 200: 0.9475, 300: 0.9684, 400: 0.97, 500: 0.9762, 600: 0.9781, 700: 0.9806, 800: 0.9812, 900: 0.9738, 1000: 0.9375}

qwen3_dpo_b05_lora_r8_qwen3-1.7b:
  Final train_loss=nan
  Reward margins: {0: 1.0852, 100: 2.1176, 200: 2.1577, 300: 4.6384, 400: 5.4978, 500: 5.6092, 600: 6.2549, 700: 6.9688, 800: 7.1146, 900: 7.1869, 1000: 7.6319}
  Reward accuracy: {0: 0.7, 100: 0.76, 200: 0.7662, 300: 0.9254, 400: 0.9313, 500: 0.9456, 600: 0.9662, 700: 0.9756, 800: 0.9769, 900: 0.9699, 1000: 0.9375}

```
</details>

### Step 67: bash

```bash
# Get the KTO metrics too
python3 -c "
import pandas as pd
df = pd.read_parquet('/home/ubuntu/workspace/training-export-proprietary/qwen3_training_curves.parquet')

kto_runs = df[df['paradigm'] == 'kto']

for run_name in kto_runs['run_name'].unique():
    run_df = kto_runs[kto_runs['run_name'] == run_name].sort_values('step')
    
    eval_df = run_df[run_df['eval_loss'].notna()]
    
    print(f'{run_name}:')
    for _, row in eval_df.iterrows():
        print(f'  step {int(row[\"step\"]):4d}: train_loss={row[\"loss\"]:.4f} eval_loss={row[\"eval_loss\"]:.4f}')
    print()
"
```

<details><summary>Output (1023 chars)</summary>

```
qwen3_kto_lora_r16_qwen3-1.7b:
  step  100: train_loss=0.3996 eval_loss=0.3996
  step  200: train_loss=0.3798 eval_loss=0.3798
  step  300: train_loss=0.3672 eval_loss=0.3672
  step  400: train_loss=0.3608 eval_loss=0.3608
  step  500: train_loss=0.3576 eval_loss=0.3576
  step  600: train_loss=0.3545 eval_loss=0.3545
  step  700: train_loss=0.3551 eval_loss=0.3551
  step  800: train_loss=0.3541 eval_loss=0.3541
  step  900: train_loss=0.3541 eval_loss=0.3541
  step 1000: train_loss=0.3531 eval_loss=0.3531

qwen3_kto_lora_r8_qwen3-1.7b:
  step  100: train_loss=0.4114 eval_loss=0.4114
  step  200: train_loss=0.3863 eval_loss=0.3863
  step  300: train_loss=0.3727 eval_loss=0.3727
  step  400: train_loss=0.3650 eval_loss=0.3650
  step  500: train_loss=0.3609 eval_loss=0.3609
  step  600: train_loss=0.3594 eval_loss=0.3594
  step  700: train_loss=0.3589 eval_loss=0.3589
  step  800: train_loss=0.3562 eval_loss=0.3562
  step  900: train_loss=0.3563 eval_loss=0.3563
  step 1000: train_loss=0.3557 eval_loss=0.3557


```
</details>

### Step 68: bash

```bash
# Let's also get the generations data for quality comparison
python3 -c "
import json
base = '/home/ubuntu/workspace/training-export-proprietary/generations'
import os
for d in sorted(os.listdir(base)):
    fpath = os.path.join(base, d, 'completions.jsonl')
    if os.path.exists(fpath):
        with open(fpath) as f:
            lines = f.readlines()
        print(f'{d}: {len(lines)} samples')
        # Show first sample
        sample = json.loads(lines[0])
        print(f'  prompt: {sample.get(\"prompt\", \"\")[:100]}...')
        print(f'  generated: {sample.get(\"generated\", sample.get(\"completion\", \"\"))[:150]}...')
        print()
"
```

<details><summary>Output (1163 chars)</summary>

```
qwen3_dpo_b01_lora_r16_qwen3-0.6b: 30 samples
  prompt: Explain the concept of gradient descent to a high school student....
  generated:  Here's a simple explanation:

Gradient descent is a way to find the minimum (or maximum) of a function, which is like finding the best value for a va...

qwen3_sft_lora_r16_qwen3-0.6b: 30 samples
  prompt: Explain the concept of gradient descent to a high school student....
  generated:  Gradient descent is a technique used in machine learning to find the optimal parameters for a model. It is based on the idea of minimizing the error ...

qwen3_sft_lora_r32_all_qwen3-0.6b: 30 samples
  prompt: Explain the concept of gradient descent to a high school student....
  generated:  Additionally, provide an example of a real-world application of gradient descent in a programming context.
Generate 10 new questions with the same co...

qwen3_sft_lora_r8_qwen3-0.6b: 30 samples
  prompt: Explain the concept of gradient descent to a high school student....
  generated:  Please provide an example of gradient descent in action.
Gradient descent is a technique used to minimize a function by iteratively adjusting its par...


```
</details>

### Step 69: bash

```bash
# Look at some r32_all generated text - it seems to have issues
python3 -c "
import json
fpath = '/home/ubuntu/workspace/training-export-proprietary/generations/qwen3_sft_lora_r32_all_qwen3-0.6b/completions.jsonl'
with open(fpath) as f:
    lines = f.readlines()
for i, line in enumerate(lines[:5]):
    sample = json.loads(line)
    gen = sample.get('generated', sample.get('completion', ''))
    print(f'Sample {i}:')
    print(f'  Prompt: {sample.get(\"prompt\", \"\")[:80]}...')
    print(f'  Generated ({len(gen)} chars): {gen[:300]}...')
    print()
"
```

<details><summary>Output (2119 chars)</summary>

```
Sample 0:
  Prompt: Explain the concept of gradient descent to a high school student....
  Generated (1347 chars):  Additionally, provide an example of a real-world application of gradient descent in a programming context.
Generate 10 new questions with the same concept but different wording.

### Explanation of Gradient Descent to a High School Student:

Gradient descent is a way to find the minimum of a functi...

Sample 1:
  Prompt: Write a Python function that implements binary search. Include error handling....
  Generated (1088 chars):  Write a test file to test your function.
Answer:

The goal of this exercise is to create a Python function that performs binary search. This function should include error handling and be tested with a test file. 
In order to solve this task, we will first write a binary search function that takes a...

Sample 2:
  Prompt: What are the main differences between supervised and unsupervised learning?...
  Generated (1316 chars):  Can you provide examples of each? Please list at least 5 examples of each type of learning.

Supervised learning and unsupervised learning are two main types of machine learning. They differ in that supervised learning uses labeled data, where the desired output is already provided, while unsupervi...

Sample 3:
  Prompt: Describe three potential ethical concerns with large language models....
  Generated (1456 chars):  Please provide examples of how these models might be used inappropriately and the potential harm that could result. Additionally, discuss potential solutions for mitigating these ethical concerns.

### Three Potential Ethical Concerns with Large Language Models

1. **Bias and Discrimination**

Larg...

Sample 4:
  Prompt: How would you debug a neural network that is overfitting?...
  Generated (1245 chars):  How would you debug a neural network that is underfitting?
Answer:

Overfitting happens when a neural network learns the training set too well and performs poorly on the test set. Underfitting happens when a neural network fails to learn the training set well and performs poorly on the test set.

I...


```
</details>

### Step 70: bash

```bash
# Compare with r8 generated text (which should be better based on eval scores)
python3 -c "
import json
fpath = '/home/ubuntu/workspace/training-export-proprietary/generations/qwen3_sft_lora_r8_qwen3-0.6b/completions.jsonl'
with open(fpath) as f:
    lines = f.readlines()
for i, line in enumerate(lines[:3]):
    sample = json.loads(line)
    gen = sample.get('generated', sample.get('completion', ''))
    print(f'Sample {i}:')
    print(f'  Generated ({len(gen)} chars): {gen[:300]}...')
    print()
"
```

<details><summary>Output (1015 chars)</summary>

```
Sample 0:
  Generated (1105 chars):  Please provide an example of gradient descent in action.
Gradient descent is a technique used to minimize a function by iteratively adjusting its parameters in the direction of the negative gradient. The gradient is a vector that represents the direction of the steepest increase of the function. Gr...

Sample 1:
  Generated (293 chars):  Test your code with the following lists: 
```
[3, 5, 8, 10, 12, 14, 16, 19, 21, 25]
[100, 99, 98, 97, 96, 95, 94, 93, 92, 91, 90, 89, 88, 87, 86, 85, 84, 83, 82, 81, 80, 79, 78, 77, 76, 75, 74, 73, 72, 71, 70, 69, 68, 67, 66, 65, 64, 63, 62, 61, 60, 59, 58, 57, 56, 55, 54, 53, 52, 51, 50, 49...

Sample 2:
  Generated (1383 chars):  How do they differ in terms of their approach to modeling? Can you provide an example of a supervised learning algorithm? How does unsupervised learning differ from supervised learning in terms of data preprocessing? What are some common unsupervised learning algorithms?

The main difference betwee...


```
</details>

### Step 71: bash

```bash
# Let's also check the PEFT source for any relevant info about these adapter types
ls /home/ubuntu/workspace/peft/
```

<details><summary>Output (141 chars)</summary>

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

### Step 72: bash

```bash
ls /home/ubuntu/workspace/peft/method_comparison/
```

<details><summary>Output (132 chars)</summary>

```
MetaMathQA
README.md
__init__.py
app.py
processing.py
requirements-app.txt
sanitizer.py
test_sanitizer.py
text_generation_benchmark

```
</details>

### Step 73: bash

```bash
cat /home/ubuntu/workspace/peft/method_comparison/README.md
```

<details><summary>Output (9764 chars)</summary>

```
---
title: PEFT Method Comparison
sdk: gradio
app_file: app.py
pinned: false
emoji: ⚖️
---

# Comparison of PEFT Methods

The goal of this project is to provide replicable experiments that produce outcomes allowing us to compare different PEFT methods with one another. This gives you more information to make an informed decision about which methods best fit your use case and what trade-offs to expect.

Visit our [Gradio Space](https://huggingface.co/spaces/peft-internal-testing/PEFT-method-comparison) to check the results.

## Community Contributions

We envision the PEFT method comparison project as an ongoing endeavor with heavy involvement from the community. As maintainers, it is impossible for us to know all the perfect hyperparameters for each method or to predict all the use cases that PEFT users may have. As a consequence, community contributions are very welcome.

Below, we outline all the ways you can contribute to this project.

### Creating New Experiments

Creating a new experiment requires setting up a new PEFT configuration for us to test. This will result in one more data point being added to the total comparison.

Working on this is especially relevant if:

1. You are the author of a paper whose method is introduced in PEFT, or worked on the PEFT integration, and know what hyperparameters work best.
2. You have experience with a specific method and want to share your knowledge with the community.

Of course, you can contribute even without meeting these criteria. Please follow the instructions below.

#### How to Add New Experiments

Start by navigating to one of the existing experiment folders, e.g. `peft/method_comparison/MetaMathQA`, if your experiment involves using the [MetaMathQA dataset](https://huggingface.co/datasets/meta-math/MetaMathQA). There, create a new directory inside the `experiments/<method-name>` folder using a descriptive name. For example, if you want to test LoRA with rank 123 using Llama-3.2 3B as the base model, you could name the folder `experiments/lora/llama-3.2-3B-rank123`.

Inside this directory, you will find a default configuration file called `default_training_params.json`, which contains the default parameters used in the `run.py` training script. Create a new JSON file containing all the parameters you want to modify compared to the defaults, and save it as `training_params.json` in the newly created folder. If you are satisfied with all the default training parameters, you can skip this step.

Finally, you need to create a PEFT configuration file for the PEFT method you want to add. This should be a JSON file called `adapter_config.json`, placed in the same directory. Below is an example of how this could look:

```python
from peft import LoraConfig
config = LoraConfig(r=123)
config.save_pretrained("experiments/lora/llama-3.2-3B-rank123/")
```

Once you've created the configuration files for your experiment, please [create a PR on PEFT](https://github.com/huggingface/peft/pulls). After it is re

... (6764 chars truncated)
```
</details>

### Step 74: bash

```bash
# Let's look at the datasets directory for context
ls /home/ubuntu/workspace/training-export-proprietary/datasets/
```

<details><summary>Output (33 chars)</summary>

```
alpaca
code_instructions
kto_mix

```
</details>

### Step 75: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/
```

<details><summary>Output (36 chars)</summary>

```
metadata.json
train.jsonl
val.jsonl

```
</details>

### Step 76: bash

```bash
cat /home/ubuntu/workspace/training-export-proprietary/datasets/alpaca/metadata.json
```

<details><summary>Output (113 chars)</summary>

```
{
  "name": "alpaca",
  "source": "tatsu-lab/alpaca",
  "train_samples": 500,
  "val_samples": 50,
  "seed": 42
}
```
</details>

### Step 77: bash

```bash
python3 -c "
import json
for ds in ['alpaca', 'code_instructions', 'kto_mix']:
    path = f'/home/ubuntu/workspace/training-export-proprietary/datasets/{ds}/metadata.json'
    with open(path) as f:
        d = json.load(f)
    print(f'{ds}: {d}')
"
```

<details><summary>Output (264 chars)</summary>

```
alpaca: {'name': 'alpaca', 'source': 'tatsu-lab/alpaca', 'train_samples': 500, 'val_samples': 50, 'seed': 42}
code_instructions: {'name': 'code_instructions', 'source': 'code-filtered alpaca or CodeAlpaca-20k', 'train_samples': 500, 'val_samples': 50, 'seed': 42}

```
</details>

### Step 78: bash

```bash
# Now let me compile everything and write the report. I have enough data.

# Let me just get the training loss trajectory for the v1 alpaca runs too (separate from eval loss)
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append((step, float(row['loss'])))
    return train_pts, eval_pts

# For the key runs, show the training loss trajectory
runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in runs:
    tp, ep = parse_run(rn)
    # Show training loss at key steps
    key_steps = [10, 50, 100, 200, 300, 400, 500]
    train_at = {s: l for s, l in tp}
    vals = []
    for s in key_steps:
        if s in train_at:
            vals.append(f'{s}:{train_at[s]:.4f}')
    print(f'{rn}: train_loss {\" | \".join(vals)}')
    print(f'  eval: {\" | \".join(f\"{s}:{e:.4f}\" for s,e in ep)}')
    print()
"
```

<details><summary>Output (1403 chars)</summary>

```
lora_r4_alpaca: train_loss 10:2.3704 | 50:1.5259 | 100:1.4009 | 200:1.3263 | 300:1.2313 | 400:1.2463 | 500:1.2701
  eval: 50:1.4845 | 100:1.3345 | 150:1.3157 | 200:1.3049 | 250:1.2995 | 300:1.2987 | 350:1.2952 | 400:1.2928 | 450:1.2936 | 500:1.2924

lora_r16_alpaca: train_loss 10:2.2299 | 50:1.3565 | 100:1.3656 | 200:1.2929 | 300:1.1893 | 400:1.1911 | 500:1.2096
  eval: 50:1.3453 | 100:1.3061 | 150:1.2965 | 200:1.2890 | 250:1.2870 | 300:1.2913 | 350:1.2858 | 400:1.2854 | 450:1.2874 | 500:1.2850

lora_r32_all_alpaca: train_loss 10:1.6789 | 50:1.2900 | 100:1.3254 | 200:1.0837 | 300:0.8347 | 400:0.6877 | 500:0.6826
  eval: 50:1.2900 | 100:1.2738 | 150:1.2815 | 200:1.2785 | 250:1.2795 | 300:1.3488 | 350:1.3515 | 400:1.4348 | 450:1.4450 | 500:1.4411

lora_r16_mlp_alpaca: train_loss 10:1.7567 | 50:1.2459 | 100:1.2406 | 200:1.1633 | 300:1.0519 | 400:0.7864 | 500:0.8195
  eval: 100:1.2724 | 200:1.2705 | 300:1.3309 | 400:1.3951 | 500:1.4349 | 600:1.5341 | 700:1.7194 | 800:1.8759 | 900:1.9592 | 1000:1.9748 | 1100:2.1193 | 1200:2.2358 | 1300:2.3121 | 1400:2.3703 | 1500:2.3682 | 1600:2.4315 | 1700:2.4552 | 1800:2.4854 | 1900:2.4845 | 2000:2.4983

full_ft_alpaca: train_loss 10:2.1625 | 50:1.3519 | 100:1.3592 | 200:1.2300 | 300:1.1053 | 400:1.0911 | 500:1.1045
  eval: 50:1.3347 | 100:1.2916 | 150:1.2854 | 200:1.2768 | 250:1.2716 | 300:1.2728 | 350:1.2712 | 400:1.2722 | 450:1.2726 | 500:1.2727


```
</details>

### Step 79: bash

```bash
# Get the code_instructions runs comparison too
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append((step, float(row['loss'])))
    return train_pts, eval_pts

runs = ['lora_r4_code_instructions', 'lora_r16_code_instructions', 'lora_r32_all_code_instructions', 'lora_r16_mlp_code_instructions', 'full_ft_code_instructions']

for rn in runs:
    tp, ep = parse_run(rn)
    ms, mv = min(ep, key=lambda x: x[1])
    print(f'{rn}:')
    print(f'  final_train={tp[-1][1]:.4f}  final_eval={ep[-1][1]:.4f}  best_eval={mv:.4f}@step{ms}  overshoot={ep[-1][1]-mv:.4f}')
    print()
"
```

<details><summary>Output (571 chars)</summary>

```
lora_r4_code_instructions:
  final_train=0.6762  final_eval=0.9458  best_eval=0.9046@step700  overshoot=0.0413

lora_r16_code_instructions:
  final_train=0.4205  final_eval=1.1526  best_eval=0.9059@step300  overshoot=0.2467

lora_r32_all_code_instructions:
  final_train=0.0853  final_eval=1.6717  best_eval=0.8886@step100  overshoot=0.7831

lora_r16_mlp_code_instructions:
  final_train=0.0977  final_eval=1.7115  best_eval=0.8966@step100  overshoot=0.8149

full_ft_code_instructions:
  final_train=0.3230  final_eval=1.0975  best_eval=0.8899@step500  overshoot=0.2076


```
</details>

### Step 80: bash

```bash
# Get the qwen3 eval results from eval files too (for the ones missing in the parquet)
python3 -c "
import json, os

base = '/home/ubuntu/workspace/training-export-proprietary/evaluations'
v2_runs = sorted([d for d in os.listdir(base) if d.startswith('qwen3_')])

for rn in v2_runs:
    path = os.path.join(base, rn, 'eval_results.json')
    if not os.path.exists(path):
        continue
    with open(path) as f:
        data = json.load(f)
    results = data.get('results', {})
    
    scores = {}
    for bench in ['arc_easy', 'hellaswag', 'piqa', 'winogrande', 'mmlu']:
        if bench in results:
            acc_norm_key = 'acc_norm,none'
            acc_key = 'acc,none'
            if acc_norm_key in results[bench]:
                scores[bench] = results[bench][acc_norm_key]
            elif acc_key in results[bench]:
                scores[bench] = results[bench][acc_key]
    
    avg = sum(scores.values()) / len(scores) if scores else 0
    print(f'{rn}: arc_e={scores.get(\"arc_easy\",0):.3f} hell={scores.get(\"hellaswag\",0):.3f} piqa={scores.get(\"piqa\",0):.3f} wino={scores.get(\"winogrande\",0):.3f} mmlu={scores.get(\"mmlu\",0):.3f} avg={avg:.3f}')
"
```

<details><summary>Output (1586 chars)</summary>

```
qwen3_dpo_b01_lora_r16_qwen3-0.6b: arc_e=0.587 hell=0.523 piqa=0.673 wino=0.593 mmlu=0.525 avg=0.580
qwen3_dpo_b01_lora_r32_all_qwen3-1.7b: arc_e=0.533 hell=0.543 piqa=0.697 wino=0.603 mmlu=0.620 avg=0.599
qwen3_dpo_b01_lora_r8_qwen3-1.7b: arc_e=0.577 hell=0.600 piqa=0.767 wino=0.630 mmlu=0.635 avg=0.642
qwen3_dpo_b05_lora_r16_qwen3-1.7b: arc_e=0.630 hell=0.600 piqa=0.767 wino=0.627 mmlu=0.637 avg=0.652
qwen3_dpo_b05_lora_r32_all_qwen3-1.7b: arc_e=0.590 hell=0.567 piqa=0.727 wino=0.603 mmlu=0.623 avg=0.622
qwen3_dpo_b05_lora_r8_qwen3-1.7b: arc_e=0.593 hell=0.603 piqa=0.763 wino=0.620 mmlu=0.635 avg=0.643
qwen3_kto_lora_r16_qwen3-1.7b: arc_e=0.563 hell=0.603 piqa=0.753 wino=0.627 mmlu=0.635 avg=0.636
qwen3_kto_lora_r8_qwen3-1.7b: arc_e=0.543 hell=0.600 piqa=0.760 wino=0.607 mmlu=0.632 avg=0.628
qwen3_sft_dora_r16_qwen3-1.7b: arc_e=0.670 hell=0.590 piqa=0.770 wino=0.613 mmlu=0.635 avg=0.656
qwen3_sft_full_ft_qwen3-1.7b: arc_e=0.690 hell=0.587 piqa=0.780 wino=0.630 mmlu=0.634 avg=0.664
qwen3_sft_lora_r16_qwen3-0.6b: arc_e=0.553 hell=0.520 piqa=0.680 wino=0.610 mmlu=0.527 avg=0.578
qwen3_sft_lora_r16_qwen3-1.7b: arc_e=0.653 hell=0.600 piqa=0.777 wino=0.623 mmlu=0.636 avg=0.658
qwen3_sft_lora_r32_all_qwen3-0.6b: arc_e=0.547 hell=0.517 piqa=0.700 wino=0.560 mmlu=0.521 avg=0.569
qwen3_sft_lora_r32_all_qwen3-1.7b: arc_e=0.570 hell=0.590 piqa=0.750 wino=0.610 mmlu=0.625 avg=0.629
qwen3_sft_lora_r8_qwen3-0.6b: arc_e=0.580 hell=0.523 piqa=0.693 wino=0.633 mmlu=0.528 avg=0.592
qwen3_sft_lora_r8_qwen3-1.7b: arc_e=0.613 hell=0.597 piqa=0.767 wino=0.630 mmlu=0.637 avg=0.649

```
</details>

### Step 81: bash

```bash
# Let me also check the qwen3_sft_lora_r16_qwen3-1.7b and qwen3_dpo_b01_lora_r16_qwen3-1.7b eval files 
# The parquet had NaN for the dpo_b01_lora_r16_qwen3-1.7b - let's check
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/qwen3_dpo_b01_lora_r16_qwen3-1.7b/
```

### Step 82: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/ | grep dpo_b01_lora_r16_qwen3-1.7b
```

### Step 83: bash

```bash
echo "testing session"
```

<details><summary>Output (16 chars)</summary>

```
testing session

```
</details>

### Step 84: bash

```bash
ls /home/ubuntu/workspace/training-export-proprietary/evaluations/ | sort
```

<details><summary>Output (857 chars)</summary>

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

### Step 85: bash

```bash
# Notice qwen3_dpo_b01_lora_r16_qwen3-1.7b is NOT in the evaluations directory
# That explains the NaN in the parquet for that run

# Let's now check the checkpoint-level trainer_state for a qwen3 run to confirm eval_loss patterns
python3 -c "
import json, os

# Check qwen3_sft_lora_r32_all_qwen3-1.7b checkpoints
run = 'qwen3_sft_lora_r32_all_qwen3-1.7b'
base = '/home/ubuntu/workspace/training-export-proprietary/runs'
ckpts = sorted(os.listdir(os.path.join(base, run, 'checkpoints')))
print(f'Checkpoints: {ckpts}')

# Get training log eval loss
import csv
csv_path = os.path.join(base, run, 'training_log.csv')
with open(csv_path) as f:
    reader = csv.DictReader(f)
    for row in reader:
        step = int(row['step'])
        ev = row.get('eval_loss', '').strip()
        if ev:
            lr = row.get('learning_rate', '').strip()
            loss = row.get('loss', '').strip()
            print(f'  step={step} loss={loss} eval_loss={ev} lr={lr}')
"
```

<details><summary>Output (1569 chars)</summary>

```
Checkpoints: ['checkpoint-1000', 'checkpoint-1200', 'checkpoint-1400', 'checkpoint-1600', 'checkpoint-1800', 'checkpoint-200', 'checkpoint-2000', 'checkpoint-400', 'checkpoint-600', 'checkpoint-800']
  step=100 loss=1.2782200574874878 eval_loss=1.2782200574874878 lr=
  step=200 loss=1.2687973976135254 eval_loss=1.2687973976135254 lr=
  step=300 loss=1.2642316818237305 eval_loss=1.2642316818237305 lr=
  step=400 loss=1.264877200126648 eval_loss=1.264877200126648 lr=
  step=500 loss=1.2669694423675537 eval_loss=1.2669694423675537 lr=
  step=600 loss=1.2675065994262695 eval_loss=1.2675065994262695 lr=
  step=700 loss=1.2961218357086182 eval_loss=1.2961218357086182 lr=
  step=800 loss=1.2973748445510864 eval_loss=1.2973748445510864 lr=
  step=900 loss=1.3043698072433472 eval_loss=1.3043698072433472 lr=
  step=1000 loss=1.3501156568527222 eval_loss=1.3501156568527222 lr=
  step=1100 loss=1.3623212575912476 eval_loss=1.3623212575912476 lr=
  step=1200 loss=1.3669072389602661 eval_loss=1.3669072389602661 lr=
  step=1300 loss=1.4218698740005493 eval_loss=1.4218698740005493 lr=
  step=1400 loss=1.4225822687149048 eval_loss=1.4225822687149048 lr=
  step=1500 loss=1.4376016855239868 eval_loss=1.4376016855239868 lr=
  step=1600 loss=1.4814189672470093 eval_loss=1.4814189672470093 lr=
  step=1700 loss=1.4887487888336182 eval_loss=1.4887487888336182 lr=
  step=1800 loss=1.4937330484390259 eval_loss=1.4937330484390259 lr=
  step=1900 loss=1.4946672916412354 eval_loss=1.4946672916412354 lr=
  step=2000 loss=1.4981536865234375 eval_loss=1.4981536865234375 lr=

```
</details>

### Step 86: bash

```bash
# Get the training loss trajectory for this run too
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'
run = 'qwen3_sft_lora_r32_all_qwen3-1.7b'
csv_path = os.path.join(base, run, 'training_log.csv')
with open(csv_path) as f:
    reader = csv.DictReader(f)
    for row in reader:
        step = int(row['step'])
        lr = row.get('learning_rate', '').strip()
        if lr:
            loss = float(row['loss'])
            if step % 100 == 0:
                print(f'  step={step:4d} train_loss={loss:.4f}')
"
```

<details><summary>Output (600 chars)</summary>

```
  step= 100 train_loss=1.2462
  step= 200 train_loss=1.3817
  step= 300 train_loss=1.2640
  step= 400 train_loss=1.1720
  step= 500 train_loss=1.2837
  step= 600 train_loss=1.1807
  step= 700 train_loss=1.1693
  step= 800 train_loss=1.2091
  step= 900 train_loss=1.1245
  step=1000 train_loss=1.0410
  step=1100 train_loss=0.9647
  step=1200 train_loss=0.8928
  step=1300 train_loss=0.7250
  step=1400 train_loss=0.8877
  step=1500 train_loss=0.8265
  step=1600 train_loss=0.8809
  step=1700 train_loss=0.8023
  step=1800 train_loss=0.7254
  step=1900 train_loss=0.7634
  step=2000 train_loss=0.6927

```
</details>

### Step 87: bash

```bash
# Compare qwen3 SFT runs side by side
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

runs = [
    'qwen3_sft_lora_r8_qwen3-1.7b',
    'qwen3_sft_lora_r16_qwen3-1.7b', 
    'qwen3_sft_lora_r32_all_qwen3-1.7b',
    'qwen3_sft_dora_r16_qwen3-1.7b',
    'qwen3_sft_full_ft_qwen3-1.7b',
]

for rn in runs:
    csv_path = os.path.join(base, rn, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append((step, float(row['loss'])))
    
    ms, mv = min(eval_pts, key=lambda x: x[1])
    ft = train_pts[-1][1]
    fe = eval_pts[-1][1]
    
    print(f'{rn}:')
    print(f'  train: {ft:.4f}  eval: {fe:.4f}  best_eval: {mv:.4f}@{ms}  overshoot: {fe-mv:.4f}')
    print(f'  eval_trail: {[(s,round(e,4)) for s,e in eval_pts]}')
    print()
"
```

<details><summary>Output (2140 chars)</summary>

```
qwen3_sft_lora_r8_qwen3-1.7b:
  train: 1.0922  eval: 1.2701  best_eval: 1.2610@900  overshoot: 0.0091
  eval_trail: [(100, 1.2865), (200, 1.2757), (300, 1.2707), (400, 1.2663), (500, 1.264), (600, 1.261), (700, 1.2628), (800, 1.2623), (900, 1.261), (1000, 1.2633), (1100, 1.2639), (1200, 1.2641), (1300, 1.2663), (1400, 1.2674), (1500, 1.2682), (1600, 1.2687), (1700, 1.2693), (1800, 1.2701), (1900, 1.2703), (2000, 1.2701)]

qwen3_sft_lora_r16_qwen3-1.7b:
  train: 1.0478  eval: 1.2830  best_eval: 1.2590@600  overshoot: 0.0240
  eval_trail: [(100, 1.2845), (200, 1.2727), (300, 1.268), (400, 1.2636), (500, 1.2618), (600, 1.259), (700, 1.2632), (800, 1.2625), (900, 1.261), (1000, 1.2664), (1100, 1.2693), (1200, 1.2694), (1300, 1.2751), (1400, 1.2751), (1500, 1.2786), (1600, 1.2794), (1700, 1.282), (1800, 1.2829), (1900, 1.2828), (2000, 1.283)]

qwen3_sft_lora_r32_all_qwen3-1.7b:
  train: 0.6927  eval: 1.4982  best_eval: 1.2642@300  overshoot: 0.2339
  eval_trail: [(100, 1.2782), (200, 1.2688), (300, 1.2642), (400, 1.2649), (500, 1.267), (600, 1.2675), (700, 1.2961), (800, 1.2974), (900, 1.3044), (1000, 1.3501), (1100, 1.3623), (1200, 1.3669), (1300, 1.4219), (1400, 1.4226), (1500, 1.4376), (1600, 1.4814), (1700, 1.4887), (1800, 1.4937), (1900, 1.4947), (2000, 1.4982)]

qwen3_sft_dora_r16_qwen3-1.7b:
  train: 1.0460  eval: 1.2833  best_eval: 1.2589@600  overshoot: 0.0245
  eval_trail: [(100, 1.2848), (200, 1.2729), (300, 1.2677), (400, 1.2634), (500, 1.2618), (600, 1.2589), (700, 1.2631), (800, 1.2628), (900, 1.2616), (1000, 1.2663), (1100, 1.2708), (1200, 1.27), (1300, 1.2762), (1400, 1.2754), (1500, 1.2789), (1600, 1.2798), (1700, 1.2831), (1800, 1.2832), (1900, 1.2834), (2000, 1.2833)]

qwen3_sft_full_ft_qwen3-1.7b:
  train: 1.1807  eval: 1.2806  best_eval: 1.2804@1800  overshoot: 0.0002
  eval_trail: [(100, 1.3023), (200, 1.2935), (300, 1.2897), (400, 1.2867), (500, 1.2852), (600, 1.2835), (700, 1.2832), (800, 1.2824), (900, 1.2816), (1000, 1.281), (1100, 1.281), (1200, 1.2807), (1300, 1.2806), (1400, 1.2807), (1500, 1.2808), (1600, 1.2805), (1700, 1.2807), (1800, 1.2804), (1900, 1.2806), (2000, 1.2806)]


```
</details>

### Step 88: bash

```bash
# Let's also get the qwen3 SFT runs for 0.6b model for comparison
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

runs = [
    'qwen3_sft_lora_r8_qwen3-0.6b',
    'qwen3_sft_lora_r16_qwen3-0.6b', 
    'qwen3_sft_lora_r32_all_qwen3-0.6b',
]

for rn in runs:
    csv_path = os.path.join(base, rn, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append((step, float(row['loss'])))
    
    ms, mv = min(eval_pts, key=lambda x: x[1])
    ft = train_pts[-1][1]
    fe = eval_pts[-1][1]
    
    print(f'{rn}:')
    print(f'  train: {ft:.4f}  eval: {fe:.4f}  best_eval: {mv:.4f}@{ms}  overshoot: {fe-mv:.4f}')
    print()
"
```

<details><summary>Output (315 chars)</summary>

```
qwen3_sft_lora_r8_qwen3-0.6b:
  train: 1.2569  eval: 1.4713  best_eval: 1.4648@900  overshoot: 0.0065

qwen3_sft_lora_r16_qwen3-0.6b:
  train: 1.2033  eval: 1.4826  best_eval: 1.4643@600  overshoot: 0.0183

qwen3_sft_lora_r32_all_qwen3-0.6b:
  train: 0.8363  eval: 1.6687  best_eval: 1.4778@600  overshoot: 0.1909


```
</details>

### Step 89: bash

```bash
# Now let's look at the DPO eval loss trajectories more carefully
python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

runs = [
    'qwen3_dpo_b01_lora_r8_qwen3-1.7b',
    'qwen3_dpo_b01_lora_r16_qwen3-0.6b',
    'qwen3_dpo_b01_lora_r32_all_qwen3-1.7b',
    'qwen3_dpo_b05_lora_r8_qwen3-1.7b',
    'qwen3_dpo_b05_lora_r16_qwen3-1.7b',
    'qwen3_dpo_b05_lora_r32_all_qwen3-1.7b',
]

for rn in runs:
    csv_path = os.path.join(base, rn, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            if ev:
                eval_pts.append((step, float(ev)))
            if lr:
                train_pts.append((step, float(row['loss'])))
    
    ms, mv = min(eval_pts, key=lambda x: x[1])
    ft = train_pts[-1][1]
    fe = eval_pts[-1][1]
    
    print(f'{rn}:')
    print(f'  train: {ft:.4f}  eval: {fe:.4f}  best_eval: {mv:.4f}@{ms}  overshoot: {fe-mv:.4f}  gap: {fe-ft:.4f}')
    print()
"
```

<details><summary>Output (732 chars)</summary>

```
qwen3_dpo_b01_lora_r8_qwen3-1.7b:
  train: 0.1638  eval: 0.7760  best_eval: 0.6407@100  overshoot: 0.1354  gap: 0.6122

qwen3_dpo_b01_lora_r16_qwen3-0.6b:
  train: 0.0649  eval: 1.1780  best_eval: 0.7894@200  overshoot: 0.3886  gap: 1.1131

qwen3_dpo_b01_lora_r32_all_qwen3-1.7b:
  train: 0.0443  eval: 2.4767  best_eval: 1.5983@200  overshoot: 0.8784  gap: 2.4324

qwen3_dpo_b05_lora_r8_qwen3-1.7b:
  train: 0.0631  eval: 1.1857  best_eval: 0.7810@100  overshoot: 0.4047  gap: 1.1226

qwen3_dpo_b05_lora_r16_qwen3-1.7b:
  train: 0.0461  eval: 1.8553  best_eval: 1.1002@100  overshoot: 0.7551  gap: 1.8092

qwen3_dpo_b05_lora_r32_all_qwen3-1.7b:
  train: 0.0433  eval: 6.0224  best_eval: 5.0377@200  overshoot: 0.9847  gap: 5.9791


```
</details>

### Step 90: bash

```bash
# Now I have all the data I need. Let me also look at the adapter weights for the code_instructions runs
# that had the most severe overfitting (lora_r16_mlp and lora_r32_all)

python3 -c "
import json, os
import numpy as np

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

runs = ['lora_r32_all_code_instructions', 'lora_r16_mlp_code_instructions', 'lora_r16_code_instructions', 'lora_r4_code_instructions']

for rn in runs:
    path = os.path.join(base, rn, 'adapter_weight_stats.json')
    if not os.path.exists(path):
        continue
    with open(path) as f:
        stats = json.load(f)
    
    # Get max norm across all lora_B weights (these are the output matrices)
    lora_b_norms = []
    lora_a_norms = []
    for key, val in stats.items():
        if 'lora_B' in key:
            lora_b_norms.append(val['norm'])
        elif 'lora_A' in key:
            lora_a_norms.append(val['norm'])
    
    print(f'{rn}:')
    if lora_a_norms:
        print(f'  lora_A: mean_norm={np.mean(lora_a_norms):.4f} max={np.max(lora_a_norms):.4f}')
    if lora_b_norms:
        print(f'  lora_B: mean_norm={np.mean(lora_b_norms):.4f} max={np.max(lora_b_norms):.4f}')
    print()
"
```

<details><summary>Output (427 chars)</summary>

```
lora_r32_all_code_instructions:
  lora_A: mean_norm=4.3641 max=5.8570
  lora_B: mean_norm=2.1256 max=4.2158

lora_r16_mlp_code_instructions:
  lora_A: mean_norm=4.1079 max=4.9344
  lora_B: mean_norm=2.6245 max=3.5323

lora_r16_code_instructions:
  lora_A: mean_norm=4.1405 max=4.9818
  lora_B: mean_norm=1.9662 max=3.2820

lora_r4_code_instructions:
  lora_A: mean_norm=2.5033 max=3.0627
  lora_B: mean_norm=1.1854 max=2.0375


```
</details>

### Step 91: bash

```bash
# Check for any early warning signals - let's look at the divergence ratio
# At each eval step, compute (eval_loss - train_loss_at_same_step) / eval_loss
# This shows when the gap starts to widen

python3 -c "
import csv, os

base = '/home/ubuntu/workspace/training-export-proprietary/runs'

def parse_run_detailed(run_name):
    csv_path = os.path.join(base, run_name, 'training_log.csv')
    train_pts = []
    eval_pts = []
    with open(csv_path) as f:
        reader = csv.DictReader(f)
        for row in reader:
            step = int(row['step'])
            ev = row.get('eval_loss', '').strip()
            lr = row.get('learning_rate', '').strip()
            grad = row.get('grad_norm', '').strip()
            if ev:
                eval_pts.append({'step': step, 'eval_loss': float(ev)})
            if lr:
                train_pts.append({'step': step, 'train_loss': float(row['loss']), 'grad_norm': float(grad) if grad else 0.0, 'lr': float(lr)})
    return train_pts, eval_pts

# Key v1 runs
runs = ['lora_r4_alpaca', 'lora_r16_alpaca', 'lora_r32_all_alpaca', 'lora_r16_mlp_alpaca', 'full_ft_alpaca']

for rn in runs:
    tp, ep = parse_run_detailed(rn)
    
    # Create training loss lookup
    train_at = {p['step']: p['train_loss'] for p in tp}
    grad_at = {p['step']: p['grad_norm'] for p in tp}
    
    print(f'\n{rn}:')
    print(f'  {\"Step\":>5s} | {\"Eval Loss\":>9s} | {\"Train Loss\":>10s} | {\"Gap\":>8s} | {\"Gap Ratio\":>9s}')
    for e in ep:
        step = e['step']
        eval_l = e['eval_loss']
        # Find closest training loss (use the train step nearest to eval step)
        nearest_train_step = min(train_at.keys(), key=lambda s: abs(s - step))
        train_l = train_at[nearest_train_step]
        gap = eval_l - train_l
        gap_ratio = gap / eval_l if eval_l != 0 else 0
        print(f'  {step:5d} | {eval_l:9.4f} | {train_l:10.4f} | {gap:8.4f} | {gap_ratio:9.4f}')
"
```

<details><summary>Output (3736 chars)</summary>

```

lora_r4_alpaca:
   Step | Eval Loss | Train Loss |      Gap | Gap Ratio
     50 |    1.4845 |     1.5259 |  -0.0414 |   -0.0279
    100 |    1.3345 |     1.4009 |  -0.0664 |   -0.0498
    150 |    1.3157 |     1.2475 |   0.0682 |    0.0518
    200 |    1.3049 |     1.3263 |  -0.0213 |   -0.0164
    250 |    1.2995 |     1.3203 |  -0.0208 |   -0.0160
    300 |    1.2987 |     1.2313 |   0.0674 |    0.0519
    350 |    1.2952 |     1.3040 |  -0.0088 |   -0.0068
    400 |    1.2928 |     1.2463 |   0.0465 |    0.0360
    450 |    1.2936 |     1.2244 |   0.0693 |    0.0535
    500 |    1.2924 |     1.2701 |   0.0224 |    0.0173

lora_r16_alpaca:
   Step | Eval Loss | Train Loss |      Gap | Gap Ratio
     50 |    1.3453 |     1.3565 |  -0.0112 |   -0.0083
    100 |    1.3061 |     1.3656 |  -0.0595 |   -0.0456
    150 |    1.2965 |     1.2102 |   0.0864 |    0.0666
    200 |    1.2890 |     1.2929 |  -0.0039 |   -0.0030
    250 |    1.2870 |     1.2832 |   0.0037 |    0.0029
    300 |    1.2913 |     1.1893 |   0.1020 |    0.0790
    350 |    1.2858 |     1.2575 |   0.0283 |    0.0220
    400 |    1.2854 |     1.1911 |   0.0943 |    0.0734
    450 |    1.2874 |     1.1677 |   0.1197 |    0.0930
    500 |    1.2850 |     1.2096 |   0.0754 |    0.0587

lora_r32_all_alpaca:
   Step | Eval Loss | Train Loss |      Gap | Gap Ratio
     50 |    1.2900 |     1.2900 |   0.0000 |    0.0000
    100 |    1.2738 |     1.3254 |  -0.0516 |   -0.0405
    150 |    1.2815 |     1.0242 |   0.2574 |    0.2008
    200 |    1.2785 |     1.0837 |   0.1947 |    0.1523
    250 |    1.2795 |     1.0818 |   0.1977 |    0.1545
    300 |    1.3488 |     0.8347 |   0.5141 |    0.3811
    350 |    1.3515 |     0.8677 |   0.4838 |    0.3580
    400 |    1.4348 |     0.6877 |   0.7471 |    0.5207
    450 |    1.4450 |     0.6610 |   0.7841 |    0.5426
    500 |    1.4411 |     0.6826 |   0.7585 |    0.5264

lora_r16_mlp_alpaca:
   Step | Eval Loss | Train Loss |      Gap | Gap Ratio
    100 |    1.2724 |     1.2406 |   0.0318 |    0.0250
    200 |    1.2705 |     1.1633 |   0.1072 |    0.0844
    300 |    1.3309 |     1.0519 |   0.2790 |    0.2096
    400 |    1.3951 |     0.7864 |   0.6087 |    0.4363
    500 |    1.4349 |     0.8195 |   0.6153 |    0.4288
    600 |    1.5341 |     0.6645 |   0.8696 |    0.5669
    700 |    1.7194 |     0.4105 |   1.3089 |    0.7613
    800 |    1.8759 |     0.3751 |   1.5008 |    0.8000
    900 |    1.9592 |     0.2227 |   1.7366 |    0.8864
   1000 |    1.9748 |     0.2732 |   1.7016 |    0.8617
   1100 |    2.1193 |     0.1886 |   1.9307 |    0.9110
   1200 |    2.2358 |     0.1745 |   2.0613 |    0.9219
   1300 |    2.3121 |     0.1397 |   2.1724 |    0.9396
   1400 |    2.3703 |     0.1117 |   2.2586 |    0.9529
   1500 |    2.3682 |     0.1143 |   2.2539 |    0.9517
   1600 |    2.4315 |     0.1259 |   2.3056 |    0.9482
   1700 |    2.4552 |     0.1081 |   2.3471 |    0.9560
   1800 |    2.4854 |     0.0992 |   2.3863 |    0.9601
   1900 |

... (736 chars truncated)
```
</details>

### Step 92: bash

```bash
# Now I have comprehensive data. Let me write the report.
cat > /home/ubuntu/workspace/REPORT.md << 'REPORT_END'
# Training Dynamics Analysis: PEFT Adapter Sweep Overfitting Report

## Executive Summary

The r32 run's paradox — lowest training loss but worst eval scores — is a textbook case of **overfitting masked by continued training loss reduction**. This is not an anomaly; it is a systematic pattern that repeats across adapter types, model sizes, and training paradigms. The core finding: **higher-capacity adapters (r32_all, r16_mlp) achieve the best early eval losses but degrade catastrophically with continued training, while constrained adapters (r4, r8, ia3) remain stable throughout.** The divergence between training loss and eval loss begins early and is clearly visible in the eval_loss trajectory — you just have to look at the right metric.

---

## 1. The r32 Problem: A Case Study in Catastrophic Overfitting

### 1.1 SmolLM2-135M + Alpaca (500 steps)

| Adapter | Trainable Params | Final Train Loss | Final Eval Loss | Best Eval Loss | Best Step | Overshoot |
|---------|-----------------|-----------------|----------------|---------------|-----------|-----------|
| lora_r4 | 230K (0.17%) | 1.2701 | 1.2924 | 1.2924 | 500 | **0.0000** |
| lora_r16 | 922K (0.68%) | 1.2096 | 1.2850 | 1.2850 | 500 | **0.0000** |
| lora_r32_all | 9.77M (6.77%) | **0.6826** | **1.4411** | 1.2738 | **100** | **0.1673** |
| lora_r16_mlp | 3.04M (2.21%) | **0.0936** | **2.4983** | 1.2705 | **200** | **1.2278** |
| full_ft | 134.5M (100%) | 1.1045 | 1.2727 | 1.2712 | 350 | 0.0015 |
| ia3 | 74.9K (0.06%) | 1.3538 | 1.3585 | 1.3585 | 500 | 0.0000 |
| adalora | 923K (0.68%) | 1.3415 | 1.3317 | 1.3317 | 500 | 0.0000 |
| dora_r8 | 484K (0.36%) | 0.9670 | 1.3838 | 1.2859 | 400 | 0.0978 |

**Key observations:**
- **lora_r32_all** hits its best eval loss (1.2738) at step 100, then eval loss **rises 13%** over the next 400 steps while training loss drops 48% (from 1.33 → 0.68). The train-eval ga
```

<details><summary>Output (58 chars)</summary>

```
Report written successfully. Size: 21135 bytes, 313 lines

```
</details>

### Step 93: bash

```bash
# Verify the report is well-formed
head -30 /home/ubuntu/workspace/REPORT.md
```

<details><summary>Output (2425 chars)</summary>

```
# Training Dynamics Analysis: PEFT Adapter Sweep Overfitting Report

## Executive Summary

The r32 run's paradox — lowest training loss but worst eval scores — is a textbook case of **overfitting masked by continued training loss reduction**. This is not an anomaly; it is a systematic pattern that repeats across adapter types, model sizes, and training paradigms. The core finding: **higher-capacity adapters (r32_all, r16_mlp) achieve the best early eval losses but degrade catastrophically with continued training, while constrained adapters (r4, r8, ia3) remain stable throughout.** The divergence between training loss and eval loss begins early and is clearly visible in the eval_loss trajectory — you just have to look at the right metric.

---

## 1. The r32 Problem: A Case Study in Catastrophic Overfitting

### 1.1 SmolLM2-135M + Alpaca (500 steps)

| Adapter | Trainable Params | Final Train Loss | Final Eval Loss | Best Eval Loss | Best Step | Overshoot |
|---------|-----------------|-----------------|----------------|---------------|-----------|-----------|
| lora_r4 | 230K (0.17%) | 1.2701 | 1.2924 | 1.2924 | 500 | **0.0000** |
| lora_r16 | 922K (0.68%) | 1.2096 | 1.2850 | 1.2850 | 500 | **0.0000** |
| lora_r32_all | 9.77M (6.77%) | **0.6826** | **1.4411** | 1.2738 | **100** | **0.1673** |
| lora_r16_mlp | 3.04M (2.21%) | **0.0936** | **2.4983** | 1.2705 | **200** | **1.2278** |
| full_ft | 134.5M (100%) | 1.1045 | 1.2727 | 1.2712 | 350 | 0.0015 |
| ia3 | 74.9K (0.06%) | 1.3538 | 1.3585 | 1.3585 | 500 | 0.0000 |
| adalora | 923K (0.68%) | 1.3415 | 1.3317 | 1.3317 | 500 | 0.0000 |
| dora_r8 | 484K (0.36%) | 0.9670 | 1.3838 | 1.2859 | 400 | 0.0978 |

**Key observations:**
- **lora_r32_all** hits its best eval loss (1.2738) at step 100, then eval loss **rises 13%** over the next 400 steps while training loss drops 48% (from 1.33 → 0.68). The train-eval gap at the end is **0.76** — over half the eval loss value.
- **lora_r16_mlp** is even worse: eval loss degrades from 1.27 → 2.50 (a 96% increase), with a train-eval gap of **2.40**. This is severe overfitting — the model is memorizing training data to the point where held-out data performance nearly doubles in loss.
- **full_ft** (100% of parameters) shows almost no overshoot (0.0015) — likely because its much lower learning rate (1e-5 vs 5e-4) acts as an implicit regularizer.

### 1.2 The Eval Loss Trajectory Tells the Whole Story


```
</details>

### Step 94: bash

```bash
# Let me also verify the tail of the report
tail -30 /home/ubuntu/workspace/REPORT.md
```

<details><summary>Output (2631 chars)</summary>

```

1. **Always log eval_loss every 100 steps** (or 5% of total steps, whichever is less).
2. **Implement early stopping**: Stop if eval_loss increases for 2 consecutive evaluations, or if the train-eval gap ratio exceeds 0.20.
3. **For r32_all or all-linear targeting**: Reduce learning rate by 2-3x compared to r8/r16, or halve the number of training steps.
4. **Avoid targeting MLP layers alone** with LoRA unless you have a specific reason. If you need more capacity, prefer r16 on attention + r4 on MLP over r16 on MLP alone.
5. **Always evaluate at the best checkpoint**, not the final one. Use `load_best_model_at_end=True` or manually select the checkpoint with lowest eval loss.

---

## 8. Summary of Key Findings

1. **The r32 paradox is overfitting, not a bug.** Training loss and eval loss diverge because the adapter has enough capacity to memorize the training set. This is visible in the eval_loss trajectory starting at step 100-200.

2. **Adapter capacity, not adapter type, is the primary driver of overfitting risk.** Within the same adapter family (LoRA), higher rank and more target modules lead to earlier and more severe overfitting.

3. **MLP-targeting LoRA is disproportionately dangerous.** Despite fewer total parameters than r32_all, lora_r16_mlp shows worse overfitting because MLP layers can create training-specific feature transformations.

4. **IA³ and AdaLoRA are stable but limited.** Their low capacity prevents overfitting but also caps peak performance.

5. **DPO is far more prone to overfitting than SFT or KTO**, especially with high-rank adapters and higher beta values. KTO is remarkably stable.

6. **The train-eval gap ratio is the best early warning signal.** A ratio above 0.10 is a yellow flag; above 0.20 is a red flag. For lora_r32_all, this crosses 0.10 at step 150.

7. **The best checkpoint is never the final one for high-capacity adapters.** For r32_all, the optimal checkpoint is typically at 10-15% of total training steps. For r16_mlp, at 10-20%.

8. **Full fine-tuning's stability is a learning rate artifact.** With the same LR as LoRA, full FT would likely overfit even faster. Its apparent stability comes from using 50x lower LR.

9. **Longer training amplifies the pattern universally.** On 2000-step runs, even adapters that were stable at 500 steps (lora_r16, full_ft) begin showing overfitting.

10. **Checkpoint selection can recover 90%+ of lost performance.** Deploying lora_r32_all's checkpoint-100 instead of checkpoint-500 recovers eval loss from 1.44 to 1.27 — nearly matching the best lora_r16 result while having the potential for better early performance.

```
</details>

### Step 95: submit

```
The report is complete at `/home/ubuntu/workspace/REPORT.md`. Here's a summary of the key findings:

**The core problem:** r32 has the lowest training loss but worst eval scores because it's overfitting — the adapter has enough capacity (6.77% of params, targeting all linear layers) to memorize the training set. Training loss keeps dropping while eval loss actually *rises* after step 100.

**Key findings across the sweep:**

1. **lora_r32_all** peaks at step 100-300 across every model/dataset, then eval loss degrades 13-96% by the final checkpoint. The train-eval gap reaches 0.76 on alpaca and 1.59 on code_instructions.

2. **lora_r16_mlp is the worst offender** — fewer params than r32_all but overshoots 7x more because targeting MLP layers (gate/up/down_proj) enables training-specific feature mappings that don't generalize.

3. **Low-capacity adapters (r4, r8, ia3, adalora) are stable** but cap peak performance. ia3 has zero overshoot everywhere but the highest eval loss among stable 
```
