---
title: "Introduction"
description: "TrueBlocks Docs"
lead: ""
date: 2020-10-06T08:48:23+00:00
lastmod:
  - :git
  - lastmod
  - date
  - publishDate
draft: false
images: []
menu:
  docs:
    parent: technical
weight: 0011
toc: true
---

# Hyperdrive

Hyperdrive is the next research leap from the Element team on variable and fixed rate primitives. _No preset expiration dates, no fragmented liquidity, and no LP rollovers, aka everlasting liquidity._

## A New Way To Trade Rates

The hyperdrive AMM introduces a market sentiment indicator (MSI) for DeFi interest rates. Almost all DeFi interest rates are constantly changing ([sometimes by the block](https://github.com/element-fi/robrox/pull/6)). In order to gauge market sentiment, a balanced system of longs and shorts must exist between fixed and variable rates, in order to capture the wisdom of the crowd. Hyperdrive provides this. The fixed rate represented in Hyperdrive is the market sentiment indicator.

Hyperdrive lets users short or long the sentiment indicator. If a user thinks the sentiment indicator is too high, they'll go long because they like the fixed rate. If they think it is too low, they go short because they like the variable rate. Which side are you on?

![](https://i.imgur.com/HrCb13e.png)

## Overview

Hyperdrive's new AMM provides the following for the DeFi space:

1. Terms on Demand
2. Consolidated and Everlasting liquidity
3. Longs and Shorts (symmetric market)
4. Trading Strategy
   - Multiplied Variable Rate Exposure
   - Volatility Harvesting on interest rates
   - Interest rate arbitrage (spread trades)
   - Fixed rate borrow
   - Spread borrow
5. Technical Teaser

### 1. Terms On Demand

Hyperdrive removes the concept of preset start and end dates. When a user chooses to trade on variable or fixed rates, the user starts their term, e.g. 6 months, on demand.

The fixed rate in these terms is the market sentiment indicator reflecting the market's expected average variable rates over the term on an underlying yield source, like stEth.

Previously, a user would be forced to pick a market with a term set to a specific maturity date. This trends towards suboptimal LP fees and UX. For example, users likely do not have a lot of demand to trade on terms that have only 1 week remaining, because gains are lower. LPs tend to be incentivized to be in new terms, since fees are higher.

### 2. Consolidated and Everlasting Liquidity

Previously, 6 month terms were deployed in a staggered manner. These staggered deployments lead to fragmented liquidity and required LPs to actively manage their position, rolling over their capital between different terms.

In Hyperdrive, terms are created on demand using the liquidity from a single pool. As a result, liquidity provision is no longer tied to a specific term. When a user provides liquidity, they do so for all future terms created from the pool. Their liquidity has no expiration. It is everlasting. The LP continues to collect fees on each trade as well as variable interest on unallocated capital, for as long as they wish.

### 3. Longs and Shorts Determine Market Sentiment

The Hyperdrive AMM gives users the ability to open both long and short positions on the market sentiment indicator, aka fixed rate.

- When a user believes market sentiment is **too high**, they prefer to **long** the fixed rate. They believe the fixed rate is **higher** than their expectation of the variable rate for the term. This drives the fixed rate down.
- When a user believes market sentiment is **too low**, they prefer to **short** the fixed rate. They believe the fixed rate is **lower** than their expectation of the variable rate for the term. This drives the fixed rate up.

Since Hyperdrive facilitates both longs and shorts, it fully captures market sentiment, letting the fixed rate reflect the market's beliefs.

Hyperdrive's approach doesn't require the use of funding rates or liquidation engines to remain solvent through volatile market conditions. Instead, all of the accounting and mathematics required to keep the system safe are baked into the AMM itself.

This creates a symmetrical market where users can drive the rates up and down as market sentiment changes, just like a game of flappy bird.

![Flappy Bird](https://i.imgur.com/W9QVOam.png)

### 4. Trading Strategies

#### A. Multiplied Variable Rate Exposure

Hyperdrive allows users to get as much variable exposure as they want by letting them borrow additional capital from the AMM at the current fixed rate and use it to open a short position.

By opening a short position, the user is buying the variable yield from the market's deployed assets. Users can buy interest on a higher amount of capital than they provide. There are no liquidations, they just provide a maximum loss to ensure protocol safety. Unlike every other market, a Hyperdrive short does not face the possibility of unlimited loss.

Because this position earns multiplied variable interest, it provides a stabilizing force encouraging the fixed rate to converge upon changes in the variable rate, otherwise Interest Rate Arbitrage exists.

#### B. Interest Rate Arbitrage

Hyperdrive's long/short mechanism allows for arbitrageurs to reap the benefit of volatile changes in interest rates from the market sentiment.

=> Insert Graph PSM Rates

As can be seen in this graph, Maker's PSM follows a stepwise function. As the PSM rate is changed, this allows for traders to quickly arbitrage the market sentiment to converge on the new rate.

#### C. Volatility Harvesting on Interest Rates

> Every user trade is met with an equal and opposite LP trade
>
> - Sir Isaac Newton

For every trade that happens on the AMM, the LP takes on the other side. This means the LP will generally hold a position that is opposite to the market sentiment. Whether the market is right or wrong, all trades pay fees to the LP holders.

Rates volatility attracts more trading, more fees, and more delusional activity from traders.

No matter the volatility, at the end of a term, the average variable rate for that term is a single number. Any trading that moves the fixed rate away from this number represents an inaccurate market prediction, which the LP takes the other side of, thereby profiting.

This means profit.

#### D. Fixed rate borrow

As described earlier, opening a short gives the user exposure to the variable rate of a position by purchasing that exposure at a fixed rate upfront. If a user pays a variable rate to borrow assets, they can use Hyperdrive to buy exposure to the variable lending rate on the same market for a fixed price. This hedges against changes in the variable rate and converts their variable rate borrow position into a fixed rate borrow position.

#### E. Spread borrow

If Hyperdrive positions are offered as collateral on a lending platform, a user can multiply their exposure if a spread exists between the borrow rate on the lending platform and the rate on Hyperdrive.

For example, let's say Maker's PSM offers a DAI lending rate for fixed rate DAI as collateral. If the lending rate is lower than the Hyperdrive's fixed rate, then the user can continue to collateralize, borrow DAI, long the fixed rate, and repeat until the rates converge on each other. Similar results can happen if shorts are taken as collateral.

## Technical Teaser

![](https://i.imgur.com/aphOgTj.png)
_Shut up and Hyperdrive_

Hyperdrive is a natural extension of the concepts introduced in the first iteration of the [Element Protocol](https://paper.element.fi/) which implemented a customised version of the constant power sum curve invariant from the seminal [YieldSpace](https://yield.is/YieldSpace.pdf) paper. Optimised for fixed rate trading, this curve's main benefit is curvature that adjusts with the passage of time.

Changing curvature of trading curves can be dangerous for protocol safety, as evidenced by the [Curve hack](https://medium.com/@peter_4205/curve-vulnerability-report-a1d7630140ec). Similar attacks are possible in a multi-curvature multi-term universe. The Hyperdrive solution does away with multiple curves, instead reflecting the passage of time in each position, an approach we're deeming "flat + curve". Each position is the sum of matured and unmatured portions.
