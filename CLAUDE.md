# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build/Execution Commands
- TradingView scripts (*.ps) are loaded directly into TradingView platform
- No linting/testing commands available for PineScript

## Code Style Guidelines

### Formatting
- Use @version=5 directive at the top of each file
- Include description/title comments with script purpose
- Group code into logical sections with comment headers (e.g., //--- SECTION NAME ---)
- Maintain consistent 4-space indentation
- arrays should be one line
### Imports
- Import libraries using: import JoePieczynski/MyReusableFunctions/2 as libName
- Use exported functions from libraries with libName.functionName() syntax

### Variable/Function Naming
- Use camelCase for variables and functions
- Prefix boolean variables with 'is' (e.g., isMarketHours)
- Use descriptive names that indicate purpose

### Documentation
- Document functions with parameter descriptions using // @param comments
- Document return values with // @returns comments
- Add brief explanations for complex calculations

### Types and Variables
- Declare variables with appropriate types (int, float, string, bool)
- Use 'var' keyword for persistent variables that maintain state between bars
- Initialize calculation variables with appropriate default values

### Time Handling
- Use the timeLib functions for consistent timezone handling
- Prefer library functions for market session detection

### Plot/Line/Label Management
- Create UI elements once using 'var' and update properties on each bar
- Group related visual elements together
- Use consistent color schemes for related indicators
- trigger logic is all on one line