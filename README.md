# Quantitative Portfolio Optimization & Risk Analysis Engine

A production-grade quantitative asset management engine built in Python. This project utilizes Modern Portfolio Theory (MPT) frameworks and matrix theory to calculate asset statistics, solve quadratic optimization constraints, map the Markowitz Efficient Frontier, and evaluate portfolio resilience under historical macroeconomic stress tests.

## Key Features
* **Automated Data Ingestion:** Asynchronously fetches historical pricing data for any arbitrary asset basket via the Yahoo Finance API.
* **Matrix Optimization Engine:** Implements daily log-returns, annualized mean vector calculations, and dynamic covariance mapping.
* **Algorithmic Asset Allocation:** Uses Sequential Least Squares Programming (SLSQP) to isolate the maximum Sharpe Ratio and Minimum Variance allocation weights.
* **Tail-Risk Diagnostics:** Computes historical Value at Risk (VaR) and Conditional Value at Risk (CVaR/Expected Shortfall) to capture non-Gaussian distribution risks.

---

## The Mathematical Framework

The engine converts asset historical performance data into continuous vectors and metrics using standard linear algebra foundations:

* **Expected Portfolio Return ($E[R_p]$):**
  $$E[R_p] = w^T R$$
  *Where $w$ represents the vector of asset weights and $R$ is the vector of annualized expected returns.*

* **Portfolio Variance ($\sigma_p^2$):**
  $$\sigma_p^2 = w^T \Sigma w$$
  *Where $\Sigma$ represents the $N \times N$ asset covariance matrix.*

* **Sharpe Ratio Optimization:**
  $$\max_{w} \frac{w^T R - R_f}{\sqrt{w^T \Sigma w}} \quad \text{subject to} \quad \sum_{i=1}^N w_i = 1, \quad 0 \le w_i \le 1$$

---

## Visualizing the Efficient Frontier

The model runs 5,000 Monte Carlo portfolio simulations alongside the exact optimized matrix constraints to pinpoint the optimal risk-return profiles.

![Efficient Frontier](output/efficient_frontier.png)

*Note: Replace this image path with the actual location of your generated output plot once pushed to GitHub.*

---

## Repository Structure & Quick Start

### Directory Blueprint
```text
├── README.md                  <- Executive project summary
├── requirements.txt           <- Production dependencies
├── portfolio_engine.py        <- Core Object-Oriented Optimization Class
├── STRESS_TEST_REPORT.md      <- Structural macro stress testing & risk diagnostics
└── output/
    └── efficient_frontier.png <- Generated publication-quality plot
