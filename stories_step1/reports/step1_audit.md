# Stories Coffee: Step 1 data audit

The file passes the structural and arithmetic checks performed. It is usable for exploratory branch and product analysis with the limitations below. These checks do not verify the completeness of the export or the economic definition of its costs.

## Scope and integrity

- 51,177 product lines, 33,887 purchases, 45 products, and 3 branches.
- Dates: 2026-01-01 through 2026-06-30 (181 calendar days).
- SHA-256: `f1672e728c28295b2b802d878fd38a158ba039827b429355e8438ee0463237a1`.
- Source CSV unchanged. All rows are retained in the primary analysis.
- Python 3.13.7, pandas 2.2.3.

## Results

| Check | Result |
|---|---|
| Required fields other than Customer ID | No missing values |
| Dates, timestamps, numeric fields, quantity and discount validity | No failures in the checks performed |
| Revenue identity | 0 discrepancies above $0.01 per line |
| Gross-profit identity | 0 discrepancies above $0.01 per line |
| Conflicting date/time/branch/order/customer within a transaction | 0 transactions |
| Branch-days with no recorded purchase | 0 of 543 |
| Extra identical rows | 132, affecting 132 purchases |
| Missing Customer ID | 18,691 lines; 12,353 purchases (36.45%) |
| Recorded customer IDs | 3,494; this does not count unidentified customers |
| Branch-product pairs with constant recorded price and cost | 135 constant-price pairs and 135 constant-cost pairs, out of 135 |

## Repeated-row sensitivity

The schema has no unique line-item ID. Exact repeats could be duplicate exports or legitimate repeated items. Neither explanation is proven.

| Measure | Keep all rows (primary) | Remove exact repeats (scenario) |
|---|---:|---:|
| Revenue | $305,925.14 | $305,183.71 |
| Gross profit | $179,430.49 | $178,994.28 |
| Purchases | 33,887 | 33,887 |

Removing repeats reduces revenue by $741.43 and gross profit by $436.21 (0.243% of primary gross profit). This is a sensitivity calculation, not lost profit or recoverable savings. A small overall effect does not guarantee a small effect in every subgroup.

## Decisions and limitations

1. Keep original rows. Recheck the final business finding under the deduplicated scenario.
2. Leave missing Customer IDs missing. Do not group all unidentified purchases into one customer or assume this group behaves like identified customers.
3. Use transaction-level aggregates for basket questions; do not treat every product line as an independent purchase.
4. Treat constant recorded unit costs as accounting inputs until their meaning is verified. Passing arithmetic checks does not validate their business interpretation.
5. Report gross profit, not net profit. Rent, wages, and other operating costs are not separately available.
6. Presence on all branch-dates does not prove all sales were included. Customer-ID consistency across visits also remains an assumption.
7. Observational comparisons cannot by themselves prove that discounts, prices, or branches cause a result.

Next: investigate a focused business question and carry these limitations into its validation.
