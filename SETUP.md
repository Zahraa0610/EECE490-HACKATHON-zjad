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
   - `02_promo_campaign.ipynb` and `03_garden_costs.ipynb` regenerate the charts in `reports/figures/`.

If a package is missing, check that the notebook kernel uses the Python installation where you installed the requirements. If the CSV cannot be found, open the repository folder itself in VS Code and keep the file at `data/raw/stories_transactions.csv`.

## Files

| Path | Contents |
|---|---|
| `README.md` | Findings and recommended decisions |
| `notebooks/01_data_audit.ipynb` | Data-quality audit (integrity, schema, missing values, financial identities, repeated rows) |
| `notebooks/02_promo_campaign.ipynb` | Harbour 15% campaign: four prediction methods compared, campaign effects, break-even, cost sensitivity |
| `notebooks/03_garden_costs.ipynb` | Garden costing pattern, margin under different cost assumptions, 10% discount side note |
| `reports/` | One-page summaries of each step, and the figures |
| `requirements.txt` | Python dependencies |

## Verification

All three notebooks were executed top to bottom with Python 3.13.7, pandas 2.2.3, matplotlib 3.10.9 and scikit-learn 1.9.1. The saved outputs come from those runs. Every analysis keeps all original rows, leaves missing customer IDs missing, and treats removal of repeated rows only as a sensitivity check.
