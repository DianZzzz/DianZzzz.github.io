---
layout: blog
topic: CFA Level III
title: Equity Portfolio Management
tags: cfa finance equity
comments: true
date: 2022-06-28
---
# Equity Portfolio Management

<!-- MDTOC maxdepth:6 firsth1:0 numbering:0 flatten:0 bullets:1 updateOnSave:1 -->

- [Benchmark](#benchmark)
  - [Index Requirement](#index-requirement)
  - [Herfindahl-Hirschman Index (HHI)](#herfindahl-hirschman-index-hhi)
- [Passive Investment](#passive-investment)
  - [Stratified Sampling](#stratified-sampling)
  - [Optimization](#optimization)
    - [Advantages](#advantages)
    - [Disadvantage](#disadvantage)
  - [Tracking Error](#tracking-error)
    - [Sources of tracking error](#sources-of-tracking-error)
- [Active Investment](#active-investment)
  - [Fundamental](#fundamental)
  - [Quantitative](#quantitative)
  - [Bottom-up approach](#bottom-up-approach)
  - [Top-down approach](#top-down-approach)
  - [Active Investment Pitfall](#active-investment-pitfall)
- [Style Analysis](#style-analysis)
  - [Holding-based analysis](#holding-based-analysis)
    - [Pros](#pros)
    - [Cons](#cons)
  - [Return-based analysis](#return-based-analysis)
    - [Pros](#pros-1)
    - [Cons](#cons-1)
  - [Building blocks of portfolio construction](#building-blocks-of-portfolio-construction)
  - [Fundamental law of active management](#fundamental-law-of-active-management)
    - [Pearson IC](#pearson-ic)
    - [Spearman Rank IC addressees this issue and is often](#spearman-rank-ic-addressees-this-issue-and-is-often)
  - [Active Share](#active-share)
  - [Active Risk](#active-risk)
    - [Pure indexing](#pure-indexing)
    - [Factor neutral](#factor-neutral)
    - [Factor diversified / Diversified stock picker](#factor-diversified--diversified-stock-picker)
    - [Concentrated factor bets](#concentrated-factor-bets)
    - [Concentrated stock picker](#concentrated-stock-picker)
  - [Strategies](#strategies)
    - [Merits of Long Only Investing](#merits-of-long-only-investing)
    - [Benefits of Long/Short Strategies](#benefits-of-longshort-strategies)
    - [Drawbacks of Long/Short Strategies](#drawbacks-of-longshort-strategies)

<!-- /MDTOC -->
## Benchmark

- Buffering: Establishing ranges around breakpoints that define whether a stock belongs in one index or another.
- Packeting: involves splitting stock positions into multiple parts. If a stock's capitalization increases and breaches the breakpoint between mid-cap and large-cap indexes, a portion of the total holding is transferred to the large-cap index but the rest stays in the mid-cap index.

### Index Requirement

1. Rules-based
2. Transparent
3. Investable

### Herfindahl-Hirschman Index (HHI)

HHI = Sum of Weights^2
Effective number of stocks = 1/HHI

## Passive Investment

### Stratified Sampling

- The manager recommends that the client set a maximum number of constituents (for example, 200) to limit the average lot size and to reduce commission costs.
- Next, the manager selects the 200 securities with the largest market capitalizations.
- Then the manager seeks to more closely match the performance of the index by matching the sector weightings of the sampled portfolio to the sector weightings of the index.


### Optimization
- Maximizing a desirable characteristic or minimizing an undesirable characteristic, subject to one or more constraints

#### Advantages
- a lower amount of tracking error than stratified sampling.
- optimization process accounts explicitly for the covariances among the portfolio constituents.

#### Disadvantage
- the output from an optimization program may apply only to the period from which the data are drawn and not to a future period.
- Even if current results apply to the future, they might not be applicable for long.
- Optimization would need to be run and adjustments made to the portfolio, which can be costly.

### Tracking Error

Tracking Error = sqrt(variance(Portfolio Return - Benchmark Return))

#### Sources of tracking error

- Fees
- Number of securities held
- Intra-day trading
- Trading costs
- Cash holding of the fund

## Active Investment

### Fundamental

- Construct the portfolio by overweighting stocks that are expected to outperform their peers or the market as a whole and underweight some benchmark stocks that are expected to underperform.
- The manager monitors each stock continuously and sells stocks when their market prices surpass the target prices

### Quantitative

- Construct the portfolio by maximizing the objective function (such as portfolio alpha or information ratio) with risk models.
- Portfolios are usually rebalanced at regular intervals, such as monthly.
- Pitfalls: Survivorship Bias, Look-Ahead Bias, Data Mining, and Overfitting, Turnover, Transaction Costs, and Short Availability

### Bottom-up approach

- Analyze information at the company level to generate investment
ideas.
- Bottom up strategies can be divided into value and growth styles. - Resulted portfolios could be diversified or concentrated depending on manager style

### Top-down approach
- Focus on the macroeconomic environment, demographic trends,
and government policies to make investment decisions.
- Typically incoporates factor timing and results in a diversified portfolio

### Active Investment Pitfall

- `Survivorship bias`: If back-tests are only applied to existing companies, then they will overlook companies that have failed in the past, and this will make the strategy look better than it actually is.
- `Look-ahead bias`: Results from using information in the model to give trading signals at a time when the information was not available, most likely due to accounting lag
- `Data-mining/overfitting`: Excessive search analysis of past financial data to find data that shows a strategy working.
- `Turnover`: Constraints on turnover may constrain the manager’s ability to follow a strategy.
- `Lack of availability of stock to borrow`: For short selling, this may also constrain a manager’s ability to follow a strategy.
- `Transaction costs`: This can quickly erode the returns of a strategy that looked good in backtesting.
- `Quant overcrowding`: Once a strategy becomes crowded, there is the risk that a period of poor performance could cause many managers
attempt to exit their positions at the same time. This rush for the exit could exaggerate losses and lead to margin calls from lenders forcing managers to further liquidate their positions at unfavorable prices.

## Style Analysis

### Holding-based analysis

The holdings-based approach looks at the attributes of each individual stock in a portfolio and aggregates these attributes to conclude the overall style of the portfolio.

#### Pros
- Generally more accurate because it uses actual portfolio holdings.
- Assesses each individual holding’s contribution to style.

#### Cons
- Requires the availability of all portfolio constituents and style
attributes of each.
- Limited derivatives data may hinder analysis if derivatives are
used.
- Different systems with different definitions of style will classify the same portfolio in different ways.

### Return-based analysis

A returns-based style analysis aims to identify the style of a fund through regression of the funds returns against a set of passive style indices.

#### Pros
- Does not require information on holdings.
- Can be easily and universally applied.

#### Cons
- Constraints on outputs can limit detection of extreme styles.

### Building blocks of portfolio construction

1. Factor weightings.
2. Alpha skills (factor timing)
3. Position sizing.
4. Breadth of expertise (integrating the first 3 blocks)

### Fundamental law of active management
Expected Active Return = Information coefficient * sqrt(Breadth) * Active Risk * Transfer Coefficient

#### Pearson IC
- Linear correlation between the factor exposure and holding period return.
- Range between +1 and –1
- A monthly value of even 5% to 6% is considered very strong.
- Sensitive to even a few outliers

#### Spearman Rank IC addressees this issue and is often
- IC of the rank of the factor scores and rank of subsequent performance.
- Addresses the outlier issue and thus more robust than Person IC

### Active Share

- Measures the degree to which the number and sizing of the positions in a manager’s portfolio are different from those of a benchmark

- Formula: Σ abs(portfolio weight - benchmark weight)

### Active Risk
- Also called tracking error, is the standard deviation of active returns (portfolio returns minus benchmark returns).

#### Pure indexing
- No active positions: portfolio is equal to the benchmark
- Zero active share and zero active risk


#### Factor neutral
- No active factor bets — idiosyncratic risk low if diversified
- Low active risk — active share low if diversified

#### Factor diversified / Diversified stock picker
- Balanced exposure to risk factors and minimized idiosyncratic risk through high number of securities in portfolio
- Reasonably low active risk
- High active share from large amount of securities used that are
unlikely to be in the benchmark

#### Concentrated factor bets
- Targeted factor bets—idiosyncratic risk likely to be high
- High active share and high active risk

#### Concentrated stock picker
- Targeted individual stock bets
- Highest Active Share and highest active risk

### Strategies

- Long only
- Long extension: long/short strategies typically constrained to have a net exposure of 100%
- Market Neutral

#### Merits of Long Only Investing
- Long-term risk premiums, such as the market risk premium, are earned by investors going net long securities
- The capacity and scalability of a long-only strategy is set by the liquidity of the underlying securities. Capacity of short-selling strategies is set by the availability of securities to borrow to facilitate short-selling.
- Due to limited legal liability laws, the maximum a long investor can lose is the amount they paid for the security (if the security falls to zero). The potential loss to a short-seller is unlimited
- Regulations allow some countries to ban short-selling in the interests of financial market stability.
- Transactional complexity is higher for a long/short fund. A shortseller must source shares to borrow, provide collateral to the lender of the shares, and faces the risk the lender recalls the shares at an inopportune time.
- Costs are likely to be higher for long/short funds than long-only funds both in terms of management fees and operational expenses.
- The personal ideology of an investor might cause them to object to short-selling.

#### Benefits of Long/Short Strategies

- Greater ability to express negative ideas than a long-only strategy. This will increase the information ratio because lower constraints will increase the transfer coefficient of the manager
- Ability to use the leverage generated by short positions to gear into high conviction long ideas.
- Ability to remove market risk and act as a diversifying investment against other strategies.
- Greater ability to control exposure to risk factors. Because most rewarded factors (size, value, momentum, etc.) are obtained through a long/short portfolio, being able to short-sell allows managers to better control their exposure to these factors.

#### Drawbacks of Long/Short Strategies

- Manager is reducing long-term exposure to the market risk premium.
- Some long/short strategies require significant leverage, which magnifies losses
- The cost of borrowing securities can become too high, particularly for securities that are difficult to borrow.
- Losses on the short position will increase collateral demands from stock lenders, particularly if leverage has been used. This may force the manager to liquidate positions at unfavorable prices.
- Vulnerable to a short squeeze, where a sudden rise in the price of a heavily-shorted security forces short-sellers to cover positions, buy back shares and potentially force the share price higher.
- Lenders of securities could also recall shares at inopportune times
causing disruption to the manager’s strategy.
