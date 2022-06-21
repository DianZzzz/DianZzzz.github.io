---
layout: blog
topic: CFA
title: Derivatives and Currency Management
tags: cfa finance
comments: true
date: 2022-06-19
---
# Derivatives and Currency Management

## Options

### Put Call Parity

C = P + S - PV(X)

### Put Call Forward Parity
C = P + PV(F) - PV(X)

### Greeks
- `Delta`: Change in value of option / Change in value of underlying
  - Delta for long calls is always positive
  - Delta for long puts is always negative
  - Delta for long (short) the underlying asset is 1 (-1)
- `Gamma`: Change in delta / Change in value of underlying
  - Gamma for long calls and long puts is always positive
- `Vega`: Change in value of option / Change in volatility of underlying
  - Vega for long calls and long puts is always positive
- `Theta`: Sensitivity of the option’s price to the passage of time, known as time decay
  - Theta for long calls and long puts is generally negative

### Synthetic Forward Position

To hedge a long forward position
- Sell the stock and lend the money
- Build a synthetic short forward position by short the call and long the put which ahve the same strike price and expiration date

To hedge a short forward position
- Borrow money to buy the underlying stock
- Build a synthetic long forward position by long the call and short the put which have the same strike price and expiration date

### Covered Call

- A long position in the asset with a short position in the call

### Protective Put

- A long position in the asset with a long position in the put

### Spreads

#### Bull spread
- A spread that becomes more valuable when the price of the underlying asset rises
- Investors buys one option and writes another with a higher exercise price

#### Bear spread
- A spread that becomes more valuable when the price of the underlying asset declines
- Investors buys the higher exercise price option and writes another with a lower exercise price

#### Calendar spread
- A long calendar spread is when one buys the more distant option and the sells the near term option
- A short calendar spread is when one buys the near term option and the sells the more distant option

### Straddle
- A long straddle is when one buys both puts and calls, with the same exercise price and same expiration date, on the same underlying asset.
- A short straddle is when one sells both puts and calls
- The investor buying a straddle is essentially betting volatility to increase

### Collar
- Long shares of stock and then buys a put with an exercise price below the current stock price and writes a call with an exercise price above the current stock price

### Volatility

σ_Annual(%)=σ_Monthly(%) * sqrt(252/21)

#### Volatility smile
- When the implied volatilities of OTM puts and calls are higher than the implied volatilities of ATM options.

#### Volatility skew
- The implied volatility increases for OTM puts and decreases for OTM calls
- This is because investors have generally less interest in OTM calls whereas OTM put options have found universal demand as portfolio insurance against a market sell-off.

#### Term Structure of Volatility
- The implied volatilities for longer-term options are usually higher than for near-term ones
- When the term structure inverted, it is usually a signal for market sell-off

#### Option Choice
![option](/assets/option.PNG)

## Derivatives

### Interest Rate Swap

Notional Amount for Interest Rate Swap = (Target Modified Duration - Portfolio Modified Duration) / Interest Rate Swap Duration * Market Value of Bond Portfolio

### Cheapest-to-deliver Bond

MV(CTD) = CTD Price / 100 * Futures Contract Size

Basis Point Value (BPV) = Modified Duration * 0.01% * Market Value

Number of Futures Contract to Hedge = - (BPV_target - BPV_portfolio) / BPV_CTD * Conversion Factor

### Equity Futures

Number of futures contract = (target beta - current beta) / futures beta * portfolio size / futures price

### Variance Swaps

Variance Notional = Vega Notional / (2 * Strike)

VarSwap_t = Variance Notional * PV factor * (t/T * realized volatility^2 + (T-t)/T * Implied volatility^2 - strike^2)

Settlement_T = Variance Notional * (Realized volatility^2 - Strike^2)

#### Delta Options
- >50 Delta Call = ITM
- =50 Delta Call = ATM
- <50 Delta cALL = OTM

### Fed Fund Futures

Fed funds futures contract price = 100 − Expected FFE rate.

Probability of rate hike = (Fed Fund Rate implied by futures contract - mid-point of current fed rate) / (mid-point if rate hike is enacted - mid-point of current fed rate)

## Foreign Currency

`Price Currency / Base Currency`

`Down the ask and divide`
`Up the bid and multiply`

### Currency Risk and Return

Domestic Currency Return = (1 + Return in Foreign Currency) * (1 + Return in Forex Rate) - 1

Domestic Currency Volatility^2 = Foreign Currency Volatility^2 + Forex Rate Volatility^2 + 2 * Foreign Currency Volatility * Forex Rate Volatility * correlation

### Currency Hedge Strategies

- To hedge a long position in the price currency, you needs to sell the price currency, i.e. purchase of the base currency. Calls will be used.
- To hedge a short position in the price currency, you needs to buy the price currency, i.e. sale of the base currency. Puts will be used.

#### Roll Yields

A **US-based** fund manager holding **UK government bonds** have a **long** position in GBP. He will want to hedge the GBP against USD by **shorting** GBP forward.

The current spot rate is USD/GBP 1.28 and the 3-month futures price is USD/GBP 1.20. **F < S**, the base currency (GBP) is trading at a forward discount. To hedge, he will short GBP futures at a lower price and as the contract is close to maturity, the futures price will approach the spot price of 1.28 and he proceeds to close the contract by buying GBP at 1.28 => there will be a loss on the futures contract => resulting in a **negative roll yield**. This would increase the hedging cost.

#### Option Strategies

- Risk Reversal
  - Buying a call and writing a put is a long position in risk reversal
  - Buying a put and writing a call is a short position in risk reversal
- Put Spread: Buying an OTM put and writing a deeper-OTM put
- Seagull Spread: Buying a protective put and write both a call and a deep-OTM put
- Cross Hedge
  - Mean Variance Hedge Ratio = correlation * domestic currency standard deviation / forex standard deviation

### Considerations for emerging market currency exposure
- Higher trading costs than the major currencies under “normal” market conditions
- Increased likelihood of extreme market events and severe illiquidity under stressed market conditions
- Government involvement in setting the exchange rate through such measures as foreign exchange market intervention, capital controls, and pegged (or at least tightly managed) exchange rates
  - `Non-deliverable forwards (NDF)`: similar to regular forward contracts, but they are cash settled (in the non-controlled currency of the currency pair)
