# Stock and News Headline Analysis

## Overview

This project aims to merge stock data and news headlines to analyze the impact of news on stock prices. It processes stock data from CSV files stored in a ZIP archive and cleans news headlines data to align both datasets on date and ticker symbol. The analysis focuses on industries with multiple stocks, such as Biotechnology and Medical Devices, to explore potential correlations between stock price changes and news events.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Setup](#setup)
- [Data Preparation](#data-preparation)
- [Script Details](#script-details)
- [Usage](#usage)
- [Results](#results)


## Features

- Extracts and processes stock data from multiple CSV files within a ZIP archive.
- Cleans and preprocesses news headlines data to ensure accurate date formats and ticker symbols.
- Merges stock and news data on matching dates and ticker symbols.
- Filters and visualizes data for industries with multiple stocks to identify trends and correlations.

## Setup

### Prerequisites

Ensure you have the following installed:

- Python 3.x
- Required libraries:
  - pandas
  - matplotlib
  - scikit-learn

### Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/stock-news-analysis.git
   cd stock-news-analysis
   ```

2. Install the required dependencies:

   ```bash
   pip install pandas matplotlib scikit-learn
   ```

3. Ensure `stocks.zip` (containing CSV files for stock data) and `news_headlines.csv` (for news data) are placed in the project's root directory.

## Data Preparation

### 1. Extracting Stock Data

The function `list_files_in_zip()` extracts stock data CSVs from `stocks.zip`. Each CSV represents a different stock ticker, and these files are loaded into a DataFrame, concatenated, and relevant columns are processed for analysis.

### 2. Cleaning News Headlines Data

The news headlines are read from `news_headlines.csv`. Key cleaning steps include:

- Splitting the combined 'date' and 'time' into separate columns.
- Converting 'date' fields into `datetime` objects for accurate merging.
- Dropping invalid dates or entries that do not match stock data criteria.

## Script Details

### Code Walkthrough

1. **Extracting Stock Files:**

   ```python
   def list_files_in_zip(zip_path):
       with zipfile.ZipFile(zip_path, 'r') as z:
           return z.namelist()
   ```

   This function lists all files within the ZIP archive (`stocks.zip`).

2. **Loading Stock Data:**

   ```python
   dfs = []
   for file_name in stock_files:
       df = pd.read_csv(f'./stocks/{file_name}')
       dfs.append(df)
   all_stocks = pd.concat(dfs)
   ```

   Stock data from each file is loaded and concatenated into a single DataFrame.

3. **Cleaning News Data:**

   ```python
   news = pd.read_csv('news_headlines.csv')
   news[['date', 'time']] = news['date'].str.split(expand=True)
   news['date'] = pd.to_datetime(news['date'], format='%Y-%m-%d', errors='coerce')
   ```

   News data is cleaned by splitting dates and times, and ensuring date formats are consistent.

4. **Merging Datasets:**

   ```python
   merged_df = all_stocks.merge(news, how='inner', left_on=['ticker', 'date'], right_on=['ticker', 'date'])
   ```

   The stock and news data are merged on matching ticker symbols and dates, filtering for relevant data.

5. **Filtering by Industry:**

   ```python
   industry_group = merged_df.groupby('Industry').filter(lambda x: x['ticker'].nunique() > 10)
   ```

   The data is filtered to focus on industries with more than 10 stocks, allowing for more robust analysis.

6. **Visualization:**

   ```python
   import matplotlib.pyplot as plt

   industry_group[industry_group['Industry'] == 'Medical Devices'].plot(x='date', y='Adj Close Diff')
   plt.title('Stock Price Changes in Medical Devices Industry')
   plt.xlabel('Date')
   plt.ylabel('Adj Close Difference')
   plt.show()
   ```

   Visualization is performed to show trends in stock price changes in the Medical Devices industry.

## Usage

1. Run the script to process and analyze the data:

   ```bash
   python main.py
   ```

2. Check the visualizations generated to interpret how news headlines correlate with stock price movements.

## Results

The analysis identifies patterns in stock price changes in relation to news events, particularly within industries with multiple stocks. This can provide insights into how specific news may affect market behavior in targeted sectors.

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.
