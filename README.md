# FinQA First-Operation Prediction Pilot

## Research Question

How does training sample size affect the ability of multinomial
logistic regression and random forests to predict the first operation
in financial numerical reasoning programs for held-out companies?

## Dataset

The processed dataset is available on Hugging Face:

https://huggingface.co/datasets/DKU-STATS201-Autumn2026/qingyue-individual-proposal

Source dataset:

https://huggingface.co/datasets/orgrctera/uda_fin_qa_qa

Source dataset revision:

`e3fd7b0cde4cf1dafb49f03528f0f9f8275fcd1f`

## Files

- `STATS201_FinQA_First_Operation_Prediction-qingyue.ipynb`:
  data preparation, company-level split, model fitting, evaluation and
  learning curve.
- `requirements.txt`: Python dependencies.

## Methods

The notebook predicts the first operation in each reference program:
`add`, `subtract`, `multiply`, or `divide`.

The comparison includes:

- Class-prior baseline
- Multinomial logistic regression
- Random forest

All methods use the same 25%, 50%, and 100% training budgets and the
same fixed held-out-company test set. The primary metric is multiclass
Log Loss, and Accuracy is reported as a secondary metric.

## How to Rerun

1. Open the `.ipynb` notebook in Google Colab.
2. Select `Runtime` → `Run all`.
3. Wait for the dataset, models, results table and learning curve to be
   generated.

The notebook downloads the source dataset directly from Hugging Face.
No local data path is required.

## Expected Output

A successful run should report:

- 8,190 original rows
- 7,788 usable four-class rows
- 6,168 training rows
- 1,620 held-out test rows
- 109 training companies
- 28 test companies
- 0 company overlap

Expected test Log Loss:

| Training budget | Class prior | Logistic regression | Random forest |
|---|---:|---:|---:|
| 25% | 1.1932 | 0.6832 | 0.7211 |
| 50% | 1.1932 | 0.6299 | 0.7156 |
| 100% | 1.1933 | 0.5933 | 0.7316 |

Small numerical differences may occur across software versions.

## Scope and Limitations

This pilot evaluates prediction of the first operation in one reference
program. It does not evaluate complete program generation, final
numerical-answer accuracy, or valuation accuracy.

Equivalent valid solutions may use a different operation order.
