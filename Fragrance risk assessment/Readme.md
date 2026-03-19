# Inhalation Toxicity Classification of Fragrance Compounds

**Authors:** Dylann Yavorski, Norah Nguyen  
**Course:** Data Science | University of Massachusetts Amherst  
**Date:** May 2025

---

## Overview

This project evaluates the inhalation hazard potential of fragrance compounds
using unsupervised clustering and logistic regression classification in R.
Using publicly available chemical datasets from PubChem and the EPA, we
investigate whether Ames mutagenicity test predictions are meaningful for
grouping toxic compounds, and identify which physicochemical properties best
predict inhalation toxicity.

---

## Research Questions

1. Are Ames Test predictions significant in identifying structural similarities
among toxic compounds?
2. Which physicochemical properties are the strongest predictors of inhalation
toxicity?

---

## Datasets

All datasets sourced from publicly available databases:

| Source | Description |
|--------|-------------|
| PubChem | Fragrance compounds with unknown toxicity (~1,600 obs. after cleaning); known inhalation toxic compounds (~1,500 obs.) |
| EPA CompTox Dashboard | Toxicity classification via Toxtree Revised Cramer Rules (Class I: low, Class II: intermediate, Class III: high) |

> Class II and III compounds were labeled **toxic**; Class I compounds were labeled **safe**.

---

## Methods

### Method 1: Clustering

- **K-Means** — optimal cluster number determined via NbClust (Hubert and
Dindex statistics); fitted with k=7
- **Gaussian Mixture Model (Mclust)** — compared 14 model types; VEV model
optimal up to 6 clusters, EEV thereafter
- Ames mutagenicity predictions evaluated across clusters via chi-square test
(p=0.025)

### Method 2: Logistic Regression

- Merged toxic and non-toxic datasets (422 observations); balanced using ROSE
- Predictors: XLog_P (lipophilicity), water solubility, vapor pressure
- 75/25 train-test split with 10-fold cross-validation
- Model performance evaluated via confusion matrix, ROC curve (AUC=0.57),
and sensitivity/specificity analysis

---

## Key Findings

- Ames Test predictions showed **limited utility** for clustering — most
clusters were not meaningfully differentiated by mutagenicity
- **XLog_P (lipophilicity)** was the only statistically significant predictor
of inhalation toxicity (p=0.041)
- Model predictive performance was marginal (AUC=0.57), likely due to class
imbalance (~11% of observations were non-toxic)
- Water solubility and vapor pressure were not significant predictors

---

## Limitations

- Imbalanced dataset (372 toxic vs. 50 safe observations) limited safe
compound classification
- Wide within-cluster variance suggests high chemical diversity even among
toxic compounds
- Binary classification may be insufficient for continuous toxicological
outcomes

---

## Future Directions

- Incorporate additional non-toxic observations to address class imbalance
- Explore ensemble methods (e.g., random forest) for improved classification
- Expand predictor set with additional toxicologically relevant features

---

## Dependencies
```r
library(NbClust)
library(mclust)
library(ROSE)
library(pROC)
library(ggplot2)
```

---

## References

1. Toxtree Revised Cramer Rules: https://toxtree.sourceforge.net/cramer.html
2. PubChem Fragrance Datasets: https://pubchem.ncbi.nlm.nih.gov
3. EPA CompTox Dashboard: https://comptox.epa.gov/dashboard/batch-search
