# Quantitative Analysis with PyNance and TA-Lib

## Overview
This project focuses on performing quantitative analysis on stock price data using PyNance and TA-Lib. The primary tasks include loading and preparing financial data, applying technical indicators, and visualizing the results to gain insights.

## Requirements
- Python 3.x
- pandas
- TA-Lib
- PyNance
- matplotlib

## Installation
First, ensure that you have Python installed. Then, install the required libraries using pip:
```bash
pip install pandas TA-Lib pynance matplotlib



Data Preparation
Load your stock price data into a pandas DataFrame. Ensure your data includes the following columns:

Open

High

Low

Close

Volume

Example:

python
import pandas as pd

# Load your data into a pandas DataFrame
data = pd.read_csv('path_to_your_data.csv')
data.fillna(method='ffill', inplace=True)  # Fill missing values
Technical Indicators
Use TA-Lib to calculate various technical indicators such as Moving Averages, RSI, and MACD.

Example:

python
import talib

# Calculate Moving Averages
data['SMA'] = talib.SMA(data['Close'], timeperiod=30)

# Calculate RSI
data['RSI'] = talib.RSI(data['Close'], timeperiod=14)

# Calculate MACD
data['MACD'], data['MACD_signal'], data['MACD_hist'] = talib.MACD(data['Close'], fastperiod=12, slowperiod=26, signalperiod=9)
Financial Metrics
Use PyNance to fetch and analyze additional financial metrics.

Example:

python
import pynance as pn

# Example of fetching and analyzing financial metrics
financial_data = pn.get_stock_data('AAPL')
Data Visualization
Create visualizations to better understand the data and the impact of different indicators on the stock price.

Example:

python
import matplotlib.pyplot as plt

# Plot Moving Averages
plt.figure(figsize=(14,7))
plt.plot(data['Close'], label='Close Price')
plt.plot(data['SMA'], label='SMA 30')
plt.legend(loc='upper left')
plt.show()

# Plot RSI
plt.figure(figsize=(14,7))
plt.plot(data['RSI'], label='RSI')
plt.legend(loc='upper left')
plt.show()

# Plot MACD
plt.figure(figsize=(14,7))
plt.plot(data['MACD'], label='MACD')
plt.plot(data['MACD_signal'], label='Signal Line')
plt.legend(loc='upper left')
plt.show()
