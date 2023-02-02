---
title: "Trading Strategies"
description: "Solutions to Common Problems"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: hyperdrive
weight: 0500
toc: true
---

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
