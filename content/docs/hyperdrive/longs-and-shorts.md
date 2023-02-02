---
title: "Longs and Shorts"
description: "Install the SDKs of TrueBlocks"
lastmod:
  - :git
  - lastmod
  - publishDate
draft: false
menu:
  docs:
    parent: hyperdrive
weight: 0400
toc: true
---

### 3. Longs and Shorts Determine Market Sentiment

The Hyperdrive AMM gives users the ability to open both long and short positions on the market sentiment indicator, aka fixed rate.

- When a user believes market sentiment is **too high**, they prefer to **long** the fixed rate. They believe the fixed rate is **higher** than their expectation of the variable rate for the term. This drives the fixed rate down.
- When a user believes market sentiment is **too low**, they prefer to **short** the fixed rate. They believe the fixed rate is **lower** than their expectation of the variable rate for the term. This drives the fixed rate up.

Since Hyperdrive facilitates both longs and shorts, it fully captures market sentiment, letting the fixed rate reflect the market's beliefs.

Hyperdrive's approach doesn't require the use of funding rates or liquidation engines to remain solvent through volatile market conditions. Instead, all of the accounting and mathematics required to keep the system safe are baked into the AMM itself.

This creates a symmetrical market where users can drive the rates up and down as market sentiment changes, just like a game of flappy bird.

![Flappy Bird](https://i.imgur.com/W9QVOam.png)
