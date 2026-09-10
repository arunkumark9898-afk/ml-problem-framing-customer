# ML Problem-Framing Memo — Customer Churn

## 1. Business decision
The business wants to decide **which customers should receive proactive retention support** before they churn.

## 2. ML question
Given information available at the prediction time, estimate the probability that a customer will churn during the defined future observation window.

## 3. Prediction target
Binary target:
- `1` / `Yes` = customer churns
- `0` / `No` = customer does not churn

## 4. Unit of observation
One customer at one prediction point.

## 5. Action window
A practical deployment setup would score customers at a fixed cadence (for example, monthly) and use the prediction for the following retention-action window. The exact window must be aligned with the business's historical churn label definition.

## 6. Non-ML baseline
Use a transparent rule-based baseline, such as flagging customers with a combination of:
- month-to-month contract,
- short tenure,
- relatively high monthly charges,
- relevant service/support warning signals when available.

The exact thresholds should be selected from the training data and documented rather than guessed after seeing test results.

## 7. Model baseline
Start with Logistic Regression after reproducible preprocessing:
- numerical imputation/scaling,
- categorical imputation/one-hot encoding,
- train/test split with stratification.

## 8. Success metrics
### Model metrics
- Recall: how many actual churners are detected.
- Precision: how many flagged customers are actually churners.
- F1-score: balance between precision and recall.
- Accuracy: overall correctness.

### Business metrics
- retention contacts per 100 customers,
- successful retention outcomes,
- cost of outreach,
- estimated value protected.

## 9. Error costs
**False negative:** A customer likely to churn is not flagged. This may lose a retention opportunity.

**False positive:** A customer is flagged but would not churn. This can waste staff time and annoy the customer.

If false negatives are more costly, the decision threshold may be lowered, but this should be validated against outreach capacity and false-positive cost.

## 10. Responsible-use constraints
The model should not:
- deny service,
- increase essential prices automatically,
- penalize customers,
- make irreversible decisions without human review,
- use unnecessary sensitive attributes.

## 11. Abstention / human review
If model confidence is close to the action threshold, abstain and send the case for human review.

## 12. Monitoring
Track:
- missingness and schema changes,
- feature distribution drift,
- prediction-rate changes,
- precision/recall,
- segment-level performance,
- complaints or unexpected outcomes.

## 13. Rollback
If the model fails quality or responsible-use checks, disable ML scoring and return to the transparent rule-based baseline while investigating the issue.

## 14. Decision to use ML
ML is justified only if it produces useful improvement over the transparent baseline, using information legitimately available at prediction time, without unacceptable privacy, fairness, or operational risk.
