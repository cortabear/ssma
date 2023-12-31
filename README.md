# Super Simple Moving Average
This repo serves as a template strategy. A fully loaded moving average trading stratgey written in [Pine Script](#) v.5 for [TradingView](#).  
  
```ps
//@version=5
strategy("Simple Moving Average Strategy", overlay=true)

// Define strategy parameters
length = input(20, "Moving Average Length")

// Calculate moving average
sma = ta.sma(close, length)

// Entry conditions
enterLong = crossover(close, sma)
enterShort = crossunder(close, sma)

// Exit conditions
exitLong = crossunder(close, sma)
exitShort = crossover(close, sma)

// Execute trades
if (enterLong)
    strategy.entry("Long", strategy.long)
if (enterShort)
    strategy.entry("Short", strategy.short)

if (exitLong)
    strategy.close("Long")
if (exitShort)
    strategy.close("Short")
```
