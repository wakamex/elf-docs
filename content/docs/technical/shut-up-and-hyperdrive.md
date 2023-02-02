---
title: "Shut Up and Hyperdrive"
description: "How does TrueBlocks address the problem"
date: 2021-10-04T10:03:01-03:00
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
weight: 0100
toc: true
---

![](https://i.imgur.com/aphOgTj.png)

Hyperdrive is a natural extension of the concepts introduced in the first iteration of the [Element Protocol](https://paper.element.fi/) which implemented a customised version of the constant power sum curve invariant from the seminal [YieldSpace](https://yield.is/YieldSpace.pdf) paper. Optimised for fixed rate trading, this curve's main benefit is curvature that adjusts with the passage of time.

Changing curvature of trading curves can be dangerous for protocol safety, as evidenced by the [Curve hack](https://medium.com/@peter_4205/curve-vulnerability-report-a1d7630140ec). Similar attacks are possible in a multi-curvature multi-term universe. The Hyperdrive solution does away with multiple curves, instead reflecting the passage of time in each position, an approach we're deeming "flat + curve". Each position is the sum of matured and unmatured portions.
