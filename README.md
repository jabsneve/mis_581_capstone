# ABC/XYZ Analysis + Time-Series Forecasting for Retail Inventory Optimization

> Capstone project integrating ABC/XYZ inventory classification with statistical time-series analysis to support inventory optimization.

## Summary
- **Goal:** Build a BI/analytics framework that blends profit-based ABC and variability-based XYZ classification with ACF/PACF diagnostics and Ljung–Box tests to guide model selection and inventory policy.
- **Data:** Synthetic DataCo Smart Supply Chain transactions across 37 months.
- **Key finding:** A "super-Pareto" profit pattern (tiny product set drives the majority of profit) and minimal/weak seasonality in X & Y groups; no seasonality in Z. Use seasonal models selectively; treat Z with non-seasonal or probabilistic approaches and robust safety stock.

## Overview
Retail inventory is noisy, promotion-driven, and often seasonal. Static ABC/XYZ segmentations are helpful but incomplete without predictive diagnostics. This project:

1. Segments products by profit contribution (ABC) and demand variability (XYZ) using coefficient of variation (CV).
2. Tests for seasonal structure with ACF/PACF and Ljung–Box white-noise checks.
3. Maps insights to forecasting/model selection and policy (service levels, safety stock).

### Research Questions & Hypotheses
1) **Which products drive the most profit?**  
   - H₀: No significant difference in average profit across products  
   - H₁: At least one product differs

2) **Which products have the most demand variability?**  
   - H₀: No significant difference in demand variability across products  
   - H₁: At least one product differs

3) **Does seasonality affect stability across XYZ categories?**  
   - H₀: Seasonality has no significant effect across XYZ groups  
   - H₁: Seasonality has a significant effect

## Data
- **Source:** DataCo Smart Supply Chain (synthetic); 37 months of sales/distribution activity.
- **Contents:** Product-level monthly demand and profit features derived from transactional records.
- **Privacy:** With synthetic data analyses were still reported at aggregate levels to maintain best practices.

## Methods
### ABC (Profit) & XYZ (Variability)
- **ABC:** Rank by cumulative profit; assign A/B/C thresholds based on observed “super-Pareto” concentration.
- **XYZ:** Compute CV of demand; assign X (stable), Y (moderate), Z (high variability).

### Seasonality Diagnostics
- **ACF/PACF** to visually assess periodicity and lag structure.  
- **Ljung–Box** to test for residual autocorrelation at seasonal lags.

## Results (Highlights)
- **Profit concentration:** Around 3% of SKUs account for nearly 50% of profit; around 6% for nearly 80% creating the "super-Pareto" effect.
- **Variability mix:** About 46% X, 10% Y, 44% Z (stable vs. volatile split is bimodal).
- **Seasonality:**  
  - **X & Y:** Weak but statistically detectable seasonality at select lags.  
  - **Z:** Variance is largely stochastic with no meaningful seasonality.
- **Inference:**
  - **Reject** H₀ for Questions 1 & 2.  
  - **Do not reject** H₀ for Question 3.
  - **Further analysis:**
    - Use seasonal ARIMA or exponential smoothing for X and Y.  
    - Use non-seasonal (Croston-type or SBA) or probabilistic approaches for Z.
