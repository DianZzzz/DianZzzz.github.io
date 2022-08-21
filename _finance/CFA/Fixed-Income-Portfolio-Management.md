---
layout: blog
topic: CFA
title: Fixed-Income Portfolio Management
tags: cfa finance
comments: true
date: 2022-06-21
---
# Fixed-Income Portfolio Management

## Fixed Income Mandates

- Total Return
  - Pure indexing
  - Enhanced indexing
  - Active management
- Liability Based
  - Cash flow matching
  - Duration matching
  - Derivatives overlay
  - Contingent immunization


## Statistical Credit Analysis

- `Reduced form credit models`: solve for default intensity, or the POD over a specific time period, using observable company-specific variables such as financial ratios and recovery assumptions as well as macroeconomic variables, including economic growth and market volatility measures.
- `Structural credit models`: use market-based variables to estimate the market value of an issuer’s assets and the volatility of asset value. The likelihood of default is defined as the probability of the asset value falling below that of liabilities.


## Fixed Income Portfolio Measures

### Duration

#### Macaulay duration
- Weighted average of the time to receipt of the bond’s promised payments
- Increases linearly with maturity of the bond

#### Modified duration
- Measures the sensitivity of the bond’s price to a change in interest rate
- = Macaulay duration / (1 + yield)
- If a bond has ModDur of 15, then for a 100bp increase in yield, its price is expected to decrease by 15%

#### Effective Duration
- Measures the sensitivity of the bond’s price to a change in a benchmark yield curve
- When a bond has embedded options, its effective duration will be different from its modified duration
- = (PV- + PV+) / (2 * ΔCurve * PV_0)

#### Key Rate Duration
- Measures the sensitivity of the bond’s price to the shape of the benchmark yield curve

#### Empirical duration
- Determined from market data - run a regression of bond price returns on changes in a benchmark interest rate

#### Money duration
- A measure of the price change in units of the currency in which the bond is denominated.

#### Price value of a basis point (PVBP)
- An estimate of the change in a bond’s price given a 1 bp change in yield to maturity.

#### Spread Duration
- Measures the sensitivity of the bond’s price to changes in credit spread

#### Duration times spread (DTS)
- DTS = EffSpreadDur * Spread

#### Portfolio dispersion
- Measures the variance of the times of the cash flow

#### Convexity
- If a bond has positive convexity, the expected return of the bond will be higher than the return of an identical-duration, lower-convexity bond if interest rates change.
- A coupon paying bond has more convexity than zero-coupon bond of the same duration

#### Effective convexity
- = (PV- + PV+ - 2PV_0) / ΔCurve^2 * PV_0)

## Fixed Income Return Model
E(R) =  Coupon income
        +/– Rolldown return
        +/– E(ΔPrice due to investor’s view of benchmark yield)
        +/– E(ΔPrice due to investor’s view of yield spreads)
        +/– E(ΔPrice due to investor’s view of currency value changes)

Rolling yield = Coupon income return + rolldown return

Coupon income return = coupon / current price
Rolldown return=(Bond price_t1 - Bond price_t0) / Bond price_to

E(ΔPrice due to investor’s view of benchmark yield) = - ModDur * ΔYield + 0.5 * Convexity * ΔYield^2

E(ΔPrice due to investor’s view of yield spreads) = - ModDur * ΔSpread + 0.5 * Convexity * ΔYield^2

## Repo Agreements

Dollar interest = principal * repo rate * days/360

## Classification of Liabilities

### Type 1
- The amount and timing of cash outlay are known
- i.e. traditional bond with no embedded options

### Type 2
- The amount is known but timing is uncertain
- i.e. term life insurance, demand deposits

### Type 3
- The amount is uncertain but the timing is known
- i.e. floating rate note, TIPS

### Type 4
- The amount and timing of cash outlay are uncertain
- residential mortgage, insurance, convertible bonds

## Portfolio Immunization

- Cash flow matching
  - A laddered portfolio
    - lower convexity and dispersion than a barbell portfolio but more than a bullet portfolio, given comparable duration and cash flow yields.
  - A bullet portfolio
  - A barbell portfolio
- Duration matching
- Derivatives overlay
- Contingent immunization

Immunized portfolio convexity = (MacDur^2 + MacDur + Dispersion) / (1 + Cash flow yield)^2

### Immunization Conditions

#### Single Liabilities
- Match the Macaulay duration
- Minimize convexity

#### Multiple Liabilities
- the money duration (or BPV) of the asset and liability to match
- the immunizing portfolio needs to be greater than the convexity (and dispersion) of the outflow portfolio. But, the convexity of the immunizing portfolio should be minimized in order to minimize dispersion and reduce structural risk.


## Fixed Income Portfolio Construction

- Laddered Portfolio
  - Protection from shifts and twists
- Barbell Portfolio
- Bullet Portfolio

### Derivatives Overlay

Number of futures to sell = (Liability BPV - Asset BPV) / Futures BPV

If assets < liabilities, we long futures. The long position increase in value if interest rate falls.
If assets > liabilities, we short futures. The short position increase in value if interest rate rises.

#### Calls and Puts
![callable-bond](/assets/callable-bond.PNG)![putable-bond](/assets/putable-bond.PNG)
#### Swap

Asset BPV + (Notional Amount * Swap BPV / 100) = Liability BPV

#### Swaptions

Long a receiver swaption: receive fixed payment and pay float

## Bond Index

Tracking error of 1% means that assuming normally distributed returns, in 68% of time periods, the fund should have a return that is within 1% of the tracked index.

### Reduce tracking error
- using the present value of distribution of cash flows methodology
- matching the amount of index duration that comes from each sector, as well as matching the amount of index duration that comes from various quality categories across government and non-government bonds, to minimize tracking error.
- evaluate the portfolio duration coming from each issuer to minimize event risk

## Yield Curve

### Butterfly Spread
- Butterfly spread = - short term yield + 2 * mid-term yield - long-term yield
- Negative butterfly: An increase in the butterfly spread due to lower short- and long-term yields-to-maturity and a higher intermediate yield-to-maturity.
  - Strategy: a short bullet with a long barbell
- Positive buttefly: A decrease in the butterfly spread due to higher short- and long-term yields-to-maturity and a lower intermediate yield-to-maturity.
  - Strategy: a long bullet with a short barbell

### Bull Steepening
- Short term rate fall more than long term rate
- Expansionary monetary policy to stimulate the economy

### Bear Steepening
- Long term rate increases more than short term rate
- Tightening monetary policy to curb inflation

### Bull Flattening
- A decrease in the yield spread between long- and short-term rate, largely driven by a decline in long-term rate

### Bear Flattening

- A decrease in the yield spread between long- and short-term rate, largely driven by a rise in short-term rate

## Credit Risk

Expected Exposure (EE) * (1 - Recovery Rate, RR) = Loss Given Default, LGD
LGD * Probability of Default, POD = Expected Loss, Loss
POD Approximation: POD = Spread / LGD

## Credit Spread
- `G-Spread`: treasury yield with the matching duration as benchmark
- `I-Spread`: interest rate swap as benchmar
- `Asset Swap Spread, ASW`: difference between the bond's fixed coupon rate and the fixed rate on an interest rate swap
- `Z-Spread`: spot curve as benchmark
- `CDS Basis`: CDS with the same duration as benchmark
-  `OAS Spread`
- Excess Spread

### Spread strategies

- When a wide spread curve flattens, underweight shorter-maturity bonds and overweight longer-maturity bonds.

### Expected Excess Return

EXR = (s × t) – (∆s × SD) – (t × p × L)
where
s = Z-spread
t = Holding period
SD = Spread duration
p = Probability of default
L = Loss severity



### Leverage Return

Leveraged Return = Unlevered return + D/E * (unlevered return - borrow rate)

## Floating Rate Note (FRN)F
- Quoted Margin, QM
- Discounted Margin, DM
- Zero Discount Margin, Z-DM

## Value at Risk
- `Incremental VaR` measures the impact of a specific portfolio position change on VaR
- `Relative VaR` evaluates all active portfolio positions versus the benchmark index
- `CVaR` measures a portfolio’s average loss over a specific time period conditional on that loss exceeding the VaR threshold.

## Methods to Assess Portfolio Tail Risk

### Parametric Method
- Uses expected value and standard deviation of risk factors assuming normal distribution
- Advantage: Simple and transparent calculation
- Disadvantage: Not well suited for non-normally distributed returns or option-based portfolios

### Historical Simulation
-	Prices existing portfolio using historical parameters and ranking results
- Advantage: Actual results, accommodates options, with no probability distribution assumed
- Disadvantage: Highly dependent on historical period and repetition of historical market trends

### Monte Carlo Analysis
- Involves generating random outcomes using portfolio measures and sensitivities
- Advantage: Randomly generated results from a probability distribution, accommodates options
- Disadvantage: Highly dependent on model assumptions and less transparent


### CDS

Upfront premium % = (Fixed Coupon - CDS Spread) * EffSpreadDur

- To underweight: buy CDS
