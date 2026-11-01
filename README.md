# forecasting_grammy

Grammy 2027 forecast for eight pop categories.

| Notebook | Stage |
|---|---|
| `grammy_nomination_dataset.ipynb` | Data: builds `grammy_nomination_dataset.csv` (artist × season × category) |
| `grammy_stage1_nomination_probit.ipynb` | Stage 1: nomination probabilities — baseline vs eight Bayesian probit models, top-5 shortlists. Default `RUN_MODE="replay"` rebuilds the report from `exports_stage1/` without training |
| `grammy_stage2_3_winners_award_counts.ipynb` | Stage 2: winner probabilities (Bayesian conditional logit); Stage 3: award-count distributions |

`exports_stage1/` holds the verified Stage 1 outputs (model `compact27-binary-unscaled-v4`, original data snapshot). Known label/identity issues are described in `exports_stage1/DATA_CHANGES.md`.
