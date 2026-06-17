# ML Engineering Sample

Calibration data and trace exports for the Jigsaw ML Engineering task collection.

## Contents

- **[DATA_REPORT.md](DATA_REPORT.md)** - Aggregate statistics, per-task leaderboards, and a trace walkthrough of grok-4.3 on Checkpoint Progression Forensics.
- **traces/** - Exported agent trajectories (tool calls and outputs) for selected rollouts.

## Tasks

| Task | Description | Models | Rollouts | Panel Pass@1 |
| ---- | ----------- | ------ | -------- | ------------ |
| Checkpoint Progression Forensics | Diagnose PEFT overfitting from 130+ checkpoints | 12 | 111 | 0% |
| Cross-Config Doc Journey | Trace documents through 7 datatrove configs | 12 | 127 | 5.5% |
| Packed-Sequence Pipeline Repair | Fix three interacting bugs in a NeMo SFT pipeline | 11 | 48 | 2.1% |

## Scorecards

Interactive scorecards with full failure-mode breakdowns:

- [Checkpoint Progression Forensics](https://data.jigsaw.build/ml-engineering/checkpoint-progression-forensics/)
- [Cross-Config Doc Journey](https://data.jigsaw.build/ml-engineering/cross-config-doc-journey/)
- [Packed-Sequence Pipeline Repair](https://data.jigsaw.build/ml-engineering/nm-pack-triple/)
