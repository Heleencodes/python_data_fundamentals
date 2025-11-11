# Stock Data Extraction and Visualization

This project focuses on collecting, cleaning, and visualizing financial data for two well-known companies: **Tesla (TSLA)** and **GameStop (GME)**. The assignment was completed as part of the IBM Data Science specialization.

## ✅ Project Overview
- Extract historical stock price data using **yfinance**
- Scrape quarterly revenue using **requests** and **BeautifulSoup**
- Clean financial data in **pandas** (remove symbols, null values, formatting)
- Visualize closing stock prices and combined price-vs-revenue charts using **matplotlib**

## ✅ Technologies Used
- Python
- yfinance
- pandas
- matplotlib
- requests
- BeautifulSoup (bs4)

## ✅ Files Included
| File | Description |
|------|-------------|
| `tesla_data_extraction.py` | Code to extract Tesla price data |
| `gme_data_extraction.py` | Code to extract GameStop price data |
| `revenue_scraper.py` | Web scraping of quarterly revenue tables |
| `notebook.ipynb` (optional) | All analysis in Jupyter Notebook form |
| `screenshots/` | Screenshots for Coursera submission |
| `stock_project_report.pdf` | Summary report of the entire project |

## ✅ Example Code (Tesla Stock Data)
```python
import yfinance as yf

tsla = yf.Ticker("TSLA")
tesla_data = tsla.history(period="max")
tesla_data.reset_index(inplace=True)
tesla_data.head()

import requests
import pandas as pd
from bs4 import BeautifulSoup

url = "https://cf-courses-data.../revenue.htm"
html_data = requests.get(url).text
tables = pd.read_html(html_data)
tesla_revenue = tables[1]
tesla_revenue.columns = ["Date", "Revenue"]
tesla_revenue["Revenue"] = tesla_revenue["Revenue"].str.replace(",|\\$","",regex=True)
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue["Revenue"] != ""]
tesla_revenue.tail()

import matplotlib.pyplot as plt

plt.figure(figsize=(12,5))
plt.plot(tesla_data["Date"], tesla_data["Close"])
plt.title("Tesla Stock Price")
plt.xlabel("Date")
plt.ylabel("Close Price (USD)")
plt.grid(True)
plt.show()

✅ Final Result

Tesla and GameStop price history successfully extracted

Quarterly revenue scraped and cleaned

Graphs produced for price trends and combined price-vs-revenue

Project submitted with screenshots and PDF report

✅ Author

Heleen — Data Analyst in training
GitHub: https://github.com/Heleencodes
