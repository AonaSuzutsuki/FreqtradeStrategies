# ClassicGridTradingStrategy Backtest Summary

## Scope

- Backtest window: 2026-03-22 00:00:00 to 2026-04-22 00:00:00
- Pair: BTC/USDT:USDT
- Trading mode: Isolated Futures
- Max open trades: 1
- Starting balance: 1,000.000 USDT
- Final balance: 1,080.201 USDT
- Absolute profit: 80.201 USDT
- Total profit: 8.02%
- Closed trades: 8
- Win rate: 100.00%
- Left-open trade in report: 1 (closed by backtest force_exit at the end)

## Headline Readout

- Freqtrade reported max drawdown: 0.00% on a closed-trade balance basis, but this should not be interpreted as "no real drawdown" during live position holding.
- Reconstructed operational drawdown: -45.716 USDT (-4.48%) at trade 2.
- Worst reconstructed trough equity: 973.845 USDT versus a prior peak of 1,019.561 USDT.
- Worst reconstructed drawdown trade window: 2026-03-23 11:45:00 to 2026-04-07 23:30:00.

## Actual Operational Drawdown

Freqtrade's default summary reports drawdown from realized balance only, which stays at 0.00% here because every closed trade was profitable.

Important: the backtest result shows `0.00%` drawdown only in the accounting sense used by Freqtrade's closed-trade summary. In actual operation, the strategy did carry floating losses while price was falling and grid entries were accumulating, so there was a real effective drawdown before exits were completed.

The table below reconstructs underwater equity from open lots by replaying each trade's order history and then valuing the still-open lots at that trade's recorded `min_rate`. This is intended to show the practical drawdown while the position was still running, not only after the sell was completed.

Method notes:

- The reconstruction uses the order list stored in the backtest JSON.
- Partial exits are matched against lots using the same highest-lower-grid rule as the strategy.
- The trough is valued at each trade's recorded `min_rate`, so this is a mark-to-market underwater estimate rather than the closed-trade balance shown by Freqtrade's summary row.
- Funding-fee timing is not exposed per event in the result JSON, so the intratrade underwater reconstruction is price-driven and does not attempt to timestamp funding accrual inside the trade.

| Trade | Open | Close | Min Rate | Open Lots At Trough | Peak Equity | Trough Equity | Drawdown | Drawdown % | Exit Reason |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 2026-03-22 00:15:00 | 2026-03-23 11:30:00 | 67,310.0 | 2 | 1,000.000 | 996.880 | -3.120 | -0.31% | partial_exit |
| 2 | 2026-03-23 11:45:00 | 2026-04-07 23:30:00 | 64,936.8 | 8 | 1,019.561 | 973.845 | -45.716 | -4.48% | grid_final_exit |
| 3 | 2026-04-07 23:45:00 | 2026-04-10 14:30:00 | 70,428.2 | 2 | 1,052.594 | 1,048.782 | -3.812 | -0.36% | partial_exit |
| 4 | 2026-04-10 14:45:00 | 2026-04-13 23:00:00 | 70,455.8 | 3 | 1,058.632 | 1,049.993 | -8.638 | -0.82% | partial_exit |
| 5 | 2026-04-13 23:15:00 | 2026-04-17 09:30:00 | 73,218.0 | 3 | 1,067.368 | 1,061.142 | -6.226 | -0.58% | partial_exit |
| 6 | 2026-04-17 09:45:00 | 2026-04-17 13:15:00 | 75,043.4 | 2 | 1,072.300 | 1,070.919 | -1.380 | -0.13% | partial_exit |
| 7 | 2026-04-17 13:30:00 | 2026-04-17 14:45:00 | 76,052.4 | 1 | 1,075.638 | 1,074.829 | -0.809 | -0.08% | partial_exit |
| 8 | 2026-04-17 15:00:00 | 2026-04-22 00:00:00 | 73,670.0 | 6 | 1,077.804 | 1,054.490 | -23.314 | -2.16% | force_exit |

## Daily Profit Breakdown

Profit percentages below are calculated against the balance at the start of each day bucket.

| Date | Start Balance | Profit | Profit % | End Balance | Closed Trades |
| --- | --- | --- | --- | --- | --- |
| 23/03/2026 | 1,000.000 | 10.541 | 1.05% | 1,010.541 | 1 |
| 24/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 25/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 26/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 27/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 28/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 29/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 30/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 31/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 01/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 02/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 03/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 04/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 05/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 06/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 07/04/2026 | 1,010.541 | 42.053 | 4.16% | 1,052.594 | 1 |
| 08/04/2026 | 1,052.594 | 0.000 | 0.00% | 1,052.594 | 0 |
| 09/04/2026 | 1,052.594 | 0.000 | 0.00% | 1,052.594 | 0 |
| 10/04/2026 | 1,052.594 | 3.118 | 0.30% | 1,055.712 | 1 |
| 11/04/2026 | 1,055.712 | 0.000 | 0.00% | 1,055.712 | 0 |
| 12/04/2026 | 1,055.712 | 0.000 | 0.00% | 1,055.712 | 0 |
| 13/04/2026 | 1,055.712 | 8.496 | 0.80% | 1,064.207 | 1 |
| 14/04/2026 | 1,064.207 | 0.000 | 0.00% | 1,064.207 | 0 |
| 15/04/2026 | 1,064.207 | 0.000 | 0.00% | 1,064.207 | 0 |
| 16/04/2026 | 1,064.207 | 0.000 | 0.00% | 1,064.207 | 0 |
| 17/04/2026 | 1,064.207 | 13.597 | 1.28% | 1,077.804 | 3 |
| 18/04/2026 | 1,077.804 | 0.000 | 0.00% | 1,077.804 | 0 |
| 19/04/2026 | 1,077.804 | 0.000 | 0.00% | 1,077.804 | 0 |
| 20/04/2026 | 1,077.804 | 0.000 | 0.00% | 1,077.804 | 0 |
| 21/04/2026 | 1,077.804 | 0.000 | 0.00% | 1,077.804 | 0 |
| 22/04/2026 | 1,077.804 | 2.397 | 0.22% | 1,080.201 | 1 |

## Weekly Profit Breakdown

Profit percentages below are calculated against the balance at the start of each week bucket reported by Freqtrade.

| Week Bucket | Start Balance | Profit | Profit % | End Balance | Closed Trades |
| --- | --- | --- | --- | --- | --- |
| 23/03/2026 | 1,000.000 | 10.541 | 1.05% | 1,010.541 | 1 |
| 30/03/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 06/04/2026 | 1,010.541 | 0.000 | 0.00% | 1,010.541 | 0 |
| 13/04/2026 | 1,010.541 | 53.666 | 5.31% | 1,064.207 | 3 |
| 20/04/2026 | 1,064.207 | 13.597 | 1.28% | 1,077.804 | 3 |
| 27/04/2026 | 1,077.804 | 2.397 | 0.22% | 1,080.201 | 1 |

## Exit Reason Summary

| Exit Reason | Trades | Profit | Profit % | Avg Profit % |
| --- | --- | --- | --- | --- |
| grid_final_exit | 1 | 42.053 | 4.21% | 5.37% |
| partial_exit | 6 | 35.751 | 3.58% | 5.40% |
| force_exit | 1 | 2.397 | 0.24% | 0.74% |

## Notes

- The `0.00%` drawdown shown in the raw backtest output is a realized-balance result, not evidence that the strategy avoided underwater periods. During sell-off phases, open grid lots held floating losses and therefore had a real effective drawdown.
- The largest underwater period occurred during the second trade, where realized-balance drawdown was still reported as 0.00% by Freqtrade but the reconstructed live equity dipped to roughly -4.48% from the prior equity peak.
- Weekly performance was concentrated in the week bucket ending `13/04/2026`, which contributed `53.666 USDT` or `5.31%` on the bucket's starting balance.
- The final trade was left open at the end of the timerange and appears in the report as a `force_exit` with `2.397 USDT` profit.

## Included Raw Freqtrade Output

The raw `output.txt` content is embedded below for reference.

```text
Result for strategy ClassicGridTradingStrategy
                                                  BACKTESTING REPORT                                                  
┏━━━━━━━━━━━━━━━┳━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┓
┃          Pair ┃ Trades ┃ Avg Profit % ┃ Tot Profit USDT ┃ Tot Profit % ┃     Avg Duration ┃  Win  Draw  Loss  Win% ┃
┡━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━┩
│ BTC/USDT:USDT │      8 │         4.82 │          80.201 │         8.02 │ 3 days, 20:45:00 │    8     0     0   100 │
│         TOTAL │      8 │         4.82 │          80.201 │         8.02 │ 3 days, 20:45:00 │    8     0     0   100 │
└───────────────┴────────┴──────────────┴─────────────────┴──────────────┴──────────────────┴────────────────────────┘
                                               LEFT OPEN TRADES REPORT                                               
┏━━━━━━━━━━━━━━━┳━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┓
┃          Pair ┃ Trades ┃ Avg Profit % ┃ Tot Profit USDT ┃ Tot Profit % ┃    Avg Duration ┃  Win  Draw  Loss  Win% ┃
┡━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━┩
│ BTC/USDT:USDT │      1 │         0.74 │           2.397 │         0.24 │ 4 days, 9:00:00 │    1     0     0   100 │
│         TOTAL │      1 │         0.74 │           2.397 │         0.24 │ 4 days, 9:00:00 │    1     0     0   100 │
└───────────────┴────────┴──────────────┴─────────────────┴──────────────┴─────────────────┴────────────────────────┘
                                                  ENTER TAG STATS                                                  
┏━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ Enter Tag ┃ Entries ┃ Avg Profit % ┃ Tot Profit USDT ┃ Tot Profit % ┃     Avg Duration ┃  Win  Draw  Loss  Win% ┃
┡━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━┩
│     OTHER │       8 │         4.82 │          80.201 │         8.02 │ 3 days, 20:45:00 │    8     0     0   100 │
│     TOTAL │       8 │         4.82 │          80.201 │         8.02 │ 3 days, 20:45:00 │    8     0     0   100 │
└───────────┴─────────┴──────────────┴─────────────────┴──────────────┴──────────────────┴────────────────────────┘
                                                   EXIT REASON STATS                                                    
┏━━━━━━━━━━━━━━━━━┳━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┓
┃     Exit Reason ┃ Exits ┃ Avg Profit % ┃ Tot Profit USDT ┃ Tot Profit % ┃      Avg Duration ┃  Win  Draw  Loss  Win% ┃
┡━━━━━━━━━━━━━━━━━╇━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━┩
│ grid_final_exit │     1 │         5.37 │          42.053 │         4.21 │ 15 days, 11:45:00 │    1     0     0   100 │
│    partial_exit │     6 │          5.4 │          35.751 │         3.58 │   1 day, 20:12:00 │    6     0     0   100 │
│      force_exit │     1 │         0.74 │           2.397 │         0.24 │   4 days, 9:00:00 │    1     0     0   100 │
│           TOTAL │     8 │         4.82 │          80.201 │         8.02 │  3 days, 20:45:00 │    8     0     0   100 │
└─────────────────┴───────┴──────────────┴─────────────────┴──────────────┴───────────────────┴────────────────────────┘
                                                           MIXED TAG STATS                                                           
┏━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ Enter Tag ┃     Exit Reason ┃ Trades ┃ Avg Profit % ┃ Tot Profit USDT ┃ Tot Profit % ┃      Avg Duration ┃  Win  Draw  Loss  Win% ┃
┡━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━┩
│           │ grid_final_exit │      1 │         5.37 │          42.053 │         4.21 │ 15 days, 11:45:00 │    1     0     0   100 │
│           │    partial_exit │      6 │          5.4 │          35.751 │         3.58 │   1 day, 20:12:00 │    6     0     0   100 │
│           │      force_exit │      1 │         0.74 │           2.397 │         0.24 │   4 days, 9:00:00 │    1     0     0   100 │
│     TOTAL │                 │      8 │         4.82 │          80.201 │         8.02 │  3 days, 20:45:00 │    8     0     0   100 │
└───────────┴─────────────────┴────────┴──────────────┴─────────────────┴──────────────┴───────────────────┴────────────────────────┘
                          SUMMARY METRICS                          
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ Metric                        ┃ Value                           ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ Backtesting from              │ 2026-03-22 00:00:00             │
│ Backtesting to                │ 2026-04-22 00:00:00             │
│ Trading Mode                  │ Isolated Futures                │
│ Max open trades               │ 1                               │
│                               │                                 │
│ Total/Daily Avg Trades        │ 8 / 0.26                        │
│ Starting balance              │ 1000 USDT                       │
│ Final balance                 │ 1080.201 USDT                   │
│ Absolute profit               │ 80.201 USDT                     │
│ Total profit %                │ 8.02%                           │
│ CAGR %                        │ 148.02%                         │
│ Sortino                       │ -100.00                         │
│ Sharpe                        │ 3.96                            │
│ Calmar                        │ -100.00                         │
│ SQN                           │ 2.13                            │
│ Profit factor                 │ 0.00                            │
│ Expectancy (Ratio)            │ 10.03 (100.00)                  │
│ Avg. daily profit             │ 2.587 USDT                      │
│ Avg. stake amount             │ 56.187 USDT                     │
│ Total trade volume            │ 10622.14 USDT                   │
│                               │                                 │
│ Best Pair                     │ BTC/USDT:USDT 8.02%             │
│ Worst Pair                    │ BTC/USDT:USDT 8.02%             │
│ Best trade                    │ BTC/USDT:USDT 9.11%             │
│ Worst trade                   │ BTC/USDT:USDT 0.74%             │
│ Best day                      │ 42.053 USDT                     │
│ Worst day                     │ 0 USDT                          │
│ Days win/draw/lose            │ 6 / 25 / 0                      │
│ Min/Max/Avg. Duration Winners │ 0d 01:15 / 15d 11:45 / 3d 20:45 │
│ Min/Max/Avg. Duration Losers  │ 0d 00:00 / 0d 00:00 / 0d 00:00  │
│ Max Consecutive Wins / Loss   │ 8 / 0                           │
│ Rejected Entry signals        │ 0                               │
│ Entry/Exit Timeouts           │ 0 / 0                           │
│                               │                                 │
│ Min balance                   │ 1010.541 USDT                   │
│ Max balance                   │ 1080.201 USDT                   │
│ Max % of account underwater   │ 0.00%                           │
│ Absolute drawdown             │ 0 USDT (0.00%)                  │
│ Drawdown duration             │ 0 days 00:00:00                 │
│ Profit at drawdown start      │ 0 USDT                          │
│ Profit at drawdown end        │ 0 USDT                          │
│ Drawdown start                │ 2026-03-23 11:30:00             │
│ Drawdown end                  │ 2026-03-23 11:30:00             │
│ Market change                 │ 11.25%                          │
└───────────────────────────────┴─────────────────────────────────┘

Backtested 2026-03-22 00:00:00 -> 2026-04-22 00:00:00 | Max open trades : 1
                                                                 STRATEGY SUMMARY                                                                  
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓
┃                   Strategy ┃ Trades ┃ Avg Profit % ┃ Tot Profit USDT ┃ Tot Profit % ┃     Avg Duration ┃  Win  Draw  Loss  Win% ┃      Drawdown ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩
│ ClassicGridTradingStrategy │      8 │         4.82 │          80.201 │         8.02 │ 3 days, 20:45:00 │    8     0     0   100 │ 0 USDT  0.00% │
└────────────────────────────┴────────┴──────────────┴─────────────────┴──────────────┴──────────────────┴────────────────────────┴───────────────┘
```
