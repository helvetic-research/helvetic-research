# Examples

Copy-paste starting points for Helvetic Research. Nothing here runs locally: Helvetic is a
hosted service that your AI client calls over MCP. These files exist so you can see exactly what
a request looks like and get a useful result on your first try.

- **[prompts.md](prompts.md)**: plain-English research requests you can paste straight into
  Claude, ChatGPT, Cursor, or Codex once you have [connected](https://helveticresearch.com/connect).
- **[strategies/](strategies/)**: ready-to-run structured strategy specifications. Paste one in
  and ask your AI to "run this strategy specification with Helvetic," or use it as a template.

Every result comes back with frequency-correct metrics, robustness diagnostics, provenance, and
a reproducibility fingerprint. Helvetic is research-only: it does not place trades, connect to
brokers, or give investment advice.

## The shape of a good request

A request your AI can run without guessing names four things: an instrument, a date range, the
rule, and the costs. For example:

```text
Backtest SPY from 2005-01-01 to 2026-01-01. Go long when price crosses above its
200-day simple moving average and exit when it crosses below. Apply 10 bps
transaction costs, then show the metrics, a walk-forward test, and an overfitting check.
```

If a request is ambiguous or asks for something unsupported, Helvetic returns its assumptions and
open questions rather than inventing a definition and pretending it ran.
