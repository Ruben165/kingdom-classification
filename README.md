# Kingdom Classification

Classifies the kingdom of a living organism (e.g. bacteria, virus, plant, vertebrate) from the codon usage frequencies in its mRNA.

- **Dataset:** [Codon Usage (Kaggle)](https://www.kaggle.com/datasets/salikhussaini49/codon-usage), about 13,028 species with 11 kingdom classes. Malformed rows are dropped during cleaning.
- **Models:** Random Forest, XGBoost, and Bagging (with Random Forest estimators), each evaluated before and after a small grid search (3-fold CV).
- **Split:** stratified 60% train / 20% validation / 20% test.
- **Best model:** chosen by validation accuracy among all six versions and saved as `result/model/model_{algorithm}.joblib` (currently XGBoost, about 92% test accuracy).
- **Inference:** the notebook ends with `predict_kingdom()`, which loads the saved model and returns kingdom names for new codon-usage data.

## Structure

```
data/    codon_usage.csv
impl/    Kingdom_Classification.ipynb
result/  saved best model, accuracy, and training-time charts (generated)
```

## Usage

Install `pandas`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn` and `joblib`, then run the notebook from the `impl/` folder. Tuning results are cached in `impl/tuning_cache/` while the notebook runs, and the cache is deleted at the end.
