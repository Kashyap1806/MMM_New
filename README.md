Project Overview

Business question: What portion of sales is driven by each channel (Search, Social, Display, etc.), and how should we reallocate spend to improve total sales/ROI?
Approach:
- Transform media with adstock (carryover) and saturation (diminishing returns).
- Fit regularized linear models (Ridge/Lasso) to stabilize channel effects and reduce multicollinearity.
- Include non-media controls (seasonality, trend, price/promo, holidays) to isolate causal-ish media effects.
- Convert coefficients to marginal and average ROAS, build response curves, and run what-if simulations for budget shifts.

📦 Data

Grain: Weekly (can be adapted to daily or monthly).

Inputs:

- sales: target variable (units or revenue).
- media_spend_*: per-channel spend (e.g., search, social, display, video).
- price / promo: merchandising & pricing signals.
- seasonality / holiday: calendar features.

Source: Synthetic (simulated) data to demonstrate method; structure matches how you’d treat real datasets.

🧠 Methodology

Transformations
- Adstock: adstock_t = media_t + λ * adstock_{t-1}, where λ is decay (estimated via search/grid).
- Saturation: logistic/Hill or log(1 + x) to model diminishing returns.

Modeling
- Models: OLS baseline, then Ridge and Lasso (scikit-learn).
- Validation: time-based split, walk-forward CV (if enough data), and residual diagnostics.

Features:
- Media (adstocked & saturated)
- Seasonality (Fourier terms or week-of-year dummies)
- Trend (time index)
- Price/promo controls
- Optional: macro indicators

KPIs & Outputs

- Channel coefficients → contribution decomposition (base vs. media).
- ROAS (avg & marginal), elasticities, response curves.
- Budget optimization: simple greedy or grid search to reallocate spend within bounds.

Tech Stack
Python: pandas, numpy, scikit-learn, statsmodels, matplotlib

ROAS (avg & marginal), elasticities, response curves.

Budget optimization: simple greedy or grid search to reallocate spend within bounds.
