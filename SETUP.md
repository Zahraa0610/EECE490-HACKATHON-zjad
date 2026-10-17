# Setup and reproduction

## Run the analysis

1. Clone this repository and open the folder in VS Code. Install the Microsoft **Python** and **Jupyter** extensions if needed.
2. Place the supplied data file at `data/raw/stories_transactions.csv`. It is not in the repository: `data/raw/.gitignore` keeps the transaction data out of GitHub.
3. Open **Terminal > New Terminal** and run:

   ```powershell
   python -m pip install -r requirements.txt
   ```

4. Open each notebook in `notebooks/` in order. Click **Select Kernel → Python Environments**, choose the same Python installation used by the terminal, then click **Run All**.
   - `01_data_audit.ipynb` ends with `Audit completed. Original CSV unchanged.` and regenerates `reports/step1_audit.md` and `reports/step1_audit.json`.
   - `02_promo_campaign.ipynb`, `03_garden_costs.ipynb` and `04_personalised_marketing.ipynb` regenerate the charts in `reports/figures/`.
   - `05_profit_levers.ipynb` produces the board decision table, the Uptown downside scenarios and the pilot rules.

If a package is missing, check that the notebook kernel uses the Python installation where you installed the requirements. If the CSV cannot be found, open the repository folder itself in VS Code and keep the file at `data/raw/stories_transactions.csv`.

## Files

| Path | Contents |
|---|---|
| `README.md` | Findings and recommended decisions |
| `notebooks/01_data_audit.ipynb` | Data-quality audit (integrity, schema, missing values, financial identities, repeated rows) |
| `notebooks/02_promo_campaign.ipynb` | Harbour 15% campaign: four prediction methods compared, campaign effects, break-even, cost sensitivity |
| `notebooks/03_garden_costs.ipynb` | Garden costing pattern, margin under different cost assumptions, 10% discount side note |
| `notebooks/04_personalised_marketing.ipynb` | Customer-history targeting vs random selection, held-out baseline comparison, positive control |
| `notebooks/05_profit_levers.ipynb` | Board decisions: Garden cost audit, Uptown pricing pilot with downside scenarios and guardrail, discount test design |
| `reports/` | One-page summaries of each step, and the figures |
| `requirements.txt` | Python dependencies |

## Verification

See [reports/verification.md](reports/verification.md). Notebooks 01–03 were verified in a fresh environment; notebooks 01–04 were later re-run in the team's existing environment; notebook 05 was re-run and checked again after its final revision. Every analysis keeps all original rows, leaves missing customer IDs missing, and treats removal of repeated rows only as a sensitivity check.
