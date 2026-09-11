# Capability Catalogue

This catalogue describes the currently available Helvetic Research service. The production
MCP surface exposes **89 research tools**. Tool selection remains with the connected AI client;
Helvetic provides deterministic research operations and structured results.

Helvetic Research is research-only. It does not place trades, connect to brokers, or provide
investment advice.

## Strategy and data inputs

| Input | Purpose |
|---|---|
| Natural language or pseudo-code | Translate a precise request into validated Strategy IR v3 |
| Pine-like / TradingView logic | Extract supported rules and translate them into a deterministic specification |
| Structured JSON | Run the rule-based research engine directly |
| Strategy IR v3 | Validate and execute a typed JSON expression tree |
| Supplied OHLCV | Research external, broker, or TradingView bars, including intraday series |
| Supplied signal/positions | Backtest a client-computed signal without executing client code |
| Supplied multi-asset book | Research prices and target weights for a custom portfolio |
| Return stream / track record | Analyse an external or manager-reported performance series |

Ambiguous or unsupported requests return assumptions, questions, and unsupported features. An
`executable=false` response is an honesty control: the engine will not invent a definition and
pretend it fulfilled the request.

## Research types

- Single-instrument signal strategies
- Long-only, short-only, and long/short research
- Multi-asset portfolios and allocation studies
- Momentum rotation and universe research
- Futures and commodity proxies
- Crypto spot and explicitly declared perpetual research
- Synthetic multi-leg option strategies using Black-Scholes repricing
- Custom signals, custom OHLCV, custom portfolios, and external track records

## Indicators and rule logic

Indicator periods are parameterised rather than limited to a few presets.

### Trend and moving averages

SMA, EMA, WMA, HMA, DEMA, TEMA, Supertrend, Parabolic SAR, ADX and directional indicators,
Aroon, Vortex, and Ichimoku.

### Momentum and oscillators

RSI, stochastic, MACD, CCI, Williams %R, ROC, momentum, CMO, TSI, Ultimate Oscillator, KST,
and Coppock Curve.

### Volatility and channels

ATR, realised volatility, Bollinger Bands, Donchian channels, Keltner channels, rolling
highs/lows, and volatility targeting.

### Volume and price structure

OBV, VWAP and anchored VWAP, MFI, CMF, Chaikin Oscillator, Force Index, Ease of Movement,
volume profile POC/value area, pivots, rolling Fibonacci retracements, and Heikin-Ashi.

### Expressions and execution rules

- Comparisons, crosses, membership tests, and nested AND/OR groups
- Arithmetic and reusable computed fields
- Rolling windows and explicitly lagged breakout levels
- Calendar predicates and first/last available bars of a period
- Completed weekly/monthly higher-timeframe filters
- Stateful rules such as highest-since-entry, stored retest values, and position age
- Fixed, volatility-targeted, Kelly, and risk-based sizing
- Stop loss, take profit, trailing stop, ATR stop, and time/calendar exits
- Next-bar execution and configurable signal lag

## Portfolio and cross-asset analysis

- Multi-asset portfolio backtesting
- Monthly, quarterly, semi-annual, annual, or buy-and-hold rebalancing
- CHF, USD, EUR, and GBP reporting currencies
- Currency conversion and FX-impact decomposition
- Exposure by asset, currency, country, and time
- Correlation, risk contribution, and return attribution
- Efficient frontier, maximum Sharpe, minimum volatility, and risk parity
- Composable weight constraints: per-name caps and floors, and per-group exposure caps
- Hedge candidate analysis and strategy combination
- Rebalance-frequency and allocation what-if analysis

## Performance and risk metrics

Metrics are annualised from the observed data frequency rather than assuming daily bars.

- Total and annualised return, CAGR, volatility
- Sharpe, Sortino, Calmar, omega, and ulcer metrics
- Maximum drawdown, duration, and recovery periods
- VaR, CVaR / Expected Shortfall, skew, and kurtosis
- Alpha, beta, R², tracking error, information ratio, and capture ratios
- Win rate, profit factor, payoff ratio, tail ratio, recovery factor
- Gain-to-pain, Ulcer Performance Index, Common Sense Ratio, and CPC Index
- System Quality Number (SQN), per-trade MAE/MFE, and long/short trade splits
- Turnover, exposure, trade statistics, and implementation-cost drag

## Robustness and validation

- Walk-forward out-of-sample analysis
- IID and block-bootstrap Monte Carlo simulation
- Parameter optimisation and sensitivity grids
- Probability of Backtest Overfitting through CSCV
- Probabilistic Sharpe Ratio and Deflated Sharpe Ratio
- Minimum Track Record Length
- Historical stress tests and custom shock scenarios
- Transaction-cost and execution-lag sensitivity
- Trade-order permutation testing to separate a real edge from sequencing luck
- Fee-cushion analysis: how much cost the edge absorbs before it breaks even
- Volatility, trend, and macro regime analysis
- Benchmark-regime Sharpe decomposition showing which regimes carry the edge
- Correlation-regime detection for multi-asset books (diversified vs fused)
- Factor exposure and benchmark regression
- Alpha decay, signal quality, capacity, and market-impact analysis
- EVT tail-risk diagnostics
- A 12-component Research Grade for the strength of evidence

The Research Grade measures methodological robustness. It is not an investment recommendation or
a claim that a strategy is suitable for deployment.

## Data integrity and look-ahead controls

- Signal on bar `t`; execution no earlier than the following bar by default
- Completed-bar higher-timeframe inputs
- Rejection of executable `lead()` expressions
- Warnings for optimistic same-bar breakout logic
- Provider, retrieval time, and adjustment provenance
- Dataset and strategy SHA-256 fingerprints
- Coverage, missing-data, and stale-cache warnings
- Integrity checks for warm-up, trade count, parameter risk, and supplied-data limitations
- No backward-fill from future prices or FX rates

The engine cannot detect look-ahead that a client has already embedded inside a supplied signal.
Caller-supplied inputs are labelled accordingly in provenance and integrity reports.

## Outputs

- Interactive result page with metrics, charts, drawdowns, trades, exposures, seasonality,
  cost waterfall, and what-if controls
- In-chat result application for supported MCP clients (a high-level quick read)
- Adaptive in-chat visual: any chart (bar, line, area, candlestick, scatter) plus stat cards,
  composed by the AI and rendered in the Helvetic frame
- PDF tear sheet, Excel workbook, CSV, and JSON exports
- Plain-language explanations and metric definitions
- Self-verifying audit bundle with raw series, formulas, hashes, provenance, and assumptions
- Explicit result sharing through revocable public permalinks

## Due diligence and record-keeping

- Track-record reconciliation: re-simulate a stated set of rules and compare the claimed return,
  CAGR, Sharpe, and drawdown against a clean re-run, field by field, with a tolerance verdict
- Duplicate-strategy detection: fingerprint a run by the trades it actually makes and flag
  near-duplicates among your saved runs by trade overlap
- Research journal: log a trade you took with a rationale and strategy tag, close it for an
  automatic P&L, return, and R-multiple, and review a per-strategy scorecard. Record-keeping
  only, with no execution and no advice

## Current structural gaps

- Historical option chains, implied-volatility surfaces, quotes, spreads, and contract liquidity
  require a licensed provider; current option research is synthetic
- Deep built-in intraday history is not licensed; bring supplied OHLCV for longer studies
- Historical constituents, delistings, and survivorship-clean universes are incomplete on
  community data
- Fundamentals such as earnings, balance-sheet ratios, and estimates are not currently provided
- Discretionary chart interpretation such as Elliott Wave or hand-selected drawing anchors is
  outside the deterministic rule engine
- Trade execution and broker connectivity are deliberately out of scope

For provider-specific details, see [Data and Limitations](DATA_AND_LIMITATIONS.md).
