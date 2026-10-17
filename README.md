# Avoiding costly decisions based on misleading profitability numbers

**EECE490 Stories Coffee Hackathon — Team: Aya Al Daouk, Zahraa Jouni**

Stories' reported profit figures point toward two decisions: treat Garden as the weak branch, and keep running discount campaigns. We tested both against the transaction data. Garden's reported margin disadvantage is largely explained by its recorded cost table, which should be audited before anyone acts on it. The tested models do not show that Harbour's campaigns generated enough extra demand to justify repeating them unchanged; a controlled experiment is the next step.

| CEO decision | Evidence | Recommended action |
|---|---|---|
| **Should Garden's menu, prices or management be penalised for its low margin?** | Garden's recorded unit costs ≈ Harbour's ÷ 0.7 on all 45 products, including sealed water, and never change. With Harbour's unit costs and Garden's actual sales, its margin goes from **46.9% to 62.9%** (+$15,923 in H1; same after removing repeated rows). | **Audit costing before acting.** Compare invoices and costing rules for water and a few representative products. At stake: up to ≈ $32k/yr if Garden truly overpays and equivalent supply terms are feasible; otherwise, avoiding a wrong decision about the 2nd-largest branch. |
| **Should Harbour repeat its 15% campaign?** | Best of four predictors on a forward-in-time test (gradient boosting did *not* beat linear regression): extra sales **−5 units in March (≈90% range −45 to +30), −16 in May (−55 to +19)**, against a break-even of **+69 / +90**. Estimates remain similar when comparison-branch sales are excluded, and across four cost scenarios. Ranges are approximate and conditional on the model's assumptions. | **Don't repeat it unchanged.** Test future discounts by randomly assigning offer days within weekday-balanced blocks, with gross profit as the outcome. A 6-week pilot's estimated minimum detectable effect is ≈ +$67/day (80% power, 5% level). |

The two findings are linked: campaign profitability depends on costs, so Step 2 recalculates its conclusion under four cost scenarios informed by Step 3. The conclusion does not change in any of them.

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
