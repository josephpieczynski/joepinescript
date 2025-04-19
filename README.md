# TradingView PineScript Collection

A collection of TradingView indicators and libraries written in PineScript v5 for technical analysis and trading.

## Overview

This repository contains custom TradingView indicators for market analysis, focusing on:
- Moving averages and technical indicators
- Market structure visualization
- Correlation analysis
- Session/time-based visualizations
- VWAP variants
- Reusable trading functions

## Scripts

### Moving Average Labels
Comprehensive indicator that displays key levels, moving averages, and VWAP lines with labels:
- Daily, weekly, and monthly moving averages (5, 20, 50, 100, 200)
- VWAP calculations (daily, weekly, monthly, quarterly, YTD)
- Previous day highs/lows and cash session levels
- Bookmap integration for ES/SPY level conversion
- Session-aware calculations with special handling for pre-market/market hours
- Color-coded breakout detection

### Market Structure
Visualizes market structure using pivot points to identify trends and potential reversal points.

### Anchored VWAP
Displays Volume Weighted Average Price anchored to specific points with customizable parameters.

### Candle Confluence, ATR & Q-Levels
Multi-purpose indicator showing candle patterns, ATR (Average True Range), and quarterly levels.

### Correlations
Calculates and displays correlation between symbols to identify related price movements.

### Multi-symbol Correlation
Extended correlation analysis across multiple symbols with visualization options.

### Trading Hours
Displays trading sessions with configurable backgrounds and time zones:
- Customizable US and European sessions
- Market open/close highlights
- Lunch session identification
- Symbol correlation matrix with breakout detection

## Library: MyReusableFunctions

Core library that provides reusable functions for other scripts:

### Trend Direction Functions
- `CurrentSymbolTrendDirection`: Detects trend direction using pivot points in current timeframe
- `OtherSymbolSmallTrendDirection`: Analyzes smaller trends on alternate symbols and timeframes
- `OtherSymbolLargeTrendDirection`: Analyzes larger trends on alternate symbols and timeframes

### Time Management
- `isInCustomTimeRange`: Checks if current time is within a specified range
- `getTimeConditions`: Pre-computes common market time conditions (market hours, pre-market, etc.)

## Installation

1. Copy the `.ps` file content for the indicator you want to use
2. In TradingView, go to Pine Editor (bottom toolbar)
3. Create a new script and paste the code
4. Save and add to your chart

For the library:
1. Copy the `MyReusableFunctions.ps` content
2. Create a new script in Pine Editor 
3. Paste code and select "Add to Library" (not "Add to Chart")
4. Access the library in other scripts using the import statement:
   ```
   import JoePieczynski/MyReusableFunctions/2 as myLib
   ```

## Performance Notes

- These indicators are optimized for performance considering TradingView's limitations
- Helper functions reduce code duplication and improve maintainability
- Security calls are batched where possible to reduce network overhead
- Visual elements (lines/labels) are created once and reused with updates
- Conditional calculations reduce processing when features aren't needed

## Compatibility

- Requires TradingView with PineScript v5 support
- Tested on various markets including futures, forex, and equities
- Optimized for US equities market timing

## License

MIT

## Contributing

Feel free to submit issues or pull requests for enhancements or bug fixes.