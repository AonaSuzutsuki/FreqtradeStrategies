# Freqtrade Strategies

This repository publishes free strategies for [Freqtrade](https://www.freqtrade.io/).

At the moment, the repository includes one public strategy:

- `ClassicGridTrading`

## Current Strategy

### ClassicGridTrading

`ClassicGridTrading` is a classic grid-style long-only strategy for Freqtrade.

The default configuration is designed with `BTC/USD` price levels in mind, but the strategy logic itself is pair-agnostic and can be used with other markets as well.

Main characteristics:

- Long-only grid trading behavior
- No FreqAI dependency
- Tracks each purchased lot separately instead of relying only on the trade-wide average entry price
- Sells lots when price reaches the next grid level and the selected lot is net profitable after fees
- Uses custom position adjustment logic for incremental buys and partial exits

Market notes:

- Default price bands are intended for `BTC/USD`-style price levels
- The strategy can still be applied to other pairs
- For non-`BTC/USD` markets, adjust grid bounds, stop level, grid count, and other risk parameters to match the asset's price range and volatility

Default strategy profile:

- Timeframe: `15m`
- Grid range: `60000` to `80000`
- Stop level: `50000`
- Grid count: `25`
- Leverage: `3x`

The strategy file is located at `Strategies/ClassicGridTrading.py` and exposes the strategy class `ClassicGridTradingStrategy`.


## How To Use

1. Copy `Strategies/ClassicGridTrading.py` into your Freqtrade `user_data/strategies/` directory.
2. Reference the strategy class `ClassicGridTradingStrategy` in your Freqtrade configuration or command line.
3. Review and adjust the grid parameters in the strategy file before running backtests or live trading.

**Important: Always perform a dry run before moving to live mode.**

Example:

```bash
freqtrade trade --strategy ClassicGridTradingStrategy
```

## Live Usage

This strategy is currently used in live trading on `Bitget` with `BTC/USDT:USDT`.

It was also used in the past on `Bitbank` spot with `XRP/JPY`.

Although the strategy was originally written for futures trading, it can also be used on spot markets. When used on spot, leverage settings are effectively ignored.

## Notes

- The strategy is designed to behave closer to a classical grid system than a trade-average-based exit model.
- Freqtrade profit reporting is still based on the full trade average entry, so some partial exits can appear negative in reports even when the targeted lot exit is logically profitable.
- In live trading, displayed profit is also calculated from the average entry price, so even if price reaches the next grid level, the position can still appear negative until the partial exit is actually executed and realized.
- Parameters such as grid bounds, leverage, and minimum per-lot profit threshold can be adjusted directly in the strategy file.

## Disclaimer

This repository is shared for research and educational purposes. Always run your own review, backtests, and risk checks before using any strategy in live markets.
