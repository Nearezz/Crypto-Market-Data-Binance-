# 📊 Crypto Market Data (Binance)

This repository contains historical OHLCV data for major cryptocurrency pairs against **USDT**, sourced from Binance.  
Data spans from **January 2021 to August 2025**, across multiple timeframes for flexible quantitative analysis and strategy development.

---

## Dataset Structure

Data is organized into subfolders by timeframe:

- **1m_Data/** → 1-minute candles  
- **3m_Data/** → 3-minute candles  
- **5m_Data/** → 5-minute candles  
- **15m_Data/** → 15-minute candles  
- **1h_Data/** → 1-hour candles  
- **4h_Data/** → 4-hour candles  

Each folder contains CSV files for each trading pair.

---

## Available Trading Pairs

Currently included:

- **BTC/USDT** (Bitcoin)  
- **ETH/USDT** (Ethereum)  
- **DOGE/USDT** (Dogecoin)  
- **XRP/USDT** (Ripple)  
- **AVAX/USDT** (Avalanche)  
- **SOL/USDT** (Solana)  
- **LTC/USDT** (Litecoin)  

---

## File Format

Each `.csv` file has the following structure:

| timestamp          | open   | high   | low    | close  | volume    |
|--------------------|--------|--------|--------|--------|-----------|
| 2021-01-01 00:00   | 29300  | 29500  | 29200  | 29450  | 120.45    |
| 2021-01-01 01:00   | 29450  | 29600  | 29350  | 29580  | 98.32     |

- **timestamp** → UTC datetime of the candle  
- **open, high, low, close** → OHLC prices in USDT  
- **volume** → Trading volume in the interval  

---

## Use Cases

- Time series forecasting  
- Technical indicator computation (RSI, EMA, MACD, Bollinger Bands, etc.)  
- Backtesting algorithmic strategies  
- Portfolio and risk management simulations  
- Machine learning for price prediction & clustering  

---

## Notes

- Data is **raw from Binance API**.  
- Missing candles may occur due to API or exchange downtime.  
- Large files (several MBs each) → recommended to use efficient libraries (`pandas`, `polars`, `dask`) for processing.  

---

## Example Usage (Python)

```python
import pandas as pd

# Load ETH 1h data
df = pd.read_csv("1h_Data/ETH_USDT_1h.csv", parse_dates=["timestamp"])

# Inspect
print(df.head())

# Compute 50-period SMA
df["SMA50"] = df["close"].rolling(window=50).mean()
