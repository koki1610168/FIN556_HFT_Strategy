# Enhanced High Frequency Trading Backtest Analysis

This comprehensive analysis tool processes multiple CSV files containing HFT backtesting results and generates detailed statistics, risk metrics, visualizations, and HTML reports.

## Features

The enhanced analysis includes:

1. **Multi-File Analysis**
   - **Fill Data** (`*_fill.csv`): Trade execution data analysis
   - **Order Data** (`*_order.csv`): Order state and execution analysis
   - **P&L Data** (`*_pnl.csv`): Profit & Loss tracking and risk metrics

2. **Overview Statistics**
   - Total trades, date ranges, trading duration
   - Buy vs Sell distribution
   - Symbol breakdown
   - File-by-file comparison (if multiple files)

3. **Execution Cost Analysis**
   - Total and average execution costs
   - Cost breakdown by symbol and trade direction
   - Cost distribution statistics
   - Cumulative cost tracking

4. **Trade Characteristics**
   - Quantity, price, and trade value statistics
   - Distribution analysis by symbol
   - Trade size patterns
   - Order execution time analysis

5. **P&L Analysis**
   - Cumulative P&L tracking
   - Realized and unrealized P&L calculations
   - P&L change distributions
   - Position tracking by symbol

6. **Risk Metrics**
   - **Sharpe Ratio**: Risk-adjusted return measure
   - **Maximum Drawdown**: Largest peak-to-trough decline
   - **Volatility**: Annualized return volatility
   - **Win Rate**: Percentage of profitable periods
   - **Profit Factor**: Ratio of gross profit to gross loss
   - **Drawdown Analysis**: Average and maximum drawdown metrics

7. **Temporal Pattern Analysis**
   - Trading activity by hour
   - Trading intensity (trades per minute)
   - Time-based patterns
   - Cumulative trade tracking

8. **Order Analysis**
   - Order state distribution (FILLED, PENDING, etc.)
   - Order type analysis (MARKET, LIMIT, etc.)
   - Execution time statistics
   - Fill rate analysis

9. **Comprehensive Visualizations**
   - 16 different charts covering all aspects of the data:
     - P&L over time and drawdown charts
     - Trade distributions and patterns
     - Execution costs and order analysis
     - Risk metrics and performance indicators
     - Temporal patterns and activity analysis
   - Saved as high-resolution PNG file

10. **HTML Report Generation**
    - Professional HTML report with executive summary
    - Detailed statistics tables
    - All metrics organized by category
    - Styled for easy reading and sharing

## Installation

1. Install required Python packages:
```bash
pip install -r requirements.txt
```

Or install individually:
```bash
pip install pandas numpy matplotlib seaborn
```

## Usage

### Automatic CSV Detection (Recommended)

The script automatically finds all CSV files in the specified directory. By default, it looks in `c:\Users\ansh6` for files containing "BACK" in the filename.

Simply run:
```bash
python hft_backtest_analysis_enhanced.py
```

Or on Windows:
```bash
py hft_backtest_analysis_enhanced.py
```

### Manual CSV File Specification

If you want to specify files manually, edit the `main()` function in the script:

```python
csv_files = [
    r'c:\Users\ansh6\BACK_*_fill.csv',
    r'c:\Users\ansh6\BACK_*_order.csv',
    r'c:\Users\ansh6\BACK_*_pnl.csv'
]
```

## Output

The analysis generates:

1. **Console Output**: Detailed statistics printed to the console, including:
   - Executive summary with key metrics
   - Fill data analysis
   - Order data analysis
   - P&L analysis
   - Risk metrics

2. **Visualization File**: `hft_backtest_analysis_enhanced.png`
   - A comprehensive dashboard with 16 charts
   - High-resolution (300 DPI) for printing and presentations
   - Covers all aspects of the backtest analysis

3. **HTML Report**: `hft_backtest_report.html`
   - Professional HTML report with executive summary
   - Detailed statistics in organized tables
   - All metrics categorized for easy navigation
   - Can be opened in any web browser
   - Suitable for sharing with stakeholders

## CSV File Formats

The script expects three types of CSV files:

### Fill Data (`*_fill.csv`)
Required columns:
- `StrategyName`: Name of the trading strategy
- `TradeTime`: Timestamp of the trade
- `Symbol`: Stock symbol (e.g., AAPL, MSFT)
- `Quantity`: Trade quantity (positive for buys, negative for sells)
- `Price`: Execution price
- `ExecutionCost`: Cost of execution
- `LiquidityAction`: Liquidity action type
- `LiquidityCode`: Liquidity code
- Other metadata columns

### Order Data (`*_order.csv`)
Required columns:
- `StrategyName`: Name of the trading strategy
- `EntryTime`: Order entry timestamp
- `LastModTime`: Last modification timestamp
- `State`: Order state (FILLED, PENDING, etc.)
- `Symbol`: Stock symbol
- `Side`: BUY or SELL
- `Type`: Order type (MARKET, LIMIT, etc.)
- `Quantity`: Order quantity
- `FilledQty`: Filled quantity
- `AvgFillPrice`: Average fill price
- `ExecutionCost`: Execution cost
- Other metadata columns

### P&L Data (`*_pnl.csv`)
Required columns:
- `Name`: Strategy name
- `Time`: Timestamp
- `Cumulative PnL`: Cumulative profit and loss

## Example Output

The analysis will display:

### Executive Summary
- Final P&L and Net P&L
- Total trades
- Sharpe Ratio
- Maximum Drawdown
- Win Rate
- Profit Factor

### Detailed Analysis
- Total number of trades
- Date range and duration
- Buy/Sell distribution
- Symbol statistics
- Execution cost breakdowns
- Trading patterns over time
- Risk metrics
- Order execution statistics
- And much more!

## Key Metrics Explained

### Sharpe Ratio
Measures risk-adjusted returns. Higher is better:
- > 1.0: Good
- > 2.0: Very good
- > 3.0: Excellent
- Negative: Poor risk-adjusted performance

### Maximum Drawdown
The largest peak-to-trough decline in P&L. Lower (less negative) is better. Indicates the worst peak-to-valley loss.

### Win Rate
Percentage of periods with positive P&L changes. Higher is generally better, but must be considered with profit factor.

### Profit Factor
Ratio of gross profit to gross loss:
- > 1.0: Profitable (gains exceed losses)
- < 1.0: Unprofitable (losses exceed gains)
- Higher is better

### Volatility
Annualized standard deviation of returns. Measures the variability of returns. Lower volatility with same returns is better.

## Customization

You can modify the script to:
- Change the output directory for visualizations and reports
- Add custom analysis functions
- Modify chart styles and layouts
- Filter data by specific criteria
- Adjust risk metric calculations
- Add additional visualizations

## Troubleshooting

**No CSV files found:**
- Check that CSV files exist in the specified directory
- Verify the file naming pattern matches the filter (contains "BACK")
- Or manually specify file paths in the script

**Import errors:**
- Ensure all required packages are installed: `pip install -r requirements.txt`
- Check Python version (3.7+ recommended)

**Date parsing errors:**
- The script handles mixed date formats automatically
- If issues persist, check that date columns are in a recognizable format

**Memory issues with large files:**
- The script processes files efficiently, but very large datasets may require additional memory
- Consider analyzing files separately if needed
- Close other applications to free up memory

**Visualization errors:**
- Ensure matplotlib backend is properly configured
- On some systems, you may need to set: `matplotlib.use('Agg')`

## File Structure

After running the analysis, you'll have:
```
c:\Users\ansh6\
├── hft_backtest_analysis_enhanced.py    # Main analysis script
├── hft_backtest_analysis_enhanced.png   # Visualization dashboard
├── hft_backtest_report.html             # HTML report
├── requirements.txt                     # Python dependencies
└── README_ANALYSIS.md                   # This file
```

## Performance Notes

- The script efficiently processes large datasets using pandas
- Typical analysis time: 10-30 seconds for ~10,000 trades
- Visualization generation: 5-15 seconds depending on data size
- HTML report generation: < 1 second

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Review the console output for specific error messages
3. Verify CSV file formats match the expected structure
4. Ensure all dependencies are installed correctly
