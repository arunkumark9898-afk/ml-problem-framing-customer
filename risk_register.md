# Risk Register — Customer Churn ML

| ID | Risk | Likelihood | Impact | Mitigation | Trigger / Monitoring | Fallback |
|---|---|---|---|---|---|---|
| R1 | Data leakage from post-churn information | Medium | High | Define prediction timestamp and exclude post-outcome fields | Feature review / time-based validation | Remove leaking fields; use rule baseline |
| R2 | Missing or inconsistent values | High | Medium | Profile missingness; impute in pipeline; validate schema | Missingness dashboard | Stop scoring and use baseline |
| R3 | False negatives miss retention opportunities | Medium | High | Track recall; tune threshold using business costs | Recall below agreed floor | Human review / baseline |
| R4 | False positives waste outreach | Medium | Medium | Track precision and contact capacity | Precision or outreach volume degrades | Raise threshold / baseline |
| R5 | Unequal performance across customer groups | Medium | High | Segment-level evaluation; avoid unnecessary sensitive features | Recall/precision gaps | Human review; pause affected segment |
| R6 | Model drift over time | Medium | High | Monitor feature and outcome drift; periodic retraining | Drift/performance alerts | Revert to baseline |
| R7 | Public exposure of customer data | Low | High | Remove identifiers; never commit real records | Repository/data audit | Remove data and rotate access if needed |
| R8 | Over-reliance on model score | Medium | High | Explain as risk signal; human review for uncertain/high-impact cases | Staff feedback / audit | Disable automatic action |
| R9 | Low-quality labels | Medium | Medium | Review label definition and time window | Label-quality checks | Rework labels |
| R10 | Operational failure / unavailable model | Low | Medium | Simple service design and documented fallback | Health checks | Rule-based scoring |
