# 🏗️ Backtrader ATR Stop Loss USDCHF - Repository Structure

## 📂 Directory Tree

```
backtrader-atr-stop-loss-usdchf/
│
├── 📁 data/                              # Market Data Files
│   └── 📄 USDCHF_5m_5Yea.csv           # 🇨🇭 USDCHF 5-minute historical data (5 years)
│
├── 📁 debug/                            # Debug & Logging Files
│   ├── 📄 entry_debug_20250830_123010.log    # Entry signal debug log
│   ├── 📄 entry_debug_20250830_123132.log    # Entry signal debug log
│   ├── 📄 entry_debug_20250830_132754.log    # Entry signal debug log
│   └── 📄 entry_debug_20250830_132908.log    # Entry signal debug log
│
├── 📁 images/                           # Strategy Performance Charts
│   ├── 🖼️ sunrise_osiris.png           # Main strategy performance chart
│   └── 🖼️ sunrise_osiris_long_entrys.png    # LONG entries visualization
│
├── 📁 src/                              # Source Code
│   └── 📁 strategy/                     # Trading Strategy Implementation
│       ├── 📄 sunrise_osiris.py         # 🌅 Main Sunrise Osiris Strategy (USDCHF)
│       └── 📁 temp_reports/             # Local strategy reports
│           ├── 📄 USDCHF_trades_20250830_132754.txt
│           └── 📄 USDCHF_trades_20250830_132908.txt
│
└── 📁 temp_reports/                     # Global Trade Reports
    ├── 📄 USDCHF_trades_20250830_123010.txt    # Detailed trade analysis
    └── 📄 USDCHF_trades_20250830_123132.txt    # Detailed trade analysis
```

---

## 📋 File Descriptions

### 📊 Data Files
- **`USDCHF_5m_5Yea.csv`**: 5-minute OHLCV historical data for USD/CHF currency pair covering approximately 5 years of trading history

### 🚀 Strategy Files
- **`sunrise_osiris.py`**: Main trading strategy implementation
  - **Purpose**: USDCHF-focused trading system with pullback entry mechanics
  - **Features**: 3-phase pullback system, ATR volatility filtering, dual cerebro mode
  - **Configuration**: LONG/SHORT trading, risk management, forex calculations
  - **Size**: ~2,640 lines of code

### 🐛 Debug & Logs
- **`entry_debug_*.log`**: Comprehensive entry signal analysis logs
  - Tracks every potential entry signal
  - Records blocking reasons (ATR filters, time filters, etc.)
  - Shows success/failure rates for optimization

### 📈 Visual Reports
- **`sunrise_osiris.png`**: Strategy performance visualization
- **`sunrise_osiris_long_entrys.png`**: LONG entry points analysis chart

### 📋 Trade Reports
- **`USDCHF_trades_*.txt`**: Detailed trade execution reports
  - Entry/exit timestamps and prices
  - P&L calculations and pip movements
  - ATR values and volatility analysis
  - Risk metrics and position sizing

---

## ⚙️ Configuration Structure

### 🎯 Entry Parameters
```python
# Trading Direction
ENABLE_LONG_TRADES = True
ENABLE_SHORT_TRADES = True
RUN_DUAL_CEREBRO = True              # Separate LONG/SHORT execution

# ATR Volatility Filters
LONG_ATR_MIN_THRESHOLD = 0.000200    # Minimum volatility for LONG
LONG_ATR_MAX_THRESHOLD = 0.000600    # Maximum volatility for LONG
SHORT_ATR_MIN_THRESHOLD = 0.000400   # Minimum volatility for SHORT
SHORT_ATR_MAX_THRESHOLD = 0.000750   # Maximum volatility for SHORT

# Pullback Entry System
LONG_USE_PULLBACK_ENTRY = True       # 3-phase pullback for LONG
LONG_PULLBACK_MAX_CANDLES = 1        # Max red candles in LONG pullback
SHORT_USE_PULLBACK_ENTRY = True      # 3-phase pullback for SHORT
SHORT_PULLBACK_MAX_CANDLES = 2       # Max green candles in SHORT pullback
```

### 💰 Risk Management
```python
# Position Sizing
STARTING_CASH = 100000.0             # Initial capital
RISK_PERCENT = 0.01                  # 1% risk per trade

# Forex Configuration
FOREX_INSTRUMENT = 'USDCHF'          # USD vs Swiss Franc
FOREX_PIP_VALUE = 0.0001             # 4 decimal places
FOREX_LOT_SIZE = 100000              # 100K USD lots
FOREX_LEVERAGE = 30.0                # 30:1 leverage
```

### 🕐 Trading Hours
```python
# Time Range Filter
USE_TIME_RANGE_FILTER = True
ENTRY_START_HOUR = 7                 # 07:00 UTC
ENTRY_END_HOUR = 17                  # 17:00 UTC
```

---

## 🏃‍♂️ Execution Commands

### From Repository Root
```bash
python src/strategy/sunrise_osiris.py
```

### From Strategy Directory
```bash
cd src/strategy
python sunrise_osiris.py
```

---

## 📊 Performance Summary

### Latest Results (Combined Strategy)
- **Total P&L**: +$35,398.93 (35.4% return)
- **Total Trades**: 155
- **Win Rate**: 34.19%
- **Profit Factor**: 1.35

### Strategy Breakdown
- **LONG-ONLY**: +$18,343.13 (100 trades, 27% win rate)
- **SHORT-ONLY**: +$17,055.80 (55 trades, 47.27% win rate)

---

## 🔧 Technical Features

### 🎯 Entry System
- **3-Phase Pullback Entry**: Signal Detection → Pullback → Breakout
- **EMA Crossover Detection**: Confirmation EMA vs Fast/Medium/Slow EMAs
- **ATR Volatility Filtering**: Dynamic market condition assessment
- **Time-Based Entry Windows**: UTC trading hours restriction

### 📈 Exit System
- **ATR-Based Stop Loss**: 2.5x ATR protection
- **ATR-Based Take Profit**: 12.0x ATR (LONG), 6.5x ATR (SHORT)
- **OCA Order Management**: One-Cancels-All protective orders

### 💱 Forex Features
- **USDCHF Optimization**: Specialized for USD/CHF currency pair
- **Dynamic Position Sizing**: Risk-based lot calculation
- **Pip Value Calculations**: Accurate P&L in USD terms
- **Leverage Integration**: 30:1 leverage with margin requirements

---

*Last Updated: August 30, 2025*
*Strategy Version: Sunrise Osiris USDCHF Clean*
