# Stories Coffee — Step 1 starter

This package contains the data audit only. It does not train a model or make a final business recommendation.

## Run on Zahraa's PC

1. Extract the ZIP. Copy the contents of `stories_step1` into your already cloned `EECE490-HACKATHON-zjad` folder, preserving the `data`, `notebooks`, and `reports` folders. The package uses `README_step1.md` and `requirements-step1.txt` so it does not replace an existing README or requirements file. It does not contain a new Git repository.
2. Open that repository folder in VS Code. Install the Microsoft **Python** and **Jupyter** extensions if needed.
3. Open **Terminal > New Terminal** and run:

   ```powershell
   python -m pip install -r requirements-step1.txt
   ```

4. Open `notebooks/01_data_audit.ipynb`. Click **Select Kernel**, choose **Python Environments**, and choose the same Python installation used by the terminal. Click **Run All**.
5. The final cell should say `Audit completed. Original CSV unchanged.` It regenerates the two aggregate reports under `reports`.

If a package is missing, confirm that the notebook kernel is using the Python installation where you installed the requirements. If the CSV cannot be found, open the repository folder in VS Code and keep the file at `data/raw/stories_transactions.csv`.

## Files

- `data/raw/stories_transactions.csv`: unchanged copy of the supplied data, included so the notebook can run immediately.
- `notebooks/01_data_audit.ipynb`: explanatory notebook with saved outputs.
- `reports/step1_audit.md`: readable audit findings and limitations.
- `reports/step1_audit.json`: the same audit evidence in a structured format.
- `requirements-step1.txt`: Python dependencies for this step.

The CSV is ignored by the included `data/raw/.gitignore` by default. Code and aggregate reports can be versioned separately; graders with the supplied file can place it at the documented path. A Git ignore rule does not remove any file that is already tracked. See the top-level README for the findings built on this audit.

## Verification

Every Python code cell was executed in order using Python 3.12.14 and pandas 2.2.3, and the saved outputs come from those executions. The builder used Python execution rather than a Jupyter server. VS Code reruns the same code using your selected kernel.

The audit retains all original rows, leaves missing customer IDs missing, and treats duplicate removal only as a sensitivity scenario. It checks file integrity, schema, missing data, numeric/date validity, financial identities, transaction metadata, time coverage, product mappings, and repeated-row sensitivity.
