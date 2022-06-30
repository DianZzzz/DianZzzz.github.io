---
layout: blog
topic: CFA
title: Equity Portfolio Management
tags: cfa finance equity
comments: true
date: 2022-06-28
---
# Equity Portfolio Management

## Benchmark

- Buffering: Establishing ranges around breakpoints that define whether a stock belongs in one index or another.
- Packeting: involves splitting stock positions into multiple parts. If a stock's capitalization increases and breaches the breakpoint between mid-cap and large-cap indexes, a portion of the total holding is transferred to the large-cap index but the rest stays in the mid-cap index.

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
- Pitfalls: Survivorship Bias, Look-Ahead Bias, Data Mining, and Overfitting
