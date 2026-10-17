# EECE490 Stories Coffee Hackathon

**Team:** Aya Al Daouk, Zahraa Jouni

## Main finding

Harbour's two 15% campaigns on cold coffee and desserts (March and May 2026) cost $472 in discounts and produced no measurable extra sales. Breaking even needed about +30% more units; the estimated lift was +2%, within normal day-to-day noise. We recommend stopping this campaign design and testing future discounts with randomized offer days.

→ **One-page summary:** [`stories_step1/reports/step2_campaign.md`](stories_step1/reports/step2_campaign.md)
→ **Full analysis:** [`stories_step1/notebooks/02_promo_campaign.ipynb`](stories_step1/notebooks/02_promo_campaign.ipynb)
→ **Data-quality audit:** [`stories_step1/reports/step1_audit.md`](stories_step1/reports/step1_audit.md)

## Reproduce

```
cd stories_step1
python -m pip install -r requirements-step1.txt
```

Place the supplied CSV at `stories_step1/data/raw/stories_transactions.csv`, then run the notebooks in order.
