---
layout: blog
topic: CFA
title: Trading and Performance Evaluation
tags: cfa finance equity
comments: true
date: 2022-07-05
---
# Trading and Performance Evaluation

## Trading Cost

Implementation Shortfall = Execution cost + Opportunity Cost + Fees

Expanded implementation shortfall = Delay cost + Trading Cost + Opportunity Cost + Fees


Opportunity Cost = # of shares not filled * (price_t1 - price_t0)

Execution Cost = Delay Cost + Trading Cost = Actual price paid - # of shares purchased * price_t0

Delay Cost = # of shares purchased * (price_delayed - price_t0)

Trading Cost = Actual price paid - # of shares purchased * price_delayed

## Performance Evaluation

- `Performance attribution`: Explains how the excess performance or risk was achieved.
- `Performance appraisal`: uses the results of risk, return, and attribution analyses to assess the quality of a portfolio's performance.

### Performance attribution

#### Return vs. Risk
-  `Return attribution`: analyzes the impact of active investment decisions on returns
-  `Risk attribution`: analyzes the risk consequences of those decisions.

#### Macro vs. Micro

-  `Macro attribution`: attribution at the sponsor level to evaluate the asset owner’s tactical asset allocation and manager selection decisions
-  `Micro attribution`: attribution at the portfolio manager level to evaluate the impact of the portfolio manager’s decisions

#### Return-based vs. Holding-based vs. Transaction-based
- `Returns-based attribution`:
  - Uses only the total portfolio returns over a period to identify the components of the investment process that have generated the returns.
  - Easiest to implement but least accurate
-  `Holdings-based attribution`: calculates the return of portfolio and benchmark components based upon the price and foreign exchange rate changes applied to daily snapshots of portfolio holdings.
-  `Transaction- based attribution`: captures the impact of intra-day trades and exogenous events such as a significant class action settlement.
- `Performance appraisal` uses the results of risk, return, and attribution analyses to assess the quality of a portfolio's performance.

#### Equity Return Attribution

##### The Brinson–Hood–Beebower approach

Allocation = (portfolio’s sector weight - benchmark’s sector weight) *  benchmark sector return
Selection = (portfolio’s sector return - benchmark’s sector return) *  benchmark sector return
Interaction = (portfolio’s sector weight - benchmark’s sector weight) * (portfolio’s sector return - benchmark’s sector return)

##### Brinson–Fachler Model
Allocation = (portfolio’s sector weight - benchmark’s sector weight) *  (benchmark sector return - benchmark return)

##### Carhart Four Factor model

- RMRF = the return on a value-weighted equity index in excess of the one-month T-bill rate
- SMB = small minus big, a size (market-capitalization) factor (SMB is the average return on three small-cap portfolios minus the average return on three large-cap portfolios)
- HML = high minus low, a value factor (HML is the average return on two high-book-to-market portfolios minus the average return on two low-book-to-market portfolios)
- WML = winners minus losers, a momentum factor (WML is the return on a portfolio of the past year’s winners minus the return on a portfolio of the past year’s losers)

##### Bailey Decomposition

Portfolio Return = Market Return + Active Management Return + Style Return
S = Benchmark - Market
A = Portfolio - Benchmark
#### Fixed-income attribution

- Exposure decomposition—duration based
- Yield curve decomposition—duration based
- Yield curve decomposition—full repricing based
-
#### Risk Attribution

- Absolute return target: marginal contribution to total risk or factor’s marginal contribution to total risk and specific risk
- Relative return target: marginal contribution to tracking risk

#### Decomposition of Portfolio Return

Return due to style = Benchmark - Market
Return due to active management = Portfolio - Benchmark

### Performance Appraisal

#### Sharpe ratio
- (Portfolio return - risk free rate) / standard deviation
- the use of standard deviation as a measure of risk assumes investors are indifferent between upside and downside volatility

#### Treynor ratio
- (Portfolio return - risk free rate) / beta
- measures the excess return per unit of systematic risk

#### Information ratio
- (Portfolio return - benchmark return) / standard deviation of excess return

#### Appraisal ratio
- alpha / sqrt(non-systematic risk)
- non-systematic risk = portfolio standard deviation^2 - beta^2 * makrt standard deviation^2

#### Sortino ratio
- (portfolio return - target return) / target standard deviation
- more relevant when return distributions are not symmetrical, as with option writing and when one of the primary objectives is capital preservation.

#### Capture ratios
- Calculate the geometric means for upside or downside returns: [(1+x1)(1+x2)...(1+xn)]^(1/n)
- Upside (Downside) Capture = Portfolio Mean / Benchmark Mean
- Capture Ratio = Upside Ratio / Downside Ratio
- Capture Ratio > 1: Convex return
- Capture Ratio < 1: Concave return
- Capture RATIO = 1: Symmetric return

## Investment Manager Selection

- Defining the universe
  - Suitability
  - Style
  - Active v. Passive
- Quantitative Analysis
  - Attribution and appraisal
  - Capture ratio
  - Drawdown
- Qualitative Analysis
  - Investment due diligence
    - Philosophy
    - Investment Process
    - People
    - Portfolio
  - Operational due diligence
    - Process and procedure
    - Firm
    - Investment vehicle
    - Terms
    - Monitoring

### Style Analysis

#### Return-based style analysis (RBSA)

##### Advantages
 - Does not require potentially difficult to acquire data.
##### Disadvantages
 - Not a precise tool
 - If the portfolio contains illiquid securities, stale prices may understate the risk exposure of the strategy.

#### Holdings-based style analysis (HBSA)
##### Advantages
 - It can identify important drivers of return and risk factors and is comparable across managers and through time.
 -
##### Disadvantages
 - The computational effort increases with the complexity of the strategy and depends on the timing and degree of the transparency provided by the manager.
 - Window dressing and high turnover can compromise the results because the results are attributed to a snapshot of the portfolio.
 - If the portfolio has illiquid securities, stale pricing may underestimate the risk exposure of the strategy.
