# Avoiding costly decisions based on misleading profitability numbers

**EECE490 Stories Coffee Hackathon — Team: Aya Al Daouk, Zahraa Jouni**

Stories' reported profit figures point toward two decisions: treat Garden as the weak branch, and keep running discount campaigns. We tested both against the transaction data. Garden's reported margin disadvantage is largely explained by its recorded cost table, which should be audited before anyone acts on it. The tested models do not show that Harbour's campaigns generated enough extra demand to justify repeating them unchanged; a controlled experiment is the next step. A supporting check finds that customer purchase history showed no demonstrated advantage for selecting valuable customers, so it should be validated before any personalised-marketing spend.

| CEO decision | Evidence | Recommended action |
|---|---|---|
| **Should Garden's menu, prices or management be penalised for its low margin?** | Garden's recorded unit costs ≈ Harbour's ÷ 0.7 on all 45 products, including sealed water, and never change. With Harbour's unit costs and Garden's actual sales, its margin goes from **46.9% to 62.9%** (+$15,923 in H1; same after removing repeated rows). | **Audit costing before acting.** Compare invoices and costing rules for water and a few representative products. At stake: up to ≈ $32k/yr if Garden truly overpays and equivalent supply terms are feasible; otherwise, avoiding a wrong decision about the 2nd-largest branch. |
| **Should Harbour repeat its 15% campaign?** | Best of four predictors on a forward-in-time test (gradient boosting did *not* beat linear regression): extra sales **−5 units in March (≈90% range −45 to +30), −16 in May (−55 to +19)**, against a break-even of **+69 / +90**. Estimates remain similar when comparison-branch sales are excluded, and across four cost scenarios. Ranges are approximate and conditional on the model's assumptions. | **Don't repeat it unchanged.** Test future discounts by randomly assigning offer days within weekday-balanced blocks, with gross profit as the outcome. A 6-week pilot's estimated minimum detectable effect is ≈ +$67/day (80% power, 5% level). |
| *Supporting:* **Should Stories invest in personalised marketing based on customer history?** | Among customers seen in Q1, selecting the top 10%, 20% or 30% by Q1 gross profit captured no more Q2 gross profit than 5,000 random selections of the same size (top 20%: $11,410 vs random 95% range $11,497–$12,512; 10% and 30% inside the range). Purchase history did not beat a no-history baseline on held-out data (log-loss difference 0.000); the same method detects a planted habit (−0.031). | **Validate customer-history targeting before committing marketing budget.** 1-day POS audit of how IDs are captured, then a 4-week verified-ID pilot with a pass criterion fixed in advance. No dollar value estimated. |

The two findings are linked: campaign profitability depends on costs, so Step 2 recalculates its conclusion under four cost scenarios informed by Step 3. The conclusion does not change in any of them.

## Key numbers, by type

**Fact** = measured directly from the data. **Model estimate** = depends on a fitted model and its assumptions. **Scenario** = hypothetical "what if", not a measured or promised saving.

| Number | Type | Source |
|---|---|---|
| Garden reported gross margin 46.9% (Harbour 65.0%, Uptown 62.6%) | Fact | [03 §2](notebooks/03_garden_costs.ipynb) |
| Garden recorded unit cost = Harbour's ÷ 0.7 (within 1 cent) on 45 of 45 products; costs never change in 181 days | Fact | [03 §1](notebooks/03_garden_costs.ipynb) |
| Recorded-cost difference vs Harbour's unit costs: $15,923 over 181 days | Fact (about the recorded cost field) | [03 §4](notebooks/03_garden_costs.ipynb) |
| Garden margin 62.9% with Harbour's unit costs | Scenario | [03 §2](notebooks/03_garden_costs.ipynb) |
| ≈ $32,100/yr (×365/181); ≈ $38,700/yr at June's rate | Scenario: cash only if Garden truly overpays *and* equivalent terms are feasible | [03 §4](notebooks/03_garden_costs.ipynb) |
| Campaign discount given: $472 on 542 units (March $210, May $262) | Fact | [02 §1](notebooks/02_promo_campaign.ipynb) |
| Extra promoted units −5 (March), −16 (May) and their ≈90% ranges | Model estimate | [02 §5](notebooks/02_promo_campaign.ipynb) |
| Harbour gross-profit effect −$308 (March), −$391 (May) | Model estimate | [02 §5](notebooks/02_promo_campaign.ipynb) |
| Break-even +69 / +90 extra units | Model estimate, under stated mix, discount and cost assumptions | [02 §6](notebooks/02_promo_campaign.ipynb) |
| Experiment sizing (107 + 107 days for +$30/day; 6-week MDE ≈ +$67/day) | Planning estimate | [02 §10](notebooks/02_promo_campaign.ipynb) |
| 10% discount: $1,707 over 181 days (≈ $3,400/yr) | Fact (annual figure is a scenario) | [03 §8](notebooks/03_garden_costs.ipynb) |
| Q2 gross profit of top 10/20/30% of Q1-seen customers by Q1 GP: $5,674 / $11,410 / $17,487 | Fact (observed, not caused by any campaign) | [04 §4b](notebooks/04_personalised_marketing.ipynb) |
| Random selections of the same size: 95% ranges $5,626–$6,359 / $11,497–$12,512 / $17,448–$18,573 | Estimate (5,000 random draws) | [04 §4b](notebooks/04_personalised_marketing.ipynb) |
| Held-out log-loss difference, history − baseline: 0.000 (real data), −0.031 (planted-habit control); negative = history better | Model estimate | [04 §4](notebooks/04_personalised_marketing.ipynb) |

## Evidence

- **Garden costing:** [summary](reports/step3_garden_costs.md) · [notebook](notebooks/03_garden_costs.ipynb)
- **Harbour campaign:** [summary](reports/step2_campaign.md) · [notebook](notebooks/02_promo_campaign.ipynb)
- **Personalised marketing (supporting):** [summary](reports/step4_personalised_marketing.md) · [notebook](notebooks/04_personalised_marketing.ipynb)
- **Data-quality audit:** [summary](reports/step1_audit.md) · [notebook](notebooks/01_data_audit.ipynb)
- **Reproduction check:** [verification report](reports/verification.md), from a fresh clone and a new Python environment

Each notebook separates **measured** facts, **estimates** and **assumptions**. It also lists the alternative explanations tested, the approaches rejected, weak areas, and a practical test Stories can run. Correlation is not presented as proof of cause.

## Reproduce

```
python -m pip install -r requirements.txt
```

Place the supplied CSV at `data/raw/stories_transactions.csv` (it is not uploaded to GitHub), then run the notebooks in `notebooks/` in order. See [SETUP.md](SETUP.md) for step-by-step instructions.
