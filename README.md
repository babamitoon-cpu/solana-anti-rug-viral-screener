# Solana Radar PRO V4 — Detailed Token Analysis

Mobile-friendly static dashboard for Solana token market discovery via public DEX Screener endpoints. Signal-only; no wallet connection, private keys, or trading.

## V4 additions
- Each scanned token row is followed by a detailed analysis panel.
- Displays available market cap/FDV, liquidity, 1h volume, 5m price change, 1h buys/sells and estimated buy/sell transaction ratio.
- Adds transparent heuristic observations for high volume relative to liquidity, sell-heavy transaction counts, and sharp 5-minute price changes.
- Adds direct links to DEX Screener and Solscan and a copy contract-address action.
- Holder count, top-10 concentration, bundle/sniper, first-20 buyers, mint/freeze authority, liquidity security, dev reputation, X/TikTok trend remain UNKNOWN / NOT SCORED unless a reliable data source is integrated.

## Deploy
Upload `index.html` to the root of the existing GitHub repository and commit the change. Keep `README.md` if desired. GitHub Pages settings should use branch `main` and folder `/ (root)`.

## Limitations
This is still a frontend MVP. It discovers recent token profiles, not every newly created Pump.fun token. It scans only when the page is open and the user presses Scan. Risk/security/social fields are not fully integrated and must not be treated as passed. The market score is a heuristic, not a prediction or guarantee.
