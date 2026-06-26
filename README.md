# ML Engineering Sample

Calibration data and trace exports for the Jigsaw ML Engineering task collection.

## Contents

- **[DATA_REPORT.md](DATA_REPORT.md)** - Aggregate statistics, per-task leaderboards, and a trace walkthrough of grok-4.3 on Packed-Sequence Pipeline Repair.
- **traces/** - Exported agent trajectories (tool calls and outputs) for selected rollouts.

## Tasks

| Task                             | What it tests                                                                                                                                                                           |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Checkpoint Progression Forensics | Diagnosing PEFT overfitting hidden by falling training loss; connecting training dynamics to downstream benchmark degradation                                                           |
| Cross-Config Doc Journey         | Tracing documents through 7 datatrove pipeline configs at the filter-threshold level; quantifying config overlap; diagnosing defective dedup variants                                   |
| Packed-Sequence Pipeline Repair  | Repairing three defects in a production NeMo-style SFT pipeline (EOS indexing, loss-boundary off-by-one, mask/label shift) from symptoms alone, with no training reproduction available |

## Scorecards

Interactive scorecards with full failure-mode breakdowns:

- [Checkpoint Progression Forensics](https://data.jigsaw.build/ml-engineering/checkpoint-progression-forensics/)
- [Cross-Config Doc Journey](https://data.jigsaw.build/ml-engineering/cross-config-doc-journey/)
- [Packed-Sequence Pipeline Repair](https://data.jigsaw.build/ml-engineering/nm-pack-triple/)
