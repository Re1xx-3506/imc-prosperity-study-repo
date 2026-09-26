# Mathematical Concepts Study Guide for IMC Prosperity
## Prioritized Study Order

Based on the Frankfurt Hedgehogs' IMC Prosperity 3 (2025) writeup — 2nd place globally out of 12,000+ teams.
Extended with Team Ryan Challman's IMC Prosperity 4 (2026) writeup — 57th globally out of 18,803 teams.

---

## Phase 1: Foundations (~1-2 weeks)

### 1.1 Core Probability & Statistics
**Priority: CRITICAL — everything builds on this**

| Concept | Why |
|---------|-----|
| Expected value, distributions | Most fundamental concept in trading |
| Variance, standard deviation | Risk measurement foundation |
| Conditional probability | Signal detection, Bayes updating |
| Autocorrelation (lag-1) | Detecting mean reversion directly |
| Stationarity | Making data meaningful for analysis |
| P-value interpretation | Knowing when a signal is real |
| Rolling statistics (min/max) | Bot pattern detection, daily extrema |
| Z-scores (when appropriate) | Normalization — only if volatility varies |
| Law of large numbers | Why strategies converge over time |

**Advanced (defer until Phase 3+):**
- Bimodal distributions, regime detection
- Skewness and kurtosis — fat tails matter in trading
- Jensen's inequality — convexity in expected values
- Leave-one-out cross-validation

---

### 1.2 Market Microstructure Fundamentals
**Priority: CRITICAL — market making is Round 1 bread-and-butter**

| Concept | Why |
|---------|-----|
| Bid-ask spreads, edge calculation | Trade price vs true fair price |
| Maker vs Taker dynamics | Passive vs aggressive execution |
| Order book basics — walls, levels | Visualizing the market |
| Fill rate / hit rate | Quote profitability |
| Queue priority (FIFO) | Time-priority matching |
| Adverse selection | Informed vs uninformed flow |
| Wall Mid | Robust proxy for true price |

**Advanced (defer):**
- Microprice — volume-weighted mid
- Order-book imbalance as signal
- Price impact modeling
- Queue estimation

---

### 1.3 Basic Time Series Intuition
**Priority: CRITICAL — underpins all strategy design**

| Concept | Why |
|---------|-----|
| Random walk theory | Some prices truly can't be predicted |
| Mean reversion (OU process intuition) | Core to many strategies |
| Exponential Moving Average (EMA) | Fair value estimation |
| Moving average crossovers | Only valid under certain beliefs |
| Negative autocorrelation | Signal for mean reversion |
| Drift modeling | start + drift × timestamp |
| Running-mean lag | The lag itself can be alpha |

**Advanced (defer until Phase 3+):**
- Autoregressive (AR) models
- Cointegration — critical for pairs/baskets
- Half-life of mean reversion
- Kalman filter for dynamic estimation
- Granger causality
- Hurst exponent

---

## Phase 2: Core Trading Strategies (~2-3 weeks)

### 2.1 Market Making
**Priority: CRITICAL — Rounds 1 and 2 are market making**

| Concept | Why |
|---------|-----|
| Inventory risk management | Position limits, skew, flattening |
| Fill probability vs edge tradeoff | Optimal quoting distance |
| Overbidding / undercutting | Capturing queue priority |
| Spread capture | Earn the spread on round-trips |
| Inventory skew (kq) | Quote asymmetrically to reduce risk |
| Take-and-make | Aggressive then passive approach |
| Symmetric vs asymmetric MM | Match strategy to regime |

**Advanced:**
- Avellaneda-Stoikov model — seminal academic framework
- Asymmetric market making — aggressive bid, wider ask
- Layered ladder strategy — tiered quotes
- Running-mean reset window tuning
- Cross-inventory hedging

---

### 2.2 Options Pricing Fundamentals
**Priority: CRITICAL — Round 3 is options and often highest PnL**

| Concept | Why |
|---------|-----|
| Black-Scholes model | Closed-form option pricing |
| Implied Volatility (IV) | Market's volatility expectation |
| Moneyness (ITM/ATM/OTM) | Strike position classification |
| Extrinsic vs intrinsic value | Time value vs in-the-money |
| The Greeks: Delta (δ) | First-order price sensitivity |
| The Greeks: Gamma (Γ) | Delta's rate of change |
| The Greeks: Vega (ν) | Volatility sensitivity |
| The Greeks: Theta (θ) | Time decay |
| Delta surface | Delta across strikes |
| Delta hedging / rehedging | Managing gamma exposure |

**Advanced (defer to Phase 3+):**
- IV scalping — exploiting short-term IV deviations
- Gamma scalping — underlying movement vs theta decay
- Volatility smile — IV vs moneyness relationship
- Local volatility models
- Heston stochastic volatility model
- Implied binomial trees

---

### 2.3 Statistical Arbitrage
**Priority: HIGH — Round 2 (ETF baskets) and Round 5 (pairs)**

| Concept | Why |
|---------|-----|
| Synthetic replication | Basket = weighted sum of constituents |
| Spread trading | Basket vs synthetic value |
| Mean reversion thresholds | Fixed-level entry signals |
| Premium/discount estimation | Persistent basket bias |
| Cross-product signals | Using one asset to bias another |
| Pairs trading | Mean reversion on paired products |
| Sum-identity baskets | Products summing to constant |
| Beta-neutral positioning | Hedging market exposure in pairs |

**Advanced:**
- Cointegration-based arbitrage
- Kalman filter for dynamic hedge ratios
- Lead-lag relationships
- Implied value extraction

---

### 2.4 Options Strategies (Exotic Structures)
**Priority: HIGH — appears in Rounds 3-5**

| Concept | Why |
|---------|-----|
| Straddle (ATM call + put) | Volatility play |
| Strangle (OTM call + put) | Cheap volatility play |
| Chooser option | Right to call or put |
| Binary option | Cash-or-nothing payoff |
| Knockout/barrier option | Ceases to exist at barrier |
| Rubinstein chooser decomposition | chooser(K, r=0) = C(3w, K) + P(2w, K) |

---

## Phase 3: Risk & Portfolio Management (~1-2 weeks)

### 3.1 Risk Measurement
**Priority: HIGH — prevents catastrophic losses**

| Concept | Why |
|---------|-----|
| Value at Risk (VaR) | 95% worst-case loss estimation |
| Position sizing | Converting limits to lot sizes |
| Maximum regret minimization | Design for worst-case scenarios |
| Drawdown analysis | Peak-to-trough loss measurement |
| Hedging fundamentals | Delta, basket-constituent hedging |
| Half-hedging | Balanced hedged/unhedged compromise |

**Advanced:**
- Sharpe ratio — risk-adjusted return
- Sortino ratio — downside risk-adjusted return
- Kelly criterion — optimal bet sizing for growth
- Tail risk — left-tail events in short-vol positions
- Correlation matrix estimation

---

### 3.2 Portfolio Construction
**Priority: HIGH — Round 5 has 50 products**

| Concept | Why |
|---------|-----|
| Efficient frontier | Pareto-optimal risk-return tradeoff |
| Markowitz optimization | Mean-variance portfolio optimization |
| Monte Carlo simulation | Simulating portfolio outcomes |
| Multi-leg combination | Building desired risk profiles |
| Per-leg sensitivity analysis | Checking each position's impact |

---

## Phase 4: Validation & Discipline (~1 week)

### 4.1 Backtesting Principles
**Priority: CRITICAL — overfitting kills strategies**

| Concept | Why |
|---------|-----|
| In-sample vs out-of-sample | Never tune on test data |
| Landscape stability over peaks | Flat regions = robust params |
| Re-sweep after every baseline change | Params can flip sign |
| Leave-one-out cross-validation | Test across all days |
| Separate backtesting by product type | Bot-interaction vs price-driven |
| Parameter surface stability | Verify flat regions, not just peaks |

**Advanced:**
- Walk-forward validation
- Bootstrap confidence intervals
- Multiple day validation across all available days

---

### 4.2 Signal Detection
**Priority: HIGH — separating signal from noise**

| Concept | Why |
|---------|-----|
| Signal-to-noise ratio | Real signal vs random noise |
| Smoothing filters | EWMA, moving averages |
| Thresholding | Act only when signal is strong |
| False positive management | Track when signals contradict |
| Confidence shrinkage | Shrink signal strength for robustness |

**Advanced:**
- Wiener filter — optimal linear filter
- Kalman filter — recursive state estimation
- Spectral analysis — frequency-domain detection

---

## Phase 5: Optimization (~1 week)

### 5.1 Parameter Tuning
**Priority: HIGH — iteration discipline wins rounds**

| Concept | Why |
|---------|-----|
| Grid search | Discrete parameter sweeps |
| Binary search | For threshold parameters |
| Multi-start optimization | Avoid local optima |
| Pareto frontier computation | Find all Pareto-optimal solutions |
| Coordinate descent | One parameter at a time |

**Advanced:**
- Simulated annealing — global optimization
- Bayesian optimization — efficient hyperparameter tuning
- Gradient descent — continuous optimization

---

## Phase 6: Advanced Topics (~2-3 weeks)

### 6.1 Machine Learning
**Priority: MEDIUM — useful for Round 4+**

| Concept | Why |
|---------|-----|
| Logistic regression | Binary classification (profitable trade?) |
| Feature engineering | Lagged features, derivatives |
| Train-test splits | Proper validation |
| Overfitting avoidance | No models without theory |
| Per-trader weight fitting | Trader ID signals (careful: may not generalize) |
| Regularization (L1/L2) | Prevent overfitting |
| Feature selection | Which features actually contribute? |

**Advanced:**
- Gradient boosting (XGBoost, LightGBM)
- Random forests
- Rolling window retraining

---

### 6.2 Game Theory (Manual Challenges)
**Priority: HIGH — manual rounds add significant PnL**

| Concept | Why |
|---------|-----|
| Payoff function optimization | Maximize expected value |
| Nash equilibrium | Predict competitor behavior |
| Expected payoff modeling | Under competitor assumptions |
| Risk aversion | Avoid high-concentration fields |
| Level-k reasoning | Iterated best-response |
| Round-number anchoring | Psychological pricing biases |
| Cubic penalty functions | Asymmetric penalty shaping |
| Winner's regret calibration | Size for when headlines beat estimates |
| Coordination game dynamics | Defensive clustering |
| Mechanism design | Incentive compatibility |

---

### 6.3 Numerical Methods
**Priority: MEDIUM — for pricing and calibration**

| Concept | Why |
|---------|-----|
| Root-finding (bisection) | Implied vol calculation |
| Newton-Raphson | Fast root-finding for calibration |
| Interpolation | Filling volatility surface gaps |
| Numerical integration | BS pricing when no closed form |
| Monte Carlo with variance reduction | Antithetic variates, control variates |

**Advanced:**
- Finite difference methods — solving PDEs for options
- Numerical differentiation — computing Greeks

---

### 6.4 Stochastic Calculus (Theory)
**Priority: LOW-MEDIUM — deep theoretical foundation**

| Concept | Why |
|---------|-----|
| Brownian motion | Continuous-time price modeling |
| Itô's lemma | Differentiating functions of stochastic processes |
| Martingales | Fair game properties |
| Change of measure | Risk-neutral pricing foundation |
| First passage time | Time until barrier is crossed |
| Geometric Brownian Motion | Stock price dynamics assumption |

---

### 6.5 Advanced Market Microstructure
**Priority: MEDIUM — for edge in market making**

| Concept | Why |
|---------|-----|
| Avellaneda-Stoikov model | High-frequency market making theory |
| Queueing theory | Modeling order flow and fills |
| Information asymmetry | What informed traders know |
| Volatility clustering (ARCH/GARCH) | Large moves follow large moves |
| Bid-ask bounce | Wrap-around effects in discrete pricing |
| Dark pool dynamics | Off-exchange liquidity venues |

---

### 6.6 Location Arbitrage
**Priority: MEDIUM — Round 4 of Prosperity 3**

| Concept | Why |
|---------|-----|
| Conversion mechanics | Internal vs external prices |
| Fee structures | Import/export/transport costs |
| Hidden taker bot detection | Price improvement capture |
| Conversion limits | Position sizing under constraints |
| External market making | Quoting on external venue |
| Arbitrage triangle | Cyclic price relationships |

---

## Summary: Study Priority Table

| Phase | Topic | Priority | Time |
|-------|-------|----------|------|
| 1 | Core Probability & Statistics | CRITICAL | 1-2 wk |
| 1 | Market Microstructure | CRITICAL | 1-2 wk |
| 1 | Time Series Intuition | CRITICAL | 1-2 wk |
| 2 | Market Making | CRITICAL | 1-2 wk |
| 2 | Options Pricing | CRITICAL | 2-3 wk |
| 2 | Statistical Arbitrage | HIGH | 1-2 wk |
| 2 | Exotic Options | HIGH | 1 wk |
| 3 | Risk Measurement | HIGH | 1 wk |
| 3 | Portfolio Construction | HIGH | 1 wk |
| 4 | Backtesting Principles | CRITICAL | 1 wk |
| 4 | Signal Detection | HIGH | 1 wk |
| 5 | Parameter Tuning | HIGH | 1 wk |
| 6 | Machine Learning | MEDIUM | 2 wk |
| 6 | Game Theory | HIGH | 1 wk |
| 6 | Numerical Methods | MEDIUM | 1 wk |
| 6 | Stochastic Calculus | LOW | 2 wk |
| 6 | Advanced Microstructure | MEDIUM | 1 wk |
| 6 | Location Arbitrage | MEDIUM | 1 wk |

---

## Academic References

| Paper | Why |
|-------|-----|
| Avellaneda-Stoikov (2008) — "High-frequency trading in a limit order book" | The seminal market-making model |
| Gatev, Goetzmann, Rouwenhorst (2006) — "Pairs Trading" | Pairs trading foundation |
| Cont (2010) — "Empirical properties of asset returns" | Stylized facts of financial data |
| Rubinstein (1994) — "Some Remarks on Options" | Chooser option decomposition |

---

## Key Competition-Specific Insights

### What Killed Strategies
- Overfitting to single-day patterns (DISHES d4 hot regime)
- Trader-bias signals that didn't generalize across days
- Opening new trading days too early — then implicitly tuning to them
- Optimizing purely on website score (simulation-specific noise)
- Single-tick tightenings on well-tuned strategies (local optima)

### What Won
- Leave-one-out cross-validation across all days
- Full grid re-sweep after every baseline change
- Regime-agnostic strategies (HYDROGEL, ATM strikes)
- Landscape stability over performance peaks
- Small, robust positions over large, brittle ones

---

## Concepts Unique to Each Competition

### Prosperity 3 (Frankfurt Hedgehogs) — 2nd Place
- Wall Mid proxy for true price
- Olivia bot pattern detection (daily extrema)
- Volatility smile parabola fitting for IV scalping
- Cross-product signal integration (Olivia → basket thresholds)
- Hidden taker bot at int(externalBid + 0.5)
- Half-hedging baskets when leading

### Prosperity 4 (Team Ryan Challman) — 57th Place
- EWMA fair vs running-mean fair lag as alpha
- Per-strike strategy dispatch
- Leave-one-out validation across days
- Trader-bias rollback (disabled for not generalizing)
- DISHES regime-aware sizing at 0.06 weight
- Quadratic fee optimization (x = r/2)
- Rubinstein chooser decomposition
- Efficient frontier portfolio construction
