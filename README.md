# Stories Coffee: three profit decisions for the board

**EECE490 Stories Coffee Hackathon — Team: Aya Al Daouk, Zahraa Jouni**

**Do first:** audit Garden's cost table. Garden's recorded unit costs are Harbour's ÷ 0.7 on all 45 products. **Earn or retain money:** up to ≈ $32,100/yr if Garden really pays more for the same goods and cheaper equivalent supply is available; then pilot a half-gap price rise at Uptown (≈ $5,272/yr at unchanged demand); and stop repeating Harbour's 15% campaign unchanged. **What could make it disappear:** if Garden's higher costs are only an accounting allocation, correcting them saves no cash; if Uptown loses about 7% or more of its units, the price rise loses gross profit.

All dollar figures are **conditional annualised gross-profit opportunities** (H1 × 365/181). They are not net profit, not promised savings, and must not be added into one total.

## Board decisions

| # | Decision | Conditional annualised GP opportunity | What must be true | Owner | First action | Implementation cost considerations |
|---|---|---|---|---|---|---|
| 1 | **Garden: audit the cost table** before any margin-based decision about Garden | up to ≈ $32,100/yr (procurement opportunity) | Garden's actual costs are confirmed higher **and** equivalent cheaper supply is feasible. Correcting an accounting allocation alone saves no cash | Finance / procurement | Pull invoices for bottled water and 3–5 high-volume products at Garden and Harbour; check the costing rule in the POS/ERP | Staff time; supplier changes may bring contract, logistics and quality costs |
| 2 | **Uptown: proposed half-gap pricing pilot** (+4.7%; Uptown is priced ≈ 91.4% of Harbour on all 45 products) | ≈ $5,272/yr at unchanged demand (see downside table) | Uptown loses less than ≈ 6.97% of units; product mix, costs and discount rates unchanged | Commercial / pricing lead with the Uptown manager | Record pre-pilot weekly gross profit and unit share; agree the guardrail before launch | POS price update, menus and signage, staff briefing; customer goodwill |
| 3 | **Harbour: don't repeat the 15% campaign unchanged** | model-estimated campaign effects of −$308 (March) and −$391 (May) gross profit | Model assumptions in Step 2; these are estimates, not proven causal savings | Marketing with the Harbour manager | Pause repeats until a randomised-day test is designed | Planning time; offer days must be followed exactly at the till |

**Uptown half-gap pilot: downside scenarios** (scenario, not a forecast; full-year run-rate; product mix, unit costs and discount rates unchanged; implementation costs excluded):

| Assumed Uptown unit loss | 0% | 3% | 5% | 7% | 10% |
|---|---:|---:|---:|---:|---:|
| Annualised GP change | +$5,272 | +$3,004 | +$1,491 | −$21 (≈ break-even) | −$2,289 |

At a 5% unit loss, about $1,491/yr is the remaining gross-profit benefit available to cover incremental implementation and ongoing costs. First-year savings after a pilot would be lower than this full-year run-rate.

**Uptown pilot rules.**
* **Primary outcome:** gross profit per day. Detecting a demand loss is not the same as proving the price rise increases profit.
* **Proposed business guardrail:** Uptown's share of chain units sold. The half-gap break-even (≈ 6.97% unit loss) corresponds to ≈ 5.73% relative share decline at Uptown's ≈ 19% share. Two consecutive weekly breaches can trigger reversal. This is not a statistical test and not a guarantee against losses.
* **Assumptions:** the share-to-unit conversion assumes stable comparison branches, product mix and costs. Branch switching or unrelated changes at Garden or Harbour invalidate it.
* **Length:** 8 weeks is an initial pilot that can remain inconclusive. Its rough detectable change (≈ 7.2% of share, ≈ 8.7% of units) is larger than the break-even.
* **Unclear result:** restore the original pre-pilot prices.

**Supporting findings:**
* **Customer targeting:** selecting customers by Q1 spending showed no demonstrated advantage over random selection for Q2 gross profit. Validate customer-history targeting before committing marketing budget ([Step 4](reports/step4_personalised_marketing.md)).
* **10% discount:** $1,707 in H1 (up to ≈ $3,400/yr) with no targeting pattern. Test removal on randomised days; not finding harm would not prove removal is profitable ([notebook 05](notebooks/05_profit_levers.ipynb)).

## Evidence behind the main decisions

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
| Uptown prices ≈ 91.4% and Garden ≈ 95.2% of Harbour's, on all 45 products, unchanged over 181 days | Fact | [05 §2](notebooks/05_profit_levers.ipynb) |
| Uptown half-gap (+4.7%): +$5,272/yr at unchanged units; break-even unit loss ≈ 6.97%; downside table | Scenario + break-even | [05 §2](notebooks/05_profit_levers.ipynb) |
| Half-gap break-even ≈ 6.97% units ≈ 5.73% relative share decline; 8-week rough detectable change ≈ 7.2% of share ≈ 8.7% of units | Planning approximation (assumes stable comparison branches, mix, costs) | [05 §3](notebooks/05_profit_levers.ipynb) |
| Q2 gross profit of top 10/20/30% of Q1-seen customers by Q1 GP: $5,674 / $11,410 / $17,487 | Fact (observed, not caused by any campaign) | [04 §4b](notebooks/04_personalised_marketing.ipynb) |
| Random selections of the same size: 95% ranges $5,626–$6,359 / $11,497–$12,512 / $17,448–$18,573 | Estimate (5,000 random draws) | [04 §4b](notebooks/04_personalised_marketing.ipynb) |
| Held-out log-loss difference, history − baseline: 0.000 (real data), −0.031 (planted-habit control); negative = history better | Model estimate | [04 §4](notebooks/04_personalised_marketing.ipynb) |

## Evidence

- **Garden costing:** [summary](reports/step3_garden_costs.md) · [notebook](notebooks/03_garden_costs.ipynb)
- **Harbour campaign:** [summary](reports/step2_campaign.md) · [notebook](notebooks/02_promo_campaign.ipynb)
- **Profit levers and board table:** [notebook 05](notebooks/05_profit_levers.ipynb)
- **Personalised marketing (supporting):** [summary](reports/step4_personalised_marketing.md) · [notebook](notebooks/04_personalised_marketing.ipynb)
- **Data-quality audit:** [summary](reports/step1_audit.md) · [notebook](notebooks/01_data_audit.ipynb)
- **Reproduction check:** [verification report](reports/verification.md), from a fresh clone and a new Python environment

Each notebook separates **measured** facts, **estimates** and **assumptions**. It also lists the alternative explanations tested, the approaches rejected, weak areas, and a practical test Stories can run. Correlation is not presented as proof of cause.

## Reproduce

```
python -m pip install -r requirements.txt
```

Place the supplied CSV at `data/raw/stories_transactions.csv` (it is not uploaded to GitHub), then run the notebooks in `notebooks/` in order. See [SETUP.md](SETUP.md) for step-by-step instructions.
