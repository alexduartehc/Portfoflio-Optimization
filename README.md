# Portfolio Optimization – Five Asset Sharpe Ratio Maximization

This project implements a simple yet powerful **portfolio optimization** algorithm that determines the optimal percentage allocation across five diverse assets to **maximize the portfolio's Sharpe Ratio**. It uses historical market data from Yahoo Finance to model returns and risk, and SciPy’s optimization tools to find the best allocation.

## Assets Included
- **SPY** – S&P 500 ETF (US large-cap equities)
- **BND** – US Bond Index ETF
- **GLD** – Gold ETF (commodity exposure)
- **QQQ** – NASDAQ-100 ETF (tech-heavy equities)
- **VTI** – Total US Stock Market ETF

This combination provides a diversified portfolio with exposure to equities, bonds, and commodities.

---

## Methodology

1. **Data Collection**  
   - Uses the [`yfinance`](https://pypi.org/project/yfinance/) library to fetch the last **5 years** (although the number of years can be easily changed) of daily adjusted close prices for each asset.
   - Adjusted prices include dividends and stock splits for accurate return calculations.

2. **Return Calculation**  
   - Computes **logarithmic daily returns** and annualizes the covariance matrix.

3. **Risk/Return Metrics**  
   - **Expected portfolio return**  
   - **Portfolio volatility (standard deviation)**  
   - **Sharpe ratio** (with an assumed 2% annual risk-free rate)

         **Sharpe Ratio Formula**
         
         $$
         \text{Sharpe Ratio} = \frac{E[R_p] - R_f}{\sigma_p}
         $$
         
         Where:
         
         - \( E[R_p] \) = Expected portfolio return  
         - \( R_f \) = Risk-free rate (assumed 2%)  
         - \( \sigma_p \) = Portfolio volatility

4. **Optimization**  
   - Objective: **Maximize Sharpe Ratio**  
   - Implemented by minimizing its negative using **SciPy’s `SLSQP`** method with constraints:
     - All weights sum to 1
     - Each weight is between 0% and 50%

---

## Installation

Clone this repository and install dependencies:

```bash
git clone https://github.com/yourusername/portfolio-optimization.git
cd portfolio-optimization
pip install -r requirements.txt

