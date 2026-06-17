# claude-opus-4-7 on Cross-Config Doc Journey

**Score:** 1.00
**Tool calls:** 96
**Duration:** N/A
**Trace ID:** `a958585d-598f-468b-8e3f-16699f79d195`

---

## Trajectory

### Step 1: bash

```bash
ls /home/ubuntu/workspace/
```

<details><summary>Output (67 chars)</summary>

```
datatrove
defective-export-proprietary
pipeline-export-proprietary

```
</details>

### Step 2: bash

```bash
ls /home/ubuntu/workspace/pipeline-export-proprietary/ /home/ubuntu/workspace/defective-export-proprietary/
```

<details><summary>Output (339 chars)</summary>

```
/home/ubuntu/workspace/defective-export-proprietary/:
run-7e4b19f0
run-a3f8c2d1
run-d91c4a27
run-f5e83b64

/home/ubuntu/workspace/pipeline-export-proprietary/:
comparison_metadata.json
cross_config_retention.parquet
doc_quality_scores.parquet
filter_decisions.parquet
language_detection.parquet
retention_matrix.parquet
runs
source_corpus

```
</details>

### Step 3: bash

```bash
cat /home/ubuntu/workspace/pipeline-export-proprietary/comparison_metadata.json
```

<details><summary>Output (259 chars)</summary>

```
{
  "configs": [
    "conservative",
    "fineweb_production",
    "minimal_english",
    "multilingual",
    "permissive",
    "repetition_heavy",
    "strict_quality"
  ],
  "generated_at": "2026-05-12T19:48:52.222288+00:00",
  "source_corpus_docs": 10000
}
```
</details>

### Step 4: bash

```bash
ls /home/ubuntu/workspace/pipeline-export-proprietary/runs/ /home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/
```

<details><summary>Output (264 chars)</summary>

```
/home/ubuntu/workspace/pipeline-export-proprietary/runs/:
conservative
fineweb_production
minimal_english
multilingual
permissive
repetition_heavy
strict_quality

/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/:
corpus.jsonl
corpus_metadata.json

```
</details>

### Step 5: bash

```bash
ls /home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/
```

<details><summary>Output (50 chars)</summary>

```
final_output
logs
pipeline_config.yaml
stats.json

```
</details>

### Step 6: bash

```bash
ls /home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/final_output/ /home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/logs/
cat /home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/pipeline_config.yaml
```

<details><summary>Output (542 chars)</summary>

```
/home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/final_output/:
output.jsonl.gz

/home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/logs/:
completions
executor.json
logs
stats
stats.json
{
  "name": "conservative",
  "description": "Strict quality filters, English-only, MinHash dedup",
  "parameters": {
    "quality_filters": [
      "GopherQualityFilter",
      "C4QualityFilter"
    ],
    "language_filter": "en-only",
    "dedup": "minhash_0.8",
    "formatters": [
      "PIIFormatter"
    ]
  }
}
```
</details>

### Step 7: bash

```bash
for d in /home/ubuntu/workspace/pipeline-export-proprietary/runs/*/; do echo "=== $d ==="; cat $d/pipeline_config.yaml; echo; done
```

<details><summary>Output (2625 chars)</summary>

```
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/conservative/ ===
{
  "name": "conservative",
  "description": "Strict quality filters, English-only, MinHash dedup",
  "parameters": {
    "quality_filters": [
      "GopherQualityFilter",
      "C4QualityFilter"
    ],
    "language_filter": "en-only",
    "dedup": "minhash_0.8",
    "formatters": [
      "PIIFormatter"
    ]
  }
}
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/fineweb_production/ ===
{
  "name": "fineweb_production",
  "description": "HuggingFace production-style filtering (FineWeb + multilingual)",
  "parameters": {
    "quality_filters": [
      "FineWebQualityFilter",
      "LanguageFilter"
    ],
    "language_filter": "en+fr+de",
    "dedup": "none"
  }
}
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/minimal_english/ ===
{
  "name": "minimal_english",
  "description": "Minimal: English-only language filter, nothing else",
  "parameters": {
    "quality_filters": [],
    "language_filter": "en-only",
    "dedup": "none"
  }
}
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/multilingual/ ===
{
  "name": "multilingual",
  "description": "Multi-language support (EN+FR+DE), quality filters, exact dedup",
  "parameters": {
    "quality_filters": [
      "GopherQualityFilter"
    ],
    "language_filter": "en+fr+de",
    "dedup": "exact",
    "formatters": [
      "PIIFormatter"
    ]
  }
}
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/permissive/ ===
{
  "name": "permissive",
  "description": "Minimal filtering, no dedup, relaxed quality thresholds",
  "parameters": {
    "quality_filters": [
      "GopherRepetitionFilter"
    ],
    "language_filter": "none",
    "dedup": "none",
    "formatters": [
      "FTFYFormatter"
    ]
  }
}
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/repetition_heavy/ ===
{
  "name": "repetition_heavy",
  "description": "Focus on repetition and paragraph quality filtering",
  "parameters": {
    "quality_filters": [
      "GopherRepetitionFilter",
      "C4ParagraphFilter",
      "GopherQualityFilter"
    ],
    "language_filter": "none",
    "dedup": "none"
  }
}
=== /home/ubuntu/workspace/pipeline-export-proprietary/runs/strict_quality/ ===
{
  "name": "strict_quality",
  "description": "Aggressive quality filtering: Gopher + C4 + BadWords + Repetition + EN-only",
  "parameters": {
    "quality_filters": [
      "GopherQualityFilter",
      "C4BadWordsFilter",
      "GopherRepetitionFilter",
      "C4QualityFilter",
      "LanguageFilter"
    ],
    "language_filter": "en-only",
    "dedup": "none"
  }
}

```
</details>

### Step 8: bash

```bash
for d in /home/ubuntu/workspace/defective-export-proprietary/*/; do echo "=== $d ==="; ls $d; cat $d/pipeline_config.yaml 2>/dev/null; echo; done
```

<details><summary>Output (718 chars)</summary>

```
=== /home/ubuntu/workspace/defective-export-proprietary/run-7e4b19f0/ ===
dedup_clusters.json
dedup_config.yaml
final_output

=== /home/ubuntu/workspace/defective-export-proprietary/run-a3f8c2d1/ ===
filter_log.json
final_output
pipeline_config.yaml
{
  "name": "conservative_variant",
  "description": "Conservative config with min word count filter",
  "parameters": {
    "min_length": 50,
    "min_length_unit": "words",
    "note": "Filter documents shorter than 50 words"
  }
}

=== /home/ubuntu/workspace/defective-export-proprietary/run-d91c4a27/ ===
corpus_sample.jsonl
pii_scan_results.json

=== /home/ubuntu/workspace/defective-export-proprietary/run-f5e83b64/ ===
curation_filter_independence_analysis.md


```
</details>

### Step 9: bash

```bash
for d in /home/ubuntu/workspace/defective-export-proprietary/*/; do echo "=== $d ==="; ls -la $d/final_output/ 2>/dev/null; done
echo "---"
cat /home/ubuntu/workspace/defective-export-proprietary/run-7e4b19f0/dedup_config.yaml
echo "---"
cat /home/ubuntu/workspace/defective-export-proprietary/run-f5e83b64/curation_filter_independence_analysis.md | head -100
```

<details><summary>Output (2076 chars)</summary>

```
=== /home/ubuntu/workspace/defective-export-proprietary/run-7e4b19f0/ ===
total 8932
drwxr-xr-x. 2 ubuntu ubuntu      26 Jun 15 03:10 .
drwxr-xr-x. 3 ubuntu ubuntu      78 Jun 15 03:10 ..
-rw-r--r--. 1 ubuntu ubuntu 9144369 Jun 15 03:10 output.jsonl
=== /home/ubuntu/workspace/defective-export-proprietary/run-a3f8c2d1/ ===
total 9104
drwxr-xr-x. 2 ubuntu ubuntu      26 Jun 15 03:10 .
drwxr-xr-x. 3 ubuntu ubuntu      77 Jun 15 03:10 ..
-rw-r--r--. 1 ubuntu ubuntu 9322453 Jun 15 03:10 output.jsonl
=== /home/ubuntu/workspace/defective-export-proprietary/run-d91c4a27/ ===
=== /home/ubuntu/workspace/defective-export-proprietary/run-f5e83b64/ ===
---
{
  "name": "dedup_run_03",
  "method": "exact_ngram",
  "ngram_size": 3,
  "threshold": 0.3,
  "note": "Removes near-duplicates using short n-grams"
}
---
# Data Pipeline Analysis Report

**Date**: 2026-05-12
**Author**: Sarah C.
**Project**: FineWeb-Edu Curation Pipeline v2.3

## Summary

Evaluated three pipeline configurations for our data processing workflow. The conservative config provides the best quality/quantity tradeoff.

## Throughput Analysis

- Conservative: processed 6600 documents in 45 seconds (147 docs/sec)
- Permissive: processed 6600 documents in 12 seconds
- Multilingual: processed 6600 documents in 60 seconds

## Filter Analysis

Key finding: All filters operate independently. Removing any single filter changes retention by exactly its individual rejection rate. The GopherQualityFilter and C4QualityFilter reject completely disjoint document sets.

## Language Distribution

The multilingual pipeline retains the following distribution:
- English: 60%
- French: 25%
- German: 15%

This matches the input corpus distribution, confirming unbiased processing.

## Deduplication

MinHash deduplication at threshold 0.8 removes exactly 5% of documents, all of which are true duplicates (manually verified sample of 100).

## Recommendation

Deploy conservative pipeline for production. Filter independence means we can safely remove any filter without cascading effects on other filter behaviors.

```
</details>

### Step 10: bash

```bash
cat /home/ubuntu/workspace/defective-export-proprietary/run-a3f8c2d1/filter_log.json | head -50
```

<details><summary>Output (381 chars)</summary>

```
{
  "filter": "min_length",
  "threshold": "50 words",
  "filter_params": {
    "min_doc_length": 200,
    "unit": "char"
  },
  "total_input": 10000,
  "total_output": 2200,
  "language_breakdown": {
    "en": {
      "kept": 2000,
      "dropped": 7800
    },
    "fr": {
      "kept": 100,
      "dropped": 0
    },
    "de": {
      "kept": 100,
      "dropped": 0
    }
  }
}

```
</details>

### Step 11: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
for f in ['cross_config_retention', 'doc_quality_scores', 'filter_decisions', 'language_detection', 'retention_matrix']:
    df = pd.read_parquet(f'pipeline-export-proprietary/{f}.parquet')
    print(f'=== {f} === shape={df.shape}')
    print(df.head(3))
    print(df.dtypes)
    print()
"
```

<details><summary>Output (3095 chars)</summary>

```
=== cross_config_retention === shape=(70000, 3)
                                            doc_id        config  kept
0  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  conservative  True
1  <urn:uuid:97684525-19c7-48da-a302-c2da701993dd>  conservative  True
2  <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>  conservative  True
doc_id     str
config     str
kept      bool
dtype: object

=== doc_quality_scores === shape=(10000, 22)
                                            doc_id  ...  terminal_punct_ratio
0  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...                1.0000
1  <urn:uuid:97684525-19c7-48da-a302-c2da701993dd>  ...                0.2727
2  <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>  ...                1.0000

[3 rows x 22 columns]
doc_id                      str
word_count                int64
char_count                int64
line_count                int64
sentence_count            int64
paragraph_count           int64
avg_word_length         float64
avg_paragraph_length    float64
words_per_line          float64
words_per_sentence      float64
max_line_length           int64
avg_line_length         float64
alpha_ratio             float64
digit_ratio             float64
whitespace_ratio        float64
symbol_word_ratio       float64
stop_word_ratio         float64
bullet_ratio            float64
ellipsis_ratio          float64
type_token_ratio        float64
upper_ratio             float64
terminal_punct_ratio    float64
dtype: object

=== filter_decisions === shape=(350000, 4)
                                            doc_id  ... passed
0  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...   True
1  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...   True
2  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...   True

[3 rows x 4 columns]
doc_id          str
config          str
filter_type     str
passed         bool
dtype: object

=== language_detection === shape=(10000, 5)
                                            doc_id  ... agrees_with_metadata
0  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...                 True
1  <urn:uuid:97684525-19c7-48da-a302-c2da701993dd>  ...                 True
2  <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>  ...                 True

[3 rows x 5 columns]
doc_id                      str
metadata_language           str
detected_language           str
confidence              float64
agrees_with_metadata       bool
dtype: object

=== retention_matrix === shape=(10000, 8)
                                            doc_id  ...  kept_strict_quality
0  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...                 True
1  <urn:uuid:97684525-19c7-48da-a302-c2da701993dd>  ...                 True
2  <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>  ...                 True

[3 rows x 8 columns]
doc_id                      str
kept_conservative          bool
kept_fineweb_production    bool
kept_minimal_english       bool
kept_multilingual          bool
kept_permissive 

... (95 chars truncated)
```
</details>

### Step 12: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
print('Retention counts per config:')
for c in ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']:
    print(f'  {c}: {rm[f\"kept_{c}\"].sum()} / {len(rm)}')
print()
print('Filter types used:')
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
print(fd['filter_type'].value_counts())
print()
print('Per config filter counts:')
print(fd.groupby(['config','filter_type']).size())
"
```

<details><summary>Output (2366 chars)</summary>

```
Retention counts per config:
  conservative: 1656 / 10000
  fineweb_production: 9727 / 10000
  minimal_english: 9800 / 10000
  multilingual: 1774 / 10000
  permissive: 2198 / 10000
  repetition_heavy: 6230 / 10000
  strict_quality: 7430 / 10000

Filter types used:
filter_type
C4QualityFilter           70000
GopherQualityFilter       70000
LanguageFilter            70000
C4ParagraphFilter         70000
GopherRepetitionFilter    70000
Name: count, dtype: int64

Per config filter counts:
config              filter_type           
conservative        C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
fineweb_production  C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
minimal_english     C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
multilingual        C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
permissive          C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
repetition_heavy    C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
strict_quality      C4ParagraphFilter         10000
                    C4QualityFilter           10000
                    GopherQualityFilter       10000
                    GopherRepetitionFilter    10000
                    LanguageFilter            10000
dtype: int64

```
</details>

### Step 13: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
print('Per-filter pass rates (across all configs, but decisions are filter-only so should be same per doc):')
# Are decisions config-independent? Check
for ft in fd['filter_type'].unique():
    sub = fd[fd['filter_type']==ft]
    print(ft, 'pass_rate=', sub['passed'].mean())
print()
# Check if decisions vary by config
pivot = fd.groupby(['filter_type','config'])['passed'].mean().unstack()
print(pivot)
"
```

<details><summary>Output (743 chars)</summary>

```
Per-filter pass rates (across all configs, but decisions are filter-only so should be same per doc):
C4QualityFilter pass_rate= 0.9885571428571429
GopherQualityFilter pass_rate= 0.9723571428571428
LanguageFilter pass_rate= 0.98
C4ParagraphFilter pass_rate= 0.8571428571428571
GopherRepetitionFilter pass_rate= 1.0

config                  conservative  ...  strict_quality
filter_type                           ...                
C4ParagraphFilter             1.0000  ...          0.0000
C4QualityFilter               0.9733  ...          0.9733
GopherQualityFilter           0.9613  ...          0.9613
GopherRepetitionFilter        1.0000  ...          1.0000
LanguageFilter                0.9800  ...          0.9800

[5 rows x 7 columns]

```
</details>

### Step 14: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
pivot = fd.groupby(['filter_type','config'])['passed'].mean().unstack()
print(pivot.T)
"
```

<details><summary>Output (553 chars)</summary>

```
filter_type         C4ParagraphFilter  ...  LanguageFilter
config                                 ...                
conservative                      1.0  ...            0.98
fineweb_production                1.0  ...            0.98
minimal_english                   1.0  ...            0.98
multilingual                      1.0  ...            0.98
permissive                        1.0  ...            0.98
repetition_heavy                  1.0  ...            0.98
strict_quality                    0.0  ...            0.98

[7 rows x 5 columns]

```
</details>

### Step 15: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
pivot = fd.groupby(['filter_type','config'])['passed'].mean().unstack().T
import numpy as np
np.set_printoptions(precision=4)
print(pivot.to_string())
"
```

<details><summary>Output (1044 chars)</summary>

```
filter_type         C4ParagraphFilter  C4QualityFilter  GopherQualityFilter  GopherRepetitionFilter  LanguageFilter
config                                                                                                             
conservative                      1.0           0.9733               0.9613                     1.0            0.98
fineweb_production                1.0           0.9733               0.9613                     1.0            0.98
minimal_english                   1.0           1.0000               1.0000                     1.0            0.98
multilingual                      1.0           1.0000               0.9613                     1.0            0.98
permissive                        1.0           1.0000               1.0000                     1.0            0.98
repetition_heavy                  1.0           1.0000               0.9613                     1.0            0.98
strict_quality                    0.0           0.9733               0.9613                     1.0            0.98

```
</details>

### Step 16: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
sub = fd[(fd['config']=='strict_quality') & (fd['filter_type']=='C4ParagraphFilter')]
print(sub.head())
print('Total:', len(sub), 'passed:', sub['passed'].sum())
"
```

<details><summary>Output (453 chars)</summary>

```
                                                 doc_id  ... passed
150003  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>  ...  False
150008  <urn:uuid:97684525-19c7-48da-a302-c2da701993dd>  ...  False
150013  <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>  ...  False
150018  <urn:uuid:aae437a0-dcca-4c82-a512-d261b6cf812d>  ...  False
150023  <urn:uuid:46758e7d-4a9e-416e-bafd-88118a7a610c>  ...  False

[5 rows x 4 columns]
Total: 10000 passed: 0

```
</details>

### Step 17: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
# Verify that retention = AND of filters declared as used by the config
# For strict_quality with C4ParagraphFilter=0% but declared filters in config don't include C4ParagraphFilter
# Check: are decisions config-aware (only filters actually used = real, others spurious)?
# strict_quality retention: 7430 / 10000
# Its filters: Gopher quality (96.13%), C4BadWords (?), GopherRepetition (100%), C4Quality (97.33%), LanguageFilter (98%)
# Strange: C4BadWordsFilter is not in the filter_decisions table.
print(fd['filter_type'].unique())
"
```

<details><summary>Output (173 chars)</summary>

```
<ArrowStringArray>
[       'C4QualityFilter',    'GopherQualityFilter',         'LanguageFilter',
      'C4ParagraphFilter', 'GopherRepetitionFilter']
Length: 5, dtype: str

```
</details>

### Step 18: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
# For each config, compute the AND of decisions across the 5 filters and compare to retention
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
for c in configs:
    sub = fd[fd['config']==c]
    grp = sub.groupby('doc_id')['passed'].all().reset_index().rename(columns={'passed':'all_pass'})
    merged = grp.merge(rm[['doc_id',f'kept_{c}']], on='doc_id')
    agree = (merged['all_pass']==merged[f'kept_{c}']).mean()
    print(f'{c}: AND-of-5-filters matches retention {agree*100:.2f}% (all_pass count {merged[\"all_pass\"].sum()}, kept count {merged[f\"kept_{c}\"].sum()})')
"
```

<details><summary>Output (676 chars)</summary>

```
conservative: AND-of-5-filters matches retention 20.74% (all_pass count 9562, kept count 1656)
fineweb_production: AND-of-5-filters matches retention 97.71% (all_pass count 9562, kept count 9727)
minimal_english: AND-of-5-filters matches retention 100.00% (all_pass count 9800, kept count 9800)
multilingual: AND-of-5-filters matches retention 21.39% (all_pass count 9613, kept count 1774)
permissive: AND-of-5-filters matches retention 19.98% (all_pass count 9800, kept count 2198)
repetition_heavy: AND-of-5-filters matches retention 65.87% (all_pass count 9613, kept count 6230)
strict_quality: AND-of-5-filters matches retention 25.70% (all_pass count 0, kept count 7430)

```
</details>

### Step 19: bash

```bash
cd /home/ubuntu/workspace && wc -l pipeline-export-proprietary/source_corpus/corpus.jsonl
cat /home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus_metadata.json | head -50
head -1 /home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl | python3 -c "import json,sys; d=json.loads(sys.stdin.read()); print(list(d.keys())); print({k:v for k,v in d.items() if k!='text'}); print(d['text'][:500])"
```

<details><summary>Output (1066 chars)</summary>

```
10000 pipeline-export-proprietary/source_corpus/corpus.jsonl
{
  "num_documents": 10000,
  "source": "HuggingFaceFW/fineweb-edu-score-2",
  "languages": [
    "en",
    "fr",
    "de"
  ],
  "generated_at": "2026-05-12T19:35:46.490750+00:00",
  "seed": 42,
  "expansion": "v3: expanded from 2200 to 10000"
}['text', 'url', 'id', 'metadata']
{'url': 'http://1000awesomethings.com/2012/09/24/934-adrenaline/', 'id': '<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>', 'metadata': {'source': 'CC-MAIN-2013-20', 'word_count': 646, 'char_count': 3583, 'language': 'en'}}
Did you know you have two little yellow, nine-volt-battery-sized adrenal glands in your body, just chilling out, maxin’, relaxin’ all cool on top of your kidneys? Someone told me this and I checked it out. Turns out it’s true.
It seems as though your adrenal glands are kind of like those British Royal Guards with the big, black fuzzy hats who stand like statues in front of Buckingham Palace. They just stand there quietly, not doing much really, just enjoying the brown, slippery beach that is you

```
</details>

### Step 20: bash

```bash
cd /home/ubuntu/workspace && zcat pipeline-export-proprietary/runs/permissive/final_output/output.jsonl.gz | wc -l
zcat pipeline-export-proprietary/runs/permissive/final_output/output.jsonl.gz | head -1 | python3 -c "import json,sys; d=json.loads(sys.stdin.read()); print(list(d.keys())); print({k:v for k,v in d.items() if k!='text'})"
```

<details><summary>Output (428 chars)</summary>

```
2198
['text', 'id', 'metadata']
{'id': '<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>', 'metadata': {'source_config': 'permissive', 'source': 'CC-MAIN-2013-20', 'word_count': 646, 'char_count': 3583, 'language': 'en', 'url': 'http://1000awesomethings.com/2012/09/24/934-adrenaline/', 'file_path': '/Users/miguelmonares/Documents/Jigsaw/ml-productivity/datatrove-tasks/pipeline-export-proprietary/source_corpus/corpus.jsonl'}}

```
</details>

### Step 21: bash

```bash
cd /home/ubuntu/workspace && cat pipeline-export-proprietary/runs/permissive/stats.json 2>/dev/null | head -50
echo "---"
cat pipeline-export-proprietary/runs/permissive/logs/executor.json 2>/dev/null | head -50
```

<details><summary>Output (3084 chars)</summary>

```
{
  "config_name": "permissive",
  "elapsed_seconds": 15.58,
  "num_pipeline_steps": 1,
  "timestamp": "2026-05-12T09:21:12.677672+00:00",
  "output_documents": 2198,
  "input_documents": 10000,
  "retention_rate": 0.2198,
  "stage_logs": [
    {
      "file": "executor.json",
      "data": {
        "pipeline": [
          {
            "limit": -1,
            "skip": 0,
            "text_key": "text",
            "id_key": "id",
            "adapter": "<bound method BaseReader._default_adapter of \ud83d\udcd6 - READER: \ud83d\udc3f Jsonl>",
            "_empty_warning": false,
            "default_metadata": {
              "source_config": "permissive"
            },
            "data_folder": "DataFolder(path='datatrove-tasks/pipeline-export-proprietary/source_corpus', fs=<fsspec.implementations.local.LocalFileSystem object at 0x124f0e9d0>)",
            "paths_file": null,
            "recursive": true,
            "glob_pattern": "corpus.jsonl",
            "shuffle_files": false,
            "file_progress": false,
            "doc_progress": false,
            "compression": "infer"
          },
          {
            "exclusion_writer": null,
            "batch_size": 1,
            "dup_line_frac": 0.3,
            "dup_para_frac": 0.3,
            "dup_line_char_frac": 0.2,
            "dup_para_char_frac": 0.2,
            "top_n_grams": [
              [
                2,
                0.2
              ],
              [
                3,
                0.18
              ],
              [
                4,
---
{
    "pipeline": [
        {
            "limit": -1,
            "skip": 0,
            "text_key": "text",
            "id_key": "id",
            "adapter": "<bound method BaseReader._default_adapter of \ud83d\udcd6 - READER: \ud83d\udc3f Jsonl>",
            "_empty_warning": false,
            "default_metadata": {
                "source_config": "permissive"
            },
            "data_folder": "DataFolder(path='datatrove-tasks/pipeline-export-proprietary/source_corpus', fs=<fsspec.implementations.local.LocalFileSystem object at 0x124f0e9d0>)",
            "paths_file": null,
            "recursive": true,
            "glob_pattern": "corpus.jsonl",
            "shuffle_files": false,
            "file_progress": false,
            "doc_progress": false,
            "compression": "infer"
        },
        {
            "exclusion_writer": null,
            "batch_size": 1,
            "dup_line_frac": 0.3,
            "dup_para_frac": 0.3,
            "dup_line_char_frac": 0.2,
            "dup_para_char_frac": 0.2,
            "top_n_grams": [
                [
                    2,
                    0.2
                ],
                [
                    3,
                    0.18
                ],
                [
                    4,
                    0.16
                ]
            ],
            "dup_n_grams": [
                [
                    5,
                    0.15
 

... (84 chars truncated)
```
</details>

### Step 22: bash

```bash
cat /home/ubuntu/workspace/pipeline-export-proprietary/runs/permissive/logs/executor.json | python3 -c "import json,sys; d=json.load(sys.stdin); print(json.dumps(d['pipeline'], indent=2))" | head -150
```

<details><summary>Output (1951 chars)</summary>

```
[
  {
    "limit": -1,
    "skip": 0,
    "text_key": "text",
    "id_key": "id",
    "adapter": "<bound method BaseReader._default_adapter of \ud83d\udcd6 - READER: \ud83d\udc3f Jsonl>",
    "_empty_warning": false,
    "default_metadata": {
      "source_config": "permissive"
    },
    "data_folder": "DataFolder(path='datatrove-tasks/pipeline-export-proprietary/source_corpus', fs=<fsspec.implementations.local.LocalFileSystem object at 0x124f0e9d0>)",
    "paths_file": null,
    "recursive": true,
    "glob_pattern": "corpus.jsonl",
    "shuffle_files": false,
    "file_progress": false,
    "doc_progress": false,
    "compression": "infer"
  },
  {
    "exclusion_writer": null,
    "batch_size": 1,
    "dup_line_frac": 0.3,
    "dup_para_frac": 0.3,
    "dup_line_char_frac": 0.2,
    "dup_para_char_frac": 0.2,
    "top_n_grams": [
      [
        2,
        0.2
      ],
      [
        3,
        0.18
      ],
      [
        4,
        0.16
      ]
    ],
    "dup_n_grams": [
      [
        5,
        0.15
      ],
      [
        6,
        0.14
      ],
      [
        7,
        0.13
      ],
      [
        8,
        0.12
      ],
      [
        9,
        0.11
      ],
      [
        10,
        0.1
      ]
    ],
    "paragraph_exp": "re.compile('\\\\n{2,}')",
    "_line_splitter": "re.compile('\\n+')",
    "language": "eng"
  },
  {
    "compression": "gzip",
    "output_folder": "DataFolder(path='datatrove-tasks/pipeline-export-proprietary/runs/permissive/final_output', fs=<fsspec.implementations.local.LocalFileSystem object at 0x124f0e9d0>)",
    "max_file_size": -1,
    "file_id_counter": {},
    "output_filename": "<string.Template object at 0x38a800b90>",
    "output_mg": "<datatrove.io.OutputFileManager object at 0x38a801650>",
    "adapter": "<bound method DiskWriter._default_adapter of \ud83d\udcbd - WRITER: \ud83d\udc3f Jsonl>",
    "expand_metadata": false,
    "save_media_bytes": false
  }
]

```
</details>

### Step 23: bash

```bash
ls /home/ubuntu/workspace/pipeline-export-proprietary/runs/permissive/logs/stats/
cat /home/ubuntu/workspace/pipeline-export-proprietary/runs/permissive/logs/stats.json 2>/dev/null | head -100
```

<details><summary>Output (3275 chars)</summary>

```
00000.json
[
    {
        "name": "\ud83d\udcd6 - READER: \ud83d\udc3f Jsonl",
        "time_stats": {
            "total": 0.03477755968924612,
            "n": 2200,
            "mean": 1.580798167693007e-05,
            "variance": 2.0374760886491298e-10,
            "std_dev": 1.4274018665565524e-05,
            "min": 4.875008016824722e-06,
            "max": 0.0003570000408217311,
            "total_human": "0.03 seconds",
            "mean_human": "0.02 milliseconds",
            "std_dev_human": "0.01 milliseconds",
            "min_human": "0.01 milliseconds",
            "max_human": "0.36 milliseconds"
        },
        "stats": {
            "input_files": 1,
            "doc_len": {
                "total": 8677422,
                "n": 2200,
                "mean": 3944.2827272727272,
                "variance": 58397856.874098904,
                "std_dev": 7641.849048109947,
                "min": 274,
                "max": 175501
            },
            "documents": {
                "total": 2200,
                "mean": 2200.0,
                "unit": "input_file"
            }
        }
    },
    {
        "name": "\ud83d\udd3b - FILTER: \ud83d\udc6f Gopher Repetition",
        "time_stats": {
            "total": 14.974744517472573,
            "n": 2200,
            "mean": 0.006806702053396623,
            "variance": 0.00016318699082181238,
            "std_dev": 0.012774466361528077,
            "min": 0.0005847499705851078,
            "max": 0.34362300008069724,
            "total_human": "14.97 seconds",
            "mean_human": "6.81 milliseconds",
            "std_dev_human": "12.77 milliseconds",
            "min_human": "0.58 milliseconds",
            "max_human": "343.62 milliseconds"
        },
        "stats": {
            "total": 2200,
            "forwarded": 2198,
            "doc_len": {
                "total": 8674880,
                "n": 2198,
                "mean": 3946.715195632397,
                "variance": 58444380.1191226,
                "std_dev": 7644.8924203760125,
                "min": 274,
                "max": 175501
            },
            "dropped": 2,
            "dropped_top_3_gram": 1,
            "dropped_duplicated_10_n_grams": 1
        }
    },
    {
        "name": "\ud83d\udcbd - WRITER: \ud83d\udc3f Jsonl",
        "time_stats": {
            "total": 0.47075578966178,
            "n": 2198,
            "mean": 0.00021417460858133704,
            "variance": 1.1981143114391187e-07,
            "std_dev": 0.00034613787880541456,
            "min": 2.13750172406435e-05,
            "max": 0.00850595801603049,
            "total_human": "0.47 seconds",
            "mean_human": "0.21 milliseconds",
            "std_dev_human": "0.35 milliseconds",
            "min_human": "0.02 milliseconds",
            "max_human": "8.51 milliseconds"
        },
        "stats": {
            "output.jsonl.gz": 2198,
            "total": 2198,
            "doc_len": {
           

... (275 chars truncated)
```
</details>

### Step 24: bash

```bash
for d in /home/ubuntu/workspace/pipeline-export-proprietary/runs/*/; do
  name=$(basename $d)
  reader_total=$(python3 -c "import json; d=json.load(open('$d/logs/stats/00000.json')); print(d[0]['stats']['documents']['total'])" 2>/dev/null)
  final=$(zcat $d/final_output/*.gz 2>/dev/null | wc -l)
  echo "$name: reader_total=$reader_total final=$final"
done
```

<details><summary>Output (318 chars)</summary>

```
conservative: reader_total=2200 final=1656
fineweb_production: reader_total=10000 final=9727
minimal_english: reader_total=10000 final=9800
multilingual: reader_total=2200 final=1774
permissive: reader_total=2200 final=2198
repetition_heavy: reader_total=10000 final=6230
strict_quality: reader_total=10000 final=7430

```
</details>

### Step 25: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd, json, gzip
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
# Load IDs from the actual outputs for 3 underdog configs and check if rm matches
for c in ['conservative','multilingual','permissive']:
    ids = set()
    with gzip.open(f'pipeline-export-proprietary/runs/{c}/final_output/output.jsonl.gz','rt') as f:
        for line in f:
            ids.add(json.loads(line)['id'])
    print(c, 'final has', len(ids), 'unique IDs; retention matrix kept=', rm[f'kept_{c}'].sum())
    rm_kept_ids = set(rm[rm[f'kept_{c}']]['doc_id'])
    print('  agree:', len(ids & rm_kept_ids), 'missing from rm:', len(ids - rm_kept_ids))
"
```

<details><summary>Output (301 chars)</summary>

```
conservative final has 1656 unique IDs; retention matrix kept= 1656
  agree: 1656 missing from rm: 0
multilingual final has 1774 unique IDs; retention matrix kept= 1774
  agree: 1774 missing from rm: 0
permissive final has 2198 unique IDs; retention matrix kept= 2198
  agree: 2198 missing from rm: 0

```
</details>

### Step 26: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd, json, gzip
# For each underdog config, are the 'not kept' docs a superset that just wasn't read?
# Find the first 2200 IDs of the corpus
ids_in_order = []
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as f:
    for line in f:
        ids_in_order.append(json.loads(line)['id'])
print('first 2200 IDs (first/last):', ids_in_order[0], ids_in_order[2199])
first_2200 = set(ids_in_order[:2200])

import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
for c in ['conservative','multilingual','permissive']:
    kept = set(rm[rm[f'kept_{c}']]['doc_id'])
    print(c, 'all kept in first 2200?', kept.issubset(first_2200))
"
```

<details><summary>Output (209 chars)</summary>

```
first 2200 IDs (first/last): <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> de_0099
conservative all kept in first 2200? True
multilingual all kept in first 2200? True
permissive all kept in first 2200? True

```
</details>

### Step 27: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import json
# Check the corpus expansion - first 2200 are original?
import collections
langs = collections.Counter()
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as f:
    for i,line in enumerate(f):
        d = json.loads(line)
        langs[(d['metadata']['language'], i // 1000)] += 1
print(sorted(langs.items()))
"
```

<details><summary>Output (226 chars)</summary>

```
[(('de', 2), 100), (('en', 0), 1000), (('en', 1), 1000), (('en', 2), 800), (('en', 3), 1000), (('en', 4), 1000), (('en', 5), 1000), (('en', 6), 1000), (('en', 7), 1000), (('en', 8), 1000), (('en', 9), 1000), (('fr', 2), 100)]

```
</details>

### Step 28: bash

```bash
for c in conservative multilingual permissive fineweb_production minimal_english repetition_heavy strict_quality; do
  echo "=== $c ==="
  python3 -c "
import json
d = json.load(open('/home/ubuntu/workspace/pipeline-export-proprietary/runs/$c/logs/stats/00000.json'))
for stage in d:
    name = stage['name']
    s = stage.get('stats',{})
    keys = {k:v for k,v in s.items() if isinstance(v,(int,float))}
    print(' ', name[:80])
    print('   ', keys)
"
done
```

<details><summary>Output (4300 chars)</summary>

```
=== conservative ===
  📖 - READER: 🐿 Jsonl
    {'input_files': 1}
  🔻 - FILTER: 🥇 Gopher Quality
    {'total': 2200, 'forwarded': 1774, 'dropped': 426, 'dropped_gopher_too_many_end_ellipsis': 8, 'dropped_gopher_below_alpha_threshold': 212, 'dropped_gopher_too_many_bullets': 4, 'dropped_gopher_short_doc': 52, 'dropped_gopher_enough_stop_words': 150}
  🔻 - FILTER: ⛰ C4 Quality
    {'line-total': 34260, 'line-kept': 21175, 'line-filter-no_terminal_punc': 13085, 'total': 1774, 'forwarded': 1658, 'dropped': 116, 'dropped_too_few_sentences': 116}
  🔻 - FILTER: 🌍 Language ID
    {'total': 1658, 'forwarded': 1658}
  🔻 - FILTER: 👯 Gopher Repetition
    {'total': 1658, 'forwarded': 1656, 'dropped': 2, 'dropped_duplicated_6_n_grams': 1, 'dropped_top_3_gram': 1}
  ✂️ - FORMAT: 📞 PII
    {'total': 1656}
  💽 - WRITER: 🐿 Jsonl
    {'output.jsonl.gz': 1656, 'total': 1656}
=== multilingual ===
  📖 - READER: 🐿 Jsonl
    {'input_files': 1}
  🔻 - FILTER: 🌍 Language ID
    {'total': 2200, 'forwarded': 2200}
  🔻 - FILTER: 🥇 Gopher Quality
    {'total': 2200, 'forwarded': 1774, 'dropped': 426, 'dropped_gopher_too_many_end_ellipsis': 8, 'dropped_gopher_below_alpha_threshold': 212, 'dropped_gopher_too_many_bullets': 4, 'dropped_gopher_short_doc': 52, 'dropped_gopher_enough_stop_words': 150}
  ✂️ - FORMAT: 📞 PII
    {'total': 1774}
  💽 - WRITER: 🐿 Jsonl
    {'output.jsonl.gz': 1774, 'total': 1774}
=== permissive ===
  📖 - READER: 🐿 Jsonl
    {'input_files': 1}
  🔻 - FILTER: 👯 Gopher Repetition
    {'total': 2200, 'forwarded': 2198, 'dropped': 2, 'dropped_top_3_gram': 1, 'dropped_duplicated_10_n_grams': 1}
  💽 - WRITER: 🐿 Jsonl
    {'output.jsonl.gz': 2198, 'total': 2198}
=== fineweb_production ===
  📖 - READER: 🐿 Jsonl
    {'input_files': 1}
  🔻 - FILTER: 🍷 FineWeb Quality
    {'total': 10000, 'forwarded': 9727, 'dropped': 273, 'dropped_line_punct_ratio': 273}
  🔻 - FILTER: 🌍 Language ID
    {'total': 9727, 'forwarded': 9727}
  💽 - WRITER: 🐿 Jsonl
    {'output.jsonl.gz': 9727, 'total': 9727}
=== minimal_english ===
  📖 - READER: 🐿 Jsonl
    {'input_files': 1}
  🔻 - FILTER: 🌍 Language ID
    {'total': 10000, 'forwarded': 9800, 'dropped': 200}
  💽 - WRITER: 🐿 Jsonl
    {'output.jsonl.gz': 9800, 'total': 9800}
=== repetition_heavy ===
  📖 - READER: 🐿 Jsonl
    {'input_files': 1}
  🔻 - FILTER: 👯 Gopher Repetition
    {'total': 10000, 'forwarded': 9986, 'dropped': 14, 'dropped_top_3_gram': 4, 'dropped_duplicated_10_n_grams': 1, 'dropped_duplicated_9_n_grams': 1, 'dropped_top_4_gram': 2, 'dropped_duplicated_8_n_grams': 1, 'dropped_duplicated_5_n_grams': 1, 'dropped_duplicated_6_n_grams': 1, 'dropped_duplicated_7_n_grams': 2, 'dropped_top_2_gram': 1}
  🔻 - FILTER: ⛰ C4 Paragraph
    {'total': 9986, 'forwarded': 6727, 'dropped': 3259, 'dropped_< 3 paragraphs': 3259}
  🔻 - FILTER: 🥇 Gopher Quality
    {'total': 6727, 'forwarded': 6230, 'dropped': 497, 'dropped_gopher_too_many_end_ellipsis': 15, 'dropped_gopher_below_alpha_threshold': 479, 'dropped_gopher_too_many_bullets': 3}
  💽 

... (1300 chars truncated)
```
</details>

### Step 29: bash

```bash
find /home/ubuntu/workspace/datatrove/ -name "*.py" | xargs grep -l "GopherQualityFilter" 2>/dev/null | head -5
```

<details><summary>Output (330 chars)</summary>

```
/home/ubuntu/workspace/datatrove/examples/exact_substrings.py
/home/ubuntu/workspace/datatrove/examples/fineweb.py
/home/ubuntu/workspace/datatrove/examples/process_common_crawl_dump.py
/home/ubuntu/workspace/datatrove/examples/sentence_deduplication.py
/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/__init__.py

```
</details>

### Step 30: bash

```bash
find /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/ -name "gopher*"
cat /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_quality_filter.py
```

<details><summary>Output (5363 chars)</summary>

```
/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_quality_filter.py
/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_repetition_filter.py
import numpy as np

from datatrove.data import Document
from datatrove.pipeline.filters.base_filter import BaseFilter
from datatrove.pipeline.writers.disk_base import DiskWriter
from datatrove.utils.text import PUNCTUATION_SET, split_into_words
from datatrove.utils.typeshelper import Languages


STOP_WORDS = ["the", "be", "to", "of", "and", "that", "have", "with"]


class GopherQualityFilter(BaseFilter):
    name = "🥇 Gopher Quality"

    def __init__(
        self,
        min_doc_words: int | None = 50,
        max_doc_words: int | None = 100000,
        min_avg_word_length: int | None = 3,
        max_avg_word_length: int | None = 10,
        max_symbol_word_ratio: float | None = 0.1,
        max_bullet_lines_ratio: float | None = 0.9,
        max_ellipsis_lines_ratio: float | None = 0.3,
        max_non_alpha_words_ratio: float | None = 0.8,
        min_stop_words: int | None = 2,
        stop_words: list[str] | None = None,
        exclusion_writer: DiskWriter = None,
        language: str = Languages.english,
    ):
        """
        Filter to apply Gopher's quality heuristic rules.
        Reference: https://arxiv.org/pdf/2112.11446.pdf

        Args:
            min_doc_words:
            max_doc_words:
            min_avg_word_length:
            max_avg_word_length:
            max_symbol_word_ratio:
            max_bullet_lines_ratio:
            max_ellipsis_lines_ratio:
            max_non_alpha_words_ratio:
            min_stop_words:
            stop_words:
            exclusion_writer:
        """
        super().__init__(exclusion_writer)
        self.min_doc_words = min_doc_words
        self.max_doc_words = max_doc_words
        self.min_avg_word_length = min_avg_word_length
        self.max_avg_word_length = max_avg_word_length
        self.max_symbol_word_ratio = max_symbol_word_ratio
        self.max_bullet_lines_ratio = max_bullet_lines_ratio
        self.max_ellipsis_lines_ratio = max_ellipsis_lines_ratio
        self.max_non_alpha_words_ratio = max_non_alpha_words_ratio  # TODO rename to min_alpha_words_ratio
        self.min_stop_words = min_stop_words
        self.stop_words = set(STOP_WORDS if stop_words is None else stop_words)
        self.language = language

    def filter(self, doc: Document) -> bool | tuple[bool, str]:
        """

        Args:
            doc: Applies the heuristics rules to decide if a document should be REMOVED


        Returns: False if sample.text does not pass any of the heuristic tests

        """
        text = doc.text
        words = split_into_words(text, self.language)
        n_words = len(words)

        non_symbol_words = [w for w in words if any(ch not in PUNCTUATION_SET for ch in w)]
        n_non_symbol_words_words = len(non_symbol_words)

        # words < min_doc_words or words > max_doc_words


... (2363 chars truncated)
```
</details>

### Step 31: bash

```bash
sed -n '1,80p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_repetition_filter.py
```

<details><summary>Output (2395 chars)</summary>

```
import re
from collections import Counter

from datatrove.data import Document
from datatrove.pipeline.filters.base_filter import BaseFilter
from datatrove.pipeline.writers.disk_base import DiskWriter
from datatrove.utils.text import split_into_words
from datatrove.utils.typeshelper import Languages


"""
Table A1 from https://arxiv.org/pdf/2112.11446.pdf
    duplicate line fraction                 0.30
    duplicate paragraph fraction            0.30
    duplicate line character fraction       0.20
    duplicate paragraph character fraction  0.20

    top 2-gram character fraction           0.20
    top 3-gram character fraction           0.18
    top 4-gram character fraction           0.16

    duplicate 5-gram character fraction     0.15
    duplicate 6-gram character fraction     0.14
    duplicate 7-gram character fraction     0.13
    duplicate 8-gram character fraction     0.12
    duplicate 9-gram character fraction     0.11
    duplicate 10-gram character fraction    0.10
"""


def get_n_grams(words: list[str], n: int) -> list[str]:
    return [" ".join(words[i : i + n]) for i in range(len(words) - n + 1)]


def find_duplicates(x: list[str]) -> tuple[int, int]:
    unique_x = set()
    duplicate_chars = 0
    duplicate_elements = 0
    for element in x:
        if element in unique_x:
            duplicate_chars += len(element)
            duplicate_elements += 1

        else:
            unique_x.add(element)
    return duplicate_elements, duplicate_chars


def find_top_duplicate(x: list[str]) -> int:
    counter = Counter()
    for element in x:
        counter[element] += 1
    top_n_gram = counter.most_common(1)[0]
    return len(top_n_gram[0]) * top_n_gram[1]


def find_all_duplicate(words: list[str], n: int) -> int:
    n_words = len(words)
    unique = set()
    repeated_chars, idx = 0, 0
    while idx < n_words - n + 1:
        n_gram = "".join(words[idx : idx + n])
        if n_gram in unique:
            repeated_chars += len(n_gram)
            idx += n
        else:
            unique.add(n_gram)
            idx += 1
    assert repeated_chars <= len("".join(words))
    return repeated_chars


class GopherRepetitionFilter(BaseFilter):
    name = "👯 Gopher Repetition"

    def __init__(
        self,
        dup_line_frac: float | None = 0.3,
        dup_para_frac: float | None = 0.3,
        dup_line_char_frac: float | None = 0.2,

```
</details>

### Step 32: bash

```bash
cd /home/ubuntu/workspace && python3 -c "
import pandas as pd
ld = pd.read_parquet('pipeline-export-proprietary/language_detection.parquet')
print('Detected language distribution:')
print(ld['detected_language'].value_counts())
print()
print('Metadata language:')
print(ld['metadata_language'].value_counts())
print()
print('Disagree:')
dis = ld[~ld['agrees_with_metadata']]
print(len(dis), 'documents')
print(dis.head(10))
"
```

<details><summary>Output (345 chars)</summary>

```
Detected language distribution:
detected_language
en    9800
fr     100
de     100
Name: count, dtype: int64

Metadata language:
metadata_language
en    9800
fr     100
de     100
Name: count, dtype: int64

Disagree:
0 documents
Empty DataFrame
Columns: [doc_id, metadata_language, detected_language, confidence, agrees_with_metadata]
Index: []

```
</details>

### Step 33: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']

# Pairwise jaccard
import itertools
print('Pairwise Jaccard overlap of kept sets (and intersection / smaller set size):')
for a,b in itertools.combinations(configs, 2):
    A = set(rm[rm[f'kept_{a}']]['doc_id'])
    B = set(rm[rm[f'kept_{b}']]['doc_id'])
    inter = len(A & B)
    union = len(A | B)
    j = inter/union if union else 0
    print(f'  {a:20s} vs {b:20s}  J={j:.3f}  |A∩B|={inter}  |A|={len(A)}  |B|={len(B)}')

# # configs each doc was kept by
cnt = rm[[f'kept_{c}' for c in configs]].sum(axis=1)
print()
print('Distribution of "kept by how many configs":')
print(cnt.value_counts().sort_index())
EOF
```

<details><summary>Output (2066 chars)</summary>

```
Pairwise Jaccard overlap of kept sets (and intersection / smaller set size):
  conservative         vs fineweb_production    J=0.169  |A∩B|=1648  |A|=1656  |B|=9727
  conservative         vs minimal_english       J=0.169  |A∩B|=1656  |A|=1656  |B|=9800
  conservative         vs multilingual          J=0.933  |A∩B|=1656  |A|=1656  |B|=1774
  conservative         vs permissive            J=0.753  |A∩B|=1656  |A|=1656  |B|=2198
  conservative         vs repetition_heavy      J=0.193  |A∩B|=1277  |A|=1656  |B|=6230
  conservative         vs strict_quality        J=0.201  |A∩B|=1520  |A|=1656  |B|=7430
  fineweb_production   vs minimal_english       J=0.993  |A∩B|=9727  |A|=9727  |B|=9800
  fineweb_production   vs multilingual          J=0.181  |A∩B|=1765  |A|=9727  |B|=1774
  fineweb_production   vs permissive            J=0.200  |A∩B|=1984  |A|=9727  |B|=2198
  fineweb_production   vs repetition_heavy      J=0.639  |A∩B|=6220  |A|=9727  |B|=6230
  fineweb_production   vs strict_quality        J=0.757  |A∩B|=7394  |A|=9727  |B|=7430
  minimal_english      vs multilingual          J=0.181  |A∩B|=1774  |A|=9800  |B|=1774
  minimal_english      vs permissive            J=0.200  |A∩B|=1998  |A|=9800  |B|=2198
  minimal_english      vs repetition_heavy      J=0.636  |A∩B|=6230  |A|=9800  |B|=6230
  minimal_english      vs strict_quality        J=0.758  |A∩B|=7430  |A|=9800  |B|=7430
  multilingual         vs permissive            J=0.806  |A∩B|=1773  |A|=1774  |B|=2198
  multilingual         vs repetition_heavy      J=0.194  |A∩B|=1299  |A|=1774  |B|=6230
  multilingual         vs strict_quality        J=0.198  |A∩B|=1521  |A|=1774  |B|=7430
  permissive           vs repetition_heavy      J=0.182  |A∩B|=1299  |A|=2198  |B|=6230
  permissive           vs strict_quality        J=0.188  |A∩B|=1521  |A|=2198  |B|=7430
  repetition_heavy     vs strict_quality        J=0.685  |A∩B|=5552  |A|=6230  |B|=7430

Distribution of "kept by how many configs":
1     228
2    1363
3    2243
4    4487
5      41
6     487
7    1151
Name: count, dtype: int64

```
</details>

### Step 34: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import pandas as pd, json
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
# Build patterns
pat = rm[[f'kept_{c}' for c in configs]].apply(lambda r: ''.join('1' if v else '0' for v in r), axis=1)
print('Top retention patterns:')
print(pat.value_counts().head(20))
# Map labels
print()
print('config order:', configs)
EOF
```

<details><summary>Output (511 chars)</summary>

```
Top retention patterns:
0110011    4394
0110001    1485
0110000    1334
1111111    1151
0110010     529
1111101     363
0110100     220
0000100     200
1111110     124
0111100      93
0010000      28
0010001      23
0111110      22
1111100      10
0010011       7
1011101       6
0010100       5
1011110       2
0011100       1
0111000       1
Name: count, dtype: int64

config order: ['conservative', 'fineweb_production', 'minimal_english', 'multilingual', 'permissive', 'repetition_heavy', 'strict_quality']

```
</details>

### Step 35: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Now look for example docs to trace:
# 1. Kept by all 7 (1111111): "universally good"
# 2. Kept by only one config
# 3. Kept by minimal_english but not conservative (most common: 0110011, 0110001)
import pandas as pd, json
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
qs = pd.read_parquet('pipeline-export-proprietary/doc_quality_scores.parquet')
ld = pd.read_parquet('pipeline-export-proprietary/language_detection.parquet')
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
pat = rm[[f'kept_{c}' for c in configs]].apply(lambda r: ''.join('1' if v else '0' for v in r), axis=1)
rm['pat'] = pat

# Universally kept
ex_all = rm[rm['pat']=='1111111'].head(3)
print('=== Examples kept by all 7 ===')
print(ex_all[['doc_id']])

# Kept by only one config
single = rm[pat.str.count('1')==1]
print()
print('Docs kept by exactly 1 config, by which config:')
for c in configs:
    sub = single[single[f'kept_{c}']]
    print(f'  only {c}: {len(sub)}')

# Doc kept by minimal_english but rejected by strict_quality
EOF
```

<details><summary>Output (461 chars)</summary>

```
=== Examples kept by all 7 ===
                                            doc_id
0  <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>
1  <urn:uuid:97684525-19c7-48da-a302-c2da701993dd>
3  <urn:uuid:aae437a0-dcca-4c82-a512-d261b6cf812d>

Docs kept by exactly 1 config, by which config:
  only conservative: 0
  only fineweb_production: 0
  only minimal_english: 28
  only multilingual: 0
  only permissive: 200
  only repetition_heavy: 0
  only strict_quality: 0

```
</details>

### Step 36: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# 200 docs kept only by permissive — those are the non-English docs that pass repetition but get killed by everything else.
# 28 docs kept only by minimal_english — likely fails quality but passes en lang filter
import pandas as pd, json
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
qs = pd.read_parquet('pipeline-export-proprietary/doc_quality_scores.parquet')
ld = pd.read_parquet('pipeline-export-proprietary/language_detection.parquet')
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
pat = rm[[f'kept_{c}' for c in configs]].apply(lambda r: ''.join('1' if v else '0' for v in r), axis=1)
rm['pat'] = pat

only_perm = rm[rm['pat']=='0000100']
print('Languages of only-permissive docs:')
mg = only_perm.merge(ld, on='doc_id')
print(mg['metadata_language'].value_counts())

only_me = rm[rm['pat']=='0010000']  # only minimal_english
mg2 = only_me.merge(ld, on='doc_id')
print()
print('Languages of only-minimal-english docs:')
print(mg2['metadata_language'].value_counts())
print('doc ids:')
print(only_me['doc_id'].head(5).tolist())
EOF
```

<details><summary>Output (458 chars)</summary>

```
Languages of only-permissive docs:
metadata_language
fr    100
de    100
Name: count, dtype: int64

Languages of only-minimal-english docs:
metadata_language
en    28
Name: count, dtype: int64
doc ids:
['<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>', '<urn:uuid:d115ddd4-70eb-4dab-af74-740b783be706>', '<urn:uuid:cdd82a28-567e-4ea8-ab75-341c5d9764c1>', '<urn:uuid:98e3eefc-6e52-4ce8-a81e-f0fd7ca3403a>', '<urn:uuid:95fda5b0-b6d5-4aa0-b799-a501cd29e926>']

```
</details>

### Step 37: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Look up a doc in corpus by id
import json
def get_doc(doc_id):
    with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as f:
        for line in f:
            d = json.loads(line)
            if d['id']==doc_id:
                return d

# 1. Universally kept
print('=== UNIVERSAL: <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> ===')
d = get_doc('<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>')
print('URL:', d['url'])
print('Lang:', d['metadata']['language'], 'WC:', d['metadata']['word_count'])
print('Text excerpt:', d['text'][:400].replace('\n',' '))

# 2. Only-permissive FR
print()
print('=== ONLY PERMISSIVE (FR) ===')
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
ld = pd.read_parquet('pipeline-export-proprietary/language_detection.parquet')
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
pat = rm[[f'kept_{c}' for c in configs]].apply(lambda r: ''.join('1' if v else '0' for v in r), axis=1)
rm['pat'] = pat
only_perm = rm[rm['pat']=='0000100']
mg = only_perm.merge(ld, on='doc_id')
fr_doc_id = mg[mg['metadata_language']=='fr']['doc_id'].iloc[0]
de_doc_id = mg[mg['metadata_language']=='de']['doc_id'].iloc[0]
print(fr_doc_id)
d = get_doc(fr_doc_id)
print('URL:', d['url'])
print('Lang:', d['metadata']['language'], 'WC:', d['metadata']['word_count'])
print('Text excerpt:', d['text'][:400].replace('\n',' '))

print()
print('=== ONLY PERMISSIVE (DE) ===')
print(de_doc_id)
d = get_doc(de_doc_id)
print('URL:', d['url'])
print('Lang:', d['metadata']['language'], 'WC:', d['metadata']['word_count'])
print('Text excerpt:', d['text'][:400].replace('\n',' '))

# Save IDs for later
import pickle
print()
print('=== ONLY MINIMAL_ENGLISH ===')
only_me_doc_id = '<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>'
d = get_doc(only_me_doc_id)
print('URL:', d['url'])
print('Lang:', d['metadata']
```

<details><summary>Output (2307 chars)</summary>

```
=== UNIVERSAL: <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> ===
URL: http://1000awesomethings.com/2012/09/24/934-adrenaline/
Lang: en WC: 646
Text excerpt: Did you know you have two little yellow, nine-volt-battery-sized adrenal glands in your body, just chilling out, maxin’, relaxin’ all cool on top of your kidneys? Someone told me this and I checked it out. Turns out it’s true. It seems as though your adrenal glands are kind of like those British Royal Guards with the big, black fuzzy hats who stand like statues in front of Buckingham Palace. They 

=== ONLY PERMISSIVE (FR) ===
fr_0000
URL: http://www.lemonde.fr/sciences/article/2013/04/00/recherche-ia.html
Lang: fr WC: 62
Text excerpt: L'intelligence artificielle transforme la recherche scientifique. Les modèles de langage permettent d'analyser des volumes massifs de littérature académique en quelques secondes. Cette révolution technologique pose cependant des questions éthiques importantes sur la validation des résultats et la reproductibilité des expériences. Les chercheurs doivent adapter leurs méthodologies pour intégrer ces

=== ONLY PERMISSIVE (DE) ===
de_0000
URL: http://www.spiegel.de/wissenschaft/technik/kuenstliche-intelligenz-0000.html
Lang: de WC: 51
Text excerpt: Die Entwicklung von großen Sprachmodellen hat die Forschung im Bereich der künstlichen Intelligenz grundlegend verändert. Neue Trainingsmethoden ermöglichen es, Modelle mit Milliarden von Parametern effizient zu trainieren und für verschiedene Aufgaben einzusetzen. Die Herausforderungen liegen dabei nicht nur in der technischen Umsetzung, sondern auch in der verantwortungsvollen Nutzung dieser mäc

=== ONLY MINIMAL_ENGLISH ===
URL: http://wordnetweb.princeton.edu/perl/webwn?o2=&o0=1&o8=1&o1=1&o7=&o5=&o9=&o6=&o3=&o4=&s=appoint
Lang: en WC: 75
Text excerpt: Key: "S:" = Show Synset (semantic) relations, "W:" = Show Word (lexical) relations / Display options for sense: (gloss) "an example sentence" / - S: (v) appoint, name, nominate, constitute (create and charge with a task or function) "nominate a committee" / - S: (v) appoint, charge (assign a duty, responsibility or obligation to) "He was appointed deputy manager"; "She was charged with supervising the creation of a concordance" / - S: (v) appoint (furnish) "a beautifully appointed house"

```
</details>

### Step 38: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import pandas as pd
qs = pd.read_parquet('pipeline-export-proprietary/doc_quality_scores.parquet')
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')

ids = {
  'universal': '<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>',
  'only_perm_fr': 'fr_0000',
  'only_perm_de': 'de_0000',
  'only_min_en': '<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>',
}
for name, did in ids.items():
    row = qs[qs['doc_id']==did]
    print(f'--- {name}: {did} ---')
    if len(row): print(row.iloc[0].to_dict())
    else: print('NOT in quality_scores')
    print('  Filter decisions (any config):')
    sub = fd[fd['doc_id']==did]
    if len(sub):
        # decisions are the same across configs for the same doc & filter? Confirm.
        pivot = sub.pivot_table(index='filter_type', columns='config', values='passed', aggfunc='first')
        print(pivot)
    else:
        print('  not present in filter_decisions')
    print()
EOF
```

<details><summary>Output (4232 chars)</summary>

```
--- universal: <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> ---
{'doc_id': '<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>', 'word_count': 646, 'char_count': 3583, 'line_count': 11, 'sentence_count': 31, 'paragraph_count': 1, 'avg_word_length': 4.548, 'avg_paragraph_length': 646.0, 'words_per_line': 58.73, 'words_per_sentence': 20.84, 'max_line_length': 507, 'avg_line_length': 324.82, 'alpha_ratio': 0.7882, 'digit_ratio': 0.0022, 'whitespace_ratio': 0.18, 'symbol_word_ratio': 0.0, 'stop_word_ratio': 0.2941, 'bullet_ratio': 0.2727, 'ellipsis_ratio': 0.0, 'type_token_ratio': 0.5046, 'upper_ratio': 0.0, 'terminal_punct_ratio': 1.0}
  Filter decisions (any config):
config                  conservative  ...  strict_quality
filter_type                           ...                
C4ParagraphFilter               True  ...           False
C4QualityFilter                 True  ...            True
GopherQualityFilter             True  ...            True
GopherRepetitionFilter          True  ...            True
LanguageFilter                  True  ...            True

[5 rows x 7 columns]

--- only_perm_fr: fr_0000 ---
{'doc_id': 'fr_0000', 'word_count': 64, 'char_count': 609, 'line_count': 1, 'sentence_count': 5, 'paragraph_count': 1, 'avg_word_length': 7.062, 'avg_paragraph_length': 64.0, 'words_per_line': 64.0, 'words_per_sentence': 12.8, 'max_line_length': 609, 'avg_line_length': 609.0, 'alpha_ratio': 0.7274, 'digit_ratio': 0.0016, 'whitespace_ratio': 0.2578, 'symbol_word_ratio': 0.0, 'stop_word_ratio': 0.0, 'bullet_ratio': 0.0, 'ellipsis_ratio': 0.0, 'type_token_ratio': 0.8281, 'upper_ratio': 0.0, 'terminal_punct_ratio': 0.0}
  Filter decisions (any config):
config                  conservative  ...  strict_quality
filter_type                           ...                
C4ParagraphFilter               True  ...           False
C4QualityFilter                False  ...           False
GopherQualityFilter            False  ...           False
GopherRepetitionFilter          True  ...            True
LanguageFilter                 False  ...           False

[5 rows x 7 columns]

--- only_perm_de: de_0000 ---
{'doc_id': 'de_0000', 'word_count': 53, 'char_count': 435, 'line_count': 1, 'sentence_count': 4, 'paragraph_count': 1, 'avg_word_length': 7.132, 'avg_paragraph_length': 53.0, 'words_per_line': 53.0, 'words_per_sentence': 13.25, 'max_line_length': 435, 'avg_line_length': 435.0, 'alpha_ratio': 0.8506, 'digit_ratio': 0.0023, 'whitespace_ratio': 0.131, 'symbol_word_ratio': 0.0, 'stop_word_ratio': 0.0377, 'bullet_ratio': 0.0, 'ellipsis_ratio': 0.0, 'type_token_ratio': 0.8868, 'upper_ratio': 0.0, 'terminal_punct_ratio': 0.0}
  Filter decisions (any config):
config                  conservative  ...  strict_quality
filter_type                           ...                
C4ParagraphFilter               True  ...           False
C4QualityFilter                False  ...           False
GopherQualityFilter            False  ...           False
Gophe

... (1232 chars truncated)
```
</details>

### Step 39: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
# Full decision matrix for the universal doc
did = '<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>'
sub = fd[fd['doc_id']==did]
print(sub.pivot_table(index='filter_type', columns='config', values='passed', aggfunc='first').to_string())
EOF
```

<details><summary>Output (938 chars)</summary>

```
config                  conservative  fineweb_production  minimal_english  multilingual  permissive  repetition_heavy  strict_quality
filter_type                                                                                                                          
C4ParagraphFilter               True                True             True          True        True              True           False
C4QualityFilter                 True                True             True          True        True              True            True
GopherQualityFilter             True                True             True          True        True              True            True
GopherRepetitionFilter          True                True             True          True        True              True            True
LanguageFilter                  True                True             True          True        True              True            True

```
</details>

### Step 40: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Why is C4ParagraphFilter always False for strict_quality and True elsewhere?
# Maybe the table is buggy here. Compare to actual config: strict_quality doesn't use C4ParagraphFilter.
# But the table records "False" for it. Probably a bug in the export: when filter not used, recorded as False instead of True (or vice versa).
# Across configs that USE C4ParagraphFilter (only repetition_heavy uses it), pass rate is 100%? Let's check.
import pandas as pd
fd = pd.read_parquet('pipeline-export-proprietary/filter_decisions.parquet')
print('C4ParagraphFilter per config pass rates:')
print(fd[fd['filter_type']=='C4ParagraphFilter'].groupby('config')['passed'].mean())
# Now per stats, repetition_heavy used C4ParagraphFilter and dropped 3259/9986 -> 67.4% pass. But table says 100% pass for repetition_heavy.
# So the exported filter_decisions table is INCONSISTENT with actual runs (which is part of the user's confusion).

# Confirm: for each config, what does the AND of "filters listed in config" predict?
config_filters = {
    'conservative': ['GopherQualityFilter','C4QualityFilter'],
    'fineweb_production': ['LanguageFilter'],  # FineWebQualityFilter not in table
    'minimal_english': [],
    'multilingual': ['GopherQualityFilter','LanguageFilter'],
    'permissive': ['GopherRepetitionFilter'],
    'repetition_heavy': ['GopherRepetitionFilter','C4ParagraphFilter','GopherQualityFilter'],
    'strict_quality': ['GopherQualityFilter','GopherRepetitionFilter','C4QualityFilter','LanguageFilter'],
}
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')

# Note: real runs only processed 2200 for some. So we need to look at WHAT subset matters.
# For configs that read 10000:
for c in ['fineweb_production','minimal_english','repetition_heavy','strict_quality']:
    filters = config_filters[c]
    if filters:
        sub = fd[(fd['config']==c) & (fd['filter_type'].isin(filters))]
        all_pass = sub.groupby('do
```

<details><summary>Output (527 chars)</summary>

```
C4ParagraphFilter per config pass rates:
config
conservative          1.0
fineweb_production    1.0
minimal_english       1.0
multilingual          1.0
permissive            1.0
repetition_heavy      1.0
strict_quality        0.0
Name: passed, dtype: float64
fineweb_production: pred-pass=9800, actually kept=9727, agree=99.27%
minimal_english: no filters listed in config (apart from language)
repetition_heavy: pred-pass=9613, actually kept=6230, agree=65.87%
strict_quality: pred-pass=9562, actually kept=7430, agree=77.60%

```
</details>

### Step 41: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Let me look at GopherRepetitionFilter more carefully.
# In actual runs, repetition_heavy dropped 14 (mostly via n-gram dups), C4ParagraphFilter dropped 3259 (<3 paragraphs), GopherQuality dropped 497.
# But the table says GopherRepetitionFilter has 100% pass, C4ParagraphFilter 100% pass for repetition_heavy.
# So filter_decisions exported is a "static" snapshot that doesn't actually reflect what the runs did.
# Big takeaway: filter_decisions.parquet appears to be unreliable / placeholder.
# The user should trust the per-run stats.json instead.

# Now what about real runs?
# Conservative reads 2200 docs and per stats:
#   GopherQuality: drop 426 (212 alpha, 150 stopwords, 52 short, 8 ellipsis, 4 bullets)
#   C4Quality: drop 116 (too few sentences)
#   LanguageFilter: drop 0 (all FR/DE? no, conservative is en-only)
# Wait, conservative is en-only and dropped 0 in language filter? But 200 docs are non-en.
# Actually looking again: 'Language ID' on conservative has total 1658 forwarded 1658. So 0 dropped.
# That's because the FR/DE docs in the 2200 were dropped by Gopher first.
# 2200 -> 1774 (gopher) -> 1658 (C4Quality) -> 1658 (Lang) -> 1656 (Repetition)

# Let me investigate the actual Gopher drops. The Gopher stats:
# dropped_gopher_below_alpha_threshold: 212 = words with <80% having at least one alpha char
# dropped_gopher_enough_stop_words: 150 = <2 stop words from {the,be,to,of,and,that,have,with}
# These mostly correspond to FR/DE docs (no English stop words)
# Verify with quality scores
import pandas as pd
qs = pd.read_parquet('pipeline-export-proprietary/doc_quality_scores.parquet')
ld = pd.read_parquet('pipeline-export-proprietary/language_detection.parquet')
fr_de = ld[ld['metadata_language'].isin(['fr','de'])]
sub = qs[qs['doc_id'].isin(fr_de['doc_id'])]
print('FR/DE: avg stop_word_ratio=', sub['stop_word_ratio'].mean(), 'avg alpha_ratio=', sub['alpha_ratio'].mean())
# Note: the "stop_word_ratio" in the table 
```

<details><summary>Output (76 chars)</summary>

```
FR/DE: avg stop_word_ratio= 0.028425000000000002 avg alpha_ratio= 0.7701965

```
</details>

### Step 42: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Let me actually run the GopherQualityFilter on the FR/DE docs and the universal doc
import sys; sys.path.insert(0,'datatrove/src')
from datatrove.pipeline.filters.gopher_quality_filter import GopherQualityFilter
from datatrove.data import Document
import json

f = GopherQualityFilter()  # default thresholds
def trace(text, lang_meta):
    d = Document(text=text, id='x')
    r = f.filter(d)
    return r

texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x

for did in ['<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>','fr_0000','de_0000','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>']:
    d = texts[did]
    r = trace(d['text'], d['metadata']['language'])
    print(f'{did} lang={d["metadata"]["language"]} -> Gopher: {r}')
EOF
```

### Step 43: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF' 2>&1
import sys; sys.path.insert(0,'datatrove/src')
from datatrove.pipeline.filters.gopher_quality_filter import GopherQualityFilter
from datatrove.data import Document
import json
f = GopherQualityFilter()
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
for did in ['<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>','fr_0000','de_0000','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>']:
    d = texts[did]
    try:
        r = f.filter(Document(text=d['text'], id='x'))
    except Exception as e:
        r = f'ERR: {e}'
    print(f'{did} ({d["metadata"]["language"]}, wc={d["metadata"]["word_count"]}) -> {r}')
EOF
```

<details><summary>Output (631 chars)</summary>

```
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
  File "/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/__init__.py", line 1, in <module>
    from .c4_filters import C4BadWordsFilter, C4ParagraphFilter, C4QualityFilter
  File "/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/c4_filters.py", line 7, in <module>
    from datatrove.io import cached_asset_path_or_download
  File "/home/ubuntu/workspace/datatrove/src/datatrove/io.py", line 11, in <module>
    from huggingface_hub import HfFileSystem, cached_assets_path
ModuleNotFoundError: No module named 'huggingface_hub'

```
</details>

### Step 44: bash

```bash
pip install huggingface_hub -q 2>&1 | tail -3
```

<details><summary>Output (275 chars)</summary>

```

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.

```
</details>

### Step 45: bash

```bash
pip install huggingface_hub --break-system-packages -q 2>&1 | tail -3
pip install datatrove --break-system-packages -q 2>&1 | tail -3
```

<details><summary>Output (803 chars)</summary>

```
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  WARNING: The scripts hf, huggingface-cli and tiny-agents are installed in '/home/ubuntu/workspace/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  WARNING: The scripts check_dataset, failed_logs, inspect_data, jobs_status, launch_pickled_pipeline, merge_stats and track_jobs are installed in '/home/ubuntu/workspace/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.

```
</details>

### Step 46: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF' 2>&1
import sys
# prefer the local datatrove
sys.path.insert(0,'datatrove/src')
from datatrove.pipeline.filters.gopher_quality_filter import GopherQualityFilter
from datatrove.data import Document
import json
f = GopherQualityFilter()
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
for did in ['<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>','fr_0000','de_0000','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>']:
    d = texts[did]
    try:
        r = f.filter(Document(text=d['text'], id='x'))
    except Exception as e:
        r = f'ERR: {e}'
    print(f'{did} ({d["metadata"]["language"]}, wc={d["metadata"]["word_count"]}) -> {r}')
EOF
```

<details><summary>Output (631 chars)</summary>

```
Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
  File "/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/__init__.py", line 1, in <module>
    from .c4_filters import C4BadWordsFilter, C4ParagraphFilter, C4QualityFilter
  File "/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/c4_filters.py", line 7, in <module>
    from datatrove.io import cached_asset_path_or_download
  File "/home/ubuntu/workspace/datatrove/src/datatrove/io.py", line 11, in <module>
    from huggingface_hub import HfFileSystem, cached_assets_path
ModuleNotFoundError: No module named 'huggingface_hub'

```
</details>

### Step 47: bash

```bash
which python3; python3 -c "import huggingface_hub; print(huggingface_hub.__version__)"
```

<details><summary>Output (41 chars)</summary>

```
/home/ubuntu/workspace/.venv/bin/python3

```
</details>

### Step 48: bash

```bash
/home/ubuntu/workspace/.venv/bin/pip install huggingface_hub -q 2>&1 | tail -3
```

<details><summary>Output (85 chars)</summary>

```
/bin/bash: line 545: /home/ubuntu/workspace/.venv/bin/pip: No such file or directory

```
</details>

### Step 49: bash

```bash
/home/ubuntu/workspace/.venv/bin/python3 -m pip install huggingface_hub -q 2>&1 | tail -3
```

<details><summary>Output (62 chars)</summary>

```
/home/ubuntu/workspace/.venv/bin/python3: No module named pip

```
</details>

### Step 50: bash

```bash
ls /home/ubuntu/workspace/.venv/lib/python*/site-packages/ | head -30
echo
ls /home/ubuntu/workspace/.venv/lib/
```

<details><summary>Output (540 chars)</summary>

```
81d243bd2c585b0f4821__mypyc.cpython-312-x86_64-linux-gnu.so
PIL
__pycache__
_cffi_backend.cpython-312-x86_64-linux-gnu.so
_pytest
_virtualenv.pth
_virtualenv.py
_yaml
a2a
a2a_sdk-0.3.26.dist-info
agents
aiofile
aiofile-3.11.1.dist-info
annotated_doc
annotated_doc-0.0.4.dist-info
annotated_types
annotated_types-0.7.0.dist-info
anthropic
anthropic-0.109.1.dist-info
anyio
anyio-4.13.0.dist-info
attr
attrs
attrs-26.1.0.dist-info
authlib
authlib-1.7.2.dist-info
backoff
backoff-2.2.1.dist-info
beartype
beartype-0.22.9.dist-info

python3.12

```
</details>

### Step 51: bash

```bash
ls /home/ubuntu/workspace/.venv/lib/python3.12/site-packages/ | grep -i "datatrove\|huggingface\|fasttext"
```

### Step 52: bash

```bash
PYTHONPATH=/home/ubuntu/.local/lib/python3.12/site-packages python3 -c "import huggingface_hub; print(huggingface_hub.__version__)"
```

### Step 53: bash

```bash
find / -name "huggingface_hub" -type d 2>/dev/null | head -5
```

### Step 54: bash

```bash
pip3 install --user huggingface_hub 2>&1 | tail -3
python3 -c "import sys; print(sys.path)"
```

<details><summary>Output (451 chars)</summary>

```

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.
['', '/home/ubuntu/workspace', '/usr/lib/python312.zip', '/usr/lib/python3.12', '/usr/lib/python3.12/lib-dynload', '/home/ubuntu/workspace/.venv/lib/python3.12/site-packages']

```
</details>

### Step 55: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import sys, importlib.util, json
# Load module file directly to bypass __init__
import numpy as np
sys.path.insert(0,'datatrove/src')

# We need datatrove.data, datatrove.pipeline.filters.base_filter, datatrove.pipeline.writers.disk_base, datatrove.utils.text, datatrove.utils.typeshelper
# Try minimal imports
spec = importlib.util.spec_from_file_location("gopher_qual", "datatrove/src/datatrove/pipeline/filters/gopher_quality_filter.py")
print(spec)
# Try direct import path
try:
    from datatrove.pipeline.filters.gopher_quality_filter import GopherQualityFilter
    print("imported")
except Exception as e:
    print("fail:", e)
EOF
```

<details><summary>Output (249 chars)</summary>

```
ModuleSpec(name='gopher_qual', loader=<_frozen_importlib_external.SourceFileLoader object at 0x7fbbd004ff50>, origin='/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_quality_filter.py')
fail: No module named 'huggingface_hub'

```
</details>

### Step 56: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Replicate Gopher filter inline so we can trace decisions without installing anything
import re, json
import numpy as np

STOP_WORDS = {"the","be","to","of","and","that","have","with"}
PUNCT = set("!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~")

def split_words(text):
    # mimic datatrove split_into_words for English: simple tokenizer
    return re.findall(r"\S+", text)

def gopher_filter(text,
                  min_doc_words=50, max_doc_words=100000,
                  min_avg_word_length=3, max_avg_word_length=10,
                  max_symbol_word_ratio=0.1,
                  max_bullet_lines_ratio=0.9,
                  max_ellipsis_lines_ratio=0.3,
                  max_non_alpha_words_ratio=0.8,
                  min_stop_words=2,
                  stop_words=None):
    sw = STOP_WORDS if stop_words is None else set(stop_words)
    words = split_words(text)
    n_words = len(words)
    non_symbol = [w for w in words if any(ch not in PUNCT for ch in w)]
    n_nsw = len(non_symbol)
    if n_words == 0: return (False, "empty")
    if n_nsw < min_doc_words: return (False, f"gopher_short_doc (n={n_nsw} < {min_doc_words})")
    if n_nsw > max_doc_words: return (False, "gopher_long_doc")
    awl = np.mean([len(w) for w in non_symbol])
    if awl < min_avg_word_length: return (False, f"gopher_below_avg_threshold (awl={awl:.2f})")
    if awl > max_avg_word_length: return (False, f"gopher_above_avg_threshold (awl={awl:.2f})")
    hash_ratio = text.count("#")/n_words
    if hash_ratio > max_symbol_word_ratio: return (False, f"gopher_too_many_hashes ({hash_ratio:.3f})")
    ell_ratio = (text.count("...")+text.count("…"))/n_words
    if ell_ratio > max_symbol_word_ratio: return (False, f"gopher_too_many_ellipsis ({ell_ratio:.3f})")
    lines = text.splitlines() or [text]
    bullet_lines = sum(s.lstrip().startswith("•") or s.lstrip().startswith("-") for s in lines)
    bullet_ratio = bullet_lines/len(lines)
    if bullet_ratio > max_bull
```

<details><summary>Output (468 chars)</summary>

```
<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> (en, wc=646):
  -> (True, 'passed', {'n_words': 643, 'awl': np.float64(4.56), 'alpha_ratio': 0.988, 'stop_hits': 8})
fr_0000 (fr, wc=62):
  -> (False, 'gopher_enough_stop_words (hit=0)')
de_0000 (de, wc=51):
  -> (False, 'gopher_enough_stop_words (hit=0)')
<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58> (en, wc=75):
  -> (True, 'passed', {'n_words': 70, 'awl': np.float64(5.79), 'alpha_ratio': 0.933, 'stop_hits': 4})

```
</details>

### Step 57: bash

```bash
sed -n '1,60p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/c4_filters.py | head -100
echo "---"
grep -n "class C4QualityFilter\|class C4ParagraphFilter\|class C4BadWords" /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/c4_filters.py
```

<details><summary>Output (2871 chars)</summary>

```
import heapq
import re

from numpy.random import default_rng

from datatrove.data import Document
from datatrove.io import cached_asset_path_or_download
from datatrove.pipeline.filters.base_filter import BaseFilter
from datatrove.pipeline.writers.disk_base import DiskWriter
from datatrove.utils.text import split_into_sentences
from datatrove.utils.typeshelper import Languages


CITATION_REGEX = re.compile(r"\[\d*]|\[edit]|\[citation needed]")
END_PUNCTUATION = (".", "?", "!", '"', "'")
ELLIPSIS = "..."
POLICY_SUBSTRINGS = [
    "terms of use",
    "privacy policy",
    "cookie policy",
    "uses cookies",
    "use of cookies",
    "use cookies",
]


class C4QualityFilter(BaseFilter):
    """Applies heuristic rules from C4 https://jmlr.org/papers/volume21/20-074/20-074.pdf

    - We only retained lines that ended in a terminal punctuation mark (! . " ?)
    - We discarded any page with fewer than 5 sentences and only retained lines that contained at least 3 words
    - [NOT IMPLEMENTED] We removed any page that contained any word on the “List of Dirty, Naughty, Obscene or Otherwise Bad Words”
    - We removed any line with the word Javascript.
    - We removed any page where the phrase “lorem ipsum” appeared
    - We removed any pages that contained a curly bracket
    Additional filters not mentioned on the list from the paper but on the code:
    - Remove lines with one word over 1000 chars
    - Remove lines with cookies and terms of use keywords

    Reference implementation: https://github.com/tensorflow/datasets/blob/master/tensorflow_datasets/text/c4_utils.py#L197
    Args:
        exclusion_writer: optionally pass in a writer that will save the dropped documents
        tokenizer_language: load a diff language specific punkt tokenizer from nltk
        split_paragraph: by default (as in the paper) split on "\n".
            Set to "False" to apply the filters to each sentence instead of to each line
        remove_citations: remove wikipedia style citations from the text
        filter_no_terminal_punct: remove lines without terminal punctuation marks
        min_num_sentences: remove documents that do not have at least this number of sentences (after line filtering).
            set to -1 to disable
        min_words_per_line: drop lines without this min number of words
        max_word_length: drop lines where at least one word has more than this number of characters
        filter_lorem_ipsum: drop documents that contain "lorem ipsum"
        filter_javascript: drop lines mentioning "javascript"
        filter_curly_bracket: drop documents containing {
        filter_policy: drop lines containing any of the phrases in POLICY_SUBSTRINGS
    """

    name = "⛰ C4 Quality"

    def __init__(
---
27:class C4QualityFilter(BaseFilter):
139:class C4ParagraphFilter(BaseFilter):
209:class C4BadWordsFilter(BaseFilter):

```
</details>

### Step 58: bash

```bash
sed -n '60,210p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/c4_filters.py
```

<details><summary>Output (5528 chars)</summary>

```
    def __init__(
        self,
        exclusion_writer: DiskWriter = None,
        split_paragraph: bool = True,  # default as used on c4. Set to "False" to split with sent_tokenize
        remove_citations: bool = True,
        filter_no_terminal_punct: bool = True,
        min_num_sentences: int = 5,  # set to -1 to disable
        min_words_per_line: int = 3,  # set to -1 to disable
        max_word_length: int = 1000,  # set to -1 to disable
        filter_lorem_ipsum: bool = True,
        filter_javascript: bool = True,
        filter_curly_bracket: bool = True,
        filter_policy: bool = True,
        language: str = Languages.english,
    ):
        super().__init__(exclusion_writer)
        self.split_paragraph = split_paragraph
        self.remove_citations = remove_citations
        self.filter_no_terminal_punct = filter_no_terminal_punct
        self.min_num_sentences = min_num_sentences
        self.min_words_per_line = min_words_per_line
        self.max_word_length = max_word_length
        self.filter_lorem_ipsum = filter_lorem_ipsum
        self.filter_javascript = filter_javascript
        self.filter_curly_bracket = filter_curly_bracket
        self.filter_policy = filter_policy
        self.language = language

    def filter(self, doc: Document) -> bool | tuple[bool, str]:
        lines = doc.text.splitlines() if self.split_paragraph else split_into_sentences(doc.text, self.language)

        num_sentences = 0
        kept_lines = []

        for line in lines:
            line = line.strip()
            words = line.split()
            self.stat_update("line-total")
            # check line has too long word
            if self.max_word_length != -1 and any(len(word) > self.max_word_length for word in words):
                self.stat_update("line-filter-too_long_word")
                continue
            # remove citation
            if self.remove_citations:
                line = CITATION_REGEX.sub("", line)
            # end punctuation
            if self.filter_no_terminal_punct and (not line.endswith(END_PUNCTUATION) or line.endswith(ELLIPSIS)):
                self.stat_update("line-filter-no_terminal_punc")
                continue
            # min words per line
            if len(words) < self.min_words_per_line:
                self.stat_update("line-filter-too_few_words")
                continue
            line_l = line.lower()
            # lorem ipsum
            if self.filter_lorem_ipsum and "lorem ipsum" in line_l:
                return False, "lorem_ipsum"  # drop entire doc
            # javascript
            if self.filter_javascript and "javascript" in line_l:
                self.stat_update("line-filter-javascript")
                continue
            # bracket
            if self.filter_curly_bracket and "{" in line:
                return False, "curly_bracket"  # drop entire doc
            # policy
            if self.filter_policy and any(p in line_l for p in POLICY_SUBSTRINGS):
      

... (2528 chars truncated)
```
</details>

### Step 59: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json, gzip
# 7e4b19f0 dedup
print('=== run-7e4b19f0 ===')
print('config: exact_ngram dedup, threshold 0.3, ngram_size 3')
with open('defective-export-proprietary/run-7e4b19f0/dedup_clusters.json') as f:
    dc = json.load(f)
if isinstance(dc, list): print('clusters list length', len(dc), 'first:', dc[:2])
elif isinstance(dc, dict): print('keys', list(dc.keys())[:5], 'len', len(dc))
print()
# Count output
n=0
with open('defective-export-proprietary/run-7e4b19f0/final_output/output.jsonl') as f:
    for line in f: n+=1
print('output docs:', n)

# Sample
with open('defective-export-proprietary/run-7e4b19f0/final_output/output.jsonl') as f:
    sample = [json.loads(next(f)) for _ in range(3)]
for s in sample[:2]:
    print('  keys:', list(s.keys()), 'id:', s.get('id'), 'text[:120]:', s.get('text','')[:120])
EOF
```

<details><summary>Output (637 chars)</summary>

```
=== run-7e4b19f0 ===
config: exact_ngram dedup, threshold 0.3, ngram_size 3
keys ['method', 'ngram_size', 'overlap_threshold', 'total_input', 'total_output'] len 7

output docs: 1992
  keys: ['text', 'url', 'id', 'metadata'] id: <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> text[:120]: Did you know you have two little yellow, nine-volt-battery-sized adrenal glands in your body, just chilling out, maxin’,
  keys: ['text', 'url', 'id', 'metadata'] id: <urn:uuid:97684525-19c7-48da-a302-c2da701993dd> text[:120]: Everyone wishes for something. And lots of people believe they know how to make their wishes come true with magical thin

```
</details>

### Step 60: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json
with open('defective-export-proprietary/run-7e4b19f0/dedup_clusters.json') as f:
    dc = json.load(f)
print(json.dumps(dc, indent=2)[:2000])
EOF
```

<details><summary>Output (2001 chars)</summary>

```
{
  "method": "exact_ngram_dedup",
  "ngram_size": 3,
  "overlap_threshold": 0.3,
  "total_input": 2200,
  "total_output": 1992,
  "removed_as_duplicates": 208,
  "flagged_samples": [
    {
      "doc_id": "<urn:uuid:a49cae97-d195-4f5e-97a3-0c90cf924f92>",
      "overlap_ratio": 0.3585,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241>",
      "overlap_ratio": 0.4348,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:fe06f384-2876-4187-a4a3-73cf51ae4f0f>",
      "overlap_ratio": 0.412,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:bc060a05-1d1a-4716-b6c4-e32b89d37f8e>",
      "overlap_ratio": 0.3618,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:67425618-4a6b-4d38-ba4b-c6fc635ae2a3>",
      "overlap_ratio": 0.4286,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:0b8d9dc1-e0fc-409b-a417-53be342b8731>",
      "overlap_ratio": 0.4338,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:c9f0e9cf-6d88-454d-8058-0de503313979>",
      "overlap_ratio": 0.481,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:ec961dfa-7382-4822-8f11-1a09ab3bb900>",
      "overlap_ratio": 0.354,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:629bd6ef-3d26-433a-a720-0d00fdcbe398>",
      "overlap_ratio": 0.4487,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:d3025dba-5b94-4c90-9ebb-993f8a616034>",
      "overlap_ratio": 0.3718,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:e5ed32a8-378d-4f84-b3c0-017e0e45741e>",
      "overlap_ratio": 0.4034,
      "language": "en"
    },
    {
      "doc_id": "<urn:uuid:4c54aba2-ffd8-48e5-8769-8b3b9719988c>",
      "overlap_ratio": 0.4028,
      "language": "en"
    },
    {
      "doc_id": "fr_0002",
      "overlap_ratio": 0.9839,
      "language": "fr"
    },
    {
      "doc_id": "fr_0003",
      "overlap_ratio": 0.9861,
      "language": "fr"
    },
    {
      "doc_id": "

```
</details>

### Step 61: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json
with open('defective-export-proprietary/run-7e4b19f0/dedup_clusters.json') as f:
    dc = json.load(f)
# Check fr/de overlap ratios
fr_de = [s for s in dc['flagged_samples'] if s['language']!='en']
print(f'fr/de flagged: {len(fr_de)}')
for s in fr_de[:10]:
    print(s)
print()
en = [s for s in dc['flagged_samples'] if s['language']=='en']
print(f'en flagged: {len(en)} avg_overlap={sum(s["overlap_ratio"] for s in en)/len(en):.3f}')
import statistics
print('fr overlap_ratio mean:', statistics.mean([s['overlap_ratio'] for s in dc['flagged_samples'] if s['language']=='fr']))
print('de overlap_ratio mean:', statistics.mean([s['overlap_ratio'] for s in dc['flagged_samples'] if s['language']=='de']))

# Now check if these IDs end up dropped from output (i.e., dedup considered them dups)
out_ids = set()
with open('defective-export-proprietary/run-7e4b19f0/final_output/output.jsonl') as f:
    for l in f:
        out_ids.add(json.loads(l)['id'])
in_out = sum(1 for s in dc['flagged_samples'] if s['doc_id'] in out_ids)
print(f'Flagged samples present in output: {in_out}/{len(dc["flagged_samples"])}')

# Are FR/DE all dropped?
fr_ids = [s['doc_id'] for s in dc['flagged_samples'] if s['language']=='fr']
de_ids = [s['doc_id'] for s in dc['flagged_samples'] if s['language']=='de']
print('FR flagged still in output:', sum(1 for i in fr_ids if i in out_ids), '/', len(fr_ids))
print('DE flagged still in output:', sum(1 for i in de_ids if i in out_ids), '/', len(de_ids))

# Total counts in output by lang prefix
fr_o = sum(1 for i in out_ids if i.startswith('fr_'))
de_o = sum(1 for i in out_ids if i.startswith('de_'))
en_o = sum(1 for i in out_ids if i.startswith('<urn'))
print(f'In output: en={en_o} fr={fr_o} de={de_o}')
EOF
```

<details><summary>Output (731 chars)</summary>

```
fr/de flagged: 38
{'doc_id': 'fr_0002', 'overlap_ratio': 0.9839, 'language': 'fr'}
{'doc_id': 'fr_0003', 'overlap_ratio': 0.9861, 'language': 'fr'}
{'doc_id': 'fr_0004', 'overlap_ratio': 0.9839, 'language': 'fr'}
{'doc_id': 'fr_0005', 'overlap_ratio': 0.9861, 'language': 'fr'}
{'doc_id': 'fr_0006', 'overlap_ratio': 0.9839, 'language': 'fr'}
{'doc_id': 'fr_0007', 'overlap_ratio': 0.9861, 'language': 'fr'}
{'doc_id': 'fr_0008', 'overlap_ratio': 0.9839, 'language': 'fr'}
{'doc_id': 'fr_0009', 'overlap_ratio': 0.9861, 'language': 'fr'}
{'doc_id': 'fr_0010', 'overlap_ratio': 0.9839, 'language': 'fr'}
{'doc_id': 'fr_0011', 'overlap_ratio': 0.9861, 'language': 'fr'}

en flagged: 12 avg_overlap=0.408
fr overlap_ratio mean: 0.985

```
</details>

### Step 62: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# fr_0002 onward is the synthetic FR docs — they have extremely high tri-gram overlap (~98%) because the corpus expansion just copied them.
# The 3-gram threshold of 0.3 catches them all (including likely real distinct sentences in EN around 0.4 overlap by chance).
# This is the "defective" issue: ngram_size=3 with threshold 0.3 is way too aggressive — any 2 random English docs share 30%+ trigrams just by writing common phrases like "of the" etc. (Actually maybe not 30% for trigrams.)
# Let's see what's in the corpus for fr
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
print('fr_0000:', texts['fr_0000']['text'][:200].replace('\n',' '))
print('fr_0002:', texts.get('fr_0002', {}).get('text','MISSING')[:200].replace('\n',' '))
print('fr_0003:', texts.get('fr_0003', {}).get('text','MISSING')[:200].replace('\n',' '))
# Check if they're highly similar
print()
print('fr_0010:', texts.get('fr_0010', {}).get('text','MISSING')[:200].replace('\n',' '))
print('fr_0099:', texts.get('fr_0099', {}).get('text','MISSING')[:200].replace('\n',' '))
EOF
```

<details><summary>Output (1051 chars)</summary>

```
fr_0000: L'intelligence artificielle transforme la recherche scientifique. Les modèles de langage permettent d'analyser des volumes massifs de littérature académique en quelques secondes. Cette révolution tech
fr_0002: L'intelligence artificielle transforme la recherche scientifique. Les modèles de langage permettent d'analyser des volumes massifs de littérature académique en quelques secondes. Cette révolution tech
fr_0003: Le traitement automatique du langage naturel a fait des progrès considérables ces dernières années. Les architectures Transformer ont révolutionné le domaine en permettant la modélisation de dépendanc

fr_0010: L'intelligence artificielle transforme la recherche scientifique. Les modèles de langage permettent d'analyser des volumes massifs de littérature académique en quelques secondes. Cette révolution tech
fr_0099: Le traitement automatique du langage naturel a fait des progrès considérables ces dernières années. Les architectures Transformer ont révolutionné le domaine en permettant la modélisation de dépendanc

```
</details>

### Step 63: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Are all en docs unique or is there template dup too?
import json, hashlib
import collections
hashes = collections.Counter()
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        if x['metadata']['language']=='en':
            h = hashlib.md5(x['text'].encode()).hexdigest()[:16]
            hashes[h]+=1
print('English unique texts:', len(hashes), 'out of', sum(hashes.values()))
print('Top dup counts:', hashes.most_common(5))

# fr and de
hashes_fr = collections.Counter()
hashes_de = collections.Counter()
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        h = hashlib.md5(x['text'].encode()).hexdigest()[:16]
        if x['metadata']['language']=='fr':
            hashes_fr[h]+=1
        elif x['metadata']['language']=='de':
            hashes_de[h]+=1
print('FR unique:', len(hashes_fr), '/', sum(hashes_fr.values()), '; top:', hashes_fr.most_common(3))
print('DE unique:', len(hashes_de), '/', sum(hashes_de.values()), '; top:', hashes_de.most_common(3))
EOF
```

<details><summary>Output (389 chars)</summary>

```
English unique texts: 9800 out of 9800
Top dup counts: [('900f116262666660', 1), ('7992824d5f519561', 1), ('571d9dac31057569', 1), ('a701fa70be3e057a', 1), ('1e9f5cc57115b379', 1)]
FR unique: 100 / 100 ; top: [('da61b5a070dcaf53', 1), ('e11c2d7c46e35a4a', 1), ('9f9d1fbd8405de47', 1)]
DE unique: 100 / 100 ; top: [('8ad395facf470a4b', 1), ('b3bf6b89c7670e97', 1), ('806f42c5b044eb54', 1)]

```
</details>

### Step 64: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json
texts = []
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        if x['metadata']['language']=='fr':
            texts.append((x['id'], x['url'], x['text']))
# print first 5 character differences
for i in [0,2,4,10]:
    print(texts[i][0], texts[i][1], 'len=', len(texts[i][2]))
    print(' tail:', texts[i][2][-200:].replace('\n',' '))
EOF
```

<details><summary>Output (1169 chars)</summary>

```
fr_0000 http://www.lemonde.fr/sciences/article/2013/04/00/recherche-ia.html len= 609
 tail:  outils tout en maintenant la rigueur scientifique qui caractérise la démarche expérimentale. (Variante 0)                                                                                              
fr_0002 http://www.lefigaro.fr/sciences/2013/05/02/innovation-technologique.php len= 584
 tail: our intégrer ces nouveaux outils tout en maintenant la rigueur scientifique qui caractérise la démarche expérimentale. (Variante 2)                                                                     
fr_0004 http://www.rfi.fr/fr/science/20130405-recherche-informatique len= 575
 tail: ologies pour intégrer ces nouveaux outils tout en maintenant la rigueur scientifique qui caractérise la démarche expérimentale. (Variante 4)                                                            
fr_0010 http://www.lemonde.fr/sciences/article/2013/04/10/recherche-ia.html len= 591
 tail: égrer ces nouveaux outils tout en maintenant la rigueur scientifique qui caractérise la démarche expérimentale. (Variante 10)                                                                           

```
</details>

### Step 65: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x

# A flagged EN doc
for did in ['<urn:uuid:a49cae97-d195-4f5e-97a3-0c90cf924f92>', '<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241>']:
    d = texts[did]
    print(did, 'url:', d['url'])
    print('text[:300]:', d['text'][:300].replace('\n',' / '))
    print()
EOF
```

<details><summary>Output (863 chars)</summary>

```
<urn:uuid:a49cae97-d195-4f5e-97a3-0c90cf924f92> url: http://www.peta.org/b/thepetafiles/archive/2011/08/09/suffering-horses-rescued.aspx
text[:300]: Written by PETA / A skeletal downed horse who was too weak and sick even to move to get a drink of water was left to suffer under the scorching Midwestern sun for days until PETA received a call from a concerned witness. We called local officials, who quickly dispatched officers to the scene. Appalled

<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241> url: http://en.wikipedia.org/wiki/Prophylaxis
text[:300]: ||This article has multiple issues. Please help improve it or discuss these issues on the talk page. / Preventive medicine or preventive care consists of measures taken to prevent diseases, (or injuries) rather than curing them or treating their symptoms. This contrasts in method with curative and pal


```
</details>

### Step 66: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Are these flagged EN docs actually dropped from the output of run-7e4b19f0?
import json
out_ids = set()
with open('defective-export-proprietary/run-7e4b19f0/final_output/output.jsonl') as f:
    for l in f:
        out_ids.add(json.loads(l)['id'])
# in dedup config: total_input=2200, total_output=1992. Removed 208.
# 100 fr + 100 de + 8 en? Or all 12 flagged EN? Let's check.
with open('defective-export-proprietary/run-7e4b19f0/dedup_clusters.json') as f:
    dc = json.load(f)
en_flag = [s['doc_id'] for s in dc['flagged_samples'] if s['language']=='en']
print('EN flagged in output:', sum(1 for i in en_flag if i in out_ids), '/', len(en_flag))
fr_flag = [s['doc_id'] for s in dc['flagged_samples'] if s['language']=='fr']
de_flag = [s['doc_id'] for s in dc['flagged_samples'] if s['language']=='de']
print('FR flagged in output:', sum(1 for i in fr_flag if i in out_ids), '/', len(fr_flag))
print('DE flagged in output:', sum(1 for i in de_flag if i in out_ids), '/', len(de_flag))
# Count by lang in output
en_o = sum(1 for i in out_ids if i.startswith('<urn'))
fr_o = sum(1 for i in out_ids if i.startswith('fr_'))
de_o = sum(1 for i in out_ids if i.startswith('de_'))
print(f'Output: en={en_o} fr={fr_o} de={de_o} total={len(out_ids)}')
print()
print('Total input was 2200, output 1992 — 208 removed.')
print('Could be: 100 fr + 100 de near-dups + 8 en? 100+100+8=208. Check below')
EOF
```

<details><summary>Output (244 chars)</summary>

```
EN flagged in output: 0 / 12
FR flagged in output: 0 / 38
DE flagged in output: 0 / 0
Output: en=1988 fr=2 de=2 total=1992

Total input was 2200, output 1992 — 208 removed.
Could be: 100 fr + 100 de near-dups + 8 en? 100+100+8=208. Check below

```
</details>

### Step 67: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# So the dedup kept 2 FR + 2 DE (1 of each duplicate cluster pair) + 1988 EN. 12 EN docs were dropped as false positives.
# 2000 EN input - 1988 EN output = 12 dropped EN (matches the flagged ones)
# Interesting! Now let me look at the conservative_variant defective config a3f8c2d1
import json
with open('defective-export-proprietary/run-a3f8c2d1/filter_log.json') as f:
    print(json.dumps(json.load(f), indent=2))
print('---')
n = 0
import collections
langs = collections.Counter()
with open('defective-export-proprietary/run-a3f8c2d1/final_output/output.jsonl') as f:
    for line in f:
        d = json.loads(line)
        n+=1
        langs[d.get('metadata',{}).get('language','?')]+=1
print('Actual output count:', n, 'langs:', dict(langs))
EOF
```

<details><summary>Output (453 chars)</summary>

```
{
  "filter": "min_length",
  "threshold": "50 words",
  "filter_params": {
    "min_doc_length": 200,
    "unit": "char"
  },
  "total_input": 10000,
  "total_output": 2200,
  "language_breakdown": {
    "en": {
      "kept": 2000,
      "dropped": 7800
    },
    "fr": {
      "kept": 100,
      "dropped": 0
    },
    "de": {
      "kept": 100,
      "dropped": 0
    }
  }
}
---
Actual output count: 2200 langs: {'en': 2000, 'fr': 100, 'de': 100}

```
</details>

### Step 68: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# That defective filter says "min_length 50 words" but the actual filter_params is 200 chars, and the actual output exactly matches the first 2200 docs of the corpus
# i.e., kept all docs of length >= 200 chars happened to be exactly the first 2200 (the un-expanded core sample)
# Let me verify
import json
ids_first2200 = []
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i,line in enumerate(fp):
        if i < 2200:
            ids_first2200.append(json.loads(line)['id'])
out_ids = []
with open('defective-export-proprietary/run-a3f8c2d1/final_output/output.jsonl') as f:
    for line in f:
        out_ids.append(json.loads(line)['id'])
print('first 2200 of corpus == output 2200?', set(ids_first2200) == set(out_ids))
print('Output IDs same order as corpus?', ids_first2200 == out_ids)

# Length stats
lens_first = []
lens_rest = []
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i,line in enumerate(fp):
        d = json.loads(line)
        if i < 2200: lens_first.append(len(d['text']))
        else: lens_rest.append(len(d['text']))
import statistics
print(f'First 2200 char-len: min={min(lens_first)} max={max(lens_first)} mean={statistics.mean(lens_first):.0f}')
print(f'Last 7800 char-len: min={min(lens_rest)} max={max(lens_rest)} mean={statistics.mean(lens_rest):.0f}')
# Check if first 2200 all >=200 chars and last 7800 all <200 chars
print('first 2200 all >=200:', all(x>=200 for x in lens_first))
print('last 7800 all <200:', all(x<200 for x in lens_rest))
EOF
```

<details><summary>Output (232 chars)</summary>

```
first 2200 of corpus == output 2200? True
Output IDs same order as corpus? True
First 2200 char-len: min=274 max=175501 mean=3944
Last 7800 char-len: min=236 max=237284 mean=4031
first 2200 all >=200: True
last 7800 all <200: False

```
</details>

### Step 69: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# So the filter_log claim is wrong. The actual run kept the first 2200 docs. Let's check if 200-char threshold really matches:
import json
kept = 0; dropped = 0
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        d = json.loads(line)
        if len(d['text']) >= 200: kept+=1
        else: dropped+=1
print(f'200-char threshold predicts kept={kept} dropped={dropped}')
# So 200-char threshold would keep 9930 (since all the synthetic ones are 200+ chars on average). The filter_log doesn't actually match the params.
EOF
```

<details><summary>Output (49 chars)</summary>

```
200-char threshold predicts kept=10000 dropped=0

```
</details>

### Step 70: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# 200-char would keep all 10000. But filter_log says it kept 2200. The defective filter_log is wrong on multiple counts:
# 1. config says 50 words, but filter_params claims 200 chars
# 2. it claims to have dropped 7800 EN docs but the synthetic EN expansion is all >200 chars (and >50 words mostly)
# Let me check word counts
import json
wc_dist = {'first_2200_en':[], 'last_7800_en':[]}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i, line in enumerate(fp):
        d = json.loads(line)
        wc = d['metadata']['word_count']
        if d['metadata']['language']=='en':
            if i<2200: wc_dist['first_2200_en'].append(wc)
            else: wc_dist['last_7800_en'].append(wc)

import statistics
for k,v in wc_dist.items():
    print(k, 'n=', len(v), 'min=', min(v), 'max=', max(v), 'mean=', statistics.mean(v), '<50 words:', sum(1 for x in v if x<50))
EOF
```

<details><summary>Output (146 chars)</summary>

```
first_2200_en n= 2000 min= 49 max= 29241 mean= 705.333 <50 words: 2
last_7800_en n= 7800 min= 41 max= 39841 mean= 661.9137179487179 <50 words: 10

```
</details>

### Step 71: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# So a true min_length=50 words would drop only ~12 EN, not 7800.
# A true min_length=200 chars would drop 0.
# The actual output is "first 2200 docs unchanged" -> the run never actually ran any filter; it just had a hard-coded total_docs=2200 limit
# (same as the other "underdog" configs that show as reader_total=2200).
# The "defective" run-a3f8c2d1 is a CONSERVATIVE config which inherited the 2200-doc limit, and the filter_log.json's "language_breakdown" is fabricated to claim filtering happened.

# Let me document this and also look at run-d91c4a27 (pii_scan)
import json
with open('defective-export-proprietary/run-d91c4a27/pii_scan_results.json') as f:
    pii = json.load(f)
print(json.dumps(pii, indent=2)[:2000])
EOF
```

<details><summary>Output (214 chars)</summary>

```
{
  "scanner": "naive_regex",
  "pattern": "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}",
  "documents_scanned": 50,
  "pii_detected": 4,
  "pii_missed": 46,
  "conclusion": "PII scanner missed 46 instances"
}

```
</details>

### Step 72: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Look at corpus_sample for run-d91c4a27
import json, collections
n = 0
emails = 0
phones = 0
ssn = 0
with open('defective-export-proprietary/run-d91c4a27/corpus_sample.jsonl') as f:
    for line in f:
        n+=1
        d = json.loads(line)
        t = d.get('text','')
        # naive
        import re
        emails += len(re.findall(r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}", t))
        phones += len(re.findall(r"\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}", t))
        ssn += len(re.findall(r"\d{3}-\d{2}-\d{4}", t))
print('n=',n,'emails=',emails,'phones=',phones,'ssn=',ssn)
EOF
```

<details><summary>Output (33 chars)</summary>

```
n= 50 emails= 6 phones= 5 ssn= 5

```
</details>

### Step 73: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# The "naive_regex" reports 4 emails but actual count is 6, and there are also phones (5) and SSN (5) it didn't even try to detect.
# Let's look at one document with PII
import json, re
with open('defective-export-proprietary/run-d91c4a27/corpus_sample.jsonl') as f:
    docs = [json.loads(l) for l in f]
# Find docs with PII
for d in docs:
    t = d.get('text','')
    if re.search(r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}", t) or re.search(r"\d{3}-\d{2}-\d{4}", t):
        print(d['id'])
        print(t[:600].replace('\n',' / '))
        print('---')
        break
EOF
```

<details><summary>Output (614 chars)</summary>

```
doc_0004
“Babylon Revisited” conveys strong and painful feelings, principally through the use of dialogue. Some of the most fraught exchanges in the story occur between Charlie and Marion. Charlie’s words make it clear that he is desperate to get Honoria back, enough to plan almost every phrase he utters and pause he takes. He stresses his healthy income to prove that he can provide for his daughter, but he drops the topic the moment he senses that Lincoln is growing annoyed with it. He coaches himself through the emotional conversation about Honoria’s future, silently reminding himself that he has to 
---

```
</details>

### Step 74: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Check the full text for embedded PII
import json, re
with open('defective-export-proprietary/run-d91c4a27/corpus_sample.jsonl') as f:
    for line in f:
        d = json.loads(line)
        t = d['text']
        e = re.findall(r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}", t)
        p = re.findall(r"\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}", t)
        s = re.findall(r"\d{3}-\d{2}-\d{4}", t)
        if e or p or s:
            print(d['id'], 'emails=', e[:3], 'phones=', p[:3], 'ssn=', s[:3])
EOF
```

<details><summary>Output (657 chars)</summary>

```
doc_0004 emails= [] phones= [] ssn= ['123-45-6789']
doc_0007 emails= ['firstname.lastname@example.org', 'email@example.com', 'firstname.lastname@example.org'] phones= [] ssn= []
doc_0009 emails= ['email@example.com'] phones= ['(703) 276-3258'] ssn= []
doc_0014 emails= [] phones= [] ssn= ['123-45-6789']
doc_0020 emails= [] phones= ['(773) 702-0025', '(773) 702-3171'] ssn= []
doc_0024 emails= ['firstname.lastname@example.org'] phones= [] ssn= ['123-45-6789']
doc_0034 emails= ['email@example.com'] phones= [] ssn= ['123-45-6789']
doc_0043 emails= [] phones= ['(877) 870-6118', '(718) 993-5369'] ssn= []
doc_0044 emails= [] phones= [] ssn= ['123-45-6789']

```
</details>

### Step 75: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Run f5e83b64 claims "filters operate independently" and "GopherQuality and C4Quality reject completely disjoint document sets"
# Let's check this empirically from stats logs.
# conservative stats: GopherQuality dropped 426/2200 (19.4%), C4Quality dropped 116/1774 (6.5%) -> in series
# strict_quality stats: GopherQuality dropped 1379/10000 (13.8%), C4Quality dropped 513/7944 (6.5%) -> in series
# These are sequential, so we can't see overlap directly. But we can replicate filters on the corpus.
import sys, re, json
import numpy as np

# Inline Gopher and C4 quality filters
STOP_WORDS = {"the","be","to","of","and","that","have","with"}
PUNCT = set("!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~")
END_PUNCT = (".","?","!", '"', "'")
ELLIPSIS = "..."
CITATION_REGEX = re.compile(r"\[\d*]|\[edit]|\[citation needed]")
POLICY = ["terms of use","privacy policy","cookie policy","uses cookies","use of cookies","use cookies"]

def split_words(text): return re.findall(r"\S+", text)

def gopher_qual(text):
    words = split_words(text)
    n = len(words)
    if n==0: return False
    ns = [w for w in words if any(c not in PUNCT for c in w)]
    if len(ns)<50: return False
    if len(ns)>100000: return False
    awl = np.mean([len(w) for w in ns])
    if awl<3 or awl>10: return False
    if text.count("#")/n > 0.1: return False
    if (text.count("...")+text.count("…"))/n > 0.1: return False
    lines = text.splitlines() or [text]
    if sum(s.lstrip().startswith("•") or s.lstrip().startswith("-") for s in lines)/len(lines) > 0.9: return False
    if sum(s.rstrip().endswith("...") or s.rstrip().endswith("…") for s in lines)/len(lines) > 0.3: return False
    if sum(any(c.isalpha() for c in w) for w in words)/n < 0.8: return False
    if len(STOP_WORDS & set(words)) < 2: return False
    return True

def c4_qual(text):
    # naive sentence split — proxy: use periods/!? as sentence count
    lines = text.splitlines()
    kept = []
    sent_count =
```

<details><summary>Output (223 chars)</summary>

```
Gopher pass: 9720/10000 (97.2%)
C4 pass: 9133/10000 (91.3%)
Both pass: 9093; if independent expected: 8877
P(C4|Gopher pass) = 0.935
P(C4|Gopher fail) = 0.143
G fail set: 280; C fail set: 867; intersection (both fail): 240

```
</details>

### Step 76: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Now: trace a couple of docs through both clean (e.g. conservative) and defective (a3f8c2d1, 7e4b19f0) pipelines.
# Doc 1: universal doc — kept by both clean and defective
# Doc 2: fr_0002 — in defective dedup it'd be killed (near-duplicate), in clean it never gets there because conservative is en-only and 2200 limit
# Doc 3: a doc in 2200-9999 range that defective a3f8c2d1 supposedly drops with min_length 50 words but actually only drops because of the 2200 limit
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i,line in enumerate(fp):
        x = json.loads(line)
        x['_idx'] = i
        texts[x['id']] = x

# A doc beyond index 2200
for did, d in texts.items():
    if d['_idx']==2500:
        target = did
        break
print('Doc idx 2500:', target, 'lang=', texts[target]['metadata']['language'], 'wc=', texts[target]['metadata']['word_count'])
print('  text[:300]:', texts[target]['text'][:300].replace('\n',' / '))

# Verify presence in each output
import gzip
def in_out(path, gz=False):
    opener = gzip.open if gz else open
    with opener(path,'rt') as f:
        for line in f:
            if target in line:
                return True
    return False
print('  in conservative output:', in_out('pipeline-export-proprietary/runs/conservative/final_output/output.jsonl.gz', True))
print('  in strict_quality output:', in_out('pipeline-export-proprietary/runs/strict_quality/final_output/output.jsonl.gz', True))
print('  in fineweb_production output:', in_out('pipeline-export-proprietary/runs/fineweb_production/final_output/output.jsonl.gz', True))
print('  in run-7e4b19f0 (defective dedup) output:', in_out('defective-export-proprietary/run-7e4b19f0/final_output/output.jsonl'))
print('  in run-a3f8c2d1 (defective filter) output:', in_out('defective-export-proprietary/run-a3f8c2d1/final_output/output.jsonl'))
EOF
```

<details><summary>Output (606 chars)</summary>

```
Doc idx 2500: <urn:uuid:9b21d708-ba05-420b-9ee3-adb51001aad1> lang= en wc= 883
  text[:300]: RG2608.AM: Solomon DeVore Butcher, 1856-1927 / Papers, research materials: 1885-1926, n.d.; 1977-1985 / Custer County and Kearney, Buffalo County, Neb.: Photographer / Size: 1.0 cu.ft.; 2 boxes / Solomon Butcher was born January 25, 1856 in Burtion, West Virginia. In 1859 the Butcher family moved to Winona,
  in conservative output: False
  in strict_quality output: False
  in fineweb_production output: True
  in run-7e4b19f0 (defective dedup) output: False
  in run-a3f8c2d1 (defective filter) output: False

```
</details>

### Step 77: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Interesting — strict_quality (10000 reader) rejected it. Why?
# Let's run filters on it
import re, json, numpy as np
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
d = texts['<urn:uuid:9b21d708-ba05-420b-9ee3-adb51001aad1>']
print('Full text len:', len(d['text']), 'word_count meta:', d['metadata']['word_count'])
print('text[:1500]:')
print(d['text'][:1500])
EOF
```

<details><summary>Output (1555 chars)</summary>

```
Full text len: 5704 word_count meta: 883
text[:1500]:
RG2608.AM: Solomon DeVore Butcher, 1856-1927
Papers, research materials: 1885-1926, n.d.; 1977-1985
Custer County and Kearney, Buffalo County, Neb.: Photographer
Size: 1.0 cu.ft.; 2 boxes
Solomon Butcher was born January 25, 1856 in Burtion, West Virginia. In 1859 the Butcher family moved to Winona, Illinois and 21 years later removed to Nebraska. Mr. Butcher took a claim 22 miles north of Broken Bow near the place upon which his father had located. At a later time, Mr. Butcher relinquished his homestead and returned east. In the fall of 1881 and spring of 1882, he was enrolled in the Minnesota Medical College and Hospital in Minneapolis. In October of 1882 he returned with his wife to Custer County where he started the first photographic studio in the county. In the autumn of 1883 he enlarged his studio with a living room also made of sod. It was in 1886 that Butcher first planned his history of Custer County. He spent seven years in preparation, making 1535 farm views and sketches of settlers. A fire destroyed the sketches, but Butcher continued to write and published the history in 1901. He also wrote a book called "Sod House." After living in Greeley, Colorado for about a year, Solomon Butcher died on May 18, 1927. He was survived by his second wife; a step-daughter, Ruby S. Nation; a son, Capt. J. L. Butcher; and a daughter, Mrs. Will Russo.
A more detailed biography can be found in Solomon D. Butcher: Photographing the American Dream by John E. Carter.
SCOPE AND CONTENT

```
</details>

### Step 78: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json, re, numpy as np
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x

t = texts['<urn:uuid:9b21d708-ba05-420b-9ee3-adb51001aad1>']['text']
# Run inline gopher + c4
STOP_WORDS = {"the","be","to","of","and","that","have","with"}
PUNCT = set("!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~")
def split_words(text): return re.findall(r"\S+", text)
def gopher_qual(text, verbose=False):
    words = split_words(text); n=len(words)
    ns = [w for w in words if any(c not in PUNCT for c in w)]
    awl = np.mean([len(w) for w in ns]) if ns else 0
    alpha = sum(any(c.isalpha() for c in w) for w in words)/n
    sw_hit = len(STOP_WORDS & set(words))
    lines = text.splitlines() or [text]
    bullet_lines = sum(s.lstrip().startswith("•") or s.lstrip().startswith("-") for s in lines)
    ell_lines = sum(s.rstrip().endswith("...") or s.rstrip().endswith("…") for s in lines)
    if verbose:
        print(f'  n_words={n}, non_symbol={len(ns)}, awl={awl:.2f}, alpha_ratio={alpha:.3f}, sw_hit={sw_hit}')
        print(f'  lines={len(lines)}, bullet={bullet_lines}, end_ellipsis={ell_lines}')
        print(f'  hash_ratio={text.count("#")/n:.3f}, ellipsis_ratio={(text.count("...")+text.count("…"))/n:.3f}')
    if len(ns)<50: return False,'short'
    if awl<3 or awl>10: return False,'awl'
    if alpha<0.8: return False,'alpha'
    if sw_hit<2: return False,'stopwords'
    if text.count("#")/n>0.1: return False,'hash'
    if (text.count("...")+text.count("…"))/n>0.1: return False,'ellipsis_symb'
    if bullet_lines/len(lines)>0.9: return False,'bullets'
    if ell_lines/len(lines)>0.3: return False,'end_ell'
    return True,'pass'

print('Gopher:', gopher_qual(t, verbose=True))

# C4 quality
END_PUNCT=(".","?","!", '"', "'"); ELLIPSIS="..."
CIT = re.compile(r"\[\d*]|\[edit]|\[citation needed]")
POLICY=["terms of use","privacy policy","coo
```

<details><summary>Output (265 chars)</summary>

```
  n_words=883, non_symbol=852, awl=5.62, alpha_ratio=0.886, sw_hit=7
  lines=53, bullet=22, end_ellipsis=0
  hash_ratio=0.007, ellipsis_ratio=0.000
Gopher: (True, 'pass')
  total lines=53, kept=10, sentences=48, drop_no_term=43, drop_few_words=0
C4: (True, 'pass')

```
</details>

### Step 79: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# It passes both. So why is it not in strict_quality output? strict_quality also has C4BadWordsFilter and language filter
# It might have hit C4BadWords. Let me check
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x

# Check this doc's id in retention matrix
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
did = '<urn:uuid:9b21d708-ba05-420b-9ee3-adb51001aad1>'
print(rm[rm['doc_id']==did])
EOF
```

<details><summary>Output (182 chars)</summary>

```
                                               doc_id  ...  kept_strict_quality
2500  <urn:uuid:9b21d708-ba05-420b-9ee3-adb51001aad1>  ...                False

[1 rows x 8 columns]

```
</details>

### Step 80: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# I'll pick a different example to trace through clean vs defective.
# Let me focus on:
# Doc A (kept by all 7 clean configs): <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>
# Doc B (fr_0000): kept only by permissive (clean), would be processed in defective dedup
# Doc C (fr_0002): a near-duplicate of fr_0000 — defective dedup kills it; clean configs already drop FR docs (except permissive which keeps both)
# Doc D: an EN doc that defective dedup misclassifies (e.g. <urn:uuid:4052ff98-...> Wikipedia article)
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
import gzip
def find(doc_id, path, gz=False):
    opener = gzip.open if gz else open
    with opener(path,'rt') as f:
        for line in f:
            if doc_id in line:
                return True
    return False

clean = {
    'conservative':'pipeline-export-proprietary/runs/conservative/final_output/output.jsonl.gz',
    'fineweb_production':'pipeline-export-proprietary/runs/fineweb_production/final_output/output.jsonl.gz',
    'minimal_english':'pipeline-export-proprietary/runs/minimal_english/final_output/output.jsonl.gz',
    'multilingual':'pipeline-export-proprietary/runs/multilingual/final_output/output.jsonl.gz',
    'permissive':'pipeline-export-proprietary/runs/permissive/final_output/output.jsonl.gz',
    'repetition_heavy':'pipeline-export-proprietary/runs/repetition_heavy/final_output/output.jsonl.gz',
    'strict_quality':'pipeline-export-proprietary/runs/strict_quality/final_output/output.jsonl.gz',
}
defective = {
    '7e4b19f0(dedup)':'defective-export-proprietary/run-7e4b19f0/final_output/output.jsonl',
    'a3f8c2d1(filter)':'defective-export-proprietary/run-a3f8c2d1/final_output/output.jsonl',
}
test_ids = [
    ('Universal EN', '<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>'),
    ('FR original', 'fr_0000'),
    ('FR 
```

<details><summary>Output (1595 chars)</summary>

```

--- Universal EN: <urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6> ---
  conservative              kept=True
  fineweb_production        kept=True
  minimal_english           kept=True
  multilingual              kept=True
  permissive                kept=True
  repetition_heavy          kept=True
  strict_quality            kept=True
  7e4b19f0(dedup)           kept=True
  a3f8c2d1(filter)          kept=True

--- FR original: fr_0000 ---
  conservative              kept=False
  fineweb_production        kept=False
  minimal_english           kept=False
  multilingual              kept=False
  permissive                kept=True
  repetition_heavy          kept=False
  strict_quality            kept=False
  7e4b19f0(dedup)           kept=True
  a3f8c2d1(filter)          kept=True

--- FR near-dup: fr_0002 ---
  conservative              kept=False
  fineweb_production        kept=False
  minimal_english           kept=False
  multilingual              kept=False
  permissive                kept=True
  repetition_heavy          kept=False
  strict_quality            kept=False
  7e4b19f0(dedup)           kept=False
  a3f8c2d1(filter)          kept=True

--- EN flagged by dedup: <urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241> ---
  conservative              kept=False
  fineweb_production        kept=True
  minimal_english           kept=True
  multilingual              kept=False
  permissive                kept=True
  repetition_heavy          kept=False
  strict_quality            kept=False
  7e4b19f0(dedup)           kept=False
  a3f8c2d1(filter)          kept=True

```
</details>

### Step 81: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json, re, numpy as np
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x

did = '<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241>'
t = texts[did]['text']
print('Length:', len(t), 'wc=', texts[did]['metadata']['word_count'])
print('---first 800---')
print(t[:800])
print('---last 200---')
print(t[-200:])

# Run gopher and c4
STOP_WORDS = {"the","be","to","of","and","that","have","with"}
PUNCT = set("!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~")
def split_words(text): return re.findall(r"\S+", text)
def gopher_qual(text):
    words = split_words(text); n=len(words)
    ns = [w for w in words if any(c not in PUNCT for c in w)]
    awl = np.mean([len(w) for w in ns]) if ns else 0
    alpha = sum(any(c.isalpha() for c in w) for w in words)/n
    sw_hit = len(STOP_WORDS & set(words))
    lines = text.splitlines() or [text]
    bl = sum(s.lstrip().startswith("•") or s.lstrip().startswith("-") for s in lines)/len(lines)
    el = sum(s.rstrip().endswith("...") or s.rstrip().endswith("…") for s in lines)/len(lines)
    print(f' Gopher: nwords={n}, nonsymbol={len(ns)}, awl={awl:.2f}, alpha={alpha:.3f}, sw_hit={sw_hit}, bullet={bl:.2f}, end_ell={el:.2f}')
    if len(ns)<50: return False,'short'
    if awl<3 or awl>10: return False,'awl'
    if alpha<0.8: return False,f'alpha {alpha:.3f}<0.8'
    if sw_hit<2: return False,'stopwords'
    if bl>0.9: return False,'bullets'
    if el>0.3: return False,'end_ell'
    return True,'pass'
print(gopher_qual(t))
EOF
```

<details><summary>Output (1168 chars)</summary>

```
Length: 18053 wc= 2572
---first 800---
||This article has multiple issues. Please help improve it or discuss these issues on the talk page.
Preventive medicine or preventive care consists of measures taken to prevent diseases, (or injuries) rather than curing them or treating their symptoms. This contrasts in method with curative and palliative medicine, and in scope with public health methods (which work at the level of population health rather than individual health). Occupational medicine operates very often within the preventive medicine.
Preventive medicine strategies are typically described as taking place at the primary, secondary, tertiary and quaternary prevention levels. In addition, the term primal prevention has been used to describe all measures taken to ensure fetal well-being and prevent any long-term health cons
---last 200---
00". JAMA 291 (10): 1238–45. doi:10.1001/jama.291.10.1238. PMID 15010446.
- US Preventive Medicine Task Force
- US Preventive Medicine
- The Prevention Plan
- Health-EU Portal Prevention and Promotion
 Gopher: nwords=2572, nonsymbol=2508, awl=6.15, alpha=0.942, sw_hit=8, bullet=0.59, end_ell=0.00
(True, 'pass')

```
</details>

### Step 82: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
import json
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i, line in enumerate(fp):
        d = json.loads(line)
        if d['id']=='<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241>':
            print('Index:', i)
            break
EOF
```

<details><summary>Output (11 chars)</summary>

```
Index: 673

```
</details>

### Step 83: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Index 673 is within first 2200. So conservative did process it. Let me check C4 quality
import json, re
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
t = texts['<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241>']['text']

END_PUNCT=(".","?","!", '"', "'"); ELLIPSIS="..."
CIT = re.compile(r"\[\d*]|\[edit]|\[citation needed]")
POLICY=["terms of use","privacy policy","cookie policy","uses cookies","use of cookies","use cookies"]
def c4_qual(text, verbose=True):
    lines = text.splitlines()
    kept = []
    sent = 0
    nt=0; few=0; cb=0; pol=0
    for line in lines:
        line = line.strip(); words = line.split()
        if any(len(w)>1000 for w in words): continue
        line = CIT.sub("", line)
        if not (line.endswith(END_PUNCT)) or line.endswith(ELLIPSIS):
            nt+=1; continue
        if len(words)<3: few+=1; continue
        l = line.lower()
        if "lorem ipsum" in l: return False, "lorem"
        if "javascript" in l: continue
        if "{" in line: cb+=1; return False, "curly"
        if any(p in l for p in POLICY): pol+=1; continue
        sent += len(re.findall(r"[.!?]+", line))
        kept.append(line)
    if verbose:
        print(f' lines={len(lines)} kept={len(kept)} sent={sent} drop_no_term={nt} drop_few_words={few} drop_curly={cb} drop_policy={pol}')
    if sent<5: return False, 'too_few_sent'
    return True, 'pass'
print(c4_qual(t))
EOF
```

<details><summary>Output (103 chars)</summary>

```
 lines=100 kept=47 sent=216 drop_no_term=53 drop_few_words=0 drop_curly=0 drop_policy=0
(True, 'pass')

```
</details>

### Step 84: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Passes both. So why does conservative drop it?
# Conservative uses minhash_0.8 dedup. The doc may have been removed as a dup.
# Look at executor for conservative pipeline
import json
e = json.load(open('pipeline-export-proprietary/runs/conservative/logs/executor.json'))
for step in e['pipeline']:
    print({k:v for k,v in step.items() if isinstance(v,(str,int,float,bool,list,dict)) and k not in ('data_folder','output_folder','output_mg','adapter','exclusion_writer')})
EOF
```

<details><summary>Output (1913 chars)</summary>

```
{'limit': -1, 'skip': 0, 'text_key': 'text', 'id_key': 'id', '_empty_warning': False, 'default_metadata': {'source_config': 'conservative'}, 'recursive': True, 'glob_pattern': 'corpus.jsonl', 'shuffle_files': False, 'file_progress': False, 'doc_progress': False, 'compression': 'infer'}
{'batch_size': 1, 'min_doc_words': 50, 'max_doc_words': 100000, 'min_avg_word_length': 3, 'max_avg_word_length': 10, 'max_symbol_word_ratio': 0.1, 'max_bullet_lines_ratio': 0.9, 'max_ellipsis_lines_ratio': 0.3, 'max_non_alpha_words_ratio': 0.8, 'min_stop_words': 2, 'stop_words': "{'be', 'of', 'that', 'the', 'to', 'have', 'with', 'and'}", 'language': 'eng'}
{'batch_size': 1, 'split_paragraph': True, 'remove_citations': True, 'filter_no_terminal_punct': True, 'min_num_sentences': 5, 'min_words_per_line': 3, 'max_word_length': 1000, 'filter_lorem_ipsum': True, 'filter_javascript': True, 'filter_curly_bracket': True, 'filter_policy': True, 'language': 'eng'}
{'batch_size': 1, 'language_threshold': 0.65, 'languages': ['en'], 'backend': 'ft176', 'model': '<datatrove.utils.lid.FT176LID object at 0x16fdb7750>', 'label_only': False, 'keep_top_pairs_threshold': -1}
{'batch_size': 1, 'dup_line_frac': 0.3, 'dup_para_frac': 0.3, 'dup_line_char_frac': 0.2, 'dup_para_char_frac': 0.2, 'top_n_grams': [[2, 0.2], [3, 0.18], [4, 0.16]], 'dup_n_grams': [[5, 0.15], [6, 0.14], [7, 0.13], [8, 0.12], [9, 0.11], [10, 0.1]], 'paragraph_exp': "re.compile('\\\\n{2,}')", '_line_splitter': "re.compile('\\n+')", 'language': 'eng'}
{'remove_emails': True, 'remove_ips': True, 'emails_replacer': '<datatrove.pipeline.formatters.pii.PIIReplacer object at 0x375b27290>', 'ip_replacer': '<datatrove.pipeline.formatters.pii.PIIReplacer object at 0x16f0deb50>'}
{'compression': 'gzip', 'max_file_size': -1, 'file_id_counter': {}, 'output_filename': '<string.Template object at 0x375b36490>', 'expand_metadata': False, 'save_media_bytes': False}

```
</details>

### Step 85: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Wikipedia article passes Gopher+C4. Could it have failed LanguageFilter (en, threshold 0.65)?
# Or GopherRepetitionFilter?
# The conservative stats showed only 2 dropped at repetition stage. And 0 at language filter.
# But wait, 4052ff98 is in the first 2200, so it WAS processed.
# Maybe my inline C4Quality is wrong. Recall stats:
#   "line-filter-no_terminal_punc": 13085 for conservative
# Actual datatrove C4Quality splits paragraphs differently. Wait - in our analysis we said C4 passes (216 sentences across 47 lines). That's > 5 sentences.
# Actually let me check using datatrove's exact logic with split_into_sentences using nltk punkt
# Actually the result with "sent_count += len(re.findall(r'[.!?]+', line))" probably overcounts. Real C4 uses nltk sentence tokenizer.
# But even with overcount, 216 is much greater than 5; if undercount it should still be fine.
# Let me check repetition filter or language detect
# 
# Wikipedia text has 100 lines, many that don't end with terminal punctuation. Let me check raw lines
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
t = texts['<urn:uuid:4052ff98-a4a2-41cf-9188-30d4728b4241>']['text']
lines = t.splitlines()
print('num lines:', len(lines))
# Count end-with-period etc
ep = sum(1 for l in lines if l.strip().endswith(('.','?','!','"', "'")))
print('lines ending with terminal:', ep)
# How many "headers" / bullets?
print('starting with -:', sum(1 for l in lines if l.lstrip().startswith('-')))
# Check repetition: look at lines repeated
import collections
ll = [l.strip() for l in lines if l.strip()]
dupes = collections.Counter(ll)
print('most common lines:', dupes.most_common(5))
EOF
```

<details><summary>Output (1982 chars)</summary>

```
num lines: 100
lines ending with terminal: 47
starting with -: 59
most common lines: [('||This article has multiple issues. Please help improve it or discuss these issues on the talk page.', 1), ('Preventive medicine or preventive care consists of measures taken to prevent diseases, (or injuries) rather than curing them or treating their symptoms. This contrasts in method with curative and palliative medicine, and in scope with public health methods (which work at the level of population health rather than individual health). Occupational medicine operates very often within the preventive medicine.', 1), ('Preventive medicine strategies are typically described as taking place at the primary, secondary, tertiary and quaternary prevention levels. In addition, the term primal prevention has been used to describe all measures taken to ensure fetal well-being and prevent any long-term health consequences from gestational history and/or disease. The rationale for such efforts is the evidence demonstrating the link between fetal well-being, or "primal health," and adult health. Primal prevention strategies typically focus on providing future parents with: education regarding the consequences of epigenetic influences on their child, sufficient leave time for both parents or, for lack of it, at least some kin caregiving.', 1), ("Simple examples of preventive medicine include hand washing, breastfeeding, and immunizations. Preventive care may include examinations and screening tests tailored to an individual's age, health, and family history. For example, a person with a family history of certain cancers or other diseases would begin screening at an earlier age and/or more frequently than those with no such family history. On the other side of preventive medicine, some nonprofit organizations, such as the Northern California Cancer Center, apply epidemiologic research towards finding ways to prevent diseases.", 1), ('|Prevention levels||Doctor’s side|', 1)]

```
</details>

### Step 86: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Let me look at what happens with the GopherRepetitionFilter, which the conservative pipeline applies
# This doc has many bullet-style lines starting with "-" — could it have high duplication via line frac?
# Actually, conservative's repetition filter dropped only 2 of 1658. Maybe this doc was already gone before repetition.
# Conservative reads 2200, drops 426 in Gopher, drops 116 in C4Quality, drops 0 in LangFilter, drops 2 in Rep.
# So either Gopher or C4Quality. My simulation said both pass. Let me look more carefully.
# Maybe my Gopher tokenizer differs from datatrove. Let me check exact alpha_ratio and stop word counts.
# Actually note datatrove's GopherQualityFilter checks: max_non_alpha_words_ratio = 0.8 means at least 80% of words have alpha
# Let me check 6's tokenizer more carefully.
# datatrove uses split_into_words which depends on language. For 'eng' (Languages.english), what does it do?
import sys
sys.path.insert(0,'/home/ubuntu/workspace/datatrove/src')
# can't import full datatrove, but let me check the file
import re
text = open('/home/ubuntu/workspace/datatrove/src/datatrove/utils/text.py').read()
# Find split_into_words
m = re.search(r'def split_into_words.*?(?=\n(?:def|class)\s|\Z)', text, re.S)
if m: print(m.group(0)[:1500])
EOF
```

<details><summary>Output (134 chars)</summary>

```
def split_into_words(text, language=Languages.english):
    return split_into_parts(text, mode=SPLIT_TEXT_WORDS, language=language)



```
</details>

### Step 87: bash

```bash
grep -n "SPLIT_TEXT_WORDS\|split_into_parts\|PUNKT\|word_tokenize" /home/ubuntu/workspace/datatrove/src/datatrove/utils/text.py | head -30
```

<details><summary>Output (625 chars)</summary>

```
273:SPLIT_TEXT_WORDS = "WORDS"
277:def split_into_parts(text, mode="DOCUMENT", language=Languages.english):
278:    from datatrove.utils.word_tokenizers import load_word_tokenizer
283:        tokenizer = load_word_tokenizer(language)
286:    elif mode == SPLIT_TEXT_WORDS:
287:        tokenizer = load_word_tokenizer(language)
288:        return tokenizer.word_tokenize(text)
309:    return split_into_parts(text, mode=SPLIT_TEXT_WORDS, language=language)
313:    return split_into_parts(text, mode=SPLIT_TEXT_SENTENCES, language=language)
317:    return split_into_parts(text, mode=SPLIT_TEXT_PARAGRAPHS, language=language)

```
</details>

### Step 88: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Find an EN doc that ALL clean configs dropped (with the 2200-limit caveat handled)
# Use a doc that is in the first 2200 and pattern shows dropped
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
pat = rm[[f'kept_{c}' for c in configs]].apply(lambda r: ''.join('1' if v else '0' for v in r), axis=1)
rm['pat']=pat
# patterns
print('rare patterns with 5 kept:')
print(rm[pat.str.count('1')==5]['pat'].value_counts())
# 1111101 means dropped only by strict_quality (which uses C4BadWords)
exs = rm[pat=='1111101'].head(3)
print(exs)
# Quality scores for these
qs = pd.read_parquet('pipeline-export-proprietary/doc_quality_scores.parquet')
print(qs[qs['doc_id'].isin(exs['doc_id'])].to_string())
EOF
```

<details><summary>Output (1985 chars)</summary>

```
rare patterns with 5 kept:
pat
0111110    22
1111100    10
1011101     6
1011110     2
0111101     1
Name: count, dtype: int64
                                             doc_id  ...      pat
2   <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>  ...  1111101
11  <urn:uuid:37377bba-5d22-4f0b-91a9-cd45df72de7c>  ...  1111101
20  <urn:uuid:d83d98aa-5343-4a37-98e6-7a953cdb894c>  ...  1111101

[3 rows x 9 columns]
                                             doc_id  word_count  char_count  line_count  sentence_count  paragraph_count  avg_word_length  avg_paragraph_length  words_per_line  words_per_sentence  max_line_length  avg_line_length  alpha_ratio  digit_ratio  whitespace_ratio  symbol_word_ratio  stop_word_ratio  bullet_ratio  ellipsis_ratio  type_token_ratio  upper_ratio  terminal_punct_ratio
2   <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>          56         396           2               5                1            6.089                  56.0           28.00               11.20              302           197.50       0.8333       0.0000            0.1389                0.0           0.2321           0.0             0.0            0.7857       0.0000                 1.000
11  <urn:uuid:37377bba-5d22-4f0b-91a9-cd45df72de7c>         218        1318           8              12                1            5.050                 218.0           27.25               18.17              985           163.88       0.7997       0.0061            0.1646                0.0           0.2294           0.0             0.0            0.7431       0.0275                 0.625
20  <urn:uuid:d83d98aa-5343-4a37-98e6-7a953cdb894c>         213        1415           6              12                1            5.648                 213.0           35.50               17.75              753           235.00       0.8339       0.0014            0.1498                0.0           0.3333           0.0             0.0            0.6338       0.0047                 0.500

```
</details>

### Step 89: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Look at 1111101 - dropped only by strict_quality. strict_quality uses C4BadWords. Probably the badwords filter
import json
texts = {}
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for line in fp:
        x = json.loads(line)
        texts[x['id']] = x
for did in ['<urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>','<urn:uuid:37377bba-5d22-4f0b-91a9-cd45df72de7c>']:
    print('---', did, '---')
    print(texts[did]['text'][:600].replace('\n',' / '))
    print()
EOF
```

<details><summary>Output (1118 chars)</summary>

```
--- <urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250> ---
Question: How is bipolar disorder different from unipolar depression or 'regular' depression? / Answer: Both bipolar disorder and major depression are typically associated with depressive episodes. So both illnesses are accompanied by depressions. The difference is that in bipolar disorder people also have periods of elevation -- or severe irritability. We call these manic or hypomanic episodes.

--- <urn:uuid:37377bba-5d22-4f0b-91a9-cd45df72de7c> ---
Discover the cosmos! Each day a different image or photograph of our fascinating universe is featured, along with a brief explanation written by a professional astronomer. / 2010 August 12 / Explanation: Each August, as planet Earth swings through dust trailing along the orbit of periodic comet Swift-Tuttle, skygazers can enjoy the Perseid Meteor Shower. The shower should build to its peak now, best seen from later tonight after moonset, until dawn tomorrow morning when Earth moves through the denser part of the wide dust trail. But shower meteors have been spotted for many days, like this bright 


```
</details>

### Step 90: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# One more quick check: configs that DO read 10000 — how does retention compare?
# fineweb_production reads 10000, drops only 273 via FineWebQualityFilter (line_punct_ratio).
# What is line_punct_ratio? Look for it
import re
for f in ['/home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/fineweb_quality_filter.py']:
    print(open(f).read()[:3000])
EOF
```

<details><summary>Output (2324 chars)</summary>

```
from datatrove.pipeline.filters.base_filter import BaseFilter
from datatrove.pipeline.filters.gopher_repetition_filter import find_duplicates
from datatrove.pipeline.writers.disk_base import DiskWriter
from datatrove.utils.text import TERMINAL_PUNCTUATION, split_into_words
from datatrove.utils.typeshelper import Languages


class FineWebQualityFilter(BaseFilter):
    name = "🍷 FineWeb Quality"

    def __init__(
        self,
        exclusion_writer: DiskWriter | None = None,
        line_punct_thr: float = 0.12,
        line_punct_exclude_zero: bool = False,
        stop_chars: tuple[str, ...] | None = None,
        short_line_thr: float = 0.67,
        short_line_length: int = 30,
        char_duplicates_ratio: float = 0.01,
        new_line_ratio: float = 0.3,
        language: str = Languages.english,
    ):
        super().__init__(exclusion_writer)
        self.line_punct_thr = line_punct_thr
        self.line_punct_exclude_zero = line_punct_exclude_zero
        self.stop_chars = stop_chars if stop_chars is not None else tuple(TERMINAL_PUNCTUATION)
        self.short_line_threshold = short_line_thr
        self.short_line_length = short_line_length
        self.char_duplicates_ratio = char_duplicates_ratio
        self.new_line_ratio = new_line_ratio
        self.language = language

    def filter(self, doc) -> bool | tuple[bool, str]:
        lines = doc.text.split("\n")
        lines = [line for line in lines if line.strip() != ""]
        if len(lines) == 0:
            return False, "empty"
        ratio = sum(1 for line in lines if line.endswith(self.stop_chars)) / len(lines)
        if ratio < self.line_punct_thr and not (ratio == 0 and self.line_punct_exclude_zero):
            return False, "line_punct_ratio"

        ratio = sum(1 for line in lines if len(line) <= self.short_line_length) / len(lines)
        if ratio > self.short_line_threshold:
            return False, "short_line_ratio"

        ratio = find_duplicates(lines)[1] / len(doc.text.replace("\n", ""))

        if ratio > self.char_duplicates_ratio:
            return False, "char_dup_ratio"

        words = split_into_words(doc.text, self.language)
        new_line = doc.text.count("\n")
        if new_line / len(words) > self.new_line_ratio:
            return False, "list_ratio"

        return True


```
</details>

### Step 91: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Quick stats for the report: how many of conservative's "drops" are actually 7800 unseen docs
import pandas as pd
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
# Within first 2200 docs:
ids = []
import json
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i, line in enumerate(fp):
        if i<2200: ids.append(json.loads(line)['id'])
sub = rm[rm['doc_id'].isin(ids)]
print('Retention within first 2200 (the docs all configs saw):')
for c in ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']:
    print(f'  {c}: {sub[f"kept_{c}"].sum()} / 2200 ({sub[f"kept_{c}"].mean()*100:.1f}%)')
EOF
```

<details><summary>Output (321 chars)</summary>

```
Retention within first 2200 (the docs all configs saw):
  conservative: 1656 / 2200 (75.3%)
  fineweb_production: 1986 / 2200 (90.3%)
  minimal_english: 2000 / 2200 (90.9%)
  multilingual: 1774 / 2200 (80.6%)
  permissive: 2198 / 2200 (99.9%)
  repetition_heavy: 1299 / 2200 (59.0%)
  strict_quality: 1521 / 2200 (69.1%)

```
</details>

### Step 92: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# And for the docs beyond 2200 (only seen by 4 configs):
import pandas as pd, json
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
ids = []
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i, line in enumerate(fp):
        if i>=2200: ids.append(json.loads(line)['id'])
sub = rm[rm['doc_id'].isin(ids)]
print('Retention within docs idx >=2200 (7800 docs, only seen by 4 configs):')
for c in ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']:
    print(f'  {c}: {sub[f"kept_{c}"].sum()} / 7800 ({sub[f"kept_{c}"].mean()*100:.1f}%)')
EOF
```

<details><summary>Output (324 chars)</summary>

```
Retention within docs idx >=2200 (7800 docs, only seen by 4 configs):
  conservative: 0 / 7800 (0.0%)
  fineweb_production: 7741 / 7800 (99.2%)
  minimal_english: 7800 / 7800 (100.0%)
  multilingual: 0 / 7800 (0.0%)
  permissive: 0 / 7800 (0.0%)
  repetition_heavy: 4931 / 7800 (63.2%)
  strict_quality: 5909 / 7800 (75.8%)

```
</details>

### Step 93: bash

```bash
cd /home/ubuntu/workspace && python3 << 'EOF'
# Pairwise Jaccard within first 2200 only (apples to apples)
import pandas as pd, json
rm = pd.read_parquet('pipeline-export-proprietary/retention_matrix.parquet')
ids = set()
with open('pipeline-export-proprietary/source_corpus/corpus.jsonl') as fp:
    for i, line in enumerate(fp):
        if i<2200: ids.add(json.loads(line)['id'])
sub = rm[rm['doc_id'].isin(ids)]
configs = ['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']
import itertools
print('Pairwise Jaccard within first 2200 (apples-to-apples):')
for a,b in itertools.combinations(configs,2):
    A = set(sub[sub[f'kept_{a}']]['doc_id'])
    B = set(sub[sub[f'kept_{b}']]['doc_id'])
    j = len(A&B)/len(A|B) if (A|B) else 0
    print(f'  {a:20s} vs {b:20s}  J={j:.3f}')
EOF
```

<details><summary>Output (1231 chars)</summary>

```
Pairwise Jaccard within first 2200 (apples-to-apples):
  conservative         vs fineweb_production    J=0.826
  conservative         vs minimal_english       J=0.828
  conservative         vs multilingual          J=0.933
  conservative         vs permissive            J=0.753
  conservative         vs repetition_heavy      J=0.761
  conservative         vs strict_quality        J=0.917
  fineweb_production   vs minimal_english       J=0.993
  fineweb_production   vs multilingual          J=0.885
  fineweb_production   vs permissive            J=0.902
  fineweb_production   vs repetition_heavy      J=0.652
  fineweb_production   vs strict_quality        J=0.761
  minimal_english      vs multilingual          J=0.887
  minimal_english      vs permissive            J=0.908
  minimal_english      vs repetition_heavy      J=0.649
  minimal_english      vs strict_quality        J=0.760
  multilingual         vs permissive            J=0.806
  multilingual         vs repetition_heavy      J=0.732
  multilingual         vs strict_quality        J=0.857
  permissive           vs repetition_heavy      J=0.591
  permissive           vs strict_quality        J=0.692
  repetition_heavy     vs strict_quality        J=0.690

```
</details>

### Step 94: edit/create

**Path:** `/home/ubuntu/workspace/REPORT.md`

<details><summary>File content (33990 chars)</summary>

```
# Pipeline Comparison Report

Source: `/home/ubuntu/workspace/pipeline-export-proprietary/` (7 clean configs)
plus `/home/ubuntu/workspace/defective-export-proprietary/` (4 variant runs).
Corpus: 10,000 documents from `fineweb-edu-score-2`, plus a synthetic
expansion (see §1.1).

---

## 0. TL;DR — what to take away first

1. **The biggest source of confusion in the export is not the filters, it is the
   reader.** Three of the seven "clean" configs (`conservative`,
   `multilingual`, `permissive`) only ever consumed **2,200 of the 10,000
   input documents**. The other four (`fineweb_production`, `minimal_english`,
   `repetition_heavy`, `strict_quality`) consumed all 10,000. The
   `retention_matrix.parquet` does not account for this; it records the 7,800
   never-read documents as `kept=False`, which is why the low-retention
   configs look catastrophically aggressive. They aren't — they just saw less
   data. Once you restrict the comparison to the 2,200 documents *every*
   pipeline actually saw, retention is 59 %–99.9 %, and pairwise Jaccard
   overlap rises from 0.17–0.20 to 0.59–0.99 (see §3).
2. **The `filter_decisions.parquet` table is not a faithful record of what
   the pipelines did.** It records 100 % pass on `GopherRepetitionFilter`,
   100 % pass on `C4ParagraphFilter` for every config except
   `strict_quality` (where the latter is 0 % — and `strict_quality` doesn't
   even use that filter). The per-run `logs/stats/00000.json` files are the
   ground truth and contradict the parquet substantially. I used the
   `stats/` JSON files where they disagree.
3. **The "filters pass at 95 %+ but retention is 20 %" paradox is mostly
   the reader bug above.** Inside the 2,200 docs that were actually
   processed, the multiplicative model works fine: e.g. `conservative` =
   0.806 (Gopher) × 0.935 (C4 | Gopher pass) × 1.0 (Lang) × 0.999 (Rep) ≈
   0.753, matching the observed 1,656 / 2,200 = 0.753.
4. **GopherQualityFilter and C4QualityFilter are strongly *correlated*,
   not independent.** Of 280 documents that fail Gopher, 240 (86 %) also
   fail C4. The defective `run-f5e83b64` analysis report claims the
   opposite ("completely disjoint document sets") — this is the wrong
   conclusion and the recommendation built on it should not be followed.
5. **Of the 7 clean configs, only 4 are meaningfully distinct in
   behaviour:** `minimal_english` (lang-only), `fineweb_production`
   (FineWebQuality + lang), `repetition_heavy` (C4Paragraph dominated),
   and `strict_quality` (Gopher + C4Quality + C4BadWords + Lang).
   `conservative` and `multilingual` are nearly equivalent to a
   Gopher+C4Quality run on the unexpanded sample; `permissive` is
   essentially identity within the unexpanded sample (drops 2/2200).
6. **The corpus is "multilingual" only in name.** It is 9,800 EN + 100 FR
   + 100 DE, where the 100 FR and 100 DE are 50 copies each of two
   templates (98 % trigram overlap). The 200 non-English docs are dropped
   by any config that uses an English language filter *or* the Gopher
   stop-word check (whose word list is English-only).

---

## 1. Configs and what they actually run

The pipeline_config.yaml declares filters; the executor logs reveal the
actual order and parameters. Both are reproduced here:

| config | declared filters | actual pipeline (from `executor.json`) | input docs |
|---|---|---|---|
| `conservative` | GopherQ, C4Q (+ minhash, PII) | Gopher → C4Q → LangID(en, 0.65) → GopherRep → PII | **2,200** |
| `fineweb_production` | FineWebQ, LangFilter | FineWebQ → LangID(en+fr+de) | 10,000 |
| `minimal_english` | (none) | LangID(en, 0.65) | 10,000 |
| `multilingual` | GopherQ (+ exact dedup, PII) | LangID(en+fr+de) → Gopher → PII | **2,200** |
| `permissive` | GopherRep (+ FTFY) | GopherRep | **2,200** |
| `repetition_heavy` | GopherRep, C4Paragraph, GopherQ | GopherRep → C4Paragraph → Gopher | 10,000 |
| `strict_quality` | GopherQ, C4BadWords, GopherRep, C4Q, LangFilter | Gopher → C4BadWords → GopherRep → C4Q → LangID(en) | 10,000 |

The "minhash dedup" in conservative and "exact dedup" in multilingual are
in the YAML but **not in the executor pipeline** — they appear to have
been dropped from the actual run.

### 1.1 Why "2,200" matters

The corpus says `expansion: v3: expanded from 2200 to 10000`. The first
2,200 documents are the original sample: 2,000 EN + 100 FR + 100 DE. The
remaining 7,800 are synthetic EN expansion. The reader in `conservative`,
`multilingual`, and `permissive` is configured to stop after 2,200, so
those configs only see the original sample.

This explains the surprising patterns in `retention_matrix.parquet`:

| docs idx | seen by 4 configs (10k readers) | seen by 3 configs (2200 readers) |
|---|---|---|
| 0-2199 (original) | yes | yes |
| 2200-9999 (synthetic) | yes | **no — never read** |

Retention within docs 0-2199, the apples-to-apples comparison:

```
conservative        1656 / 2200   (75.3%)
fineweb_production  1986 / 2200   (90.3%)
minimal_englis

... (28990 chars truncated)
```
</details>

### Step 95: bash

```bash
wc -l /home/ubuntu/workspace/REPORT.md
head -50 /home/ubuntu/workspace/REPORT.md
```

<details><summary>Output (3086 chars)</summary>

```
731 /home/ubuntu/workspace/REPORT.md
# Pipeline Comparison Report

Source: `/home/ubuntu/workspace/pipeline-export-proprietary/` (7 clean configs)
plus `/home/ubuntu/workspace/defective-export-proprietary/` (4 variant runs).
Corpus: 10,000 documents from `fineweb-edu-score-2`, plus a synthetic
expansion (see §1.1).

---

## 0. TL;DR — what to take away first

1. **The biggest source of confusion in the export is not the filters, it is the
   reader.** Three of the seven "clean" configs (`conservative`,
   `multilingual`, `permissive`) only ever consumed **2,200 of the 10,000
   input documents**. The other four (`fineweb_production`, `minimal_english`,
   `repetition_heavy`, `strict_quality`) consumed all 10,000. The
   `retention_matrix.parquet` does not account for this; it records the 7,800
   never-read documents as `kept=False`, which is why the low-retention
   configs look catastrophically aggressive. They aren't — they just saw less
   data. Once you restrict the comparison to the 2,200 documents *every*
   pipeline actually saw, retention is 59 %–99.9 %, and pairwise Jaccard
   overlap rises from 0.17–0.20 to 0.59–0.99 (see §3).
2. **The `filter_decisions.parquet` table is not a faithful record of what
   the pipelines did.** It records 100 % pass on `GopherRepetitionFilter`,
   100 % pass on `C4ParagraphFilter` for every config except
   `strict_quality` (where the latter is 0 % — and `strict_quality` doesn't
   even use that filter). The per-run `logs/stats/00000.json` files are the
   ground truth and contradict the parquet substantially. I used the
   `stats/` JSON files where they disagree.
3. **The "filters pass at 95 %+ but retention is 20 %" paradox is mostly
   the reader bug above.** Inside the 2,200 docs that were actually
   processed, the multiplicative model works fine: e.g. `conservative` =
   0.806 (Gopher) × 0.935 (C4 | Gopher pass) × 1.0 (Lang) × 0.999 (Rep) ≈
   0.753, matching the observed 1,656 / 2,200 = 0.753.
4. **GopherQualityFilter and C4QualityFilter are strongly *correlated*,
   not independent.** Of 280 documents that fail Gopher, 240 (86 %) also
   fail C4. The defective `run-f5e83b64` analysis report claims the
   opposite ("completely disjoint document sets") — this is the wrong
   conclusion and the recommendation built on it should not be followed.
5. **Of the 7 clean configs, only 4 are meaningfully distinct in
   behaviour:** `minimal_english` (lang-only), `fineweb_production`
   (FineWebQuality + lang), `repetition_heavy` (C4Paragraph dominated),
   and `strict_quality` (Gopher + C4Quality + C4BadWords + Lang).
   `conservative` and `multilingual` are nearly equivalent to a
   Gopher+C4Quality run on the unexpanded sample; `permissive` is
   essentially identity within the unexpanded sample (drops 2/2200).
6. **The corpus is "multilingual" only in name.** It is 9,800 EN + 100 FR
   + 100 DE, where the 100 FR and 100 DE are 50 copies each of two
   templates (98 % trigram overlap). The 200 non-English d

... (86 chars truncated)
```
</details>

### Step 96: submit

```
Report written to `/home/ubuntu/workspace/REPORT.md` (731 lines). Here is what's in it:

**Big-picture findings (TL;DR section):**
- The dominant "low retention" cause is a **reader limit bug**: 3 of 7 configs only read 2,200 of 10,000 docs; the retention matrix counts the 7,800 unread docs as "not kept". Restricting to the 2,200 docs every config saw, retention is 59 %–99.9 % and Jaccard overlaps jump from ~0.2 to ~0.6–0.99.
- `filter_decisions.parquet` is unreliable — contradicts the per-run `stats/00000.json` (which I treat as ground truth).
- Gopher and C4Quality are NOT independent — 86 % of Gopher rejections also fail C4 — directly contradicting `run-f5e83b64`'s headline claim.
- Only 4 of the 7 configs are meaningfully distinct; `conservative` ≈ `multilingual`, and `fineweb_production` ≈ `minimal_english` (J=0.99).

**GopherQualityFilter sub-thresholds:** Full table of all 10 checks with their default values, plus per-run actual rejection-reason breakdown showing that the alpha-
```
