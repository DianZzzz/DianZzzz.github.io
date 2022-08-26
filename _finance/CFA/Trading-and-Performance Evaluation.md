---
layout: blog
topic: CFA
title: Trading and Performance Evaluation
tags: cfa finance equity
comments: true
date: 2022-07-05
---
# Trading and Performance Evaluation

## Reference Prices

### Pre-trade benchmarks

Used by portfolio managers who are buying or selling securities on the basis of decision prices.
- `Decision price`: the security price at the time the portfolio manager made the decision to buy or sell the security
- `Previous close`: often specified by quantitative portfolio managers who incorporate the previous close in a quantitative model, portfolio optimizer, or screening model.
- `Opening price`: If the trade is to be executed in the opening auction, then using the opening price as a reference benchmark is not appropriate because the trade itself can influence the reference benchmark.
- `Arrival price`: the price of the security at the time the order is entered into the market for execution.

### Intraday benchmarks

- `VWAP`: Portfolio managers who are rebalancing their portfolios over the day and have both buy and sell orders may select the VWAP
- `TWAP`: Portfolio managers may choose TWAP when they wish to exclude potential trade outliers.

### Post-trade benchmarks

- `Closing price`: An advantage of the closing price benchmark is that it provides portfolio managers with the price used for fund valuation and thus minimizes potential tracking error. A disadvantage is that the benchmark price is not known until after trading is completed.

### Price target benchmarks
- Used by portfolio managers seeking short-term alpha

## Execution Algorithm

### Scheduled algorithm (POV, VWAP, TWAP)

- Send orders to the market following a schedule
- Appropriate for orders in which portfolio managers or traders do not have expectations of adverse price movement during the trade horizon and are more concerned with minimizing market impact.

#### Percentage of volume (POV)

- As trading volume increases in the market, these algorithms will trade more shares, and as volume decreases, these algorithms will trade fewer shares.
- Advantages: will automatically take advantage of increased liquidity conditions by trading more shares when there is ample market liquidity and will not trade in times of illiquidity.
- Disadvantages: may incur higher trading costs by continuing to buy as prices move higher and to sell as prices move lower and may not complete the order within the time period specified.

#### VWAP algorithms

-  Trade a higher percentage of the order at the open and close and a smaller percentage of the order during midday.
- Advantages: ensures the specified number of shares are executed within the specified time period.
- Disadvantages: may not be optimal for illiquid stocks because such algorithms may not complete the order in cases where volumes are low.

#### TWAP algorithms

- Send the same number of shares and the same percentage of the order to be traded in each time period.
- Suitable for trading that needs to be completed within a short timeframe

### Opportunistic algorithms (Liquidity-seeking)

- Take advantage of market liquidity across multiple venues by trading faster when liquidity exists at a favorable price.

### Dark Aggregator

- Used when portfolio managers and traders are concerned with information leakage that may occur from posting limit orders.
- Used when the order size is large relative to the market and are appropriate for trades in which the trader or portfolio manager does not need to execute the order in its entirety.

### Arrival price

- Seek to trade close to current market prices at the time the order is received for execution.
- Arrival price algorithms will trade more aggressively at the beginning of trading to execute more shares nearer to the arrival price, known as a front-loaded strategy.
- Used for orders in which the portfolio manager or trader believes prices are likely to move unfavorably during the trade horizon.

## Trading Cost

Implementation Shortfall = Trading Cost + Delay cost + Opportunity Cost + Fees (TDOF)

Trading Cost = # of shares purchased * (actual price - price_delayed)

Delay Cost = # of shares purchased * (price_delayed - decision price)

Opportunity Cost = # of shares not filled * (closing price - decision price)

Execution Cost = Delay Cost + Trading Cost


### Arrival cost

Arrival cost = side * (average price - arrival price) / arrival price * 10000 bps

### Market-adjusted cost

Index cost (in bps) = (average index price - arrival index price) / arrival index price * 10000 bps

Market-adjusted cost = arrival cost (in bps) - beta * index cost

If market-adjusted cost is significantly lower than the total arrival cost, this indicates that most of the expense associated with buying is due to the effect of buying it in a rising market as opposed to the buying pressure induced by the order itself.

## Trading Strategies

### Equitization

- To temporarily invest cash using futures or ETFs to gain the desired equity exposure before investing in the underlying securities longer term.
- May be required if large inflows into a portfolio are hindered by lack of liquidity in the underlying securities.

### Cash Market vs. Derivatives Market

Derivative market has the following advantages
- Quick implementation
- Flexibility to tactically adjust exposure and quickly reverse decisions
- Ability to leave external managers in place
- High levels of liquidity

Thus derivative market is suitable for short-term rebalancing as opposed to reallocating amongst managers


## Investment Philosophy

- `Behavioral inefficiencies` are perceived mispricings created by the actions of other market participants, usually associated with biases. These inefficiencies are temporary, lasting long enough for the manager to identify and exploit them before the market price and perceived intrinsic value converge.

- `Structural inefficiencies` are perceived mispricings created by external or internal rules and regulations. These inefficiencies can be long lived


## Performance Evaluation

- `Performance measurement`: provides an overall indication of the portfolio’s performance, usually relative to a benchmark.
- `Performance attribution`: analyzes the impact of active investment decisions on returns and the risk consequences of those decisions.
- `Performance appraisal`: indicates whether the portfolio’s performance was achieved through manager skill or through luck.

### Performance attribution

#### Return vs. Risk
-  `Return attribution`: analyzes the impact of active investment decisions on returns
-  `Risk attribution`: analyzes the risk consequences of those decisions.

#### Macro vs. Micro

-  `Macro attribution`: attribution at the sponsor level to evaluate the asset owner’s tactical asset allocation and manager selection decisions
-  `Micro attribution`: attribution at the portfolio manager level to evaluate the impact of the portfolio manager’s decisions

#### Three Approaches

##### Returns-based attribution
- Uses only the total portfolio returns over a period to identify the components of the investment process that have generated the returns.
- Easiest to implement but least accurate
- Most appropriate when the underlying portfolio holdings are not readily available with sufficient frequency at the required level of detail (e.g., hedge funds)

##### Holdings-based attribution
- Calculates the return of portfolio and benchmark components based upon the price and foreign exchange rate changes applied to daily snapshots of portfolio holdings.
- Most appropriate for investment strategies with little turnover (e.g., passive strategies)

##### Transaction- based attribution
- Most effective for active stock selection portfolios because it captures both the holdings and the transactions (purchases/sales) completed within the defined period, which would allow the entire excess return to be quantified and explained.


#### Equity Return Attribution

##### The Brinson–Hood–Beebower approach

Allocation = (portfolio’s sector weight - benchmark’s sector weight) *  benchmark sector return
Selection = (portfolio’s sector return - benchmark’s sector return) *  benchmark sector weight
Interaction = (portfolio’s sector weight - benchmark’s sector weight) * (portfolio’s sector return - benchmark’s sector return)

##### Brinson–Fachler Model
Allocation = (portfolio’s sector weight - benchmark’s sector weight) *  (benchmark sector return - benchmark return)

##### Carhart Four Factor model

- RMRF = the return on a value-weighted equity index in excess of the one-month T-bill rate
- SMB = small minus big, a size (market-capitalization) factor (SMB is the average return on three small-cap portfolios minus the average return on three large-cap portfolios)
- HML = high minus low, a value factor (HML is the average return on two high-book-to-market portfolios minus the average return on two low-book-to-market portfolios)
- WML = winners minus losers, a momentum factor (WML is the return on a portfolio of the past year’s winners minus the return on a portfolio of the past year’s losers)


#### Fixed-income attribution

- Exposure decomposition—duration based
- Yield curve decomposition—duration based
- Yield curve decomposition—full repricing based
-
#### Risk Attribution

- Absolute return target:  contribution to total risk or factor’s  contribution to total risk and specific risk
- Relative return target: marginal contribution to tracking risk

#### Decomposition of Portfolio Return

Portfolio Return = Market Return + Active Management Return + Style Return
S = Benchmark - Market
A = Portfolio - Benchmark

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

### Separately Managed Account

#### Advantages

- Ownership: In an SMA, the investor owns the individual securities directly. This approach provides additional safety should a liquidity event occur.

- Independence: Investment decisions will not be influenced by the redemption or liquidity demand of other investors in the strategy.

- Customization: SMAs allow the investor to potentially express individual constraints or preferences within the portfolio. SMAs can thus more closely address the investor’s particular investment objectives.

- Tax efficiency: SMAs offer potentially improved tax efficiency because the investor pays taxes only on the capital gains realized and allows the implementation of tax-efficient investing and trading strategies.

- Transparency: SMAs offer real-time, position-level detail to the investor, providing complete transparency and accurate attribution to the investor.

#### Disadvantages

- Cost: Separate accounts represent an additional operational burden on the manager, which translates into potentially higher costs for the investor. In addition, SMAs are likely to face higher transaction costs to the degree that trades cannot be aggregated to reduce trade volumes.

- Tracking risk: Customization of the strategy creates tracking risk relative to the benchmark, which can confuse attribution because performance will reflect investor constraints rather than manager decisions.

- Investor behavior: Potential micromanagement by the investor. Potential investor behaviors include performance chasing, familiarity bias (being overly averse to unfamiliar holdings), and loss aversion

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

## Portfolio Reporting and Review

### Portfolio Reporting

- A portfolio asset allocation report, which may reflect strategic asset allocation targets
- A performance summary report for the current (often year-to-date) period
- A detailed performance report, which may include asset class and/or individual security performance
- A historical performance report covering the period since the inception of the client’s investment strategy
- A contribution and withdrawal report for the current period
- A purchase and sale report for the current period
- A currency exposure report detailing the effects of exchange rate fluctuations
- An accompanying letter that provides market commentary, investment context, education, and other advice

## Fee Structure

### AUM Based

- Advantages: avoid making risky decisions
- Disadvantages: less incentive to generate extra return

### Performance Based

- Advantages: align interests of the manager and the client
- Disadvantages: may lead to misestimates of portfolio risk and may incentivize managers to assume higher portfolio risk; may incentivize managers to hold on to assets until a profit can be realized even if the client would benefit from selling the assets at a loss and investing the proceeds elsewhere.
