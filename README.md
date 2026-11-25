# UK equity portfolio analyser

A Jupyter notebook that downloads five years of daily prices for six London-listed shares and works out how each has performed, how they move together, and which mix of them gave the best return for the risk taken.

## What it does

1. Downloads dividend-adjusted prices from Yahoo Finance with `yfinance`, plus the FTSE 100 as a benchmark.
2. Plots the growth of £1,000 in each share against the index.
3. Calculates annual return (CAGR), volatility, Sharpe ratio, beta against the FTSE 100 and maximum drawdown for each share.
4. Draws a correlation heatmap of daily returns.
5. Simulates 10,000 random long-only portfolios.
6. Uses `scipy.optimize` to find the minimum-volatility portfolio, the maximum-Sharpe portfolio and the efficient frontier.

The default basket is Greggs, Lloyds, AstraZeneca, Shell, Unilever and Rightmove. Change the `TICKERS` dictionary to analyse any shares Yahoo Finance covers.

## How to run it

```
pip install -r requirements.txt
jupyter notebook uk_portfolio_analyser.ipynb
```

Then choose Kernel → Restart & Run All.

## Settings

| Setting | Default | Meaning |
| --- | --- | --- |
| `TICKERS` | six FTSE shares | Yahoo tickers and the names to show |
| `BENCHMARK` | `^FTSE` | Index used for beta and the growth chart |
| `START` | 2021-11-01 | First day of data |
| `RISK_FREE` | 4.0% | Annual risk-free rate for the Sharpe ratio (Bank Rate, November 2026) |

## Limitations

The optimiser only knows the past five years, so its weights tend to pile into whichever shares happened to do best. Mean returns are noisy, volatility treats gains and losses alike, and trading costs and tax are ignored. The notebook ends with a short section on these points and some ideas for extending it.

## Author

James Suggitt, BSc Banking and Finance, University of Leeds.
