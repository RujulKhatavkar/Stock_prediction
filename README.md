# Stock Market and News Headline Analysis

## Overview

This project aims to analyze stock market data in conjunction with news headlines to explore potential correlations between market sentiment and stock price movements. The analysis involves extracting and processing stock market data and news headlines, performing sentiment analysis, and visualizing the results.

## Table of Contents

- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Methods](#methods)
- [Results](#results)
- [Data](#data)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)

## Project Structure

```
stock-sentiment-analysis/
├── extracted_files/          # Folder where extracted stock CSV files are stored
├── stocks.zip                # Zip file containing individual stock CSV files
├── news_headlines.csv        # CSV file containing news headlines
├── news_data.csv             # CSV file with industry information
├── stock_data.csv            # Aggregated stock data CSV file
├── training_data.csv         # Final dataset with merged and processed data
├── analysis.ipynb            # Jupyter notebook with analysis and visualization
├── requirements.txt          # List of Python packages required
└── README.md                 # This README file
```

## Getting Started

To get started with this project, you'll need to clone the repository and install the required dependencies.

### Clone the Repository

```bash
git clone https://github.com/yourusername/stock-sentiment-analysis.git
cd stock-sentiment-analysis
```

### Install Dependencies

Ensure you have `pip` installed, then run:

```bash
pip install -r requirements.txt
```

## Usage

### Data Extraction and Processing

1. **Extract Stock Data**: Extract CSV files for the specified stocks from the `stocks.zip` file.
2. **Process News Headlines**: Clean and preprocess the news headlines dataset.
3. **Merge Data**: Combine the stock data and news headlines data, aligning on date and ticker symbol.
4. **Perform Sentiment Analysis**: Analyze the sentiment of the news headlines using VADER sentiment analysis.
5. **Save Processed Data**: Save the final merged dataset with sentiment scores to `training_data.csv`.

### Running the Analysis

You can use the provided Jupyter notebook (`analysis.ipynb`) to perform exploratory data analysis and visualization. Open the notebook and run the cells to generate insights and visualizations.

## Methods

1. **Data Extraction**:
   - **Stock Data**: Extracted from zip files containing historical stock prices in CSV format.
   - **News Headlines**: Gathered from various news sources and stored in `news_headlines.csv`.

2. **Data Processing**:
   - **Cleaning**: Removed duplicates, handled missing values, and standardized date formats.
   - **Merging**: Combined stock price data and news headlines based on date and ticker symbol.
   - **Feature Engineering**: Created additional features like moving averages and volatility from stock price data.

3. **Sentiment Analysis**:
   - **Tool Used**: VADER sentiment analysis tool was employed to analyze the sentiment of news headlines.
   - **Sentiment Scoring**: Each headline was scored for positive, negative, and neutral sentiment.

4. **Data Integration**:
   - Combined sentiment scores with stock price data to create a comprehensive dataset (`training_data.csv`).
   - Analyzed correlations between sentiment scores and stock price movements.

5. **Visualization and Analysis**:
   - Used `matplotlib` and `seaborn` for visualizing stock price trends, sentiment trends, and correlation heatmaps.
   - Applied statistical methods to determine the relationship between sentiment and stock price changes.

## Results

- **Sentiment and Stock Prices**: Preliminary results indicate a moderate correlation between sentiment scores and stock price movements. Positive sentiment often correlates with price increases, while negative sentiment correlates with price decreases.
- **Visualizations**:
  - **Stock Price Trends**: Line charts showing stock price movements over time.
  - **Sentiment Trends**: Plots showing the variation in sentiment scores over time.
  - **Correlation Heatmaps**: Visualizations indicating the strength of the relationship between sentiment and various stock price metrics.

- **Insights**:
  - **Positive Sentiment**: Generally associated with upward price trends.
  - **Negative Sentiment**: Often precedes downward price trends.
  - **Volatility Analysis**: Higher sentiment variability tends to correspond with increased stock price volatility.

## Data

- **Stock Data**: CSV files inside `stocks.zip`, containing historical stock prices for various companies.
- **News Headlines**: `news_headlines.csv`, containing news headlines with associated dates and stock tickers.
- **Industry Data**: `news_data.csv`, containing ticker and industry information.
- **Processed Data**: `training_data.csv`, the final dataset with merged stock data, sentiment scores, and additional features.

## Dependencies

The following Python packages are required:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `vaderSentiment`
- `zipfile36` (for handling zip files)
- `openpyxl` (if working with Excel files)

You can install them using `pip`:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn vaderSentiment zipfile36 openpyxl
```

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes. For significant changes, please open an issue first to discuss the proposed changes.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to adjust the Methods and Results sections based on the specifics of your analysis and findings.
