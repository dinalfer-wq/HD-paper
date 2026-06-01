# Cross-lingual transfer: source selection vs. in-language data

Code, results, and paper for a controlled study of zero-shot cross-lingual
transfer on XNLI. We compare two remedies for weak target-language transfer,
substituting the fine-tuning source language vs. augmenting with
machine-translated in-language data, across three model families (XLM-R, mBART,
Qwen2.5-0.5B). A 2x2 experiment separates source proximity from source resource
level.

**Headline finding:** changing the fine-tuning source barely moves transfer
(mean +0.4 points across 36 controlled source configurations; neither
typological proximity nor source resource level has a detectable effect), while
in-language data augmentation improves every model (+9.89 points, p=0.002) and
rescues the small decoder LLM by 23 points.

## Repository layout

```
notebooks/   experiment code (Jupyter)
results/     committed CSV outputs and figures
paper/       LaTeX source, references, and compiled PDF
```

## Reproducing the experiments

1. Install dependencies (GPU strongly recommended; Colab T4/L4/A100 all work):
   ```
   pip install -r requirements.txt
   ```
2. Run the notebooks in order. Each has a `QUICK_SMOKE` flag near the top: set
   it `True` first for a fast pipeline check, then `False` for the full run.
   - `notebooks/dcsm_experiment.ipynb` — zero-shot baselines, the
     substitution-vs-augmentation experiment, deficit diagnosis, error analysis.
   - `notebooks/dcsm_2x2.ipynb` — the resource x proximity follow-up.
3. Outputs are written to a local `outputs/` directory and the key tables and
   figures are committed under `results/` for reference.

The XNLI dataset (`facebook/xnli`) downloads automatically on first run.
Typological distances use the `lang2vec` / URIEL `syntax_knn` vector, with a
precomputed fallback table if the package is unavailable.

## Notes on the data

CC-100 pretraining sizes are taken from the XLM-R paper (Conneau et al., 2020,
Appendix A). All accuracy numbers in `results/` come from the runs in this repo;
nothing is hand-entered. Experiments use a single seed (42); see the paper's
Future Work for the multi-seed extension.

## Paper

`paper/paper.pdf` is the compiled write-up. To rebuild from source:
```
cd paper
pdflatex paper && bibtex paper && pdflatex paper && pdflatex paper
```
(Overleaf: upload `paper.tex` + `references.bib` + `paperfigs/`, compiler
pdfLaTeX.)
