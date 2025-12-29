Barra-Style Multi-Factor Risk Model (Market + Size)

This project implements an institutional-grade Barra-style equity risk model from first principles, closely aligned with methodologies used by Morningstar, MSCI Barra, and BlackRock Aladdin.

The model decomposes portfolio risk into systematic factor risk and idiosyncratic risk using cross-sectional regression and factor covariance estimation.

🔍 Model Overview

The risk model is defined as:

Σ
=
𝐵
Σ
𝑓
𝐵
⊤
+
Σ
𝜖
Σ=BΣ
f
	​

B
⊤
+Σ
ϵ
	​


Where:

𝐵
B: factor exposure matrix

Σ
𝑓
Σ
f
	​

: factor covariance matrix

Σ
𝜖
Σ
ϵ
	​

: idiosyncratic (stock-specific) risk

🧠 Factors Implemented
1. Market Factor (Statistical)

Estimated via PCA on standardized stock returns

Captures dominant systematic co-movement

Explains ~40% of cross-sectional variance

2. Size Factor (Fundamental)

Constructed as −log(Market Capitalization)

Cross-sectionally winsorized and z-scored monthly

Built using point-in-time shares outstanding (SimFin)

⚙️ Methodology
Data

Prices: Stooq (free source)

Fundamentals: SimFin (free API)

Frequency: Monthly

Window: Rolling 5–10 year logic

Estimation Steps

Factor exposure construction (Market, Size)

Monthly cross-sectional regression to estimate factor returns

Factor covariance estimation

Idiosyncratic variance from regression residuals

Full asset covariance matrix assembly

Portfolio risk decomposition

📊 Risk Decomposition Example

For an equal-weighted large-cap portfolio:

~90% of risk explained by systematic factors

~10% by idiosyncratic risk

Market factor dominates total risk contribution

Marginal and component risk contributions are computed at both asset and factor levels.

📁 Repository Structure

notebooks/ → step-by-step construction and validation

src/ → reusable model components

data/ → source documentation (no raw data committed)

🎯 Why This Matters

This project demonstrates:

Proper cross-sectional factor pricing (not time-series misuse)

Institutional treatment of factor covariance and residual risk

Full portfolio risk attribution consistent with Barra-style models

🚀 Possible Extensions

Add Value, Momentum, Volatility factors

EWMA / shrinkage covariance estimation

Rolling re-estimation and stability analysis