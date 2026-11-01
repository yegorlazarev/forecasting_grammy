# forecasting_grammy

Grammy 2027 forecast for eight pop categories.

| Notebook | Stage |
|---|---|
| `grammy_nomination_dataset.ipynb` | Data: builds `grammy_nomination_dataset.csv` (artist × season × category) |
| `grammy_stage1_nomination_probit.ipynb` | Stage 1: nomination probabilities — baseline vs eight Bayesian probit models, top-5 shortlists. Default `RUN_MODE="replay"` rebuilds the report from `exports_stage1/` without training; last cell runs an expanded 2018–2025 backtest (requires JAX/NumPyro) |
| `grammy_stage2_3_winners_award_counts.ipynb` | Stage 2: winner probabilities (Bayesian conditional logit); Stage 3: award-count distributions; last cell runs an expanded 2018–2025 backtest |
| `grammy_billboard_only_baselines.ipynb` | Billboard-only baselines for Stages 1–3 (chart exposure only, MLE) for comparison with the Bayesian pipeline; input data embedded; last cell runs an expanded 2018–2025 backtest |
| `grammy_stage123_ridge_nonbayesian.ipynb` | Classical (non-Bayesian) competitors for Stages 1–3: Ridge probit (Billboard-only 8 vs full 27 features) and Ridge conditional logit, penalty tuned on 2022–2023 |

`stage23_inputs/` holds the hashed inputs for Stage 2/3 and the Ridge notebook (work sets, historical outcomes, artist features, Stage 1 exports).

`exports_stage1/` holds the verified Stage 1 outputs (model `compact27-binary-unscaled-v4`, original data snapshot).

`results_2018_2025/` holds the expanded 2018–2025 backtest results (training on earlier seasons only; Stage 2/3 evaluated among official nominees):

| Folder | Produced by |
|---|---|
| `bayesian_stage1/` | `grammy_stage1_nomination_probit.ipynb` |
| `bayesian_stage23/` | `grammy_stage2_3_winners_award_counts.ipynb` |
| `billboard_baseline_123/` | `grammy_billboard_only_baselines.ipynb` |
| `ridge_nonbayesian_123/` | `grammy_stage123_ridge_nonbayesian.ipynb` |
