# Avoiding costly decisions based on misleading profitability numbers

**EECE490 Stories Coffee Hackathon — Team: Aya Al Daouk, Zahraa Jouni**

Stories' reported profit figures point toward two decisions: treat Garden as the weak branch, and keep running discount campaigns. We tested both against the transaction data. The first rests on a costing assumption nobody has verified. The second has no evidence of paying off.

| CEO decision | Evidence | Recommended action |
|---|---|---|
| **Should Garden's menu, prices or management be penalised for its low margin?** | Garden's recorded unit costs ≈ Harbour's ÷ 0.7 on all 45 products, including sealed water, and never change. With Harbour's unit costs and Garden's actual sales, its margin goes from **46.9% to 62.9%** (+$15,923 in H1). | **Audit costing before acting.** Compare invoices and costing rules for water and a few representative products. At stake: ≈ $32k/yr if Garden truly overpays; otherwise, avoiding a wrong decision about the 2nd-largest branch. |
| **Should Harbour repeat its 15% campaign?** | Best of four predictors (tested on 130 hidden periods; gradient boosting did *not* beat linear regression): extra sales **−5 units (March), −16 (May)**, against a break-even of **+72 / +93**. Holds at any plausible cost level. | **Don't repeat it unchanged.** Run any future discount as a randomized test with gross profit as the outcome (≈ 6 weeks). |

The two findings are linked: campaign profitability depends on costs, so Step 2 recalculates its conclusion under different cost assumptions from Step 3. The conclusion does not change.

## Evidence

- **Garden costing:** [summary](reports/step3_garden_costs.md) · [notebook](notebooks/03_garden_costs.ipynb)
- **Harbour campaign:** [summary](reports/step2_campaign.md) · [notebook](notebooks/02_promo_campaign.ipynb)
- **Data-quality audit:** [summary](reports/step1_audit.md) · [notebook](notebooks/01_data_audit.ipynb)

Each notebook separates **measured** facts, **estimates** and **assumptions**. It also lists the alternative explanations tested, the approaches rejected, weak areas, and a practical test Stories can run. Correlation is not presented as proof of cause.

## Reproduce

```
python -m pip install -r requirements.txt
```

Place the supplied CSV at `data/raw/stories_transactions.csv` (it is not uploaded to GitHub), then run the notebooks in `notebooks/` in order. See [SETUP.md](SETUP.md) for step-by-step instructions.
