<p align="center">
  <img src="https://helveticresearch.com/static/brand/helvetic-icon-192.png" alt="Helvetic Research" width="96" />
</p>

# Helvetic Research

**Research-only MCP server that turns your AI chat into a quant research desk.**

Describe a strategy in plain English — your AI (Claude, ChatGPT, Cursor, Codex, …) runs it
on a real backtest engine: walk-forward analysis, Monte Carlo, stress tests, and 85
read-only research tools. Every result ships with data provenance and a self-verifying
audit bundle.

- 🌐 Website: **[helveticresearch.com](https://helveticresearch.com)**
- 🔌 MCP endpoint: `https://helveticresearch.com/mcp` (OAuth, free tier — unlimited history
  on community data sources)
- 📊 See a real sample result: [helveticresearch.com/sample](https://helveticresearch.com/sample)
- 📖 Methodology: [helveticresearch.com/methodology](https://helveticresearch.com/methodology)

## What it is

A hosted [Model Context Protocol](https://modelcontextprotocol.io) server. Your AI is the
interface; Helvetic is the engine. Strategies are expressed as a validated JSON AST — the
AI can't write arbitrary code, which is why results are reproducible and auditable.

## What it is not

Helvetic Research is **research-only**: it places no trades, connects to no brokers, and
provides no investment advice. Nothing it produces is financial, investment, or trading
advice.

## This repository

The hosted service is not open source. This repo carries the public face of the project;
an open-source verifier for Helvetic audit bundles is planned to live here.

---

© Helvetic Research · [Privacy](https://helveticresearch.com/privacy) ·
[Terms](https://helveticresearch.com/terms) ·
[Research disclaimer](https://helveticresearch.com/research-disclaimer)
