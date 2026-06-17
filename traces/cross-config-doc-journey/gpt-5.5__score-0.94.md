# gpt-5.5 on Cross-Config Doc Journey

**Score:** 0.94
**Tool calls:** 69
**Duration:** N/A
**Trace ID:** `c6cd153c-8d64-4e8f-9c5a-708de72d63b8`

---

## Trajectory

### Step 1: shell

```json
{
  "commands": [
    "ls -la /home/ubuntu/workspace && find /home/ubuntu/workspace -maxdepth 2 -type d -printf '%p\n' | sort | sed -n '1,200p'"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 2: shell

```json
{
  "commands": [
    "find /home/ubuntu/workspace/pipeline-export-proprietary -maxdepth 4 -type f | sort | sed -n '1,240p'",
    "find /home/ubuntu/workspace/defective-export-proprietary -maxdepth 4 -type f | sort | sed -n '1,240p'"
  ],
  "timeout_ms": 120000,
  "max_output_length": 30000
}
```

### Step 3: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json, os\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nfor f in ['comparison_metadata.json','source_corpus/corpus_metadata.json']:\n print('\\n###',f)\n print(open(os.path.join(base,f)).read()[:4000])\nPY\n\nfor d in /home/ubuntu/workspace/pipeline-export-proprietary/runs/*; do echo '###' $(basename $d); sed -n '1,240p' \"$d/pipeline_config.yaml\"; done"
  ],
  "timeout_ms": 120000,
  "max_output_length": 50000
}
```

### Step 4: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd, os\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nfor f in ['retention_matrix.parquet','cross_config_retention.parquet','doc_quality_scores.parquet','filter_decisions.parquet','language_detection.parquet']:\n print('\\n###',f)\n df=pd.read_parquet(os.path.join(base,f))\n print(df.shape)\n print(df.dtypes)\n print(df.head(10).to_string())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 50000
}
```

### Step 5: shell

```json
{
  "commands": [
    "grep -R \"class GopherQualityFilter\" -n /home/ubuntu/workspace/datatrove/src /home/ubuntu/workspace/datatrove/tests | head -20 && grep -R \"class GopherRepetitionFilter\\|class C4QualityFilter\\|class FineWebQualityFilter\\|class C4ParagraphFilter\\|class C4BadWordsFilter\" -n /home/ubuntu/workspace/datatrove/src | head -50"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 6: shell

```json
{
  "commands": [
    "sed -n '1,260p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_quality_filter.py\nprintf '\\n--- c4 ---\\n'\nsed -n '1,320p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/c4_filters.py\nprintf '\\n--- fineweb ---\\n'\nsed -n '1,260p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/fineweb_quality_filter.py\nprintf '\\n--- repetition ---\\n'\nsed -n '1,260p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/gopher_repetition_filter.py\nprintf '\\n--- language? ---\\n'\ngrep -R \"class LanguageFilter\" -n /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters | head -20"
  ],
  "timeout_ms": 120000,
  "max_output_length": 60000
}
```

### Step 7: shell

```json
{
  "commands": [
    "sed -n '1,220p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/filters/language_filter.py"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 8: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json, os, glob\nbase='/home/ubuntu/workspace/pipeline-export-proprietary/runs'\nfor d in sorted(glob.glob(base+'/*')):\n name=os.path.basename(d)\n print('\\n###',name,'stats.json')\n for f in ['stats.json','logs/stats.json','logs/executor.json']:\n  p=os.path.join(d,f)\n  print('---',f)\n  txt=open(p).read()\n  print(txt[:5000])\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 80000
}
```

### Step 9: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport gzip,json,glob,os\nbase='/home/ubuntu/workspace/pipeline-export-proprietary/runs'\nfor d in sorted(glob.glob(base+'/*')):\n name=os.path.basename(d)\n p=glob.glob(d+'/final_output/output.jsonl*')[0]\n opener=gzip.open if p.endswith('.gz') else open\n cnt=0; ids=[]; metas=[]; lens=[]\n with opener(p,'rt',encoding='utf8') as f:\n  for line in f:\n   if not line.strip(): continue\n   cnt+=1\n   if cnt<=3:\n    obj=json.loads(line); ids.append(obj.get('id')); metas.append(obj.get('metadata')); lens.append(len(obj.get('text','')))\n print(name, cnt, p, ids, metas, lens)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 10: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json, glob, os, re\nbase='/home/ubuntu/workspace/pipeline-export-proprietary/runs'\nfor d in sorted(glob.glob(base+'/*')):\n name=os.path.basename(d)\n stats=json.load(open(os.path.join(d,'logs/stats.json')))\n print('\\n###',name)\n for stage in stats:\n  nm=stage['name']\n  st=stage.get('stats',{})\n  if 'FILTER' in nm or 'WRITER' in nm or 'READER' in nm:\n   print(nm)\n   keys=['documents','total','forwarded','dropped']\n   for k in keys:\n    if k in st: print(' ',k,st[k])\n   reasons={k:v for k,v in st.items() if k.startswith('dropped') and k!='dropped'}\n   if reasons: print(' ',reasons)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 50000
}
```

### Step 11: shell

```json
{
  "commands": [
    "for d in /home/ubuntu/workspace/defective-export-proprietary/run-*; do echo '###' $(basename $d); find \"$d\" -maxdepth 2 -type f -printf '--- %p\\n' -exec sh -c 'echo; sed -n \"1,220p\" \"$1\"' sh {} \\; ; done"
  ],
  "timeout_ms": 120000,
  "max_output_length": 100000
}
```

### Step 12: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport os,json,glob\nbase='/home/ubuntu/workspace/defective-export-proprietary'\nfor d in sorted(glob.glob(base+'/run-*')):\n name=os.path.basename(d)\n print('\\n###',name)\n for f in sorted(glob.glob(d+'/*')):\n  print(os.path.basename(f), 'dir' if os.path.isdir(f) else os.path.getsize(f))\n for f in ['pipeline_config.yaml','dedup_config.yaml','filter_log.json','dedup_clusters.json','pii_scan_results.json','curation_filter_independence_analysis.md']:\n  p=os.path.join(d,f)\n  if os.path.exists(p):\n   print('---',f)\n   txt=open(p,encoding='utf8').read()\n   print(txt[:5000].replace('\\n','\\n'))\n # count outputs\n outs=glob.glob(d+'/final_output/output.jsonl*')\n for p in outs:\n  cnt=sum(1 for line in open(p,encoding='utf8') if line.strip())\n  print('output_count',cnt)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 50000
}
```

### Step 13: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json, collections, os\np='/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'\nlangs=collections.Counter(); ids=[]; lens=[]; first_lang_indices=[]; n=0\nfor line in open(p,encoding='utf8'):\n if not line.strip(): continue\n obj=json.loads(line); n+=1\n md=obj.get('metadata',{})\n lang=md.get('language')\n langs[lang]+=1\n if lang!='en' and len(first_lang_indices)<10:\n  first_lang_indices.append((n-1,obj.get('id'),lang,obj.get('url'),len(obj.get('text','')),obj.get('text','')[:100].replace('\\n',' ')))\n if n<=5: ids.append((n-1,obj['id'],lang,md.get('word_count'),md.get('char_count')))\nprint('n',n,'langs',langs)\nprint('first',ids)\nprint('first non-en', first_lang_indices)\n# index ranges by lang changes\nprev=None; ranges=[]; start=0\nfor i,line in enumerate(open(p,encoding='utf8')):\n obj=json.loads(line); lang=obj['metadata'].get('language')\n if prev is None: prev=lang; start=i\n elif lang!=prev:\n  ranges
```

### Step 14: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json, gzip, glob, os, collections\nsource=[]\nfor line in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl',encoding='utf8'):\n obj=json.loads(line); source.append(obj['id'])\nfirst2200=set(source[:2200])\nallids=set(source)\nfor d in sorted(glob.glob('/home/ubuntu/workspace/defective-export-proprietary/run-*')):\n outs=glob.glob(d+'/final_output/output.jsonl*')\n if outs:\n  p=outs[0]; ids=[]\n  opener=gzip.open if p.endswith('.gz') else open\n  with opener(p,'rt',encoding='utf8') as f:\n   for line in f:\n    if line.strip(): ids.append(json.loads(line)['id'])\n  print(os.path.basename(d), len(ids), 'subset_first2200', set(ids)<=first2200, 'same_as_first_n', ids==source[:len(ids)], 'missing_from_first2200', len(first2200-set(ids)), 'extra_not_source', len(set(ids)-allids))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 15: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json, gzip, glob, os\nsource=[json.loads(l)['id'] for l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl')]\nfirst2200=set(source[:2200])\nfor d in sorted(glob.glob('/home/ubuntu/workspace/pipeline-export-proprietary/runs/*')):\n p=glob.glob(d+'/final_output/output.jsonl*')[0]\n opener=gzip.open if p.endswith('.gz') else open\n ids=[json.loads(l)['id'] for l in opener(p,'rt',encoding='utf8') if l.strip()]\n print(os.path.basename(d), len(ids), 'subset_first2200', set(ids)<=first2200, 'num_after_2200', sum(source.index(i)>=2200 for i in ids if i in source))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 16: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nfd=pd.read_parquet(base+'/filter_decisions.parquet')\nprint(fd.groupby(['config','filter_type'])['passed'].agg(['count','sum','mean']).to_string())\nprint('\\nunique filter types', fd.filter_type.unique())\n# compare if pass vectors identical across configs for same filter\nfor ft in sorted(fd.filter_type.unique()):\n pivot=fd[fd.filter_type==ft].pivot(index='doc_id',columns='config',values='passed')\n print('\\n',ft)\n for c in pivot.columns:\n  neq=(pivot[c]!=pivot.iloc[:,0]).sum()\n  print(c,'diff vs',pivot.columns[0],neq)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 50000
}
```

### Step 17: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd\nret=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/retention_matrix.parquet')\ncols=[c for c in ret.columns if c.startswith('kept_')]\nret['n_kept']=ret[cols].sum(axis=1)\nprint(ret['n_kept'].value_counts().sort_index().to_string())\n# patterns most frequent\nret['pattern']=''.join([])\nconfigs=[c.replace('kept_','') for c in cols]\nret['pattern']=ret[cols].apply(lambda r: ''.join('1' if x else '0' for x in r),axis=1)\nvc=ret.groupby('pattern').size().sort_values(ascending=False)\nprint('\\npatterns order',configs)\nprint(vc.head(30).to_string())\n# only one config counts\nfor col in cols:\n cnt=((ret[col]) & (ret[cols].sum(axis=1)==1)).sum()\n print(col,cnt)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 18: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd,json\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nret=pd.read_parquet(base+'/retention_matrix.parquet')\nlang=pd.read_parquet(base+'/language_detection.parquet')\nret=ret.merge(lang[['doc_id','metadata_language','detected_language','confidence']],on='doc_id')\ncols=[c for c in ret.columns if c.startswith('kept_')]\nprint('retention by metadata_language')\nfor langval,g in ret.groupby('metadata_language'):\n print('\\n',langval,len(g))\n print(g[cols].mean().round(4).to_string())\n print(g[cols].sum().astype(int).to_string())\n# patterns by language\nret['pattern']=ret[cols].apply(lambda r: ''.join('1' if x else '0' for x in r),axis=1)\nprint('\\nPatterns by language')\nfor langval,g in ret.groupby('metadata_language'):\n print('\\n',langval)\n print(g['pattern'].value_counts().head(10).to_string())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 30000
}
```

### Step 19: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,pandas as pd\nids=['fr_0000','de_0000']\nfor line in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl',encoding='utf8'):\n obj=json.loads(line)\n if obj['id'] in ids:\n  print('\\n###', obj['id'], obj['metadata'])\n  print(repr(obj['text'][:1000]))\n  lines=[l for l in obj['text'].split('\\n') if l.strip()]\n  print('lines',len(lines),'ends terminal',sum(l.endswith(('.', '?','!','\"',\"'\")) for l in lines), 'line_punct_ratio',sum(l.endswith(('.', '?','!','\"',\"'\")) for l in lines)/len(lines))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 20: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport sys,json\nsys.path.insert(0,'/home/ubuntu/workspace/datatrove/src')\nfrom datatrove.utils.text import split_into_words, split_into_sentences\nprint(split_into_words('Hello, world! This is a test.', 'eng'))\nprint(split_into_sentences('Hello world. How are you?','eng'))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 21: shell

```json
{
  "commands": [
    "/home/ubuntu/workspace/.venv/bin/python - <<'PY'\nimport sys,json\nsys.path.insert(0,'/home/ubuntu/workspace/datatrove/src')\nfrom datatrove.utils.text import split_into_words, split_into_sentences\nprint(split_into_words('Hello, world! This is a test.', 'eng'))\nprint(split_into_sentences('Hello world. How are you?','eng'))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 22: shell

```json
{
  "commands": [
    "sed -n '1,360p' /home/ubuntu/workspace/datatrove/src/datatrove/utils/text.py\nsed -n '1,260p' /home/ubuntu/workspace/datatrove/src/datatrove/utils/word_tokenizers.py\nsed -n '1,220p' /home/ubuntu/workspace/datatrove/src/datatrove/utils/sentence_tokenizers.py"
  ],
  "timeout_ms": 120000,
  "max_output_length": 60000
}
```

### Step 23: shell

```json
{
  "commands": [
    "sed -n '260,560p' /home/ubuntu/workspace/datatrove/src/datatrove/utils/word_tokenizers.py"
  ],
  "timeout_ms": 120000,
  "max_output_length": 30000
}
```

### Step 24: shell

```json
{
  "commands": [
    "python - <<'PY'\nmods=['spacy','nltk','regex','numpy','pandas','pyarrow','fasttext','loguru']\nfor m in mods:\n try:\n  __import__(m); print(m,'ok')\n except Exception as e:\n  print(m,'FAIL',e)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 25: shell

```json
{
  "commands": [
    "grep -E '^(eng|en),' /home/ubuntu/workspace/datatrove/src/datatrove/assets/tokenizer_assignment.csv | head -20"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 26: shell

```json
{
  "commands": [
    "find /home/ubuntu -path '*c4_badwords*' -type f -o -path '*badwords*' -type f | sed -n '1,200p'\nfind /home/ubuntu -type f -name '*bad*word*' | sed -n '1,200p'"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 27: shell

```json
{
  "commands": [
    "find /home/ubuntu -maxdepth 5 -type f | grep -Ei 'bad|dirty|naughty|obscene|filters|c4' | sed -n '1,200p'"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 28: shell

```json
{
  "commands": [
    "grep -R \"doc_quality_scores\\|alpha_ratio\\|terminal_punct_ratio\\|type_token_ratio\" -n /home/ubuntu/workspace | head -50"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 29: shell

```json
{
  "commands": [
    "sed -n '1,220p' /home/ubuntu/workspace/datatrove/src/datatrove/pipeline/stats/word_stats.py"
  ],
  "timeout_ms": 120000,
  "max_output_length": 30000
}
```

### Step 30: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,collections,os\np='/home/ubuntu/workspace/defective-export-proprietary/run-7e4b19f0/dedup_clusters.json'\nd=json.load(open(p))\nflags=d['flagged_samples']\nprint('n flags',len(flags), 'counts lang', collections.Counter(f['language'] for f in flags))\nfor lang in ['en','fr','de']:\n ratios=[f['overlap_ratio'] for f in flags if f['language']==lang]\n print(lang,len(ratios), min(ratios) if ratios else None, max(ratios) if ratios else None, sum(ratios)/len(ratios) if ratios else None)\nprint('first/last flags', flags[:5], flags[-5:])\n# output missing by language from first 2200\nsource=[]\nlang_by={}\nfor i,line in enumerate(open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl',encoding='utf8')):\n obj=json.loads(line); source.append(obj['id']); lang_by[obj['id']]=obj['metadata']['language']\nids=[json.loads(line)['id'] for line in open('/home/ubuntu/workspace/defective-export-proprietary/run-7e4b19f0/final
```

### Step 31: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,gzip,glob,os,collections\n# load clean sets\nsets={}\nfor name in ['conservative','multilingual','permissive','fineweb_production','minimal_english','repetition_heavy','strict_quality']:\n p=f'/home/ubuntu/workspace/pipeline-export-proprietary/runs/{name}/final_output/output.jsonl.gz'\n with gzip.open(p,'rt',encoding='utf8') as f:\n  sets[name]=set(json.loads(l)['id'] for l in f if l.strip())\nfor run in ['run-7e4b19f0','run-a3f8c2d1']:\n p=f'/home/ubuntu/workspace/defective-export-proprietary/{run}/final_output/output.jsonl'\n ids=set(json.loads(l)['id'] for l in open(p,encoding='utf8') if l.strip())\n print('\\n',run,len(ids))\n for name,s in sets.items():\n  print(name,'inter',len(ids&s),'def_only',len(ids-s),'clean_only',len(s-ids),'jacc',len(ids&s)/len(ids|s))\n# clean permissive vs dedup language of differences\nsource=[]; lang_by={}\nfor line in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl
```

### Step 32: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,gzip\np='/home/ubuntu/workspace/pipeline-export-proprietary/runs/permissive/final_output/output.jsonl.gz'\nper=set(json.loads(l)['id'] for l in gzip.open(p,'rt',encoding='utf8') if l.strip())\nsource=[]; obj_by={}\nfor line in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n obj=json.loads(line); source.append(obj['id']); obj_by[obj['id']]=obj\nmiss=[i for i in source[:2200] if i not in per]\nprint(miss)\nfor id in miss:\n o=obj_by[id]\n print(id,o['metadata'],o['url'], o['text'][:500].replace('\\n',' | '))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 33: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd,json\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nret=pd.read_parquet(base+'/retention_matrix.parquet')\ncols=[c for c in ret.columns if c.startswith('kept_')]\nret['n_kept']=ret[cols].sum(axis=1)\nmins=ret[(ret['n_kept']==1)&(ret['kept_minimal_english'])]['doc_id'].tolist()\nprint('minimal only count',len(mins), mins[:20])\nobj_by={}\nfor line in open(base+'/source_corpus/corpus.jsonl'):\n obj=json.loads(line); obj_by[obj['id']]=obj\nqs=pd.read_parquet(base+'/doc_quality_scores.parquet').set_index('doc_id')\nfor id in mins[:10]:\n o=obj_by[id]; print('\\n',id,o['metadata'],o.get('url'), 'idx?', 'text', o['text'][:400].replace('\\n',' | '))\n print(qs.loc[id][['word_count','char_count','line_count','sentence_count','alpha_ratio','stop_word_ratio','bullet_ratio','ellipsis_ratio','terminal_punct_ratio','type_token_ratio']].to_dict())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 30000
}
```

### Step 34: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re,collections,math\nids=['<urn:uuid:a49cae97-d195-4f5e-97a3-0c90cf924f92>','fr_0002','de_0002']\nobjs=[]; obj_by={}; order=[]\nfor line in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n obj=json.loads(line); obj_by[obj['id']]=obj; order.append(obj['id'])\nfor id in ids:\n o=obj_by.get(id)\n if o:\n  print('\\n###',id,'idx',order.index(id),o['metadata'],o['url'])\n  print(o['text'][:1200].replace('\\n',' | '))\n# find similar previous to a49 based on word 3gram Jaccard/containment\ndef toks(t): return re.findall(r\"\\b\\w+\\b\", t.lower())\ndef grams(t,n=3):\n w=toks(t); return set(tuple(w[i:i+n]) for i in range(len(w)-n+1))\ntarget=ids[0]\ntg=grams(obj_by[target]['text']); idx=order.index(target)\nbest=[]\nfor id in order[:idx]:\n g=grams(obj_by[id]['text'])\n if not g or not tg: continue\n inter=len(tg & g)\n # maybe overlap ratio inter/min or inter/len(tg)\n best.append((inter/len(tg), inte
```

### Step 35: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,collections\nobjs=[json.loads(l) for l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl')]\nfor subset,name in [(objs[:2200],'first2200'),(objs,'all')]:\n under=[o for o in subset if o['metadata']['word_count']<50]\n print(name,'under50',len(under),'minwords',min(o['metadata']['word_count'] for o in subset),'minchar',min(o['metadata']['char_count'] for o in subset),'under50 examples')\n for o in under[:5]: print(o['id'],o['metadata'],o['url'],o['text'][:200].replace('\\n',' | '))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 36: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd\nids=['<urn:uuid:b671790f-33c4-4296-8784-1ac2edca9910>','<urn:uuid:ab817a28-3bf9-4039-aabb-c940081670c6>','de_0001']\nret=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/retention_matrix.parquet').set_index('doc_id')\nqs=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/doc_quality_scores.parquet').set_index('doc_id')\nfor id in ids:\n print(id, ret.loc[id].to_dict())\n print(qs.loc[id][['word_count','char_count','line_count','sentence_count','alpha_ratio','stop_word_ratio','terminal_punct_ratio']].to_dict())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 37: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,gzip,glob,os,pandas as pd\nbase='/home/ubuntu/workspace/pipeline-export-proprietary/runs'\nconfigs=sorted(os.listdir(base))\n# maintain metadata order list as in comparison\nconfigs=['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']\nsets={}\nfor c in configs:\n p=f'{base}/{c}/final_output/output.jsonl.gz'\n with gzip.open(p,'rt',encoding='utf8') as f: sets[c]=set(json.loads(l)['id'] for l in f if l.strip())\nprint('counts', {c:len(s) for c,s in sets.items()})\nprint('\\nintersection counts')\nprint(pd.DataFrame([[len(sets[a]&sets[b]) for b in configs] for a in configs], index=configs, columns=configs).to_string())\nprint('\\njaccard')\nprint(pd.DataFrame([[len(sets[a]&sets[b])/len(sets[a]|sets[b]) for b in configs] for a in configs], index=configs, columns=configs).round(3).to_string())\n# containment intersection/row count\nprint('\\ncontainment row share in col')\
```

### Step 38: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd,json\nids=['<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>','<urn:uuid:7df989ff-e6ed-4ed4-9e6d-7f18ad77dff5>','<urn:uuid:a49cae97-d195-4f5e-97a3-0c90cf924f92>','<urn:uuid:897afb88-02e0-41fa-ae1e-d57db783775f>']\nret=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/retention_matrix.parquet').set_index('doc_id')\nqs=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/doc_quality_scores.parquet').set_index('doc_id')\nobj_by={}\nfor line in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n obj=json.loads(line); obj_by[obj['id']]=obj\nfor id in ids:\n print('\\n',id)\n print(ret.loc[id].to_dict())\n print(qs.loc[id][['word_count','char_count','line_count','sentence_count','alpha_ratio','stop_word_ratio','bullet_ratio','ellipsis_ratio','terminal_punct_ratio','type_token_ratio']].to_dict())\n o=obj_by[id]; print(o['metadata'], o['url']); print(o['text'][:350].
```

### Step 39: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re\nfrom collections import Counter\nPUNCT=set('')\ndef split_words(text):\n    # rough: all non-space tokens? datatrove/spacy keeps punctuation; for repetition, words include punctuation tokens maybe. Try regex word tokens.\n    return re.findall(r\"\\S+\", text)\ndef get_n_grams(words,n): return [' '.join(words[i:i+n]) for i in range(len(words)-n+1)]\ndef find_duplicates(x):\n    unique=set(); dup_chars=0; dup=0\n    for e in x:\n        if e in unique:\n            dup_chars+=len(e); dup+=1\n        else: unique.add(e)\n    return dup,dup_chars\ndef find_top_duplicate(x):\n    c=Counter(x); e,n=c.most_common(1)[0]; return len(e)*n, e,n\ndef find_all_duplicate(words,n):\n    n_words=len(words); unique=set(); repeated_chars=0; idx=0; reps=[]\n    while idx<n_words-n+1:\n        ng=''.join(words[idx:idx+n])\n        if ng in unique:\n            repeated_chars+=len(ng); reps.append((idx,ng)); idx+=n\n        else:\n            unique.
```

### Step 40: shell

```json
{
  "commands": [
    "python - <<'PY'\n# same but word regex lower\nimport json,re\nfrom collections import Counter\ndef split_words(text): return re.findall(r\"\\b\\w+\\b\", text.lower())\ndef get_n_grams(words,n): return [' '.join(words[i:i+n]) for i in range(len(words)-n+1)]\ndef find_duplicates(x):\n unique=set(); dc=0; de=0\n for e in x:\n  if e in unique: dc+=len(e); de+=1\n  else: unique.add(e)\n return de,dc\ndef find_top_duplicate(x):\n e,c=Counter(x).most_common(1)[0]; return len(e)*c,e,c\ndef find_all_duplicate(words,n):\n unique=set(); repeated=0; idx=0; reps=[]\n while idx<len(words)-n+1:\n  ng=''.join(words[idx:idx+n])\n  if ng in unique:\n   repeated+=len(ng); reps.append(ng); idx+=n\n  else: unique.add(ng); idx+=1\n return repeated,reps\ndef rep(text):\n res={}; lines=re.split(r'\\n+',text); ld,lc=find_duplicates(lines); res['dup_line_frac']=ld/len(lines); res['dup_line_char_frac']=lc/len(text)\n words=split_words(text)\n for n,thr in [(2,0.2),(3,0.18),(4,0.16)]:\n  ng
```

### Step 41: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re,collections\nobj_by={}\nfor l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n o=json.loads(l); obj_by[o['id']]=o\nid='<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>'\nw=re.findall(r\"\\b\\w+\\b\", obj_by[id]['text'].lower())\nfor n in [2,3,4]:\n c=collections.Counter(tuple(w[i:i+n]) for i in range(len(w)-n+1))\n print(n,c.most_common(10))\nprint(obj_by[id]['text'])\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 20000
}
```

### Step 42: shell

```json
{
  "commands": [
    "python - <<'PY'\ntry:\n from nltk.tokenize import word_tokenize\n print(word_tokenize('Hello, world! This is a test.', language='english'))\nexcept Exception as e: print('ERR',e)\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 43: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re,collections\nobj_by={}\nfor l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n o=json.loads(l); obj_by[o['id']]=o\nid='<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>'\ntext=obj_by[id]['text']\n# tokens words or single non-whitespace char punctuation\ntokens=re.findall(r\"\\w+|[^\\w\\s]\", text)\nfor n in [2,3,4]:\n grams=[' '.join(tokens[i:i+n]) for i in range(len(tokens)-n+1)]\n c=collections.Counter(grams)\n top=c.most_common(10)\n print(n, top)\n for g,cnt in top[:3]: print('frac', len(g)*cnt/len(text), len(g),cnt,repr(g))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 44: shell

```json
{
  "commands": [
    "cat > /home/ubuntu/workspace/analyze_pipeline.py <<'PY'\nimport json,gzip,glob,os,re,collections,math\nimport pandas as pd\nfrom pathlib import Path\nBASE=Path('/home/ubuntu/workspace/pipeline-export-proprietary')\nRUNS=BASE/'runs'\nCONFIGS=['conservative','fineweb_production','minimal_english','multilingual','permissive','repetition_heavy','strict_quality']\n# load\nsource=[]; obj_by={}; idx_by={}\nfor i,line in enumerate(open(BASE/'source_corpus/corpus.jsonl',encoding='utf8')):\n    obj=json.loads(line); source.append(obj); obj_by[obj['id']]=obj; idx_by[obj['id']]=i\nret=pd.read_parquet(BASE/'retention_matrix.parquet').set_index('doc_id')\nqs=pd.read_parquet(BASE/'doc_quality_scores.parquet').set_index('doc_id')\nlang=pd.read_parquet(BASE/'language_detection.parquet').set_index('doc_id')\nsets={}\nfor c in CONFIGS:\n    p=RUNS/c/'final_output/output.jsonl.gz'\n    with gzip.open(p,'rt',encoding='utf8') as f:\n        sets[c]=set(json.loads(l)['id'] for l in f i
```

### Step 45: shell

```json
{
  "commands": [
    "python - <<'PY'\n# patch script to use csv print instead of markdown\np='/home/ubuntu/workspace/analyze_pipeline.py'\ns=open(p).read()\ns=s.replace(\"print(sel[['label','idx','short_id','meta_lang','kept_count','pattern','defective_kept_by','words','chars','lines','sentences','alpha_ratio','stop_ratio','bullet_ratio','ellipsis_ratio','term_punct_ratio','gopher_hint','fw_line_punct_ratio','fw_short_line_ratio','fw_newline_per_word','c4p_top3_lengths','c4p_pass']].to_markdown(index=False))\", \"print(sel[['label','idx','short_id','meta_lang','kept_count','pattern','defective_kept_by','words','chars','lines','sentences','alpha_ratio','stop_ratio','bullet_ratio','ellipsis_ratio','term_punct_ratio','gopher_hint','fw_line_punct_ratio','fw_short_line_ratio','fw_newline_per_word','c4p_top3_lengths','c4p_pass']].to_csv(index=False))\")\ns=s.replace(\"print(ret2['pattern'].value_counts().head(30).to_markdown())\", \"print(ret2['pattern'].value_counts().head(30).to_csv())\"
```

### Step 46: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re,pandas as pd\nids=['<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>','<urn:uuid:7b4a4e77-bd9b-4f88-99e5-45c3ea132708>','fr_0000','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>','<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>']\nobj={json.loads(l)['id']:json.loads(l) for l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl')}\nfor id in ids:\n t=obj[id]['text']\n # spacy-like tokens words or punctuation or symbols (excluding whitespace)\n toks=re.findall(r\"\\w+|[^\\w\\s]\", t, flags=re.UNICODE)\n alpha=sum(any(c.isalpha() for c in w) for w in toks)/len(toks)\n non_symbol=[w for w in toks if any(not re.match(r'[^\\w\\s]',c) for c in w)]\n # This condition wrong. Just count tokens not all punctuation\n print(id,len(toks),alpha, len(set(w.lower() for w in toks)&set(['the','be','to','of','and','that','have','with'])))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 47: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re,pandas as pd\nids=['<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>','<urn:uuid:2178a29b-8ebd-4286-bf29-ea4790939202>','<urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>','<urn:uuid:7b4a4e77-bd9b-4f88-99e5-45c3ea132708>','<urn:uuid:f7082439-68e9-45b6-a427-4600dceaf5e3>','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>','fr_0000','de_0001','<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>','<urn:uuid:7df989ff-e6ed-4ed4-9e6d-7f18ad77dff5>','<urn:uuid:a49cae97-d195-4f5e-97a3-0c90cf924f92>','fr_0002','<urn:uuid:b671790f-33c4-4296-8784-1ac2edca9910>']\nobj={json.loads(l)['id']:json.loads(l) for l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl')}\nqs=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/doc_quality_scores.parquet').set_index('doc_id')\nSTOP={'the','be','to','of','and','that','have','with'}\ndef gm(text):\n toks=re.findall(r\"\\w+|[^\\w\\s]\", text, flags=re.UNICODE)\n if
```

### Step 48: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json\nid='<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>'\nfor l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n o=json.loads(l)\n if o['id']==id:\n  print(repr(o['text']))\n  for i,line in enumerate(o['text'].split('\\n')): print(i,repr(line),line.endswith(('.', '?','!','\"',\"'\")),len(line))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 49: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd\nid='<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>'\nprint(pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/language_detection.parquet').set_index('doc_id').loc[id].to_dict())\nprint(pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/filter_decisions.parquet').query('doc_id == @id').to_string())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 50: shell

```json
{
  "commands": [
    "zgrep -c '7c72b03f' /home/ubuntu/workspace/pipeline-export-proprietary/runs/fineweb_production/final_output/output.jsonl.gz; zgrep -c '7c72b03f' /home/ubuntu/workspace/pipeline-export-proprietary/runs/minimal_english/final_output/output.jsonl.gz"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 51: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport sys,json,re\nsys.path.insert(0,'/home/ubuntu/workspace/datatrove/src')\nfrom datatrove.utils.text import TERMINAL_PUNCTUATION\nfor id in ['<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>','fr_0000','<urn:uuid:f7082439-68e9-45b6-a427-4600dceaf5e3>','<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>']:\n for l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n  o=json.loads(l)\n  if o['id']==id:\n   lines=[line for line in o['text'].split('\\n') if line.strip()!='']\n   ratio=sum(line.endswith(tuple(TERMINAL_PUNCTUATION)) for line in lines)/len(lines)\n   print(id, ratio, [(line[-10:], line.endswith(tuple(TERMINAL_PUNCTUATION))) for line in lines[:6]])\n   break\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 52: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport sys,json,pandas as pd,re\nsys.path.insert(0,'/home/ubuntu/workspace/datatrove/src')\nfrom datatrove.utils.text import TERMINAL_PUNCTUATION\nids=['<urn:uuid:803e14c3-dc2e-43d6-b75d-6fb3981c4fe6>','<urn:uuid:2178a29b-8ebd-4286-bf29-ea4790939202>','<urn:uuid:e6ba92ad-ed0a-4cac-8e5d-204b78cdd250>','<urn:uuid:7b4a4e77-bd9b-4f88-99e5-45c3ea132708>','<urn:uuid:f7082439-68e9-45b6-a427-4600dceaf5e3>','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>','fr_0000','de_0001','<urn:uuid:bdb7981b-b4a6-4ed4-9fb5-7fc08da1d564>','<urn:uuid:7df989ff-e6ed-4ed4-9e6d-7f18ad77dff5>','<urn:uuid:b671790f-33c4-4296-8784-1ac2edca9910>']\nobj={json.loads(l)['id']:json.loads(l) for l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl')}\nqs=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/doc_quality_scores.parquet').set_index('doc_id')\nfor id in ids:\n lines=[line for line in obj[id]['text'].split('\\n') if line.s
```

### Step 53: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,re\nid='<urn:uuid:f7082439-68e9-45b6-a427-4600dceaf5e3>'\nfor l in open('/home/ubuntu/workspace/pipeline-export-proprietary/source_corpus/corpus.jsonl'):\n o=json.loads(l)\n if o['id']==id:\n  t=o['text'];\n  for m in re.finditer('sex|sexual|Spermatozoidum',t,re.I):\n   print(m.start(), t[max(0,m.start()-120):m.start()+180].replace('\\n',' '))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 54: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd\nlang=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/language_detection.parquet')\nprint(lang.groupby(['metadata_language','detected_language']).size().to_string())\nprint(lang.groupby('metadata_language')['confidence'].describe().round(3).to_string())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 55: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,gzip,collections\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nobjs=[]; lang={}\nfor l in open(base+'/source_corpus/corpus.jsonl'):\n o=json.loads(l); objs.append(o); lang[o['id']]=o['metadata']['language']\nsets={}\nfor c in ['fineweb_production','minimal_english','repetition_heavy','strict_quality','conservative','multilingual','permissive']:\n with gzip.open(f'{base}/runs/{c}/final_output/output.jsonl.gz','rt') as f: sets[c]=set(json.loads(l)['id'] for l in f if l.strip())\nfor c in ['fineweb_production','minimal_english','repetition_heavy','strict_quality','multilingual','conservative','permissive']:\n dropped=set(lang)-sets[c]\n print(c,'dropped by lang',collections.Counter(lang[x] for x in dropped))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 56: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport json,gzip,collections\nbase='/home/ubuntu/workspace/pipeline-export-proprietary'\nids=[]; lang={}\nfor l in open(base+'/source_corpus/corpus.jsonl'):\n o=json.loads(l); ids.append(o['id']); lang[o['id']]=o['metadata']['language']\nfirst=set(ids[:2200])\nfor c in ['conservative','multilingual','permissive','fineweb_production','minimal_english','repetition_heavy','strict_quality']:\n with gzip.open(f'{base}/runs/{c}/final_output/output.jsonl.gz','rt') as f: s=set(json.loads(l)['id'] for l in f if l.strip())\n kept_first=s&first\n print('\\n',c,'first kept',len(kept_first),collections.Counter(lang[x] for x in kept_first),'first dropped',collections.Counter(lang[x] for x in first-kept_first))\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 12000
}
```

### Step 57: shell

```json
{
  "commands": [
    "python - <<'PY'\nimport pandas as pd\nids=['fr_0000','de_0001','<urn:uuid:7c72b03f-b12a-4638-994f-bb2b05350c58>','<urn:uuid:f7082439-68e9-45b6-a427-4600dceaf5e3>']\nlang=pd.read_parquet('/home/ubuntu/workspace/pipeline-export-proprietary/language_detection.parquet').set_index('doc_id')\nfor id in ids: print(id,lang.loc[id].to_dict())\nPY"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 58: edit/create

**Path:** `/home/ubuntu/workspace/REPORT.md`

<details><summary>File content (33288 chars)</summary>

```
# Pipeline retention analysis

Data inspected:

- clean export: `/home/ubuntu/workspace/pipeline-export-proprietary/`
- defective export variants: `/home/ubuntu/workspace/defective-export-proprietary/`
- Datatrove source: `/home/ubuntu/workspace/datatrove/`

I used the final output files and Datatrove executor/stats logs as the source of truth for actual retention. The top-level `stats.json` files and `filter_decisions.parquet` are useful context, but they are not fully consistent with the executed runs.

## Executive summary

1. **Three of the seven “clean” runs are stale/truncated.** `conservative`, `multilingual`, and `permissive` only read the original first **2,200** documents, while the source corpus now has **10,000** documents. This is the single biggest reason their apparent retention is low. They did not filter out the appended 7,800 English documents; they never processed them.

2. **The full-corpus clean runs are: `fineweb_production`, `minimal_english`, `repetition_heavy`, and `strict_quality`.** Their actual retained counts are:

   | config | output docs | retention vs 10k |
   |---|---:|---:|
   | `minimal_english` | 9,800 | 98.00% |
   | `fineweb_production` | 9,727 | 97.27% |
   | `strict_quality` | 7,430 | 74.30% |
   | `repetition_heavy` | 6,230 | 62.30% |
   | `permissive` | 2,198 | 21.98% but only read 2,200 |
   | `multilingual` | 1,774 | 17.74% but only read 2,200 |
   | `conservative` | 1,656 | 16.56% but only read 2,200 |

3. **The biggest actual filter drop is `C4ParagraphFilter` in `repetition_heavy`: 3,259 docs.** This is the answer to the “individual filters mostly pass but retention is low” confusion for that config. The independent `filter_decisions.parquet` says `C4ParagraphFilter` passes everything for `repetition_heavy`, but the actual executor log shows it drops 3,259/9,986 docs after the repetition stage.

4. **`filter_decisions.parquet` is not a reliable representation of the executed pipelines.** It omits actual filters (`FineWebQualityFilter`, `C4BadWordsFilter`), marks some non-executed filters as pass-all/fail-all, and contradicts executor logs for `C4ParagraphFilter` and `GopherRepetitionFilter`.

5. **Language matters, but not because language ID is confused.** The language detector agrees with metadata for all 10,000 docs. The 100 French and 100 German docs are retained only by `permissive`. They are dropped by:
   - English-only language configs (`minimal_english`, `conservative`, `strict_quality`),
   - `fineweb_production` before language ID because FineWeb line-punctuation ratio is 0.0 on the synthetic French/German lines,
   - `multilingual` because it runs `GopherQualityFilter` with English stop words.

6. **Clean config YAMLs do not exactly match executed pipelines.** In particular, clean `conservative` declares MinHash dedup and `multilingual` declares exact dedup, but their executor pipelines have no dedup step. The defective `run-7e4b19f0` is the one that actually applies an exact 3-gram near-dedup stage.

---

## Corpus shape and the stale-run issue

The source corpus has 10,000 documents:

| source index range | language | count |
|---:|---|---:|
| 0-1,999 | English | 2,000 |
| 2,000-2,099 | French | 100 |
| 2,100-2,199 | German | 100 |
| 2,200-9,999 | English | 7,800 |

The clean logs show:

| config | docs actually read by reader | docs never read, relative to 10k | output docs |
|---|---:|---:|---:|
| `conservative` | 2,200 | 7,800 | 1,656 |
| `multilingual` | 2,200 | 7,800 | 1,774 |
| `permissive` | 2,200 | 7,800 | 2,198 |
| `fineweb_production` | 10,000 | 0 | 9,727 |
| `minimal_english` | 10,000 | 0 | 9,800 |
| `repetition_heavy` | 10,000 | 0 | 6,230 |
| `strict_quality` | 10,000 | 0 | 7,430 |

So the apparent similarity between `conservative`, `multilingual`, and `permissive` is partly real for the first 2,200 docs, but their non-retention of docs 2,200-9,999 is not a filter decision.

---

## What each clean pipeline actually executed

The executor logs show the actual stages below.

| config | actual stages | important drops |
|---|---|---:|
| `conservative` | reader(2,200) → GopherQuality → C4Quality → Language(en) → GopherRepetition → PII → writer | Gopher 426, C4Quality 116, Repetition 2 |
| `fineweb_production` | reader(10,000) → FineWebQuality → Language(en/fr/de) → writer | FineWeb line-punctuation 273 |
| `minimal_english` | reader(10,000) → Language(en) → writer | Language 200 |
| `multilingual` | reader(2,200) → Language(en/fr/de) → GopherQuality → PII → writer | Gopher 426 |
| `permissive` | reader(2,200) → GopherRepetition → writer | Repetition 2 |
| `repetition_heavy` | reader(10,000) → GopherRepetition → C4Paragraph → GopherQuality → writer | Repetition 14, C4Paragraph 3,259, Gopher 497 |
| `strict_quality` | reader(10,000) → GopherQuality → C4BadWords → GopherRepetition → C4Quality → Language(en) → writer | Gopher 1,379, BadWords 672, Repetition 5, C4Quality 513, Language 1 |

### Actual drop reasons from logs

`GopherQualityFilt

... (28288 chars truncated)
```
</details>

### Step 59: shell

```json
{
  "commands": [
    "sed -n '1,260p' /home/ubuntu/workspace/REPORT.md"
  ],
  "timeout_ms": 120000,
  "max_output_length": 40000
}
```

### Step 60: shell

```json
{
  "commands": [
    "sed -n '260,620p' /home/ubuntu/workspace/REPORT.md"
  ],
  "timeout_ms": 120000,
  "max_output_length": 60000
}
```

### Step 61: edit/insert

**Path:** `/home/ubuntu/workspace/REPORT.md`

### Step 62: edit/insert

**Path:** `/home/ubuntu/workspace/REPORT.md`

### Step 63: edit/str_replace

**Path:** `/home/ubuntu/workspace/REPORT.md`

### Step 64: shell

```json
{
  "commands": [
    "grep -n \"Scores below\" -A3 -B2 /home/ubuntu/workspace/REPORT.md"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 65: edit/insert

**Path:** `/home/ubuntu/workspace/REPORT.md`

### Step 66: shell

```json
{
  "commands": [
    "sed -n '236,252p' /home/ubuntu/workspace/REPORT.md"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 67: edit/str_replace

**Path:** `/home/ubuntu/workspace/REPORT.md`

### Step 68: shell

```json
{
  "commands": [
    "wc -l /home/ubuntu/workspace/REPORT.md && ls -lh /home/ubuntu/workspace/REPORT.md"
  ],
  "timeout_ms": 120000,
  "max_output_length": 10000
}
```

### Step 69: submit

```
Done — wrote the analysis to:

`/home/ubuntu/workspace/REPORT.md`
```
