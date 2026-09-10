# Responsible Data Card — Customer Churn Baseline

## 1. Dataset / intended use
**Task:** Predict whether a customer is likely to churn so that a business can offer appropriate retention support.

**Intended use:** Prioritize voluntary retention outreach, service-quality follow-up, or customer-support review. The prediction is a decision-support signal, not an automatic reason to deny service, change essential terms, or penalize a customer.

**Unit of observation:** One customer record representing the customer state available at the prediction point.

**Prediction target:** `Churn` — whether the customer leaves during the defined observation window.

## 2. Data provenance
The assignment page provides a small labelled customer-churn training dataset and a responsible data-card template. This package includes a small **synthetic sample only** so the notebook can run immediately. For the final submission, place the course-provided training CSV in `data/` and update the filename/schema in the notebook if required.

No real customer personal information should be uploaded to the public repository.

## 3. Features
Typical churn predictors may include tenure, contract type, service subscriptions, payment method, monthly charges and other service-use attributes.

Direct identifiers such as customer ID should not be used as predictive features.

## 4. Sensitive / potentially sensitive attributes
Possible attributes such as age-related indicators, gender, location, or other demographic fields can create fairness concerns. They should be reviewed before deployment. If a sensitive attribute is not necessary for the business decision, exclude it from model inputs. If it is retained for fairness auditing, restrict access and document the purpose.

## 5. Consent and privacy
Use only data collected for a legitimate, documented business purpose and according to the applicable privacy policy and permissions. Minimize data to what is needed for churn prediction. Remove direct identifiers from training and public artifacts. Do not publish real customer records.

## 6. Data quality and missingness
Check duplicate rows, impossible values, missing values, inconsistent categories, and numeric fields stored as text. Missingness should be measured by feature and handled using a reproducible preprocessing pipeline.

## 7. Leakage risks
Do not train on information that becomes available only after the prediction point, such as cancellation confirmation, post-churn complaints, refund records created after cancellation, or retention actions taken because the customer was already known to be leaving.

## 8. Harm analysis
False negatives can miss customers who would benefit from timely support. False positives can waste outreach effort or annoy customers. Over-targeting particular groups can create unfair treatment.

**Mitigation:** use threshold review, segment-level evaluation, human review for high-impact actions, monitoring, and a clear opt-out / support path.

## 9. Evaluation
Report:
- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

Where appropriate, compare performance across relevant customer segments. Recall is important when missing likely churners is costly, but threshold selection should consider the actual business cost of false positives and false negatives.

## 10. Intended decision and non-ML baseline
A simple non-ML baseline can flag customers using a transparent rule, for example:
- short tenure,
- month-to-month contract,
- unusually high monthly charge,
- repeated service/support issues when available.

The ML model should only be adopted if it provides meaningful improvement over the transparent baseline and remains acceptable on fairness, privacy, and operational criteria.

## 11. Ab
stention and human review
If the predicted probability is near the decision threshold, the system should abstain and send the case to a human reviewer. Model output should be shown as a risk signal, not as certainty.

## 12. Monitoring and rollback
Monitor data drift, missingness, prediction rates, precision/recall, and segment-level performance. Revert to the transparent baseline if data quality breaks, performance drops materially, or an unexpected fairness/privacy issue is detected.

## 13. Limitations
This baseline is not proof that churn can be predicted reliably in every business. Churn drivers vary by company, product, time period, geography, and customer population. Validation on current, representative data is required before real-world use.

## 14. Responsible-use statement
This model is intended for **decision support and customer-service improvement**, not for punitive, discriminatory, or essential-service-denial decisions.
