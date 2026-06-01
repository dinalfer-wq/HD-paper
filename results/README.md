# Results

Committed outputs from the notebooks in `../notebooks/`. These are the exact
numbers reported in the paper.

| File | Produced by | Contents |
|------|-------------|----------|
| `results_zeroshot.csv` | dcsm_experiment | Per-model, per-language zero-shot XNLI accuracy (the baseline) |
| `results_mitigation_deltas.csv` | dcsm_experiment | Pivot and matched-data arms with deltas vs. baseline |
| `policy_summary.csv` | dcsm_experiment | Routed vs. fixed mitigation policies |
| `deficit_diagnosis.csv` | dcsm_experiment | Residual-based data- vs. distance-limited labels |
| `results_2x2.csv` | dcsm_2x2 | Raw accuracy for each source type in the 2x2 |
| `analysis_2x2.csv` | dcsm_2x2 | Per-target deltas and contrasts |
| `figs/` | both | Figures used in the paper |

All figures and tables in the paper are generated from these files.

## Before pushing

The CSV files are written when you run the notebooks. After your final run,
copy them from the notebook's local `outputs/` (and `outputs_2x2/`) directories
into this folder so the committed results match your reported numbers. The
figures here are already the versions used in the paper.
