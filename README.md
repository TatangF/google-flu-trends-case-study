# Google Flu Trends: why a famous study was wrong

A case study for the question *"Why did a famous dataset or study turn out to be wrong, and what should have caught it?"*

The people behind Google Flu Trends (GFT) were not trying to mislead anyone. This repository shows **where the analysis went wrong** (the automatic selection of 45 queries out of ~50 million by correlation, on 1,152 data points) and **what a skeptical analyst would have checked**, with a small simulation you can run yourself.

> **The notebook is a teaching simulation of the mechanism, not Google's data.** Google never published the 45 queries. All parameters other than the orders of magnitude taken from the papers are modeling choices. See [`docs/SOURCES.md`](docs/SOURCES.md) for what is verified and what still needs checking.

## Contents

| Path | What it is |
|---|---|
| [`slides/GFT_presentation_en.pptx`](slides/GFT_presentation_en.pptx) | 7-slide talk (~15 min) with speaker notes, English |
| [`slides/GFT_presentation_fr.pptx`](slides/GFT_presentation_fr.pptx) | Same talk, French |
| [`notebooks/gft_simulation_en.ipynb`](notebooks/gft_simulation_en.ipynb) | Simulation notebook, English (outputs included) |
| [`notebooks/gft_simulation_fr.ipynb`](notebooks/gft_simulation_fr.ipynb) | Same notebook, French |
| [`docs/SOURCES.md`](docs/SOURCES.md) | Sources, links, and verification status |

## Run the notebook

```bash
git clone https://github.com/TatangF/google-flu-trends-case-study
cd google-flu-trends-case-study
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt jupyterlab
jupyter lab notebooks/gft_simulation_en.ipynb
```

Runtime is roughly 30 seconds. Results are seeded, so numbers are reproducible.

Headless run (as in CI):

```bash
pip install nbconvert ipykernel
jupyter nbconvert --to notebook --execute notebooks/gft_simulation_en.ipynb --output /tmp/out.ipynb
```

## What the simulation shows

Three experiments, 30 seeds each unless stated otherwise:

1. **Selection.** Picking the best correlations from 10,000+ candidates gives a high in-sample correlation that drops out of sample. The top-20 queries are mostly "winter detectors" (seasonal series unrelated to flu), not flu queries.
2. **Off-season.** A model built on winter detectors misses a non-seasonal epidemic (H1N1-like).
3. **Drift.** A frozen model degrades when query volume changes; recalibrating with lagged CDC data helps.

Headline numbers from the notebook (simulation, not real data):

| Metric | Value |
|---|---|
| Mean correlation of the aggregated model, test set | 0.89 |
| GFT-type MAE vs. "value from 2 weeks ago" (test set) | 0.140 vs. 0.126 |
| Seeds where the GFT-type model is worse than that baseline | 25 / 30 |
| Recalibrated model better than the baseline (test set) | 30 / 30 |
| Epidemic window MAE: GFT-type / baseline / recalibrated | 0.409 / 0.208 / 0.254 |

Note that the recalibrated model is **not** better than the simple baseline on the epidemic window itself. The drift effect is an assumption (all queries scaled by a constant), not a proof of what happened at Google.

## Limitations

- Simulation only: it shows that the mechanism can produce this kind of error, not that it is what happened at Google.
- Parameters (number of candidates, noise levels, drift factor) are arbitrary choices.
- Some figures quoted in the slides come from the papers' supplementary material and should be checked against the original before citing (see `docs/SOURCES.md`).

## License

Code and slides are released under the MIT License (see [`mayerfeld.consulting`](mayerfeld.consulting)). The cited papers remain the property of their publishers; this repository quotes only short facts and figures and links to the originals.
