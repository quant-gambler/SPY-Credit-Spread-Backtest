# SPY Credit Spread Backtesting Strategy

This repository provides a Python-based framework for backtesting a short volatility credit spread strategy on the SPY ETF (S&P 500). The strategy is designed to capitalize on situations where implied volatility (IV) is elevated relative to historical volatility (HV), allowing for premium capture through the sale of out-of-the-money options.

The backtest is implemented using a simplified Black-Scholes model for theoretical pricing and Greek calculations. It includes configurable parameters, risk controls, trade management logic, and visual performance analysis.

---

## Project Overview

- Strategy: Short Call and Put Credit Spreads
- Underlying: SPY (S&P 500 ETF)
- Timeframe: 2020-01-01 to 2023-12-31
- Framework: Python, with no broker APIs required

---

## Features

### Strategy Logic

- Entry trigger based on IV to HV ratio
- Credit spread structure (sell one OTM option, buy further OTM for protection)
- Option pricing via custom Black-Scholes implementation
- Delta-based strike selection for risk control
- Fixed-width spreads and configurable days to expiry (DTE)
- Early exit via profit target or stop-loss rules

### Performance Metrics

- Total Net PnL
- Number of Trades
- Win Rate and Loss Rate
- Average PnL per Trade
- Maximum Gain and Loss
- Cumulative Equity Curve
- Max Drawdown
- Sharpe Ratio (if enhanced tracking is enabled)

### Visualizations

- Cumulative PnL over time
- Daily drawdown curve

---

## Configuration Parameters

| Parameter | Description |
|----------|-------------|
| `symbol` | Ticker of underlying asset (default: "SPY") |
| `start_date`, `end_date` | Backtest period |
| `risk_free_rate` | Annual interest rate for Black-Scholes |
| `hv_lookback_days` | Lookback period for HV calculation |
| `iv_to_hv_ratio_entry` | Entry condition multiplier (e.g., 1.5) |
| `target_delta_min`, `target_delta_max` | Delta range for short strike selection |
| `spread_width` | Distance between short and long strike |
| `max_portfolio_risk_per_trade_pct` | Position sizing control |
| `target_dte_min`, `target_dte_max` | Days to expiry limits |
| `profit_target_pct` | Exit if profit exceeds this threshold |
| `stop_loss_multiple` | Exit if loss exceeds this multiple of credit |
| `min_profit_buffer_per_spread` | Minimum profit after commissions |
| `commission_per_contract` | Round-trip commission applied per contract |

---

## Requirements

Install dependencies using pip:

```bash
pip install yfinance pandas numpy scipy matplotlib
