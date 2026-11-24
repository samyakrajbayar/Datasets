# Crypto Market Snapshot — 750 Coins + 7-Day Hourly Price History

**Subtitle:** Market-cap-ranked snapshot of 750 cryptocurrencies with 31 fundamentals and a 121,405-row hourly price panel for time-series work.

---

## 📖 Description

This is a **two-file** crypto dataset rather than the usual single "top 100 coins" CSV.

**File 1 — `crypto_markets.csv` (750 rows × 31 columns)** is a full fundamental snapshot of the top 750 coins by market cap: price, market cap, fully diluted valuation, 24-hour volume and range, 24-hour price and market-cap change, circulating/total/max supply, all-time high and low prices with dates, ROI since ICO, and two derived metrics:

- `volume_to_market_cap` — turnover/liquidity proxy (high values flag speculative churn)
- `volatility_7d_pct` — standard deviation of hourly returns over the past week, computed from the sparkline

**File 2 — `crypto_7day_price_history.csv` (121,405 rows × 7 columns)** is a tidy long-format panel: 167 hourly price points for each of the top 750 coins, with reconstructed UTC timestamps. That gives you a genuine time-series dataset with cross-sectional breadth — rare in free crypto data.

Both files share `id`, `symbol` and `rank`, so they join cleanly.

## 🧾 Schema highlights

`crypto_markets.csv`: `rank`, `id`, `symbol`, `name`, `current_price_usd`, `market_cap_usd`, `fully_diluted_valuation_usd`, `volume_24h_usd`, `volume_to_market_cap`, `high_24h_usd`, `low_24h_usd`, `intraday_range_pct`, `price_change_24h_usd`, `price_change_pct_24h`, `market_cap_change_pct_24h`, `circulating_supply`, `total_supply`, `max_supply`, `supply_ratio`, `fully_diluted_ratio`, `ath_usd`, `ath_change_pct`, `ath_date`, `atl_usd`, `atl_change_pct`, `atl_date`, `roi_times`, `roi_currency`, `volatility_7d_pct`, `sparkline_points`, `last_updated_utc`

`crypto_7day_price_history.csv`: `rank`, `id`, `symbol`, `name`, `timestamp_utc`, `hours_ago`, `price_usd`

Machine-readable dictionaries: `data_dictionary.csv` and `data_dictionary_price_history.csv`.

## 💡 Ideas for using this data

1. **Cross-sectional factor analysis** — does 7-day volatility predict 24-hour volume or market-cap rank?
2. **Supply-overhang modelling** — compare `supply_ratio` and `fully_diluted_ratio` against price momentum.
3. **Clustering coins** into "large-cap stable", "high-turnover speculative" and "supply-dilution risk" groups.
4. **Time-series EDA** — autocorrelation, realised volatility, and drawdown curves from the hourly panel.
5. **Regression** — predict `ath_change_pct` or `roi_times` from fundamentals (with all the usual survivorship caveats).
6. **Dashboard** — a market-cap treemap with volatility colouring.

## ⚠️ Caveats

- Single point-in-time snapshot: prices move, so cite the `last_updated_utc` values.
- The 7-day panel is reconstructed from CoinGecko's hourly sparkline, so timestamps are aligned to the snapshot hour rather than exchange open/close.
- `roi_*` and `max_supply` are often empty for newer or uncapped tokens.
- Not investment advice; no survivorship-bias correction for delisted coins.

## 🔗 Provenance & licence

- Source: CoinGecko public API (`/coins/markets`), free tier.
- Snapshot: November 2026. 750 coins; 121,405 hourly price observations.
- CoinGecko data is provided for informational purposes; check CoinGecko's attribution requirements before commercial reuse.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
