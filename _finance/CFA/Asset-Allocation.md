---
layout: blog
topic: CFA
title: Asset Allocation
tags: cfa finance
comments: true
date: 2022-06-17
---
# Asset Allocation

## Asset Risks

### Three Super-Classes of Risks
- Capital Assets
- Consumable/transformable Assets
- Store of Value of Assets

### Optimal Choice Between One Risky Asset and Risk Free Asset
w* =1/λ * (μ−r_f/σ^2)
λ: investor's risk aversion

### Risk Budgeting
- Objective: specifies the total amount of risk and how much of risk should be budgeted for each asset class
- Marginal Contribution to Total Risk (MCTR) = beta * portfolio volatility
- Absolute Contribution to Total Risk (ACTR) = weight * MCTR
- An optimal asset allocation is when the ratio of excess return to MCTR is the same for all assets and matches the Sharpe ratio of the tangency portfolio


## Implementation Choices
- Whether to allow deviations from the strategic allocation
  - `Tactical asset allocation`: deliberation short term deviation from the strategic asset allocation
  - `Dynamic asset allocation`: deliberation long term deviation from the strategic asset allocation
- Invest along the active/passive spectrum

## Approaches to Asset Allocation

- Asset-only
  - Mean variance optimization
- Liability-relative
  - Surplus optimization
  - Hedging/Return-Seeking Portfolio Approach
- Goals-based

### Mean Variance Optimization

#### Utility Function

U = E(R) - 0.005 * λ * σ^2 where λ = the investor’s risk aversion coefficient

#### Criticism of MVO
- Outputs are highly sensitive to small changes in inputs
- Investors are concerned more than just mean and variance of return
- Does not take into account of trading costs and taxes
- Efficient portfolios are highly concentrated in a subset of the available asset classes

#### Alternative Models
- Reverse MVO
- Black-Litterman Model
- Constrained asset class weights
- Resampled MVO = MVO + Monte Carlo Simulation

### Surplus Optimization

U = E(R) - 0.005 * λ * σ^2
where E(R) = surplus return = (Δ in asset value - Δ in liability value) / Initial asset value
Δ in liability value = time value of money for the liabilities + any expected changes in the discount rate and future cash flows over the planning horizon
- Assumes linear correlation between assets and liabilities
- Can apply to any funded ratio
- Single period model

### Hedging/Return-Seeking Portfolio Approach
- Assumes both linear and nonlinear correlation between assets and liabilities
- Requires positive funded ratio
- Single period model

### Integrated Asset-Liability Approach

- Assumes both linear and nonlinear correlation between assets and liabilities
- Can apply to any funded ratio
- Multi period model

## Rebalance

### Optimal Width of Corridor
- Higher transaction costs -> wider corridor
- Higher risk tolerance -> wider corridor
- Higher correlation with the rest of portfolio -> wider corridor
- Higher tax -> wider corridor
- Higher volatility -> wider corridor
- Higher volatility of the rest of portfolio -> narrower corridor

## Tax Consideration

- after-tax standard deviation = pre-tax standard deviation * (1-t)
- Tax Advantage Retirement Account = Investment grade bonds, high yield bond, dividend income stock, total return (capital gain) stock

## Behavior Biases in Asset Allocation

### Loss Aversion
- Frame risk in terms of shortfall probability
- Fund high-priority goals with low risk assets

### Illusion of Control
- Use global market portfolio as the starting point in developing asset allocation
- A formal asset allocation process that employs long-term return and risk forecasts, optimization constraints anchored around asset class weights in the global market portfolio, and strict policy ranges

### Mental Accounting
- Goals-based investing by aligning each goal with a discrete sub-portfolio, and the investor can specify the acceptable level of risk for each goal.
- Assign the concentrated stock position to an aspirational goal—one that the client would like to achieve but to which he or she is willing to assign a lower probability of success.

### Representativeness Bias
- A formal asset allocation policy with pre-specified allowable ranges
- A strong governance framework with the appropriate level of expertise and well-documented investment beliefs

### Framing Bias
- Use alternative risk measurement such as VaR and Conditional VaR
  - VaR: the minimum loss that would be expected a certain percentage of the time over a certain period of time given the assumed market conditions.
  - CVaR: the probability-weighted average of losses when the VaR threshold is breached.
  - Shortfall Proability
- Present the possible asset allocation choices with multiple perspectives on the risk/reward trade-off.

### Availability Bias
- A formal asset allocation process using the global market portfolio as the starting point for asset allocation modeling
- A strong governance framework with the appropriate level of expertise and well-documented investment beliefs 
