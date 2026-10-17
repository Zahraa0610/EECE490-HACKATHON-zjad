# Verification report

Generated 2026-10-17 by re-running every notebook from a clean copy of the repository in a **new, empty Python environment** with only `requirements.txt` installed (plus `nbconvert` to run notebooks from the command line). The outputs were then compared with the notebooks saved in this repository.

- **Repository content:** commit `1eb4bc0` plus the changes committed together with this report
- **Environment:** Python 3.13.7, pandas 2.2.3, numpy 2.5.4, scikit-learn 1.9.1, matplotlib 3.10.9, ipykernel 7.4.0, nbconvert 7.17.2 (fresh virtual environment)
- **Operating system:** Windows 11
- **Data file SHA-256:** `f1672e728c28295b2b802d878fd38a158ba039827b429355e8438ee0463237a1` (matches the hash recorded by the Step 1 audit)

**Overall result: PASS.** Every notebook ran without errors, and every printed result and table is identical to the saved version.

## Notebooks

| Notebook | Code cells | Errors in fresh run | Cells with text output compared | Saved vs fresh outputs |
|---|---:|---:|---:|---|
| `01_data_audit.ipynb` | 8 | 0 | 8 | identical |
| `02_promo_campaign.ipynb` | 12 | 0 | 12 | identical |
| `03_garden_costs.ipynb` | 10 | 0 | 10 | identical |

Each cell's printed text and tables are compared as a whole, so it does not matter how the output happens to be split into chunks. Warnings printed to stderr are excluded because they are not results.

## Generated files

| File | Saved vs regenerated |
|---|---|
| `reports/step1_audit.md` | identical |
| `reports/step1_audit.json` | identical |
| `reports/figures/campaign_counterfactual.png` | identical |
| `reports/figures/garden_cost_rule.png` | identical |

## Key results reproduced in the fresh run

| Check | Output line from the fresh run |
|---|---|
| Audit completion message | `Audit completed. Original CSV unchanged.` |
| Campaign discount given | `Discount given (list price x 15%): $472.08 on 542 units` |
| Model chosen on forward test | `Most accurate method on the forward test: {'Harbour gross profit $': 'Linear regression', 'other-item units': 'Linear regression', 'promoted units': 'Linear regression'}` |
| Experiment sizing | `Estimated minimum detectable effect of a 6-week pilot (21 + 21 days, 80% power, 5% level): about +$67/day` |
| Garden cost rule | `Garden cost within 1 cent of Harbour cost / 0.7: 45 of 45 products` |
| Garden recorded-cost gap | `Gap at recorded costs, 181 observed days (measured from the cost field): $15,923` |
| Garden gap annualised | `Annualised over the observed period (181 days -> 365): $32,111` |
| Garden repeated-row check | `Without repeated rows: reported margin 46.9%, with Harbour's unit costs 62.9%, difference $15,888` |
| 10% discount | `Discount given: $1,707 in 181 days (0.56% of revenue); annualised x365/181: $3,443` |

## How to repeat this check

1. Clone the repository and place the supplied CSV at `data/raw/stories_transactions.csv`.
2. Create a new environment: `python -m venv .venv`, activate it, then `python -m pip install -r requirements.txt nbconvert`.
3. Run `python -m jupyter nbconvert --to notebook --execute --inplace notebooks/*.ipynb` and compare the outputs with this repository's copies.

On Windows, keep the environment at a short path, or enable long paths. Some package files have very long names.
