# Data Coverage and Limitations

Helvetic Research records provenance and quality information for every completed run, but no data
source is perfect. This document states the current provider paths and the limitations researchers
should consider before relying on a result.

## Current data paths

| Data | Primary | Fallback / reference | Notes |
|---|---|---|---|
| Equities and ETFs | Yahoo Finance | Tiingo when configured | Tiingo is daily EOD and mainly covers US securities |
| Crypto | Yahoo Finance | Coinbase Exchange | Coinbase fallback is daily in this product |
| FX | Yahoo Finance | ECB reference series where applicable | Cross-currency portfolio conversion is supported |
| Macro and rates | FRED | ECB Data Portal | Authoritative public reference adapters |
| Intraday OHLCV | Yahoo Finance | None | Timestamp-preserving; provider lookback limits apply |

Yahoo Finance is community/unlicensed convenience data. Tiingo and Coinbase provide resilience,
not a licensed point-in-time institutional dataset.

## Intraday intervals

`get_price_history` supports `1m`, `2m`, `5m`, `15m`, `30m`, `60m`, `90m`, and `1h` bars.
It also accepts `2h`, `3h`, and `4h`, resampled from `1h` bars.

| Interval | Practical provider lookback |
|---|---:|
| `1m` | About 7 calendar days |
| `2m`–`90m` | About 60 calendar days; 59 days is safer at the boundary |
| `1h` | About 730 calendar days |
| `2h`–`4h` | About 730 calendar days, resampled from `1h` |

Intraday timestamps are preserved. Tiingo and Coinbase fallbacks do not extend intraday coverage.
For longer or licensed studies, provide external OHLCV from a broker, TradingView, or another
entitled feed through the custom-data research tools.

## Known limitations

Depending on the instrument and date range, community-source histories may not fully capture:

- Historical index constituents and survivorship bias
- Delisted securities and symbol changes
- Corporate actions and adjustment differences
- Futures rolls and contract-specific liquidity
- Point-in-time fundamentals
- Historical option chains and implied-volatility surfaces
- Bid/ask quotes, spreads, depth, and market microstructure

Index tickers can also have weaker fallback coverage. An ETF proxy such as `SPY` may be more
appropriate than `^GSPC` when resilience matters, provided the proxy choice is disclosed.

## What the service records

Completed runs include:

- Provider and retrieval timestamp
- Price-adjustment method
- Requested-versus-effective coverage
- Missing-data and stale-cache warnings
- Provider fallback and disagreement warnings
- Dataset fingerprint and data-quality assessment
- Machine-readable integrity checks

When live providers are unavailable, a complete stale cached history may be returned with an
explicit warning. Degraded data must remain visible; it is never silently relabelled as clean.

## Research use

Community data can be appropriate for prototyping, education, and preliminary research. Material
financial decisions require independent replication, appropriate licensed data, and review of the
specific instrument's corporate actions, liquidity, and point-in-time universe.

Past or simulated results do not indicate future performance. Helvetic Research provides research
and analytical tooling, not investment advice.
