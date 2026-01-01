# Earnings Trading Dashboard - IV Crush Analysis

This application is a Python-based desktop dashboard designed to help traders analyze the "IV Crush" phenomenon around earnings events. It visualizes stock prices, estimates implied volatility (IV) crush using VIX as a proxy, and calculates the theoretical P/L of an At-The-Money (ATM) Straddle strategy.

## Features

-   **Stock Data Analysis**: Downloads historical price data using `yfinance`.
-   **IV Estimation**: Estimates Implied Volatility (IV) using VIX data as a proxy (since historical option data is not free).
-   **IV Crush Simulation**: Simulates the drop in implied volatility that typically occurs after an earnings announcement.
-   **Option Pricing**: Uses the Black-Scholes model to calculate theoretical option prices (Call, Put, Straddle) before and after earnings.
-   **P/L & Greeks**: Calculates theoretical Profit/Loss (P/L) changes and Option Greeks (Delta, Vega).
-   **Interactive Visualizations**:
    -   Stock Price Chart
    -   Straddle Price Impact Bar Chart
    -   Market Volatility (VIX) Chart
-   **Advanced Statistics**: Displays Breakeven points and Market Implied Moves.
-   **Scrollable UI**: Modern, scrollable interface for easy viewing on any screen size.

## Prerequisites

Ensure you have **Python 3.x** installed. You will need the following Python libraries:

*   `tkinter` (usually included with Python)
*   `pandas`
*   `numpy`
*   `matplotlib`
*   `scipy`
*   `yfinance`

## Installation

1.  **Clone or Download** this repository to your local machine.
2.  **Install Dependencies**:
    Open a terminal or command prompt and run:

    ```bash
    pip install pandas numpy matplotlib scipy yfinance
    ```

## Usage

1.  **Run the Application**:
    Navigate to the project directory in your terminal and execute:

    ```bash
    python app.py
    ```

2.  **Configure Analysis**:
    *   **Ticker**: Enter the stock symbol (e.g., `NVDA`, `AAPL`, `TSLA`).
    *   **Earnings Date**: Enter the historical earnings date you want to analyze (Format: `YYYY-MM-DD`).
    *   **Days to Expiry**: Enter the number of days to expiration for the option contract simulation (default: 30).

3.  **Analyze**:
    *   Click the **Analyze IV Crush** button.
    *   The dashboard will fetch data, perform calculations, and display the results in the metrics and charts below.

## How It Works

1.  **Data Fetching**: The app pulls historical stock prices and VIX data for a 20-day window around the specified earnings date.
2.  **IV Simulation**:
    *   *Pre-Earnings IV* is estimated based on the VIX level prior to the event (plus a markup, as individual stocks typically have higher volatility than the index).
    *   *Post-Earnings IV* is estimated to drop significantly (the "crush").
3.  **Black-Scholes Model**: The app calculates the price of an ATM Straddle (Call + Put) using the pre-earnings stock price/IV and then re-calculates it using the post-earnings stock price/IV.
4.  **Results**: The difference shows how much value the option strategy might lose due to volatility dropping, even if the stock price moves.

## Disclaimer

This tool is for educational and analytical purposes only. It uses theoretical models (Black-Scholes) and estimated volatility data. Real-world option prices are affected by supply/demand, skew, and other market factors not fully captured here. Always do your own due diligence before trading.
