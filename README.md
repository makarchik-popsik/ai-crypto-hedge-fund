# AI-Driven Crypto Hedge Fund: Multi-Level Portfolio Optimization & Backtesting Pipeline

An institutional-grade algorithmic trading and portfolio management framework built to navigate highly volatile cryptocurrency environments. This project demonstrates an end-to-end quantitative research workflow, evolving from basic technical indicators to a scalable, machine-learning-enhanced multi-asset fund with robust capital preservation protocols.

## 🚀 System Architecture & Evolution

The framework is developed across **5 progressive levels**, reflecting the evolution of systematic trading strategies:

1. **Level 1: Baseline Trend-Following (SMA Crossover)**
   * Implements a classic dual Simple Moving Average crossover logic on Bitcoin (BTC-USD). Established a transparent baseline to evaluate more complex iterations.
2. **Level 2: Predictive Machine Learning Framework**
   * Integrates a `GradientBoostingClassifier` / `Random Forest` ensemble trained on structural features (RSI, historical volatility, rolling volume). The model shifts from simple heuristics to predicting probability distributions of positive regime shifts.
3. **Level 3: Modern Portfolio Theory (Markowitz Mean-Variance)**
   * Expands the asset universe to a multi-token portfolio (7 major liquid assets). Implements a rolling Markowitz optimizer maximizing the expected Sharpe Ratio based on the historical covariance matrix.
   * *Risk Constraints:* Enforces institutional guardrails—minimum 5% exposure per asset (guaranteed diversification) and a maximum 30% cap (concentration risk mitigation).
4. **Level 4: Dynamic Rebalancing & Friction Modeling**
   * Replaces continuous rebalancing with an optimized threshold-drift mechanism (5% boundary). Introduces realistic trading friction (0.1% exchange execution fee) to eliminate backtest overfitting and verify economic viability.
5. **Level 5: Scaled Momentum Pipeline (100+ Assets) & Production Monitoring**
   * Expands the investment universe to 100 assets. Replaces unstable large-scale covariance matrices with a **Cross-Sectional Momentum Rank** combined with an **Absolute Momentum Overlay** (automatically rotating capital 100% into stablecoins (USDT) during macro bear markets).
   * Incorporates an asynchronous, lightweight **Telegram Notification Agent** via the Telegram Bot API for real-time fund metrics and rebalancing logs.

## 📊 Institutional Risk & Friction Modeling

Unlike naive academic backtests, this framework integrates institutional-grade market friction and risk metrics:
* **Total Transaction Costs (0.2% per trade):** Combines the exchange execution fee (0.1%) with an empirical model for **price slippage** and bid-ask spread friction (0.1%) encountered when executing larger block orders in crypto markets.
* **Risk-Free Rate ($R_f = 4\%$):** Adjusted Sharpe and Sortino ratios to include an annualized 4% risk-free rate (representing short-term US Treasury yields) to isolate and evaluate true mathematical Alpha.
* **Advanced Tail-Risk Analytics:** Calculates the **Sortino Ratio** (penalizing exclusively downside volatility) and the **Calmar Ratio** (measuring annualized net return against Maximum Drawdown) to fully evaluate tail-risk exposures.

## 📈 Empirical Insights: The Rebalancing Paradox

During high-volatility, regime-shifting environments (such as the 2022 Crypto Winter), backtest analytics revealed a crucial market phenomenon: **the static passive allocation ($1/N$ Buy & Hold) occasionally outpaced dynamic monthly rebalancing.** ### Key Quantitative Explanations:
1. **The Whipsaw Effect:** Medium-term cross-sectional momentum models systematically buy asset breakouts near localized peaks and are forced to liquidate them at a loss during sharp trend reversals.
2. **Compounding Execution Costs:** Shifting entire fund allocations across 100 highly volatile assets every 30 days generates heavy portfolio turnover. The 0.2% combined slippage and fee drag compounds aggressively over a multi-year horizon, eating away at the Net Asset Value (NAV).
3. **The Robustness of Naive Diversification:** The static portfolio benefits from unoptimized structural stability, confirming that minimizing active trading frequency in highly chaotic market states can serve as an effective risk-mitigation tool.

## 🛠️ Installation & Rapid Deployment

The project is designed to be fully self-contained and reproducible.

### Prerequisites
```bash
pip install -r requirements.txt
