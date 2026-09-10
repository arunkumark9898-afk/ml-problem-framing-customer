# ML Problem Framing & Responsible Data Card — Customer Churn

This repository is prepared for the **ML Problem Framing & Responsible Data Card** task.

## Deliverables
1. `problem_framing.md` — ML problem-framing memo
2. `responsible_data_card.md` — responsible data card
3. `baseline_model.ipynb` — reproducible Logistic Regression baseline
4. `risk_register.md` — risk register
5. `data/customer_churn_sample.csv` — synthetic sample for demonstration only

## Important before public submission
The task page provides a **Customer churn training data** file. This package uses a synthetic sample so the notebook is executable without exposing real/customer-provided records.

For the strongest submission, download the official training dataset from the task page, place it in `data/`, and update the notebook's `DATA_PATH` if the filename differs.

**Do not publish real personal/customer data in a public GitHub repository.**

## How to run
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook baseline_model.ipynb
```

The notebook:
- loads the dataset,
- identifies the churn target,
- performs preprocessing,
- trains Logistic Regression,
- prints accuracy/precision/recall/F1,
- displays a confusion matrix,
- compares with a transparent rule baseline,
- demonstrates an abstention zone.

## Suggested public repository name
`ml-problem-framing-customer-churn`
