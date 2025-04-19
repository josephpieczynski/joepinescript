# JoePineScript: TradingView Indicators Collection

A comprehensive collection of TradingView indicators written in PineScript v5 for technical analysis, market structure visualization, and advanced trading strategies.

## Overview

This repository contains custom indicators designed for market analysis and trading decisions, focusing on:
- Technical analysis (moving averages, ATR, VWAP variants)
- Market structure visualization
- Multi-symbol correlation analysis
- Time-based session management
- Advanced visualization techniques for pivot points and breakouts

## Version Information

All indicators use PineScript v5 with consistent coding practices:
- `@version=5` directive in each script
- Organized code sections with clear comments
- Consistent variable naming using camelCase
- Optimized for performance with reusable functions

Recent updates (as of April 2025):
- Added several new indicators (Anchored VWAP, Market Structure, Mega TICKS)
- Renamed and fixed MyReusableFunctions library
- Optimized Moving Average Labels for better performance
- Enhanced documentation across all scripts

## Indicators

### Anchored VWAP (`Anchored VWAP.ps`)
- Creates VWAP lines anchored to pivot high/low points
- Features configurable appearance (colors, line widths)
- Includes signal-based conditional display for pivot high/low VWAPs
- Plots crossover/crossunder signals for potential trade entries
- Uses incremental calculations for performance optimization

### Candle Confluence, ATR & Q-Levels (`Candle Confluence, ATR & Q-Levels.ps`)
- Imports custom time library for market session detection
- Analyzes multi-symbol correlation with TICK index
- Visualizes ATR (Average True Range) with threshold-based indicators
- Displays relative volume as percentage on chart
- Includes Q-Levels from external file for key price levels
- Identifies potential top/bottom patterns with smart box visualization

### Correlations (`Correlations.ps`)
- Tracks currency correlations with configurable symbols
- Features correlation-based background color changes
- Includes Rate of Change (ROC) calculations for divergence detection
- Visualizes bull/bear percentage metrics in realtime
- Identifies trend days based on correlation metrics
- Contains special signals for Opening Range Breakout (ORB) patterns

### Market Structure (`Market Structure.ps`)
- Multi-timeframe structure analysis (configurable TF1, TF2, TF3)
- Visualizes higher highs (HH), lower highs (LH), lower lows (LL), higher lows (HL)
- Identifies breakouts and change of trend signals
- Provides Fibonacci retracement levels (0.618) for potential trade entries
- Includes strategies for different market scenarios (ORB, 5DMA, EOD breakouts)
- Advanced hunting wick detection for potential reversal patterns

### Mega TICKS (`Mega TICKS.ps`)
- Weighted TICK index calculations using precise coefficients for major tech stocks
- Features adjustable MA periods for signal generation
- Includes ATR-based candle coloring for volatility visualization
- Tracks volume and percentage change across major tech stocks (AAPL, MSFT, GOOG, AMZN, META, etc.)
- Identifies pivot points in TICK data for direction changes
- Provides custom weighted averages for market breadth analysis

### Moving Average Labels (`Moving Average Labels.ps`)
- Displays multiple timeframe moving averages (daily, weekly, monthly)
- Shows various VWAP calculations (D, W, M, Q, YTD)
- Visualizes previous day and current day high/low levels
- Includes Bollinger Bands visualization
- Integrates with Bookmap levels through conversion calculations
- Optimized with persistent lines/labels and consolidated helper functions
- Efficiently batches security() calls to minimize API requests
- Uses caching techniques for improved performance

### Multi-symbol correlation (`Multi-symbol correlation.ps`)
- Dual timeframe analysis with configurable symbols 
- Calculates correlations across 8 different instruments simultaneously
- Features weighted divergence histogram for combined signal strength
- Includes normalized signal line for trend direction
- Works with customizable lower/higher timeframes
- Supports both cash market hours and extended trading

### Trading Hours (`Trading Hours.ps`)
- Highlights trading sessions with customizable time ranges
- Features US, European sessions and lunch period identification
- Includes real-time market dashboard with correlated instruments
- Detects and displays daily/weekly breakouts (PDH/PDL/PWH/PWL)
- Shows percent change calculations across multiple instruments
- Monitors correlations between risk assets (HYG/IEI ratio)

## Library

### MyReusableFunctions (`MyReusableFunctions.ps`)
Core library providing reusable functions for other scripts:

#### Trend Direction Functions
- `CurrentSymbolTrendDirection`: Detects trend using pivot points
- `OtherSymbolSmallTrendDirection`: Analyzes smaller trends on alternate symbols
- `OtherSymbolLargeTrendDirection`: Analyzes larger trends with wider pivots

#### Time Management
- `isInCustomTimeRange`: Time range checker using America/Los_Angeles timezone
- `getTimeConditions`: Pre-computes common market time conditions:
  - Market hours (6:30-13:00)
  - Pre-market (0:00-6:30)
  - Market open/close
  - London open
  - Overnight hours

## Dependencies and Common Patterns

### Library Imports
Most indicators import the MyReusableFunctions library:
```pine
import JoePieczynski/MyReusableFunctions/2 as timeLib
```

### Time Conditions
Scripts consistently use time conditions from the library:
```pine
timeConditions = timeLib.getTimeConditions()
```

### Performance Optimizations
- Batch security() calls to reduce API requests
- Use persistent objects (var keyword) for lines/labels 
- Implement helper functions for repetitive tasks
- Cache frequently used calculations

### Future Optimization Opportunities
- **Anchored VWAP**: Cache historical VWAP calculations in arrays; reduce line redraws
- **Candle Confluence/ATR**: Consolidate security() calls; pre-compute common conditions
- **Moving Average Labels**: Batch security() calls; create unified helper functions
- **Multi-symbol**: Cache time checks; use vector operations for histogram calculations
- **Mega TICKS**: Combine security() calls for stock data; use persistent variables
- **Market Structure**: Add timeframe validation helpers; consolidate pivot calculations
- **Correlations**: Batch security() calls; pre-calculate time conditions once per bar
- **Trading Hours**: Cache time range checks; consolidate breakout function calls

## Usage

1. Each script can be copied directly into TradingView's Pine Editor
2. Add the MyReusableFunctions library first (required by most scripts)
3. Configure indicator parameters through the settings panel
4. Indicators are designed primarily for US markets but can be adapted

## Common Configuration Options

Most indicators include these configuration options:
- Symbol selection for correlation or VWAP calculations
- Color settings for visual elements
- Timeframe selections for multi-timeframe analysis
- Toggle switches to enable/disable specific features
- Threshold values for signals and alerts