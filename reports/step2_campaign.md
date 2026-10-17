# Step 2: Did Harbour's 15% campaigns pay for themselves — and how sure can we be?

## Conclusion

Harbour ran two 8-day campaigns (12–19 March and 12–19 May 2026) with 15% off 9 cold-coffee and dessert items. They gave away **$472** in discounts (measured). To judge them, we estimated what Harbour would have sold without the campaign.

- **Choosing a method:** we compared four predictors on a forward-in-time test.
  - A **linear regression** on weekday, trend and same-day Garden + Uptown sales was the most accurate.
  - Gradient boosting was 5–22% less accurate in the configuration tested, so we did not use it.
- **Estimated extra promoted-item sales:** **−5 units in March** (approximate 90% range −45 to +30) and **−16 in May** (−55 to +19). Break-even was about **+69 and +90**.
- **Estimated effect on Harbour's total gross profit:** **−$308** (March) and **−$391** (May).
- **Robustness:** the same picture holds with weekday and trend only, with Garden or Uptown alone as the comparison, after removing repeated rows, and across four cost scenarios.

**The tested models do not support a break-even lift under the stated assumptions.**

**Recommendation:** do not repeat the campaign unchanged. If Stories wants these discounts, test them by randomizing offer days, with daily gross profit as the main outcome. Detecting a +$30/day profit gain needs about 107 offer days and 107 no-offer days. A 6-week pilot can only detect about +$67/day, so treat it as a first check, not proof.

![Actual vs predicted](figures/campaign_counterfactual.png)

## Which predictor?

Mean absolute error over hidden 8-day ordinary periods:

| Method | Promoted units (forward test) | Harbour gross profit (forward test) | Harbour gross profit (retrospective test) |
|---|---:|---:|---:|
| Same-weekday average | 25.5 | $299 | $294 (biased by growth) |
| Branch ratio | 28.2 | $300 | $269 |
| **Linear regression** | **20.5** | **$200** | **$174** |
| Gradient boosting (ML) | 24.1 | $244 | $225 |

- **Forward test:** each method uses only earlier days, which mimics real forecasting. It is used to select the method.
- **Retrospective test:** the method is trained on all other ordinary days, as for the campaign estimate. Its errors provide the uncertainty ranges.
- **Overlap:** the 130 windows overlap, which makes them roughly equivalent to 17 independent periods.

## Campaign estimates (linear regression)

| | March | May |
|---|---:|---:|
| Discount given (measured) | $210 | $262 |
| Extra promoted units (≈90% range) | −5 (−45 to +30) | −16 (−55 to +19) |
| Break-even extra units: recorded costs / half costs | +69 / +52 | +90 / +67 |
| Harbour gross profit effect (≈90% range) | −$308 (−$629 to +$45) | −$391 (−$712 to −$38) |
| Same, weekday + trend only (no comparison branches) | −$308 | −$390 |
| Week after the campaign: promoted units / gross profit | −24 / −$364 | +9 / +$21 |

- **Methods disagree on direction for units:** three of the four estimate a small positive effect in one campaign, up to +21 units. All point estimates are far below break-even.
- **Ranges** come from the errors on ordinary periods. They are not causal confidence intervals.

## Measured vs. estimated vs. assumed

- **Measured:**
  - Campaign dates, items and branch, and the $472 of discount.
  - About half of the purchases with a discounted item also contained full-price items.
- **Estimated:** the effects, ranges and break-even levels above.
- **Assumed:**
  - Harbour's relationship to weekday, trend and the other branches would have continued without the campaign.
  - The counterfactual sells the same product mix as the campaign did.
  - Ordinary days carry Harbour's usual 0.55% discount on these items.
- **Not observed:** the campaign's goal, advertising cost and waste avoided. Waste avoided is the main benefit that could still justify a redesigned campaign.

Full analysis: [`notebooks/02_promo_campaign.ipynb`](../notebooks/02_promo_campaign.ipynb).
