# SAI Candles — Minimal SPA

This is a very simple single‑page app that visualizes candlesticks pulled from your UDF backend and can optionally embed the official TradingView Advanced Chart widget.

- Lightweight Charts view is fed by your backend: `https://sai-candles.testnet-2.nibiru.fi/candles/udf` (proxied on Vercel via `vercel.json`).
- TradingView Widget view shows TradingView’s own data for supported tickers.

## Local development
```
npm install
npm run start
# open http://localhost:5173
```

## Deploy on Vercel
This is a static site. You can deploy with zero build.

1. Push this repo to GitHub (see below).
2. In Vercel, create a new project from this repo.
3. Framework preset: Other.
4. Build command: (leave empty)
5. Output directory: `.` (project root)

`vercel.json` already rewrites `/candles/udf/*` to your backend, so the browser calls your domain and Vercel proxies to the backend (avoids CORS).

## GitHub remote
This project is configured for the repository:

```
git@github.com:onikonychev/candles.git
```

If you cloned from elsewhere and want to set the remote:
```
git init -b main
git add -A
git commit -m "chore: initial import of SAI Candles SPA"
git remote add origin git@github.com:onikonychev/candles.git
# first push
git push -u origin main
```

## Environment
- Node 18+
- Static server used for local dev: `npx serve`

## Notes
- Resolutions supported: 1m, 5m, 15m, 1h, 4h, 1d (mapped to UDF `1,5,15,60,240,D`).
- Auto refresh options: Off/5s/15s/30s/60s.
- Symbol list is fetched via `/candles/udf/search` if available, else falls back to [BTC, ETH, ATOM, OSMO, NIBI].
- To use the full TradingView Charting Library with your custom UDF datafeed, you need a separate license from TradingView.
