# Changelog

Notable changes to the public Helvetic Research service. This is a product changelog for the
hosted engine, not a source-code history. Dates are when a capability went live.

## 2026-09

- **Research journal** (new tool): log a trade you actually took with a rationale and a strategy
  tag, close it for an automatic P&L, return, and R-multiple, and review a per-strategy scorecard
  (win rate, expectancy, profit factor). Record-keeping only, with no execution and no advice.
- **Track-record reconciliation** (new tool): re-simulate a stated set of rules and reconcile the
  claimed return, CAGR, Sharpe, and drawdown against a clean re-run, field by field.
- **Duplicate-strategy detection** (new tool): fingerprint a run by the trades it actually makes
  and flag near-duplicates among your saved runs.
- **Deeper robustness on every result**: trade-order permutation testing (edge vs sequencing
  luck), benchmark-regime Sharpe decomposition (which regimes carry the edge), a fee-cushion
  ratio, System Quality Number with per-trade MAE/MFE, and a correlation-regime read for
  multi-asset books.
- **Composable portfolio constraints**: per-name caps and floors and per-group exposure caps on
  the optimiser.
- The MCP surface now exposes **88 research tools**.

## 2026-08

- Public result permalinks with an auto-generated social card, served from the edge with no
  database load on anonymous views.
- A 12-component Research Grade reframed around strength of evidence and a "try to break it"
  challenge set.
- Independent, from-scratch verification of the core calculations; full return-quality metric
  parity (payoff, tail, recovery, gain-to-pain, Ulcer Performance Index, Common Sense Ratio, CPC).

## Earlier

- In-chat interactive result delivery through MCP Apps, presigned data exports, and a
  self-verifying audit bundle.
- Frequency-correct metrics and annualisation, provenance, and integrity controls across the
  backtest, portfolio, custom-signal, and custom-OHLCV engines.

For the full current capability set, see [CAPABILITIES.md](CAPABILITIES.md).
