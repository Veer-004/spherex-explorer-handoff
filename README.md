# SPHEREx Explorer: handoff package

`spherex_explorer_handoff.zip` contains everything needed to run SPHEREx Explorer on real NASA
SPHEREx data and use its moving-object models:

- **Models:** `stack_model.pkl` (LightGBM + XGBoost stacking classifier, tuned with Optuna) and
  `mover_model.pkl` (tuned LightGBM), plus metrics and plots
- **Dataset:** 15 real SPHEREx fields (per-visit stacks, measurements, Gaia DR3 and CatWISE2020
  catalogs, previews) downloaded from NASA/IPAC IRSA
- **Simulator:** `ml/movers/simulate.py` generates model inputs by injecting sources into real fields
- **App code:** FastAPI backend and React frontend, dataset builder, training scripts, WiseView viewer

Unzip it and start with `spherex_explorer/HANDOFF_README.md`. Model usage and simulator options are
in `spherex_explorer/ml/movers/INTEGRATION.md`.

## Model results

Measured on sky fields that neither the model nor its tuning ever saw:

| Model | Moving objects found | Real non-moving Gaia stars flagged |
|---|---|---|
| Stack (LightGBM + XGBoost, Optuna) | 68.0% | 1.32% |
| Single LightGBM | 65.3% | 0.92% |
| Simple rule | 45.9% | 1.06% |

## Data credits

SPHEREx (NASA/JPL-Caltech) via NASA/IPAC IRSA; Gaia DR3 (ESA/Gaia/DPAC); CatWISE2020
(Marocco et al. 2021); WiseView (public domain, ascl:1806.004).
