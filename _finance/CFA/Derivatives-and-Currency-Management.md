---
layout: blog
topic: CFA
title: Derivatives and Currency Management
tags: cfa finance
comments: true
date: 2022-06-19
---
# Derivatives and Currency Management

<!-- MDTOC maxdepth:6 firsth1:0 numbering:0 flatten:0 bullets:1 updateOnSave:1 -->

- [Options](#options)   
   - [Put Call Parity](#put-call-parity)   
   - [Put Call Forward Parity](#put-call-forward-parity)   
   - [Greeks](#greeks)   
   - [Synthetic Forward Position](#synthetic-forward-position)   
   - [Covered Call](#covered-call)   
   - [Protective Put](#protective-put)   
   - [Spreads](#spreads)   
      - [Bull spread](#bull-spread)   
      - [Bear spread](#bear-spread)   
      - [Calendar spread](#calendar-spread)   
   - [Straddle](#straddle)   
   - [Strangle](#strangle)   
   - [Collar](#collar)   
   - [Volatility](#volatility)   
      - [Volatility smile](#volatility-smile)   
      - [Volatility skew](#volatility-skew)   
      - [Term Structure of Volatility](#term-structure-of-volatility)   
      - [Option Choice](#option-choice)   
- [Derivatives](#derivatives)   
   - [Interest Rate Swap](#interest-rate-swap)   
   - [Cheapest-to-deliver Bond](#cheapest-to-deliver-bond)   
   - [Equity Futures](#equity-futures)   
   - [Bond Futures](#bond-futures)   
   - [Variance Swaps](#variance-swaps)   
   - [Total Return Swap](#total-return-swap)   
      - [Compared to ETF](#compared-to-etf)   
   - [Fed Fund Futures](#fed-fund-futures)   
- [Foreign Currency](#foreign-currency)   
   - [Currency Risk and Return](#currency-risk-and-return)   
   - [Currency Hedge Strategies](#currency-hedge-strategies)   
      - [Dynamic vs. Static](#dynamic-vs-static)   
      - [Forward vs. Futures](#forward-vs-futures)   
      - [Option Strategies](#option-strategies)   
      - [Roll Yields](#roll-yields)   
      - [Option Strategies](#option-strategies)   
   - [Considerations for emerging market currency exposure](#considerations-for-emerging-market-currency-exposure)   
   - [Currency Hedge Consideration](#currency-hedge-consideration)   
   - [Carry Trade and Forward Premium Bias](#carry-trade-and-forward-premium-bias)   

<!-- /MDTOC -->
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
  - 50-delta ATM; <50 ITM; >50 OTM
- `Gamma`: Change in delta / Change in value of underlying
  - Gamma for long calls and long puts is always positive
  - The largest gamma occurs when options are trading at the money or near expiration
- `Vega`: Change in value of option / Change in volatility of underlying
  - Vega for long calls and long puts is always positive
- `Theta`: Sensitivity of the option’s price to the passage of time, known as time decay
  - Theta for long calls and long puts is generally negative

### Synthetic Forward Position

To hedge a long forward position
- Sell the stock and lend the money
- Build a synthetic short forward position by short the call and long the put which have the same strike price and expiration date

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
- Investors buys the higher exercise price put and writes another with a lower exercise price

#### Calendar spread
- A long calendar spread is when one buys the more distant option and the sells the near term option
- A short calendar spread is when one buys the near term option and the sells the more distant option

### Straddle
- A long straddle is when one buys both ATM puts and calls, with the same exercise price and same expiration date, on the same underlying asset.
- A short straddle is when one sells both puts and calls
- The investor buying a straddle is essentially betting volatility to increase

### Strangle
- A long position is buying OTM puts and calls with the same expiry date and the same degree of being out of the money
- Because OTM options are being bought, the cost of the position is cheaper—but conversely, it also does not pay off until the spot rate passes the OTM strike levels. As a result, the risk–reward for a strangle is more moderate than that for a straddle.

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

### Bond Futures

- If the basis is positive, a trader would make a profit by “selling the basis” — selling the bond and buying the futures.
- If the basis is negative, the trader would make a profit by “buying the basis” - buying the bond and short the futures.

### Variance Swaps

Variance Notional = Vega Notional / (2 * Strike)

VarSwap_t = Variance Notional * PV factor * (t/T * realized volatility^2 + (T-t)/T * Implied volatility^2 - strike^2)

Settlement_T = Variance Notional * (Realized volatility^2 - Strike^2)

### Total Return Swap

- The TRS payer buys protection against a possible decline in the value of the asset. The payer pays positive return to the receiver while being paid LIBOR-based interest returns
- The TRS receiver pays a LIBOR-based payment and any depreciation in the value of the asset

#### Compared to ETF
- Capital Commitment: an ETF would be less efficient (requiring a larger cash outlay) because the capital commitment equals the full notional value. In contrast, a total return swap generates a similar economic exposure to ETFs with much lower capital.
- Liquidity: ETF would be more efficient as ETFs enjoy liquid trading and narrow bid–ask spreads. In contrast, total return swaps are over-the-counter contracts (not exchange traded) that are negotiated and customizable on such features as maturity, leverage, and cost.
- Tracking Error: ETF would have associated tracking error, which may result from premiums and discounts to net asset value, cash drag, or regulatory diversification requirements. In contrast, for total return swaps, the replication is exact.

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

#### Dynamic vs. Static

A static hedge will avoid transaction costs but tend to accumulate unwanted currency exposures as the value of the foreign-currency assets change, causing a mismatch between the market value of the foreign-currency asset portfolio and the nominal size of the forward contract used for the currency hedge

#### Forward vs. Futures

- A forward contract is more flexible in terms of currency pair, settlement date, and transaction amount.
- Forward contracts are simpler than futures contracts owing to the absence of margin requirements, reducing portfolio management expense.
- Forward contracts are more liquid than futures because the daily trade volume for OTC currency forward contracts dwarfs those for exchange-traded futures contracts.
- Futures contract has lower transaction costs. However, they not only have initial margin requirements, they also have daily mark-to-market and can be subject to daily margin calls.

#### Option Strategies

- To hedge a long position in the price currency, you needs to sell the price currency, i.e. purchase of the base currency. Calls will be used.
- To hedge a short position in the price currency, you needs to buy the price currency, i.e. sale of the base currency. Puts will be used.

#### Roll Yields

A **US-based** fund manager holding **UK government bonds** have a **long** position in GBP. He will want to hedge the GBP against USD by **shorting** GBP forward.

The current spot rate is USD/GBP 1.28 and the 3-month futures price is USD/GBP 1.20. **F < S**, the base currency (GBP) is trading at a forward discount. To hedge, he will short GBP futures at a lower price and as the contract gets close to maturity, the futures price will approach the spot price of 1.28 and he proceeds to close the contract by buying GBP at 1.28 => there will be a loss on the futures contract => resulting in a **negative roll yield**. This would increase the hedging cost.


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

### Currency Hedge Consideration

- Trading cost: bid-offer spread, option premiums, rolling hedges, administrative infrastructure for setting up currency trading operation
- Opportunity cost: To be 100% hedged is to forgo any possibility of favorable currency rate moves. If skillfully handled, accepting and managing currency risk—or any financial risk—can potentially add value to the portfolio

### Carry Trade and Forward Premium Bias

||Buy/Invest        | Sell/Borrow |
|:-------------|:------------------|:------|
|Implementing the carry trade | High-yield currency | Low-yield currency  |
| Trading the forward rate bias | Forward discount currency |	Forward premium currency
