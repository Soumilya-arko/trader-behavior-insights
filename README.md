# Trader Performance vs Market Sentiment

## Overview
The objective is to analyze how Bitcoin market sentiment (Fear/Greed) influences trader behavior and performance on the Hyperliquid platform.

## Datasets
1. Bitcoin Market Sentiment (Fear/Greed): https://drive.google.com/file/d/1PgQC0tO8XN-wqkNyghWc_-mnrYv_nhSf/view
2. Historical Trader Data (Hyperliquid): https://drive.google.com/file/d/1IAfLZwu6rJzyWKgBToqwSmmVYU6VbjVs/view

## Setup & Execution
1. **Prerequisites:** Python 3.8+, `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.
2. **Installation:** Run `pip install pandas numpy matplotlib seaborn scikit-learn`.
3. **Execution:** Open `trader_analysis.ipynb` in VS Code or Jupyter Notebook and run the cells sequentially from top to bottom. The script will ingest the raw data, clean it, merge it on daily timestamps, and generate all visualizations and clustering models inline.

## Methodology
* **Data Preparation:** Aligned millisecond Unix timestamps to standard daily dates. Calculated daily metrics per trader, including Daily PnL, Win Rate (filtering out 0-PnL entry positions for accuracy), Average Trade Size, and Long/Short Ratios.
* **Analysis:** Merged trader metrics with Bitcoin Fear/Greed index data to evaluate behavioral shifts across different market conditions.
* **Advanced Segmentation (Bonus):** Applied K-Means clustering (unsupervised ML) using `scikit-learn` to group 32 unique traders into three distinct behavioral archetypes based on lifetime trades, average win rate, total PnL, and median trade size.

## Key Insights
1. **The "Fear" Premium:** Average daily profits are unexpectedly highest during "Fear" days ($5,185) compared to "Greed" days ($4,144), driven by higher volatility rather than an increased win rate.
2. **Behavioral Shifts:** In fearful markets, traders execute more frequent but smaller trades (defensive behavior). In greedy markets, trade frequency drops, but median position sizing increases significantly (conviction trading).
3. **Archetype Divergence:** Machine learning clustering revealed three distinct trader archetypes: "The Whales" (High Size/Solid Win Rate), "Algo Snipers" (High Frequency/High Win Rate), and "Retail Casuals" (Low Frequency/Low Win Rate). 

## Strategy Recommendations (Actionable Output)
1. **Risk Mitigation for "Retail Casuals":** Implement a dynamic leverage or position-sizing cap for low-win-rate retail traders during extreme *Greed* days to prevent severe drawdowns driven by market overconfidence.
2. **Volatility Harvesting for "Algo Snipers":** During extreme *Fear* days, incentivize the high-frequency "Algo Snipers" cluster (e.g., via temporary fee rebates) to maximize their trade volume, taking advantage of their statistically proven 78% win rate during high-volatility periods.
