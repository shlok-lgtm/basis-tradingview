# AGENTS.md — basis-tradingview

This is a SPOKE project. It does NOT connect to the Basis hub database or import from Deploy-Guide.

## Rules

1. Pine Script files (.pine) are the deliverables. They run inside TradingView, not on our infrastructure.
2. Pine Script v5 cannot make HTTP requests. All data comes from TradingView's built-in feeds.
3. The indicator is a PROXY — it approximates Basis scores, not replicates them.
4. Always include a link to the full Basis scores in the info table.
5. Use the same grade thresholds as the real SII (defined in Deploy-Guide/app/scoring.py).
6. Do not hardcode stablecoin lists. The indicator works on any chart — the user chooses what to analyze.

## Architecture

This repo contains Pine Script indicators that run entirely inside TradingView.
They are renderers in the Basis V6 architecture — they consume the concept of
Basis scores and present a proxy version in the TradingView UI.

Hub API: https://basis-deploy-guide.replit.app
GitHub: github.com/shlok-lgtm
