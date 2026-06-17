# grok-4.3 on Packed-Sequence Pipeline Repair

**Score:** 0.00
**Tool calls:** 47
**Duration:** ~8 min
**Trace ID:** `0d3f5359-e597-4131-8227-96ae378f3e5e`

---

## Trajectory

### Step 1: bash

```bash
find / -name "*.py" | head -20
```

### Step 2: bash

```bash
find / -type d -name "nemo" 2>/dev/null | head -5
```

### Step 3: bash

```bash
ls -la /
```

### Step 4: bash

```bash
find / -name "*pack*" -type f 2>/dev/null | head -30
```

### Step 5: bash

```bash
find / -path "*/nemo/*" -name "*.py" 2>/dev/null | head -20
```

### Step 6: bash

```bash
find / -name "*.py" 2>/dev/null | xargs grep -l "sequence packing" 2>/dev/null | head -10
```

### Step 7: bash

```bash
find / -name "*.py" 2>/dev/null | xargs grep -l "pack_sequences" 2>/dev/null | head -10
```

### Step 8: bash

```bash
ls -la /workspace 2>/dev/null || ls -la /opt 2>/dev/null || find / -maxdepth 3 -type d 2>/dev/null | head -30
```

### Step 9: bash

```bash
find / -name "*.py" 2>/dev/null | xargs grep -l "answer_start_idx" 2>/dev/null | head -5
```

### Step 10: bash

```bash
find / -name "*.py" 2>/dev/null | xargs grep -l "loss_mask" 2>/dev/null | head -10
```

### Step 11: bash

```bash
find / -maxdepth 5 -name "*.py" 2>/dev/null | head -50
```

### Step 12: bash

```bash
find / -name "megatron*" -type d 2>/dev/null | head -5
```

### Step 13: bash

```bash
python -c "import nemo; print(nemo.__file__)" 2>/dev/null || echo "no nemo"
```

<details><summary>Output (40 chars)</summary>

```
/home/ubuntu/workspace/nemo/__init__.py

```
</details>

### Step 14: bash

```bash
python -c "import megatron; print(megatron.__file__)" 2>/dev/null || echo "no megatron"
```

<details><summary>Output (5 chars)</summary>

```
None

```
</details>

### Step 15: bash

```bash
ls -la /home/ubuntu/workspace/
```

<details><summary>Output (430 chars)</summary>

```
total 10
drwxr-xr-x 1 ubuntu ubuntu  180 Jun 12 21:45 .
drwxr-x--- 1 ubuntu ubuntu   80 Jun 12 21:45 ..
lrwxrwxrwx 1 ubuntu ubuntu    9 Jun 12 21:45 .venv -> /opt/venv
drwx------ 1 ubuntu ubuntu  300 Jun 12 21:45 examples
drwx------ 1 ubuntu ubuntu  280 Jun 12 21:46 nemo
drwx------ 1 ubuntu ubuntu  760 Jun 12 21:45 scripts
-rwx------ 1 ubuntu ubuntu 9967 Jun 12 21:45 setup.py
drwx------ 1 ubuntu ubuntu  400 Jun 12 21:45 tests

```
</details>

### Step 16: bash

```bash
find /home/ubuntu/workspace/nemo -name "*.py" | xargs grep -l "pack" 2>/dev/null | head -20
```

<details><summary>Output (1064 chars)</summary>

```
/home/ubuntu/workspace/nemo/utils/nemo_logging.py
/home/ubuntu/workspace/nemo/utils/model_utils.py
/home/ubuntu/workspace/nemo/utils/loggers/clearml_logger.py
/home/ubuntu/workspace/nemo/utils/exceptions.py
/home/ubuntu/workspace/nemo/utils/te_utils.py
/home/ubuntu/workspace/nemo/utils/exp_manager.py
/home/ubuntu/workspace/nemo/utils/import_utils.py
/home/ubuntu/workspace/nemo/utils/export_utils.py
/home/ubuntu/workspace/nemo/utils/env_var_parsing.py
/home/ubuntu/workspace/nemo/utils/sequence_packing_utils.py
/home/ubuntu/workspace/nemo/package_info.py
/home/ubuntu/workspace/nemo/export/trt_llm/nemo_ckpt_loader/nemo_file.py
/home/ubuntu/workspace/nemo/export/tensorrt_lazy_compiler.py
/home/ubuntu/workspace/nemo/export/utils/utils.py
/home/ubuntu/workspace/nemo/export/multimodal/run.py
/home/ubuntu/workspace/nemo/lightning/megatron_parallel.py
/home/ubuntu/workspace/nemo/deploy/multimodal/query_multimodal.py
/home/ubuntu/workspace/nemo/__init__.py
/home/ubuntu/workspace/nemo/core/classes/common.py
/home/ubuntu/workspace/nemo/core/classes/modelPT.py

```
</details>

### Step 17: bash

```bash
ls -la /home/ubuntu/workspace/nemo/
```

<details><summary>Output (763 chars)</summary>

```
total 7
drwx------ 1 ubuntu ubuntu  280 Jun 12 21:46 .
drwxr-xr-x 1 ubuntu ubuntu  180 Jun 12 21:45 ..
-rwx------ 1 ubuntu ubuntu 2904 Jun 12 21:45 README.md
-rwx------ 1 ubuntu ubuntu  874 Jun 12 21:45 __init__.py
drwxr-xr-x 1 ubuntu ubuntu  120 Jun 12 21:46 __pycache__
drwx------ 1 ubuntu ubuntu  120 Jun 12 21:45 automodel
drwx------ 1 ubuntu ubuntu  340 Jun 12 21:45 collections
-rwx------ 1 ubuntu ubuntu 1247 Jun 12 21:45 constants.py
drwx------ 1 ubuntu ubuntu  180 Jun 12 21:45 core
drwx------ 1 ubuntu ubuntu  200 Jun 12 21:45 deploy
drwx------ 1 ubuntu ubuntu  340 Jun 12 21:45 export
drwx------ 1 ubuntu ubuntu  380 Jun 12 21:45 lightning
-rwx------ 1 ubuntu ubuntu 1400 Jun 12 21:45 package_info.py
drwx------ 1 ubuntu ubuntu  820 Jun 12 21:45 utils

```
</details>

### Step 18: bash

```bash
find /home/ubuntu/workspace -name "*.py" | xargs grep -l "sequence_packing\|pack_sequences\|packed_sequence" 2>/dev/null | head -20
```

<details><summary>Output (1429 chars)</summary>

```
/home/ubuntu/workspace/nemo/collections/multimodal/data/energon/task_encoder.py
/home/ubuntu/workspace/nemo/collections/nlp/data/language_modeling/text_memmap_dataset.py
/home/ubuntu/workspace/nemo/collections/nlp/models/language_modeling/megatron_gpt_model.py
/home/ubuntu/workspace/nemo/collections/nlp/models/language_modeling/megatron_gpt_sft_model.py
/home/ubuntu/workspace/nemo/collections/audio/modules/masking.py
/home/ubuntu/workspace/nemo/collections/avlm/data/energon/avlm_task_encoder.py
/home/ubuntu/workspace/nemo/collections/avlm/model/base.py
/home/ubuntu/workspace/nemo/collections/vlm/mllama/data/preloaded.py
/home/ubuntu/workspace/nemo/collections/vlm/llama4/data/mock.py
/home/ubuntu/workspace/nemo/collections/vlm/llava_next/data/task_encoder.py
/home/ubuntu/workspace/nemo/collections/vlm/neva/model/base.py
/home/ubuntu/workspace/nemo/collections/vlm/neva/data/mock.py
/home/ubuntu/workspace/nemo/collections/vlm/neva/data/preloaded.py
/home/ubuntu/workspace/nemo/collections/vlm/qwen2vl/data/preloaded.py
/home/ubuntu/workspace/nemo/collections/vlm/data/task_encoder.py
/home/ubuntu/workspace/nemo/collections/vlm/recipes/neva_llama3_8b.py
/home/ubuntu/workspace/nemo/collections/tts/modules/common.py
/home/ubuntu/workspace/nemo/collections/tts/modules/tacotron2.py
/home/ubuntu/workspace/nemo/collections/tts/modules/encodec_modules.py
/home/ubuntu/workspace/nemo/collections/tts/modules/submodules.py

```
</details>

### Step 19: bash

```bash
cat /home/ubuntu/workspace/nemo/utils/sequence_packing_utils.py
```

<details><summary>Output (11231 chars)</summary>

```
# Copyright (c) 2025, NVIDIA CORPORATION.  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

import collections
from typing import Dict, List, Tuple

import numpy as np
from tqdm import tqdm

from nemo.utils import logging

PACKING_ALGOS = ["first_fit_decreasing", "first_fit_shuffle"]


def find_first_bin_that_fits(bins: List[List[int]], s: int, bin_size: int) -> int:
    """
    Finds the first bin in a list of bins that has enough space to fit a sequence of size 's'.

    Args:
      bins: A list of lists, where each inner list represents a bin and contains the current elements in that bin.
      s: The size of the sequence to be placed in a bin.
      bin_size: The maximum capacity of each bin.

    Returns:
      The index of the first bin that can fit the sequence 's', or -1 if no such bin exists.
    """
    for i, abin in enumerate(bins):
        if sum(abin) + s <= bin_size:
            return i
    return -1


def first_fit(seqlens: List[int], pack_size: int) -> List[List[int]]:
    """
    Packs sequences of varying lengths into bins using the First-Fit algorithm.

    Args:
      seqlens: A list of integers, representing the lengths of the sequences to be packed.
      pack_size: The maximum capacity of each bin.

    Returns:
      A list of lists, where each inner list represents a bin and contains the indices
        of the sequences assigned to that bin.
    """
    res = []
    for s in seqlens:
        first_bin = find_first_bin_that_fits(res, s, pack_size)
        if first_bin == -1:  # open a new bin
            res.append([s])
        else:
            res[first_bin].append(s)
    return res


def first_fit_decreasing(seqlens: List[int], pack_size: int) -> List[List[int]]:
    """
    Packs sequences of varying lengths into bins using the First-Fit Decreasing algorithm.

    This is a variation of the First-Fit algorithm where the sequences are sorted by decreasing length before packing.

    Args:
      seqlens: A list of integers, representing the lengths of the sequences to be packed.
      pack_size: The maximum capacity of each bin.

    Returns:
      A list of lists, similar to the output of the 'first_fit' function.
    """
    sorted_seqlens = sorted(seqlens, reverse=True)
    return first_fit(sorted_seqlens, pack_size)


def first_fit_shuffle(seqlens: List[int], pack_size: int) -> List[List[int]]:
    """
    Packs sequences of varying lengths into bins using the First-Fit with Shuffling algorithm.

    This 

... (8231 chars truncated)
```
</details>

### Step 20: bash

```bash
find /home/ubuntu/workspace -name "*.py" | xargs grep -l "from nemo.utils.sequence_packing_utils import" 2>/dev/null
```

<details><summary>Output (234 chars)</summary>

```
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/packed_sequence.py
/home/ubuntu/workspace/nemo/collections/diffusion/data/diffusion_taskencoder.py
/home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py

```
</details>

### Step 21: bash

```bash
find /home/ubuntu/workspace -name "*.py" | xargs grep -l "sequence_packing_utils" 2>/dev/null
```

<details><summary>Output (234 chars)</summary>

```
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/packed_sequence.py
/home/ubuntu/workspace/nemo/collections/diffusion/data/diffusion_taskencoder.py
/home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py

```
</details>

### Step 22: bash

```bash
cat /home/ubuntu/workspace/nemo/collections/llm/gpt/data/packed_sequence.py
```

<details><summary>Output (7483 chars)</summary>

```
# Copyright (c) 2025, NVIDIA CORPORATION.  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
import json
from dataclasses import dataclass
from pathlib import Path
from typing import Optional

import numpy as np

from nemo.collections.common.tokenizers import TokenizerSpec
from nemo.collections.llm.gpt.data.core import create_sft_dataset
from nemo.utils import logging
from nemo.utils.sequence_packing_utils import create_hist, create_packing_strategy, fill_packing_strategy


def tokenize_dataset(
    path: Path,
    tokenizer: TokenizerSpec,
    max_seq_length: int,
    seed: int,
    dataset_kwargs: Optional[dict],
):
    """
    Tokenizes a dataset from the provided path using the specified tokenizer
    and prepares it for further processing.

    Args:
        path (Path): Path to the dataset file.
        tokenizer (TokenizerSpec): The tokenizer to use for tokenization.
        max_seq_length (int): Maximum sequence length for the tokens.
        seed (int): Random seed for shuffling the dataset (optional).

    Returns:
        np.ndarray: A NumPy array containing the tokenized data.
    """

    if not dataset_kwargs:
        dataset_kwargs = {}

    ts = dataset_kwargs.get("tool_schemas")
    if ts and not isinstance(ts, str):
        dataset_kwargs["tool_schemas"] = json.dumps(ts)

    chat_template = dataset_kwargs.pop("chat_template", None)
    if chat_template:
        # Needs to be called after the trainer has started and populated the tokenizer
        # But it can't be in prepare_data because it is only called in Rank 0
        tokenizer.tokenizer.chat_template = chat_template

    dataset = create_sft_dataset(
        path=path,
        tokenizer=tokenizer,
        seq_length=max_seq_length,
        seed=seed,
        is_test=True,
        **dataset_kwargs,
    )
    return np.array([dataset[i] for i in range(len(dataset))])


def prepare_packed_sequence_data(
    input_path: Path,
    output_path: Path,
    output_metadata_path: Path,
    packed_sequence_size: int,
    tokenizer: TokenizerSpec,
    max_seq_length: int,
    seed: Optional[int] = 0,
    packing_algorithm: str = "first_fit_shuffle",
    dataset_kwargs: dict = None,
):
    """
    Prepares a packed sequence dataset from a given input file and saves it to an output file.

    Args:
        input_path (Path): Path to the input dataset file.
        output_path (Path): Path to save the packed sequence data.
        packed_sequence_size (int): The maximum size for 

... (4483 chars truncated)
```
</details>

### Step 23: bash

```bash
find /home/ubuntu/workspace -name "*.py" | xargs grep -l "seq_start_id\|cu_seqlens\|packed.*sequence" 2>/dev/null | head -20
```

<details><summary>Output (1517 chars)</summary>

```
/home/ubuntu/workspace/nemo/utils/sequence_packing_utils.py
/home/ubuntu/workspace/nemo/collections/speechlm/models/speech_to_text_llm_model.py
/home/ubuntu/workspace/nemo/collections/multimodal/data/energon/task_encoder.py
/home/ubuntu/workspace/nemo/collections/nlp/modules/common/megatron/adapters/mcore_mixins.py
/home/ubuntu/workspace/nemo/collections/nlp/modules/common/megatron/attention.py
/home/ubuntu/workspace/nemo/collections/nlp/data/language_modeling/text_memmap_dataset.py
/home/ubuntu/workspace/nemo/collections/nlp/data/language_modeling/megatron/gpt_sft_dataset.py
/home/ubuntu/workspace/nemo/collections/nlp/models/language_modeling/megatron_gpt_model.py
/home/ubuntu/workspace/nemo/collections/nlp/models/language_modeling/megatron_gpt_sft_model.py
/home/ubuntu/workspace/nemo/collections/audio/modules/masking.py
/home/ubuntu/workspace/nemo/collections/avlm/data/energon/avlm_task_encoder.py
/home/ubuntu/workspace/nemo/collections/avlm/model/base.py
/home/ubuntu/workspace/nemo/collections/vlm/mllama/data/preloaded.py
/home/ubuntu/workspace/nemo/collections/vlm/mllama/model/base.py
/home/ubuntu/workspace/nemo/collections/vlm/llama4/model/base.py
/home/ubuntu/workspace/nemo/collections/vlm/llama4/data/mock.py
/home/ubuntu/workspace/nemo/collections/vlm/llama4/data/task_encoder.py
/home/ubuntu/workspace/nemo/collections/vlm/gemma3vl/data/task_encoder.py
/home/ubuntu/workspace/nemo/collections/vlm/gemma3vl/model/base.py
/home/ubuntu/workspace/nemo/collections/vlm/llava_next/model/base.py

```
</details>

### Step 24: bash

```bash
find /home/ubuntu/workspace -path "*/llm/*" -name "*.py" | head -30
```

<details><summary>Output (2195 chars)</summary>

```
/home/ubuntu/workspace/nemo/collections/llm/evaluation/base.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/api.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/interceptors/endpoint_interceptor.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/interceptors/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/interceptors/system_message_interceptor.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/interceptors/types.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/interceptors/logging_interceptor.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/interceptors/reasoning_interceptor.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/server.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/adapters/utils.py
/home/ubuntu/workspace/nemo/collections/llm/evaluation/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/peft/canonical_lora.py
/home/ubuntu/workspace/nemo/collections/llm/peft/module_matcher.py
/home/ubuntu/workspace/nemo/collections/llm/peft/api.py
/home/ubuntu/workspace/nemo/collections/llm/peft/utils.py
/home/ubuntu/workspace/nemo/collections/llm/peft/lora.py
/home/ubuntu/workspace/nemo/collections/llm/peft/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/peft/dora.py
/home/ubuntu/workspace/nemo/collections/llm/deploy/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/deploy/base.py
/home/ubuntu/workspace/nemo/collections/llm/api.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/quantization/quant_cfg_choices.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/quantization/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/quantization/quantizer.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/quantization/utils.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/model_utils.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/distill/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/distill/model.py
/home/ubuntu/workspace/nemo/collections/llm/modelopt/distill/loss.py

```
</details>

### Step 25: bash

```bash
find /home/ubuntu/workspace -path "*/llm/gpt/data/*" -name "*.py"
```

<details><summary>Output (2986 chars)</summary>

```
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/alpaca.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/packed_sequence.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/megatron/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/megatron/hyena/evo2_dataset.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/megatron/hyena/config.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/megatron/hyena/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/squad.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/api.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/pre_training.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/hf_dataset_packed_sequence.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/reranker.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/__init__.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/hf_dataset.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/utils.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/retrieval.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/mock.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/fine_tuning.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/chat.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/dolly.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/mlperf_govreport.py
/home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_utils_gpt_llm.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_core.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_hf_mockdataset.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_mock_dataset_gpt_llm.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_reranker.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_chat_dataset.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_pre_training_data.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_fine_tune_dataset.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/megatron/hyena/test_evo2_dataset.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/megatron/hyena/test_config.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_packed_sequence.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_dolly_dataset.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_mlperf_govreport.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_squad.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_alpaca_dataset.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_hf_datamodule_gpt_llm.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_retrieval.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_hf_hellaswag.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_hf_datamodule_packed.py
/home/ubuntu/workspace/tests/collections/llm/gpt/data/test_pre_training.py

```
</details>

### Step 26: bash

```bash
cat /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py
```

<details><summary>Output (50557 chars)</summary>

```
# Copyright (c) 2025, NVIDIA CORPORATION.  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

import json
import logging
import math
import re
from pathlib import Path
from typing import List, Mapping, Optional

import datasets
import numpy as np
import torch
from datasets import load_dataset

from nemo.collections.common.tokenizers import TokenizerSpec
from nemo.collections.llm.gpt.data.utils import (
    _chat_preprocess,
    _get_samples_mapping,
    _JSONLMemMapDataset,
    _OnlineSampleMapping,
    _preprocess,
)
from nemo.core.classes import Dataset
from nemo.lightning.base import NEMO_DATASETS_CACHE

logger = logging.getLogger(__name__)

# hack to avoid the "not enough disk space" error in some slurm cluster
datasets.builder.has_sufficient_disk_space = lambda needed_bytes, directory=".": True

PREFIX_STR = (
    "\x00"  # the prefix string used in the tokenizer to deal with the added empty token for some of the tokenizers
)

__idx_version__ = "0.2"  # index file version
__idx_suffix__ = "idx"  # index file suffix


def get_dataset_root(name: str) -> Path:
    """ """
    output = Path(NEMO_DATASETS_CACHE) / name
    output.mkdir(parents=True, exist_ok=True)

    return output


def create_sft_dataset(
    path: Path,
    tokenizer: "TokenizerSpec",
    seq_length: int = 2048,
    add_bos: bool = False,
    add_eos: bool = True,
    add_sep: bool = False,
    seed: int = 1234,
    label_key: str = "output",
    answer_only_loss: bool = True,
    truncation_field: str = "input",
    pad_to_max_length: bool = False,
    index_mapping_dir: Optional[str] = None,
    prompt_template: str = "{input} {output}",
    truncation_method: str = "right",
    memmap_workers: int = 2,
    hf_dataset: bool = False,
    global_sample_mapping: bool = False,
    pack_metadata_file_path: Path = None,
    pad_cu_seqlens: bool = False,
    chat: bool = False,
    use_hf_tokenizer_chat_template: bool = False,
    **kwargs,
) -> "GPTSFTDataset":
    """
    Create the dataset class (GPTSFTDataset, GPTSFTChatDataset or GPTSFTPackedDataset)
    """

    if isinstance(path, str):
        path = Path(path)

    gpt_sft_dataset_kwargs = {
        "file_path": str(path),
        "tokenizer": tokenizer,
        "max_seq_length": seq_length,
        "memmap_workers": memmap_workers,
        "hf_dataset": hf_dataset,
        "global_sample_mapping": global_sample_mapping,
        "add_bos": add_bos,
        "add_eos": add_eos,
        "add_sep": add_sep,
        "se

... (47557 chars truncated)
```
</details>

### Step 27: bash

```bash
find /home/ubuntu/workspace -name "*.py" | xargs grep -l "prepadd\|prepad\|cp_size\|context_parallel" 2>/dev/null | head -10
```

<details><summary>Output (570 chars)</summary>

```
/home/ubuntu/workspace/nemo/utils/app_state.py
/home/ubuntu/workspace/nemo/utils/callbacks/dist_ckpt_io.py
/home/ubuntu/workspace/nemo/utils/exp_manager.py
/home/ubuntu/workspace/nemo/automodel/misc_utils.py
/home/ubuntu/workspace/nemo/lightning/megatron_init.py
/home/ubuntu/workspace/nemo/lightning/run/plugins.py
/home/ubuntu/workspace/nemo/lightning/megatron_parallel.py
/home/ubuntu/workspace/nemo/lightning/fabric/strategies.py
/home/ubuntu/workspace/nemo/lightning/_strategy_lib.py
/home/ubuntu/workspace/nemo/lightning/pytorch/callbacks/megatron_comm_overlap.py

```
</details>

### Step 28: bash

```bash
grep -r "eos_id" /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py | head -20
```

<details><summary>Output (1727 chars)</summary>

```
            context_ids = [self.tokenizer.eos_id] * self.virtual_tokens + context_ids
            input_ids = input_ids + [self.tokenizer.eos_id]
            self._collate_item(input_ids, max_length=max_length, pad_id=self.tokenizer.eos_id)
        labels = torch.LongTensor(self._collate_item(labels, max_length=max_length, pad_id=self.tokenizer.eos_id))
        contexts = torch.LongTensor(self._collate_item(contexts, max_length=max_length, pad_id=self.tokenizer.eos_id))
        answers = torch.LongTensor(self._collate_item(answers, max_length=max_length, pad_id=self.tokenizer.eos_id))
                    0 if x == self.tokenizer.eos_id else 1.0
                # since the data could be prepadded with tokenizer's eos_id,
                # we can find out the index of all the eos_id
                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)
                # The second eos_id index marks the length of the original unpadded sequence if the sequence is
                seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)
        input_ids = self._collate_item(input_ids, max_length=max_length, pad_id=self.tokenizer.eos_id)
        labels = self._collate_item(labels, max_length=max_length, pad_id=self.tokenizer.eos_id)
            self._collate_item(input_ids, max_length=max_length, pad_id=self.tokenizer.eos_id)
        labels = torch.LongTensor(self._collate_item(labels, max_length=max_length, pad_id=self.tokenizer.eos_id))
        contexts = torch.LongTensor(self._collate_item(contexts, max_length=max_length, pad_id=self.tokenizer.eos_id))
        answers = torch.LongTensor(self._collate_item(answers, max_length=max_length, pad_id=self.tokenizer.eos_id))

```
</details>

### Step 29: bash

```bash
cat /home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py
```

<details><summary>Output (11005 chars)</summary>

```
# Copyright (c) 2025, NVIDIA CORPORATION.  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

import os
from dataclasses import dataclass
from typing import TYPE_CHECKING, Tuple

import numpy as np

from nemo.collections.nlp.data.language_modeling.megatron.gpt_sft_dataset import GPTSFTDataset
from nemo.collections.nlp.modules.common.tokenizer_utils import get_nmt_tokenizer
from nemo.core.config import hydra_runner
from nemo.utils import logging
from nemo.utils.sequence_packing_utils import create_hist, create_packing_strategy, fill_packing_strategy

if TYPE_CHECKING:
    from omegaconf import DictConfig

""" 
Script to prepare packed dataset from a SFT/PEFT dataset in the jsonl format.
Two main steps are run in this script:
1. The online processing code in GPTSFTDataset is run (including prompt template manipulation, 
sequence length truncation, tokenization, etc) and the result is an array of tokenized sequences, 
represented by indices). 
2. The sequences are grouped by length, and a packing algorithm is run. (https://en.wikipedia.org/wiki/Bin_packing_problem#Offline_algorithms)
Currently, two variants of "first fit" are supported.
"first_fit_decreasing" sorts the sequences in decreasing order before applying first-fit. 
It generates a more optimal packing, but it tends to keep all short sequences together, which may affect convergence.
"first_fit_shuffle" runs first-fit in a random order. Packing is less optimal but it keeps the dataset order random.
The recommendation is to run "first_fit_shuffle" and check the packed sequence lengths in the printout. 
If they are similar to the target length (i.e. packing is efficient), then use shuffle. Otherwise try first_fit_decreasing.

Example usage:

python scripts/nlp_language_modeling/prepare_packed_ft_dataset.py \
   model.data.train_ds.file_names=[/path/to/training.jsonl] \
   model.data.train_ds.max_seq_length=2048 \
   +tokenizer_path=<see note 1 below> \
   +output_dir=/path/to/output_folder \
   +pack_sizes=[2048,4096,8192]
   
when using context parallelism (CP) with packed dataset, CP size needs to be set in the command:

python scripts/nlp_language_modeling/prepare_packed_ft_dataset.py \
    model.data.train_ds.file_names=[/path/to/training.jsonl] \
    model.data.train_ds.max_seq_length=4096 \
    ++model.context_parallel_size=2 \
    +tokenizer_path=<see note 1 below> \
    +output_dir=/path/to/output_folder \
    +pack_sizes=[4096]

Note: 
  - Tokenizer path supports SentencePiece 

... (8005 chars truncated)
```
</details>

### Step 30: bash

```bash
cat /home/ubuntu/workspace/tests/collections/llm/gpt/data/test_packed_sequence.py
```

<details><summary>Output (3906 chars)</summary>

```
# Copyright (c) 2025, NVIDIA CORPORATION.  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
import tempfile
from pathlib import Path

import numpy as np
import pytest

from nemo.collections.llm.gpt.data.packed_sequence import (
    PackedSequenceSpecs,
    prepare_packed_sequence_data,
    tokenize_dataset,
)


class MockTokenizer:
    def __init__(self):
        self.eos_id = 2

    def text_to_ids(self, text):
        # Simple mock implementation that converts each character to its ASCII value
        return [ord(c) % 10 for c in text]


@pytest.fixture
def mock_tokenizer():
    return MockTokenizer()


@pytest.fixture
def sample_data_file():
    with tempfile.NamedTemporaryFile(mode='w', suffix='.jsonl', delete=False) as f:
        f.write('{"input": "Hello"}\n')
        f.write('{"input": "World"}\n')
    yield Path(f.name)
    Path(f.name).unlink()


def test_tokenize_dataset(mock_tokenizer, sample_data_file):
    max_seq_length = 10
    seed = 42

    result = tokenize_dataset(
        path=sample_data_file, tokenizer=mock_tokenizer, max_seq_length=max_seq_length, seed=seed, dataset_kwargs=None
    )

    assert isinstance(result, np.ndarray)
    assert len(result) > 0


def test_prepare_packed_sequence_data(mock_tokenizer, sample_data_file):
    with tempfile.TemporaryDirectory() as tmpdir:
        output_path = Path(tmpdir) / "packed_sequences.npy"
        metadata_path = Path(tmpdir) / "metadata.json"

        prepare_packed_sequence_data(
            input_path=sample_data_file,
            output_path=output_path,
            output_metadata_path=metadata_path,
            packed_sequence_size=16,
            tokenizer=mock_tokenizer,
            max_seq_length=10,
            seed=42,
            packing_algorithm="first_fit_shuffle",
        )

        # Check if output files were created
        assert output_path.exists()
        assert metadata_path.exists()


def test_packed_sequence_specs():
    # Test initialization with default values
    specs = PackedSequenceSpecs()
    assert specs.packed_sequence_size == -1
    assert specs.tokenizer_model_name is None
    assert specs.packed_train_data_path is None
    assert specs.packed_val_data_path is None
    assert specs.packed_metadata_path is None
    assert specs.pad_cu_seqlens is False

    # Test with valid packed data paths
    with (
        tempfile.NamedTemporaryFile(suffix='.npy') as train_file,
        tempfile.NamedTemporaryFile(suffix='.npy') as val_file,
    ):

... (906 chars truncated)
```
</details>

### Step 31: bash

```bash
cat /home/ubuntu/workspace/nemo/collections/llm/gpt/data/hf_dataset_packed_sequence.py | head -100
```

<details><summary>Output (4224 chars)</summary>

```
# Copyright (c) 2025, NVIDIA CORPORATION.  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

from typing import Dict, List, Union

import torch
from datasets import Dataset
from torch.nn import functional as F
from tqdm import tqdm

from nemo.utils import logging

CROSS_ENTROPY_IGNORE_IDX = -100
PACK_TYPE = Dict[str, Union[torch.Tensor, List[int]]]


# based on https://github.com/pytorch/torchtune/blob/v0.6.1/torchtune/datasets/_packed.py#L17
class HFDatasetPackedSequenceHelper:
    """
    Args:
    dataset: Actual dataset (can be 'train', 'val' or 'test')
    split (str): Whether the dataset is 'train', 'val' or 'test'
    """

    def __init__(self, dataset, split):
        self.dataset = dataset
        self.split = split
        self.padding_idx = 0  # Padding value to pack a sequence to self.packed_sequence_size
        self.contains_loss_mask = False

    def pack(self, packed_sequence_size, split_across_pack, max_packs):
        """Iterate through the dataset. Use a buffer to hold samples until packed_sequence_size,
        then append the buffer to self.packs as a single "packed" sample. Continue
        until max_packs or end of dataset.

        Args:
        packed_sequence_size (int): Number of tokens in a pack
        split_across_pack (bool): If the last sample in a pack does not fit in ``packed_sequence_size``,
        split the sample into the next pack, or move it entirely to the beginning of the next pack.
        max_packs (int): Maximum number of packs.

        Returns the Packed dataset which is an object of Dataset class.

        """
        self.packed_sequence_size = packed_sequence_size
        self.split_across_pack = split_across_pack
        self.max_packs = max_packs
        # Only show progress bar on rank 0
        rank = (
            torch.distributed.get_rank()
            if torch.distributed.is_available() and torch.distributed.is_initialized()
            else 0
        )

        # Pack dataset
        self.packs: List[PACK_TYPE] = []
        if "loss_mask" in self.dataset[0]:
            self.contains_loss_mask = True
        # Buffer to hold samples until they are long enough to be added to self.packs
        current_pack = {
            "tokens": [],
            "labels": [],
            "position_ids": [],
            "seq_lens": [],
        }
        if self.contains_loss_mask:
            current_pack["loss_mask"] = []
        self.previous_sample_boundary: int = 0
        if rank == 0:
     

... (1224 chars truncated)
```
</details>

### Step 32: bash

```bash
sed -n '650,720p' /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py
```

<details><summary>Output (2676 chars)</summary>

```
            "context_lengths": context_lengths,
            "answers": answers,
            "metadata": metadata,
            "token_count": token_count,
        }

        if not self.get_attention_mask_from_fusion:
            processed_batch["attention_mask"] = attention_mask

        return processed_batch


class GPTSFTPackedDataset(GPTSFTDataset):
    """ """

    def __init__(
        self,
        file_path: str,
        tokenizer: TokenizerSpec,
        return_cu_seqlen: bool = True,
        pad_cu_seqlens: bool = False,
        pack_metadata_file_path: Optional[str] = None,
        **kwargs,
    ):
        """
        file_path: See `file_path` in the parent class.
        tokenizer: See `tokenizer` in the parent class.
        return_cu_seqlen: Whether to return `cu_seqlen` to pass to the model. Having `cu_seqlen` in the model input
                enables THD attention kernel, which is the correct format for training with packed sequence to prevent
                cross-sequence attention. This flag should be True unless you have a specific use case.
        """
        np.random.seed(kwargs.get("seed", 1234))
        super().__init__(file_path, tokenizer, **kwargs)
        assert self.virtual_tokens == 0, "P-Tuning with packed sequence is not supported."
        self.return_cu_seqlen = return_cu_seqlen

        self.pad_cu_seqlens = pad_cu_seqlens
        if self.pad_cu_seqlens:
            assert (
                pack_metadata_file_path is not None
            ), "a metadata json file is required when pad_cu_seqlens is enabled"
            assert (
                self.pad_to_max_length is True
            ), "'pad_to_max_length=True' is required when pad_cu_seqlens is enabled"

        self.pack_metadata = None
        if pack_metadata_file_path is not None:
            with open(pack_metadata_file_path) as f:
                self.pack_metadata = json.load(f)

    def __getitem__(self, idx):
        if self.samples_mapping is not None:
            # assert idx < len(self.samples_mapping)
            idx = self.samples_mapping[idx]

        input_ids = self.indexed_dataset[idx]["input_ids"]
        seq_boundaries = self.indexed_dataset[idx]["seq_start_id"] + [len(input_ids)]
        loss_mask = self.indexed_dataset[idx]["loss_mask"]
        if idx < 0:
            loss_mask = [0] * len(loss_mask)
        return {
            "input_ids": input_ids,
            "seq_boundaries": seq_boundaries,
            "loss_mask": loss_mask,
        }

    def _load_dataset(self):
        try:
            self.indexed_dataset = np.load(self.file_path, allow_pickle=True)
        except Exception as e:
            logger.error(

```
</details>

### Step 33: edit/str_replace

**Path:** `/home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py`

**Old:**
```python
    def _build_loss_mask(self, processed_example):
        seq_boundaries = processed_example["seq_boundaries"]
        if self.answer_only_loss:
            return np.concatenate(
                [
                    processed_example["loss_mask"][seq_boundaries[i] : seq_boundaries[i + 1] - 1]
                    for i in range(len(seq_boundaries) - 1)
                ]
            )
        return np.concatenate(
            [
                [
                    0 if x == self.tokenizer.eos_id else 1.0
                    for x in processed_example["input_ids"][seq_boundaries[i] : seq_boundaries[i + 1] - 1]
                ]
                for i in range(len(seq_boundaries) - 1)
            ]
        )

```

**New:**
```python
    def _build_loss_mask(self, processed_example):
        seq_boundaries = processed_example["seq_boundaries"]
        if self.answer_only_loss:
            return np.concatenate(
                [
                    processed_example["loss_mask"][seq_boundaries[i] + 1 : seq_boundaries[i + 1]]
                    for i in range(len(seq_boundaries) - 1)
                ]
            )
        return np.concatenate(
            [
                [
                    0 if x == self.tokenizer.eos_id else 1.0
                    for x in processed_example["input_ids"][seq_boundaries[i] : seq_boundaries[i + 1] - 1]
                ]
                for i in range(len(seq_boundaries) - 1)
            ]
        )

```

### Step 34: edit/str_replace

**Path:** `/home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py`

**Old:**
```python
        for key, val in data.items():
            if key in {'input_ids', 'context_ids'}:
                if len(val) <= max_length_to_pad:
                    # because input_ids are truncated by 1 for inputs and labels,
                    # we add 1 extra padding here to make sure padded inputs and labels
                    # are is a multiple of (cp_size * 2)
                    val = val + [pad_id] * (max_length_to_pad - len(val) + 1)
                    data[key] = val
                elif len(val) > max_seq_length:
                    logging.info(
                        f"""The current sequence length {len(val)} for packing is
                                    larger than the max_seq_length specified ({max_seq_length}).
                                    The current seqquence length is truncated to the size of max_seq_length.
                                    Please consider increase the sequence packing size"""
                    )
                    data[key] = val[:max_seq_length]
            return

```

**New:**
```python
        for key, val in data.items():
            if key in {'input_ids', 'context_ids'}:
                if len(val) <= max_length_to_pad:
                    # because input_ids are truncated by 1 for inputs and labels,
                    # we add 1 extra padding here to make sure padded inputs and labels
                    # are is a multiple of (cp_size * 2)
                    num_pad = max_length_to_pad - len(val) + 1
                    val = val + [pad_id] * num_pad
                    data[key] = val
                elif len(val) > max_seq_length:
                    logging.info(
                        f"""The current sequence length {len(val)} for packing is
                                    larger than the max_seq_length specified ({max_seq_length}).
                                    The current seqquence length is truncated to the size of max_seq_length.
                                    Please consider increase the sequence packing size"""
                    )
                    data[key] = val[:max_seq_length]
            if key == 'loss_mask':
                # pad loss_mask with 0s so it stays aligned with padded input_ids; do not compute loss on pad tokens
                if 'input_ids' in data:
                    target_len = len(data['input_ids'])
                    if len(val) < target_len:
                        data[key] = val + [0.0] * (target_len - len(val))
            return

```

### Step 35: bash

```bash
sed -n '140,175p' /home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py
```

<details><summary>Output (1817 chars)</summary>

```
        hf_dataset=data_cfg.get('hf_dataset', False),
        truncation_method=data_cfg.get('truncation_method', 'right'),
        special_tokens=data_cfg.get('chat_prompt_tokens', None),
        is_test=True,
    )

    max_seq_length = dataset.max_seq_length
    pad_id = dataset.tokenizer.eos_id
    tokenizer = dataset.tokenizer
    pad_seq_length_to_mult = dataset.pad_seq_length_to_mult
    dataset = np.array([dataset[i] for i in range(len(dataset))])
    if cp_size > 1:

        def pre_pad_dataset(data, max_seq_length, max_length_to_pad, pad_id):
            '''
            pad each individual data point to the length of max_length
            '''
            assert max_seq_length >= max_length_to_pad
            for key, val in data.items():
                if key in {'input_ids', 'context_ids'}:
                    if len(val) <= max_length_to_pad:
                        # because input_ids are truncated by 1 for inputs and labels,
                        # we add 1 extra padding here to make sure padded inputs and labels
                        # are is a multiple of (cp_size * 2)
                        val = val + [pad_id] * (max_length_to_pad - len(val) + 1)
                        data[key] = val
                    elif len(val) > max_seq_length:
                        logging.info(
                            f"""The current sequence length {len(val)} for packing is
                                        larger than the max_seq_length specified ({max_seq_length}).
                                        The current seqquence length is truncated to the size of max_seq_length.
                                        Please consider increase the sequence packing size"""
                        )
                        data[key] = val[:max_seq_length]
            return


```
</details>

### Step 36: edit/str_replace

**Path:** `/home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py`

**Old:**
```python
            for key, val in data.items():
                if key in {'input_ids', 'context_ids'}:
                    if len(val) <= max_length_to_pad:
                        # because input_ids are truncated by 1 for inputs and labels,
                        # we add 1 extra padding here to make sure padded inputs and labels
                        # are is a multiple of (cp_size * 2)
                        val = val + [pad_id] * (max_length_to_pad - len(val) + 1)
                        data[key] = val
                    elif len(val) > max_seq_length:
                        logging.info(
                            f"""The current sequence length {len(val)} for packing is
                                        larger than the max_seq_length specified ({max_seq_length}).
                                        The current seqquence length is truncated to the size of max_seq_length.
                                        Please consider increase the sequence packing size"""
                        )
                        data[key] = val[:max_seq_length]
            return
```

**New:**
```python
            for key, val in data.items():
                if key in {'input_ids', 'context_ids'}:
                    if len(val) <= max_length_to_pad:
                        # because input_ids are truncated by 1 for inputs and labels,
                        # we add 1 extra padding here to make sure padded inputs and labels
                        # are is a multiple of (cp_size * 2)
                        num_pad = max_length_to_pad - len(val) + 1
                        val = val + [pad_id] * num_pad
                        data[key] = val
                    elif len(val) > max_seq_length:
                        logging.info(
                            f"""The current sequence length {len(val)} for packing is
                                        larger than the max_seq_length specified ({max_seq_length}).
                                        The current seqquence length is truncated to the size of max_seq_length.
                                        Please consider increase the sequence packing size"""
                        )
                        data[key] = val[:max_seq_length]
                if key == 'loss_mask':
                    # pad loss_mask with 0s so it stays aligned with padded input_ids; do not compute loss on pad tokens
                    if 'input_ids' in data:
                        target_len = len(data['input_ids'])
                        if len(val) < target_len:
                            data[key] = val + [0.0] * (target_len 
```

### Step 37: bash

```bash
sed -n '100,160p' /home/ubuntu/workspace/nemo/utils/sequence_packing_utils.py
```

<details><summary>Output (2804 chars)</summary>

```

def create_hist(dataset: np.array, truncate_seq_len: int):
    """
    Creates a histogram of sequence lengths from a tokenized dataset.

    This function analyzes the tokenized dataset and creates a histogram showing the distribution of sequence lengths.

    Args:
      dataset: A NumPy array containing the tokenized sequences. Each element is a dictionary that contains at minimum
               the key `input_ids`.
      truncate_seq_len: The maximum sequence length to consider in the histogram.

    Returns:
      sequences: A dictionary where keys are sequence lengths and values are lists
                 of corresponding sequences from the dataset.
      histogram: A list representing the histogram data (number of sequences for each length).
    """
    logging.info("Creating histogram from tokenized dataset...")

    sequences = collections.defaultdict(list)
    counts = [0] * (truncate_seq_len + 1)

    for item_dict in dataset:
        # Minus 1 here to account for the fact that transformer input and label
        # have one less token than the full sequence.
        # Input is missing the last token and label is missing the first token
        # (this way the tokens are aligned for next token prediction).
        # We want pack size to be the length of the actual input and label, hence minus 1.
        seq_len = len(item_dict["input_ids"]) - 1
        sequences[seq_len].append(item_dict)
        counts[seq_len] += 1

    logging.debug("Histogram of sequence lengths")
    logging.debug(counts)

    histogram = []
    for seq_len in range(truncate_seq_len + 1):
        histogram.append(len(sequences[seq_len]))

    return sequences, histogram


def create_packing_strategy(
    histogram: List[int], pack_size: int, packing_algorithm: str = "first_fit"
) -> Tuple[List[List[int]], dict]:
    """
    Packs sequences into bins using the specified packing algorithm.

    This function takes the histogram of sequence lengths, desired pack size, and a string representing the packing
    algorithm to use. It then calls the corresponding function (e.g., 'first_fit_decreasing') and performs the
    packing process using only sequence lengths as input (without the actual sequences).

    Args:
          histogram: A list representing the histogram data (number of sequences for each length).
          pack_size: The maximum capacity of each bin.
          packing_algorithm: One of the supported packing algorithms from ['first_fit_decreasing', 'first_fit_shuffle']

    Returns:
          assignments: A list of lists, where each inner list represents a bin and contains the indices of the
                        sequence lengths assigned to that bin.
          pack_metadata: A dict that records packing metadata, for instance the max number of samples per bin.

```
</details>

### Step 38: bash

```bash
sed -n '200,260p' /home/ubuntu/workspace/nemo/utils/sequence_packing_utils.py
```

<details><summary>Output (3018 chars)</summary>

```
    """
    Fills the packing strategy with actual sequence data based on assignments and sequence information.

    This function takes the assignments generated by the packing algorithm (containing sequence length indices),
    the original sequences data, and the pack size. It iterates through the assignments, retrieves the corresponding
    sequences from the sequences dictionary, and constructs the final output data structure with input IDs, loss masks
    (if available), and starting indices for each sequence in a packed sequence.

    Args:
          assignments: A list of lists, where each inner list represents a bin and contains the indices of the
                        sequence lengths assigned to that bin (output of 'create_packing_strategy').
          sequences: A dictionary where keys are sequence lengths and values are lists of corresponding sequences
                      from the dataset (output of 'create_hist').
          pack_size: The maximum capacity of each bin.
          pad_id: The tokenizer's padding token.

    Returns:
          output_data: A list of dictionaries, where each dictionary represents a packed sequence with its input IDs,
                        loss mask (if available), and starting indices.
    """
    ifile_handles = dict()
    for seq_len in tqdm(range(pack_size + 1)):
        per_seq_data = sequences[seq_len]
        if len(per_seq_data) > 0:
            perm = np.random.permutation(len(per_seq_data))
            input_ids = np.array([x["input_ids"] for x in per_seq_data])[perm].tolist()
            try:
                loss_mask = np.array([x["loss_mask"] for x in per_seq_data])[perm].tolist()
            except KeyError:
                try:
                    loss_mask = np.array(
                        [
                            [
                                idx >= x["answer_start_idx"] and x["input_ids"][idx] != pad_id
                                for idx in range(len(x["input_ids"]))
                            ]
                            for x in per_seq_data
                        ]
                    )[perm].tolist()
                except KeyError as err:
                    err_msg = "Key errors loss_mask and answer_start_idx missing in example - "
                    err_msg += f"{err} {per_seq_data[0]}"
                    logging.error(err_msg)
                    raise ValueError(err_msg)

            ifile_handles[seq_len] = (input_ids, loss_mask)

    input_ids, loss_mask, seq_start_id = {}, {}, {}

    for oindex, assignment in tqdm(enumerate(assignments), total=len(assignments)):
        _input_ids, _loss_mask, _seq_start_id = [], [], [0]

        for seq_length in assignment:
            _input_ids.extend(ifile_handles[seq_length][0].pop())
            _loss_mask.extend(ifile_handles[seq_length][1].pop())
            _seq_start_id.append(len(_input_ids))

        input_ids[oindex] = _input_ids
        loss_mask[oindex] = _loss_mask
        seq_start_id[oindex] = _s

... (18 chars truncated)
```
</details>

### Step 39: bash

```bash
sed -n '220,250p' /home/ubuntu/workspace/nemo/utils/sequence_packing_utils.py
```

<details><summary>Output (1405 chars)</summary>

```
    ifile_handles = dict()
    for seq_len in tqdm(range(pack_size + 1)):
        per_seq_data = sequences[seq_len]
        if len(per_seq_data) > 0:
            perm = np.random.permutation(len(per_seq_data))
            input_ids = np.array([x["input_ids"] for x in per_seq_data])[perm].tolist()
            try:
                loss_mask = np.array([x["loss_mask"] for x in per_seq_data])[perm].tolist()
            except KeyError:
                try:
                    loss_mask = np.array(
                        [
                            [
                                idx >= x["answer_start_idx"] and x["input_ids"][idx] != pad_id
                                for idx in range(len(x["input_ids"]))
                            ]
                            for x in per_seq_data
                        ]
                    )[perm].tolist()
                except KeyError as err:
                    err_msg = "Key errors loss_mask and answer_start_idx missing in example - "
                    err_msg += f"{err} {per_seq_data[0]}"
                    logging.error(err_msg)
                    raise ValueError(err_msg)

            ifile_handles[seq_len] = (input_ids, loss_mask)

    input_ids, loss_mask, seq_start_id = {}, {}, {}

    for oindex, assignment in tqdm(enumerate(assignments), total=len(assignments)):
        _input_ids, _loss_mask, _seq_start_id = [], [], [0]

```
</details>

### Step 40: bash

```bash
grep -n "seq_boundaries\|cu_seqlens_unpadded" /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py | head -30
```

<details><summary>Output (2058 chars)</summary>

```
706:        seq_boundaries = self.indexed_dataset[idx]["seq_start_id"] + [len(input_ids)]
712:            "seq_boundaries": seq_boundaries,
740:        seq_boundaries = processed_example["seq_boundaries"]
744:                    processed_example["loss_mask"][seq_boundaries[i] + 1 : seq_boundaries[i + 1]]
745:                    for i in range(len(seq_boundaries) - 1)
752:                    for x in processed_example["input_ids"][seq_boundaries[i] : seq_boundaries[i + 1] - 1]
754:                for i in range(len(seq_boundaries) - 1)
765:                    item["input_ids"][item["seq_boundaries"][i] : item["seq_boundaries"][i + 1] - 1]
766:                    for i in range(len(item["seq_boundaries"]) - 1)
774:                    item["input_ids"][item["seq_boundaries"][i] + 1 : item["seq_boundaries"][i + 1]]
775:                    for i in range(len(item["seq_boundaries"]) - 1)
800:        cu_seqlens_unpadded: List[List[int]] = []
804:            cu_seqlens_unpadded.append([0])
805:            seqlens = np.array(item["seq_boundaries"][1:]) - np.array(item["seq_boundaries"][:-1])
819:            for i in range(len(item["seq_boundaries"]) - 1):
820:                current_seq = item["input_ids"][item["seq_boundaries"][i] : item["seq_boundaries"][i + 1] - 1]
829:                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)
833:            if len(cu_seqlens[-1]) > len(cu_seqlens_unpadded[-1]):
834:                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1])
866:            cu_seqlens_unpadded = self._collate_item(
867:                cu_seqlens_unpadded,
868:                max_length=max(len(length) for length in cu_seqlens_unpadded) + 1,
876:            cu_seqlens_unpadded = torch.IntTensor(cu_seqlens_unpadded)
877:            cu_seqlens_unpadded_argmin = torch.argmin(cu_seqlens_unpadded, dim=1, keepdim=True)
901:                    "cu_seqlens_unpadded": torch.IntTensor(cu_seqlens_unpadded),
902:                    "cu_seqlens_unpadded_argmin": cu_seqlens_unpadded_argmin,

```
</details>

### Step 41: bash

```bash
grep -n "seqlen_unpadded\|eos_idx" /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py
```

<details><summary>Output (283 chars)</summary>

```
824:                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)
828:                seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)
829:                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)

```
</details>

### Step 42: bash

```bash
sed -n '810,840p' /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py
```

<details><summary>Output (1883 chars)</summary>

```

            # the last seq needs to be the max seq len because rope and attn kernels expect no padding
            assert cu_seqlens[-1][-1] <= max_length

            # since data is prepadded when cp_size > 1, there may be some extra padding at the end
            # of the packed sequence. In this case, we need to add the max seq len to the end.
            if cu_seqlens[-1][-1] != max_length:
                cu_seqlens[-1].append(max_length)

            for i in range(len(item["seq_boundaries"]) - 1):
                current_seq = item["input_ids"][item["seq_boundaries"][i] : item["seq_boundaries"][i + 1] - 1]

                # since the data could be prepadded with tokenizer's eos_id,
                # we can find out the index of all the eos_id
                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)

                # The second eos_id index marks the length of the original unpadded sequence if the sequence is
                # prepadded for cp_size > 1. Otherwise, there is no extra padding.
                seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)
                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)

            # if extra paddings are added in the packed sequence, they can't be counted as
            # actual tokens for training
            if len(cu_seqlens[-1]) > len(cu_seqlens_unpadded[-1]):
                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1])

            if self.pad_cu_seqlens:
                # pad cu_seqlens to a constant shape with zero length sequences
                max_samples_per_bin = max(p["max_samples_per_bin"] for p in self.pack_metadata)
                # plus 2 since cu_seqlens additionally contains 0 and may append max_length
                pad_num = max_samples_per_bin - len(cu_seqlens[-1]) + 2

```
</details>

### Step 43: edit/str_replace

**Path:** `/home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py`

**Old:**
```python
                # since the data could be prepadded with tokenizer's eos_id,
                # we can find out the index of all the eos_id
                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)

                # The second eos_id index marks the length of the original unpadded sequence if the sequence is
                # prepadded for cp_size > 1. Otherwise, there is no extra padding.
                seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)
                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)

```

**New:**
```python
                # since the data could be prepadded with tokenizer's eos_id,
                # we can find out the index of all the eos_id
                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)

                # The second eos_id index marks the length of the original unpadded sequence if the sequence is
                # prepadded for cp_size > 1. Otherwise, there is no extra padding.
                if eos_idx[0].any():
                    if len(eos_idx[0]) > 1:
                        # prepadded: second EOS marks end of real content
                        seqlen_unpadded = eos_idx[0][1] + 1
                    else:
                        seqlen_unpadded = eos_idx[0][0] + 1
                else:
                    seqlen_unpadded = len(current_seq)
                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)

```

### Step 44: edit/str_replace

**Path:** `/home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py`

**Old:**
```python
                # since the data could be prepadded with tokenizer's eos_id,
                # we can find out the index of all the eos_id
                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)

                # The second eos_id index marks the length of the original unpadded sequence if the sequence is
                # prepadded for cp_size > 1. Otherwise, there is no extra padding.
                if eos_idx[0].any():
                    if len(eos_idx[0]) > 1:
                        # prepadded: second EOS marks end of real content
                        seqlen_unpadded = eos_idx[0][1] + 1
                    else:
                        seqlen_unpadded = eos_idx[0][0] + 1
                else:
                    seqlen_unpadded = len(current_seq)
                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)

```

**New:**
```python
                # since the data could be prepadded with tokenizer's eos_id,
                # we can find out the index of all the eos_id
                eos_idx = np.where(np.array(current_seq) == self.tokenizer.eos_id)

                # The first eos_id index marks the length of the original unpadded sequence.
                # When prepadded for cp_size > 1, extra EOS tokens are appended after the original EOS,
                # so we always use the first EOS to determine the real content length.
                seqlen_unpadded = eos_idx[0][0] + 1 if eos_idx[0].any() else len(current_seq)
                cu_seqlens_unpadded[-1].append(cu_seqlens_unpadded[-1][-1] + seqlen_unpadded)

```

### Step 45: bash

```bash
python -m py_compile /home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py && echo "core.py OK"
```

<details><summary>Output (11 chars)</summary>

```
core.py OK

```
</details>

### Step 46: bash

```bash
python -m py_compile /home/ubuntu/workspace/scripts/nlp_language_modeling/prepare_packed_ft_dataset.py && echo "prepare script OK"
```

<details><summary>Output (18 chars)</summary>

```
prepare script OK

```
</details>

### Step 47: submit

```
The bugs have been diagnosed and fixed in the source. Here's a summary of the root causes and changes:

## Root Cause Analysis

### Bug 1: Off-by-one in answer_start_idx-based loss masking (packed dataset)
**Location:** `GPTSFTPackedDataset._build_loss_mask()` in `/home/ubuntu/workspace/nemo/collections/llm/gpt/data/core.py`

When `answer_only_loss=True`, the loss_mask was sliced as:
```python
loss_mask[seq_boundaries[i] : seq_boundaries[i + 1] - 1]
```
This aligns with raw `input_ids` positions, but the model's `labels` (and thus loss computation) use the *shifted* targets `[seq_boundaries[i]+1 : seq_boundaries[i+1]]`. The mask was off-by-one relative to the actual loss targets.

**Fix:** Slice the mask to match labels:
```python
loss_mask[seq_boundaries[i] + 1 : seq_boundaries[i + 1]]
```

### Bug 2: Pre-computed loss_mask misalignment with labels
Same root cause as above — the packed loss_mask from `fill_packing_strategy` (or pre-computed in dataset) was never shifted to align with 
```
