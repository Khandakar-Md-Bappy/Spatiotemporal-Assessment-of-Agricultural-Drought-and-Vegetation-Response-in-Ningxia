Key Scientific Contributions
Indicator Divergence: Proves that VCI, SMDI, SPEI, and TVDI identify different years as the "most severe" drought, demonstrating that drought indicators are not interchangeable.

Detrending Analysis: Shows that a significant portion of the raw VCI–SMDI correlation (0.47) is driven by shared long-term greening/wetting trends, which drops to 0.36 after linear detrending. VCI–SPEI-6, however, remains stable.

Temporal Transferability: Exposes the "random-split illusion." By isolating all preprocessing (scaling, clipping) within training folds, the study proves that within-record interpolation accuracy does not translate to forecasting skill for unseen growing seasons.

Explainable AI (XAI): Utilizes SHAP and permutation importance to reveal that Land Surface Temperature (LST) is the most influential predictor of VCI, despite having a weak linear correlation, highlighting non-linear thermal stress on vegetation.

Methodology & Workflow
The repository is divided into the following reproducible steps:

Data harmonization (QA screening, monthly aggregation, resampling to a 1 km grid).

Calculation of VCI, SMDI (GLDAS), SPEI (ERA5), and TVDI (LST-NDVI feature space).

Regional and pixel-wise Mann-Kendall tests with Benjamini-Hochberg (FDR) correction.

Pooled Spearman correlations (Lag-0 to Lag-2) and raw vs. linearly detrended pixel-wise correlations.

model_training: Random 70:30 split and 5-fold CV for XGBoost, LightGBM, and Random Forest.

loyo_forward_chaining The robust temporal validation scripts. Contains custom logic to ensure target scaling and feature clipping occur strictly inside training folds to prevent data leakage.

shap_interpretation: Generates SHAP summary and dependence plots.

Data Sources
MODIS (Terra): MOD13A2 (NDVI) & MOD11A2 (LST)

GLDAS-Noah v2.1: 0–10 cm Soil Moisture

ERA5-Drought: SPEI-3 & SPEI-6

Station Data: Historical SPI/SPEI dataset for China (Used for external meteorological comparison).
