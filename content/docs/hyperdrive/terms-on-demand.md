---
title: "Terms On Demand"
description: "There are three ways to get the index. Each way involves some
tradeoff between initialization time, storage use, and local access."
date: 2021-08-09T10:19:51-03:00
lastmod:
  - :git
  - lastmod
  - date
  - publishDate
draft: false
menu: 
  docs:
    parent: hyperdrive
weight: 0300	
toc: true
---

### 1. Terms On Demand

Hyperdrive removes the concept of preset start and end dates. When a user chooses to trade on variable or fixed rates, the user starts their term, e.g. 6 months, on demand.

The fixed rate in these terms is the market sentiment indicator reflecting the market's expected average variable rates over the term on an underlying yield source, like stEth.

Previously, a user would be forced to pick a market with a term set to a specific maturity date. This trends towards suboptimal LP fees and UX. For example, users likely do not have a lot of demand to trade on terms that have only 1 week remaining, because gains are lower. LPs tend to be incentivized to be in new terms, since fees are higher.
