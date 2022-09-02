---
layout: blog
topic: CFA
title: Fixed-Income Portfolio Management
tags: cfa finance
comments: true
date: 2022-06-21
---
# Fixed-Income Portfolio Management

<!-- MDTOC maxdepth:6 firsth1:0 numbering:0 flatten:0 bullets:1 updateOnSave:1 -->

- [Statistical Credit Analysis](#statistical-credit-analysis)   
- [Fixed Income Portfolio Measures](#fixed-income-portfolio-measures)   
   - [Duration](#duration)   
      - [Macaulay duration](#macaulay-duration)   
      - [Modified duration](#modified-duration)   
      - [Effective Duration](#effective-duration)   
      - [Key Rate Duration](#key-rate-duration)   
      - [Empirical duration](#empirical-duration)   
      - [Money duration](#money-duration)   
      - [Price value of a basis point (PVBP)](#price-value-of-a-basis-point-pvbp)   
      - [Spread Duration](#spread-duration)   
      - [Duration times spread (DTS)](#duration-times-spread-dts)   
      - [Portfolio dispersion](#portfolio-dispersion)   
      - [Convexity](#convexity)   
      - [Effective convexity](#effective-convexity)   
- [Fixed Income Return Model](#fixed-income-return-model)   
- [Repo Agreements](#repo-agreements)   
- [Classification of Liabilities](#classification-of-liabilities)   
   - [Type 1](#type-1)   
   - [Type 2](#type-2)   
   - [Type 3](#type-3)   
   - [Type 4](#type-4)   
- [Portfolio Immunization](#portfolio-immunization)   
   - [Immunization Conditions](#immunization-conditions)   
      - [Single Liabilities](#single-liabilities)   
      - [Multiple Liabilities](#multiple-liabilities)   
   - [Derivatives Overlay](#derivatives-overlay)   
      - [Calls and Puts](#calls-and-puts)   
      - [Swap](#swap)   
      - [Swaptions](#swaptions)   
- [Bond Index](#bond-index)   
   - [Reduce tracking error](#reduce-tracking-error)   
- [Yield Curve](#yield-curve)   
   - [Butterfly Spread](#butterfly-spread)   
   - [Bull Steepening](#bull-steepening)   
   - [Bear Steepening](#bear-steepening)   
   - [Bull Flattening](#bull-flattening)   
   - [Bear Flattening](#bear-flattening)   
- [Credit Risk](#credit-risk)   
- [Credit Spread](#credit-spread)   
   - [Spread strategies](#spread-strategies)   
   - [Expected Excess Return](#expected-excess-return)   
   - [Leverage Return](#leverage-return)   
- [Floating Rate Note (FRN)](#floating-rate-note-frn)   
- [Value at Risk](#value-at-risk)   
- [Methods to Assess Portfolio Tail Risk](#methods-to-assess-portfolio-tail-risk)   
   - [Parametric Method](#parametric-method)   
   - [Historical Simulation](#historical-simulation)   
   - [Monte Carlo Analysis](#monte-carlo-analysis)   
   - [CDS](#cds)   

<!-- /MDTOC -->

## Statistical Credit Analysis

- `Reduced form credit models`: solve for default intensity, or the POD over a specific time period, using observable company-specific variables such as financial ratios and recovery assumptions as well as macroeconomic variables, including economic growth and market volatility measures.
- `Structural credit models`: use market-based variables to estimate the market value of an issuer’s assets and the volatility of asset value. The likelihood of default is defined as the probability of the asset value falling below that of liabilities.


## Fixed Income Portfolio Measures

### Duration

#### Macaulay duration
- Weighted average of the time to receipt of the bond’s promised payments
- Increases linearly with maturity of the bond
- Zero replication: If the investment horizon equals the Macaulay duration of the portfolio, the capital loss created by the increase in yields and the reinvestment effects (gains) will roughly offset, leaving the realized return approximately equal to the original yield to maturity.

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
- Contingent immunization: allows for active bond portfolio management until a minimum threshold in the surplus is reached.

Immunized portfolio convexity = (MacDur^2 + MacDur + Dispersion) / (1 + Cash flow yield)^2

### Immunization Conditions

#### Single Liabilities
- Match the Macaulay duration
- Minimize convexity

#### Multiple Liabilities
- the money duration (or BPV) of the asset and liability to match
- the immunizing portfolio needs to be greater than the convexity (and dispersion) of the outflow portfolio. But, the convexity of the immunizing portfolio should be minimized in order to minimize dispersion and reduce structural risk.

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
Long a payer swaption: receive float and pay fixed

## Bond Index

Tracking error of 1% means that assuming normally distributed returns, in 68% of time periods, the fund should have a return that is within 1% of the tracked index.

### Reduce tracking error
- using the present value of distribution of cash flows methodology
- matching the amount of index duration that comes from each sector, as well as matching the amount of index duration that comes from various quality categories across government and non-government bonds, to minimize tracking error.
- evaluate the portfolio duration coming from each issuer to minimize event risk

## Yield Curve

### Butterfly Spread
- Butterfly spread = - short term yield + 2 * mid-term yield - long-term yield
- Positive butterfly: A decrease in the butterfly spread due to higher short- and long-term yields-to-maturity and a lower intermediate yield-to-maturity.
  - Strategy: a long bullet with a short barbell
- Negative butterfly: An increase in the butterfly spread due to lower short- and long-term yields-to-maturity and a higher intermediate yield-to-maturity.
  - Strategy: a short bullet with a long barbell


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
- `Yield/Benchmark-Spread`: subtracts the yield of an on-the-run government bond; maturities may not match
- `G-Spread`: treasury yield with the matching duration as benchmark
- `I-Spread`: interest rate swap as benchmark
- `Asset Swap Spread, ASW`: difference between the bond's fixed coupon rate and its interest swap rate
- `Z-Spread`: spot curve as benchmark
- `CDS Basis`: CDS with the same duration as benchmark
-  `OAS Spread`
- Excess Spread

### Spread strategies

- When a wide spread curve flattens, underweight shorter-maturity bonds and overweight longer-maturity bonds.

### Expected Excess Return

E [ExcessSpread] ≈ Current OAS − (EffSpreadDur × ΔSpread) − (POD × LGD)

EXR = (s × t) – (∆s × SD) – (t × p × L)
where
s = Z-spread
t = Holding period
SD = Spread duration
p = Probability of default
L = Loss severity

Or

EXR = OAS - Expected Loss


### Leverage Return

Leveraged Return = Unlevered return + D/E * (unlevered return - borrow rate)

## Floating Rate Note (FRN)
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
