# Starter prompts

Paste any of these into your connected AI client. Each one stands on its own: a real instrument,
a real date range, the rule in plain English, and the costs. Change the tickers and dates freely.

## Run a strategy

**Trend following (equities)**
```text
Backtest SPY from 2005-01-01 to 2026-01-01. Go long when price crosses above its
200-day simple moving average and exit when it crosses below. Apply 10 bps transaction
costs, then show the key metrics and the equity curve.
```

**Long-term trend (crypto, weekly)**
```text
Backtest BTC-USD from 2018-01-01 to 2026-01-01 on weekly bars. Go long when price crosses
above its 200-week moving average and exit when it crosses below. Show metrics and drawdowns.
```

**Momentum rotation (multi-asset)**
```text
Build a monthly momentum rotation between SPY and TLT from 2005-01-01 to 2026-01-01: each
month hold whichever has the stronger 6-month return. Show metrics, exposure over time, and
the calendar-year returns.
```

**Commodity trend (monthly)**
```text
Backtest gold (GC=F) from 2005-01-01 to 2026-01-01 on monthly bars: go long when price
crosses above its 20-month moving average and exit when it crosses below. Report in USD.
```

## Try to break it

```text
Take the SPY 200-day trend result and try to break it: run a walk-forward out-of-sample
test, a Monte Carlo block bootstrap, an overfitting (CSCV/PBO) check, and a trade-order
permutation test. Then give me the Research Grade and tell me where the edge actually comes from.
```

```text
How sensitive is this strategy to costs and execution lag? Run the transaction-cost and
signal-lag sensitivity analyses and show me the fee cushion before the edge breaks even.
```

## Understand a result

```text
For the last backtest, show me the drawdowns, the trade statistics with MAE/MFE, the
monthly returns table, and a plain-language explanation of what drove the performance.
```

```text
Regress this strategy against SPY: alpha, beta, tracking error, information ratio, and how
the Sharpe decomposes across bear, normal, and bull regimes.
```

## Portfolios

```text
Optimise a portfolio of SPY, TLT, GLD, and QQQ over 2015-01-01 to 2026-01-01: show the
efficient frontier plus the max-Sharpe, minimum-volatility, and risk-parity weights. Cap any
single name at 40%.
```

## Due diligence and record-keeping

```text
A manager claims these rules produced an 18% CAGR and a 1.4 Sharpe from 2010 to 2024.
Re-simulate the rules with Helvetic and reconcile the claimed numbers against a clean re-run,
field by field, and tell me where they diverge.
```

```text
Is this new strategy genuinely different from what I have already saved, or is it a repackage?
Fingerprint it by its trades and check for near-duplicates among my saved runs.
```

```text
Log a trade in my research journal: long 50 SPY at 190 on 2026-01-05, stop at 180, tagged
"trend-200d", because the 200-day trend just turned up. Later: close it at 205 and show my
per-strategy scorecard.
```

Every one of these is research and record-keeping only. Helvetic never places an order.
