---
name: price-action-analyzer
description: >
  Based on Al Brooks price action for A-share/global stock technical analysis.
  Trigger on price action analysis, pattern identification, trend judgment,
  entry/exit timing, stop loss, or keywords like price action, PA, Al Brooks,
  candlestick analysis, trend analysis, pullback entry, breakout analysis,
  trading range, wedge reversal. Uses china_stock/cn_financial MCP tools.
---

# Price Action Analyzer

Analyze stock K-line charts using Al Brooks Trading Price Action framework.
Complete trading rules in references/price-action-rules.md. Read that file before each analysis.

## Workflow

### Step 1: Fetch Data

Use china_stock get_hist_data for daily K-lines with indicators:
SMA(20), EMA(20), RSI(14), MACD, BOLL(20,2), ATR(14), OBV.
Also fetch weekly data for higher timeframe context.
For A-shares, also get basic_info. Use realtime_data for current price.

### Step 2: Determine Market State

Classify into one of four states using recent 20-100 daily bars:

1. Breakout: consecutive large bodies, pullbacks under 1-3 bars, price pulls away from 20 EMA
2. Tight Channel: small pullbacks, clear direction, EMA stays on one side of price
3. Broad Channel: 5-20 bar pullbacks, EMA loosely supports/resists price
4. Trading Range: price repeatedly hits boundaries, overlapping bars, EMA crosses through price

Align findings with weekly timeframe direction.

### Step 3: Identify Key Signals

Read references/price-action-rules.md and identify:
- Trend continuation: H1/H2 pullback entries, M2B/M2S (two-leg pullback to EMA), 20 GAP Bar
- Breakout quality: strong vs weak/false breakout, follow-through confirmation
- Reversal signals: MTR four conditions, Wedge/3P, Climax, Final Flag, Double Top/Bottom
- Range signals: boundary touch count, 80% breakout failure rule

### Step 4: Output Analysis

Output structured analysis in Chinese:

Market State: current cycle (Breakout/Tight Channel/Broad Channel/Trading Range),
weekly background (bullish/bearish/neutral), 20 EMA relationship

Key Signals: specific price action signals with bar dates and price levels

Trade Suggestions (if user requests):
- Direction: long/short/wait
- Entry logic and confirmation conditions
- Stop loss: specific price or bar level
- Target: Measured Move or key support/resistance
- Position size: small/normal

Risk Notes: failure probability (40-60 rule), invalidation conditions

### Step 5: Risk-Reward Assessment

Calculate actual R:R from entry-to-stop vs entry-to-target.
Under 1:1 not recommended. 1:1 needs 60%+ confidence. 2:1+ is ideal.

## Core Principles

- Minimum two reasons per entry (e.g. H2 + 20 EMA support)
- Weekly + daily alignment = highest probability
- Trading ranges: default to fade breakouts (80% fail)
- Strong trends: ignore counter-trend signals (Always In Long)
- Climax does not equal reversal (likely goes to range first)
- Trade management > entry (give trailing stop and scale-out advice)

## Communication

- Output in Chinese, technical terms in English (H2, MTR, EMA, etc.)
- Reference specific bar dates so user can verify on chart
- If user only asks about trend or pattern, only run relevant steps
