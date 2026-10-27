# Solana Anti-RUG + Viral Trend Screener (signal-only MVP)

Mobile-friendly static dashboard for discovering recent Solana token pairs through the public DEX Screener API. No wallet connection, no private keys, no trade execution.

## Implemented
- Discovery from DEX Screener latest token profiles, then batch-fetches token pairs.
- Filters: market cap >= $50,000, liquidity >= $10,000, pair age <= 60 minutes by default.
- Transparent heuristic score 0–100 (not an AI prediction).
- Unknown risk metrics are shown as `UNKNOWN`.
- Social trend panel explicitly shows X/TikTok as `UNKNOWN` and viral score as `NOT SCORED` until a permitted, reliable data source is connected. No fake social scores are generated.
- **Fail-closed alert policy:** no token can be marked as a verified alert until holder count, bundle holdings, sniper holdings, first-20-buyer holdings, and top-10-holder concentration are all sourced and verified. The MVP deliberately shows 0 verified alerts rather than fabricating those metrics.

## Important data limitation
DEX Screener's public pair endpoints expose market/pair metrics, but not reliable holder count, bundle holdings, sniper holdings, or first-20-buyer ownership. Standard Solana `getTokenLargestAccounts` returns the 20 largest token accounts, not a complete holder count or transaction-history classification. To enable verified alerts, integrate a trusted Solana indexer/analytics provider with:
- token holder count and normalized wallet balances,
- bundle/sniper labels or wallet clustering,
- chronological buyer transactions for first 20 unique buyers,
- top-10 holder concentration with LP/burn/known program accounts handled consistently.

Until that adapter is implemented, these risk fields must remain `UNKNOWN` and must not pass the strict filter. Do not rely on the score alone for trading decisions.

## Run locally
Open `index.html` in a browser with internet access. If browser CORS blocks the API, use a local static server:
```bash
python -m http.server 8080
```
Then visit `http://localhost:8080`.

## Deploy to GitHub Pages
1. Sign in to GitHub and create a new public repository, e.g. `solana-meme-screener`.
2. Upload `index.html` and `README.md` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main`, folder `/ (root)`, then **Save**.
6. Wait for the Pages deployment and open the URL shown on the Pages settings screen (usually `https://YOUR-USERNAME.github.io/solana-meme-screener/`).
7. Open the URL on your phone and tap **Scan sekarang**.

## Notes
- GitHub Pages only hosts the front-end. The browser calls the public API directly, so the dashboard scans only when the page is open and the user taps Scan. It is not a 24/7 server or scheduled alert service.
- Discovery is based on latest token profiles, not a complete feed of every newly created token/pair.
- Public APIs may rate-limit, change schemas, or be blocked by browser CORS. For more robust usage, add a small backend/proxy and a paid or keyed analytics provider. Never put private API keys in public front-end JavaScript or a public repository.
- The heuristic score is intentionally transparent and must not be interpreted as guaranteed predictive performance.


## Viral/social trend status (current MVP)
The dashboard does **not** currently scrape X or TikTok and does not claim to calculate a real viral score. It labels unavailable social inputs `UNKNOWN` and the score `NOT SCORED`. This is intentional: lack of accessible data is not evidence that a token is or is not viral. Public website access, API terms, authentication, rate limits, and platform restrictions must be checked before any automated connector is added.

## Next integrations needed for the full version
1. Pump.fun new-token/migration feed (e.g. a permitted public stream; check provider terms and costs).
2. Solana transaction/indexing source for holder count, creator balance, top-10, first-20 unique buyers, bundle/sniper heuristics.
3. DEX market metrics for market cap, liquidity, age, volume, price and trades.
4. Permitted social-data sources for X and TikTok with timestamped metrics.
5. Backend service for persistent monitoring; GitHub Pages alone cannot keep a scanner running 24/7.

A token is not a verified pass until all required risk gates are known and pass. Viral score and Anti-RUG score are separate; neither guarantees safety.
