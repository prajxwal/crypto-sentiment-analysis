# CRYPTO Sentiment Analysis

## Overview

This project analyzes the relationship between market sentiment and trading performance using historical trading data and a sentiment index (Fear & Greed Index). It leverages advanced data processing, statistical analysis, and machine learning to extract actionable trading insights and strategies.

## Project Structure

```
.
├── data/
│   ├── historical_data.csv         # Raw trading data (large file)
│   ├── fear_greed_index.csv        # Market sentiment index (Fear & Greed)
├── notebooks/
│   └── analysis.ipynb              # Main analysis notebook
├── reports/
│   └── (analysis outputs: plots, CSVs, dashboards)
├── env/
│   └── (Python virtual environment, Python 3.13.4)
```

## Data Sources

### 1. `data/historical_data.csv`
- **Description:** Contains detailed trading records.
- **Key columns (inferred):**
  - `Timestamp IST`: Trade timestamp (format: `%d-%m-%Y %H:%M`)
  - `Account`: Trader/account identifier
  - `Closed PnL`: Profit and loss for the trade
  - `Size USD`: Trade size in USD
  - `Direction`: Trade direction (e.g., Buy/Sell)
  - (Additional columns may exist)

### 2. `data/fear_greed_index.csv`
- **Description:** Daily market sentiment index.
- **Columns:**
  - `timestamp`: Unix timestamp
  - `value`: Sentiment score (0-100)
  - `classification`: Sentiment label (e.g., Extreme Fear, Fear, Neutral, Greed, Extreme Greed)
  - `date`: Date (YYYY-MM-DD)

## Main Analysis Notebook

### `notebooks/analysis.ipynb`

#### Features:
- **Data Preprocessing:** Cleans and merges trading and sentiment data, adds engineered features (hour, day, session, PnL per USD, win/loss, etc.).
- **Statistical Analysis:** 
  - Sentiment transition matrices
  - Performance by sentiment and trader type
  - Time decay and volume analysis
  - Risk-reward and streak analysis
- **Machine Learning:**
  - Random Forest models to identify key features influencing PnL and win rate
  - Feature importance and partial dependence plots
- **Strategy Generation:**
  - Actionable strategies based on sentiment extremes, optimal trading hours, and elite trader behavior
  - Backtesting and performance comparison
- **Reporting:**
  - Generates summary dashboards and exports key results to the `reports/` directory

#### Outputs:
- `reports/sentiment_analysis_dashboard.png`: Visual dashboard of key findings
- `reports/sentiment_insights_summary.csv`: Summary of sentiment-based performance
- `data/processed_merged_data.csv`: Cleaned and merged dataset

## How to Run

1. **Set up the environment:**
   - Python 3.13.4 (see `env/pyvenv.cfg`)
   - Recommended: Use the provided virtual environment (`env/`) or create a new one.

2. **Install dependencies:**
   - Install required packages (see below for a typical list).

3. **Run the analysis:**
   - Open `notebooks/analysis.ipynb` in Jupyter.
   - Run all cells to execute the full analysis pipeline.
   - Outputs will be saved in the `reports/` and `data/` directories.

## How to Run the Jupyter Notebook

1. **Activate your virtual environment (if using one):**
   - On Windows:
     ```sh
     .\env\Scripts\activate
     ```
   - On macOS/Linux:
     ```sh
     source env/bin/activate
     ```

2. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

3. **Launch Jupyter Notebook:**
   ```sh
   jupyter notebook
   ```
   This will open the Jupyter interface in your browser. Navigate to `notebooks/analysis.ipynb` and run the cells to execute the analysis.

## Example Dependencies

Add a `requirements.txt` with (at minimum):

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```

## Key Insights (from the notebook)

- **Market sentiment significantly impacts trading performance.**
- **Extreme sentiments (fear/greed) present unique opportunities.**
- **Elite traders show consistent, superior patterns.**
- **Time-of-day and sentiment interactions are crucial.**
- **Risk management must adapt to sentiment conditions.**

## Outputs

- **Dashboards and plots**: Visual summaries of findings.
- **CSV summaries**: Key metrics and strategy results.
- **Processed data**: For further analysis or modeling.

## Notes

- The `env/` directory is a Python virtual environment (not for code editing).
- The `reports/` directory will be populated after running the analysis.
- The trading data file is large; ensure sufficient memory for processing.
