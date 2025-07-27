# SPY Credit Spread Backtesting Strategy

## Description

This repository contains a Python-based backtesting framework designed to evaluate the performance of a short volatility credit spread strategy on the SPY (S&P 500 ETF) using historical price data. The strategy leverages a simplified Black-Scholes model for theoretical options pricing and aims to capture premium from selling out-of-the-money options. The backtest covers the period from 2020-01-01 to 2023-12-31.

## Features

- **Historical Data Acquisition**: Automatically downloads historical daily price data for SPY using `yfinance`.
- **Historical Volatility (HV) Calculation**: Computes annualized historical volatility over a configurable lookback period.
- **Simplified Options Pricing**: Utilizes a custom Black-Scholes model to estimate theoretical option prices and Greeks (Delta, Gamma, Vega, Theta, Rho) based on market conditions and historical volatility.
- **Credit Spread Strategy Implementation**: Simulates the entry and exit of short call and put credit spreads based on predefined parameters (IV/HV ratio, Delta range, DTE).
- **Dynamic Position Sizing**: Adjusts the number of spreads opened per trade based on a percentage of the current portfolio value and the maximum potential loss per spread.
- **Trade Management**: Implements profit target and stop-loss rules for early exit of positions.
- **Comprehensive Performance Metrics**: Calculates and displays key backtest statistics including Total Net PnL, Win Rate, Average PnL per trade, Max Win/Loss, CAGR, Max Drawdown, and Sharpe Ratio.
- **Visualizations**: Generates plots of portfolio value over time and daily drawdown to visually assess performance.

## Strategy Parameters

The strategy's behavior is controlled by the following key parameters, which can be adjusted within the `backtest_short_volatility_credit_spread_enhanced` function:

- `symbol`: The ticker symbol of the underlying asset (e.g., `"SPY"`).
- `start_date`, `end_date`: The period for which the backtest will run.
- `initial_capital`: Starting capital for the backtest.
- `risk_free_rate`: Annualized risk-free interest rate used in the Black-Scholes model.
- `hv_lookback_days`: Number of days to look back for historical volatility calculation.
- `iv_to_hv_ratio_entry`: Multiplier for historical volatility to determine the theoretical implied volatility for trade entry.
- `target_delta_min`, `target_delta_max`: The acceptable range for the absolute delta of the short option leg.
- `spread_width`: The difference between the strike prices of the short and long options in the spread (e.g., $5.00 or $10.00).
- `max_portfolio_risk_per_trade_pct`: The maximum percentage of the current portfolio value to risk on a single trade.
- `commission_per_contract`: Commission charged per option contract.
- `target_dte_min`, `target_dte_max`: The minimum and maximum days to expiration (DTE) for options considered for trade entry.
- `profit_target_pct`: Percentage of the maximum credit received at which to close the trade for profit.
- `stop_loss_multiple`: Multiplier of the initial credit received at which to close the trade for a loss.
- `min_profit_buffer_per_spread`: Minimum desired profit per spread after accounting for all round-trip commissions.

---

## Requirements

Install dependencies using pip:
```bash
pip install yfinance pandas numpy scipy matplotlib
```
---

## Backtest Performance

| Metric                   | Value        |
|--------------------------|--------------|
| Total Closed Trades      | 897          |
| Successful Trades        | 659          |
| Losing Trades            | 238          |
| Win Rate                 | 73.47%       |
| Total Net PnL            | $131,382.47  |
| Avg Net PnL per Trade    | $-194.95     |
| Max Win (Single Trade)   | $353.67      |
| Max Loss (Single Trade)  | $-1851.59    |

---

## Portfolio Performance

| Metric                   | Value         |
|--------------------------|---------------|
| Initial Capital          | $100,000.00   |
| Final Portfolio Value    | $231,382.47   |
| CAGR                     | 23.40%        |
| Max Drawdown             | -19.02%       |
| Sharpe Ratio             | 1.47          |

---
## Results Visualization

The plot below shows the portfolio value growth over the backtest period (2020-01-01 to 2023-12-31):

<img width="1012" height="505" alt="Untitled" src="https://github.com/user-attachments/assets/009f86e1-1f4c-447f-afa5-e967a8c881a1" />


## License

This project is open-source and available under the [MIT License](LICENSE).
