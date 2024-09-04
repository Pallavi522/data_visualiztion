# data_visualiztion
# Stock Analysis and Visualization

This project involves analyzing and visualizing stock data using Python. It uses various libraries to load historical stock data, calculate moving averages, visualize price trends, and monitor real-time stock prices.

## Features

- **Load Historical Stock Data:** Retrieve and analyze historical data for stocks using the `yfinance` library.
- **Plot Stock Price Over Time:** Visualize the stock's closing price over time.
- **Candlestick Chart:** Display a candlestick chart for visualizing the stock's price movement.
- **Moving Averages:** Calculate and plot 20-day and 50-day moving averages.
- **Trading Volume:** Visualize trading volume over time.
- **Daily Returns Distribution:** Plot the distribution of daily returns.
- **Correlation Matrix:** Analyze the correlation between daily returns of multiple stocks.
- **Real-Time Stock Price Monitoring:** Fetch and display real-time stock prices.

## Requirements

- Python 3.6 or higher
- pandas
- numpy
- matplotlib
- seaborn
- plotly
- yfinance

## Installation

1. Clone this repository to your local machine.

   ```bash
   git clone https://github.com/your-username/stock-analysis.git
2. Navigate to the project directory.

    ```bash
    cd stock-analysis
3. Create and activate a virtual environment (optional but recommended).

    ```bash
    python -m venv env
    source env/bin/activate  # On Windows, use `env\Scripts\activate`
4. Install the required packages.
    ```bash
    pip install -r requirements.txt
5. Alternatively, you can install the dependencies manually:
    ```bash
    pip install pandas numpy matplotlib seaborn plotly yfinance
Usage
1. Analyzing a Single Stock
Loading and Visualizing Stock Data:

Load data for a specific stock (e.g., Apple Inc.) and visualize the closing price over time:

python

ticker = 'AAPL'
df = yf.download(ticker, start='2020-01-01', end='2023-01-01')
Candlestick Chart:

Display a candlestick chart:

python

fig = make_subplots(rows=1, cols=1, shared_xaxes=True)
candlestick = go.Candlestick(x=df.index, open=df['Open'], high=df['High'], low=df['Low'], close=df['Close'], name='Candlestick')
fig.add_trace(candlestick)
fig.show()
Moving Averages:

Calculate and plot 20-day and 50-day moving averages:

python

df['MA20'] = df['Close'].rolling(window=20).mean()
df['MA50'] = df['Close'].rolling(window=50).mean()
2. Analyzing Multiple Stocks
Download and Analyze Data:

Download closing prices for multiple stocks and calculate daily returns:

python

tickers = ['AAPL', 'MSFT', 'GOOGL']
data = yf.download(tickers, start='2020-01-01', end='2023-01-01')['Close']
returns = data.pct_change()
Correlation Matrix:

Visualize the correlation matrix of daily returns:

python

sns.heatmap(returns.corr(), annot=True, cmap='coolwarm')
plt.show()
3. Real-Time Stock Price Monitoring
Real-Time Stock Price:

Fetch and print the real-time stock price every minute:

python

def get_real_time_price(ticker):
    df = yf.download(ticker, period='1d', interval='1m')
    return df['Close'].iloc[-1]
Example usage:

python

ticker = 'AAPL'
while True:
    price = get_real_time_price(ticker)
    print(f'The current price of {ticker} is {price}')
    time.sleep(60)  # Update every minute
