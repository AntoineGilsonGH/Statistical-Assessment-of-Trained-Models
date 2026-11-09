# Statistical Assessment of Trained Models

A set of notebooks to answer two questions about a trained model, from its per-sample test errors:

1. **How well does it perform, and how precisely do we know it?** (one model)
2. **Is it really better than another model?** (two models, paired)

Written during my internship at the ARAMIS Lab (Paris Brain Institute, 2024), as groundwork for our study of confidence intervals in medical image analysis:

> P. André et al. *Performance uncertainty in medical image analysis: a large-scale investigation of confidence intervals.* [arXiv:2601.17103](https://arxiv.org/abs/2601.17103), 2026.

The notebooks are designed to be reused: you point them to a CSV or Excel file of per-sample errors, and they produce the statistics, plots and a JSON summary.

## Notebooks

| Notebook | Content |
|---|---|
| `1_Data_Simulation.ipynb` | Simulate datasets with known data-generating processes (regression, classification) |
| `2_Model_Fits.ipynb` | Fit standard models and export their per-sample errors to `Errors/` |
| `3_Statistical_Assessment_One_Model.ipynb` | **One model** — see below |
| `Two_Models.ipynb` | **Two models** — confidence interval for the difference and paired tests |
| `Statistical_Assessment_Two_Classifiers.ipynb` | Lighter version for two classifiers (ROC AUC, paired tests, McNemar) |

**One model** (`3_...`):
- Descriptive statistics and plots of the error distribution
- Which parametric distribution fits the errors best (Kolmogorov–Smirnov, MSE between CDFs, KL divergence, likelihood / AIC / BIC), plus a KDE estimate
- Standard error of the mean and confidence intervals: normal, percentile, basic, bias-corrected and BCa bootstrap
- **Real coverage of these intervals**, estimated by resampling from a fitted parametric distribution or from the KDE — that is, how often each method actually contains the true mean
- A short introduction to Bayesian estimation and credible intervals

**Two models**: confidence interval for the mean paired difference; parametric, permutation and bootstrap tests; Wilcoxon signed-rank; McNemar for classifiers.

## Repository layout

```
Data/      simulated datasets
Errors/    per-sample errors of fitted models (inputs of the assessment notebooks)
Summary/   JSON summaries produced by the notebooks
```

## Run

The assessment notebooks open in Colab from the badge at the top of each one. Locally, they need the usual scientific Python stack (`numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `statsmodels`).
