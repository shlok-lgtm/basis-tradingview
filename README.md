# Basis Protocol — TradingView Indicators

TradingView Pine Script indicators for [Basis Protocol](https://basisprotocol.xyz) risk surfaces.

## SII Proxy Indicator

A TradingView indicator that approximates the Basis Stablecoin Integrity Index (SII) using TradingView's built-in price and volume data.

**Important:** This is a proxy, not the full SII. The real SII uses 102 components across 11 categories including reserve quality, attestation recency, holder distribution, smart contract risk, and more. This proxy captures peg stability and liquidity — roughly 55% of the full methodology.

For full 102-component scores: [basisprotocol.xyz](https://basisprotocol.xyz)

### How to install

1. Open TradingView and navigate to any stablecoin chart (USDCUSD, USDTUSD, DAIUSD, etc.)
2. Click "Indicators" at the top of the chart
3. Click "Pine Editor" tab at the bottom
4. Delete any existing code in the editor
5. Copy and paste the entire contents of `sii_proxy.pine`
6. Click "Add to Chart"

### What it shows

- **Score (0-100):** Higher is better. Combines peg stability (60%) and volume health (40%) with a volatility penalty.
- **Grade (A+ to F):** Same grading scale as the full Basis SII.
- **Color coding:** Green (A), yellow-green (B), yellow (C), orange (D), red (F).
- **Info table:** Top-right overlay showing current score, grade, and link to full Basis scores.

### Grade thresholds

| Grade | Score |
|-------|-------|
| A+ | 90-100 |
| A | 85-89 |
| A- | 80-84 |
| B+ | 75-79 |
| B | 70-74 |
| B- | 65-69 |
| C+ | 60-64 |
| C | 55-59 |
| C- | 50-54 |
| D | 45-49 |
| F | 0-44 |

### Built-in alerts

- **SII Below C:** Triggers when proxy score drops below 60
- **SII Below D:** Triggers when proxy score drops below 45

### Works on

Any stablecoin pair pegged to $1.00: USDCUSD, USDTUSD, DAIUSD, FRAXUSD, FDUSD, TUSD, PYUSD, and exchange-specific pairs (USDCUSDT, etc.).

### Limitations

This proxy captures approximately 55% of the full SII methodology:
- **Included:** Peg deviation, volume health, price volatility
- **Not included:** Reserve quality, attestation recency, holder distribution, smart contract risk, oracle integrity, governance, network risk, mint/burn dynamics

## About Basis Protocol

Basis Protocol provides 17 primitives for building risk infrastructure on-chain. The Stablecoin Integrity Index (SII) is the first risk surface — a standardized, deterministic score measuring stablecoin operational integrity.

- **API:** https://basisprotocol.xyz/api/scores
- **MCP Server:** `npx @basis-protocol/mcp-server`
- **GitHub:** github.com/shlok-lgtm

## Future indicators

- PSI Proxy (Protocol Solvency — approximates DeFi protocol health)
- CQI Overlay (Collateral Quality — composites SII × PSI)
