# Stock Analyzer Dashboard

Generates a single-page technical analysis dashboard for any stock, ETF or index
from live market data.

![GOOG dashboard](examples/GOOG_dashboard-06-06-25.png)

## Running it

You need Python 3.8+ and a free [Twelve Data](https://twelvedata.com/) API key
(800 calls/day on the free tier).

```bash
git clone https://github.com/Boakye-20/stock_analyzer.git
cd stock_analyzer
pip install -r requirements.txt
```

Set your API key in `stock_analyzer.py`:

```python
API_KEY = 'your_api_key_here'
```

Then run it with a ticker:

```bash
python stock_analyzer.py AAPL
python stock_analyzer.py MSFT --period 1y
python stock_analyzer.py GOOGL --period 6mo --save reports/google.png
```

| Option | Values | Default |
| --- | --- | --- |
| `ticker` | Any Twelve Data symbol (stocks, ETFs, indices) | required |
| `--period` | `1mo`, `3mo`, `6mo`, `1y`, `2y`, `5y` | `2y` |
| `--save` | Path to write the PNG to | shows on screen |

## What's on the dashboard

Price action with moving averages · Bollinger Bands · colour-coded volume · RSI ·
MACD · returns distribution · a key metrics table.

![MSFT dashboard](examples/MSFT_dashboard-06-06-25.png)

More samples in [`examples/`](examples/): AAPL, BAC, BLK, GOOG, GOOGL, GS, JPM,
MA, MS, MSFT, SPY, V, WFC.

## The indicators

| Indicator | Settings |
| --- | --- |
| Moving averages | 20, 50 and 200 periods |
| Bollinger Bands | 2 standard deviations |
| RSI | 14 periods |
| MACD | 12, 26, 9 |

## The metrics

| Metric | What it tells you |
| --- | --- |
| Total return | Performance over the selected period |
| Annualised return | Year-on-year growth rate |
| Volatility | Annualised standard deviation |
| Sharpe ratio | Return adjusted for risk |
| Maximum drawdown | Largest peak-to-trough fall |
| VaR (95%) | Value at Risk at 95% confidence |

## Project layout

```
stock_analyzer.py   The whole application
examples/           Sample dashboards
requirements.txt    Dependencies
```

Built with matplotlib, pandas, numpy, scipy and the `twelvedata` client.


## Licence

MIT. Author: Paul Kwarteng ([@Boakye-20](https://github.com/Boakye-20) ·
[LinkedIn](https://www.linkedin.com/in/paul-kwarteng-22a71b196/)).
